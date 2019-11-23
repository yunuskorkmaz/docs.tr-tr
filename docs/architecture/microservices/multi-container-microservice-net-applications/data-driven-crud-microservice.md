---
title: Basit bir veri temelli CRUD mikro hizmeti oluşturma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Bir mikro Hizmetler uygulaması bağlamında basit bir CRUD (veri odaklı) mikro hizmeti oluşturmayı anlayın.
ms.date: 01/07/2019
ms.openlocfilehash: 56cec488c22b0f3b45b9c1dae9d2f4fd7ef7beaa
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737364"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Basit bir veri temelli CRUD mikro hizmeti oluşturma

Bu bölümde, bir veri kaynağı üzerinde oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemlerini gerçekleştiren basit bir mikro hizmetin nasıl oluşturulacağı özetlenmektedir.

## <a name="designing-a-simple-crud-microservice"></a>Basit bir CRUD mikro hizmeti tasarlama

Bir görünüm tasarım noktasından, Kapsayıcılı mikro hizmet türü çok basittir. Belki de çözüme sorunu basittir veya uygulama yalnızca kavram kanıtı olabilir.

![Basit bir CRUD mikro hizmet dahili tasarım deseninin gösterildiği diyagram.](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

**Şekil 6-4**. Basit CRUD mikro hizmetleri için dahili tasarım

Bu tür basit veri sürücüsü hizmetine bir örnek, eShopOnContainers örnek uygulamasından Katalog mikro hizmetidir. Bu hizmet türü, tüm işlevlerini, veri modeli, iş mantığı ve veri erişim kodu için sınıflar içeren tek bir ASP.NET Core Web API projesinde uygular. Ayrıca, Şekil 6-5 ' de gösterildiği gibi, ilgili verileri SQL Server çalıştıran bir veritabanında depolar (geliştirme ve test amaçları için başka bir kapsayıcı olarak), ancak normal SQL Server ana bilgisayar da olabilir.

![Veri odaklı/CRUD mikro hizmet kapsayıcısını gösteren diyagram.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

**Şekil 6-5**. Basit veri odaklı/CRUD mikro hizmet tasarımı

Önceki diyagramda, Katalog veritabanı da dahil olmak üzere, aynı Docker konağında bulunmayan veya bulunmayan mantıksal Katalog mikro hizmeti gösterilmektedir. Veritabanının aynı Docker ana bilgisayarında olması, geliştirme için uygun olabilir, ancak üretime yönelik değildir. Bu tür bir hizmet geliştirirken yalnızca [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) ve [Entity Framework Core](https://docs.microsoft.com/ef/core/index)gibi bir veri ERIŞIM API 'si veya ORM yeterlidir. Ayrıca, sonraki bölümde açıklandığı gibi, hizmetinizin neleri sunduğunu bir açıklama sağlamak için [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) aracılığıyla [Swagger](https://swagger.io/) meta verileri otomatik olarak oluşturabilirsiniz.

Bulutta veya şirket içinde bir veritabanı sağlamaya gerek kalmadan tüm bağımlılıklarınızın çalışır durumda olmasını sağlayabileceğinizden, bir Docker kapsayıcısı içinde SQL Server gibi bir veritabanı sunucusunu çalıştırmanın geliştirme ortamları için harika olduğunu unutmayın. Bu, tümleştirme testlerini çalıştırırken oldukça kullanışlıdır. Ancak, üretim ortamlarında, genellikle bu yaklaşımla yüksek kullanılabilirlik olmadığı için bir kapsayıcıda veritabanı sunucusu çalıştırmak önerilmez. Azure 'da bir üretim ortamında, Azure SQL DB 'yi veya yüksek kullanılabilirlik ve yüksek ölçeklenebilirlik sağlayabilen başka bir veritabanı teknolojisini kullanmanız önerilir. Örneğin, bir NoSQL yaklaşımı için CosmosDB ' yi seçebilirsiniz.

Son olarak, Dockerfile ve Docker-Compose. yıml meta veri dosyalarını düzenleyerek, bu kapsayıcının görüntüsünün nasıl oluşturulacağını — hangi temel görüntünün kullanılacağını ve iç ve dış adlar ve TCP bağlantı noktaları gibi tasarım ayarlarını yapılandırabilirsiniz.

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>ASP.NET Core ile basit bir CRUD mikro hizmeti uygulama

.NET Core ve Visual Studio kullanarak basit bir CRUD mikro hizmeti uygulamak için, Şekil 6-6 ' de gösterildiği gibi basit bir ASP.NET Core Web API projesi (bir Linux Docker konağında çalışacak şekilde .NET Core üzerinde çalışan) oluşturarak başlayın.

![Projenin kurulumunu gösteren görsel Studios ekran görüntüsü.](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

**Şekil 6-6**. Visual Studio 'da ASP.NET Core Web API projesi oluşturma

ASP.NET Core Web API projesi oluşturmak için önce bir ASP.NET Core Web uygulaması seçin ve ardından API türünü seçin. Projeyi oluşturduktan sonra, Entity Framework API 'sini veya diğer API 'yi kullanarak, MVC denetleyicilerinizi diğer Web API projesinde yaptığınız gibi uygulayabilirsiniz. Yeni bir Web API projesinde, bu mikro hizmette sahip olduğunuz tek bağımlılığın ASP.NET Core kendisinde olduğunu görebilirsiniz. Dahili olarak, *Microsoft. AspNetCore. All* bağımlılığında, Şekil 6-7 ' de gösterildiği gibi Entity Framework ve diğer birçok .NET Core NuGet paketine başvuruyorlar.

![Catalog. API ' nin NuGet bağımlılıklarının gösterildiği VS 'nin ekran görüntüsü.](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

**Şekil 6-7**. Basit bir CRUD Web API mikro hizmetindeki bağımlılıklar

API projesi, tüm gerekli paketlere yönelik başvuruları içeren Microsoft. AspNetCore. app NuGet paketine yönelik başvuruları içerir. Diğer bazı paketleri de içerebilir.

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Entity Framework Core ile CRUD Web API hizmetlerini uygulama

Entity Framework (EF) Core, popüler Entity Framework veri erişim teknolojisinin basit, genişletilebilir ve platformlar arası bir sürümüdür. EF Core, .NET geliştiricilerinin .NET nesnelerini kullanarak bir veritabanıyla çalışmasını sağlayan bir nesne ilişkisel Eşleyici (ORM).

Veritabanı, Linux Docker görüntüsü için SQL Server bir kapsayıcıda çalıştığı için, Katalog mikro hizmeti EF ve SQL Server sağlayıcısını kullanır. Ancak, veritabanı Windows Şirket içi veya Azure SQL VERITABANı gibi herhangi bir SQL Server dağıtılabilir. Değiştirmeniz gereken tek şey, ASP.NET Web API mikro hizmetindeki bağlantı dizesidir.

#### <a name="the-data-model"></a>Veri modeli

EF Core, veri erişimi bir model kullanılarak gerçekleştirilir. Bir model (etki alanı modeli) varlık sınıfları ve veritabanı ile bir oturumu temsil eden türetilmiş bir bağlam (DbContext) ve verileri sorgulamanızı ve kaydetmenizi sağlar. Var olan bir veritabanından bir model oluşturabilir, bir modeli veritabanınıza eşleştirmek üzere el ile kodlayabilir veya modelinizde bir veritabanı oluşturmak için EF geçişlerini kullanabilirsiniz (Bu, modelin zaman içinde değiştiği şekilde veritabanını kolayca geliştirebilir). Katalog mikro hizmeti için son yaklaşımı kullandık. Aşağıdaki kod örneğinde, bir basit düz eski CLR nesnesi ([poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) varlık sınıfı olan CatalogItem varlık sınıfının bir örneğini görebilirsiniz.

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

Ayrıca, veritabanı ile bir oturumu temsil eden bir DbContext gerekir. Katalog mikro hizmeti için, CatalogContext sınıfı, aşağıdaki örnekte gösterildiği gibi DbContext temel sınıfından türetilir:

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

Ek `DbContext` uygulamalarına sahip olabilirsiniz. Örneğin, örnek katalog. API mikro hizmetinde, veritabanına erişmeye çalıştığında örnek verileri otomatik olarak dolduran `CatalogContextSeed` adlı ikinci bir `DbContext` vardır. Bu yöntem, tanıtım verileri ve otomatikleştirilmiş test senaryoları için yararlıdır.

`DbContext`içinde, nesne/veritabanı varlık eşlemelerini ve diğer [EF genişletilebilirlik noktalarını](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)özelleştirmek için `OnModelCreating` yöntemini kullanırsınız.

##### <a name="querying-data-from-web-api-controllers"></a>Web API denetleyicilerinden verileri sorgulama

Varlık sınıflarınızın örnekleri, aşağıdaki örnekte gösterildiği gibi, genellikle dil ile tümleşik sorgu (LINQ) kullanılarak veritabanından alınır:

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

Veri, varlık sınıflarınızın örnekleri kullanılarak oluşturulur, silinir ve değiştirilir. Web API denetleyicilerinize aşağıdaki sabit kodlanmış örnek (Bu durumda sahte veriler) gibi bir kod ekleyebilirsiniz.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>ASP.NET Core ve Web API denetleyicilerine bağımlılık ekleme

ASP.NET Core, bağımlılık ekleme (dı) kutusunu kutudan çıkar. Tercih ettiğiniz IOC kapsayıcısını ASP.NET Core altyapısına takabilirsiniz, ancak isterseniz, üçüncü taraf bir denetim (IOC) kapsayıcısı ayarlamanız gerekmez. Bu durumda, gerekli EF DBContext veya ek depoları denetleyici Oluşturucusu aracılığıyla doğrudan ekleyebileceðiniz anlamına gelir.

`CatalogController` sınıfının Yukarıdaki örnekte, `CatalogController()` Oluşturucusu aracılığıyla `CatalogContext` türünde bir nesne ve diğer nesneler ekleme.

Web API projesinde ayarlanmakta olan önemli bir yapılandırma, hizmetin IOC kapsayıcısına DbContext sınıfı kaydolmalıdır. Genellikle, aşağıdaki örnekte gösterildiği gibi `ConfigureServices()` yönteminin içindeki `services.AddDbContext<DbContext>()` yöntemini çağırarak `Startup` sınıfında bunu yapabilirsiniz:

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

- **Veri sorgulama** \
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- **Veri kaydetme** \
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Docker kapsayıcıları tarafından kullanılan DB bağlantı dizesi ve ortam değişkenleri

Aşağıdaki örnekte gösterildiği gibi Settings. JSON dosyanıza ASP.NET Core ayarlarını kullanabilir ve bir ConnectionString özelliği ekleyebilirsiniz:

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

Settings. JSON dosyası ConnectionString özelliği veya diğer herhangi bir özellik için varsayılan değerlere sahip olabilir. Ancak, Docker kullanılırken, bu özellikler Docker-Compose. override. yıml dosyasında belirttiğiniz ortam değişkenlerinin değerleri tarafından geçersiz kılınır.

Docker-Compose. yıml veya Docker-Compose. override. yıml dosyalarından, bu ortam değişkenlerini, Docker 'ın sizin için aşağıdaki Docker-Compose. override. yıml dosyasında gösterildiği gibi, sizin için işletim sistemi ortam değişkenleri olarak ayarlayabilmesi için başlatabilirsiniz (bağlantı Bu örnekte dize ve diğer satırlar kaydırılır, ancak kendi dosyanıza sarılmaz.

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

Çözüm düzeyindeki Docker-Compose. yıml dosyaları, proje veya mikro hizmet düzeyindeki yapılandırma dosyalarından yalnızca daha esnek değildir, ancak değerleri ayarlanan değerlerle Docker-Compose dosyalarında belirtilen ortam değişkenlerini geçersiz kılarsınız, daha da güvenli hale geldi. Azure DevOps Services Docker dağıtım görevleri gibi dağıtım araçlarınız.

Son olarak, bir önceki kod örneğinde ConfigureServices yönteminde gösterildiği gibi, yapılandırma\["ConnectionString"\]kullanarak bu değeri kodunuzda alabilirsiniz.

Ancak, üretim ortamları için bağlantı dizeleri gibi gizli dizileri nasıl depolayabileceğiniz konusunda ek yöntemleri incelemek isteyebilirsiniz. Uygulama gizli dizilerini yönetmenin harika bir yolu [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)kullanmaktır.

Azure Key Vault, bulut Uygulamalarınız ve hizmetleriniz tarafından kullanılan şifreleme anahtarlarını ve gizli dizileri depolamanıza ve korumanıza yardımcı olur. Gizli dizi, API anahtarları, bağlantı dizeleri, parolalar vb. gibi tam denetim sağlamak istediğiniz her şey, kullanım günlüğü, zaman aşımı ayarlama, *diğer kullanıcıların arasında*erişim yönetimi içerir.

Azure Key Vault, uygulama gizli dizileri kullanımının herkes tarafından haberdar olmasına gerek kalmadan çok ayrıntılı denetim düzeyine izin verir. Gizli dizileri geliştirme veya işlemleri kesintiye uğratmadan gelişmiş güvenlik için de döndürülebilir.

Uygulamaların, Key Vault kullanabilmesi için kuruluşun Active Directory kayıtlı olmaları gerekir.

Daha fazla ayrıntı için *Key Vault kavramlar belgelerini* kontrol edebilirsiniz.

### <a name="implementing-versioning-in-aspnet-web-apis"></a>ASP.NET Web API 'Lerinde sürüm oluşturma uygulama

İş gereksinimleri değiştikçe, yeni kaynak koleksiyonları eklenebilir, kaynaklar arasındaki ilişkiler değişebilir ve kaynaklardaki verilerin yapısı değiştirilebilir. Bir Web API 'sini yeni gereksinimleri işleyecek şekilde güncelleştirmek nispeten doğrudan bir işlemdir, ancak söz konusu değişikliklerin Web API 'sini kullanan istemci uygulamalarında sahip olacağı etkileri göz önünde bulundurmanız gerekir. Bir Web API 'SI tasarlayan ve uygulayan geliştirici, bu API üzerinde tam denetime sahiptir, ancak geliştirici, üçüncü taraf kuruluşların uzaktan çalıştığı istemci uygulamalar üzerinde aynı denetim derecesine sahip değildir.

Sürüm oluşturma, Web API 'sinin sunduğu özellikleri ve kaynakları belirtecek şekilde olanak sağlar. İstemci uygulama, istekleri bir özelliğin veya kaynağın belirli bir sürümüne gönderebilir. Sürüm oluşturmayı uygulamak için birkaç yaklaşım vardır:

- URI sürümü oluşturma

- Sorgu dizesi sürümü oluşturma

- Üst bilgi sürümü oluşturma

Sorgu dizesi ve URI sürümü oluşturma en basit uygulama kullanmaktır. Üst bilgi sürümü oluşturma iyi bir yaklaşımdır. Ancak, üstbilgi sürümü oluşturma, URI sürümü oluşturma kadar açık ve kolay değildir. URL sürümü oluşturma en basit ve en açık olduğundan, eShopOnContainers örnek uygulaması URI sürümü oluşturmayı kullanır.

URI sürümü oluşturma ile, eShopOnContainers örnek uygulamasında olduğu gibi, Web API 'sini her değiştirdiğinizde veya kaynak şemasını değiştirdiğinizde her kaynak için URI 'ye bir sürüm numarası eklersiniz. Mevcut URI 'Ler, istenen sürümle eşleşen şemaya uyan kaynakları döndürerek daha önce çalışmaya devam etmelidir.

Aşağıdaki kod örneğinde gösterildiği gibi, sürüm, Web API denetleyicisindeki Route özniteliği kullanılarak ayarlanabilir, bu da sürümü URI 'de (Bu durumda v1) açık hale getirir.

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Bu sürüm oluşturma mekanizması basittir ve isteği uygun uç noktaya yönlendirme sunucusuna bağlıdır. Ancak, daha gelişmiş bir sürüm oluşturma ve REST kullanırken en iyi yöntem için hiper medya kullanmanız ve [Hateoas (uygulama durumu altyapısı olarak köprü metni)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)uygulamanız gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

- **Scott Hanselman. ASP.NET Core yeniden oluşturulmuş Web API 'SI sürümü kullanımı kolay** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Yeniden bir Web API 'Sinin sürümü oluşturma** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy Fielding. Sürüm oluşturma, hiper medya ve REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>ASP.NET Core Web API 'nizden Swagger açıklaması meta verileri oluşturuluyor

[Swagger](https://swagger.io/) , daha önce yaptığınız API 'lerinizi tasarlamanıza, oluşturmanıza, belgelemenize ve kullanmanıza yardımcı olan büyük bir araç tarafından desteklenen, yaygın olarak kullanılan bir açık kaynak çerçevesidir. API 'Ler açıklama meta verileri etki alanı için standart haline geliyor. Veri odaklı mikro hizmetler veya daha gelişmiş etki alanı tabanlı mikro hizmetler (aşağıdaki bölümde açıklandığı gibi) herhangi bir tür mikro hizmetle Swagger açıklaması meta verilerini dahil etmelisiniz.

Swagger kalbi, bir JSON veya YAML dosyasındaki API açıklaması meta verileri olan Swagger belirtimidir. Bu belirtim, API 'niz için yeniden teknik sözleşme oluşturur ve kolay geliştirme, bulma ve tümleştirme için hem insanlar hem de makine tarafından okunabilen bir biçimde tüm kaynaklarını ve işlemlerini ayrıntılandıran bir şekilde ayrıntılı hale getirin.

Belirtim, Openapı belirtiminin (OAS) temelini oluşturur ve bir açık, şeffaf ve işbirliğine dayalı bir topluluk içinde geliştirilmiş arabirimlerin tanımlanma biçimini standartlaştırır.

Belirtim, bir hizmetin nasıl keşfedildiğini ve yeteneklerini nasıl anladığını belirleyen yapıyı tanımlar. Bir Web Düzenleyicisi ve Spotify, Uber, bolluk ve Microsoft gibi şirketlerin Swagger belirtimlerinin örnekleri dahil daha fazla bilgi için bkz. Swagger sitesi (<https://swagger.io>).

### <a name="why-use-swagger"></a>Swagger neden kullanılmalıdır?

API 'leriniz için Swagger meta verileri oluşturmaya yönelik başlıca nedenler şunlardır.

**Diğer ürünlerin API 'lerinizi otomatik olarak tüketmesi ve tümleştirmesine olanak tanır**. Onlarca ürün ve [Ticari Araçlar](https://swagger.io/commercial-tools/) ve birçok [kitaplık ve çerçeve](https://swagger.io/open-source-integrations/) Swagger 'yi destekler. Microsoft, Swagger tabanlı API 'Leri otomatik olarak kullanabilen ve aşağıdakiler gibi üst düzey ürün ve araçlara sahiptir:

- [Oto Rest](https://github.com/Azure/AutoRest). Swagger 'yi çağırmak için otomatik olarak .NET istemci sınıfları oluşturabilirsiniz. Bu araç, CLı 'dan kullanılabilir ve ayrıca GUI aracılığıyla kolayca kullanılmak üzere Visual Studio ile tümleşir.

- [Microsoft Flow](https://flow.microsoft.com/). [API 'nizi otomatik olarak kullanabilir ve](https://flow.microsoft.com/blog/integrating-custom-api/) bir üst düzey Microsoft Flow iş akışında tümleştirebilirsiniz; böylece programlama becerileri gerekli değildir.

- [Microsoft PowerApps](https://powerapps.microsoft.com/). API 'nizi, [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/)Ile oluşturulmuş [PowerApps mobil uygulamalarından](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) otomatik olarak kullanabilir ve programlama becerileri gerektirmez.

- [Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). [API 'nizi otomatik olarak kullanabilir ve bir Azure App Service Logic App ile tümleştirebilirsiniz ve](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)böylece programlama becerileri gerekli değildir.

**API belgelerini otomatik olarak oluşturma yeteneği**. Karmaşık mikro hizmet tabanlı uygulamalar gibi büyük ölçekli yeniden kullanılabilir API 'Ler oluşturduğunuzda, istek ve yanıt yüklerinizde kullanılan farklı veri modelleriyle birçok uç nokta işlemeniz gerekir. Doğru belgelere sahip olma ve Swagger ile yaptığınız gibi katı bir API Gezgini içeren, API 'nizin başarısı ve geliştiriciler tarafından benimseme için anahtar.

Swagger 'nin meta verileri, API 'Leri kullanmayı ve bunlara bağlanmayı anlamak için Microsoft Flow, PowerApps ve Azure Logic Apps kullanmaktır.

*Swagger-UI*temel ALıNARAK işlevsel API Yardım sayfaları biçiminde ASP.NET Core REST API uygulamaları için Swagger meta veri üretimini otomatik hale getirmek için çeşitli seçenekler vardır.

Büyük olasılıkla [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) 'da kullanılmakta olan [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) , bu kılavuzda bazı ayrıntılarla ele alacağız, ancak [nswag](https://github.com/RSuter/NSwag)kullanma seçeneği de mevcuttur. bunun yanı sıra, [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio)kullanarak, bir Swagger veya openapı belirtiminden ve ayrıca, denetleyicileri Içeren. dll dosyasını tarayarak, TypeScript ve c\# API istemcilerinin yanı sıra c\# denetleyicilerini de üretebilirler.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Swashbuckle NuGet paketi ile API Swagger meta veri üretimini otomatikleştirme

Swagger meta verilerinin el ile oluşturulması (bir JSON veya YAML dosyasında) sıkıcı bir iş olabilir. Bununla birlikte, dinamik olarak Swagger API meta verilerini oluşturmak için [swashbuckle NuGet paketini](https://aka.ms/swashbuckledotnetcore) kullanarak ASP.NET Web API hizmetlerinin API bulmayı otomatik hale getirebilirsiniz.

Swashbuckle, ASP.NET Web API projeleriniz için Swagger meta verilerini otomatik olarak oluşturur. ASP.NET Core Web API projelerini ve geleneksel ASP.NET Web API 'sini ve ASP.NET tabanlı Azure API uygulaması, Azure mobil uygulaması, Azure Service Fabric mikro hizmetleri gibi diğer tüm tercihleri destekler. Ayrıca, başvuru uygulamasındaki gibi kapsayıcılarda dağıtılan düz Web API 'sini de destekler.

Swashbuckle, API Gezginini ve Swagger ya da [Swagger arabirimini](https://github.com/swagger-api/swagger-ui) birleştirerek API Tüketicileriniz için zengin bir keşif ve belge deneyimi sağlar. Sashbuckle, Swagger meta veri Oluşturucu altyapısına ek olarak, swashbuckle yüklendikten sonra otomatik olarak sunulacak olan Swagger-UI ' nin ekli bir sürümünü de içerir.

Bu, geliştiricilerin API 'nizi kullanmasına yardımcı olmak için iyi bir keşif Kullanıcı arabirimi ile API 'nizi tamamlayoluşturabileceğiniz anlamına gelir. Otomatik olarak oluşturulduğundan, API 'nizi oluşturmaya odaklanmanızı sağlayan çok az miktarda kod ve bakım gerektirir. API Explorer için sonuç Şekil 6-8 gibi görünür.

![EShopOContainers API 'sini görüntüleyen Swagger API Explorer 'ın ekran görüntüsü.](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

**Şekil 6-8**. Swagger meta verileri tabanlı swashbuckle API Explorer — eShopOnContainers Catalog mikro hizmeti

Swashbuckle tarafından oluşturulan Swagger Kullanıcı arabirimi API 'SI belgeleri, yayımlanan tüm eylemleri içerir. API Explorer buradaki en önemli şey değildir. Swagger meta verilerde kendisini betimleyen bir Web API 'niz olduktan sonra, API 'niz birçok platformu hedefleyen istemci proxy sınıfı kod oluşturucuları dahil olmak üzere Swagger tabanlı araçlardan sorunsuz bir şekilde kullanılabilir. Örneğin, belirtildiği gibi, otomatik [rest](https://github.com/Azure/AutoRest) otomatik olarak .NET istemci sınıfları oluşturur. Ancak, API istemci kitaplıklarının, sunucu saplamalarının ve belgelerinin otomatik olarak kod oluşturmaya izin veren [Swagger-CodeGen](https://github.com/swagger-api/swagger-codegen) gibi ek araçlar da mevcuttur.

Şu anda, swashbuckle, ASP.NET Core uygulamalar için üst düzey meta-paket [swashbuckle. AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) altında beş iç NuGet paketinden oluşur.

Bu NuGet paketlerini Web API Projenize yükledikten sonra, başlangıç sınıfında, aşağıdaki kodda olduğu gibi Swagger 'yi yapılandırmanız gerekir (Basitleştirilmiş):

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

Bu işlem tamamlandıktan sonra, aşağıdaki gibi URL 'Leri kullanarak uygulamanızı başlatabilir ve aşağıdaki Swagger JSON ve UI uç noktalarına gidebilirsiniz:

```url
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

Daha önce `http://<your-root-url>/swagger`gibi bir URL için swashbuckle tarafından oluşturulan oluşturulan kullanıcı arabirimini gördünüz. Şekil 6-9 ' de, herhangi bir API yöntemini nasıl test kullanabileceğinizi da görebilirsiniz.

![Kullanılabilir test araçlarını gösteren Swagger Kullanıcı arabiriminin ekran görüntüsü.](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

**Şekil 6-9**. Sashbuckle Kullanıcı arabirimi Katalog/öğe API yöntemini test etme

Swagger Kullanıcı arabirimi API 'SI ayrıntısı yanıtın bir örneğini gösterir ve geliştirici keşfi için harika olan gerçek API 'yi yürütmek için kullanılabilir. Şekil 6-10, [Postman](https://www.getpostman.com/)kullanarak `http://<your-root-url>/swagger/v1/swagger.json` Istediğinizde, eShopOnContainers mikro hizmetinden oluşturulan Swagger JSON meta verilerini (Bu araçların altında kullanıldığı) gösterir.

![Swagger JSON meta verilerini gösteren örnek bir Postman Kullanıcı arabiriminin ekran görüntüsü.](./media/data-driven-crud-microservice/swagger-json-metadata.png)

**Şekil 6-10**. Swagger JSON meta verileri

Bu basit bir işlemdir. Otomatik olarak oluşturulduğu için, API 'nize daha fazla işlevsellik eklediğinizde Swagger meta verileri büyüyecektir.

### <a name="additional-resources"></a>Ek kaynaklar

- **Swagger \ kullanarak Web API 'Si yardım sayfaları ASP.net**
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- **Swashbuckle ve ASP.NET Core \ ile çalışmaya** başlayın
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- **NSwag ve ASP.NET Core ile çalışmaya başlama** \
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> [Önceki](microservice-application-design.md)
> [İleri](multi-container-applications-docker-compose.md)
