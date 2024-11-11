![.NET Conf 2024 Banner](cfc-banner-dark.png)

# .NET Conf 2024

* https://github.com/dotnetConf/2024
* https://github.com/dotnetConf/FocusOnAI_24

## Agenda

https://devblogs.microsoft.com/dotnet/dotnet-conf-2024-celebrating-the-release-of-dotnet-9-save-the-date/

## Personal Highlights

The `⭐` indicates my personal highlights. And the `🔥` indicates the most important features for me.

## C#

https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-13

* 🔥⭐ params collections - You can now use params with any recognized collection type, including System.Span<T>, System.ReadOnlySpan<T>, and types that implement System.Collections.Generic.IEnumerable<T> and have an Add method.
* 🔥⭐ New lock object - The C# lock statement recognizes if the target of the lock is a Lock object.
* Implicit index access in initializers
* ref and unsafe in iterators and async methods
* allows ref struct
* More partial members

## Runtime 

https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-9/runtime

* 🔥⭐ Features switches with support for trimming and AOT scenarios (good for library developers)
* 🔥⭐ GC - Datas by default (from .NET 8) - DATAS helps most with "bursty" workloads where the heap size should be adjusted according to how demanding the workload is, particularly as demand decreases.
* 🔥⭐ Performance improvements
  * Many more...
  * E.g:New exception hanlding - The new exception handling implementation is 2-4 times faster, per some exception handling micro-benchmarks. 

## Libraries

https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-9/libraries

* Collections
  * 🔥⭐ LINQ: `CountyBy` and `AggregateBy`, `Index<TSource>`
  * `Dictionary<TKey,TValue>.GetAlternateLookup` - lookp based on span
  * 🔥⭐`OrderedDictionary<TKey, TValue>`
  * `PriorityQueue.Remove()`
  * 🔥⭐`ReadOnlySet<T>`
* Cryptography
* 🔥⭐`Base64Url`
* `BinaryFormatter` removed
* System.Text.Json
    * 🔥⭐ JSON Sceham Exporter
    * JsonReader support reading multiple json documents, can be useful in jsonl, it also has streaming possible `JsonSerializer.DeserializeAsyncEnumerable`
    * Respect nullable annotations - futher nullable support wihh `RespectNullableAnnotations`, `RespectRequiredConstructorParameters`, there is a feature switch to turn this globally.
    * Customizing enum member names
    * Customizing indentation
    * JsonObject property order manipulation
    * DeepEquals methods in JsonElement and JsonNode
    * Performance improvements
* Diagnostics
  * Debug.Assert reports assert condition
  * 🔥⭐New Activity.AddLink method (good for Otel)
  * Out-of-proc Meter wildcard listening
  * Logging source generator for partial classes with primary constructors
* Networking
  * SocketsHttpHandler is default in HttpClientFactory
  * System.Net.ServerSentEvents (used by OpenAI to stream text), protocal on top of HTTP
  * `TLS resume` with client certificates on Linux
  * WebSocket keep-alive ping and timeout
  * HttpClientFactory no longer logs header values by default
* Reflection
  * PersistedAssemblyBuilder 
  * TypeName is a parser for ECMA-335 type names that provides much the same functionality as System.Type 
* Regular expressions
  * `[GeneratedRegex]` on properties, because C# 13 supports partial properties (on mehtods it was available since .NET 7)
  * `Regex.EnumerateSplits` instead of `Regex.Split` for no allocations
* 🔥⭐ System.Guid V7 - which "features a time-ordered value field derived from the widely implemented and well-known Unix Epoch timestamp source".
* System.IO - Starting in .NET 9 use zlib-ng
* New `Tensor<T>` type - good for AI - Represent and encode data such as text sequences (tokens), images, video, and audio; Efficiently manipulate higher-dimensional data.
* Threading
  * 🔥⭐ `Task.WhenEach`
  * Prioritized unbounded channel for `System.Threading.Channels`

## SDK

https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-9/sdk

* Run tests in parallel
* Terminal logger test display
* ⭐.NET tool roll-forward
* 🔥⭐Terminal logger
  * Clickable links, Duration timers for MSBuild tasks, Color coding of warning and error messages, The terminal logger now summarizes the total count of failures and warnings at the end of a build. It also shows errors that contain newlines.
* 🔥⭐ NuGet security audits

## ASP.NET Core

https://learn.microsoft.com/en-us/aspnet/core/release-notes/aspnetcore-9.0?view=aspnetcore-9.0

* Blazor
  * .NET MAUI Blazor Hybrid and Web App solution template
  * Static asset delivery optimization
  * Improved server-side reconnection experience:
  * Simplified authentication state serialization for Blazor Web Apps
  * Add static server-side rendering (SSR) pages to a globally-interactive Blazor Web App
  * ⭐ Constructor injection
  * Websocket compression for Interactive Server components
  * ⭐ Handle keyboard composition events in Blazor
* SignalR
  * Polymorphic type support in SignalR Hubs
  * 🔥⭐ Improved Activities for SignalR
  * SignalR supports trimming and Native AOT - Continuing the Native AOT journey started in .NET 8, we have enabled trimming and native ahead-of-time (AOT) compilation support for both SignalR client and server scenarios. With limitations*
* Minimal APIs
  * 🔥⭐ Added InternalServerError and InternalServerError<TValue> to TypedResults
  * Call `ProducesProblem` and `ProducesValidationProblem` on route groups
  * `Problem` and `ValidationProblem` result types support construction with `IEnumerable<KeyValuePair<string, object?>>` values
* OpenAPI
  * 🔥⭐ Built-in support for OpenAPI document generation via the `Microsoft.AspNetCore.OpenApi` package
  * 🔥⭐ OpenAPI documents can also be generated at build-time by adding the `Microsoft.Extensions.ApiDescription.Server` package
  * `Microsoft.AspNetCore.OpenApi` supports trimming and Native AOT (interesting)
* Authentication and authorization
  * OpenIdConnectHandler adds support for Pushed Authorization Requests (PAR)
  * OIDC and OAuth Parameter Customization
  * Configure HTTP.sys extended authentication flags
* 🔥⭐ New HybridCache library - `Microsoft.Extensions.Caching.Hybrid` (probably not mature as `HybridCache` anyway)
* ⭐ Developer exception page improvements
* Optimize static web asset delivery
* ExceptionHandlerMiddleware option to choose the status code based on the exception type
* ⭐ Opt-out of HTTP metrics on certain endpoints and requests
* ⭐ Middleware supports Keyed DI
* ⭐ Trust the ASP.NET Core HTTPS development certificate on Linux

## Aspire

https://learn.microsoft.com/en-us/dotnet/aspire/whats-new/dotnet-aspire-9-release-candidate-1?tabs=windows&pivots=dotnet-cli

* 🔥⭐ You no longer need a .NET workload. Instead, add the 📦 Aspire.AppHost.Sdk
* 🔥⭐ Manage resource lifecycle
* ⭐ Health checks in resource details
* 🔥⭐ Persistent containers
* 🔥⭐ Resource commands, including - restart command
* ⭐ Azure Functions Support (Preview)
* Mobile and responsive support
* Sensitive properties, volumes
* Colorful console log
* Container networking
* Eventing model
* More integrations

## AI

* `ML.NET` - 4.0
* 🔥⭐ `Microsoft.Extensions.AI` Preview
* Official `OpenAI` library has been released

## EF

https://learn.microsoft.com/en-us/ef/core/what-is-new/ef-core-9.0/whatsnew

* Azure Cosmos DB for NoSQL
* 🔥⭐ AOT and pre-compiled queries - there is a lot of work going on behind the scenes to allow EF Core to run without just-in-time (JIT) compilation. Instead, EF compile ahead-of-time (AOT) everything needed to run queries in the application.
* ⭐ LINQ and SQL translation
* Complex types: GroupBy and ExecuteUpdate support
* Prune unneeded elements from SQL
* And many more
* ⭐ Improved data seeding - `UseAsyncSeeding` - The new seeding methods are called as part of `EnsureCreated` operation, `Migrate` and `dotnet ef database update`
* Auto-compiled models - MSBuild integration
* Read-only primitive collections
* Make existing model building conventions more extensible

## References

* https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-9/overview
* https://devblogs.microsoft.com/dotnet/dotnet-9-rc-2/
* https://devblogs.microsoft.com/dotnet/dotnet-9-release-candidate-1-is-now-available/
* https://devblogs.microsoft.com/dotnet/system-text-json-in-dotnet-9/
* https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-13
* https://learn.microsoft.com/en-us/aspnet/core/release-notes/aspnetcore-9.0?view=aspnetcore-9.0
* https://learn.microsoft.com/en-us/ef/core/what-is-new/ef-core-9.0
* https://learn.microsoft.com/en-us/dotnet/maui/whats-new/dotnet-9?view=net-maui-8.0
* https://devblogs.microsoft.com/dotnet/introducing-microsoft-extensions-ai-preview/
* https://devblogs.microsoft.com/dotnet/announcing-the-stable-release-of-the-official-open-ai-library-for-dotnet/
* https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-9/
* https://devblogs.microsoft.com/dotnet/binaryformatter-removed-from-dotnet-9/

