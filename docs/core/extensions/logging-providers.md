---
title: .NET 'te günlüğe kaydetme sağlayıcıları
description: Günlüğe kaydetme sağlayıcısı API 'sinin .NET uygulamalarında nasıl kullanıldığını öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.openlocfilehash: 936413be1514e6cea20e28a7d4431c572560d193
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614759"
---
# <a name="logging-providers-in-net"></a>.NET 'te günlüğe kaydetme sağlayıcıları

Günlüğe kaydetme sağlayıcıları, `Console` yalnızca günlükleri standart çıkış olarak görüntüleyen sağlayıcı dışında günlükleri kalıcı hale gelir. Örneğin, Azure Application Insights sağlayıcısı günlükleri Azure Application Insights depolar. Birden çok sağlayıcı etkinleştirilebilir.

Varsayılan .NET Worker uygulama şablonları:

- [Genel Konağı](generic-host.md)kullanın.
- <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>Aşağıdaki günlük sağlayıcılarını ekleyen çağırın:
  - [Konsol](#console)
  - [H](#debug)
  - [EventSource](#event-source)
  - [EventLog](#windows-eventlog): yalnızca Windows

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

Yukarıdaki kod, `Program` .NET çalışan uygulama şablonlarıyla oluşturulan sınıfı gösterir. Sonraki birkaç bölüm, genel ana bilgisayarı kullanan .NET Worker uygulama şablonlarına göre örnekler sağlar.

Tarafından eklenen varsayılan günlük sağlayıcıları kümesini geçersiz kılmak için `Host.CreateDefaultBuilder` , istediğiniz `ClearProviders` günlüğe kaydetme sağlayıcılarını çağırın ve ekleyin. Örneğin, aşağıdaki kod:

- <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A>Oluşturucunun tüm örneklerini kaldırmak için çağırır <xref:Microsoft.Extensions.Logging.ILoggerProvider> .
- [Konsol](#console) günlüğü sağlayıcısını ekler.

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

Ek sağlayıcılar için bkz.:

- [Yerleşik günlük oluşturma sağlayıcıları](#built-in-logging-providers).
- [Üçüncü taraf günlüğü sağlayıcıları](#third-party-logging-providers).

## <a name="configure-a-service-that-depends-on-ilogger"></a>ILogger 'a bağlı bir hizmet yapılandırma

Bağımlı olan bir hizmeti yapılandırmak için `ILogger<T>` , Oluşturucu ekleme veya bir fabrika yöntemi sağlama kullanın. Fabrika yöntemi yaklaşımı yalnızca başka bir seçenek yoksa önerilir. Örneğin, DI tarafından sağlanmış bir örneğe ihtiyacı olan bir hizmeti düşünün `ILogger<T>` :

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

Yukarıdaki kod, dı kapsayıcısının bir örneğini oluşturmak için ilk kez çalışan bir [Func<Iservıceprovider, ıexampleservice>](/dotnet/api/system.func-2) `IExampleService` . Kayıtlı hizmetlerden herhangi birine bu şekilde erişebilirsiniz.

## <a name="built-in-logging-providers"></a>Yerleşik günlük oluşturma sağlayıcıları

Microsoft uzantıları, çalışma zamanı kitaplıklarının bir parçası olarak aşağıdaki günlük sağlayıcılarını içerir:

- [Konsol](#console)
- [H](#debug)
- [EventSource](#event-source)
- [EventLog](#windows-eventlog)

Aşağıdaki günlük oluşturma sağlayıcıları Microsoft tarafından gönderilir, ancak çalışma zamanı kitaplıklarının bir parçası değildir. Bunların ek NuGet paketleri olarak yüklenmesi gerekir.

- [AzureAppServicesFile ve AzureAppServicesBlob](#azure-app-service)
- [ApplicationInsights](#azure-application-insights)

### <a name="console"></a>Konsol

`Console`Sağlayıcı çıktıyı konsola kaydeder. Geliştirme sırasında günlükleri görüntüleme hakkında daha fazla bilgi için `Console` bkz. [DotNet Run ve Visual Studio 'Dan çıktıyı günlüğe kaydetme](logging.md#logging-output-from-dotnet-run-and-visual-studio).

### <a name="debug"></a>Hata ayıklama

`Debug`Sağlayıcı, [System. Diagnostics. Debug](/dotnet/api/system.diagnostics.debug) sınıfını kullanarak günlük çıktısını yazar. `System.Diagnostics.Debug.WriteLine`Sağlayıcıya yazmak için çağrılar `Debug` .

Linux 'ta, `Debug` sağlayıcı günlük konumu dağıtıma bağımlıdır ve aşağıdakilerden biri olabilir:

- */var/log/Message*
- */var/log/Syslog*

### <a name="event-source"></a>Olay Kaynağı

`EventSource`Sağlayıcı, adlı platformlar arası bir olay kaynağına Yazar `Microsoft-Extensions-Logging` . Windows 'da, sağlayıcı [ETW](/windows/win32/etw/event-tracing-portal)kullanır.

#### <a name="dotnet-trace-tooling"></a>DotNet izleme araçları

[DotNet-Trace](../diagnostics/dotnet-trace.md) Aracı, çalışan bir Işlemin .NET Core izlemelerinin toplanmasını sağlayan platformlar arası CLI genel aracıdır. Araç, <xref:Microsoft.Extensions.Logging.EventSource> kullanarak sağlayıcı verilerini toplar <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource> .

Bkz. yükleme yönergeleri için [DotNet-Trace](../diagnostics/dotnet-trace.md) . Kullanarak bir tanılama öğreticisi için `dotnet-trace` bkz. [.NET Core 'DA yüksek CPU kullanımı hata ayıklama](/../diagnostics/debug-highcpu.md).

### <a name="windows-eventlog"></a>Windows olay günlüğü

`EventLog`Sağlayıcı, Windows olay günlüğüne günlük çıktısı gönderir. Diğer sağlayıcılardan farklı olarak, `EventLog` sağlayıcı varsayılan sağlayıcı ***not*** olmayan ayarları uygulamaz. `EventLog`Günlük ayarları belirtilmemişse, varsayılan olarak `LogLevel.Warning` .

Olayları daha düşük günlüğe kaydetmek için <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType> , günlük düzeyini açık olarak ayarlayın. Aşağıdaki örnek, olay günlüğü varsayılan günlük düzeyini şu şekilde ayarlar <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType> :

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

[AddEventLog aşırı yüklemeleri](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) geçiş yapabilir <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings> . `null`Veya belirtilmemişse, aşağıdaki varsayılan ayarlar kullanılır:

- `LogName`: "Uygulama"
- `SourceName`: ".NET çalışma zamanı"
- `MachineName`: Yerel makine adı kullanılır.

Aşağıdaki kod, ' `SourceName` nin varsayılan değerinden öğesini olarak değiştirir `".NET Runtime"` `CustomLogs` :

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

### <a name="azure-app-service"></a>Azure App Service

[Microsoft. Extensions. Logging. AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) sağlayıcı paketi, günlükleri bir Azure App Service uygulamasının dosya sistemindeki metin dosyalarına ve bir Azure depolama hesabındaki [BLOB depolama](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) alanına yazar.

Sağlayıcı paketi çalışma zamanı kitaplıklarına dahil değildir. Sağlayıcıyı kullanmak için sağlayıcı paketini projeye ekleyin.

Sağlayıcı ayarlarını yapılandırmak için <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions> Aşağıdaki örnekte gösterildiği gibi ve kullanın:

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

Uygulama Azure App Service dağıtıldığında, Azure portal **App Service** sayfasının [App Service Günlükler](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) bölümündeki ayarları kullanır. Aşağıdaki ayarlar güncelleştirilirken, değişiklikler uygulamanın yeniden başlatılmasını veya yeniden dağıtımı gerekmeden hemen etkili olur.

- **Uygulama günlüğü (dosya sistemi)**
- **Uygulama günlüğü (blob)**

Günlük dosyaları için varsayılan konum *D: \\ Home \\ LogFiles \\ uygulama* klasöründedir ve varsayılan dosya adı *diagnostics-yyyymmdd.txt*. Varsayılan dosya boyutu sınırı 10 MB 'tır ve tutulan varsayılan en fazla dosya sayısı 2 ' dir. Varsayılan blob adı *{app-name} {timestamp}/yyyy/mm/dd/ss/{Guid} -applicationLog.txt*.

Bu sağlayıcı yalnızca proje Azure ortamında çalıştırıldığında günlüğe kaydedilir.

#### <a name="azure-log-streaming"></a>Azure günlük akışı

Azure günlük akışı, günlük etkinliklerini gerçek zamanlı olarak görüntülemeyi destekler:

- Uygulama sunucusu
- Web sunucusu
- Başarısız istek izleme

Azure günlük akışını yapılandırmak için:

- Uygulamanın Portal sayfasından **App Service günlükleri** sayfasına gidin.
- **Uygulama günlüğünü (FileSystem)** **Açık**olarak ayarlayın.
- Günlük **düzeyini**seçin. Bu ayar yalnızca Azure günlük akışı için geçerlidir.

Günlükleri görüntülemek için **günlük akışı** sayfasına gidin. Günlüğe kaydedilen iletiler arabirimiyle günlüğe kaydedilir `ILogger` .

### <a name="azure-application-insights"></a>Azure Application Insights

[Microsoft. Extensions. Logging. ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) sağlayıcı paketi günlükleri [Azure Application Insights](/azure/azure-monitor/app/cloudservices)yazar. Application Insights, bir Web uygulamasını izleyen ve telemetri verilerini sorgulamak ve analiz etmek için araçlar sağlayan bir hizmettir. Bu sağlayıcıyı kullanıyorsanız, Application Insights araçlarını kullanarak günlüklerinizi sorgulayabilir ve analiz edebilirsiniz.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [Application Insights'a genel bakış](/azure/application-insights/app-insights-overview)
- [.NET Core ILogger günlükleri Için Applicationınsightsloggerprovider](/azure/azure-monitor/app/ilogger) -günlük sağlayıcısını Application Insights telemetri olmadan uygulamak istiyorsanız buraya başlayın.
- [Günlüğe kaydetme bağdaştırıcılarını Application Insights](/azure/azure-monitor/app/asp-net-trace-logs).
- Microsoft Learn sitede Application Insights SDK-etkileşimli öğreticisini [yükleyip başlatın](/learn/modules/instrument-web-app-code-with-application-insights) .

## <a name="third-party-logging-providers"></a>Üçüncü taraf günlük oluşturma sağlayıcıları

Çeşitli .NET iş yükleriyle çalışan bazı üçüncü taraf günlük çerçeveleri aşağıda verilmiştir:

- [ELMAH.io](https://elmah.io) ([GitHub deposu](https://github.com/elmahio/Elmah.Io.Extensions.Logging))
- [Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub deposu](https://github.com/mattwcole/gelf-extensions-logging))
- [Jsnlog](https://jsnlog.com) ([GitHub deposu](https://github.com/mperdeck/jsnlog))
- [KissLog.net](https://kisslog.net) ([GitHub deposu](https://github.com/catalingavan/KissLog-net))
- [Log4Net](https://logging.apache.org/log4net) ([GitHub deposu](https://github.com/apache/logging-log4net))
- [Loggr](https://loggr.net) ([GitHub deposu](https://github.com/imobile3/Loggr.Extensions.Logging))
- [NLog](https://nlog-project.org) ([GitHub deposu](https://github.com/NLog/NLog.Extensions.Logging))
- [Sentry](https://sentry.io/welcome) ([GitHub deposu](https://github.com/getsentry/sentry-dotnet))
- [Serilog](https://serilog.net) ([GitHub deposu](https://github.com/serilog/serilog-sinks-console))
- [Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub deposu](https://github.com/googleapis/google-cloud-dotnet))

Bazı üçüncü taraf çerçeveler [, yapılandırılmış günlük olarak da bilinen anlam günlüğe kaydetme](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging)işlemini gerçekleştirebilir.

Bir üçüncü taraf çerçevesinin kullanılması, yerleşik sağlayıcılardan birini kullanmaya benzer:

1. Projenize bir NuGet paketi ekleyin.
1. `ILoggerFactory` `ILoggingBuilder` Günlüğe kaydetme çerçevesi tarafından sağlanmış bir veya genişletme yöntemi çağırın.

Daha fazla bilgi için bkz. her sağlayıcının belgeleri. Üçüncü taraf günlüğü sağlayıcıları Microsoft tarafından desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET oturumu açılıyor](logging.md).
- [.Net ' te özel bir günlüğe kaydetme sağlayıcısı uygulayın](custom-logging-provider.md).
- [.Net ' te yüksek performanslı günlük kaydı](high-performance-logging.md).
