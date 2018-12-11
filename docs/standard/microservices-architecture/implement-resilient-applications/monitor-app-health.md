---
title: Sistem durumu izleme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Sistem durumu izleme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 35f6d773d714878f56a5e9151320072ebcd51e06
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145981"
---
# <a name="health-monitoring"></a>Sistem durumu izleme

Sistem durumu izleme, kapsayıcılar ve mikro hizmet durumu hakkında neredeyse gerçek zamanlı bilgi izin verebilirsiniz. Sistem durumu izleme, kritik işletme mikro hizmetler birçok yönünü ve düzenleyicileri kısmi uygulama yükseltmeleri aşamalarında, daha sonra açıklandığı gibi gerçekleştirin, özellikle önemlidir.

Mikro hizmet tabanlı uygulamalar genellikle sinyal kullanabilir veya kendi performans izleyicileri, zamanlayıcılar ve düzenleyicileri birçok izlemenize olanak sağlamak için sistem durumu denetimleri. Hizmetleri "I canlı" bir sinyal çeşit isteğe bağlı veya bir zamanlamaya göre gönderemiyorsanız riskleri uygulamanızı yüz güncelleştirmelerini dağıtma veya yalnızca çok geç hatalarını algılamak ve ana kesintilerine sona erdirebilirsiniz zincirleme hatalara durdurmak mümkün olmaması.

Tipik modelinde Hizmetleri durumlarını hakkında raporlar gönderin ve uygulama durumunu durumunun genel bir görünümünü sağlamak için bu bilgileri toplanır. Bir orchestrator kullanıyorsanız, küme uygun şekilde işlem yapabilmesi, düzenleyicinin küme sistem durumu bilgilerini sağlayabilir. Uygulamanız için özelleştirilmiş, yüksek kaliteli sistem durumu raporlama yatırım yaparsanız, algılayın ve çalışan uygulamanız için çok daha kolay sorunları giderin.

## <a name="implementing-health-checks-in-aspnet-core-services"></a>ASP.NET Core Hizmetleri sistem durumu uygulama denetler

Bir ASP.NET Core mikro hizmet veya web uygulama geliştirirken, bir bant dışı kitaplığı kullanabilirsiniz (değil resmi ASP.NETCore bir parçası olarak) adlı `HealthChecks` ASP.NET ekibinden. Şu anda kullanılabilir [GitHub deposunu](https://github.com/dotnet-architecture/HealthChecks).

Bu kitaplık kullanımı kolaydır ve uygulamanız (örneğin, bir SQL Server veritabanı veya Uzak API) için gereken tüm belirli dış kaynak düzgün şekilde çalıştığını doğrulama olanak sağlayan özellikler sunar. Bu kitaplığı kullandığınızda, daha sonra anlatıldığı şekilde resource sağlam, anlamı da karar verebilirsiniz.

Bu kitaplığı kullanmak için öncelikle mikro hizmetlerin kitaplıkta kullanmanız gerekir. İkinci olarak, sorgular bir ön uç uygulaması için sistem durumu raporlarının gerekir. Ön uç uygulaması, bir özel raporlama uygulaması olabilir ya da uygun şekilde tepki verebilir bir orchestrator kendisini olabileceği için sağlık durumlarını.

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Arka ucunuza ASP.NET mikro hizmetler HealthChecks kitaplıkta kullanma

HealthChecks kitaplığı hizmetine örnek uygulamada nasıl kullanıldığını görebilirsiniz. Başlamak için her bir mikro hizmet durumu sağlıklı nelerden tanımlamanız gerekir. Örnek uygulamada, mikro hizmetler, HTTP ve ilgili SQL Server veritabanını da kullanılabilir olup olmadığını API mikro hizmet erişilemez iyi durumda.

Gelecekte bir NuGet paketi olarak HealthChecks kitaplığını yüklemek mümkün olacaktır. Ancak bu makalenin yazıldığı tarih itibarıyla, indirmek ve çözümünüzün bir parçası olarak Kodu derlemek gerekir. Kullanılabilir kod klonlama https://github.com/dotnet-architecture/HealthChecks ve çözümünüze aşağıdaki klasörleri kopyalayın:

  - src/ortak
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ancak bu sürümü hizmetine Azure'da herhangi bir bağımlılığı olmadığından olanlar gibi ek denetimler de kullanabilirsiniz, bunun gerekmez. ASP.NET Core, hizmetine dayandığından, ASP.NET sistem durumu denetimleri ihtiyacınız yoktur.

Şekil 10-6 HealthChecks Kitaplığı Visual Studio, bir yapı taşı olarak herhangi bir mikro hizmetler tarafından kullanılmaya hazır gösterir.

![](./media/image6.png)

**Şekil 10-6**. ASP.NET Core HealthChecks kitaplığı kaynak kodunu bir Visual Studio çözümü içinde

Daha önce sunulan gibi her bir mikro hizmet projesine yapılacak ilk şey bir başvuru üç HealthChecks kitaplıkları eklemektir. Bundan sonra bu mikro hizmet içinde gerçekleştirmek istediğiniz sistem durumu denetimi eylemlerini ekleyin. Bu eylemler temel olarak diğer mikro hizmetler (HttpUrlCheck) veya veritabanlarını bağımlılıkları olan (şu anda SqlCheck\* SQL Server veritabanları için). Eylem içinde her ASP.NET mikro hizmet veya ASP.NET web uygulaması başlangıç sınıfı ekleyin.

Her hizmeti veya web uygulamasına bir AddHealthCheck yöntemi olarak HTTP ya da veritabanı tüm bağımlılıkları ekleyerek yapılandırılması gerekir. Örneğin, MVC web hizmetine uygulamadan birden çok hizmete bağlıdır, bu nedenle, sistem durumu denetimleri için eklenen çeşitli AddCheck yöntemler vardır.

Örneğin, aşağıdaki kodda nasıl Kataloğu mikro hizmet kendi SQL Server veritabanı üzerinde bir bağımlılık ekler görebilirsiniz.

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

Ancak, hizmetine MVC web uygulaması, mikro hizmetler geri kalanı üzerinde birden çok bağımlılıkları vardır. Bu nedenle, bir AddUrlCheck yöntemini her mikro hizmet için aşağıdaki örnekte gösterildiği gibi çağırır:

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

Bu nedenle, tüm denetimleri de sağlıklı olduğunu kadar bir mikro hizmet "iyi" duruma sağlamaz.

Mikro hizmet veya SQL Server bir bağımlılık yoksa, yalnızca bir Healthy("Ok") onay eklemeniz gerekir. Hizmetine basket.api mikro hizmet kodudur. (Redis cache sepet mikro hizmet kullanır, ancak kitaplık bir Redis sistem durumu denetimi sağlayıcısı henüz içermez.)

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

UseHealthChecks etkinleştirmek olan sistem durumu onay uç noktası kullanıma sunmak bir hizmeti veya web uygulaması için (\[*url\_için\_sistem durumu\_denetler*\]) uzantısı yöntem. Bu yöntem WebHostBuilder ana yöntemde, ASP.NET Core hizmeti veya web uygulaması, aşağıdaki kodda gösterildiği gibi sağ UseKestrel sonra Program sınıfının düzeyi gider.

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

İşlem şu şekilde çalışır: her mikro hizmet uç noktası HC kullanıma sunar. Uç noktanın HealthChecks kitaplığı ASP.NET Core ara yazılımı tarafından oluşturulur. Uç noktanın çağrıldığında başlangıç sınıfındaki AddHealthChecks yöntemi yapılandırılan tüm sistem durumu denetimleri çalıştırır.

Bir bağlantı noktası veya yol UseHealthChecks yöntemi bekliyor. Bu bağlantı noktası veya yol, hizmetin sistem durumunu denetlemek için uç noktadır. Örneğin, katalog mikro hizmet yolu HC kullanır.

### <a name="caching-health-check-responses"></a>Sistem durumu onay yanıtları önbelleğe alma

Çok sık hizmetlerinizde bir hizmet reddi (DoS) neden istemediğiniz veya yalnızca kaynak kontrol ederek hizmet performansı etkileyecek şekilde istemiyorsanız bu yana önbelleğe döndürür ve önbelleğe alma süresi her sistem durumu denetimi için yapılandırma kullanabilirsiniz.

Varsayılan olarak, önbelleğe alma süresi 5 dakika ile dahili olarak ayarlanır, ancak bu önbelleğe alma süresi şu kod gibi her sistem durumu denetimi üzerinde değiştirebilirsiniz:

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>Mikro hizmetlerin sistem durumlarına raporlamak sorgulama

Sistem durumu denetimleri, bir Docker mikro hizmet çalışmaya başladıktan sonra burada açıklanan şekilde yapılandırdığınızda, sağlıksız olması durumunda doğrudan bir tarayıcıdan denetleyebilirsiniz. (Bu kapsayıcı veya dış Docker ana bilgisayar IP'SİNİN localhost aracılığıyla erişebilmesi için Docker konağı kapsayıcı bağlantı noktası yayımladığınız gerektirir.) Şekil 10-7, bir tarayıcı ve karşılık gelen yanıt bir istek gösterir.

![](./media/image7.png)

**Şekil 10-7**. Tek bir hizmet tarayıcısından sistem durumunu denetleme

Bu test, (5101 bağlantı noktasında çalışan) catalog.api mikro hizmet sağlıklı, 200 HTTP durum ve durum bilgileri JSON biçiminde döndüren görebilirsiniz. Ayrıca dahili olarak hizmet aynı zamanda SQL Server veritabanı bağımlılık durumunu iade etmeniz ve sistem durumu denetimi kendisini sağlıklı olarak rapor edilmiştir, anlamına gelir.

## <a name="using-watchdogs"></a>Watchdogs kullanma

Bir izleme sistem durumu izleyin ve daha önce sunulan HealthChecks kitaplığıyla sorgulayarak Hizmetleri ve mikro hizmetler hakkında rapor sistem genelinde yük ayrı bir hizmettir. Bu işlem, tek bir hizmette bir görünümü temel alarak değil algılanır hataları önlemeye yardımcı olabilir. Watchdogs de iyi bir kullanıcı etkileşimi olmadan bilinen koşulları için düzeltme eylemleri gerçekleştirebilen konak koda yerdir.

Şekil 10-8'de gösterildiği örnek sistem durumu denetimi raporları görüntüleyen bir web sayfası hizmetine örnek içerir. Bu, sahip olabilir, en basit izleme, mikro hizmetler ve web uygulamalarını hizmetine durumunu itibaren tüm olduğunu gösterir. Genellikle, iyi durumda olmayan durumlar algıladığında bir bekçi ayrıca eylemleri gerçekleştirir.

![](./media/image8.png)

**Şekil 10-8**. Hizmetine örnek sistem durumu denetimi raporu

Özet olarak, ASP.NET, ASP.NET Core HealthChecks kitaplığının tek sistem durumu onay uç noktası için her bir mikro hizmetin ihtiyacımızı karşılıyor. İçinde tanımlanan tüm sistem durumu denetimleri yürütmek ve genel sistem durumuna bağlı tüm denetimleri olarak döndürür.

Gelecekteki dış kaynaklara yeni sistem durumu denetimleri Genişletilebilir HealthChecks kitaplığıdır. Örneğin, gelecekte kitaplığı diğer veritabanları ve Redis önbelleği için sistem durumu denetimleri olacağını umuyoruz. Birden çok hizmet veya uygulama bağımlılıkları raporlama sistem durumu kitaplığı sağlar ve sonra bu sistem durumu denetimleri üzerinde temel eylemleri gerçekleştirebilir.

## <a name="health-checks-when-using-orchestrators"></a>Düzenleyiciler kullanırken sistem durumu denetimleri

Mikro hizmetlerin kullanılabilirliğini izlemek için Docker Swarm, Kubernetes ve Service Fabric gibi düzenleyicilerle düzenli aralıklarla sistem durumu denetimleri mikro Hizmetleri test etmek için istekleri göndererek gerçekleştirir. Ne zaman bir orchestrator hizmet/kapsayıcı yönlendirme istekleri bu örneği durdurur, sağlıksız olduğunu belirler. Ayrıca genellikle, bu kapsayıcı yeni bir örneğini oluşturur.

Örneğin, çoğu düzenleyicileri, sistem durumu denetimleri kesintisiz dağıtımlarını yönetmek için kullanabilirsiniz. Yalnızca sağlıklı bir hizmeti/kapsayıcı değişiklikleri durumunu olacak orchestrator başlattığınızda hizmet/kapsayıcı örneklerine trafiği yönlendirme.

Bir orchestrator uygulama yükseltme yaparken, sistem durumu izleme özellikle önemlidir. Bazı düzenleyiciler (örneğin, Azure Service Fabric) Hizmetleri'nde aşamaları güncelleştirme — Örneğin, her uygulama yükseltmesi için küme yüzeyinde bir beşinci güncelleştirebilir. Aynı anda yükseltilir düğümleri kümesini şeklinde adlandırılan bir *yükseltme etki alanı*. Her bir yükseltme etki alanı yükseltildi ve kullanıcılar tarafından kullanılabilir sonra dağıtım için bir sonraki yükseltme etki alanına taşınmadan önce yükseltme etki alanı sistem durumu denetimleri geçmesi gerekir.

Bir diğer unsuru hizmet sistem durumu hizmetinden alınan ölçümleri bildiriyor. Bu, Service Fabric gibi bazı düzenleyiciler sistem durumu modeli, Gelişmiş bir özelliktir. Ölçümler, kaynak kullanımı dengelemek için kullanıldığından bir orchestrator kullanırken önemlidir. Ölçümleri de sistem durumu göstergesi olabilir. Örneğin, birçok mikro olan bir uygulama olabilir ve her örneği bir saniyede istekleri (RP'ler) ölçüm bildirir. Bir hizmetin başka bir hizmete daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsanız, orchestrator hizmet örnekleri bile kaynak kullanımını korumak için kümedeki yerleri.

Azure Service Fabric kullanıyorsanız, bunu kendi sağladığını unutmayın [sistem durumu izleme modeli](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), basit bir sistem durumu denetimleri daha gelişmiş olduğu.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Gelişmiş izleme: Görselleştirme ve çözümleme uyarıları

İzleme son bölümü göre servis performansını raporlama ve bir sorun algılandığında uyarı olay akışını görselleştirme olduğu. Bu izleme açısını için farklı çözümler kullanabilirsiniz.

Hizmetlerinizin durumunu gösteren basit bir özel uygulamalar kullanabilir, özel sayfa gibi biz size zaman açıklandığı gösterdi. [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks). Veya Azure Application Insights ve Operations Management Suite gibi daha gelişmiş araçlar, olayların akışa göre uyarıları yükseltmek için kullanabilir.

Depoladığınız tüm olay akışları, son olarak, Microsoft Power BI veya Kibana veya Splunk gibi bir üçüncü taraf çözümünü verileri görselleştirmek için kullanabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

-   **ASP.NET Core HealthChecks** (önceki sürüm) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Service Fabric sistem durumu izlemeye giriş**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite'e**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
>[Önceki](implement-circuit-breaker-pattern.md)
>[İleri](../secure-net-microservices-web-applications/index.md)