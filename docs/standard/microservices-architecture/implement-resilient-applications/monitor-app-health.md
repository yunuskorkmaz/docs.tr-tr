---
title: Sistem durumu izleme
description: Sistem durumu izleme uygulama yollarından keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 90beb8073cd169b0a68dc0025d8cd815ccb5a308
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464014"
---
# <a name="health-monitoring"></a>Sistem durumu izleme

Sistem durumu izleme, kapsayıcılar ve mikro hizmet durumu hakkında neredeyse gerçek zamanlı bilgi izin verebilirsiniz. Sistem durumu izleme, kritik işletme mikro hizmetler birçok yönünü ve düzenleyicileri kısmi uygulama yükseltmeleri aşamalarında, daha sonra açıklandığı gibi gerçekleştirin, özellikle önemlidir.

Mikro hizmet tabanlı uygulamalar genellikle sinyal kullanabilir veya kendi performans izleyicileri, zamanlayıcılar ve düzenleyicileri birçok izlemenize olanak sağlamak için sistem durumu denetimleri. Hizmetleri "I canlı" bir sinyal çeşit isteğe bağlı veya bir zamanlamaya göre gönderemiyorsanız riskleri uygulamanızı yüz güncelleştirmelerini dağıtma veya yalnızca çok geç hatalarını algılamak ve ana kesintilerine sona erdirebilirsiniz zincirleme hatalara durdurmak mümkün olmaması.

Tipik modelinde Hizmetleri durumlarını hakkında raporlar gönderin ve uygulama durumunu durumunun genel bir görünümünü sağlamak için bu bilgileri toplanır. Bir orchestrator kullanıyorsanız, küme uygun şekilde işlem yapabilmesi, düzenleyicinin küme sistem durumu bilgilerini sağlayabilir. Uygulamanız için özelleştirilmiş, yüksek kaliteli sistem durumu raporlama yatırım yaparsanız, algılayın ve çalışan uygulamanız için çok daha kolay sorunları giderin.

## <a name="implement-health-checks-in-aspnet-core-services"></a>ASP.NET Core Hizmetleri uygulama durum denetimleri

Bir ASP.NET Core mikro hizmet veya web uygulama geliştirirken, ASP .NET Core 2.2 içinde sunulan yerleşik sistem durumu denetimleri özelliğini kullanabilirsiniz. Çoğu gibi ASP.NET Core özellikleri, sistem durumu denetimleri bir dizi hizmet ve bir ara yazılım birlikte gelir.

Sistem durumu denetimi Hizmetleri ve ara yazılım kullanın ve uygulamanız (örneğin, bir SQL Server veritabanı veya bir uzak API'ye) için gerekli olan herhangi bir dış kaynağa düzgün çalıştığını doğrulamak olanak veren özellikler sağlamak kolaydır. Bu özelliği kullandığınızda, daha sonra anlatıldığı şekilde resource sağlam, anlamı da karar verebilirsiniz.

Bu özelliği etkili bir şekilde kullanmak için önce mikro Hizmetleri services'ı yapılandırmanız gerekir. İkinci olarak, sorgular bir ön uç uygulaması için sistem durumu raporlarının gerekir. Ön uç uygulaması, bir özel raporlama uygulaması olabilir ya da uygun şekilde tepki verebilir bir orchestrator kendisini olabileceği için sağlık durumlarını.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Arka uç ASP.NET mikro hizmetlerin de HealthChecks özelliğini kullanma

Bu bölümde, örnek ASP.NET Core 2.2 Web API uygulamasında HealthChecks özelliği nasıl kullanıldığını öğreneceksiniz. Bu özelliği hizmetine gibi büyük ölçekli mikro Hizmetler uygulaması sonraki bölümde açıklanmıştır. Başlamak için her bir mikro hizmet durumu sağlıklı nelerden tanımlamanız gerekir. Örnek uygulamada, mikro hizmet API'si, HTTP üzerinden erişilebilir ve ilgili SQL Server veritabanını da kullanılabilir, mikro hizmetler iyi durumda.

Yerleşik API'leri ile .NET Core 2.2 Hizmetleri, yapılandırabileceğiniz ekleme mikro hizmet ve bu şekilde bağımlı SQL Server veritabanı için sistem durumunu denetleyin:

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

Önceki kodda, `services.AddHealthChecks()` yöntemi yapılandırır bir durum kodu döndüren temel bir HTTP denetimini **200** "Sağlıklı" ile.  Ayrıca `AddCheck()` özel bir genişletme yöntemi yapılandırır `SqlConnectionHealthCheck` ilgili SQL veritabanının durumu denetler.

`AddCheck()` Yöntemi, belirtilen ada ve uygulama türü ile yeni bir sistem durumu denetimi ekler `IHealthCheck`. Birden çok durum denetimleri kadar tüm denetimleri sağlıklı bir mikro hizmet "iyi" duruma sağlamayacak şekilde AddCheck yöntemi kullanarak ekleyebilirsiniz.

`SqlConnectionHealthCheck` uygulayan özel bir sınıf `IHealthCheck`, oluşturucu parametresi olarak bir bağlantı dizesi alır ve SQL veritabanı bağlantısı başarılı olup olmadığını denetlemek için basit bir sorgu yürütür. Döndürür `HealthCheckResult.Healthy()` sorgu başarıyla yürütüldü ve bir `FailureStatus` gerçek özel durumuyla başarısız olduğunda.

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

Önceki kodda, dikkat `Select 1` veritabanı durumunu kontrol etmek için kullanılan sorgu. Mikro hizmetlerin kullanılabilirliğini izlemek için Kubernetes ve Service Fabric gibi düzenleyicileri düzenli aralıklarla sistem durumu denetimleri mikro Hizmetleri test etmek için istekleri göndererek gerçekleştirir. Böylece bu işlemler, hızlı ve daha yüksek bir kullanımı kaynakların neden olmayan veritabanı sorgularınızı verimli tutmak önemlidir.

Son olarak, url yoluyla "HC" yanıt veren bir ara yazılım oluşturun:

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

Uç nokta `<yourmicroservice>/hc` olan çağrılır, yapılandırılan tüm sistem durumu denetimleri çalıştırır `AddHealthChecks()` sınıfında başlatma yöntemi ve sonucu görüntüler.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Hizmetine HealthChecks uygulama

Mikro hizmetler hizmetine görevini gerçekleştirmek için birden çok Hizmetleri'ni kullanır. Örneğin, `Catalog.API` hizmetine gelen mikro hizmet, Azure Blob Depolama, SQL Server ve RabbitMQ gibi birçok hizmet bağlıdır. Bu nedenle, bazı sistem durumu denetimleri kullanılarak eklenen sahip `AddCheck()` yöntemi. Her bir bağlı hizmet için özel bir `IHealthCheck` ilgili sistem durumunu tanımlar uygulama eklenmesi gerekiyor.

Açık kaynaklı proje [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) üzerinde .NET Core 2.2 oluşturulan bu enterprise hizmetlerinin her biri için özel sistem durumu denetimi uygulamaları sağlayarak bu sorunu çözer. Her sistem durumu denetimi, projeye kolayca eklenebilen tek bir NuGet paketi olarak kullanılabilir. Hizmetine bunları kapsamlı bir şekilde kendi mikro Hizmetleri kullanın.

Örneğin, `Catalog.API` mikro hizmet, aşağıdaki NuGet paketleri eklendi:

![Çözüm Gezgini görünümü nerede AspNetCore.Diagnostics.HealthChecks NuGet paketlerini başvurulan Catalog.API projenin](./media/image6.png)

**Şekil 8-7**. Özel durum AspNetCore.Diagnostics.HealthChecks kullanarak Catalog.API içinde uygulanan denetimleri

Aşağıdaki kodda, bağımlı her hizmet için sistem durumu denetimi uygulamaları eklenir ve ardından Ara yazılım yapılandırılır:

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

Son olarak, "/ HC" uç noktası dinleyecek şekilde HealthCheck ara yazılım ekleyin:

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Mikro hizmetlerin sistem durumlarına raporlamak sorgulama

Sağlıksız olması durumunda bu makalede anlatıldığı gibi sistem durumu denetimleri yapılandırdıysanız ve Docker'da çalışan mikro hizmet sahip olduğunda, doğrudan bir tarayıcıdan denetleyebilirsiniz. Kapsayıcı dış Docker ana bilgisayar IP üzerinden veya aracılığıyla erişebilmesi için kapsayıcı bağlantı noktasından Docker konağı yayımlamak sahip olduğunuz `localhost`Şekil 8-8 ' gösterildiği gibi.

![Sistem durumu denetimi tarafından döndürülen JSON yanıtı tarayıcı görünümü](./media/image7.png)

**Şekil 8-8**. Tek bir hizmet tarayıcısından sistem durumunu denetleme

Bu test, gördüğünüz gibi `Catalog.API` sağlıklı, 200 HTTP durum ve durum bilgileri JSON biçiminde döndüren mikro hizmet (5101 bağlantı noktasında çalışıyor). Sistem durumu denetimi kendisini sağlıklı olarak rapor için hizmet durumunu, SQL Server veritabanı bağımlılık ve RabbitMQ, ayrıca kullanıma.

## <a name="use-watchdogs"></a>Watchdogs kullanın

Bir izleme sistem durumu izleme ve yük Hizmetleri ve mikro hizmetler hakkında rapor sistem durumu ile sorgulayarak ayrı bir hizmet olan `HealthChecks` kitaplığı sunulan daha önce. Bu işlem, tek bir hizmette bir görünümü temel alarak değil algılanır hataları önlemeye yardımcı olabilir. Watchdogs de iyi bir kullanıcı etkileşimi olmadan bilinen koşulları için düzeltme eylemleri gerçekleştirebilen konak koda yerdir.

Şekil 8-9'da gösterildiği örnek sistem durumu denetimi raporları görüntüleyen bir web sayfası hizmetine örnek içerir. Mikro hizmetler ve web uygulamalarının durumu hizmetine yalnızca gösterdiğinden, olabilir basit izleme budur. Genellikle, iyi durumda olmayan durumlar algıladığında bir bekçi ayrıca eylemleri gerçekleştirir.

Neyse ki, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) ayrıca sağlar [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) sistem durumu denetimini görüntülemek için kullanılan NuGet paketini yapılandırılmış bir URI'leri oluşur.

![Sistem durumu hizmetine gelen tüm mikro hizmetler, gösteren WebStatus uygulamasının tarayıcı görünümü](./media/image8.png)

**Şekil 8-9**. Hizmetine örnek sistem durumu denetimi raporu

Özet olarak, her bir mikro hizmetin ait "/ HC" uç noktası bu izleme hizmetini sorgular. İçinde tanımlanan tüm sistem durumu denetimleri yürütmek ve genel sistem durumuna bağlı tüm denetimleri olarak döndürür. HealthChecksUI birkaç yapılandırma girdileri ve iki izleme hizmeti Startup.cs eklenmesi gereken kod satırı ile kullanmak kolay bir işlemdir.

Sistem durumu için örnek yapılandırma dosyası, UI kontrol edin:

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

HealthChecksUI ekler Startup.cs dosyası:

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

## <a name="health-checks-when-using-orchestrators"></a>Düzenleyiciler kullanırken sistem durumu denetimleri

Mikro hizmetlerin kullanılabilirliğini izlemek için Kubernetes ve Service Fabric gibi düzenleyicileri düzenli aralıklarla sistem durumu denetimleri mikro Hizmetleri test etmek için istekleri göndererek gerçekleştirir. Ne zaman bir orchestrator hizmet/kapsayıcı yönlendirme istekleri bu örneği durdurur, sağlıksız olduğunu belirler. Ayrıca genellikle, bu kapsayıcı yeni bir örneğini oluşturur.

Örneğin, çoğu düzenleyicileri, sistem durumu denetimleri kesintisiz dağıtımlarını yönetmek için kullanabilirsiniz. Yalnızca sağlıklı bir hizmeti/kapsayıcı değişiklikleri durumunu olacak orchestrator başlattığınızda hizmet/kapsayıcı örneklerine trafiği yönlendirme.

Bir orchestrator uygulama yükseltme yaparken, sistem durumu izleme özellikle önemlidir. Bazı düzenleyiciler (örneğin, Azure Service Fabric) Hizmetleri'nde aşamaları güncelleştirme — Örneğin, her uygulama yükseltmesi için küme yüzeyinde bir beşinci güncelleştirebilir. Aynı anda yükseltilir düğümleri kümesini şeklinde adlandırılan bir *yükseltme etki alanı*. Her bir yükseltme etki alanı yükseltildi ve kullanıcılar tarafından kullanılabilir sonra dağıtım için bir sonraki yükseltme etki alanına taşınmadan önce yükseltme etki alanı sistem durumu denetimleri geçmesi gerekir.

Bir diğer unsuru hizmet sistem durumu hizmetinden alınan ölçümleri bildiriyor. Bu, Service Fabric gibi bazı düzenleyiciler sistem durumu modeli, Gelişmiş bir özelliktir. Ölçümler, kaynak kullanımı dengelemek için kullanıldığından bir orchestrator kullanırken önemlidir. Ölçümleri de sistem durumu göstergesi olabilir. Örneğin, birçok mikro olan bir uygulama olabilir ve her örneği bir saniyede istekleri (RP'ler) ölçüm bildirir. Bir hizmetin başka bir hizmete daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsanız, orchestrator hizmet örnekleri bile kaynak kullanımını korumak için kümedeki yerleri.

Azure Service Fabric kendi sağladığını unutmayın [sistem durumu izleme modeli](/azure/service-fabric/service-fabric-health-introduction), basit bir sistem durumu denetimleri daha gelişmiş olduğu.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Gelişmiş izleme: Görselleştirme ve çözümleme uyarıları

İzleme son bölümü göre servis performansını raporlama ve bir sorun algılandığında uyarı olay akışını görselleştirme olduğu. Bu izleme açısını için farklı çözümler kullanabilirsiniz.

Açıklayan gösterilen özel sayfa gibi hizmetlerinizin durumunu gösteren basit bir özel uygulamalar kullanabilir [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Ya da olayların akışa göre uyarıları artırmak için Azure Application Insights gibi daha gelişmiş araçları kullanabilirsiniz.

Tüm olay akışlarını depoladığınız, son olarak, Microsoft Power BI veya Kibana veya Splunk gibi diğer çözümlerle verileri görselleştirmek için kullanabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

-   **HealthChecks ve ASP.NET Core HealthChecks kullanıcı Arabirimi**
    [https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks )

-   **Service Fabric sistem durumu izlemeye giriş**
    [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

-   **Azure Application Insights**
    [https://azure.microsoft.com/services/application-insights/](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite'e**
    [https://www.microsoft.com/en-us/cloud-platform/operations-management-suite](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
>[Önceki](implement-circuit-breaker-pattern.md)
>[İleri](../secure-net-microservices-web-applications/index.md)