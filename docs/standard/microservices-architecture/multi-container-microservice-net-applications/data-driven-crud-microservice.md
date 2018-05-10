---
title: Bir basit veri güdümlü CRUD mikro hizmet oluşturma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Bir basit veri güdümlü CRUD mikro hizmet oluşturma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 1186ad41fa1a6befcfcc4fa1f547605bb69e68bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Bir basit veri güdümlü CRUD mikro hizmet oluşturma

Bu bölüm anahatları basit bir oluşturmak için gerçekleştirdiği mikro hizmet oluşturun nasıl okuma, güncelleştirme ve bir veri kaynağında Sil (CRUD) işlemleri.

## <a name="designing-a-simple-crud-microservice"></a>Basit bir CRUD mikro hizmet tasarlama

Bir tasarım açısından bakıldığında, bu tür kapsayıcılı mikro çok kolaydır. Belki de sorunu çözmek için basit bir işlemdir veya yalnızca bir kavram kanıtı belki de uygulamasıdır.

![](./media/image4.png)

**Şekil 8-4**. Basit CRUD mikro için iç tasarımı

Bu tür bir basit veri sürücüsü hizmet Kataloğu mikro hizmet eShopOnContainers örnek uygulamadan örnektir. Bu tür bir hizmet kendi veri modeli, iş mantığı ve kendi veri erişim kodu için sınıflar içerir tek bir ASP.NET çekirdek Web API projesinde tüm işlevlerini uygular. Ayrıca, ilgili verilerini (olarak geliştirme ve test amaçları için başka bir kapsayıcı) SQL Server çalıştıran bir veritabanında depolar ancak normal herhangi bir SQL Server ana Şekil 8-5'te gösterildiği gibi de olabilir.

![](./media/image5.png)

**Şekil 8-5**. Basit veri-güdümlü/CRUD mikro hizmet tasarım

Bu tür bir hizmet geliştirirken, yalnızca ihtiyacınız [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) ve veri erişimi API veya ORM gibi [Entity Framework Çekirdek](https://docs.microsoft.com/ef/core/index). Ayrıca üretebilir [Swagger](https://swagger.io/) meta verileri otomatik olarak ile [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) ne hizmetiniz sunar, açıklaması bir sonraki bölümde açıklandığı gibi sağlamak için.

Tüm bağımlılıklarınızı sahip için SQL Server'ın bir Docker kapsayıcısı içinde geliştirme ortamları için harikadır gibi bir veritabanı sunucusunu çalıştıran ve bir veritabanı bulutta veya şirket içi sağlamak zorunda kalmadan çalışan unutmayın. Tümleştirme testleri, bu çok kullanışlı olur. Bu yaklaşım ile yüksek kullanılabilirlik genellikle almazsanız olduğundan ancak üretim ortamları için bir veritabanı sunucusu bir kapsayıcıda çalışan, önerilmez. Azure'da bir üretim ortamı için Azure SQL DB veya yüksek kullanılabilirlik ve yüksek ölçeklenebilirlik sağlayabilir herhangi bir veritabanı teknolojisini kullanmanız önerilir. Örneğin, bir NoSQL yaklaşım için DocumentDB seçebilirsiniz.

Son olarak, Dockerfile ve docker-compose.yml meta veri dosyaları düzenleyerek, bu kapsayıcı görüntüsünü nasıl oluşturulacak yapılandırabileceğiniz — hangi temel görüntü, kullanın, artı tasarım iç ve dış adlar ve TCP bağlantı noktaları gibi ayarlar. 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>ASP.NET Core ile basit bir CRUD mikro hizmet uygulama

.NET Core ve Visual Studio kullanarak basit bir CRUD mikro hizmet uygulamak için (Linux Docker ana bilgisayarda çalıştırabilmeniz için .NET Core üzerinde çalışan), basit bir ASP.NET çekirdek Web API projesi oluşturarak gösterildiği Şekil 8-6 olarak başlatın.

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**Şekil 8-6**. Visual Studio'da ASP.NET çekirdek Web API projesi oluşturma

Projesi oluşturduktan sonra Entity Framework API veya diğer API kullanarak tüm diğer Web API projesinde, olduğu gibi MVC denetleyicileri uygulayabilirsiniz. Yeni bir Web API projesinde, mikro hizmet ASP.NET Core üzerinde kendisini bakımından, yalnızca bağımlılık, olduğunu görebilirsiniz. Dahili olarak, içinde `Microsoft.AspNetCore.All` bağımlılık, onu başvurduğu Entity Framework ve diğer birçok .NET Core Nuget paketleri, Şekil 8-7'de gösterildiği gibi.

![](./media/image8.PNG)

**Şekil 8-7**. Basit bir CRUD Web API mikro Hizmet bağımlılıkları

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Entity Framework Çekirdek ile uygulama CRUD Web API Hizmetleri

Hafif, Genişletilebilir, Entity Framework (EF) çekirdeği olur ve platformlar arası sürümü popüler Entity Framework verilerine erişim teknolojisini. EF çekirdeği .NET geliştiricilerinin .NET nesneleri kullanarak bir veritabanı ile çalışmak bir nesne ilişkisel Eşleyici (ORM) olur.

Veritabanını bir kapsayıcıda Linux Docker görüntüsü için SQL Server ile çalıştığı için katalog mikro hizmet EF ve SQL Server sağlayıcısı kullanır. Ancak, veritabanı içine Windows Şirket içi veya Azure SQL DB gibi herhangi bir SQL sunucusuna dağıtılabilir. Değiştirmek için gereken tek şey, ASP.NET Web API mikro hizmet bağlantı dizesinde.


#### <a name="the-data-model"></a>Veri modeli

EF çekirdek ile veri erişim modeli kullanarak gerçekleştirilir. Bir model sınıflar ve sorgu ve veri kaydetmenize olanak veren veritabanı, oturumla temsil eden bir türetilmiş bağlamı oluşur. Varolan bir veritabanından bir model oluşturmak, el ile veritabanınızı eşleştirmek için bir model kod veya EF geçişler modelinizin dışında bir veritabanı oluşturmak için (ve modelinizi zaman içinde değiştikçe gelişmesi için) kullanın. Katalog mikro hizmet için son yaklaşım kullanıyoruz. Basit bir düz eski CLR nesnesi aşağıdaki kod örneğinde, CatalogItem varlık sınıfı örneği görebilirsiniz ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) varlık sınıfı.

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

Ayrıca veritabanı oturumla temsil eden bir DbContext gerekir. Katalog mikro hizmet için CatalogContext sınıfı aşağıdaki örnekte gösterildiği gibi DbContext temel sınıfından türetilen:

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...

}
```

Ek olabilir `DbContext` uygulamaları. Örneğin, örnek Catalog.API mikro yoktur saniyenin `DbContext` adlı `CatalogContextSeed` burada bunu otomatik olarak doldurur örnek verileri çalışır veritabanına erişmek için ilk kez. Bu yöntem, demo verileri ve otomatikleştirilmiş test senaryoları için de kullanışlıdır. İçinde `DbContext`, kullandığınız `OnModelCreating` nesne/veritabanı varlık eşlemeleri ile ve diğer özelleştirmek için yöntemi [EF genişletilebilirlik noktaları](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

##### <a name="querying-data-from-web-api-controllers"></a>Web API denetleyicilerinin verileri Sorgulama

Varlık sınıfları, genellikle aşağıdaki örnekte gösterildiği gibi dil tümleşik sorgu (LINQ), kullanarak veritabanından alınır:

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(CatalogContext context, 
                             IOptionsSnapshot<CatalogSettings> settings,
                             ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    public async Task<IActionResult> Items([FromQuery]int pageSize = 10, 
                                           [FromQuery]int pageIndex = 0)

    {
        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();

        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();

        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);

        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);

        return Ok(model);
    } 
    //...
}
```

##### <a name="saving-data"></a>Verileri kaydetme

Veri oluşturulur, silinmiş ve varlık sınıfların örneklerini kullanarak veritabanında değiştirildi. Kod aşağıdaki sabit kodlanmış örneği (Bu durumda sahte veriler), Web API denetleyicilerinin gibi ekleyebilirsiniz.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>ASP.NET Core ve Web API denetleyicilerinin bağımlılık ekleme

ASP.NET Core kutu dışı bağımlılık ekleme (dı) kullanabilirsiniz. İsterseniz, tercih edilen IOC kapsayıcı ASP.NET Core altyapısını ekleyebilirsiniz ancak bir üçüncü taraf denetimi tersine çevirme (IOC) kapsayıcı ayarlamak gerekmez. Bu durumda, doğrudan gerekli EF DBContext veya denetleyicisi Oluşturucusu aracılığıyla ek depoları ekleyemezsiniz, anlamına gelir. Örnekte `CatalogController` sınıfı, biz injecting bir nesnenin `CatalogContext` yazın diğer nesneler arasında artı `CatalogController()` Oluşturucusu.

DbContext sınıf kaydı hizmetin IOC kapsayıcı içine Web API projesinde ayarlamak için önemli bir yapılandırmadır. Bu nedenle, genellikle yaptığınız `Startup` çağırarak sınıfı `services.AddDbContext<DbContext>()` yönteminin içinde `ConfigureServices()` yöntemi, aşağıdaki örnekte gösterildiği gibi:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
           sqlOptions.
               MigrationsAssembly(
                   typeof(Startup).
                    GetTypeInfo().
                     Assembly.
                      GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...

}
```

### <a name="additional-resources"></a>Ek kaynaklar

-   **Veri sorgulama**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **Verileri kaydetme**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Docker kapsayıcıları tarafından kullanılan DB bağlantı dizesi ve ortam değişkenleri

ASP.NET Core ayarları kullanmak ve ConnectionString özelliğini settings.json dosyanıza aşağıdaki örnekte gösterildiği gibi ekleyin:

```csharp
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

Settings.json dosyası ConnectionString özelliği için veya başka bir özellik için varsayılan değerleri olabilir. Ancak, bu özellikleri Docker kullanırken, docker compose.override.yml dosyasında belirlediğiniz ortam değişkenleri değerlerle geçersiz kılınır.

Bu Docker bunları işletim sistemi ortam değişkenleri olarak sizin için ayarlamanız şekilde, docker-compose.yml veya docker compose.override.yml dosyalarından, bu ortam değişkenleri aşağıdaki docker compose.override.yml dosyasında (bağlantı gösterildiği gibi başlatabilir Bu örnekte, dize ve diğer satırlar sarmalama, ancak bunu kendi kod dosyasında kaydırılacak).

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

Çözüm düzeyinde docker-compose.yml dosyaları yalnızca proje veya mikro hizmet düzeyi, ancak daha da yapılandırma dosyaları ancak docker-compose dosyalarıyla adresindeki bildirilen ortam değişkenleri geçersiz kılarsanız daha da güvenli çok daha esnektir değil değerleri, dağıtım araçlarından VSTS Docker dağıtım görevleri gibi ayarlayın. 

Son olarak, bu değeri kodunuzdan yapılandırmayı kullanarak alabileceğiniz\["ConnectionString"\]ConfigureServices yöntemi bir önceki kod örneğinde gösterildiği gibi.

Ancak, üretim ortamları için başka bir yolu Gezgini bağlantı dizeleri gibi parolaları depolamak nasıl isteyebilirsiniz. Genellikle, yönetilecek, seçilen orchestrator tarafından ile yapabileceğiniz gibi [Docker Swarm gizli Yönetim](https://docs.docker.com/engine/swarm/secrets/).

### <a name="implementing-versioning-in-aspnet-web-apis"></a>ASP.NET Web API uygulama sürüm oluşturma

İş gereksinimleri değişirken kaynakların yeni koleksiyonları eklenebilir, kaynakları arasındaki ilişkileri değişebilir ve veri kaynaklarında yapısını dayanıklıdır. Yeni gereksinimleri işlemek için bir Web API güncelleştirme görece basit bir işlemdir, ancak bu değişiklikleri Web API'sini kullanan istemci uygulamaları üzerinde sahip olacağı etkilerini dikkate almanız gerekir. Tasarlama ve bir Web API Uygulama geliştirici bu API üzerinde tam denetime sahip olsa da, geliştirici aynı derecede uzaktan işletim üçüncü taraf kuruluşlar tarafından oluşturulan istemci uygulamaları denetime sahip değil.

Sürüm oluşturma, sunar kaynaklarını ve Özellikler belirtmek bir Web API sağlar. Bir istemci uygulaması sonra bir özellik veya kaynak belirli bir sürümünü istekleri gönderebilirsiniz. Sürüm oluşturma uygulamak için birçok yaklaşım vardır:

-   URI sürüm oluşturma

-   Sorgu dizesi sürüm oluşturma

-   Üstbilgi sürüm oluşturma

Sorgu dizesi ve URI sürüm basit uygulamak markalarıdır. Üstbilgi sürüm iyi bir yaklaşımdır. Ancak, üstbilgi sürüm olarak açık ve URI sürüm olarak kolay. URL sürüm en basit ve en açık olduğundan, eShopOnContainers örnek uygulama URI sürüm kullanır.

EShopOnContainers örnek uygulama olduğu gibi URI sürüm ile Web API değiştirmek veya kaynakları, şema değiştirme her zaman, bir sürüm numarası için her kaynak için URI ekleyin. Varolan URI, uygun kaynaklar istenen sürümüyle eşleşen şemanın dönmeden önce gibi çalışmaya devam etmelidir.

Aşağıdaki kod örneğinde gösterildiği gibi sürüm rota özniteliğinin sürüm URI açık hale getirir Web API kullanılarak ayarlanabilir (Bu durumda v1).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Bu sürüm oluşturma mekanizması basittir ve uygun uç noktasına istek yönlendirme sunucusu bağlıdır. Ancak, daha karmaşık bir sürüm oluşturma ve REST kullanırken en iyi yöntemi için iletilir kullanın ve uygulamak [HATEOAS (köprü metni olarak uygulama altyapısı durumu)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Ek kaynaklar

-   **Scott Hanselman. Kolay ASP.NET Core RESTful Web API'si sürüm oluşturma**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Sürüm oluşturma bir RESTful web API'si**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding. Sürüm oluşturma, iletilir ve REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Oluşturma Swagger açıklama meta verilerini, ASP.NET çekirdek Web API 

[Swagger](https://swagger.io/) olan yaygın olarak kullanılan açık kaynak framework tasarımı, yapı, belge yardımcı olan bir büyük ekosistemi araçları tarafından desteklenen ve RESTful API'lerini kullanma. API tanımı meta verileri etki alanı için standart durumundadır. Mikro hizmet, veri tabanlı mikro veya daha fazla etki alanı tabanlı mikro (aşağıdaki bölümde açıklandığı gibi) Gelişmiş herhangi bir tür ile Swagger açıklama meta verileri içermelidir.

Swagger Kalp API açıklama meta veriler JSON veya YAML dosyasında Swagger belirtimidir. Belirtimi tüm kaynakları ve işlemleri hem bir biçimde İnsan ve machine readable kolay geliştirme, bulma ve tümleştirme için ayrıntılı API'nizi RESTful sözleşmesi oluşturur.

Belirtimi OpenAPI belirtimi'nın (OAS) temelini ve RESTful arabirimlerinden tanımlanan şekilde standart hale getirmek için bir açık, saydam ve işbirliği topluluğuna geliştirilmiştir.

Belirtimi nasıl bir hizmeti bulunan ve nasıl yeteneklerini anladım yapısını tanımlar. Daha fazla bilgi için bir web Düzenleyicisi'ni ve Swagger belirtimleri Spotify, Uber, boşluk ve Microsoft, gibi şirketlerden örnekleri dahil olmak üzere Swagger sitesine bakın (<https://swagger.io/>).

### <a name="why-use-swagger"></a>Swagger neden kullanılır?

API için Swagger meta verileri oluşturmak için nedenler şunlardır:

**Otomatik olarak kullanabilir ve Apı'lerinizi tümleştirmek diğer ürünleri yeteneği**. Ürünler onlarca ve [ticari Araçları](https://swagger.io/commercial-tools/) ve birçok [kitaplıklarını ve çerçevelerini](https://swagger.io/open-source-integrations/) Swagger destekler. Microsoft, üst düzey ürünleri ve otomatik olarak aşağıdaki gibi Swagger tabanlı API'ler tüketebileceği araçlara sahiptir:

-   [AutoRest](https://github.com/Azure/AutoRest). .NET istemci sınıfları Swagger çağırmak için otomatik olarak oluşturabilir. CLI üzerinden bu aracı kullanılabilir ve GUI aracılığıyla kolay kullanım için de Visual Studio ile tümleştirir.

-   [Microsoft Akış](https://flow.microsoft.com/en-us/). Otomatik olarak [kullanın ve API'nizi tümleştirme](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) üst düzey bir Microsoft Flow akışına olmadan programlama gerekli niteliklere.

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/). Otomatik olarak API öğesinden tüketebileceği [PowerApps mobil uygulamaları](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) ile oluşturulan [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), gerekli hiçbir programlama becerilerine sahip.

-   [Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Otomatik olarak [kullanın ve Azure App Service Logic uygulamaya API'nizi tümleştirme](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), gerekli herhangi bir programlama becerilerine sahip.

**API belgelerine otomatik olarak oluşturma yeteneği**. Mikro hizmet tabanlı karmaşık uygulamalar gibi büyük ölçekli RESTful API'lerini oluşturduğunuzda, istek ve yanıt yükleri kullanılır farklı veri modelleri ile çok sayıda uç noktaları ele almanız gerekir. API ve benimseme geliştiriciler tarafından başarısı için uygun belgeleri olması ve Swagger ile aldıkça düz bir API Gezgini sahip anahtardır.

Swagger ait meta verileri ne Microsoft Flow, PowerApps ve Azure mantıksal uygulamaları API'leri kullanan ve kendilerine bağlanması nasıl anlamak için kullandığınız yöntemdir.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>API Swagger meta verileri oluşturma Swashbuckle NuGet paketi ile otomatikleştirme

Swagger meta verilerde el ile (JSON veya YAML dosyası) oluşturma can sıkıcı iş olabilir. Ancak, ASP.NET Web API hizmetlerinin API bulma kullanarak otomatik hale getirebilir [Swashbuckle NuGet paketi](http://aka.ms/swashbuckledotnetcore) dinamik olarak Swagger API'si meta verileri oluşturmak için.

Swashbuckle, ASP.NET Web API projeleri için Swagger meta verileri otomatik olarak oluşturur. ASP.NET Core Web API projeleri ve geleneksel ASP.NET Web API ve Azure API uygulaması, Azure mobil uygulaması, ASP Azure Service Fabric mikro gibi diğer tüm özellik destekler. Ayrıca, kapsayıcılarında olarak başvuru uygulaması için Dağıtılmış düz Web API destekler.

Swashbuckle birleştirir API'si Gezgini ve Swagger veya [swagger kullanıcı arabirimi](https://github.com/swagger-api/swagger-ui) zengin bulma ve belgeleri API tüketicileriniz için deneyimi sağlamak için. Kendi Swagger meta verileri Oluşturucu Altyapısı'na ek olarak, Swashbuckle swagger Swashbuckle yüklendikten sonra onu otomatik olarak hizmet verecektir yukarı kullanıcı arabirimi, katıştırılmış bir sürümünü de içerir.

Başka bir deyişle, API'nizi iyi bulma API'nizi kullanmak için geliştiricilere yardımcı olmak için kullanıcı Arabirimi ile tamamlayabilir. Bu otomatik olarak, API'nizi oluşturmaya odaklanmanıza olanak tanıyan üretildiği için çok küçük miktarda kod ve bakım gerektirir. Sonucun API'si Gezgini için Şekil 8-8 gibi görünüyor.

![](./media/image9.png)

**Şekil 8-8**. Swashbuckle API'si Gezgini Swagger meta verilerini temel — eShopOnContainers mikro hizmet Kataloğu

API explorer en önemli şey burada değil. Kendisini Swagger meta verilerde açıklayan bir Web API oluşturduktan sonra API birçok platformda hedefleyebilirsiniz istemci proxy sınıfı kod oluşturucuları dahil olmak üzere Swagger tabanlı Araçları'ndan, sorunsuz bir şekilde kullanılabilir. Örneğin, söz edildiği gibi [AutoRest](https://github.com/Azure/AutoRest) otomatik olarak .NET istemci sınıfları oluşturur. Ancak ek araçlar [swagger codegen](https://github.com/swagger-api/swagger-codegen) kod oluşturma API İstemci kitaplıkları, sunucu saplamalar ve belgeleri otomatik olarak izin veren öğeler de kullanılabilir.

Şu anda Swashbuckle iki üst düzey meta paket altındaki çeşitli iç NuGet paketlerini oluşur [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) sürümü 1.0.0 veya ASP.NET Core uygulamaları daha yeni.

Web API projesinde bu NuGet paketleri yükledikten sonra aşağıdaki kodu olduğu gibi başlangıç sınıftaki Swagger yapılandırmanız gerekir:

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new Swashbuckle.AspNetCore.Swagger.Info
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample",
                TermsOfService = "Terms Of Service"
            });
        });

        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

Bunu yaptıktan sonra uygulamanızı başlatın ve bu benzer URL'ler kullanarak aşağıdaki Swagger JSON ve kullanıcı Arabirimi uç noktaları göz atın:

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

Daha önce oluşturulan kullanıcı arabirimini http:// URL için Swashbuckle tarafından oluşturulan gördüğünüz&lt;kök URL'si bilgisayarınızı &gt; /swagger/kullanıcı arabirimi. Şekil 8-9'da herhangi bir API yöntemi test nasıl de görebilirsiniz.

![](./media/image10.png)

**Şekil 8-9**. Swashbuckle katalog/öğeleri API yöntemi sınama UI

Şekil 8-10 eShopOnContainers mikro oluşturulan Swagger JSON meta verileri gösterir (olduğu Araçları altında kullanın) olduğunda, isteği &lt;kök URL'si bilgisayarınızı&gt;/swagger/v1/swagger.json kullanarak [Postman](https://www.getpostman.com/).

![](./media/image11.png)

**Şekil 8-10**. Swagger JSON meta verileri

Bu basit bir işlemdir. Ve otomatik olarak oluşturulduğundan, API için daha fazla işlevsellik eklediğinizde, Swagger meta verileri büyüyecektir.

### <a name="additional-resources"></a>Ek kaynaklar

-   **ASP.NET Web API Yardım Swagger kullanarak sayfaları**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[Önceki] (mikro hizmet-uygulama-design.md) [sonraki] (çok-container-uygulamalar-docker-compose.md)
