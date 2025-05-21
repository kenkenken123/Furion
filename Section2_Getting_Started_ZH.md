# 入门指南
## 2.1 入门指南
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

## 2.2 ASP.NET 5 集成
要在 ASP.NET 5 项目中集成 Furion 框架，请遵循以下步骤：
1.  **创建 Web 项目**：首先，创建一个标准的 ASP.NET Core Web 应用程序项目。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器将 `Furion` 包添加到您的项目中。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中，调用 `Inject()` 方法。
    *   在 `Startup.cs` 文件中，确保在 `ConfigureServices` 和 `Configure` 方法中都调用了 `Inject()` 方法。具体来说，是在 `services.AddControllersWithViews().AddInject();` 和 `app.UseInject("api");`。
4.  **启动应用**：完成以上配置后，即可启动您的 ASP.NET 5 应用程序，并通过浏览器访问。

## 2.3 ASP.NET 6 集成
在 ASP.NET 6 项目中集成 Furion 框架的步骤如下，特别注意 .NET 6 推荐使用 `Minimal API` 模式：
1.  **创建 Web 项目**：使用 Visual Studio 或 `dotnet new web` 命令创建一个 ASP.NET Core Web 应用程序。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器搜索并安装 `Furion` 包。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中（.NET 6 的主配置区域），添加 `builder.Services.AddInject();` 来注册 Furion 服务，并在构建应用后通过 `app.UseInject("api");` 来启用 Furion 的API功能。
4.  **启动应用**：完成配置后，即可运行项目并通过浏览器访问。
5.  **WebApplication 说明**：文档还特别说明了 `WebApplication` 对象在 .NET 6 中的使用，它是配置和运行应用的核心。

## 2.4 ASP.NET 7 集成
在 ASP.NET 7 项目中集成 Furion 框架的步骤与 .NET 6 基本一致，继续沿用 `Minimal API` 模式：
1.  **创建 Web 项目**：通过 Visual Studio 或 `dotnet new web` 命令创建 ASP.NET Core Web 应用（选择 .NET 7 框架）。
2.  **添加 Furion 依赖包**：使用 NuGet 包管理器安装 `Furion` 包。
3.  **Furion 基本配置**：
    *   编辑 `Program.cs` 文件。通过 `builder.Services.AddInject();` 添加 Furion 服务。
    *   在应用构建后（`var app = builder.Build();`之后），调用 `app.UseInject("api");` 来启用 Furion 的 API 功能。
4.  **启动应用**：配置完成后，运行项目即可。
5.  **WebApplication 说明**：与 .NET 6 类似，`WebApplication` 类是 .NET 7 中配置和运行应用的中心。

## 2.5 ASP.NET 8 集成
在 ASP.NET 8 项目中集成 Furion 框架的步骤与 .NET 6 和 .NET 7 非常相似，继续采用 `Minimal API` 模式进行开发：
1.  **创建 Web 项目**：使用 Visual Studio 或通过 `dotnet new web` 命令创建 ASP.NET Core Web 应用（确保选择 .NET 8 框架）。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器，搜索并安装 `Furion` 最新版本包。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中，通过 `builder.Services.AddInject();` 来注册 Furion 核心服务。
    *   在应用构建（`var app = builder.Build();`）之后，调用 `app.UseInject("api");` 以启用 Furion 的 API 功能。
4.  **启动应用**：完成上述步骤后，即可运行您的 ASP.NET 8 项目。
5.  **WebApplication 说明**：.NET 8 同样使用 `WebApplication` 类作为应用配置和运行的中心点。

## 2.6 ASP.NET 9 集成
在 ASP.NET 9 项目中集成 Furion 框架的步骤预计将延续 .NET 8 的 `Minimal API` 模式：
1.  **创建 Web 项目**：使用 Visual Studio 或通过 `dotnet new web` 命令创建 ASP.NET Core Web 应用（确保选择 .NET 9 框架预览版或正式版）。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器，搜索并安装与 .NET 9 兼容的 `Furion` 最新版本包。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中，通过 `builder.Services.AddInject();` 来注册 Furion 核心服务。
    *   在应用构建（`var app = builder.Build();`）之后，调用 `app.UseInject("api");` 以启用 Furion 的 API 功能。
4.  **启动应用**：完成上述步骤后，即可运行您的 ASP.NET 9 项目。
5.  **WebApplication 说明**：.NET 9 将继续使用 `WebApplication` 类作为应用配置和运行的中心点。

注意：由于 .NET 9 可能仍在开发或预览阶段，具体步骤请参考 Furion 框架针对 .NET 9 的最新官方文档。

## 2.7 ASP.NET 10 集成
在 ASP.NET 10 项目中集成 Furion 框架的步骤预计将与 .NET 9 类似，继续采用 `Minimal API` 模式：
1.  **创建 Web 项目**：使用 Visual Studio 或通过 `dotnet new web` 命令创建 ASP.NET Core Web 应用（确保选择 .NET 10 框架预览版或正式版）。
2.  **添加 Furion 依赖包**：通过 NuGet 包管理器，搜索并安装与 .NET 10 兼容的 `Furion` 最新版本包。
3.  **Furion 基本配置**：
    *   在 `Program.cs` 文件中，通过 `builder.Services.AddInject();` 来注册 Furion 核心服务。
    *   在应用构建（`var app = builder.Build();`）之后，调用 `app.UseInject("api");` 以启用 Furion 的 API 功能。
4.  **启动应用**：完成上述步骤后，即可运行您的 ASP.NET 10 项目。
5.  **WebApplication 说明**：.NET 10 将继续使用 `WebApplication` 类作为应用配置和运行的中心点。

注意：由于 .NET 10 可能仍在开发或预览阶段，具体步骤请参考 Furion 框架针对 .NET 10 的最新官方文档。

## 2.8 官方脚手架
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

## 2.9 手动搭建分层
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

## 2.10 神奇的 Inject
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

## 2.11 .NET5 升级 .NET6
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

## 2.12 .NET6 升级 .NET7
将基于 Furion 的 .NET 6 项目升级到 .NET 7 相对简单，因为两者都采用了相似的项目结构和 `Minimal API` 风格。主要步骤如下：

1.  **安装 .NET 7 SDK**：首先，确保您的开发环境中已安装 .NET 7 SDK。
2.  **编辑项目文件 (`.csproj`)**：
    *   将解决方案中所有项目的目标框架从 `net6.0` 修改为 `net7.0`。
3.  **升级 NuGet 包**：将 `Furion` 及其所有相关依赖项（如 `Furion.Extras.xxx`）升级到与 .NET 7 兼容的最新版本。建议查看 Furion 的更新日志以获取特定版本的兼容性信息。
4.  **重新编译**：完成上述更改后，清理并重新编译整个解决方案，以确保所有依赖项正确更新并且代码能够顺利编译。

由于 .NET 6 和 .NET 7 在项目模型上差异不大，通常不需要像从 .NET 5 升级那样修改 `Program.cs` 的启动代码结构，除非 Furion 的新版本针对 .NET 7 有特定的启动代码调整建议。

## 2.13 .NET7 升级 .NET8
将基于 Furion 的 .NET 7 项目升级到 .NET 8 过程较为平滑，因为 .NET 8 延续了 .NET 7 的 `Minimal API` 风格和项目结构。关键步骤包括：

1.  **安装 .NET 8 SDK**：确保您的开发环境中已安装 .NET 8 SDK。
2.  **编辑项目文件 (`.csproj`)**：
    *   将解决方案中所有项目的目标框架从 `net7.0` 修改为 `net8.0`。
3.  **升级 NuGet 包**：
    *   将 `Furion` 包及其所有 `Furion.Extras.xxx` 扩展包升级到与 .NET 8 兼容的最新版本。
    *   同时，也需要更新其他第三方依赖库到它们的 .NET 8 兼容版本。
4.  **重新编译**：完成上述更改后，清理并重新编译整个解决方案。
5.  **升级失败解决方案**：如果遇到升级问题，文档建议删除 `bin` 和 `obj` 目录，清除 NuGet 缓存 (`dotnet nuget locals all --clear`)，然后重新编译。

通常情况下，升级到 .NET 8 不需要对 `Program.cs` 中的 Furion 配置代码进行大的调整，除非 Furion 针对 .NET 8 推出了特定的新配置方式或有重大更改。

## 2.14 .NET8 升级 .NET9
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

## 2.15 .NET9 升级 .NET10
将基于 Furion 的 .NET 9 项目升级到 .NET 10 时，预计遵循与之前版本升级相似的步骤：

1.  **安装 .NET 10 SDK**：确保您的开发环境中已安装 .NET 10 SDK（预览版或正式版，一旦可用）。
2.  **编辑项目文件 (`.csproj`)**：
    *   将解决方案中所有项目的目标框架从 `net9.0` 修改为 `net10.0`。
3.  **升级 NuGet 包**：
    *   将 `Furion` 包及其所有 `Furion.Extras.xxx` 扩展包升级到与 .NET 10 兼容的最新版本。
    *   同时，更新其他第三方依赖库至其 .NET 10 兼容版本。
4.  **重新编译**：完成上述更改后，清理并重新编译整个解决方案。
5.  **升级失败解决方案**：如升级过程中遇到问题，文档通常建议删除 `bin` 和 `obj` 目录，清理 NuGet 缓存（例如，通过 `dotnet nuget locals all --clear` 命令），然后再次尝试编译。

重要提示：由于 .NET 10 尚处于早期阶段或未正式发布，具体的迁移步骤和潜在的重大更改需密切关注 Microsoft 和 Furion 框架的官方公告和最新文档。

## 2.16 GlobalUsing 使用
C# 10 和 .NET 6 引入了 `global using` 指令，允许开发者在项目级别定义全局命名空间，从而避免在每个文件中重复编写大量 `using` 语句。Furion 框架充分利用了此特性以简化代码。

1.  **关于 GlobalUsing**：
    *   `global using` 是一种在整个项目中生效的 `using` 指令。
    *   它可以定义在任何 `.cs` 文件中，但通常建议集中存放在一个或多个特定文件（如 `GlobalUsings.cs`）中，或直接在 `.csproj` 项目文件中定义。

2.  **必要配置**（主要针对 .NET 6 及更高版本）：
    *   此功能默认在 .NET 6+ 项目中启用。
    *   Furion 框架会自动包含一组常用的全局 `using`。

3.  **基本使用**：
    *   开发者可以在项目的任何 `.cs` 文件顶部（通常是 `GlobalUsings.cs` 或 `Program.cs`）使用 `global using <命名空间>;` 来声明全局命名空间。
    *   **默认全局 using**：Furion 框架及 ASP.NET Core 默认会隐式包含一些全局命名空间（如 `System`, `System.Linq`, `Microsoft.AspNetCore.Builder` 等），这些通常由 SDK 在项目构建时自动生成。开发者可以通过在 `.csproj` 文件中设置 `<ImplicitUsings>disable</ImplicitUsings>` 来禁用此行为。

4.  **.NET 5 项目开启支持**：
    *   虽然 `global using` 是 .NET 6 的特性，但通过在 .NET 5 项目的 `.csproj` 文件中设置 `<LangVersion>10</LangVersion>` 或更高（如 `preview`），并手动创建包含 `global using` 指令的 `.cs` 文件，也可以在 .NET 5 中使用此功能。

通过合理使用 `global using`，可以使代码文件更加整洁，减少冗余的 `using` 声明。

## 2.17 JSON Schema 使用
JSON Schema 是一种用于描述 JSON 数据结构的规范，它可以为 `appsettings.json` 等配置文件提供智能提示（IntelliSense）和验证功能，从而提高开发效率和配置准确性。

1.  **关于 JSON Schema**：
    *   它定义了 JSON 数据的结构、类型、约束等元数据。
    *   在 IDE（如 Visual Studio, VS Code）中，当 `appsettings.json` 文件关联了对应的 JSON Schema 后，编辑器能提供自动补全、属性说明提示和格式验证。

2.  **框架提供**：
    *   Furion 框架为其核心配置以及一些常用模块的配置提供了预定义的 JSON Schema 文件。
    *   这些 Schema 文件通常托管在公共可访问的 URL（如 `furion.net` 或 `gitee.com` 上的静态资源）。

3.  **如何使用**：
    *   **Visual Studio**：通常在 `appsettings.json` 文件的顶部，会有一个 `$schema` 属性。将此属性的值设置为 Furion 提供的对应 Schema URL 即可启用。例如：`"$schema": "https://furion.net/schemas/v4/furion-schema.json"`。VS 会自动下载并缓存此 Schema。
    *   **Visual Studio Code**：VS Code 也能识别 `$schema` 属性。或者，可以通过安装特定的 JSON 插件（如 YAML by Red Hat）并在用户或工作区设置中配置 `json.schemas` 来关联 Schema 文件。

4.  **JSON Schema 失效解决**：
    *   **Visual Studio**：
        *   检查 Schema URL 是否正确且可访问。
        *   尝试清除 VS 的 Schema 缓存（通常位于 `%APPDATA%\Microsoft\VisualStudio\<VS_Version>\JSON\Schemas` 或类似路径，或通过 VS 选项查找）。
        *   重启 Visual Studio。
    *   **Visual Studio Code**：
        *   验证 `$schema` 路径或 `json.schemas` 配置是否正确。
        *   检查网络连接，确保可以访问 Schema URL。
        *   重启 VS Code 或重新加载窗口。

5.  **如何更新 JSON Schema**：
    *   当 Furion 框架版本更新，其 JSON Schema 也可能更新。
    *   **Visual Studio**：通常会自动检测并提示更新，或者可以手动删除旧的缓存 Schema 文件，让 VS 重新下载。
    *   **Visual Studio Code**：如果 Schema URL 指向的是一个版本化的路径（如 `v4/furion-schema.json`），则在新版本发布后，需要手动更新该 URL。如果 URL 是一个始终指向最新版本的链接，则可能需要清除编辑器缓存或重启来获取更新。

通过为 `appsettings.json` 等配置文件关联正确的 JSON Schema，可以极大地提升配置编写的体验和准确性。

## 2.18 Visual Studio 高效率
为了在 Visual Studio 中更高效地开发 Furion 项目，可以利用以下技巧和设置：

1.  **开启内联参数提示**：
    *   在 Visual Studio 的 `工具` -> `选项` -> `文本编辑器` -> `C#` -> `高级` (或 `IntelliCode`) 中，启用“显示内联参数名称提示”和“显示内联类型提示”。这有助于在调用方法时直接看到参数名和类型，增强代码可读性。

2.  **开启全局智能提示 (IntelliCode)**：
    *   确保 Visual Studio IntelliCode 扩展已启用。它可以提供基于 AI 的增强型智能提示，预测最可能使用的代码成员。
    *   在 `工具` -> `选项` -> `IntelliCode` -> `常规` 中，可以管理其设置，如“C# 建议”。

3.  **实时显示诊断错误**：
    *   在 `工具` -> `选项` -> `文本编辑器` -> `C#` -> `高级` 中，将“以完整解决方案分析为背景分析范围”设置为“当前文档”或“打开的文档”，以获得更实时的错误和警告反馈，避免等待整个解决方案分析。

4.  **中文智能提示**：
    *   Furion 框架的 XML 文档注释支持中文。确保 Visual Studio 的语言设置或相关区域设置能正确显示中文，以便在智能提示中看到中文注释。

5.  **高效代码搜索**：
    *   熟练使用 Visual Studio 的代码搜索功能（快捷键通常是 `Ctrl + T` 或 `Ctrl + ,`），可以快速导航到文件、类型、成员和符号。

通过以上设置和技巧，可以提升在 Visual Studio 中使用 Furion 框架进行开发时的编码效率和体验。

## 2.19 NuGet 本地调试包
在开发或调试 Furion 框架或其相关 NuGet 包时，使用本地调试包是一种常见的做法。这允许开发者在本地测试未经发布的包版本。

1.  **关于本地测试包**：
    *   本地测试包通常是开发者在本地修改或构建的 NuGet 包（`.nupkg` 文件），用于在实际项目中测试这些更改，然后再发布到公共 NuGet 源。
    *   Furion 框架的源码编译后也会生成此类包。

2.  **如何配置**：
    *   **测试包命名规则**：Furion 的测试包通常会在版本号后附加如 `-alpha.时间戳` 或类似标识，以区别于正式发布的稳定版本。
    *   **配置本地包源**：
        *   创建一个本地文件夹，用于存放这些 `.nupkg` 文件（例如 `D:\LocalNuGet`）。
        *   **在 Visual Studio 中配置路径**：
            1.  打开 Visual Studio，进入 `工具` -> `选项` -> `NuGet 包管理器` -> `程序包源`。
            2.  点击“+”号添加新的包源。
            3.  在下方“名称”处填写一个自定义名称（如 "Furion Local"）。
            4.  在“源”处填写或浏览到你创建的本地文件夹路径。
            5.  点击“更新”并“确定”。
    *   **选择测试版安装或更新**：
        *   在 Visual Studio 的 NuGet 包管理器界面中，确保选中“包括预发行版”复选框。
        *   在“程序包源”下拉列表中选择你配置的本地源。
        *   此时，你可以搜索并安装或更新到本地文件夹中的测试包版本。

3.  **Visual Studio 调试 NuGet 包**：
    *   要单步调试本地 NuGet 包中的代码，需要确保该包的 `.pdb` (程序数据库) 文件与 `.dll` 文件一同存在于包中，并且被正确加载。
    *   在 Visual Studio 的调试选项 (`工具` -> `选项` -> `调试` -> `常规`) 中：
        *   取消选中“启用‘仅我的代码’”选项。
        *   启用“启用源链接支持”和“要求源文件与原始版本完全匹配”。
    *   在 `调试` -> `符号` 选项中，可以添加符号文件 (`.pdb`) 的位置，或者确保 NuGet 包源的符号服务器已启用（如果适用）。
    *   如果 Furion 源码在你本地，并且项目直接引用了这些源码项目，则可以直接调试。如果引用的是编译后的本地 NuGet 包，确保 `.pdb` 文件可用是关键。

通过以上配置，开发者可以方便地在本地环境中测试和调试 NuGet 包，加快开发和问题修复的进程。
