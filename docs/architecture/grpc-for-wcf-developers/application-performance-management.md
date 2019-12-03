---
title: Uygulama performansı yönetimi-WCF geliştiricileri için gRPC
description: ASP.NET Core gRPC uygulamaları için günlüğe kaydetme, ölçümler ve izleme.
ms.date: 09/02/2019
ms.openlocfilehash: e8ec701af69e8ced674183ce0afa25547713c647
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711560"
---
# <a name="application-performance-management"></a>Uygulama Performansı Yönetimi

Kubernetes gibi üretim ortamlarında, en iyi şekilde çalıştığından emin olmak için uygulamaları izlemeniz önemlidir. Günlüğe kaydetme ve ölçümler özellikle önemlidir. GRPC dahil ASP.NET Core, günlük iletilerinin ve ölçüm verilerinin oluşturulması ve yönetilmesi için yerleşik destek ve verilerin *izlenmesini* sağlar.

## <a name="the-difference-between-logging-and-metrics"></a>Günlüğe kaydetme ve ölçümler arasındaki fark

*Günlüğe kaydetme* , sistemde gerçekleşen şeyler hakkında ayrıntılı bilgileri kaydeden metin iletileriyle ilgilidir. Günlük iletileri, yığın izlemeleri gibi özel durum verilerini veya ileti hakkında bağlam sağlayan yapılandırılmış verileri içerebilir. Günlüğe kaydetme çıkışı genellikle aranabilir bir metin deposuna yazılır.

*Ölçümler* , kümelenebilir ve bir panodaki grafikler ve grafikler kullanılarak sunulacak şekilde tasarlanan sayısal verileri ifade eder. Pano, bir uygulamanın genel sistem durumunun ve performansının görünümünü sağlar. Ölçüm verileri, bir eşik aşıldığında otomatik uyarıları tetiklemek için de kullanılabilir. Ölçüm verilerine ilişkin bazı örnekler aşağıda verilmiştir:

- İstekleri işlemek için geçen süre.
- Bir hizmet örneği tarafından işlenen saniye başına istek sayısı.
- Bir örnekteki başarısız istek sayısı.

## <a name="logging-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 'de oturum açma

ASP.NET Core, [Microsoft. Extensions. Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) NuGet paketi biçiminde günlük için yerleşik destek sağlar. Bu kitaplığın temel kısımları Web SDK 'sına dahildir, bu yüzden el ile yüklemeniz gerekmez. Varsayılan olarak, günlük iletileri standart çıktıya ("konsol") ve herhangi bir ekli hata ayıklayıcıya yazılır. Kalıcı dış veri depolarına Günlükler yazmak için [isteğe bağlı günlük havuzu paketlerini](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers)içeri aktarmanız gerekebilir.

ASP.NET Core gRPC çerçevesi, bu günlüğe kaydetme çerçevesine ayrıntılı tanılama günlüğü iletileri yazar ve bu sayede uygulamanızın kendi iletileriyle birlikte işlenebilirler ve depolanabilir.

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

İstekler ve özel durumlar gibi birçok günlük iletisi ASP.NET Core ve gRPC çerçevesi bileşenleri tarafından sağlanır. Alt düzey sorunlar yerine uygulama mantığı hakkında ayrıntı ve bağlam sağlamak için kendi günlük iletilerinizi ekleyin.

Günlük iletilerini ve kullanılabilir günlük havuzları ve hedefleri yazma hakkında daha fazla bilgi için bkz. [.NET Core ve ASP.NET Core oturum açma](/aspnet/core/fundamentals/logging/).

## <a name="metrics-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 'de ölçümler

.NET Core çalışma zamanı, ölçümleri yayma ve gözlemlemek için bir bileşen kümesi sağlar. Bunlar, <xref:System.Diagnostics.Tracing.EventSource> ve <xref:System.Diagnostics.Tracing.EventCounter> sınıfları gibi API 'Leri içerir. Bu API 'Ler, dış süreçler tarafından tüketilen, [DotNet sayaçları genel aracı](../../core/diagnostics/dotnet-counters.md)veya Windows Için olay izleme gibi temel sayısal verileri yayabilir. Kendi kodunuzda `EventCounter` kullanma hakkında daha fazla bilgi için bkz. [EventCounter tanıtımı](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

Daha gelişmiş ölçümler ve ölçüm verilerini daha geniş veri depolarına yazmak için, [uygulama ölçümleri](https://www.app-metrics.io)adlı açık kaynaklı bir projeyi deneyebilirsiniz. Bu kitaplıklar paketi kodunuzu işaretlemek için kapsamlı bir tür kümesi sağlar. Ayrıca, Prometheus ve ımexdb gibi zaman serisi veritabanlarını içeren farklı türlerdeki hedeflere yönelik ölçümleri yazmak için paketler sağlar ve [Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview). [App. ölçümler. AspNetCore. Mvc](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) NuGet paketi, ASP.NET Core çerçevesi ile tümleştirme aracılığıyla otomatik olarak oluşturulan kapsamlı bir temel ölçümler kümesi ekler. Proje Web sitesi, [Grafana](https://grafana.com/) görselleştirme platformu ile bu ölçümleri görüntülemeye yönelik [Şablonlar](https://www.app-metrics.io/samples/grafana/) sağlar.

### <a name="produce-metrics"></a>Ölçüm üretin

Çoğu ölçüm platformu aşağıdaki türleri destekler:

| Ölçüm türü | Açıklama |
| ----------- | ----------- |
| Sayaç     | İstekler ve hatalar gibi ne sıklıkla bir şeyin gerçekleştiğini izler. |
| Ölçer       | Etkin bağlantılar gibi zaman içinde değişen tek bir değer kaydeder. |
| Histogram   | Değerlerin bir dağılımını rastgele sınırlar arasında ölçer. Örneğin, bir histogram veri kümesi boyutunu izleyebilir, kaç tane < bir kayıt olduğunu, kaç tane 11-100 kaydı olduğunu, kaç adet 101-1000 kaydı olduğunu ve kaç tane > 1000 kaydı olduğunu gösterebilir. |
| si       | Bir olayın çeşitli zaman yayıldığında oluşma oranını ölçer. |
| Zamanlayıcı       | Etkinlik süresini ve oluşma hızını izler, histogram olarak depolanır. |

*Uygulama ölçümlerini*kullanarak, bağımlılık ekleme yoluyla bir `IMetrics` arabirimi elde edilebilir ve bir GRPC hizmeti için bu ölçülerden herhangi birini kaydetmek için kullanılır. Aşağıdaki örnek, zaman içinde yapılan `Get` isteklerinin sayısını nasıl saymayı gösterir:

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

Ölçüm verilerini görselleştirmeye yönelik geçerli go çözümü, çok çeşitli depolama sağlayıcılarıyla birlikte [Grafana](https://grafana.com). Aşağıdaki görüntüde, StockData örneğini çalıştıran Linkerd hizmet kafeslerinden alınan ölçümleri görüntüleyen örnek bir Grafana panosu gösterilmektedir:

![Grafana panonun ekran görüntüsü](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>Ölçüm tabanlı uyarı

Ölçüm verilerinin sayısal doğası, uyarı sistemlerini, geliştiricilerin veya Destek mühendislerinin bir değer tanımlı tolerans dışında kaldığında geliştiricilere bildirmek için uygun olduğu anlamına gelir. Zaten bahsedilen platformlar, e-postalar, metin iletileri veya Pano içi görselleştirmeler dahil olmak üzere çeşitli seçenekler aracılığıyla uyarı desteği sağlar.

## <a name="distributed-tracing"></a>Dağıtılmış izleme

Dağıtılmış izleme, mikro hizmetler ve dağıtılmış mimarilerin artan kullanımını gösteren, izleme sırasında görece son bir geliştirmede oluşur. İstemci tarayıcısından, uygulamadan veya cihazdan gelen tek bir istek birçok adım ve alt isteklere ayrılabilir ve bir ağ genelinde birçok hizmetin kullanımını içerir. Bu, günlük iletilerinin ve ölçümlerinin tetiklediği belirli bir istekle ilişkilendirilmesi güç sağlar. Dağıtılmış izleme, isteklere tanımlayıcılar uygular ve bu, günlüklerin ve ölçümlerin belirli bir işlemle bağıntılı olmasını sağlar. Bu, [WCF 'nin uçtan uca izlemeye](../../framework/wcf/diagnostics/tracing/end-to-end-tracing.md)benzerdir, ancak birden çok platformda uygulanır.

Dağıtılmış izleme popülerliği arttı ve standartlaştırmaya başlıyor. Bulut Yerel Bilgi Işlem altyapısı, [Açık izleme standardı](https://opentracing.io)oluşturdu ve [Deleger](https://www.jaegertracing.io/) ve [elastik APM](https://www.elastic.co/products/apm)gibi arka uçlar ile çalışmaya yönelik satıcıya ait kitaplıkları sağlamaya çalışıyor. Aynı zamanda, Google aynı sorun kümesini karşılamak için [Opencensus projesini](https://opencensus.io/) oluşturmuştur. Bu iki proje, gelecekteki sektörün sektör standardı olacak şekilde yeni bir proje olan [Opentelemetriyi](https://opentelemetry.io)birleştiriyor.

### <a name="how-distributed-tracing-works"></a>Dağıtılmış izlemenin nasıl çalıştığı

Dağıtılmış izleme, tek bir *izlemenin*parçası olanadlandırılmış, zaman aşımına uğramış işlemler, bir sistemin birden çok düğümünde işlemeyi içerebilir. Yeni bir işlem başlatıldığında, benzersiz tanımlayıcı ile bir izleme oluşturulur. Her alt işlem için, kendi tanımlayıcısı ve izleme tanımlayıcısı ile bir span oluşturulur. İstek sistem etrafında geçerken, çeşitli bileşenler *üst*ilişkilerini içeren *alt* yayılma oluşturabilir. Bir yayılma, izleme ve yayma tanımlayıcılarını ve ayrıca anahtar ve değer çiftleri ( *Bagaj*adı verilir) biçimindeki yararlı verileri içeren bir *içeriğe*sahiptir.

### <a name="distributed-tracing-with-diagnosticsource"></a>`DiagnosticSource` ile dağıtılmış izleme

.NET Core, dağıtılmış izlemeler ve yayılmalar için iyi eşleşen bir iç modüle sahiptir: [Diagnosticsource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide). Ayrıca, bir işlem içinde tanılamayı oluşturmak ve kullanmak için basit bir yol sağlamak üzere `DiagnosticSource` modülü bir *etkinlik*kavramıdır. Etkinlik etkin bir şekilde dağıtılmış izlemenin veya bir izleme içindeki yayılımın bir uygulamasıdır. Modülün iç işlevleri, tanımlayıcıları ayırmak da dahil olmak üzere üst/alt etkinliklerden yararlanın. `Activity` türünü kullanma hakkında daha fazla bilgi için bkz. [GitHub 'Da etkinlik Kullanıcı Kılavuzu](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide).

`DiagnosticSource` çekirdek Framework 'ün bir parçası olduğundan, çeşitli çekirdek bileşenleri tarafından desteklenir. Bunlar, gRPC çerçevesinde açık destek de dahil olmak üzere <xref:System.Net.Http.HttpClient>, Entity Framework Core ve ASP.NET Core içerir. ASP.NET Core bir istek aldığında, [W3C Trace bağlam](https://www.w3.org/TR/trace-context) standardı ile eşleşen BIR çift http üst bilgisi olup olmadığını denetler. Üstbilgiler bulunursa bir etkinlik, üst bilgilerden kimlik değerleri ve bağlamı kullanılarak başlatılır. Üst bilgi bulunmazsa, standart biçimle eşleşen üretilen kimlik değerleriyle bir etkinlik başlatılır. Bu etkinliğin ömrü boyunca Framework veya uygulama kodu tarafından oluşturulan tüm Tanılamalar, izleme ve span tanımlayıcılarıyla etiketlenebilir. `HttpClient` desteği, her istekte geçerli bir etkinliği denetleyerek ve izleme üstbilgilerini giden isteğe otomatik olarak ekleyerek bunu daha fazla genişletir.

ASP.NET Core gRPC istemci ve sunucu kitaplıkları, `DiagnosticSource` ve `Activity`yönelik açık destek içerir ve Etkinlikler oluşturup üstbilgi bilgilerini otomatik olarak kullanabilir ve kullanır.

> [!NOTE]
> Tüm bu yalnızca bir dinleyicinin tanılama bilgilerini tükettiği durumlarda gerçekleşir. Dinleyici yoksa, hiçbir Tanılama yazılmaz ve hiçbir etkinlik oluşturulmaz.

### <a name="add-your-own-diagnosticsource-and-activity"></a>Kendi `DiagnosticSource` ve `Activity` ekleyin

Kendi tanılamayı eklemek veya uygulama kodunuzda açık yayılma oluşturmak için, bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener) ve [etkinlik Kullanıcı Kılavuzu](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage).

### <a name="store-distributed-trace-data"></a>Dağıtılmış izleme verilerini depola

Yazma sırasında, Opentelemetri projesi hala erken aşamalarındayken ve yalnızca alfa kalite paketleri .NET uygulamaları için kullanılabilir. OpenTracing projesi şu anda daha fazla yetişkin kitaplığı sunmaktadır.

OpenTracing API 'SI aşağıdaki bölümde açıklanmıştır. Bunun yerine uygulamanızda Opentelemetri API 'sini kullanmak istiyorsanız GitHub 'da [opentelemetri .NET SDK deposuna](https://github.com/open-telemetry/opentelemetry-dotnet) bakın.

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>Dağıtılmış izleme verilerini depolamak için OpenTracing paketini kullanın

[Opentracing NuGet paketi](https://www.nuget.org/packages/OpenTracing/) , tüm opentracing uyumlu arka uçları destekler (`DiagnosticSource`bağımsız olarak kullanılabilir). Opentracing API katkıları projesinden [opentracing. contrib. NetCore](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/)'a ek bir paket vardır. Bu paket bir `DiagnosticSource` dinleyicisi ekler ve olayları ve etkinlikleri otomatik olarak arka uca yazar. Bu paketin etkinleştirilmesi, NuGet 'den yüklemek ve `Startup` sınıfınıza bir hizmet olarak eklemek kadar basittir.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

OpenTracing paketi bir Özet katmanıdır ve bu nedenle arka uca özel uygulama gerektirir. OpenTracing API uygulamaları aşağıdaki açık kaynak arka uçları için kullanılabilir.

| Name | Paket | Websitesi |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| Elastik APM | [Elastik. APM. NetCoreAll](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

.NET için opentracing API 'si hakkında daha fazla bilgi için GitHub 'daki [opentracing ve C# ](https://github.com/opentracing/opentracing-csharp) [opentracing contrib C#/.NET Core](https://github.com/opentracing-contrib/csharp-netcore) depoları konusuna bakın.

>[!div class="step-by-step"]
>[Önceki](load-balancing.md)
>[İleri](appendix.md)
