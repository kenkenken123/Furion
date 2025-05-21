# 规范化接口文档 (Swagger)

## 6.1 什么是接口文档
接口文档是描述应用程序编程接口（API）功能、请求方式、参数、返回数据结构等信息的文档，是前后端开发协作、API使用者理解和集成API的重要依据。

## 6.2 为什么要写接口文档
编写接口文档有助于：
- **明确契约**：清晰定义前后端或不同服务间的交互约定。
- **提高协作效率**：减少沟通成本，方便团队成员理解和使用API。
- **便于测试**：为API测试提供依据。
- **方便维护**：API变更时，文档可以同步更新，降低维护难度。
- **对外开放**：如果是公开API，文档是吸引和帮助第三方开发者的关键。

## 6.3 为什么需要规范化文档
规范化的接口文档能带来诸多好处：
- **一致性**：所有API遵循统一的描述风格和结构，易于阅读和理解。
- **准确性**：减少因描述模糊或不一致导致的误解。
- **自动化**：规范化的文档更容易被工具解析，用于自动生成代码、测试用例或客户端SDK。
- Furion强调以下规范：协议规范 (HTTP/HTTPS)、接口路径规范 (RESTful)、版本控制规范、接口命名规范、请求参数规范 (驼峰、蛇形等)、返回数据规范。

## 6.4 什么是 Swagger (OpenAPI)
Swagger (现称 OpenAPI Specification) 是一种用于描述、生成、可视化和使用 RESTful Web 服务的语言无关的规范。它允许开发者和机器都能理解API的功能，而无需访问源代码、文档或进行网络流量检查。

## 6.5 Swagger 使用
Furion 框架深度集成了 Swagger (Swashbuckle.AspNetCore)，提供了丰富的配置选项来生成和定制API文档。

主要配置和使用方式：
- **注册服务**：通过 `services.AddInject()` 或更细致的 `AddSpecificationDocuments()` 方法在 `Program.cs` (或 .NET 5的 `Startup.cs`) 中注册 Swagger 服务。
- **默认地址**：通常 Swagger UI 界面可以通过 `/swagger` 路径访问。
- **文档注释**：通过在代码中编写 XML 文档注释（如 `<summary>`, `<remarks>`, `<param>`, `<returns>`），这些注释会自动包含在 Swagger 文档中。
- **多分组支持**：可以将 API 按模块或功能划分到不同的分组中，方便管理和查阅。通过特性 `[ApiDescriptionSettings(Tag = "分组名")]` 或配置实现。
- **排序**：支持对分组、控制器及方法进行排序。
- **授权控制**：可以配置 Swagger UI 支持 JWT Bearer Token 等授权方式，方便在线测试需要授权的接口。
- **在线测试**：Swagger UI 提供了直接在线调用和测试 API 的功能。
- **生产环境关闭**：通常建议在生产环境中禁用 Swagger UI，可以通过配置或条件编译实现。
- **自定义配置**：Furion 允许通过 `SpecificationDocumentSettingsOptions` 或直接操作 `SwaggerGenOptions` 和 `SwaggerUIOptions` 进行深度自定义，如修改文档标题、添加自定义JS/CSS、配置SchemaId、OperationId等。
- **统一返回值模型**：Furion 的规范化结果功能会自动调整 Swagger 文档中的响应类型，以反映真实的返回数据结构。

## 6.6 SpecificationDocumentSettings 配置
Furion 提供 `SpecificationDocumentSettingsOptions` 类来集中管理 Swagger 文档的各种配置，如文档信息、服务器地址、安全定义等。这些配置通常在 `appsettings.json` 中或通过代码进行设置。

## 6.7 统一返回值模型/规范化结果/API 返回值
Furion 框架提倡使用统一的API返回值模型，即“规范化结果”。这有助于前端和客户端以一致的方式处理API响应。

- **自动处理**：框架会自动将控制器的返回结果包装在统一的响应结构中（通常包含成功状态、数据、错误码、消息等字段）。
- **Swagger 适配**：Swagger 文档会自动适配这种规范化结果，正确显示最终的响应数据结构。
- **排除规范化**：可以通过特性 `[NonUnify]` 来使特定接口或控制器不使用规范化结果处理。

## 6.8 支持多套规范化配置
Furion 允许定义多套不同的规范化结果配置，并按需应用于不同的API或模块，以满足复杂场景下的需求。

## 6.9 针对特定控制器或特定方法配置序列化选项
在某些情况下，可能需要为特定的API接口或控制器配置不同于全局设置的JSON序列化选项（如日期格式、大小写等）。Furion 提供了实现这一需求的机制，例如通过返回特定的 `JsonResult` 并指定其序列化选项，或者注册多套具名的序列化配置。
