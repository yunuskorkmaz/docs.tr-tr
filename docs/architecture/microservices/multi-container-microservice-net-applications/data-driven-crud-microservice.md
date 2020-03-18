---
title: Basit bir veri temelli CRUD mikro hizmeti oluşturma
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Bir microservices uygulaması bağlamında basit bir CRUD (veri odaklı) microservice oluşturulmasını anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: b72d7defed81e57e2971c5e2b53df2d86b2dc947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502346"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Basit bir veri temelli CRUD mikro hizmeti oluşturma

Bu bölümde, bir veri kaynağında oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemlerini gerçekleştiren basit bir mikro hizmetin nasıl oluşturulacak olduğu açıklanmıştır.

## <a name="designing-a-simple-crud-microservice"></a>Basit bir CRUD microservice tasarımı

Bakış bir tasarım açısından, konteyner microservice bu tür çok basittir. Belki de çözmek için sorun basit, ya da belki de uygulama kavramının sadece bir kanıtıdır.

![Basit bir CRUD microservice iç tasarım deseni gösteren diyagram.](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

**Şekil 6-4**. Basit CRUD mikroservisleri için dahili tasarım

Basit veri sürücü hizmeti bu tür bir örnek eShopOnContainers örnek uygulamadan katalog microservice olduğunu. Bu hizmet türü, tüm işlevselliğini veri modeli, iş mantığı ve veri erişim kodu için sınıflar içeren tek bir ASP.NET Çekirdek Web API projesinde uygular. Ayrıca, ilgili verilerini SQL Server'da çalışan bir veritabanında (dev/test amacıyla başka bir kapsayıcı olarak) de polar, ancak Şekil 6-5'te gösterildiği gibi normal bir SQL Server ana bilgisayarı da olabilir.

![Veri odaklı/CRUD microservice konteynerini gösteren diyagram.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

**Şekil 6-5**. Basit veri odaklı/CRUD microservice tasarım

Önceki diyagram, aynı Docker ana bilgisayarda olabilir veya olmayabilir katalog veritabanını içeren mantıksal Katalog microservice gösterir. Veritabanının aynı Docker ana bilgisayarda olması geliştirme için iyi olabilir, ancak üretim için iyi olmayabilir. Bu tür bir hizmet geliştirirken, yalnızca [ASP.NET Core'a](https://docs.microsoft.com/aspnet/core/) ve [Entity Framework Core](https://docs.microsoft.com/ef/core/index)gibi veri erişim API veya ORM'ye ihtiyacınız vardır. Ayrıca, bir sonraki bölümde açıklandığı gibi, hizmetinizin neler sunduğunun açıklamasını sağlamak için [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) üzerinden otomatik olarak [Swagger](https://swagger.io/) meta verileri oluşturabilirsiniz.

Bir Docker kapsayıcısı içinde SQL Server gibi bir veritabanı sunucusu çalıştırmanın geliştirme ortamları için harika olduğunu unutmayın, çünkü bulutta veya şirket içinde bir veritabanı sağlamanıza gerek kalmadan tüm bağımlılıklarınızı çalışır duruma getirebilirsiniz. Bu, tümleştirme testlerini çalıştırırken çok kullanışlıdır. Ancak, üretim ortamları için, genellikle bu yaklaşımla yüksek kullanılabilirlik elde etmediğiniz için bir kapsayıcıda veritabanı sunucusu çalıştırmak önerilmez. Azure'daki bir üretim ortamı için, Yüksek kullanılabilirlik ve yüksek ölçeklenebilirlik sağlayabilen Azure SQL DB veya başka bir veritabanı teknolojisi kullanmanız önerilir. Örneğin, Bir NoSQL yaklaşımı için CosmosDB'yi seçebilirsiniz.

Son olarak, Dockerfile ve docker-compose.yml meta veri dosyalarını düzenleyerek, bu kapsayıcının görüntüsünün nasıl oluşturulacağını-hangi temel görüntüyü kullanacağını ve iç ve dış adlar ve TCP bağlantı noktaları gibi tasarım ayarlarını yapılandırabilirsiniz.

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>ASP.NET Core ile basit bir CRUD microservice uygulama

.NET Core ve Visual Studio'yu kullanarak basit bir CRUD microservice uygulamak için, Şekil 6-6'da gösterildiği gibi basit bir ASP.NET Core Web API projesi (.NET Core'da çalışan ve böylece Bir Linux Docker ana bilgisayarda çalıştırılabilen) oluşturarak başlarsınız.

![Projenin kurulumlarını gösteren Görsel Stüdyoların ekran görüntüsü.](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

**Şekil 6-6**. Visual Studio 2019'da ASP.NET Core Web API projesi oluşturma

ASP.NET Çekirdek Web API Projesi oluşturmak için önce ASP.NET Bir Web Uygulaması seçin ve ardından API türünü seçin. Projeyi oluşturduktan sonra, Varlık Çerçevesi API'sini veya diğer API'yi kullanarak MVC denetleyicilerinizi diğer Web API projesinde olduğu gibi uygulayabilirsiniz. Yeni bir Web API projesinde, bu mikro hizmetteki tek bağımlılığın ASP.NET Core'un kendisi olduğunu görebilirsiniz. Dahili olarak, *Microsoft.AspNetCore.All* bağımlılığı içinde, Şekil 6-7'de gösterildiği gibi Varlık Çerçevesi ve diğer birçok .NET Core NuGet paketine başvurur.

![Catalog.Api'nin NuGet bağımlılıklarını gösteren VS ekran görüntüsü.](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

**Şekil 6-7**. Basit bir CRUD Web API microservice bağımlılıkları

API projesi, gerekli tüm paketlere yapılan başvuruları içeren Microsoft.AspNetCore.App NuGet paketine yapılan başvuruları içerir. Diğer bazı paketleri de içerebilir.

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Entity Framework Core ile CRUD Web API hizmetlerinin uygulanması

Entity Framework (EF) Core, popüler Entity Framework veri erişim teknolojisinin hafif, genişletilebilir ve çapraz platformlu bir sürümüdür. EF Core, .NET geliştiricilerin .NET nesnelerini kullanarak bir veritabanıyla çalışmasını sağlayan bir nesne ilişkisisel mapper (ORM) dir.

Veritabanı Linux Docker görüntü için SQL Server ile bir kapsayıcıda çalışıyor çünkü katalog microservice EF ve SQL Server sağlayıcısı kullanır. Ancak, veritabanı Windows şirket içi veya Azure SQL DB gibi herhangi bir SQL Server'da dağıtılabilir. Değiştirmek için gereken tek şey ASP.NET Web API microservice bağlantı dizesi.

#### <a name="the-data-model"></a>Veri modeli

EF Core ile veri erişimi bir model kullanılarak gerçekleştirilir. Bir model, (etki alanı modeli) varlık sınıfları ve veritabanıyla bir oturumu temsil eden ve verileri sorgulayıp kaydetmenize olanak tanıyan türemiş bir bağlam (DbContext) oluşur. Varolan bir veritabanından bir model oluşturabilir, veritabanınızla eşleşecek bir modeli el ile kodlayabilir veya modelinizden bir veritabanı oluşturmak için EF geçişlerini kodlama yaklaşımını kullanarak (modeliniz zaman içinde değiştikçe veritabanını geliştirmeyi kolaylaştırır). Katalog microservice için son yaklaşımı kullanıyoruz. Aşağıdaki kod örneğinde CatalogItem varlık sınıfının bir örneğini görebilirsiniz, basit bir Düz Eski CLR Nesnesi ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) varlık sınıfıdır.

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

Ayrıca, veritabanıyla ilgili bir oturumu temsil eden bir DbContext'a da ihtiyacınız vardır. Katalog microservice için CatalogContext sınıfı aşağıdaki örnekte gösterildiği gibi DbContext taban sınıfından türetilmiştir:

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    { }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...
}
```

Ek `DbContext` uygulamalar olabilir. Örneğin, örnek Catalog.API microservice'de, veritabanına `DbContext` `CatalogContextSeed` ilk kez erişmeye çalıştığında örnek verileri otomatik olarak doldurduğu ikinci bir ad vardır. Bu yöntem demo verileri ve otomatik test senaryoları için de yararlıdır.

Içinde, nesne / veritabanı varlık eşlemeleri ve diğer [EF genişletilebilirlik noktaları](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)özelleştirmek için `OnModelCreating` yöntemi kullanın. `DbContext`

##### <a name="querying-data-from-web-api-controllers"></a>Web API denetleyicilerinden veri sorgulama

Varlık sınıflarınızın örnekleri genellikle aşağıdaki örnekte gösterildiği gibi, Dil Tümleşik Sorgusu (LINQ) kullanılarak veritabanından alınır:

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(
        CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService
            ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        context.ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("items")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType(typeof(IEnumerable<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType((int)HttpStatusCode.BadRequest)]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery]int pageSize = 10,
        [FromQuery]int pageIndex = 0,
        string ids = null)
    {
        if (!string.IsNullOrEmpty(ids))
        {
            var items = await GetItemsByIdsAsync(ids);

            if (!items.Any())
            {
                return BadRequest("ids value invalid. Must be comma-separated list of numbers");
            }

            return Ok(items);
        }

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

Veriler, varlık sınıflarınızın örnekleri kullanılarak veritabanında oluşturulur, silinir ve değiştirilir. Web API denetleyicilerinize aşağıdaki sabit kodlu örnek (bu durumda sahte veri) gibi kod ekleyebilirsiniz.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>ASP.NET Çekirdek ve Web API denetleyicilerinde Bağımlılık Enjeksiyonu

CoreASP.NET de Bağımlılık Enjeksiyonu'nu (DI) kutunun dışında kullanabilirsiniz. İsterseniz tercih ettiğiniz IoC kapsayıcısını ASP.NET Core altyapısına takabilirsiniz, ancak üçüncü taraf Bir Denetim Ters Çevirme (IoC) kapsayıcısı kurmanız gerekmez. Bu durumda, denetleyici oluşturucu aracılığıyla gerekli EF DBContext veya ek depoları doğrudan enjekte edebilirsiniz anlamına gelir.

`CatalogController` Sınıfın yukarıdaki örneğinde, `CatalogController()` bir tür nesnesi `CatalogContext` ve diğer nesneleri oluşturucu aracılığıyla enjekte ediyoruz.

Web API projesinde ayarlanan önemli bir yapılandırma, hizmetin IoC kapsayıcısına DbContext sınıf kaydıdır. `Startup` Bunu genellikle aşağıdaki **basitleştirilmiş** örnekte `services.AddDbContext<DbContext>()` gösterildiği gibi yöntemin içindeki `ConfigureServices()` yöntemi çağırarak sınıfta yaparsınız:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.MigrationsAssembly(
                typeof(Startup).GetTypeInfo().Assembly.GetName().Name);

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

- **Verileri Sorgulama** \
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- **Veri Kaydetme** \
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Docker kapları tarafından kullanılan DB bağlantı dizesi ve ortam değişkenleri

ASP.NET Core ayarlarını kullanabilir ve aşağıdaki örnekte gösterildiği gibi settings.json dosyanıza bir ConnectionString özelliği ekleyebilirsiniz:

```json
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

settings.json dosyası, ConnectionString özelliği veya başka bir özellik için varsayılan değerlere sahip olabilir. Ancak, bu özellikler Docker kullanırken docker-compose.override.yml dosyasında belirttiğiniz ortam değişkenlerinin değerleri tarafından geçersiz kılınacaktır.

Docker-compose.yml veya docker-compose.override.yml dosyalarınızdan, docker'ın aşağıdaki docker-compose.override.yml dosyasında gösterildiği gibi, bunları sizin için işletim sistemi ortam değişkenleri olarak ayarlaması için bu ortam değişkenlerini başlangıç olarak verebilirsiniz (bağlantı dize ve diğer satırları bu örnekte sarın, ancak kendi dosyanızda kaydırma olmaz).

```yml
# docker-compose.override.yml

#
catalog-api:
  environment:
    - ConnectionString=Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

Çözüm düzeyindeki docker-compose.yml dosyaları yalnızca proje veya microservice düzeyindeki yapılandırma dosyalarından daha esnek olmakla kalmıyor, aynı zamanda docker-compose dosyalarında belirtilen değerlere sahip ortam değişkenlerini geçersiz kılarsanız daha güvenlidir. Azure DevOps Services Docker dağıtım görevlerinden olduğu gibi dağıtım araçlarınız.

Son olarak, daha önceki bir kod\[örneğinde ConfigureServices yönteminde gösterildiği gibi Yapılandırma "ConnectionString"\]kullanarak bu değeri kodunuzdan alabilirsiniz.

Ancak, üretim ortamları için bağlantı dizeleri gibi sırları niçin depolayabildiğinize ilişkin ek yollar keşfetmek isteyebilirsiniz. Uygulama sırlarını yönetmenin mükemmel bir yolu [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)kullanmaktır.

Azure Key Vault, bulut uygulamalarınız ve hizmetleriniz tarafından kullanılan şifreleme anahtarlarını ve sırlarını depolamaya ve korumaya yardımcı olur. Bir sır, API tuşları, bağlantı dizeleri, parolalar, vb gibi sıkı kontrol tutmak istediğiniz bir şey ve sıkı kontrol kullanım günlüğü içerir, sona erme ayarı, erişim yönetmek, *diğerleri arasında*.

Azure Key Vault, uygulama sırlarını niçin herkesin tanımasına gerek kalmadan kullanımının çok ayrıntılı bir kontrol düzeyine izin verir. Sırlar, geliştirme veya işlemleri kesintiye uğratmadan gelişmiş güvenlik için döndürülebilir.

Anahtar Kasası'nı kullanabilmeleri için başvuruların kuruluşun Active Directory'sine kaydedilmesi gerekir.

Daha fazla bilgi için *Key Vault Concepts belgelerini* kontrol edebilirsiniz.

### <a name="implementing-versioning-in-aspnet-web-apis"></a>ASP.NET Web API'lerinde sürüm uygulama

İş gereksinimleri değiştikçe, yeni kaynak koleksiyonları eklenebilir, kaynaklar arasındaki ilişkiler değişebilir ve kaynaklardaki verilerin yapısı değiştirilebilir. Yeni gereksinimleri işlemek için bir Web API'sini güncelleştirmek nispeten basit bir işlemdir, ancak bu tür değişikliklerin Web API'sını tüketen istemci uygulamaları üzerindeki etkilerini göz önünde bulundurmanız gerekir. Bir Web API'sini tasarlayan ve uygulayan geliştirici bu API üzerinde tam denetime sahip olsa da, geliştirici uzaktan çalışan üçüncü taraf kuruluşlar tarafından oluşturulabilecek istemci uygulamaları üzerinde aynı denetim derecesine sahip değildir.

Sürüm, bir Web API'sinin açığa çıkardığı özellikleri ve kaynakları göstermesini sağlar. İstemci uygulaması daha sonra bir özellik veya kaynağın belirli bir sürümüne istek gönderebilir. Sürüm uygulamak için çeşitli yaklaşımlar vardır:

- URI sürümü oluşturma

- Sorgu dizesi sürümü oluşturma

- Üst bilgi sürümü oluşturma

Sorgu dizesi ve URI sürümü uygulamak için en basit olandır. Üstbilgi sürümü iyi bir yaklaşımdır. Ancak, üstbilgi sürümü URI sürümü kadar açık ve basit değildir. URL sürümü en basit ve en açık olduğundan, eShopOnContainers örnek uygulama URI sürümü kullanır.

URI sürümünde, eShopOnContainers örnek uygulamasında olduğu gibi, Web API'sını her değiştirdiğinizde veya kaynakların şemasını değiştirdiğinizde, her kaynak için URI'ye bir sürüm numarası eklersiniz. Varolan URI'ler, istenen sürümle eşleşen şemaya uygun kaynakları döndürerek eskisi gibi çalışmaya devam etmelidir.

Aşağıdaki kod örneğinde gösterildiği gibi, sürüm, Web API denetleyicisindeki Rota özniteliği kullanılarak ayarlanabilir ve bu da sürümü URI'de açık hale getirir (bu durumda v1).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Bu sürüm mekanizması basittir ve isteği uygun bitiş noktasına yönlendiren sunucuya bağlıdır. Ancak, REST kullanırken daha sofistike bir sürüm ve en iyi yöntem için, hipermedya kullanmanız ve [HATEOAS (Uygulama Durumu Motoru olarak Hypertext)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)uygulamak gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

- **Scott Hanselman' ı. ASP.NET Çekirdek RESTful Web API sürümü kolay** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **RESTful web API'yi sürümleme** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy Fielding' i. Sürüm, Hipermedya ve REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>ASP.NET Core Web API'nızdan Swagger açıklama meta verileri oluşturma

[Swagger,](https://swagger.io/) restful API'lerinizi tasarlamanıza, oluşturmanıza, belgelemenize ve tüketmenize yardımcı olan büyük bir araç ekosistemi tarafından desteklenen yaygın olarak kullanılan bir açık kaynak çerçevesidir. API açıklama meta veri etki alanı için standart haline gelmektedir. Swagger açıklama meta verilerini, veri odaklı mikro hizmetler veya daha gelişmiş etki alanına dayalı mikro hizmetler (aşağıdaki bölümde açıklandığı gibi) her türlü mikro hizmete eklemelisiniz.

Swagger'ın kalbi, JSON veya YAML dosyasındaki API açıklama meta verileri olan Swagger belirtimidir. Belirtim, KOLAY geliştirme, keşif ve tümleştirme için tüm kaynaklarını ve işlemlerini hem insan hem de makine tarafından okunabilir bir biçimde ayrıntılı olarak açıklayan API'niz için yeniden kullanılabilir sözleşme oluşturur.

Belirtim, OpenAPI Belirtimi'nin (OAS) temelini oluşturur ve yeniden yapılan arabirimlerin tanımlanma biçimini standartlaştırmak için açık, şeffaf ve işbirlikçi bir topluluk içinde geliştirilmiştir.

Belirtim, bir hizmetin nasıl keşfedilebildiğini ve yeteneklerinin nasıl anlaşıldığının yapısını tanımlar. Spotify, Uber, Slack ve Microsoft gibi şirketlerden bir web editörü ve Swagger belirtimleri örnekleri<https://swagger.io>dahil olmak üzere daha fazla bilgi için Swagger sitesine bakın ( ).

### <a name="why-use-swagger"></a>Neden Swagger kullanıyorsun?

API'leriniz için Swagger meta verileri oluşturmanın başlıca nedenleri şunlardır.

**Diğer ürünlerin API'lerinizi otomatik olarak tüketme ve tümleştirme yeteneği.** Düzinelerce ürün ve [ticari araç](https://swagger.io/commercial-tools/) ve birçok kütüphane ve çerçeveSwagger'ı desteklemez. [libraries and frameworks](https://swagger.io/open-source-integrations/) Microsoft, aşağıdakiler gibi Swagger tabanlı API'leri otomatik olarak tüketebilen üst düzey ürünlere ve araçlara sahiptir:

- [AutoRest](https://github.com/Azure/AutoRest). Swagger'ı aramak için otomatik olarak .NET istemci sınıfları oluşturabilirsiniz. Bu araç CLI'den kullanılabilir ve GUI aracılığıyla kolay kullanım için Visual Studio ile entegre olur.

- [Microsoft Akışı](https://flow.microsoft.com/). [API'nizi](https://flow.microsoft.com/blog/integrating-custom-api/) programlama becerisi gerektirmeden otomatik olarak kullanabilir ve üst düzey bir Microsoft Flow iş akışına entegre edebilirsiniz.

- [Microsoft PowerApps](https://powerapps.microsoft.com/). [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/)ile oluşturulmuş [PowerApps mobil uygulamalarından](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) API'nizi programlama becerisi gerektirmeden otomatik olarak tüketebilirsiniz.

- [Azure Uygulama Hizmeti Mantık Uygulamaları](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Programlama becerisi gerektirmeden [API'nizi](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)otomatik olarak kullanabilir ve Azure Uygulaması Logic App'e entegre edebilirsiniz.

**API belgelerini otomatik olarak oluşturabilme.** Karmaşık mikro hizmet tabanlı uygulamalar gibi büyük ölçekli YENIDEN kullanılabilir API'ler oluşturduğunuzda, istek ve yanıt yüklerinde kullanılan farklı veri modelleri ile birçok uç noktayı işlemeniz gerekir. Uygun belgelere sahip olmak ve sağlam bir API gezginine sahip olmak, Swagger ile birlikte olsun, API'nizin başarısı ve geliştiriciler tarafından benimsenmesi için anahtardır.

Swagger'ın meta verileri, Microsoft Flow, PowerApps ve Azure Logic Apps'ın API'lerin nasıl kullanılacağını ve bunlara nasıl bağlanış yapılacağını anlamak için kullandığı verilerdir.

*Swagger-ui*dayalı fonksiyonel API yardım sayfaları şeklinde, ASP.NET Core REST API uygulamaları için Swagger meta veri üretimi otomatikleştirmek için çeşitli seçenekler vardır.

Muhtemelen en iyi bilmek Şu anda [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) kullanılan [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) ve biz bu kılavuzda bazı ayrıntılı olarak ele alırsınız ama aynı\# zamanda [NSwag](https://github.com/RSuter/NSwag)kullanmak için seçenek var , Typescript ve C API istemcileri üretebilir, yanı sıra C\# denetleyicileri, bir Swagger veya OpenAPI belirtimi ve hatta kontrolörleri içeren .dll tarayarak, [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio)kullanarak .

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Swashbuckle NuGet paketi ile API Swagger meta veri oluşturma otomatikleştirin nasıl

Swagger meta verilerini el ile (JSON veya YAML dosyasında) oluşturmak sıkıcı bir iş olabilir. Ancak, Swagger API meta verilerini dinamik olarak oluşturmak için [Swashbuckle NuGet paketini](https://aka.ms/swashbuckledotnetcore) kullanarak ASP.NET Web API hizmetlerinin API keşfini otomatikleştirebilirsiniz.

Swashbuckle, ASP.NET Web API projeleriniz için otomatik olarak Swagger meta verilerini oluşturur. ASP.NET Core Web API projelerini ve geleneksel ASP.NET Web API'sını ve Azure API Uygulaması, Azure Mobil Uygulaması, Azure Hizmet Dokusu mikro hizmetleri gibi diğer lezzetleri ASP.NET dayalı olarak destekler. Ayrıca, başvuru uygulamasında olduğu gibi kapsayıcılarda dağıtılan düz Web API'sini de destekler.

Swashbuckle, API tüketicileriniz için zengin bir keşif ve dokümantasyon deneyimi sağlamak için API Explorer ve [Swagger veya swagger-ui'yi](https://github.com/swagger-api/swagger-ui) birleştirir. Onun Swagger meta veri jeneratör motoruna ek olarak, Swashbuckle da swagger-ui gömülü bir sürümünü içerir, Hangi otomatik olarak swashbuckle yüklü bir kez hizmet verecek.

Bu, geliştiricilerin API'nizi kullanmasına yardımcı olmak için API'nizi güzel bir keşif ui'si ile tamamlayabileceğiniz anlamına gelir. Otomatik olarak oluşturulduğu için çok az miktarda kod ve bakım gerektirir ve böylece API'nizi oluşturmaya odaklanmanıza olanak sağlar. API Explorer'ın sonucu Şekil 6-8'e benzer.

![eShopOContainers API gösteren Swagger API Explorer ekran görüntüsü.](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

**Şekil 6-8**. Swagger meta verilere dayalı Swashbuckle API Explorer—eShopOnContainers katalog microservice

Swashbuckle oluşturulan Swagger UI API belgeleri tüm yayımlanmış eylemleri içerir. API explorer burada en önemli şey değildir. Swagger meta verilerinde kendisini tanımlayabilen bir Web API'niz olduktan sonra, API'niz birçok platformu hedef alabilecek istemci proxy sınıfı kod üreteçleri de dahil olmak üzere Swagger tabanlı araçlardan sorunsuz bir şekilde kullanılabilir. Örneğin, belirtildiği gibi, [AutoRest](https://github.com/Azure/AutoRest) otomatik olarak .NET istemci sınıfları oluşturur. Ancak api istemci kitaplıklarının, sunucu saplamalarının ve belgelerin kod oluşturmalarına otomatik olarak izin veren [swagger-codegen](https://github.com/swagger-api/swagger-codegen) gibi ek araçlar da mevcuttur.

Şu anda, Swashbuckle ASP.NET Core uygulamaları için üst düzey meta paketi [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) altında beş dahili NuGet paketleri oluşur.

Bu NuGet paketlerini Web API projenize yükledikten sonra, Aşağıdaki **basitleştirilmiş** kodda olduğu gibi Başlangıç sınıfında Swagger'ı yapılandırmanız gerekir:

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
            options.SwaggerDoc("v1", new OpenApiInfo
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample"
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

Bu işlem yapıldıktan sonra, uygulamanızı başlatabilir ve aşağıdaki Gibi URL'leri kullanarak aşağıdaki Swagger JSON ve Kullanıcı Altı Kullanıcı Tarafından kullanıcı tarafından kullanılabilir:

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

Daha önce swashbuckle tarafından oluşturulan oluşturulan ui `http://<your-root-url>/swagger`gibi bir URL gördüm. Şekil 6-9'da herhangi bir API yöntemini nasıl test edebileceğinizi de görebilirsiniz.

![Kullanılabilir test araçlarını gösteren Swagger UI ekran görüntüsü.](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

**Şekil 6-9**. Katalog/Öğeler API yöntemini test eden Swashbuckle UI

Swagger UI API ayrıntısı yanıtın bir örneğini gösterir ve geliştirici keşfi için harika olan gerçek API'yi çalıştırmak için kullanılabilir. Şekil 6-10 `http://<your-root-url>/swagger/v1/swagger.json` [Postacı](https://www.getpostman.com/)kullanarak talep ettiğinizde eShopOnContainers microservice oluşturulan Swagger JSON meta verileri gösterir (hangi araçları altında kullanmak) .

![Swagger JSON meta verilerini gösteren örnek postacı ui ekran görüntüsü.](./media/data-driven-crud-microservice/swagger-json-metadata.png)

**Şekil 6-10**. Swagger JSON meta verileri

Bu kadar basit. Ve otomatik olarak oluşturulduğundan, API'nize daha fazla işlevsellik eklediğinizde Swagger meta verileri büyür.

### <a name="additional-resources"></a>Ek kaynaklar

- **Swagger kullanarak ASP.NET Web API Yardım Sayfaları** \
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- **Swashbuckle ve ASP.NET Core ile başlayın** \
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- **NSwag ve ASP.NET Core ile başlayın** \
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> [Önceki](microservice-application-design.md)
> [Sonraki](multi-container-applications-docker-compose.md)
