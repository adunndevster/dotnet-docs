---
title: dotnet command
description: Learn about the dotnet command (the generic driver for the .NET Core CLI) and its usage.
ms.date: 02/13/2020
---
# dotnet command

**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions

## Name

`dotnet` - A tool for managing .NET source code and binaries.

## Synopsis

To get information about the `dotnet` command and the environment:

```dotnetcli
dotnet [-h|--help] [--version] [--info] [--list-runtimes] [--list-sdks] 
```

To run a command:

```dotnetcli
[dotnet] [command] [-d|--diagnostics] [-h|--help] [--verbosity] [command-options] [arguments]
```

To run an application (.NET Core SDK 2.x):

```dotnetcli
dotnet [--additionalprobingpath] [--deps-file] [--additional-deps] [--fx-version]  [--roll-forward-on-no-candidate-fx] [path-to-application] [arguments]
```

To run an application (.NET Core SDK 3.x):

```dotnetcli
dotnet [--additionalprobingpath] [--deps-file] [--additional-deps] [--fx-version]  [--roll-forward] [path-to-application] [arguments]
```

## Description

`dotnet` is a tool for managing .NET source code and binaries. It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md). Each command defines its own arguments. Enter `--help` after each command to access brief help documentation.

`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`. See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.

## Options

The options are listed here in three groups:

* Options for use with the `dotnet` command by itself (for example,`dotnet --info`).
* Options for use when `dotnet` is used to run a command.
* Options for use when `dotnet` is used to run an application.

### Options for dotnet by itself

`-h|--help`

Prints out a list of available commands.

`--info`

Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.

`--version`

Prints out the version of the .NET Core SDK in use.

`--list-runtimes`

Displays the installed .NET Core runtimes.

`--list-sdks`

Displays the installed .NET Core SDKs.

### Options for running a command

`-d|--diagnostics`

Enables diagnostic output.

`-h|--help`

Prints out documentation for a given command, such as `dotnet build --help`.

`-v|--verbosity <LEVEL>`

Sets the verbosity level of the command. Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`. Not supported in every command; see specific command page to determine if this option is available.

## Options for running an application

`--additionalprobingpath <PATH>`

Path containing probing policy and assemblies to probe.

`--depsfile`

Path to a *deps.json* file.

A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts. For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.

`--additional-deps <PATH>`

Path to an additional *.deps.json* file.

`--fx-version <VERSION>`

Version of the .NET Core runtime to use to run the application.

`--runtimeconfig`

Path to a *runtimeconfig.json* file.

A *runtimeconfig.json* file is a configuration file containing run-time settings. For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).

`--roll-forward-on-no-candidate-fx <N>` (.NET Core SDK 2.x)

Defines behavior when the required shared framework is not available. `N` can be:

- `0` - Disable even minor version roll forward.
- `1` - Roll forward on minor version, but not on major version. This is the default behavior.
- `2` - Roll forward on minor and major versions.

 For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).

`--roll-forward <setting>` (.NET Core SDK 3.x)

Controls how roll forward is applied to the app. The roll forward `setting` can be one of the following values. If the setting is omitted, `Minor` is the default.

- `2` - Roll forward on minor and major versions.

- `LatestPatch` - Roll forward to the highest patch version. This disables minor version roll forward.
- `Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing. If the requested minor version is present, then the LatestPatch policy is used.
- `Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing. If the requested major version is present, then the Minor policy is used.
- `LatestMinor` - Roll forward to highest minor version, even if requested minor version is present. Intended for component hosting scenarios.
- `LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present. Intended for component hosting scenarios.
- `Disable` - Don't roll forward. Only bind to specified version. This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches. This value is only recommended for testing.

With the exception of the `Disable` setting, all settings will use the highest available patch version.

## dotnet commands

### General

| Command                                       | Function                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Builds a .NET Core application.                                     |
| [dotnet build-server](dotnet-build-server.md) | Interacts with servers started by a build.                          |
| [dotnet clean](dotnet-clean.md)               | Clean build outputs.                                                |
| [dotnet help](dotnet-help.md)                 | Shows more detailed documentation online for the command.           |
| [dotnet migrate](dotnet-migrate.md)           | Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Provides access to the MSBuild command line.                        |
| [dotnet new](dotnet-new.md)                   | Initializes a C# or F# project for a given template.                |
| [dotnet pack](dotnet-pack.md)                 | Creates a NuGet package of your code.                               |
| [dotnet publish](dotnet-publish.md)           | Publishes a .NET framework-dependent or self-contained application. |
| [dotnet restore](dotnet-restore.md)           | Restores the dependencies for a given application.                  |
| [dotnet run](dotnet-run.md)                   | Runs the application from source.                                   |
| [dotnet sln](dotnet-sln.md)                   | Options to add, remove, and list projects in a solution file.       |
| [dotnet store](dotnet-store.md)               | Stores assemblies in the runtime package store.                     |
| [dotnet test](dotnet-test.md)                 | Runs tests using a test runner.                                     |

### Project references

Command | Function
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Adds a project reference.
[dotnet list reference](dotnet-list-reference.md) | Lists project references.
[dotnet remove reference](dotnet-remove-reference.md) | Removes a project reference.

### NuGet packages

Command | Function
--- | ---
[dotnet add package](dotnet-add-package.md) | Adds a NuGet package.
[dotnet remove package](dotnet-remove-package.md) | Removes a NuGet package.

### NuGet commands

Command | Function
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Deletes or unlists a package from the server.
[dotnet nuget locals](dotnet-nuget-locals.md) | Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.
[dotnet nuget push](dotnet-nuget-push.md) | Pushes a package to the server and publishes it.

### Global, tool-path, and local tools commands

Tools are console applications that are installed from NuGet packages and are invoked from the command prompt. You can write tools yourself or install tools written by third parties. Tools are also known as global tools, tool-path tools, and local tools. For more information, see [.NET Core tools overview](global-tools.md). Global and tool-path tools are available starting with .NET Core SDK 2.1. Local tools are available starting with .NET Core SDK 3.0.

Command | Function
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Installs a tool on your machine.
[dotnet tool list](dotnet-tool-list.md) | Lists all global, tool-path, or local tools currently installed on your machine.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Uninstalls a tool from your machine.
[dotnet tool update](dotnet-tool-update.md) | Updates a tool that is installed on your machine.

### Additional tools

Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK. These tools are listed in the following table:

| Tool                                              | Function                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Creates and manages development certificates.                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core command-line tools.                    |
| sql-cache                                         | SQL Server cache command-line tools.                         |
| [user-secrets](/aspnet/core/security/app-secrets) | Manages development user secrets.                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | Starts a file watcher that runs a command when files change. |

For more information about each tool, type `dotnet <tool-name> --help`.

## Examples

Create a new .NET Core console application:

```dotnetcli
dotnet new console
```

Restore dependencies for a given application:

```dotnetcli
dotnet restore
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Build a project and its dependencies in a given directory:

```dotnetcli
dotnet build
```

Run an application DLL, such as `myapp.dll`:

```dotnetcli
dotnet myapp.dll
```

## Environment variables

`DOTNET_PACKAGES`

The global packages folder. If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.

`DOTNET_SERVICING`

Specifies the location of the servicing index to use by the shared host when loading the runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft. Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted). Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted). If not set, the default is `false` and the telemetry feature is active.

`DOTNET_MULTILEVEL_LOOKUP`

Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location. If not set, it defaults to `true`. Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted). For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Disables minor version roll forward, if set to `0`. For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).

## See also

- [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [.NET Core run-time configuration settings](../run-time-config/index.md)
