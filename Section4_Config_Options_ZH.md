# 配置与选项

## 4.1 配置
Furion 框架强调“约定大于配置，配置大于硬编码”的原则。它利用 ASP.NET Core 的配置系统，主要通过 `appsettings.json` 文件进行管理。

主要特点和用法：
- **`appsettings.json`**：核心配置文件，支持不同环境（如 `appsettings.Development.json`）的特定配置。
- **读取配置**：框架提供了多种便捷方式读取配置，如通过 `App.Configuration` 静态属性，或依赖注入 `IConfiguration`。
- **强类型配置**：可以将配置绑定到强类型对象上，便于管理和使用。
- **Furion特定配置**：框架自身有许多预定义的配置节，用于控制各种模块的行为，如数据库连接、日志、JWT、Swagger等。这些配置通常有默认值，开发者可以按需覆盖。
- **环境变量和命令行参数**：ASP.NET Core 的配置系统也支持从环境变量和命令行参数加载配置，它们可以覆盖文件中的设置。

## 4.2 选项
Furion 框架大量使用“选项模式”（Options Pattern）来管理和使用配置，使得配置的消费更加面向对象和类型安全。

主要特点和用法：
- **选项类**：为特定的配置节定义强类型 C# 类（通常以 `Options` 或 `Settings` 结尾）。
- **注册选项**：在服务容器中注册这些选项类，通常在 `ConfigureServices` 方法中通过 `services.Configure<MyOptions>(Configuration.GetSection("MySection"))` 或 Furion 提供的便捷方法进行。
- **使用选项**：通过依赖注入 `IOptions<MyOptions>`、`IOptionsSnapshot<MyOptions>` 或 `IOptionsMonitor<MyOptions>` 来在服务或控制器中访问配置。
    - `IOptions<TOptions>`：提供单例的选项实例，配置在应用启动时加载一次。
    - `IOptionsSnapshot<TOptions>`：提供作用域（Scoped）的选项实例，每次请求会获取最新的配置，适合需要读取请求期间可能变化的配置。
    - `IOptionsMonitor<TOptions>`：提供单例服务，可以监听配置变化并实时更新选项实例。
- **可配置选项 (`IConfigurableOptions`)**：Furion 提供了 `IConfigurableOptions<TOptions>` 接口，允许在运行时动态修改选项值，这对于某些需要程序化调整配置的场景非常有用。

选项模式提高了配置的可维护性、可测试性，并使得配置的消费更加符合面向对象的原则。
