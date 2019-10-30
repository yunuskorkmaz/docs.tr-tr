---
title: Sistem durumu izleme
description: Sistem durumu izlemeyi uygulamayla bir yolu bulun.
ms.date: 01/07/2019
ms.openlocfilehash: 2d43efa7b6cfb855a033ee4d766c64c2472ceb36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094077"
---
# <a name="health-monitoring"></a>Sistem durumu izleme

Sistem durumu izleme, kapsayıcılarınızın ve mikro hizmetlerinizin durumu hakkında neredeyse gerçek zamanlı bilgilere izin verebilir. Sistem durumu izleme, işletim mikro hizmetlerinin birden çok yönü için kritik öneme sahiptir ve bu, daha sonra açıklandığı gibi, bazı durumlarda, aşamalar halinde kısmi uygulama yükseltmeleri gerçekleştirirken özellikle önemlidir.

Mikro hizmet tabanlı uygulamalar genellikle performans izleyicilerinin, zamanlayıcılar ve düzenleyicilerin çok sayıda hizmeti izlemesini sağlamak için sinyal veya sistem durumu denetimleri kullanır. Hizmetler, istek üzerine veya bir zamanlamaya göre bir miktar "canlım" sinyali gönderebiliyorsa, güncelleştirmeleri dağıtırken uygulamanız risk altında olabilir veya yalnızca çok geç olan sorunları algılayabilir ve büyük kesintilerde ortaya çıkabilecek basamaklı sorunları durduramaz.

Tipik modelde, hizmetler durumları hakkında raporlar gönderir ve uygulamanızın sistem durumu durumunun genel bir görünümünü sağlamak için bu bilgiler toplanır. Orchestrator kullanıyorsanız, kümenin uygun şekilde davranabilmesi için Orchestrator kümesine sistem durumu bilgileri sağlayabilirsiniz. Uygulamanız için özelleştirilmiş yüksek kaliteli sistem durumu raporlaması yatırdığınızda, çalışan uygulamanızın sorunlarını daha kolay algılayabilir ve giderebilirsiniz.

## <a name="implement-health-checks-in-aspnet-core-services"></a>ASP.NET Core hizmetlerinde sistem durumu denetimleri uygulama

ASP.NET Core mikro hizmet veya Web uygulaması geliştirirken, ASP .NET Core 2,2 ' de yayınlanan yerleşik sistem durumu denetimleri özelliğini kullanabilirsiniz. Birçok ASP.NET Core özelliği gibi, sistem durumu denetimleri de bir dizi hizmet ve bir ara yazılım ile gelir.

Sistem durumu denetimi Hizmetleri ve ara yazılımı kullanımı kolaydır ve uygulamanız için gerekli herhangi bir dış kaynak (SQL Server veritabanı veya uzak bir API gibi) düzgün çalışıp çalışmadığını doğrulamanıza olanak sağlayan yetenekler sağlar. Bu özelliği kullandığınızda, daha sonra açıklandığımız için kaynağın sağlıklı ne anlama geldiğini de seçebilirsiniz.

Bu özelliği etkin bir şekilde kullanmak için, önce mikro hizmetinizdeki hizmetleri yapılandırmanız gerekir. İkincisi, sistem durumu raporlarını sorgulayan bir ön uç uygulamasına ihtiyacınız vardır. Bu ön uç uygulama özel bir raporlama uygulaması olabilir veya sistem durumu durumlarına göre tepki verebilecek bir Orchestrator 'ın kendisi olabilir.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Arka uç ASP.NET mikro hizmetlerinizin Healthdenetimleri özelliğini kullanın

Bu bölümde, Healthdenetimleri özelliğinin örnek bir ASP.NET Core 2,2 Web API uygulamasında nasıl kullanıldığını öğreneceksiniz. EShopOnContainers gibi büyük ölçekli mikro hizmetlerde bu özelliğin uygulanması, sonraki bölümde açıklanmaktadır. Başlamak için, her mikro hizmet için sağlıklı durumu neyin oluşturduğunu tanımlamanız gerekir. Örnek uygulamada, mikro hizmet API 'sine HTTP üzerinden erişilebiliyorsa ve ilgili SQL Server veritabanı da kullanılabilir olduğunda mikro hizmetler sağlıklı olur.

.NET Core 2,2 ' de, yerleşik API 'Ler ile hizmetleri yapılandırabilir, mikro hizmet için bir sistem durumu denetimi ve bu şekilde bağımlı SQL Server veritabanı ekleyebilirsiniz:

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
    // Add a health check for a SQL database
    .AddCheck("MyDatabase", new SqlConnectionHealthCheck(Configuration["ConnectionStrings:DefaultConnection"]));
}
```

Önceki kodda `services.AddHealthChecks()` yöntemi, "sağlıklı" ile **200** durum kodunu döndüren temel bir http denetimini yapılandırır.  Ayrıca, `AddCheck()` uzantısı yöntemi, ilgili SQL veritabanının sistem durumunu denetleyen özel bir `SqlConnectionHealthCheck` yapılandırır.

`AddCheck()` yöntemi, belirtilen bir ad ve `IHealthCheck`türünde uygulamayla yeni bir sistem durumu denetimi ekler. AddCheck metodunu kullanarak birden çok sistem durumu denetimi ekleyebilirsiniz, bu nedenle bir mikro hizmet, tüm denetimleri sağlıklı olana kadar "sağlıklı" bir durum sağlamaz.

`SqlConnectionHealthCheck`, bir bağlantı dizesini Oluşturucu parametresi olarak alan ve SQL veritabanı bağlantısının başarılı olup olmadığını kontrol etmek için basit bir sorgu yürüten `IHealthCheck`uygulayan özel bir sınıftır. Sorgu başarıyla yürütülürse ve başarısız olduğunda gerçek özel duruma sahip bir `FailureStatus` `HealthCheckResult.Healthy()` döndürür.

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

Önceki kodda `Select 1` veritabanının durumunu denetlemek için kullanılan sorgu olduğunu unutmayın. Mikro hizmetlerinizin kullanılabilirliğini izlemek için, Kubernetes gibi düzenleyiciler ve Service Fabric mikro hizmetleri test etmek üzere istek göndererek düzenli aralıklarla durum denetimleri gerçekleştirir. Bu işlemlerin hızlı olması için veritabanı sorgularınızın etkili tutulması ve kaynakların daha yüksek kullanımına neden olması önemlidir.

Son olarak, "/HC" URL yoluna yanıt veren bir ara yazılım oluşturun:

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecks("/hc");
    //…
}
```

Uç nokta `<yourmicroservice>/hc` çağrıldığında, başlangıç sınıfındaki `AddHealthChecks()` yönteminde yapılandırılan tüm sistem durumu denetimlerini çalıştırır ve sonucu gösterir.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>EShopOnContainers 'da Healthdenetimlerin uygulanması

EShopOnContainers 'daki mikro hizmetler, görevini gerçekleştirmek için birden çok hizmete bağımlıdır. Örneğin, eShopOnContainers 'dan `Catalog.API` mikro hizmeti, Azure Blob depolama, SQL Server ve Kbbitmq gibi birçok hizmete bağlıdır. Bu nedenle, `AddCheck()` yöntemi kullanılarak birçok sistem durumu denetimi eklenmiştir. Her bağımlı hizmet için, ilgili sistem durumunu tanımlayan özel bir `IHealthCheck` uygulamasının eklenmesi gerekir.

Açık kaynaklı proje [Aspnetcore. Diagnostics. healthcheck](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) , .net Core 2,2 üzerinde oluşturulan bu kurumsal hizmetlerden her biri için özel sistem durumu denetimi uygulamaları sağlayarak bu sorunu çözer. Her bir sistem durumu denetimi, projeye kolaylıkla eklenebilen tek bir NuGet paketi olarak kullanılabilir. eShopOnContainers bunları, tüm mikro hizmetlerinde kapsamlı olarak kullanır.

Örneğin, `Catalog.API` mikro hizmetinde aşağıdaki NuGet paketleri eklendi:

![AspNetCore. Diagnostics. Healthdenetimlerinin NuGet paketlerine başvurduğu katalog. API projesinin Çözüm Gezgini görünümü](./media/image6.png)

**Şekil 8-7**. AspNetCore. Diagnostics. Healthdenetimleri kullanılarak Catalog. API dosyasında uygulanan özel durum denetimleri

Aşağıdaki kodda, her bağımlı hizmet için sistem durumu denetimi uygulamaları eklenir ve ardından ara yazılım yapılandırılır:

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

Son olarak, "/HC" uç noktasını dinlemek için HealthCheck ara yazılımını ekliyoruz:

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Mikro hizmetlerinizi, sistem durumu hakkında raporlamak için sorgulayın

Bu makalede açıklandığı şekilde sistem durumu denetimleri yapılandırdığınızda ve mikro hizmeti Docker 'da çalışıyorsa, iyi durumda bir tarayıcıdan doğrudan kontrol edebilirsiniz. Kapsayıcı bağlantı noktasını Docker konağında yayımlamanız gerekir. bu sayede, Şekil 8-8 ' de gösterildiği gibi, kapsayıcıya dış Docker ana bilgisayar IP 'si veya `localhost`aracılığıyla erişebilirsiniz.

![Bir sistem durumu denetimi tarafından döndürülen JSON yanıtının tarayıcı görünümü](./media/image7.png)

**Şekil 8-8**. Bir tarayıcıdan tek bir hizmetin sistem durumunu denetleme

Bu testte, `Catalog.API` mikro hizmetinin (5101 bağlantı noktasında çalışan) sağlıklı olduğunu, HTTP durum 200 ve durum bilgilerini JSON 'da döndürdüğünü görebilirsiniz. Hizmet Ayrıca, SQL Server veritabanı bağımlılığının ve Kbbitmq 'in sistem durumunu kontrol etti, bu nedenle sistem durumu denetimi kendisini sağlıklı olarak raporladı.

## <a name="use-watchdogs"></a>Watchdogs kullanma

İzleme, hizmetler genelinde sistem durumunu izleyebilecek ve daha önce tanıtılan `HealthChecks` kitaplığıyla sorgulama yaparak mikro hizmetlerle ilgili sistem durumunu rapor eden ayrı bir hizmettir. Bu, tek bir hizmetin görünümüne göre algılanamayan hataları önlemeye yardımcı olabilir. Watchdogs Ayrıca, Kullanıcı etkileşimi olmadan bilinen koşullar için düzeltme eylemleri gerçekleştirebilen kodu barındırmak için iyi bir yerdir.

EShopOnContainers örneği, Şekil 8-9 ' de gösterildiği gibi, örnek sistem durumu denetimi raporlarını görüntüleyen bir Web sayfası içerir. Bu, yalnızca mikro hizmetlerin ve eShopOnContainers 'daki Web uygulamalarının durumunu gösterdiği için, sahip olduğunuz en basit izleme budur. Genellikle bir izleme uygun olmayan durumları algıladığında de Eylemler gerçekleştirir.

Neyse ki, [aspnetcore. Diagnostics. healthcheck](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) Ayrıca, yapılandırılmış URI 'lerden gelen sistem durumu denetimi sonuçlarını göstermek Için kullanılabilen [Aspnetcore. HEALTHCHECK. UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet paketini de sağlar.

![EShopOnContainers 'daki tüm mikro hizmetlerin sistem durumunu gösteren WebStatus uygulamasının tarayıcı görünümü](./media/image8.png)

**Şekil 8-9**. EShopOnContainers 'daki örnek durum denetimi raporu

Özet olarak, bu izleme hizmeti her mikro hizmetin "/HC" uç noktasını sorgular. Bu, içinde tanımlanan tüm sistem durumu denetimlerini yürütür ve tüm bu denetimlerine bağlı olarak genel bir sistem durumu döndürür. Healthchecksuı, birkaç yapılandırma girişi ve izleme hizmetinin Startup.cs eklenmesi gereken iki satırlık kod ile kolayca tüketicektir.

Sistem durumu denetimi kullanıcı arabirimi için örnek yapılandırma dosyası:

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

Healthchecksuı ekleyen Startup.cs dosyası:

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config=> config.UIPath = “/hc-ui”);
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a>Düzenleyiciler kullanılırken durum denetimleri

Mikro hizmetlerinizin kullanılabilirliğini izlemek için, Kubernetes gibi düzenleyiciler ve Service Fabric mikro hizmetleri test etmek üzere istek göndererek düzenli aralıklarla durum denetimleri gerçekleştirir. Bir Orchestrator bir hizmetin/kapsayıcının sağlıksız olduğunu belirlediğinde, bu örneğe yönlendirme isteklerini sonlandırır. Ayrıca genellikle bu kapsayıcının yeni bir örneğini oluşturur.

Örneğin, çoğu düzenleyen, sıfır kesinti dağıtımlarını yönetmek için sistem durumu denetimlerini kullanabilir. Yalnızca bir hizmet/kapsayıcının durumu sağlıklı olarak değiştiğinde, Orchestrator başlatması trafiği hizmet/kapsayıcı örneklerine yönlendirmektedir.

Bir Orchestrator uygulama yükseltmesi gerçekleştirdiğinde sistem durumu izleme özellikle önemlidir. Bazı düzenleyiciler (Azure Service Fabric) aşamalarda güncelleştirme hizmetleri — Örneğin, her uygulama yükseltmesi için küme yüzeyinin bir beşinci birini güncelleştirebilir. Aynı anda yükseltilen düğüm kümesi, *yükseltme etki alanı*olarak adlandırılır. Her yükseltme etki alanı yükseltildikten ve kullanıcılar tarafından kullanılabilir olduktan sonra, dağıtım bir sonraki yükseltme etki alanına geçmeden önce bu yükseltme etki alanı, sistem durumu denetimleri iletmelidir.

Hizmet sistem durumunun başka bir yönü, hizmetten rapor ölçümleridir. Bu, Service Fabric gibi bazı düzenleyicilerinin durum modelinin gelişmiş bir özelliğidir. Kaynak kullanımını dengelemek için kullanıldıklarından, bir Orchestrator kullanılırken ölçümler önemlidir. Ölçümler Ayrıca sistem durumunun bir göstergesi olabilir. Örneğin, çok sayıda mikro hizmeti olan bir uygulamanız olabilir ve her örnek, saniye başına istek (RPS) ölçümünü rapor edebilir. Bir hizmet başka bir hizmetten daha fazla kaynak (bellek, işlemci vb.) kullanıyorsa, Orchestrator kaynak kullanımını bile sürdürmek için hizmet örneklerini kümedeki etrafında taşıyabilir.

Azure Service Fabric 'in kendi [sistem durumu izleme modelini](/azure/service-fabric/service-fabric-health-introduction)sağladığını, bu da basit sistem durumu denetimlerinden daha gelişmiş olduğunu unutmayın.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Gelişmiş izleme: görselleştirme, analiz ve uyarılar

İzlemenin son bölümü, olay akışını görselleştirme, hizmet performansını raporlama ve bir sorun algılandığında uyarma. İzlemenin bu yönü için farklı çözümler kullanabilirsiniz.

[Aspnetcore. Diagnostics. Healthdenetimlerini](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks)açıklayarak gösterilen özel sayfa gibi, hizmetlerinizin durumunu gösteren basit özel uygulamalar kullanabilirsiniz. Ya da olayları akışa göre uyarıları yükseltmek için [Azure izleyici](https://azure.microsoft.com/services/monitor/) gibi daha gelişmiş araçlar da kullanabilirsiniz.

Son olarak, tüm olay akışlarını depoluyorsanız, verileri görselleştirmek için Microsoft Power BI veya kibana ya da splunk gibi diğer çözümleri kullanabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core \ Için healthdenetimleri ve healthdenetimleri Kullanıcı arabirimi**
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Service Fabric sistem durumu Izlemeye giriş** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Izleyici**  
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[Önceki](implement-circuit-breaker-pattern.md)
>[İleri](../secure-net-microservices-web-applications/index.md)
