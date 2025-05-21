# 应用启动

## 3.1 AppStartup 启动
Furion 框架支持通过 `AppStartup` 类来配置和管理应用的启动过程。这种方式允许开发者在一个集中的位置定义服务注册和中间件配置。

主要特点和用法：
- **集中配置**：`AppStartup` 类作为应用启动的配置中心，可以在其中调用 `ConfigureServices` 方法注册服务，调用 `Configure` 方法配置 HTTP 请求管道。
- **生命周期方法**：`AppStartup` 提供了如 `PreConfigureServices`, `PostConfigureServices`, `PreConfigure`, `PostConfigure` 等方法，允许在 Furion 框架核心服务注册和配置的不同阶段插入自定义逻辑。
- **自定义顺序**：可以通过 `[AppStartup(Order = n)]` 特性来控制多个 `AppStartup` 类的执行顺序。
- **模块化**：可以将不同模块的启动配置分散到各自的 `AppStartup` 类中，实现更好的代码组织。

使用 `AppStartup` 可以使项目启动逻辑更加清晰和结构化。

## 3.2 组件化启动
组件化启动是 Furion 框架推荐的一种更高级、更灵活的应用启动配置方式。它允许将应用的功能模块化为独立的“组件”，每个组件可以有自己的服务注册和中间件配置。

主要特点和用法：
- **定义组件**：创建一个类并实现 `IApplicationComponent` 接口（或继承 `ApplicationComponent` 基类）。
- **组件生命周期**：
    - `Load(IApplicationBuilder app, IWebHostEnvironment env, ComponentContext componentContext)`: 在此方法中配置组件的中间件。
    - `ConfigureServices(IServiceCollection services, IWebHostEnvironment env, ComponentContext componentContext)`: 在此方法中注册组件所需的服务。
- **自动发现和加载**：Furion 框架会自动扫描项目中所有实现了 `IApplicationComponent` 的组件，并按照它们之间的依赖关系（通过 `[DependsOn(typeof(OtherComponent))]` 特性定义）和指定的顺序（通过 `[Component(Order = n)]` 特性定义）进行加载和配置。
- **解耦与复用**：组件化有助于实现功能模块的高度解耦，使得组件更容易在不同项目中复用。
- **配置注入**：组件上下文 `ComponentContext` 允许传递和共享配置信息。

组件化启动是构建大型、模块化应用的理想选择，它能有效提升项目的可维护性和扩展性。
