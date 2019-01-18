---
title: Sistem durumu izleme
description: Sistem durumu izleme uygulama yollarından keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 666b55608ca4e5d18448e1a0b4a1735f3e856474
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362489"
---
# <a name="health-monitoring"></a>Sistem durumu izleme

Sistem durumu izleme, kapsayıcılar ve mikro hizmet durumu hakkında neredeyse gerçek zamanlı bilgi izin verebilirsiniz. Sistem durumu izleme, kritik işletme mikro hizmetler birçok yönünü ve düzenleyicileri kısmi uygulama yükseltmeleri aşamalarında, daha sonra açıklandığı gibi gerçekleştirin, özellikle önemlidir.

Mikro hizmet tabanlı uygulamalar genellikle sinyal kullanabilir veya kendi performans izleyicileri, zamanlayıcılar ve düzenleyicileri birçok izlemenize olanak sağlamak için sistem durumu denetimleri. Hizmetleri "I canlı" bir sinyal çeşit isteğe bağlı veya bir zamanlamaya göre gönderemiyorsanız riskleri uygulamanızı yüz güncelleştirmelerini dağıtma veya yalnızca çok geç hatalarını algılamak ve ana kesintilerine sona erdirebilirsiniz zincirleme hatalara durdurmak mümkün olmaması.

Tipik modelinde Hizmetleri durumlarını hakkında raporlar gönderin ve uygulama durumunu durumunun genel bir görünümünü sağlamak için bu bilgileri toplanır. Bir orchestrator kullanıyorsanız, küme uygun şekilde işlem yapabilmesi, düzenleyicinin küme sistem durumu bilgilerini sağlayabilir. Uygulamanız için özelleştirilmiş, yüksek kaliteli sistem durumu raporlama yatırım yaparsanız, algılayın ve çalışan uygulamanız için çok daha kolay sorunları giderin.

## <a name="implement-health-checks-in-aspnet-core-services"></a>ASP.NET Core Hizmetleri uygulama durum denetimleri

Bir ASP.NET Core mikro hizmet veya web uygulama geliştirirken, Deneysel bir bant dışı kitaplığı kullanabilirsiniz (resmi olarak ASP.NETCore parçası olduğunu ve artık kullanım dışı) adlı *durum denetimleri* ASP.NET ekibinden. Şu anda kullanılabilir [dotnet-mimari GitHub deposu](https://github.com/dotnet-architecture/HealthChecks). Ancak, resmi sürümü *durum denetimleri* [içinde ASP.NET Core 2.2 yayımlanacak](https://github.com/aspnet/Announcements/issues/307) (resmi olarak 2018 sonuna kadar serbest bırakılması).

Bu kitaplık kullanımı kolaydır ve uygulamanız (örneğin, bir SQL Server veritabanı veya Uzak API) için gereken tüm belirli dış kaynak düzgün şekilde çalıştığını doğrulama olanak sağlayan özellikler sunar. Bu kitaplığı kullandığınızda, daha sonra anlatıldığı şekilde resource sağlam, anlamı da karar verebilirsiniz.

Bu kitaplığı kullanmak için öncelikle mikro hizmetlerin kitaplıkta kullanmanız gerekir. İkinci olarak, sorgular bir ön uç uygulaması için sistem durumu raporlarının gerekir. Ön uç uygulaması, bir özel raporlama uygulaması olabilir ya da uygun şekilde tepki verebilir bir orchestrator kendisini olabileceği için sağlık durumlarını.

### <a name="use-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Arka uç ASP.NET mikro hizmetlerin HealthChecks kitaplıkta kullan

HealthChecks kitaplığı hizmetine örnek uygulamada nasıl kullanıldığını görebilirsiniz. Başlamak için her bir mikro hizmet durumu sağlıklı nelerden tanımlamanız gerekir. Örnek uygulamada, mikro hizmetler, HTTP ve ilgili SQL Server veritabanını da kullanılabilir olup olmadığını API mikro hizmet erişilemez iyi durumda.

Gelecekte bir NuGet paketi olarak HealthChecks kitaplığını yüklemek mümkün olacaktır. Ancak bu makalenin yazıldığı tarih itibarıyla, indirmek ve çözümünüzün bir parçası olarak Kodu derlemek gerekir. Kullanılabilir kod klonlama <https://github.com/dotnet-architecture/HealthChecks> ve çözümünüze aşağıdaki klasörleri kopyalayın:

- src/ortak
- src/Microsoft.AspNetCore.HealthChecks
- src/Microsoft.Extensions.HealthChecks
- src/Microsoft.Extensions.HealthChecks.SqlServer

Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ancak bu sürümü hizmetine Azure'da herhangi bir bağımlılığı olmadığından olanlar gibi ek denetimler de kullanabilirsiniz, bunun gerekmez. ASP.NET Core, hizmetine dayandığından, ASP.NET sistem durumu denetimleri ihtiyacınız yoktur.

Şekil 8-7, Visual Studio, bir yapı taşı olarak herhangi bir mikro hizmetler tarafından kullanılmaya hazır HealthChecks kitaplığı gösterir.

![Çözüm Gezgini görünümü HealthChecks klasörünün üç proje gösteriliyor.](./media/image6.png)

**Şekil 8-7**. ASP.NET Core HealthChecks kitaplığı kaynak kodunu bir Visual Studio çözümü içinde

Daha önce sunulan gibi her bir mikro hizmet projesine yapılacak ilk şey bir başvuru üç HealthChecks kitaplıkları eklemektir. Bundan sonra bu mikro hizmet içinde gerçekleştirmek istediğiniz sistem durumu denetimi eylemlerini ekleyin. Bu eylemler temel olarak diğer mikro hizmetler (HttpUrlCheck) veya veritabanlarını bağımlılıkları olan (şu anda SqlCheck\* SQL Server veritabanları için). Eylem içinde her ASP.NET mikro hizmet veya ASP.NET web uygulaması başlangıç sınıfı ekleyin.

Her hizmeti veya web uygulamasına bir AddHealthCheck yöntemi olarak HTTP ya da veritabanı tüm bağımlılıkları ekleyerek yapılandırılması gerekir. Örneğin, MVC web hizmetine uygulamadan birden çok hizmete bağlıdır, bu nedenle, sistem durumu denetimleri için eklenen çeşitli AddCheck yöntemler vardır.

Örneğin, (Basitleştirilmiş) aşağıdaki kodda nasıl Kataloğu mikro hizmet kendi SQL Server veritabanı üzerinde bir bağımlılık ekler görebilirsiniz.

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

Ancak, hizmetine MVC web uygulaması, mikro hizmetler geri kalanı üzerinde birden çok bağımlılıkları vardır. Bu nedenle, bir AddUrlCheck yöntemini her mikro hizmet için (Basitleştirilmiş) aşağıdaki örnekte gösterildiği gibi çağırır:

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

Mikro hizmet veya SQL Server bir bağımlılık yoksa, yalnızca bir Healthy("Ok") onay eklemeniz gerekir. Aşağıdaki kodu hizmetine olan `basket.api` mikro hizmet. (Redis cache sepet mikro hizmet kullanır, ancak kitaplık bir Redis sistem durumu denetimi sağlayıcısı henüz içermez.)

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

Etkinleştirmek olan sistem durumu onay uç noktası kullanıma sunmak bir hizmeti veya web uygulaması için `UseHealthChecks([*url_for_health_checks*])` genişletme yöntemi. Bu yöntem, gider `WebHostBuilder` ana yöntemi düzeyde `Program` ASP.NET Core hizmeti veya web uygulamanız, sonra sağ sınıfının <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> Basitleştirilmiş aşağıdaki kodda gösterildiği gibi:

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = WebHost.CreateDefaultBuilder(args)
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseStartup<Startup>()
                .Build();

            host.Run();
        }
    }
}
```

İşlem bu şekilde çalışır: her mikro hizmet uç noktası HC kullanıma sunar. Uç noktanın HealthChecks kitaplığı ASP.NET Core ara yazılımı tarafından oluşturulur. Uç noktanın çağrıldığında başlangıç sınıfındaki AddHealthChecks yöntemi yapılandırılan tüm sistem durumu denetimleri çalıştırır.

Bir bağlantı noktası veya yol UseHealthChecks yöntemi bekliyor. Bu bağlantı noktası veya yol, hizmetin sistem durumunu denetlemek için uç noktadır. Örneğin, katalog mikro hizmet yolu HC kullanır.

### <a name="cache-health-check-responses"></a>Önbellek sistem durumu onay yanıtları

Çok sık hizmetlerinizde bir hizmet reddi (DoS) neden istemediğiniz veya yalnızca kaynak kontrol ederek hizmet performansı etkileyecek şekilde istemiyorsanız bu yana önbelleğe döndürür ve önbelleğe alma süresi her sistem durumu denetimi için yapılandırma kullanabilirsiniz.

Varsayılan olarak, önbelleğe alma süresi 5 dakika ile dahili olarak ayarlanır, ancak bu önbelleğe alma süresi şu kod gibi her sistem durumu denetimi üzerinde değiştirebilirsiniz:

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Mikro hizmetlerin sistem durumlarına raporlamak sorgulama

Sağlıksız olması durumunda bu makalede anlatıldığı gibi sistem durumu denetimleri yapılandırdıysanız ve Docker'da çalışan mikro hizmet sahip olduğunda, doğrudan bir tarayıcıdan denetleyebilirsiniz.

Kapsayıcı dış Docker ana bilgisayar IP üzerinden veya aracılığıyla erişebilmesi için kapsayıcı bağlantı noktasından Docker konağı yayımlamak sahip olduğunuz `localhost`Şekil 8-8 ' gösterildiği gibi.

![Sistem durumu denetimi tarafından döndürülen JSON yanıtı tarayıcı görünümü](./media/image7.png)

**Şekil 8-8**. Tek bir hizmet tarayıcısından sistem durumunu denetleme

Bu test, (5101 bağlantı noktasında çalışan) catalog.api mikro hizmet sağlıklı, 200 HTTP durum ve durum bilgileri JSON biçiminde döndüren görebilirsiniz. Ayrıca dahili olarak hizmet aynı zamanda SQL Server veritabanı bağımlılık durumunu iade etmeniz ve sistem durumu denetimi kendisini sağlıklı olarak rapor edilmiştir, anlamına gelir.

## <a name="use-watchdogs"></a>Watchdogs kullanın

Bir izleme sistem durumu izleme ve yük Hizmetleri ve mikro hizmetler hakkında rapor sistem durumu ile sorgulayarak ayrı bir hizmet olan `HealthChecks` kitaplığı sunulan daha önce. Bu işlem, tek bir hizmette bir görünümü temel alarak değil algılanır hataları önlemeye yardımcı olabilir. Watchdogs de iyi bir kullanıcı etkileşimi olmadan bilinen koşulları için düzeltme eylemleri gerçekleştirebilen konak koda yerdir.

Şekil 8-9'da gösterildiği örnek sistem durumu denetimi raporları görüntüleyen bir web sayfası hizmetine örnek içerir. Mikro hizmetler ve web uygulamalarının durumu hizmetine yalnızca gösterdiğinden, olabilir basit izleme budur. Genellikle, iyi durumda olmayan durumlar algıladığında bir bekçi ayrıca eylemleri gerçekleştirir.

![Sistem durumu hizmetine gelen beş mikro hizmetler, gösteren WebStatus uygulamasının tarayıcı görünümü](./media/image8.png)

**Şekil 8-9**. Hizmetine örnek sistem durumu denetimi raporu

Özet olarak, ASP.NET, ASP.NET Core HealthChecks kitaplığının tek sistem durumu onay uç noktası için her bir mikro hizmetin ihtiyacımızı karşılıyor. İçinde tanımlanan tüm sistem durumu denetimleri yürütmek ve genel sistem durumuna bağlı tüm denetimleri olarak döndürür.

Gelecekteki dış kaynaklara yeni sistem durumu denetimleri Genişletilebilir HealthChecks kitaplığıdır. Örneğin, gelecekte kitaplığı diğer veritabanları ve Redis önbelleği için sistem durumu denetimleri olacağını umuyoruz. Birden çok hizmet veya uygulama bağımlılıkları raporlama sistem durumu kitaplığı sağlar ve sonra bu sistem durumu denetimleri üzerinde temel eylemleri gerçekleştirebilir.

## <a name="health-checks-when-using-orchestrators"></a>Düzenleyiciler kullanırken sistem durumu denetimleri

Mikro hizmetlerin kullanılabilirliğini izlemek için Kubernetes ve Service Fabric gibi düzenleyicileri düzenli aralıklarla sistem durumu denetimleri mikro Hizmetleri test etmek için istekleri göndererek gerçekleştirir. Ne zaman bir orchestrator hizmet/kapsayıcı yönlendirme istekleri bu örneği durdurur, sağlıksız olduğunu belirler. Ayrıca genellikle, bu kapsayıcı yeni bir örneğini oluşturur.

Örneğin, çoğu düzenleyicileri, sistem durumu denetimleri kesintisiz dağıtımlarını yönetmek için kullanabilirsiniz. Yalnızca sağlıklı bir hizmeti/kapsayıcı değişiklikleri durumunu olacak orchestrator başlattığınızda hizmet/kapsayıcı örneklerine trafiği yönlendirme.

Bir orchestrator uygulama yükseltme yaparken, sistem durumu izleme özellikle önemlidir. Bazı düzenleyiciler (örneğin, Azure Service Fabric) Hizmetleri'nde aşamaları güncelleştirme — Örneğin, her uygulama yükseltmesi için küme yüzeyinde bir beşinci güncelleştirebilir. Aynı anda yükseltilir düğümleri kümesini şeklinde adlandırılan bir *yükseltme etki alanı*. Her bir yükseltme etki alanı yükseltildi ve kullanıcılar tarafından kullanılabilir sonra dağıtım için bir sonraki yükseltme etki alanına taşınmadan önce yükseltme etki alanı sistem durumu denetimleri geçmesi gerekir.

Bir diğer unsuru hizmet sistem durumu hizmetinden alınan ölçümleri bildiriyor. Bu, Service Fabric gibi bazı düzenleyiciler sistem durumu modeli, Gelişmiş bir özelliktir. Ölçümler, kaynak kullanımı dengelemek için kullanıldığından bir orchestrator kullanırken önemlidir. Ölçümleri de sistem durumu göstergesi olabilir. Örneğin, birçok mikro olan bir uygulama olabilir ve her örneği bir saniyede istekleri (RP'ler) ölçüm bildirir. Bir hizmetin başka bir hizmete daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsanız, orchestrator hizmet örnekleri bile kaynak kullanımını korumak için kümedeki yerleri.

Azure Service Fabric kendi sağladığını unutmayın [sistem durumu izleme modeli](/azure/service-fabric/service-fabric-health-introduction), basit bir sistem durumu denetimleri daha gelişmiş olduğu.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Gelişmiş izleme: Görselleştirme ve çözümleme uyarıları

İzleme son bölümü göre servis performansını raporlama ve bir sorun algılandığında uyarı olay akışını görselleştirme olduğu. Bu izleme açısını için farklı çözümler kullanabilirsiniz.

Açıklayan gösterilen özel sayfa gibi hizmetlerinizin durumunu gösteren basit bir özel uygulamalar kullanabilir [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks). Ya da olayların akışa göre uyarıları artırmak için Azure Application Insights gibi daha gelişmiş araçları kullanabilirsiniz.

Tüm olay akışlarını depoladığınız, son olarak, Microsoft Power BI veya Kibana veya Splunk gibi diğer çözümlerle verileri görselleştirmek için kullanabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core HealthChecks** (Deneysel sürüm) \
  [*https://github.com/dotnet-architecture/HealthChecks/*](https://github.com/dotnet-architecture/HealthChecks/)

- **Service Fabric sistem durumu izlemeye giriş**\
  [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Application Insights**\
  [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

- **Microsoft Operations Management Suite'e**\
  [*https://www.microsoft.com/cloud-platform/operations-management-suite*](https://www.microsoft.com/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
>[Önceki](implement-circuit-breaker-pattern.md)
>[İleri](../secure-net-microservices-web-applications/index.md)