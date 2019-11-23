---
title: Uygulama performansı yönetimi-WCF geliştiricileri için gRPC
description: ASP.NET Core gRPC uygulamaları için günlüğe kaydetme, ölçümler ve izleme.
ms.date: 09/02/2019
ms.openlocfilehash: 2b6a30ab68cb6e2fdc81c59e7faef81064b948c1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968173"
---
# <a name="application-performance-management"></a>Uygulama Performansı Yönetimi

Kubernetes gibi modern üretim ortamlarında, en iyi şekilde çalıştığından emin olmak için uygulamaları izleyebilmek çok önemlidir. Günlüğe kaydetme ve ölçümler gibi sorunlar hiçbir şekilde daha önemli değildir. GRPC dahil ASP.NET Core, günlük iletilerini ve *ölçüm verilerini üretmek* ve yönetmek için birinci sınıf desteğe ve verileri izlemelerine sahiptir. Bu bölümde daha ayrıntılı bilgi edinmek için bu alanların araştırılacak.

## <a name="logging-vs-metrics"></a>Günlük vs ölçümleri

Uygulama ayrıntılarına bakmadan önce, günlüğe kaydetme ve ölçümler arasındaki farkı anlamak gerekir.

Günlüğe kaydetme, sistemde gerçekleşen şeyler hakkında ayrıntılı bilgileri kaydeden metin iletileriyle ilgilidir. Günlük iletileri yığın izlemeleri gibi özel durum verilerini veya ileti hakkında bağlam sağlayan yapılandırılmış verileri içerebilir. Günlüğe kaydetme çıkışı genellikle aranabilir bir metin deposuna yazılır.

Ölçümler, bir uygulamanın genel sistem durumunun ve performansının görünümünü sağlayan bir panodaki grafikler ve grafikler kullanılarak toplanacak ve sunulacak şekilde tasarlanan sayısal verilere başvurur. Ölçüm verileri, bir eşik aşıldığında otomatik uyarıları tetiklemek için de kullanılabilir. Aşağıdaki listede ölçüm verilerine ilişkin bazı örnekler gösterilmektedir:

- İstekleri işlemek için geçen süre.
- Bir hizmet örneği tarafından işlenen saniye başına istek sayısı.
- Bir örnekteki başarısız istek sayısı.

## <a name="logging-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 'de oturum açma

ASP.NET Core, [Microsoft. Extensions. Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) NuGet paketi biçiminde günlük için yerleşik destek sağlar. Bu kitaplığın temel kısımları Web SDK 'sına dahildir, bu yüzden el ile yüklemeniz gerekmez. Varsayılan olarak, günlük iletileri standart çıktıya ("konsol") ve herhangi bir ekli hata ayıklayıcıya yazılır. Kalıcı dış veri depolarına Günlükler yazmak için [isteğe bağlı günlük havuzu paketlerini](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers)içeri aktarmanız gerekebilir.

ASP.NET Core gRPC çerçevesi, bu günlük çerçevesini ayrıntılı tanılama günlüğü iletileri yazarak uygulamanızın kendi iletileriyle birlikte işlenebilirler.

### <a name="produce-log-messages"></a>Günlük iletileri üretme

Günlüğe kaydetme uzantısı, ASP.NET Core bağımlılık ekleme sistemine otomatik olarak kaydedilir, bu sayede Günlükçüleri gRPC hizmet türlerinde bir oluşturucu parametresi olarak belirtebilirsiniz.

```csharp
public class StockData : Stocks.StocksBase
{
    private readonly ILogger<StockData> _logger;

    public StockData(ILogger<StockData> logger)
    {
        _logger = logger;
    }
}
```

İstekler, özel durumlar ve benzeri birçok günlük mesajı, ASP.NET Core ve gRPC çerçevesi bileşenleri tarafından sağlanır. Alt düzey sorunlar yerine uygulama mantığı hakkında ayrıntı ve bağlam sağlamak için kendi günlük iletilerinizi ekleyin.

Günlük iletilerini ve kullanılabilir günlük havuzlarını ve hedefleri yazma hakkında daha fazla bilgi için bkz. [.NET Core 'Da günlüğe kaydetme ve ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) makalesi.

## <a name="metrics-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 'de ölçümler

.NET Core çalışma zamanı, <xref:System.Diagnostics.Tracing.EventSource> ve <xref:System.Diagnostics.Tracing.EventCounter> sınıfları gibi API 'Leri içeren ölçümleri yayma ve gözlemlemek için bir bileşen kümesi sağlar. Bu API 'Ler, [DotNet sayaçları genel aracı](https://github.com/dotnet/diagnostics/blob/master/documentation/dotnet-counters-instructions.md)veya Windows Için olay izleme gibi dış süreçler tarafından tüketilen temel sayısal verileri göstermek için kullanılabilir. Kendi kodunuzda `EventCounter` kullanma hakkında daha fazla bilgi için [EventCounter tanıtım](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md) Öğreticisi ' ne bakın.

Daha gelişmiş ölçümler ve ölçüm verilerini daha geniş veri depolarına yazmak için, [uygulama ölçümleri](https://www.app-metrics.io)adlı harika bir açık kaynak projesi vardır. Bu kitaplıklar paketi kodunuzu işaretlemek için kapsamlı bir tür kümesi sağlar. Ayrıca, Prometheus ve etkileyen, [Azure Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)gibi zaman serisi veritabanlarını içeren farklı türlerdeki hedeflere ölçümleri yazmak için paketler sunar. [App. ölçümler. AspNetCore. Mvc](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) NuGet paketi, ASP.NET Core çerçevesi ile tümleştirme aracılığıyla otomatik olarak oluşturulan kapsamlı bir temel ölçümler kümesi ekler ve Web sitesi bu ölçümleri [Grafana](https://grafana.com/) görselleştirme platformu ile görüntülemek için [Şablonlar](https://www.app-metrics.io/samples/grafana/) sağlar.

Uygulama ölçümleri hakkında daha fazla bilgi ve belge hakkında daha fazla bilgi için [App-Metrics.io](https://app-metrics.io) Web sitesine bakın.

### <a name="produce-metrics"></a>Ölçüm üretin

Çoğu ölçüm platformu, aşağıdaki tabloda özetlenen beş temel ölçüm türünü destekler:

| Ölçüm türü | Açıklama |
| ----------- | ----------- |
| Sayaç     | İstekler, hatalar vb. gibi bir şeyin ne sıklıkta gerçekleştiğini izler. |
| Ölçer       | Etkin bağlantılar gibi zaman içinde değişen tek bir değer kaydeder. |
| Histogram   | Değerlerin bir dağılımını rastgele sınırlar arasında ölçer. Örneğin, bir histogram veri kümesi boyutunu izleyip, kaç tane < 10 kayıt olduğunu, kaç 11-100 ve 101-1000 olduğunu ve 1000 kaydı > saymaya yönelik olabilir. |
| Si       | Bir olayın çeşitli zaman yayıldığında oluşma oranını ölçer. |
| Zamanlayıcı       | Etkinlik süresini ve oluşma hızını izler, histogram olarak depolanır. |

*Uygulama ölçümlerini*kullanarak, bir `IMetrics` arabirimi bağımlılık ekleme yoluyla elde edilebilir ve bir GRPC hizmeti için bu ölçümlerin herhangi birini kaydetmek üzere kullanılabilir. Aşağıdaki örnek, zaman içinde yapılan `Get` isteklerinin sayısını nasıl saymayı gösterir:

```csharp
public class StockData : Stocks.StocksBase
{
    private static readonly CounterOptions GetRequestCounter = new CounterOptions
    {
        Name = "StockData_Get_Requests",
        MeasurementUnit = Unit.Calls
    };

    private readonly IStockRepository _repository;
    private readonly IMetrics _metrics;

    public StockData(IStockRepository repository, IMetrics metrics)
    {
        _repository = repository;
        _metrics = metrics;
    }

    public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
    {
        _metrics.Measure.Counter.Increment(GetRequestCounter);

        // Serve request...
    }
}
```

### <a name="store-and-visualize-metrics-data"></a>Ölçüm verilerini depolayın ve görselleştirin

Ölçüm verilerini depolamanın en iyi yolu, zaman damgalarla işaretlenmiş sayısal veri serisini kaydetmek üzere tasarlanan özel bir veri deposu olan *zaman serisi bir veritabanıdır*. Bu veritabanlarının en popüler değeri, [Prometheus](https://prometheus.io/) ve [etkileyen](https://www.influxdata.com/products/influxdb-overview/). Microsoft Azure Ayrıca, [Azure izleyici](https://docs.microsoft.com/azure/azure-monitor/overview) hizmeti aracılığıyla adanmış ölçüm depolama alanı sağlar.

Ölçüm verilerinin görselleştirilmesi için geçerli yapılacak çözüm, Azure Izleyici, etkileyen ve Prometheus gibi çok çeşitli depolama sağlayıcılarıyla birlikte [Grafana](https://grafana.com). Aşağıdaki görüntüde, StockData örneğini çalıştıran Linkerd hizmet kafeslerinden alınan ölçümleri görüntüleyen örnek bir Grafana panosu gösterilmektedir:

![Grafana panosu](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>Ölçüm tabanlı uyarı

Ölçüm verilerinin sayısal doğası, uyarı sistemlerini, geliştiricilerin veya Destek mühendislerinin bir değer tanımlı tolerans dışında kaldığında geliştiricilere bildirmek için uygun olduğu anlamına gelir. Zaten bahsedilen platformlar, e-postalar, metin iletileri veya Pano içi görselleştirmeler dahil olmak üzere çeşitli seçenekler aracılığıyla uyarı desteği sağlar.

## <a name="distributed-tracing"></a>Dağıtılmış izleme

*Dağıtılmış izleme* , mikro hizmetler ve dağıtılmış mimarilerin artan kullanımını gösteren, izleme sırasında görece son bir geliştirmede oluşur. İstemci tarayıcısından, uygulamadan veya cihazdan gelen tek bir istek birçok adım ve alt isteklere ayrılabilir ve bir ağ genelinde birçok hizmetin kullanımını içerir. Bu, günlük iletilerinin ve ölçümlerinin tetiklediği belirli bir istekle ilişkilendirilmesi güç sağlar. Dağıtılmış izleme, günlüklere ve ölçümlere belirli bir işlemle bağıntılı olarak izin veren isteklere tanımlayıcılar uygular. Bu, [WCF 'nin uçtan uca izlemeye](https://docs.microsoft.com/dotnet/framework/wcf/diagnostics/tracing/end-to-end-tracing)benzerdir, ancak birden çok platformda uygulanır.

Hala bir teknoloji alanı olsa da, dağıtılmış izleme popülerliği hızla arttı ve şimdi bir standartlaştırma süreci ile geçiyor. Bulut Yerel Bilgi Işlem altyapısı, [Açık izleme standardı](https://opentracing.io)oluşturdu ve [caeger](https://www.jaegertracing.io/) ve [elastik APM](https://www.elastic.co/products/apm)gibi arka uçlarla çalışmaya yönelik satıcıya ait kitaplıkları sağlamaya çalışıyor. Aynı zamanda, Google aynı sorun kümesini karşılamak için [Opencensus projesini](https://opencensus.io/) oluşturmuştur. Bu iki proje artık yeni bir proje olan [opentelemetri](https://opentelemetry.io)ile birleştirilecektir ve bu da gelecekteki sektör standardı olacak şekilde amaçlar.

### <a name="how-distributed-tracing-works"></a>Dağıtılmış izlemenin nasıl çalıştığı

Dağıtılmış izleme, bir sistemin birden çok düğümündeişlemeyi gerektirebilecek tek bir *izlemenin*parçası olan adlandırılmış, zamanlanmış işlemler olan adlandırılmış, zaman aşımına uğrayan işlem kavramını temel alır. Yeni bir işlem başlatıldığında, benzersiz tanımlayıcı ile bir izleme oluşturulur. Her alt işlem için, kendi tanımlayıcısı ve izleme tanımlayıcısı ile bir span oluşturulur. İstek sistem etrafında geçerken, çeşitli bileşenler *üst*ilişkilerini içeren *alt* yayılma oluşturabilir. Bir yayılma, izleme ve yayma tanımlayıcılarını ve ayrıca anahtar/değer çiftleri ( *Bagaj*adı verilir) biçimindeki yararlı verileri içeren bir *içeriğe*sahiptir.

### <a name="distributed-tracing-with-diagnosticsource"></a>DiagnosticSource ile dağıtılmış izleme

.NET Core, dağıtılmış izlemeler ve yayılmalar için iyi eşleşen bir iç modüle sahiptir: [Diagnosticsource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide). Ayrıca, bir işlem içinde tanılamayı oluşturmak ve kullanmak için basit bir yol sağlamak üzere `DiagnosticSource` modülü, dağıtılmış izlemenin etkili bir şekilde uygulanması veya bir izleme içindeki bir yayılım olan bir *etkinlik*kavramıdır. Modülün iç işlevleri, tanımlayıcıları ayırmak da dahil olmak üzere üst/alt etkinliklerden yararlanın. `Activity` türünü kullanma hakkında daha fazla bilgi için bkz. [GitHub 'Da etkinlik Kullanıcı Kılavuzu](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)

DiagnosticSource, çekirdek çerçevesinin bir parçası olduğundan, gRPC çerçevesindeki açık destek dahil olmak üzere <xref:System.Net.Http.HttpClient>, Entity Framework Core ve ASP.NET Core dahil olmak üzere çeşitli çekirdek bileşenler tarafından desteklenir. ASP.NET Core bir istek aldığında, [W3C Trace bağlam](https://www.w3.org/TR/trace-context) standardı ile eşleşen BIR çift http üst bilgisi olup olmadığını denetler. Üstbilgiler bulunursa bir etkinlik, üst bilgilerden kimlik değerleri ve bağlam kullanılarak başlatılır. Üst bilgi bulunmazsa, standart biçimle eşleşen üretilen kimlik değerleriyle bir etkinlik başlatılır. Bu etkinliğin ömrü boyunca Framework veya uygulama kodu tarafından oluşturulan tüm Tanılamalar, izleme ve span tanımlayıcılarıyla etiketlenebilir. `HttpClient` desteği, her istekte geçerli bir etkinliği denetleyerek ve izleme üstbilgilerini giden isteğe otomatik olarak ekleyerek bunu daha fazla genişletir.

ASP.NET Core gRPC istemcisi ve sunucu kitaplıkları, DiagnosticSource ve Activity için açık destek içerir ve etkinlik oluşturur ve başlık bilgilerini otomatik olarak uygular ve kullanır.

> [!NOTE]
> Bunun hepsi, bir *dinleyicinin* tanılama bilgilerini tüketmesi durumunda meydana gelir. Dinleyici yoksa, hiçbir Tanılama yazılmaz ve hiçbir etkinlik oluşturulmaz.

### <a name="add-your-own-diagnosticsources-and-activities"></a>Kendi DiagnosticSources ve etkinliklerinizi ekleyin

GRPC dahil ASP.NET Core ve Entity Framework Core ve `HttpClient`gibi iyi bir veri miktarı otomatik olarak oluşturulsa da, kendi tanılamayı eklemek veya uygulama kodunuzda açık yayılmalar oluşturmak isteyebilirsiniz. Kendi tanılamayı nasıl uygulayacağınızı öğrenmek için [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener) ve [etkinlik Kullanıcı Kılavuzu](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage) ' na bakın.

### <a name="store-distributed-trace-data"></a>Dağıtılmış izleme verilerini depola

Opentelemetri projesini yazma sırasında hala erken aşamalarındayken, .NET uygulamaları için yalnızca alfa kalite paketleri kullanılabilir. OpenTracing projesi daha fazla yetişkin kitaplığı sunar, ancak gelecekte bu yana Opentelemetri kitaplıklarının yerini alır.

OpenTracing API 'SI aşağıda açıklanmıştır. Uygulamanızda daha yeni Opentelemetri API 'sini kullanmayı tercih ediyorsanız, [GitHub 'Da opentelemetri .NET SDK deposuna](https://github.com/open-telemetry/opentelemetry-dotnet)bakın.

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>Dağıtılmış izleme verilerini depolamak için OpenTracing paketini kullanın

Tüm OpenTracing uyumlu arka uçları destekleyen [Opentracing NuGet paketi](https://www.nuget.org/packages/OpenTracing/) (`DiagnosticSource`bağımsız olarak kullanılabilir). Opentracing API katkıları projesinden, [opentracing. contrib. NetCore](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/), `DiagnosticSource` dinleyicisi ekleyen ve olayları ve etkinlikleri otomatik olarak arka uca yazan ek bir paket vardır. Bu paketin etkinleştirilmesi, NuGet 'den yüklemek ve `Startup` sınıfınıza bir hizmet olarak eklemek kadar basittir.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

OpenTracing paketi bir Özet katmanıdır ve bu nedenle arka uca özel bir uygulama gerektirir. OpenTracing API uygulamaları aşağıdaki açık kaynak arka uçları için kullanılabilir.

| Name | Paket | Web sitesi |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| Elastik APM | [Elastik. APM. NetCoreAll](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

.NET için opentracing API 'si hakkında daha fazla bilgi için GitHub 'daki [opentracing ve C# ](https://github.com/opentracing/opentracing-csharp) [opentracing contrib C#/.NET Core](https://github.com/opentracing-contrib/csharp-netcore) depoları konusuna bakın.

>[!div class="step-by-step"]
>[Önceki](load-balancing.md)
>[İleri](appendix.md)
