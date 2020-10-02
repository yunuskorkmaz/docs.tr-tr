---
title: .NET 'te günlüğe kaydetme sağlayıcıları
description: Günlüğe kaydetme sağlayıcısı API 'sinin .NET uygulamalarında nasıl kullanıldığını öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.openlocfilehash: 3bd10564f23744d4798d0a6a4b49a7a29be2bc19
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654685"
---
# <a name="logging-providers-in-net"></a><span data-ttu-id="38f51-103">.NET 'te günlüğe kaydetme sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="38f51-103">Logging providers in .NET</span></span>

<span data-ttu-id="38f51-104">Günlüğe kaydetme sağlayıcıları, `Console` yalnızca günlükleri standart çıkış olarak görüntüleyen sağlayıcı dışında günlükleri kalıcı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="38f51-104">Logging providers persist logs, except for the `Console` provider, which only displays logs as standard output.</span></span> <span data-ttu-id="38f51-105">Örneğin, Azure Application Insights sağlayıcısı günlükleri Azure Application Insights depolar.</span><span class="sxs-lookup"><span data-stu-id="38f51-105">For example, the Azure Application Insights provider stores logs in Azure Application Insights.</span></span> <span data-ttu-id="38f51-106">Birden çok sağlayıcı etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="38f51-106">Multiple providers can be enabled.</span></span>

<span data-ttu-id="38f51-107">Varsayılan .NET Worker uygulama şablonları:</span><span class="sxs-lookup"><span data-stu-id="38f51-107">The default .NET Worker app templates:</span></span>

- <span data-ttu-id="38f51-108">[Genel Konağı](generic-host.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f51-108">Use the [Generic Host](generic-host.md).</span></span>
- <span data-ttu-id="38f51-109"><xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>Aşağıdaki günlük sağlayıcılarını ekleyen çağırın:</span><span class="sxs-lookup"><span data-stu-id="38f51-109">Call <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>, which adds the following logging providers:</span></span>
  - [<span data-ttu-id="38f51-110">Konsol</span><span class="sxs-lookup"><span data-stu-id="38f51-110">Console</span></span>](#console)
  - [<span data-ttu-id="38f51-111">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="38f51-111">Debug</span></span>](#debug)
  - [<span data-ttu-id="38f51-112">EventSource</span><span class="sxs-lookup"><span data-stu-id="38f51-112">EventSource</span></span>](#event-source)
  - <span data-ttu-id="38f51-113">[EventLog](#windows-eventlog): yalnızca Windows</span><span class="sxs-lookup"><span data-stu-id="38f51-113">[EventLog](#windows-eventlog): Windows only</span></span>

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

<span data-ttu-id="38f51-114">Yukarıdaki kod, `Program` .NET çalışan uygulama şablonlarıyla oluşturulan sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="38f51-114">The preceding code shows the `Program` class created with the .NET Worker app templates.</span></span> <span data-ttu-id="38f51-115">Sonraki birkaç bölüm, genel ana bilgisayarı kullanan .NET Worker uygulama şablonlarına göre örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="38f51-115">The next several sections provide samples based on the .NET Worker app templates, which use the Generic Host.</span></span>

<span data-ttu-id="38f51-116">Tarafından eklenen varsayılan günlük sağlayıcıları kümesini geçersiz kılmak için `Host.CreateDefaultBuilder` , istediğiniz `ClearProviders` günlüğe kaydetme sağlayıcılarını çağırın ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38f51-116">To override the default set of logging providers added by `Host.CreateDefaultBuilder`, call `ClearProviders` and add the logging providers you want.</span></span> <span data-ttu-id="38f51-117">Örneğin, aşağıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="38f51-117">For example, the following code:</span></span>

- <span data-ttu-id="38f51-118"><xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A>Oluşturucunun tüm örneklerini kaldırmak için çağırır <xref:Microsoft.Extensions.Logging.ILoggerProvider> .</span><span class="sxs-lookup"><span data-stu-id="38f51-118">Calls <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> to remove all the <xref:Microsoft.Extensions.Logging.ILoggerProvider> instances from the builder.</span></span>
- <span data-ttu-id="38f51-119">[Konsol](#console) günlüğü sağlayıcısını ekler.</span><span class="sxs-lookup"><span data-stu-id="38f51-119">Adds the [Console](#console) logging provider.</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

<span data-ttu-id="38f51-120">Ek sağlayıcılar için bkz.:</span><span class="sxs-lookup"><span data-stu-id="38f51-120">For additional providers, see:</span></span>

- <span data-ttu-id="38f51-121">[Yerleşik günlük oluşturma sağlayıcıları](#built-in-logging-providers).</span><span class="sxs-lookup"><span data-stu-id="38f51-121">[Built-in logging providers](#built-in-logging-providers).</span></span>
- <span data-ttu-id="38f51-122">[Üçüncü taraf günlüğü sağlayıcıları](#third-party-logging-providers).</span><span class="sxs-lookup"><span data-stu-id="38f51-122">[Third-party logging providers](#third-party-logging-providers).</span></span>

## <a name="configure-a-service-that-depends-on-ilogger"></a><span data-ttu-id="38f51-123">ILogger 'a bağlı bir hizmet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="38f51-123">Configure a service that depends on ILogger</span></span>

<span data-ttu-id="38f51-124">Bağımlı olan bir hizmeti yapılandırmak için `ILogger<T>` , Oluşturucu ekleme veya bir fabrika yöntemi sağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f51-124">To configure a service that depends on `ILogger<T>`, use constructor injection or provide a factory method.</span></span> <span data-ttu-id="38f51-125">Fabrika yöntemi yaklaşımı yalnızca başka bir seçenek yoksa önerilir.</span><span class="sxs-lookup"><span data-stu-id="38f51-125">The factory method approach is recommended only if there is no other option.</span></span> <span data-ttu-id="38f51-126">Örneğin, DI tarafından sağlanmış bir örneğe ihtiyacı olan bir hizmeti düşünün `ILogger<T>` :</span><span class="sxs-lookup"><span data-stu-id="38f51-126">For example, consider a service that needs an `ILogger<T>` instance provided by DI:</span></span>

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

<span data-ttu-id="38f51-127">Yukarıdaki kod, dı kapsayıcısının bir örneğini oluşturmak için ilk kez çalışan bir [Func<Iservıceprovider, ıexampleservice>](/dotnet/api/system.func-2) `IExampleService` .</span><span class="sxs-lookup"><span data-stu-id="38f51-127">The preceding code is a [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) that runs the first time the DI container needs to construct an instance of `IExampleService`.</span></span> <span data-ttu-id="38f51-128">Kayıtlı hizmetlerden herhangi birine bu şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38f51-128">You can access any of the registered services in this way.</span></span>

## <a name="built-in-logging-providers"></a><span data-ttu-id="38f51-129">Yerleşik günlük oluşturma sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="38f51-129">Built-in logging providers</span></span>

<span data-ttu-id="38f51-130">Microsoft uzantıları, çalışma zamanı kitaplıklarının bir parçası olarak aşağıdaki günlük sağlayıcılarını içerir:</span><span class="sxs-lookup"><span data-stu-id="38f51-130">Microsoft Extensions include the following logging providers as part of the runtime libraries:</span></span>

- [<span data-ttu-id="38f51-131">Konsol</span><span class="sxs-lookup"><span data-stu-id="38f51-131">Console</span></span>](#console)
- [<span data-ttu-id="38f51-132">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="38f51-132">Debug</span></span>](#debug)
- [<span data-ttu-id="38f51-133">EventSource</span><span class="sxs-lookup"><span data-stu-id="38f51-133">EventSource</span></span>](#event-source)
- [<span data-ttu-id="38f51-134">EventLog</span><span class="sxs-lookup"><span data-stu-id="38f51-134">EventLog</span></span>](#windows-eventlog)

<span data-ttu-id="38f51-135">Aşağıdaki günlük oluşturma sağlayıcıları Microsoft tarafından gönderilir, ancak çalışma zamanı kitaplıklarının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="38f51-135">The following logging providers are shipped by Microsoft, but not as part of the runtime libraries.</span></span> <span data-ttu-id="38f51-136">Bunların ek NuGet paketleri olarak yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="38f51-136">They must be installed as additional NuGet packages.</span></span>

- [<span data-ttu-id="38f51-137">AzureAppServicesFile ve AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="38f51-137">AzureAppServicesFile and AzureAppServicesBlob</span></span>](#azure-app-service)
- [<span data-ttu-id="38f51-138">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="38f51-138">ApplicationInsights</span></span>](#azure-application-insights)

### <a name="console"></a><span data-ttu-id="38f51-139">Konsol</span><span class="sxs-lookup"><span data-stu-id="38f51-139">Console</span></span>

<span data-ttu-id="38f51-140">`Console`Sağlayıcı çıktıyı konsola kaydeder.</span><span class="sxs-lookup"><span data-stu-id="38f51-140">The `Console` provider logs output to the console.</span></span>

### <a name="debug"></a><span data-ttu-id="38f51-141">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="38f51-141">Debug</span></span>

<span data-ttu-id="38f51-142">`Debug`Sağlayıcı, [System. Diagnostics. Debug](/dotnet/api/system.diagnostics.debug) sınıfını kullanarak günlük çıktısını yazar.</span><span class="sxs-lookup"><span data-stu-id="38f51-142">The `Debug` provider writes log output by using the [System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug) class.</span></span> <span data-ttu-id="38f51-143">`System.Diagnostics.Debug.WriteLine`Sağlayıcıya yazmak için çağrılar `Debug` .</span><span class="sxs-lookup"><span data-stu-id="38f51-143">Calls to `System.Diagnostics.Debug.WriteLine` write to the `Debug` provider.</span></span>

<span data-ttu-id="38f51-144">Linux 'ta, `Debug` sağlayıcı günlük konumu dağıtıma bağımlıdır ve aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="38f51-144">On Linux, the `Debug` provider log location is distribution-dependent and may be one of the following:</span></span>

- <span data-ttu-id="38f51-145">*/var/log/Message*</span><span class="sxs-lookup"><span data-stu-id="38f51-145">*/var/log/message*</span></span>
- <span data-ttu-id="38f51-146">*/var/log/Syslog*</span><span class="sxs-lookup"><span data-stu-id="38f51-146">*/var/log/syslog*</span></span>

### <a name="event-source"></a><span data-ttu-id="38f51-147">Olay Kaynağı</span><span class="sxs-lookup"><span data-stu-id="38f51-147">Event Source</span></span>

<span data-ttu-id="38f51-148">`EventSource`Sağlayıcı, adlı platformlar arası bir olay kaynağına Yazar `Microsoft-Extensions-Logging` .</span><span class="sxs-lookup"><span data-stu-id="38f51-148">The `EventSource` provider writes to a cross-platform event source with the name `Microsoft-Extensions-Logging`.</span></span> <span data-ttu-id="38f51-149">Windows 'da, sağlayıcı [ETW](/windows/win32/etw/event-tracing-portal)kullanır.</span><span class="sxs-lookup"><span data-stu-id="38f51-149">On Windows, the provider uses [ETW](/windows/win32/etw/event-tracing-portal).</span></span>

#### <a name="dotnet-trace-tooling"></a><span data-ttu-id="38f51-150">DotNet izleme araçları</span><span class="sxs-lookup"><span data-stu-id="38f51-150">dotnet trace tooling</span></span>

<span data-ttu-id="38f51-151">[DotNet-Trace](../diagnostics/dotnet-trace.md) Aracı, çalışan bir Işlemin .NET Core izlemelerinin toplanmasını sağlayan platformlar arası CLI genel aracıdır.</span><span class="sxs-lookup"><span data-stu-id="38f51-151">The [dotnet-trace](../diagnostics/dotnet-trace.md) tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process.</span></span> <span data-ttu-id="38f51-152">Araç, <xref:Microsoft.Extensions.Logging.EventSource> kullanarak sağlayıcı verilerini toplar <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource> .</span><span class="sxs-lookup"><span data-stu-id="38f51-152">The tool collects <xref:Microsoft.Extensions.Logging.EventSource> provider data using a <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource>.</span></span>

<span data-ttu-id="38f51-153">Bkz. yükleme yönergeleri için [DotNet-Trace](../diagnostics/dotnet-trace.md) .</span><span class="sxs-lookup"><span data-stu-id="38f51-153">See [dotnet-trace](../diagnostics/dotnet-trace.md) for installation instructions.</span></span> <span data-ttu-id="38f51-154">Kullanarak bir tanılama öğreticisi için `dotnet-trace` bkz. [.NET Core 'DA yüksek CPU kullanımı hata ayıklama](/../diagnostics/debug-highcpu.md).</span><span class="sxs-lookup"><span data-stu-id="38f51-154">For a diagnostic tutorial using `dotnet-trace`, see [Debug high CPU usage in .NET Core](/../diagnostics/debug-highcpu.md).</span></span>

### <a name="windows-eventlog"></a><span data-ttu-id="38f51-155">Windows olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="38f51-155">Windows EventLog</span></span>

<span data-ttu-id="38f51-156">`EventLog`Sağlayıcı, Windows olay günlüğüne günlük çıktısı gönderir.</span><span class="sxs-lookup"><span data-stu-id="38f51-156">The `EventLog` provider sends log output to the Windows Event Log.</span></span> <span data-ttu-id="38f51-157">Diğer sağlayıcılardan farklı olarak, `EventLog` sağlayıcı varsayılan sağlayıcı ***not*** olmayan ayarları uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="38f51-157">Unlike the other providers, the `EventLog` provider does ***not*** inherit the default non-provider settings.</span></span> <span data-ttu-id="38f51-158">`EventLog`Günlük ayarları belirtilmemişse, varsayılan olarak `LogLevel.Warning` .</span><span class="sxs-lookup"><span data-stu-id="38f51-158">If `EventLog` log settings aren't specified, they default to `LogLevel.Warning`.</span></span>

<span data-ttu-id="38f51-159">Olayları daha düşük günlüğe kaydetmek için <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType> , günlük düzeyini açık olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="38f51-159">To log events lower than <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType>, explicitly set the log level.</span></span> <span data-ttu-id="38f51-160">Aşağıdaki örnek, olay günlüğü varsayılan günlük düzeyini şu şekilde ayarlar <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="38f51-160">The following example sets the Event Log default log level to <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType>:</span></span>

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

<span data-ttu-id="38f51-161">[AddEventLog aşırı yüklemeleri](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) geçiş yapabilir <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings> .</span><span class="sxs-lookup"><span data-stu-id="38f51-161">[AddEventLog overloads](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) can pass in <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings>.</span></span> <span data-ttu-id="38f51-162">`null`Veya belirtilmemişse, aşağıdaki varsayılan ayarlar kullanılır:</span><span class="sxs-lookup"><span data-stu-id="38f51-162">If `null` or not specified, the following default settings are used:</span></span>

- <span data-ttu-id="38f51-163">`LogName`: "Uygulama"</span><span class="sxs-lookup"><span data-stu-id="38f51-163">`LogName`: "Application"</span></span>
- <span data-ttu-id="38f51-164">`SourceName`: ".NET çalışma zamanı"</span><span class="sxs-lookup"><span data-stu-id="38f51-164">`SourceName`: ".NET Runtime"</span></span>
- <span data-ttu-id="38f51-165">`MachineName`: Yerel makine adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38f51-165">`MachineName`: The local machine name is used.</span></span>

<span data-ttu-id="38f51-166">Aşağıdaki kod, ' `SourceName` nin varsayılan değerinden öğesini olarak değiştirir `".NET Runtime"` `CustomLogs` :</span><span class="sxs-lookup"><span data-stu-id="38f51-166">The following code changes the `SourceName` from the default value of `".NET Runtime"` to `CustomLogs`:</span></span>

```csharp
public class Program
{
    public static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddEventLog(configuration =>
                    configuration.SourceName = "CustomLogs"));
}
```

### <a name="azure-app-service"></a><span data-ttu-id="38f51-167">Azure App Service</span><span class="sxs-lookup"><span data-stu-id="38f51-167">Azure App Service</span></span>

<span data-ttu-id="38f51-168">[Microsoft. Extensions. Logging. AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) sağlayıcı paketi, günlükleri bir Azure App Service uygulamasının dosya sistemindeki metin dosyalarına ve bir Azure depolama hesabındaki [BLOB depolama](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) alanına yazar.</span><span class="sxs-lookup"><span data-stu-id="38f51-168">The [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) provider package writes logs to text files in an Azure App Service app's file system and to [blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) in an Azure Storage account.</span></span>

<span data-ttu-id="38f51-169">Sağlayıcı paketi çalışma zamanı kitaplıklarına dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="38f51-169">The provider package isn't included in the runtime libraries.</span></span> <span data-ttu-id="38f51-170">Sağlayıcıyı kullanmak için sağlayıcı paketini projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38f51-170">To use the provider, add the provider package to the project.</span></span>

<span data-ttu-id="38f51-171">Sağlayıcı ayarlarını yapılandırmak için <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions> Aşağıdaki örnekte gösterildiği gibi ve kullanın:</span><span class="sxs-lookup"><span data-stu-id="38f51-171">To configure provider settings, use <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> and <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, as shown in the following example:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddAzureWebAppDiagnostics())
            .ConfigureServices(services =>
                services.Configure<AzureFileLoggerOptions>(options =>
                {
                    options.FileName = "azure-diagnostics-";
                    options.FileSizeLimit = 50 * 1024;
                    options.RetainedFileCountLimit = 5;
                })
                .Configure<AzureBlobLoggerOptions>(options =>
                {
                    options.BlobName = "log.txt";
                }));
}
```

<span data-ttu-id="38f51-172">Uygulama Azure App Service dağıtıldığında, Azure portal **App Service** sayfasının [App Service Günlükler](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) bölümündeki ayarları kullanır.</span><span class="sxs-lookup"><span data-stu-id="38f51-172">When deployed to Azure App Service, the app uses the settings in the [App Service logs](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) section of the **App Service** page of the Azure portal.</span></span> <span data-ttu-id="38f51-173">Aşağıdaki ayarlar güncelleştirilirken, değişiklikler uygulamanın yeniden başlatılmasını veya yeniden dağıtımı gerekmeden hemen etkili olur.</span><span class="sxs-lookup"><span data-stu-id="38f51-173">When the following settings are updated, the changes take effect immediately without requiring a restart or redeployment of the app.</span></span>

- <span data-ttu-id="38f51-174">**Uygulama günlüğü (dosya sistemi)**</span><span class="sxs-lookup"><span data-stu-id="38f51-174">**Application Logging (Filesystem)**</span></span>
- <span data-ttu-id="38f51-175">**Uygulama günlüğü (blob)**</span><span class="sxs-lookup"><span data-stu-id="38f51-175">**Application Logging (Blob)**</span></span>

<span data-ttu-id="38f51-176">Günlük dosyaları için varsayılan konum *D: \\ Home \\ LogFiles \\ uygulama* klasöründedir ve varsayılan dosya adı *diagnostics-yyyymmdd.txt*.</span><span class="sxs-lookup"><span data-stu-id="38f51-176">The default location for log files is in the *D:\\home\\LogFiles\\Application* folder, and the default file name is *diagnostics-yyyymmdd.txt*.</span></span> <span data-ttu-id="38f51-177">Varsayılan dosya boyutu sınırı 10 MB 'tır ve tutulan varsayılan en fazla dosya sayısı 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="38f51-177">The default file size limit is 10 MB, and the default maximum number of files retained is 2.</span></span> <span data-ttu-id="38f51-178">Varsayılan blob adı *{app-name} {timestamp}/yyyy/mm/dd/ss/{Guid} -applicationLog.txt*.</span><span class="sxs-lookup"><span data-stu-id="38f51-178">The default blob name is *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*.</span></span>

<span data-ttu-id="38f51-179">Bu sağlayıcı yalnızca proje Azure ortamında çalıştırıldığında günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="38f51-179">This provider only logs when the project runs in the Azure environment.</span></span>

#### <a name="azure-log-streaming"></a><span data-ttu-id="38f51-180">Azure günlük akışı</span><span class="sxs-lookup"><span data-stu-id="38f51-180">Azure log streaming</span></span>

<span data-ttu-id="38f51-181">Azure günlük akışı, günlük etkinliklerini gerçek zamanlı olarak görüntülemeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="38f51-181">Azure log streaming supports viewing log activity in real time from:</span></span>

- <span data-ttu-id="38f51-182">Uygulama sunucusu</span><span class="sxs-lookup"><span data-stu-id="38f51-182">The app server</span></span>
- <span data-ttu-id="38f51-183">Web sunucusu</span><span class="sxs-lookup"><span data-stu-id="38f51-183">The web server</span></span>
- <span data-ttu-id="38f51-184">Başarısız istek izleme</span><span class="sxs-lookup"><span data-stu-id="38f51-184">Failed request tracing</span></span>

<span data-ttu-id="38f51-185">Azure günlük akışını yapılandırmak için:</span><span class="sxs-lookup"><span data-stu-id="38f51-185">To configure Azure log streaming:</span></span>

- <span data-ttu-id="38f51-186">Uygulamanın Portal sayfasından **App Service günlükleri** sayfasına gidin.</span><span class="sxs-lookup"><span data-stu-id="38f51-186">Navigate to the **App Service logs** page from the app's portal page.</span></span>
- <span data-ttu-id="38f51-187">**Uygulama günlüğünü (FileSystem)** **Açık**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="38f51-187">Set **Application Logging (Filesystem)** to **On**.</span></span>
- <span data-ttu-id="38f51-188">Günlük **düzeyini**seçin.</span><span class="sxs-lookup"><span data-stu-id="38f51-188">Choose the log **Level**.</span></span> <span data-ttu-id="38f51-189">Bu ayar yalnızca Azure günlük akışı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="38f51-189">This setting only applies to Azure log streaming.</span></span>

<span data-ttu-id="38f51-190">Günlükleri görüntülemek için **günlük akışı** sayfasına gidin.</span><span class="sxs-lookup"><span data-stu-id="38f51-190">Navigate to the **Log Stream** page to view logs.</span></span> <span data-ttu-id="38f51-191">Günlüğe kaydedilen iletiler arabirimiyle günlüğe kaydedilir `ILogger` .</span><span class="sxs-lookup"><span data-stu-id="38f51-191">The logged messages are logged with the `ILogger` interface.</span></span>

### <a name="azure-application-insights"></a><span data-ttu-id="38f51-192">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="38f51-192">Azure Application Insights</span></span>

<span data-ttu-id="38f51-193">[Microsoft. Extensions. Logging. ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) sağlayıcı paketi günlükleri [Azure Application Insights](/azure/azure-monitor/app/cloudservices)yazar.</span><span class="sxs-lookup"><span data-stu-id="38f51-193">The [Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) provider package writes logs to [Azure Application Insights](/azure/azure-monitor/app/cloudservices).</span></span> <span data-ttu-id="38f51-194">Application Insights, bir Web uygulamasını izleyen ve telemetri verilerini sorgulamak ve analiz etmek için araçlar sağlayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="38f51-194">Application Insights is a service that monitors a web app and provides tools for querying and analyzing the telemetry data.</span></span> <span data-ttu-id="38f51-195">Bu sağlayıcıyı kullanıyorsanız, Application Insights araçlarını kullanarak günlüklerinizi sorgulayabilir ve analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38f51-195">If you use this provider, you can query and analyze your logs by using the Application Insights tools.</span></span>

<span data-ttu-id="38f51-196">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="38f51-196">For more information, see the following resources:</span></span>

- [<span data-ttu-id="38f51-197">Application Insights'a genel bakış</span><span class="sxs-lookup"><span data-stu-id="38f51-197">Application Insights overview</span></span>](/azure/application-insights/app-insights-overview)
- <span data-ttu-id="38f51-198">[.NET Core ILogger günlükleri Için Applicationınsightsloggerprovider](/azure/azure-monitor/app/ilogger) -günlük sağlayıcısını Application Insights telemetri olmadan uygulamak istiyorsanız buraya başlayın.</span><span class="sxs-lookup"><span data-stu-id="38f51-198">[ApplicationInsightsLoggerProvider for .NET Core ILogger logs](/azure/azure-monitor/app/ilogger) - Start here if you want to implement the logging provider without the rest of Application Insights telemetry.</span></span>
- <span data-ttu-id="38f51-199">[Günlüğe kaydetme bağdaştırıcılarını Application Insights](/azure/azure-monitor/app/asp-net-trace-logs).</span><span class="sxs-lookup"><span data-stu-id="38f51-199">[Application Insights logging adapters](/azure/azure-monitor/app/asp-net-trace-logs).</span></span>
- <span data-ttu-id="38f51-200">Microsoft Learn sitede Application Insights SDK-etkileşimli öğreticisini [yükleyip başlatın](/learn/modules/instrument-web-app-code-with-application-insights) .</span><span class="sxs-lookup"><span data-stu-id="38f51-200">[Install, configure, and initialize the Application Insights SDK](/learn/modules/instrument-web-app-code-with-application-insights) - Interactive tutorial on the Microsoft Learn site.</span></span>

## <a name="third-party-logging-providers"></a><span data-ttu-id="38f51-201">Üçüncü taraf günlük oluşturma sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="38f51-201">Third-party logging providers</span></span>

<span data-ttu-id="38f51-202">Çeşitli .NET iş yükleriyle çalışan bazı üçüncü taraf günlük çerçeveleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="38f51-202">Here are some third-party logging frameworks that work with various .NET workloads:</span></span>

- <span data-ttu-id="38f51-203">[ELMAH.io](https://elmah.io) ([GitHub deposu](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="38f51-203">[elmah.io](https://elmah.io) ([GitHub repo](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span></span>
- <span data-ttu-id="38f51-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub deposu](https://github.com/mattwcole/gelf-extensions-logging))</span><span class="sxs-lookup"><span data-stu-id="38f51-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub repo](https://github.com/mattwcole/gelf-extensions-logging))</span></span>
- <span data-ttu-id="38f51-205">[Jsnlog](https://jsnlog.com) ([GitHub deposu](https://github.com/mperdeck/jsnlog))</span><span class="sxs-lookup"><span data-stu-id="38f51-205">[JSNLog](https://jsnlog.com) ([GitHub repo](https://github.com/mperdeck/jsnlog))</span></span>
- <span data-ttu-id="38f51-206">[KissLog.net](https://kisslog.net) ([GitHub deposu](https://github.com/catalingavan/KissLog-net))</span><span class="sxs-lookup"><span data-stu-id="38f51-206">[KissLog.net](https://kisslog.net) ([GitHub repo](https://github.com/catalingavan/KissLog-net))</span></span>
- <span data-ttu-id="38f51-207">[Log4Net](https://logging.apache.org/log4net) ([GitHub deposu](https://github.com/apache/logging-log4net))</span><span class="sxs-lookup"><span data-stu-id="38f51-207">[Log4Net](https://logging.apache.org/log4net) ([GitHub repo](https://github.com/apache/logging-log4net))</span></span>
- <span data-ttu-id="38f51-208">[Loggr](https://loggr.net) ([GitHub deposu](https://github.com/imobile3/Loggr.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="38f51-208">[Loggr](https://loggr.net) ([GitHub repo](https://github.com/imobile3/Loggr.Extensions.Logging))</span></span>
- <span data-ttu-id="38f51-209">[NLog](https://nlog-project.org) ([GitHub deposu](https://github.com/NLog/NLog.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="38f51-209">[NLog](https://nlog-project.org) ([GitHub repo](https://github.com/NLog/NLog.Extensions.Logging))</span></span>
- <span data-ttu-id="38f51-210">[Sentry](https://sentry.io/welcome) ([GitHub deposu](https://github.com/getsentry/sentry-dotnet))</span><span class="sxs-lookup"><span data-stu-id="38f51-210">[Sentry](https://sentry.io/welcome) ([GitHub repo](https://github.com/getsentry/sentry-dotnet))</span></span>
- <span data-ttu-id="38f51-211">[Serilog](https://serilog.net) ([GitHub deposu](https://github.com/serilog/serilog-sinks-console))</span><span class="sxs-lookup"><span data-stu-id="38f51-211">[Serilog](https://serilog.net) ([GitHub repo](https://github.com/serilog/serilog-sinks-console))</span></span>
- <span data-ttu-id="38f51-212">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub deposu](https://github.com/googleapis/google-cloud-dotnet))</span><span class="sxs-lookup"><span data-stu-id="38f51-212">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub repo](https://github.com/googleapis/google-cloud-dotnet))</span></span>

<span data-ttu-id="38f51-213">Bazı üçüncü taraf çerçeveler [, yapılandırılmış günlük olarak da bilinen anlam günlüğe kaydetme](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging)işlemini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="38f51-213">Some third-party frameworks can perform [semantic logging, also known as structured logging](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).</span></span>

<span data-ttu-id="38f51-214">Bir üçüncü taraf çerçevesinin kullanılması, yerleşik sağlayıcılardan birini kullanmaya benzer:</span><span class="sxs-lookup"><span data-stu-id="38f51-214">Using a third-party framework is similar to using one of the built-in providers:</span></span>

1. <span data-ttu-id="38f51-215">Projenize bir NuGet paketi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38f51-215">Add a NuGet package to your project.</span></span>
1. <span data-ttu-id="38f51-216">`ILoggerFactory` `ILoggingBuilder` Günlüğe kaydetme çerçevesi tarafından sağlanmış bir veya genişletme yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="38f51-216">Call an `ILoggerFactory` or `ILoggingBuilder` extension method provided by the logging framework.</span></span>

<span data-ttu-id="38f51-217">Daha fazla bilgi için bkz. her sağlayıcının belgeleri.</span><span class="sxs-lookup"><span data-stu-id="38f51-217">For more information, see each provider's documentation.</span></span> <span data-ttu-id="38f51-218">Üçüncü taraf günlüğü sağlayıcıları Microsoft tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="38f51-218">Third-party logging providers aren't supported by Microsoft.</span></span>

## <a name="see-also"></a><span data-ttu-id="38f51-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38f51-219">See also</span></span>

- <span data-ttu-id="38f51-220">[.NET oturumu açılıyor](logging.md).</span><span class="sxs-lookup"><span data-stu-id="38f51-220">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="38f51-221">[.Net ' te özel bir günlüğe kaydetme sağlayıcısı uygulayın](custom-logging-provider.md).</span><span class="sxs-lookup"><span data-stu-id="38f51-221">[Implement a custom logging provider in .NET](custom-logging-provider.md).</span></span>
- <span data-ttu-id="38f51-222">[.Net ' te yüksek performanslı günlük kaydı](high-performance-logging.md).</span><span class="sxs-lookup"><span data-stu-id="38f51-222">[High-performance logging in .NET](high-performance-logging.md).</span></span>
