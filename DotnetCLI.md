# .NET CLI (Command Line Interface)

The .NET CLI (Command Line Interface) provides a set of commands that allow developers to manage and interact with .NET applications and projects from the command line. Here's an explanation of the basic .NET CLI commands you mentioned:
1. [`dotnet new`](#dotnet-new): Creates new .NET projects from various templates.
2. [`dotnet restore`](#dotnet-restore): Restores project dependencies. It fetches and installs the required packages defined in the project's *.csproj or *.fsproj files.
3. [`dotnet build`](#dotnet-build): Compiles and builds .NET projects.
4. [`dotnet publish`](#dotnet-publish): Prepares applications for deployment.
5. [`dotnet run`](#dotnet-run): Builds and runs applications in one step.
6. [`dotnet test`](#dotnet-test): Executes unit tests for projects.
7. [`dotnet clean`](#dotnet-clean): Removes build artifacts and intermediate files.
8. [`dotnet store`](#dotnet-store): Manages shared runtime assemblies.
9. [`dotnet watch`](#dotnet-watch): Monitors and automates code changes during development.

## `dotnet new`

**Command:** `dotnet new`

**Description:** Creates a new .NET project based on predefined templates.

**Options:**
- `<TEMPLATE>`: Specifies the project template (e.g., `console`, `webapi`, `classlib`).
- `-n <NAME>`: Specifies the name of the project.
- `-o <OUTPUT_DIRECTORY>`: Specifies the output directory.
- `-lang <LANGUAGE>`: Specifies the programming language (e.g., C# or F#).

**Examples:**
1. Create a new console application:
   ```bash
   dotnet new console -n MyConsoleApp
   ```

2. Create a new ASP.NET Core Web API project:
   ```bash
   dotnet new webapi -n MyWebAPI
   ```

3. Create a new class library project:
   ```bash
   dotnet new classlib -n MyLibrary
   ```

4. Create a new F# console application:
   ```bash
   dotnet new console -n MyFSharpApp -lang F#
   ```

This command allows you to quickly set up the structure of your project based on templates, making it easy to start working on your .NET application.

## `dotnet restore`

**Command:** `dotnet restore`

**Description:** Restores dependencies for a .NET project.

**Options:**
- `<PROJECT>`: Specifies the path to the project or solution file.
- `<SOLUTION>`: Specifies the path to a solution file containing multiple projects.

**Key Concepts:**
1. **Dependency Resolution**: `dotnet restore` fetches and installs all required NuGet packages and project references for a project.
2. **NuGet Package Restore**: Downloads and stores NuGet packages from package sources (e.g., NuGet.org) into a local cache directory.
3. **Project Reference Restore**: Ensures that project references within the solution or project are correctly resolved and built.
4. **Transitive Dependencies**: Handles dependencies of your project's dependencies to ensure a complete dependency graph.

**Examples:**
1. Restore dependencies for a single project:
   ```bash
   dotnet restore
   ```

2. Restore dependencies for a specific project:
   ```bash
   dotnet restore MyProject.csproj
   ```

3. Restore dependencies for a solution file:
   ```bash
   dotnet restore MySolution.sln
   ```

After running `dotnet restore`, your project will have all the necessary dependencies available for building and running your .NET application. This is a crucial step in the development workflow to ensure your code has access to the required libraries and packages.

## `dotnet build`

**Command:** `dotnet build`

**Description:** Compiles and builds a .NET project.

**Options:**
- `<PROJECT>`: Specifies the path to the project or solution file.
- `<SOLUTION>`: Specifies the path to a solution file containing multiple projects.
- `-c|--configuration <CONFIGURATION>`: Specifies the build configuration (e.g., Debug or Release).
- `--framework <FRAMEWORK>`: Specifies the target framework.
- `--output <OUTPUT_DIRECTORY>`: Specifies the output directory for build artifacts.
- `--runtime <RUNTIME_IDENTIFIER>`: Specifies the target runtime.

**Key Concepts:**
1. **Compilation**: `dotnet build` compiles source code files into Intermediate Language (IL) code that can be executed by the .NET runtime.
2. **Dependency Resolution**: Ensures all dependencies (including NuGet packages and project references) are available.
3. **Output Generation**: Generates output files, such as executables or DLLs, in an output directory (usually "bin").
4. **Configuration and Target Framework**: The build process can be customized by specifying the configuration and target framework.
5. **Error Reporting**: Reports any compilation errors or warnings in the console output.

**Examples:**
1. Build a single project:
   ```bash
   dotnet build
   ```

2. Build a specific project:
   ```bash
   dotnet build MyProject.csproj
   ```

3. Build a solution file:
   ```bash
   dotnet build MySolution.sln
   ```

4. Build for a specific configuration and framework:
   ```bash
   dotnet build -c Release --framework net5.0
   ```

After running `dotnet build`, your project will be compiled and built, and the output files will be available in the specified output directory. This command is essential for preparing your code for execution and distribution.

## `dotnet publish`

**Command:** `dotnet publish`

**Description:** Packages and publishes a .NET application for deployment.

**Options:**
- `<PROJECT>`: Specifies the path to the project or solution file.
- `<SOLUTION>`: Specifies the path to a solution file containing multiple projects.
- `-c|--configuration <CONFIGURATION>`: Specifies the build configuration (e.g., Debug or Release).
- `--framework <FRAMEWORK>`: Specifies the target framework.
- `--output <OUTPUT_DIRECTORY>`: Specifies the output directory for published files.
- `--runtime <RUNTIME_IDENTIFIER>`: Specifies the target runtime.
- `--self-contained`: Creates a self-contained deployment that includes the .NET runtime and dependencies.
- `--no-self-contained`: Publishes as a framework-dependent deployment.
- `--publish-single-file`: Packages the application into a single executable file.
- `--version-suffix <VERSION_SUFFIX>`: Adds a version suffix to the published output.
- `-o|--output <OUTPUT_DIRECTORY>`: Specifies the output directory for published files.

**Key Concepts:**
1. **Packaging and Publishing**: `dotnet publish` packages your application and its dependencies for deployment.
2. **Configuration and Target Framework**: Customize the build configuration and target framework for publishing.
3. **Output Generation**: The command generates output files in an output directory.
4. **Self-Contained Deployment**: Option to create a self-contained deployment with the .NET runtime and dependencies included.
5. **Single File Deployment**: Option to package the application into a single executable file.
6. **Version Suffix**: Add a version suffix to the published output for versioning.

**Examples:**
1. Publish a single project:
   ```bash
   dotnet publish
   ```

2. Publish a specific project:
   ```bash
   dotnet publish MyProject.csproj
   ```

3. Publish a solution file:
   ```bash
   dotnet publish MySolution.sln
   ```

4. Publish for a specific configuration and framework:
   ```bash
   dotnet publish -c Release --framework net5.0
   ```

5. Create a self-contained deployment for a specific runtime:
   ```bash
   dotnet publish --runtime win-x64 --self-contained
   ```

After running `dotnet publish`, your application will be packaged and prepared for deployment in the specified output directory. Depending on the options chosen, it can include the .NET runtime and dependencies, making it ready to run on the target system. This command is a critical step in preparing your application for distribution.

## `dotnet run`

**Command:** `dotnet run`

**Description:** Builds and executes a .NET application directly from the command line.

**Options:**
- `<PROJECT>`: Specifies the path to the project or solution file.
- `<SOLUTION>`: Specifies the path to a solution file containing multiple projects.
- `--project <PROJECT>`: Specifies a specific project to run.
- `--verbosity <LEVEL>`: Sets the verbosity level of the command.
- `--configuration <CONFIGURATION>`: Specifies the build configuration (e.g., Debug or Release).
- `--framework <FRAMEWORK>`: Specifies the target framework.
- `--launch-profile <PROFILE>`: Specifies a launch profile for ASP.NET Core applications.
- `--no-build`: Skips the build process and runs the most recently built executable.

**Key Concepts:**
1. **Build and Run**: `dotnet run` compiles and runs your application in a single step.
2. **Project Selection**: You can specify the project or solution to run.
3. **Configuration and Target Framework**: Customize the build configuration and target framework.
4. **Verbosity**: Set the verbosity level for the command to control the amount of output displayed.
5. **Launch Profile**: For ASP.NET Core applications, you can specify a launch profile.
6. **No-Build Option**: Skip the build process if the application was already built.

**Examples:**
1. Run the default project in the current directory:
   ```bash
   dotnet run
   ```

2. Run a specific project:
   ```bash
   dotnet run MyProject.csproj
   ```

3. Run an ASP.NET Core application with a launch profile:
   ```bash
   dotnet run --launch-profile Development
   ```

4. Run without building (assuming the project was previously built):
   ```bash
   dotnet run --no-build
   ```

After running `dotnet run`, your application will be compiled (if necessary) and executed. This command is a convenient way to quickly test and run your .NET application during development without manually building or locating the executable file.

## `dotnet test`

**Command:** `dotnet test`

**Description:** Runs unit tests for a .NET project.

**Options:**
- `<PROJECT>`: Specifies the path to the project or solution file.
- `<SOLUTION>`: Specifies the path to a solution file containing multiple projects.
- `--verbosity <LEVEL>`: Sets the verbosity level of the command.
- `--filter <EXPRESSION>`: Filters tests based on a test case filter expression.
- `--list-tests`: Lists discovered tests without running them.
- `--no-build`: Skips the build process.
- `--logger <LOGGER_NAME>`: Specifies a test logger (e.g., trx, console).

**Key Concepts:**
1. **Test Execution**: `dotnet test` discovers and runs unit tests in the specified project or solution.
2. **Project Selection**: You can specify the project or solution that contains the tests to be run.
3. **Verbosity**: Set the verbosity level to control the amount of output displayed during testing.
4. **Test Filtering**: Use the `--filter` option to selectively run specific tests based on filter expressions.
5. **List Tests**: Use the `--list-tests` option to list discovered tests without running them.
6. **No-Build Option**: Skip the build process if the tests were previously built.
7. **Test Loggers**: Choose a test logger to specify the format of the test output.

**Examples:**
1. Run tests for the default project in the current directory:
   ```bash
   dotnet test
   ```

2. Run tests for a specific project:
   ```bash
   dotnet test MyProject.Tests.csproj
   ```

3. Run tests with increased verbosity:
   ```bash
   dotnet test --verbosity detailed
   ```

4. Run tests with a filter expression to select specific tests:
   ```bash
   dotnet test --filter "TestCategory=Unit"
   ```

5. List discovered tests without running them:
   ```bash
   dotnet test --list-tests
   ```

After running `dotnet test`, the unit tests in your project will be executed, and the results will be displayed in the console. This command is essential for ensuring the correctness of your code and catching any issues through automated testing.

## `dotnet clean`

**Command:** `dotnet clean`

**Description:** Cleans a .NET project by removing build artifacts and intermediate files.

**Options:**
- `<PROJECT>`: Specifies the path to the project or solution file.
- `<SOLUTION>`: Specifies the path to a solution file containing multiple projects.
- `-c|--configuration <CONFIGURATION>`: Specifies the build configuration (e.g., Debug or Release).
- `--framework <FRAMEWORK>`: Specifies the target framework.
- `--output <OUTPUT_DIRECTORY>`: Specifies the output directory for build artifacts.
- `--verbosity <LEVEL>`: Sets the verbosity level of the command.

**Key Concepts:**
1. **Cleaning Process**: `dotnet clean` removes build artifacts, intermediate files, and other generated files.
2. **Project Selection**: You can specify the project or solution to clean.
3. **Configuration and Target Framework**: Customize the build configuration and target framework.
4. **Output Directory**: Specify the output directory where build artifacts are stored.
5. **Verbosity**: Set the verbosity level to control the amount of output displayed.

**Examples:**
1. Clean the default project in the current directory:
   ```bash
   dotnet clean
   ```

2. Clean a specific project:
   ```bash
   dotnet clean MyProject.csproj
   ```

3. Clean a solution file:
   ```bash
   dotnet clean MySolution.sln
   ```

4. Clean for a specific configuration and framework:
   ```bash
   dotnet clean -c Release --framework net5.0
   ```

5. Clean with increased verbosity:
   ```bash
   dotnet clean --verbosity detailed
   ```

After running `dotnet clean`, your project will be free of build artifacts and intermediate files, ensuring a clean and efficient development environment. This command is useful for resolving build issues and starting with a fresh project state when necessary.

## `dotnet store`

**Command:** `dotnet store`

**Description:** Stores specified assemblies in the runtime package store.

**Options:**
- `-m|--manifest <PATH_TO_MANIFEST_FILE>`: Specifies the package store manifest file.
- `-f|--framework <FRAMEWORK_VERSION>`: Specifies the target framework.
- `-r|--runtime <RUNTIME_IDENTIFIER>`: Specifies the target runtime.
- `--framework-version <FRAMEWORK_VERSION>`: Specifies the .NET SDK version.
- `--output <OUTPUT_DIRECTORY>`: Specifies the path to the runtime package store.
- `--skip-optimization`: Skips the optimization phase.
- `--skip-symbols`: Skips symbol generation (Windows and Linux only).
- `-v|--verbosity <LEVEL>`: Sets the verbosity level of the command.
- `--working-dir <WORKING_DIRECTORY>`: Specifies the working directory used by the command.

**Key Concepts:**
1. **Storing Assemblies**: `dotnet store` stores specified assemblies in the runtime package store.
2. **Manifest File**: Use the `-m|--manifest` option to specify a package store manifest file containing a list of packages to store.
3. **Configuration and Target Runtime**: Customize the target framework, runtime, and SDK version.
4. **Output Directory**: Specify the path to the runtime package store using the `--output` option.
5. **Skipping Optimization**: The `--skip-optimization` option skips the optimization phase.
6. **Skipping Symbols**: The `--skip-symbols` option skips symbol generation (supported on Windows and Linux).
7. **Verbosity**: Set the verbosity level to control the amount of output displayed.
8. **Working Directory**: Use the `--working-dir` option to specify the working directory.

**Examples:**
1. Store assemblies specified in a package manifest file for .NET 6.0.1:
   ```bash
   dotnet store --manifest packages.csproj --framework-version 6.0.1 --framework net6.0 --runtime win-x64
   ```

2. Store assemblies specified in a package manifest file without optimization:
   ```bash
   dotnet store --manifest packages.csproj --skip-optimization --framework net6.0 --runtime linux-x64
   ```

After running `dotnet store`, the specified assemblies will be stored in the runtime package store, optimizing them for the target runtime and framework. This command is useful for managing dependencies and ensuring that the necessary assemblies are available for your application.

## `dotnet watch`

**Command:** `dotnet watch`

**Description:** Monitors your .NET application for changes and automatically rebuilds and restarts it when changes are detected.

**Options:**
- `<COMMAND>`: Specifies the command to execute when changes are detected (e.g., `run`, `test`, or a custom script).
- `<ARGS>`: Specifies any arguments to pass to the `<COMMAND>`.

**Key Concepts:**
1. **Automatic Reloading**: `dotnet watch` continuously monitors your project's source files for changes.
2. **Rebuild and Restart**: When changes are detected, it automatically rebuilds the project and restarts the application.
3. **Custom Commands**: You can specify a custom `<COMMAND>` to execute when changes occur, such as running the application, running tests, or executing a custom script.
4. **Command Arguments**: Pass additional `<ARGS>` to the `<COMMAND>` when it's executed.

**Examples:**
1. Watch and run the application (default command):
   ```bash
   dotnet watch run
   ```

2. Watch and run tests whenever changes are detected:
   ```bash
   dotnet watch test
   ```

3. Watch and execute a custom script on changes:
   ```bash
   dotnet watch exec my-script.sh
   ```

4. Watch and run a specific command with arguments:
   ```bash
   dotnet watch myapp.dll arg1 arg2
   ```

After starting `dotnet watch`, it will continuously monitor your project's files. When changes are detected, it will automatically rebuild and restart your application using the specified command or script. This is extremely helpful during development, as it eliminates the need to manually stop and restart your application every time you make code changes.
