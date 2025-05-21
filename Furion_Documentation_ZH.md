# Furion 框架文档说明

## 2. 入门指南
### 2.1 入门指南
本入门指南旨在帮助开发者快速上手 Furion 框架。主要步骤包括：
1.  **创建项目**：通常创建一个控制台项目开始。
2.  **添加依赖**：通过 NuGet 包管理器添加 `Furion` 核心依赖包。
3.  **快速启动**：仅需简单配置，例如使用 `Serve.Run()` 即可启动应用。
4.  **编写API**：指南包含编写第一个 API 接口的示例。
5.  **配置选项**：介绍了 `Serve.Run()` 的多种配置方式，包括设置启动地址/端口、便捷服务注册及自定义配置。
6.  **集成所有功能**：即使从控制台项目开始，也能支持 Furion 的所有 Web 项目功能，如添加 `appsettings.json`、自定义 `Startup` 类等。
7.  **多种运行选项**：解释了 `RunOptions`、`LegacyRunOptions` 和 `GenericRunOptions` 的使用。
8.  **多平台支持**：介绍了如何在 WinForm, WPF 及控制台应用中集成和初始化 Furion。
9.  **其他特性**：提及了静默启动以及解决 .NET 5 视图路径问题的说明。

通过本指南，开发者可以快速搭建并运行一个基于 Furion 框架的应用，并了解其基本配置和使用方法。

### 2.2 ASP.NET 5 集成
要在 ASP.NET 5 项目中集成 Furion 框架，请遵循以下步骤：
1.  **创建 Web 项目**：首先，创建一个标准的 ASP.NET Core Web 应用程序项目。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器将 `Furion` 包添加到您的项目中。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中，调用 `Inject()` 方法。
    *   在 `Startup.cs` 文件中，确保在 `ConfigureServices` 和 `Configure` 方法中都调用了 `Inject()` 方法。具体来说，是在 `services.AddControllersWithViews().AddInject();` 和 `app.UseInject("api");`。
4.  **启动应用**：完成以上配置后，即可启动您的 ASP.NET 5 应用程序，并通过浏览器访问。

### 2.3 ASP.NET 6 集成
在 ASP.NET 6 项目中集成 Furion 框架的步骤如下，特别注意 .NET 6 推荐使用 `Minimal API` 模式：
1.  **创建 Web 项目**：使用 Visual Studio 或 `dotnet new web` 命令创建一个 ASP.NET Core Web 应用程序。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器搜索并安装 `Furion` 包。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中（.NET 6 的主配置区域），添加 `builder.Services.AddInject();` 来注册 Furion 服务，并在构建应用后通过 `app.UseInject("api");` 来启用 Furion 的API功能。
4.  **启动应用**：完成配置后，即可运行项目并通过浏览器访问。
5.  **WebApplication 说明**：文档还特别说明了 `WebApplication` 对象在 .NET 6 中的使用，它是配置和运行应用的核心。

### 2.4 ASP.NET 7 集成
在 ASP.NET 7 项目中集成 Furion 框架的步骤与 .NET 6 基本一致，继续沿用 `Minimal API` 模式：
1.  **创建 Web 项目**：通过 Visual Studio 或 `dotnet new web` 命令创建 ASP.NET Core Web 应用（选择 .NET 7 框架）。
2.  **添加 Furion 依赖包**：使用 NuGet 包管理器安装 `Furion` 包。
3.  **Furion 基本配置**：
    *   编辑 `Program.cs` 文件。通过 `builder.Services.AddInject();` 添加 Furion 服务。
    *   在应用构建后（`var app = builder.Build();`之后），调用 `app.UseInject("api");` 来启用 Furion 的 API 功能。
4.  **启动应用**：配置完成后，运行项目即可。
5.  **WebApplication 说明**：与 .NET 6 类似，`WebApplication` 类是 .NET 7 中配置和运行应用的中心。

### 2.5 ASP.NET 8 集成
在 ASP.NET 8 项目中集成 Furion 框架的步骤与 .NET 6 和 .NET 7 非常相似，继续采用 `Minimal API` 模式进行开发：
1.  **创建 Web 项目**：使用 Visual Studio 或通过 `dotnet new web` 命令创建 ASP.NET Core Web 应用（确保选择 .NET 8 框架）。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器，搜索并安装 `Furion` 最新版本包。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中，通过 `builder.Services.AddInject();` 来注册 Furion 核心服务。
    *   在应用构建（`var app = builder.Build();`）之后，调用 `app.UseInject("api");` 以启用 Furion 的 API 功能。
4.  **启动应用**：完成上述步骤后，即可运行您的 ASP.NET 8 项目。
5.  **WebApplication 说明**：.NET 8 同样使用 `WebApplication` 类作为应用配置和运行的中心点。

### 2.6 ASP.NET 9 集成
在 ASP.NET 9 项目中集成 Furion 框架的步骤预计将延续 .NET 8 的 `Minimal API` 模式：
1.  **创建 Web 项目**：使用 Visual Studio 或通过 `dotnet new web` 命令创建 ASP.NET Core Web 应用（确保选择 .NET 9 框架预览版或正式版）。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器，搜索并安装与 .NET 9 兼容的 `Furion` 最新版本包。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中，通过 `builder.Services.AddInject();` 来注册 Furion 核心服务。
    *   在应用构建（`var app = builder.Build();`）之后，调用 `app.UseInject("api");` 以启用 Furion 的 API 功能。
4.  **启动应用**：完成上述步骤后，即可运行您的 ASP.NET 9 项目。
5.  **WebApplication 说明**：.NET 9 将继续使用 `WebApplication` 类作为应用配置和运行的中心点。

注意：由于 .NET 9 可能仍在开发或预览阶段，具体步骤请参考 Furion 框架针对 .NET 9 的最新官方文档。

### 2.7 ASP.NET 10 集成
在 ASP.NET 10 项目中集成 Furion 框架的步骤预计将与 .NET 9 类似，继续采用 `Minimal API` 模式：
1.  **创建 Web 项目**：使用 Visual Studio 或通过 `dotnet new web` 命令创建 ASP.NET Core Web 应用（确保选择 .NET 10 框架预览版或正式版）。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器，搜索并安装与 .NET 10 兼容的 `Furion` 最新版本包。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中，通过 `builder.Services.AddInject();` 来注册 Furion 核心服务。
    *   在应用构建（`var app = builder.Build();`）之后，调用 `app.UseInject("api");` 以启用 Furion 的 API 功能。
4.  **启动应用**：完成上述步骤后，即可运行您的 ASP.NET 10 项目。
5.  **WebApplication 说明**：.NET 10 将继续使用 `WebApplication` 类作为应用配置和运行的中心点。

注意：由于 .NET 10 可能仍在开发或预览阶段，具体步骤请参考 Furion 框架针对 .NET 10 的最新官方文档。

### 2.8 官方脚手架
Furion 提供了官方的项目脚手架，以帮助开发者快速创建项目骨架。主要内容包括：

1.  **脚手架类型**：
    *   `Furion + EFCore`：集成 Entity Framework Core 的版本。
    *   `Furion + SqlSugar`：集成 SqlSugar ORM 的版本。

2.  **安装脚手架**：
    *   使用 `dotnet new --install Furion.Template` 命令安装基础版 (EFCore)。
    *   使用 `dotnet new --install Furion.SqlSugar.Template` 命令安装 SqlSugar 版。
    *   特定版本安装：可以通过附加 `--version <版本号>` 来安装指定版本的脚手架。

3.  **使用脚手架创建项目**：
    *   通过 `dotnet new furion` (EFCore版) 或 `dotnet new furionsqlsugar` (SqlSugar版) 命令创建新项目。
    *   可以通过 `-o <输出目录名>` 或 `--output <输出目录名>` 指定项目输出名称。

4.  **脚手架管理**：
    *   **更新**：重新执行安装命令即可更新到最新版。
    *   **卸载**：使用 `dotnet new --uninstall Furion.Template` 或 `dotnet new --uninstall Furion.SqlSugar.Template` 进行卸载。

5.  **Visual Studio 集成**：
    *   安装脚手架后，可以在 Visual Studio 的“创建新项目”对话框中找到并使用 Furion 相关的模板。
    *   如果 VS 中未显示模板，尝试重启 VS 或检查 .NET SDK 版本是否匹配。

6.  **常见问题**：
    *   文档提及了 MVC 项目中“添加区域”可能出现的问题及相关解决提示。

7.  **自定义脚手架**：开发者也可以参考官方文档搭建自己的项目脚手架。

通过使用官方脚手架，可以大大简化项目的初始搭建工作。

### 2.9 手动搭建分层
Furion 框架支持标准的领域驱动设计 (DDD) 分层架构。如果您不希望使用官方脚手架，可以手动搭建项目分层：

1.  **推荐分层设计**：
    *   **`Project.Core`** (核心层)：通常包含实体、仓储接口、领域服务等。
    *   **`Project.Application`** (应用层)：包含应用服务、DTOs (数据传输对象)等，处理业务逻辑。
    *   **`Project.Web`** (Web/展现层)：ASP.NET Core 项目，处理API接口、MVC视图等，作为启动项目。
    *   **`Project.EntityFramework.Core`** (基础设施层/EFCore实现)：具体的数据访问实现，如使用 Entity Framework Core。
    *   **`Project.Database.Migrations`** (数据库迁移层)：存放数据库迁移相关代码。

2.  **集成 Furion 功能**：
    *   在手动创建的各项目中，根据需要添加对 `Furion` NuGet包的引用。
    *   主要的 Furion 配置（如 `Inject()` 调用）通常在 Web 启动项目 (`Project.Web`) 的 `Program.cs` (或 `Startup.cs` for .NET 5) 中进行。
    *   其他层（如 Application, Core）按需引用 `Furion` 或其子模块即可使用框架提供的功能。

手动分层允许开发者根据项目需求灵活组织代码结构，并能很好地与 Furion 框架结合使用。

### 2.10 神奇的 Inject
Furion 框架中的 `Inject` 是一个核心特性，旨在简化应用的配置和服务的注册与使用。

1.  **设计理念**：`Inject` 的核心目标是实现配置代码的最小化，甚至一行代码即可完成常用配置。它遵循“约定优于配置”的原则，自动注册框架常用服务和配置。

2.  **主要方法**：
    *   **`Inject()` (在 `Program.cs` 或 `WebApplicationBuilder` 中)**：这是最常用的方法，用于在应用启动时注入 Furion 的所有核心组件和服务。对于 .NET 6+ 的 `Minimal API`，通常是 `builder.Services.AddInject()`。
    *   **`AddInject()` / `AddInjectBase()` / `AddInjectMini()` / `AddInjectWithUnifyResult()` (在 `Startup.ConfigureServices` 中，适用于 .NET 5)**：
        *   `AddInject()`：注册所有 Furion 服务。
        *   `AddInjectBase()`：只注册基础服务，不含 MVC、规范化结果等。
        *   `AddInjectMini()`：注册最核心的服务。
        *   `AddInjectWithUnifyResult()`：在 `AddInject()` 基础上额外注册规范化结果服务。
    *   **`UseInject()` / `UseInjectBase()` (在 `Startup.Configure` 中，适用于 .NET 5)**：
        *   `UseInject("api")`：启用 Furion 中间件，如动态API、异常处理、路由等。参数 "api" 是路由前缀。
        *   `UseInjectBase()`：只启用最核心的中间件。

3.  **使用场景**：
    *   **.NET 6+ (`Program.cs`)**：
        *   `builder.Services.AddInject();`
        *   `var app = builder.Build();`
        *   `app.UseInject("api");`
    *   **.NET 5 (`Startup.cs`)**：
        *   `ConfigureServices` 方法中: `services.AddControllersWithViews().AddInject();` (或其它 `AddInject` 系列方法)
        *   `Configure` 方法中: `app.UseInject("api");`

4.  **默认注册服务配置**：可以通过 `services.AddInject(options => { ... });` 来自定义 `Inject` 注册的服务范围，例如关闭某些默认服务的自动注册。

`Inject` 机制使得 Furion 框架的集成和启动过程非常便捷，开发者可以快速搭建起一个功能完备的应用环境。

### 2.11 .NET5 升级 .NET6
将基于 Furion 的 .NET 5 项目升级到 .NET 6，主要涉及以下步骤和注意事项：

1.  **安装 .NET 6 SDK**：确保开发环境中已安装 .NET 6 SDK。
2.  **编辑项目文件 (`.csproj`)**：
    *   将所有项目的目标框架从 `net5.0` 修改为 `net6.0`。
    *   移除Web启动项目中与 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` 和 `Furion.Pure`相关的 `FrameworkReference` (如果存在)。
3.  **升级 NuGet 包**：将 `Furion` 及其他相关依赖包升级到与 .NET 6 兼容的最新版本。
4.  **迁移到 `Minimal API` 模式**：
    *   **删除 `Startup.cs` 文件**：.NET 6 推荐使用 `Minimal API` 风格，不再默认使用 `Startup.cs`。
    *   **编辑 Web 启动层 `.csproj`**：移除 `<StartupObject>Program</StartupObject>` (如果存在)。
    *   **替换 `Program.cs` 内容**：将原 `Program.cs` 的内容替换为 .NET 6 的 `Minimal API` 启动方式。这通常包括：
        *   创建 `WebApplicationBuilder`：`var builder = WebApplication.CreateBuilder(args);`
        *   注册 Furion 服务：`builder.Services.AddInject();`
        *   构建应用：`var app = builder.Build();`
        *   启用 Furion 中间件：`app.UseInject();` (或 `app.UseInject("api");`)
        *   添加其他应用配置和中间件。
        *   运行应用：`app.Run();`
5.  **重新编译**：完成上述修改后，重新编译整个解决方案以确保所有更改生效且无编译错误。

升级过程主要是适配 .NET 6 的新特性，特别是 `Minimal API` 带来的项目结构和启动代码的变化。

### 2.12 .NET6 升级 .NET7
将基于 Furion 的 .NET 6 项目升级到 .NET 7 相对简单，因为两者都采用了相似的项目结构和 `Minimal API` 风格。主要步骤如下：

1.  **安装 .NET 7 SDK**：首先，确保您的开发环境中已安装 .NET 7 SDK。
2.  **编辑项目文件 (`.csproj`)**：
    *   将解决方案中所有项目的目标框架从 `net6.0` 修改为 `net7.0`。
3.  **升级 NuGet 包**：将 `Furion` 及其所有相关依赖项（如 `Furion.Extras.xxx`）升级到与 .NET 7 兼容的最新版本。建议查看 Furion 的更新日志以获取特定版本的兼容性信息。
4.  **重新编译**：完成上述更改后，清理并重新编译整个解决方案，以确保所有依赖项正确更新并且代码能够顺利编译。

由于 .NET 6 和 .NET 7 在项目模型上差异不大，通常不需要像从 .NET 5 升级那样修改 `Program.cs` 的启动代码结构，除非 Furion 的新版本针对 .NET 7 有特定的启动代码调整建议。

### 2.13 .NET7 升级 .NET8
将基于 Furion 的 .NET 7 项目升级到 .NET 8 过程较为平滑，因为 .NET 8 延续了 .NET 7 的 `Minimal API` 风格和项目结构。关键步骤包括：

1.  **安装 .NET 8 SDK**：确保您的开发环境已安装 .NET 8 SDK。
2.  **编辑项目文件 (`.csproj`)**：
    *   将解决方案中所有项目的目标框架从 `net7.0` 修改为 `net8.0`。
3.  **升级 NuGet 包**：
    *   将 `Furion` 包及其所有 `Furion.Extras.xxx` 扩展包升级到与 .NET 8 兼容的最新版本。
    *   同时，也需要更新其他第三方依赖库到它们的 .NET 8 兼容版本。
4.  **重新编译**：完成上述更改后，清理并重新编译整个解决方案。
5.  **升级失败解决方案**：如果遇到升级问题，文档建议删除 `bin` 和 `obj` 目录，清除 NuGet 缓存 (`dotnet nuget locals all --clear`)，然后重新编译。

通常情况下，升级到 .NET 8 不需要对 `Program.cs` 中的 Furion 配置代码进行大的调整，除非 Furion 针对 .NET 8 推出了特定的新配置方式或有重大更改。

### 2.14 .NET8 升级 .NET9
将基于 Furion 的 .NET 8 项目升级到 .NET 9 时，需关注以下关键步骤，此过程与先前 .NET 版本间的升级类似：

1.  **安装 .NET 9 SDK**：确保您的开发环境中已安装 .NET 9 SDK（预览版或正式版）。
2.  **编辑项目文件 (`.csproj`)**：
    *   将解决方案中所有项目的目标框架从 `net8.0` 修改为 `net9.0`。
3.  **升级 NuGet 包**：
    *   将 `Furion` 包及其所有 `Furion.Extras.xxx` 扩展包升级到与 .NET 9 兼容的最新版本。
    *   同时，更新其他第三方依赖库至其 .NET 9 兼容版本。
4.  **重新编译**：完成上述更改后，清理并重新编译整个解决方案。
5.  **升级失败解决方案**：如升级过程中遇到问题，文档通常建议删除 `bin` 和 `obj` 目录，清理 NuGet 缓存（例如，通过 `dotnet nuget locals all --clear` 命令），然后再次尝试编译。

由于 .NET 9 可能引入新的特性和变化，建议密切关注 Furion 框架的官方文档和版本说明，以获取针对 .NET 9 的最新和最详细的升级指导和兼容性信息。
