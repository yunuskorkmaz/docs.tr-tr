---
title: Basit bir veri temelli CRUD mikro hizmeti oluşturma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Bir mikro Hizmetler uygulaması bağlamında basit bir CRUD (veri odaklı) mikro hizmeti oluşturmayı anlayın.
ms.date: 01/07/2019
ms.openlocfilehash: 53aba727c8dae35df8b34bc1558c0cc390fe2014
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296664"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="74fef-103">Basit bir veri temelli CRUD mikro hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="74fef-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="74fef-104">Bu bölümde, bir veri kaynağı üzerinde oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemlerini gerçekleştiren basit bir mikro hizmetin nasıl oluşturulacağı özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="74fef-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="74fef-105">Basit bir CRUD mikro hizmeti tasarlama</span><span class="sxs-lookup"><span data-stu-id="74fef-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="74fef-106">Bir görünüm tasarım noktasından, Kapsayıcılı mikro hizmet türü çok basittir.</span><span class="sxs-lookup"><span data-stu-id="74fef-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="74fef-107">Belki de çözüme sorunu basittir veya uygulama yalnızca kavram kanıtı olabilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Basit bir CRUD mikro hizmeti, dahili bir tasarım modelidir.](./media/image4.png)

<span data-ttu-id="74fef-109">**Şekil 6-4**.</span><span class="sxs-lookup"><span data-stu-id="74fef-109">**Figure 6-4**.</span></span> <span data-ttu-id="74fef-110">Basit CRUD mikro hizmetleri için dahili tasarım</span><span class="sxs-lookup"><span data-stu-id="74fef-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="74fef-111">Bu tür basit veri sürücüsü hizmetine bir örnek, eShopOnContainers örnek uygulamasından Katalog mikro hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="74fef-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="74fef-112">Bu hizmet türü, tüm işlevlerini, veri modeli, iş mantığı ve veri erişim kodu için sınıflar içeren tek bir ASP.NET Core Web API projesinde uygular.</span><span class="sxs-lookup"><span data-stu-id="74fef-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="74fef-113">Ayrıca, Şekil 6-5 ' de gösterildiği gibi, ilgili verileri SQL Server çalıştıran bir veritabanında depolar (geliştirme ve test amaçları için başka bir kapsayıcı olarak), ancak normal SQL Server ana bilgisayar da olabilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Mantıksal Katalog mikro hizmeti, katalog veritabanını içerir ve aynı Docker ana bilgisayarında yer alabilir.](./media/image5.png)

<span data-ttu-id="74fef-116">**Şekil 6-5**.</span><span class="sxs-lookup"><span data-stu-id="74fef-116">**Figure 6-5**.</span></span> <span data-ttu-id="74fef-117">Basit veri odaklı/CRUD mikro hizmet tasarımı</span><span class="sxs-lookup"><span data-stu-id="74fef-117">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="74fef-118">Bu tür bir hizmet geliştirirken yalnızca [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) ve [Entity Framework Core](https://docs.microsoft.com/ef/core/index)gibi bir veri ERIŞIM API 'si veya ORM yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="74fef-118">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="74fef-119">Ayrıca, sonraki bölümde açıklandığı gibi, hizmetinizin neleri sunduğunu bir açıklama sağlamak için [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) aracılığıyla [Swagger](https://swagger.io/) meta verileri otomatik olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-119">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="74fef-120">Bulutta veya şirket içinde bir veritabanı sağlamaya gerek kalmadan tüm bağımlılıklarınızın çalışır durumda olmasını sağlayabileceğinizden, bir Docker kapsayıcısı içinde SQL Server gibi bir veritabanı sunucusunu çalıştırmanın geliştirme ortamları için harika olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="74fef-120">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="74fef-121">Bu, tümleştirme testlerini çalıştırırken oldukça kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="74fef-121">This is very convenient when running integration tests.</span></span> <span data-ttu-id="74fef-122">Ancak, üretim ortamlarında, genellikle bu yaklaşımla yüksek kullanılabilirlik olmadığı için bir kapsayıcıda veritabanı sunucusu çalıştırmak önerilmez.</span><span class="sxs-lookup"><span data-stu-id="74fef-122">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="74fef-123">Azure 'da bir üretim ortamında, Azure SQL DB 'yi veya yüksek kullanılabilirlik ve yüksek ölçeklenebilirlik sağlayabilen başka bir veritabanı teknolojisini kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-123">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="74fef-124">Örneğin, bir NoSQL yaklaşımı için CosmosDB ' yi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-124">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="74fef-125">Son olarak, Dockerfile ve Docker-Compose. yıml meta veri dosyalarını düzenleyerek, bu kapsayıcının görüntüsünün nasıl oluşturulacağını — hangi temel görüntünün kullanılacağını ve iç ve dış adlar ve TCP bağlantı noktaları gibi tasarım ayarlarını yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-125">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="74fef-126">ASP.NET Core ile basit bir CRUD mikro hizmeti uygulama</span><span class="sxs-lookup"><span data-stu-id="74fef-126">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="74fef-127">.NET Core ve Visual Studio kullanarak basit bir CRUD mikro hizmeti uygulamak için, Şekil 6-6 ' de gösterildiği gibi basit bir ASP.NET Core Web API projesi (bir Linux Docker konağında çalışacak şekilde .NET Core üzerinde çalışan) oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="74fef-127">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![ASP.NET Core Web API projesi oluşturmak için önce bir ASP.NET Core Web uygulaması seçin ve ardından API türünü seçin.](./media/image6.png)

<span data-ttu-id="74fef-129">**Şekil 6-6**.</span><span class="sxs-lookup"><span data-stu-id="74fef-129">**Figure 6-6**.</span></span> <span data-ttu-id="74fef-130">Visual Studio 'da ASP.NET Core Web API projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="74fef-130">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="74fef-131">Projeyi oluşturduktan sonra, Entity Framework API 'sini veya diğer API 'yi kullanarak, MVC denetleyicilerinizi diğer Web API projesinde yaptığınız gibi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-131">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="74fef-132">Yeni bir Web API projesinde, bu mikro hizmette sahip olduğunuz tek bağımlılığın ASP.NET Core kendisinde olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-132">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="74fef-133">Dahili olarak, *Microsoft. AspNetCore. All* bağımlılığında, Şekil 6-7 ' de gösterildiği gibi Entity Framework ve diğer birçok .NET Core NuGet paketine başvuruyorlar.</span><span class="sxs-lookup"><span data-stu-id="74fef-133">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 6-7.</span></span>

![API projesi, tüm gerekli paketlere yönelik başvuruları içeren Microsoft. AspNetCore. app NuGet paketine yönelik başvuruları içerir.](./media/image8.png)

<span data-ttu-id="74fef-136">**Şekil 6-7**.</span><span class="sxs-lookup"><span data-stu-id="74fef-136">**Figure 6-7**.</span></span> <span data-ttu-id="74fef-137">Basit bir CRUD Web API mikro hizmetindeki bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="74fef-137">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="74fef-138">Entity Framework Core ile CRUD Web API hizmetlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="74fef-138">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="74fef-139">Entity Framework (EF) Core, popüler Entity Framework veri erişim teknolojisinin basit, genişletilebilir ve platformlar arası bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="74fef-139">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="74fef-140">EF Core, .NET geliştiricilerinin .NET nesnelerini kullanarak bir veritabanıyla çalışmasını sağlayan bir nesne ilişkisel Eşleyici (ORM).</span><span class="sxs-lookup"><span data-stu-id="74fef-140">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="74fef-141">Veritabanı, Linux Docker görüntüsü için SQL Server bir kapsayıcıda çalıştığı için, Katalog mikro hizmeti EF ve SQL Server sağlayıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="74fef-141">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="74fef-142">Ancak, veritabanı Windows Şirket içi veya Azure SQL VERITABANı gibi herhangi bir SQL Server dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-142">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="74fef-143">Değiştirmeniz gereken tek şey, ASP.NET Web API mikro hizmetindeki bağlantı dizesidir.</span><span class="sxs-lookup"><span data-stu-id="74fef-143">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="74fef-144">Veri modeli</span><span class="sxs-lookup"><span data-stu-id="74fef-144">The data model</span></span>

<span data-ttu-id="74fef-145">EF Core, veri erişimi bir model kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-145">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="74fef-146">Bir model (etki alanı modeli) varlık sınıfları ve veritabanı ile bir oturumu temsil eden türetilmiş bir bağlam (DbContext) ve verileri sorgulamanızı ve kaydetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="74fef-146">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="74fef-147">Var olan bir veritabanından bir model oluşturabilir, bir modeli veritabanınıza eşleştirmek üzere el ile kodlayabilir veya modelinizde bir veritabanı oluşturmak için EF geçişlerini kullanabilirsiniz (Bu, modelin zaman içinde değiştiği şekilde veritabanını kolayca geliştirebilir).</span><span class="sxs-lookup"><span data-stu-id="74fef-147">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="74fef-148">Katalog mikro hizmeti için son yaklaşımı kullandık.</span><span class="sxs-lookup"><span data-stu-id="74fef-148">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="74fef-149">Aşağıdaki kod örneğinde, bir basit düz eski CLR nesnesi ([poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) varlık sınıfı olan CatalogItem varlık sınıfının bir örneğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-149">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="74fef-150">Ayrıca, veritabanı ile bir oturumu temsil eden bir DbContext gerekir.</span><span class="sxs-lookup"><span data-stu-id="74fef-150">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="74fef-151">Katalog mikro hizmeti için, CatalogContext sınıfı, aşağıdaki örnekte gösterildiği gibi DbContext temel sınıfından türetilir:</span><span class="sxs-lookup"><span data-stu-id="74fef-151">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="74fef-152">Ek `DbContext` uygulamalarına sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-152">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="74fef-153">Örneğin, örnek katalog. API mikro hizmetinde, veritabanına ilk kez erişmeye çalıştığında örnek verileri `DbContext` otomatik `CatalogContextSeed` olarak dolduran ikinci bir adlandırılmış ad vardır.</span><span class="sxs-lookup"><span data-stu-id="74fef-153">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="74fef-154">Bu yöntem, tanıtım verileri ve otomatikleştirilmiş test senaryoları için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="74fef-154">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="74fef-155">İçinde, nesne/veritabanı varlık `OnModelCreating` eşlemelerini ve diğer [EF genişletilebilirlik noktalarını](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)özelleştirmek için yöntemini kullanırsınız. `DbContext`</span><span class="sxs-lookup"><span data-stu-id="74fef-155">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="74fef-156">Web API denetleyicilerinden verileri sorgulama</span><span class="sxs-lookup"><span data-stu-id="74fef-156">Querying data from Web API controllers</span></span>

<span data-ttu-id="74fef-157">Varlık sınıflarınızın örnekleri, aşağıdaki örnekte gösterildiği gibi, genellikle dil ile tümleşik sorgu (LINQ) kullanılarak veritabanından alınır:</span><span class="sxs-lookup"><span data-stu-id="74fef-157">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="74fef-158">Verileri kaydetme</span><span class="sxs-lookup"><span data-stu-id="74fef-158">Saving data</span></span>

<span data-ttu-id="74fef-159">Veri, varlık sınıflarınızın örnekleri kullanılarak oluşturulur, silinir ve değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-159">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="74fef-160">Web API denetleyicilerinize aşağıdaki sabit kodlanmış örnek (Bu durumda sahte veriler) gibi bir kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-160">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="74fef-161">ASP.NET Core ve Web API denetleyicilerine bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="74fef-161">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="74fef-162">ASP.NET Core, bağımlılık ekleme (dı) kutusunu kutudan çıkar.</span><span class="sxs-lookup"><span data-stu-id="74fef-162">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="74fef-163">Tercih ettiğiniz IOC kapsayıcısını ASP.NET Core altyapısına takabilirsiniz, ancak isterseniz, üçüncü taraf bir denetim (IOC) kapsayıcısı ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="74fef-163">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="74fef-164">Bu durumda, gerekli EF DBContext veya ek depoları denetleyici Oluşturucusu aracılığıyla doğrudan ekleyebileceðiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="74fef-164">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="74fef-165">`CatalogController` Sınıfının Yukarıdaki örnekte, `CatalogController()` Oluşturucu aracılığıyla ve diğer nesneler `CatalogContext` türünde bir nesne ekleme.</span><span class="sxs-lookup"><span data-stu-id="74fef-165">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="74fef-166">Web API projesinde ayarlanmakta olan önemli bir yapılandırma, hizmetin IOC kapsayıcısına DbContext sınıfı kaydolmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74fef-166">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="74fef-167">Bu şekilde `Startup` , aşağıdaki örnekte gösterildiği gibi `ConfigureServices()` yöntemi içindeki `services.AddDbContext<DbContext>()` yöntemini çağırarak sınıfında.</span><span class="sxs-lookup"><span data-stu-id="74fef-167">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="74fef-168">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="74fef-168">Additional resources</span></span>

- <span data-ttu-id="74fef-169">**Verileri sorgulama** </span><span class="sxs-lookup"><span data-stu-id="74fef-169">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="74fef-170">**Verileri kaydetme** </span><span class="sxs-lookup"><span data-stu-id="74fef-170">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="74fef-171">Docker kapsayıcıları tarafından kullanılan DB bağlantı dizesi ve ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="74fef-171">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="74fef-172">Aşağıdaki örnekte gösterildiği gibi Settings. JSON dosyanıza ASP.NET Core ayarlarını kullanabilir ve bir ConnectionString özelliği ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74fef-172">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="74fef-173">Settings. JSON dosyası ConnectionString özelliği veya diğer herhangi bir özellik için varsayılan değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-173">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="74fef-174">Ancak, Docker kullanılırken, bu özellikler Docker-Compose. override. yıml dosyasında belirttiğiniz ortam değişkenlerinin değerleri tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="74fef-174">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="74fef-175">Docker-Compose. yıml veya Docker-Compose. override. yıml dosyalarından, bu ortam değişkenlerini, Docker 'ın sizin için aşağıdaki Docker-Compose. override. yıml dosyasında gösterildiği gibi, sizin için işletim sistemi ortam değişkenleri olarak ayarlayabilmesi için başlatabilirsiniz (bağlantı Bu örnekte dize ve diğer satırlar kaydırılır, ancak kendi dosyanıza sarılmaz.</span><span class="sxs-lookup"><span data-stu-id="74fef-175">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

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

<span data-ttu-id="74fef-176">Çözüm düzeyindeki Docker-Compose. yıml dosyaları, proje veya mikro hizmet düzeyindeki yapılandırma dosyalarından yalnızca daha esnek değildir, ancak değerleri ayarlanan değerlerle Docker-Compose dosyalarında belirtilen ortam değişkenlerini geçersiz kılarsınız, daha da güvenli hale geldi. Azure DevOps Services Docker dağıtım görevleri gibi dağıtım araçlarınız.</span><span class="sxs-lookup"><span data-stu-id="74fef-176">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="74fef-177">Son olarak, bir önceki kod örneğinde ConfigureServices yönteminde gösterildiği gibi,\["ConnectionString"\]yapılandırmasını kullanarak kodunuzda bu değeri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-177">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="74fef-178">Ancak, üretim ortamları için bağlantı dizeleri gibi gizli dizileri nasıl depolayabileceğiniz konusunda ek yöntemleri incelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-178">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="74fef-179">Uygulama gizli dizilerini yönetmenin harika bir yolu [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="74fef-179">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="74fef-180">Azure Key Vault, bulut Uygulamalarınız ve hizmetleriniz tarafından kullanılan şifreleme anahtarlarını ve gizli dizileri depolamanıza ve korumanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="74fef-180">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="74fef-181">Gizli dizi, API anahtarları, bağlantı dizeleri, parolalar vb. gibi tam denetim sağlamak istediğiniz her şey, kullanım günlüğü, zaman aşımı ayarlama, *diğer kullanıcıların arasında*erişim yönetimi içerir.</span><span class="sxs-lookup"><span data-stu-id="74fef-181">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="74fef-182">Azure Key Vault, uygulama gizli dizileri kullanımının herkes tarafından haberdar olmasına gerek kalmadan çok ayrıntılı denetim düzeyine izin verir.</span><span class="sxs-lookup"><span data-stu-id="74fef-182">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="74fef-183">Gizli dizileri geliştirme veya işlemleri kesintiye uğratmadan gelişmiş güvenlik için de döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-183">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="74fef-184">Uygulamaların, Key Vault kullanabilmesi için kuruluşun Active Directory kayıtlı olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="74fef-184">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="74fef-185">Daha fazla ayrıntı için *Key Vault kavramlar belgelerini* kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-185">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="74fef-186">ASP.NET Web API 'Lerinde sürüm oluşturma uygulama</span><span class="sxs-lookup"><span data-stu-id="74fef-186">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="74fef-187">İş gereksinimleri değiştikçe, yeni kaynak koleksiyonları eklenebilir, kaynaklar arasındaki ilişkiler değişebilir ve kaynaklardaki verilerin yapısı değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-187">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="74fef-188">Bir Web API 'sini yeni gereksinimleri işleyecek şekilde güncelleştirmek nispeten doğrudan bir işlemdir, ancak söz konusu değişikliklerin Web API 'sini kullanan istemci uygulamalarında sahip olacağı etkileri göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="74fef-188">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="74fef-189">Bir Web API 'SI tasarlayan ve uygulayan geliştirici, bu API üzerinde tam denetime sahiptir, ancak geliştirici, üçüncü taraf kuruluşların uzaktan çalıştığı istemci uygulamalar üzerinde aynı denetim derecesine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="74fef-189">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="74fef-190">Sürüm oluşturma, Web API 'sinin sunduğu özellikleri ve kaynakları belirtecek şekilde olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="74fef-190">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="74fef-191">İstemci uygulama, istekleri bir özelliğin veya kaynağın belirli bir sürümüne gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-191">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="74fef-192">Sürüm oluşturmayı uygulamak için birkaç yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="74fef-192">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="74fef-193">URI sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="74fef-193">URI versioning</span></span>

- <span data-ttu-id="74fef-194">Sorgu dizesi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="74fef-194">Query string versioning</span></span>

- <span data-ttu-id="74fef-195">Üst bilgi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="74fef-195">Header versioning</span></span>

<span data-ttu-id="74fef-196">Sorgu dizesi ve URI sürümü oluşturma en basit uygulama kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="74fef-196">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="74fef-197">Üst bilgi sürümü oluşturma iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="74fef-197">Header versioning is a good approach.</span></span> <span data-ttu-id="74fef-198">Ancak, üstbilgi sürümü oluşturma, URI sürümü oluşturma kadar açık ve kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="74fef-198">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="74fef-199">URL sürümü oluşturma en basit ve en açık olduğundan, eShopOnContainers örnek uygulaması URI sürümü oluşturmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="74fef-199">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="74fef-200">URI sürümü oluşturma ile, eShopOnContainers örnek uygulamasında olduğu gibi, Web API 'sini her değiştirdiğinizde veya kaynak şemasını değiştirdiğinizde her kaynak için URI 'ye bir sürüm numarası eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-200">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="74fef-201">Mevcut URI 'Ler, istenen sürümle eşleşen şemaya uyan kaynakları döndürerek daha önce çalışmaya devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="74fef-201">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="74fef-202">Aşağıdaki kod örneğinde gösterildiği gibi, sürüm, Web API denetleyicisindeki Route özniteliği kullanılarak ayarlanabilir, bu da sürümü URI 'de (Bu durumda v1) açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="74fef-202">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="74fef-203">Bu sürüm oluşturma mekanizması basittir ve isteği uygun uç noktaya yönlendirme sunucusuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="74fef-203">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="74fef-204">Ancak, daha gelişmiş bir sürüm oluşturma ve REST kullanırken en iyi yöntem için hiper medya kullanmanız ve [Hateoas (uygulama durumu altyapısı olarak köprü metni)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="74fef-204">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="74fef-205">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="74fef-205">Additional resources</span></span>

- <span data-ttu-id="74fef-206">**Scott Hanselman. ASP.NET Core daha fazla Web API sürümü oluşturma kolaylaştırıldı** </span><span class="sxs-lookup"><span data-stu-id="74fef-206">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="74fef-207">**Yeniden bir Web API 'sinin sürümü oluşturma** </span><span class="sxs-lookup"><span data-stu-id="74fef-207">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="74fef-208">**Roy Fielding. Sürüm oluşturma, hiper medya ve REST** </span><span class="sxs-lookup"><span data-stu-id="74fef-208">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="74fef-209">ASP.NET Core Web API 'nizden Swagger açıklaması meta verileri oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="74fef-209">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="74fef-210">[Swagger](https://swagger.io/) , daha önce yaptığınız API 'lerinizi tasarlamanıza, oluşturmanıza, belgelemenize ve kullanmanıza yardımcı olan büyük bir araç tarafından desteklenen, yaygın olarak kullanılan bir açık kaynak çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="74fef-210">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="74fef-211">API 'Ler açıklama meta verileri etki alanı için standart haline geliyor.</span><span class="sxs-lookup"><span data-stu-id="74fef-211">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="74fef-212">Veri odaklı mikro hizmetler veya daha gelişmiş etki alanı tabanlı mikro hizmetler (aşağıdaki bölümde açıklandığı gibi) herhangi bir tür mikro hizmetle Swagger açıklaması meta verilerini dahil etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-212">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="74fef-213">Swagger kalbi, bir JSON veya YAML dosyasındaki API açıklaması meta verileri olan Swagger belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="74fef-213">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="74fef-214">Bu belirtim, API 'niz için yeniden teknik sözleşme oluşturur ve kolay geliştirme, bulma ve tümleştirme için hem insanlar hem de makine tarafından okunabilen bir biçimde tüm kaynaklarını ve işlemlerini ayrıntılandıran bir şekilde ayrıntılı hale getirin.</span><span class="sxs-lookup"><span data-stu-id="74fef-214">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="74fef-215">Belirtim, Openapı belirtiminin (OAS) temelini oluşturur ve bir açık, şeffaf ve işbirliğine dayalı bir topluluk içinde geliştirilmiş arabirimlerin tanımlanma biçimini standartlaştırır.</span><span class="sxs-lookup"><span data-stu-id="74fef-215">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="74fef-216">Belirtim, bir hizmetin nasıl keşfedildiğini ve yeteneklerini nasıl anladığını belirleyen yapıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74fef-216">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="74fef-217">Bir Web Düzenleyicisi ve Spotify, Uber, bolluk ve Microsoft gibi şirketlerin Swagger belirtimlerinin örnekleri dahil daha fazla bilgi için bkz. Swagger sitesi (<https://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="74fef-217">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="74fef-218">Swagger neden kullanılmalıdır?</span><span class="sxs-lookup"><span data-stu-id="74fef-218">Why use Swagger?</span></span>

<span data-ttu-id="74fef-219">API 'leriniz için Swagger meta verileri oluşturmaya yönelik başlıca nedenler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="74fef-219">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="74fef-220">**Diğer ürünlerin API 'lerinizi otomatik olarak tüketmesi ve tümleştirmesine olanak tanır**.</span><span class="sxs-lookup"><span data-stu-id="74fef-220">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="74fef-221">Onlarca ürün ve [Ticari Araçlar](https://swagger.io/commercial-tools/) ve birçok [kitaplık ve çerçeve](https://swagger.io/open-source-integrations/) Swagger 'yi destekler.</span><span class="sxs-lookup"><span data-stu-id="74fef-221">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="74fef-222">Microsoft, Swagger tabanlı API 'Leri otomatik olarak kullanabilen ve aşağıdakiler gibi üst düzey ürün ve araçlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="74fef-222">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="74fef-223">[Oto Rest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="74fef-223">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="74fef-224">Swagger 'yi çağırmak için otomatik olarak .NET istemci sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-224">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="74fef-225">Bu araç, CLı 'dan kullanılabilir ve ayrıca GUI aracılığıyla kolayca kullanılmak üzere Visual Studio ile tümleşir.</span><span class="sxs-lookup"><span data-stu-id="74fef-225">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="74fef-226">[Microsoft Flow](https://flow.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="74fef-226">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="74fef-227">[API 'nizi otomatik olarak kullanabilir ve](https://flow.microsoft.com/blog/integrating-custom-api/) bir üst düzey Microsoft Flow iş akışında tümleştirebilirsiniz; böylece programlama becerileri gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="74fef-227">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="74fef-228">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="74fef-228">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="74fef-229">API 'nizi, [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/)Ile oluşturulmuş [PowerApps mobil uygulamalarından](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) otomatik olarak kullanabilir ve programlama becerileri gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="74fef-229">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="74fef-230">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="74fef-230">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="74fef-231">[API 'nizi otomatik olarak kullanabilir ve bir Azure App Service Logic App ile tümleştirebilirsiniz ve](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)böylece programlama becerileri gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="74fef-231">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="74fef-232">**API belgelerini otomatik olarak oluşturma yeteneği**.</span><span class="sxs-lookup"><span data-stu-id="74fef-232">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="74fef-233">Karmaşık mikro hizmet tabanlı uygulamalar gibi büyük ölçekli yeniden kullanılabilir API 'Ler oluşturduğunuzda, istek ve yanıt yüklerinizde kullanılan farklı veri modelleriyle birçok uç nokta işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="74fef-233">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="74fef-234">Doğru belgelere sahip olma ve Swagger ile yaptığınız gibi katı bir API Gezgini içeren, API 'nizin başarısı ve geliştiriciler tarafından benimseme için anahtar.</span><span class="sxs-lookup"><span data-stu-id="74fef-234">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="74fef-235">Swagger 'nin meta verileri, API 'Leri kullanmayı ve bunlara bağlanmayı anlamak için Microsoft Flow, PowerApps ve Azure Logic Apps kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="74fef-235">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="74fef-236">*Swagger-UI*temel ALıNARAK işlevsel API Yardım sayfaları biçiminde ASP.NET Core REST API uygulamaları için Swagger meta veri üretimini otomatik hale getirmek için çeşitli seçenekler vardır.</span><span class="sxs-lookup"><span data-stu-id="74fef-236">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="74fef-237">Büyük olasılıkla [eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) 'da kullanılmakta olan [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) , bu kılavuzda bazı ayrıntılarla ele alacağız, ancak aynı zamanda TypeScript ve C\# API istemcileri oluşturabilen [nswag](https://github.com/RSuter/NSwag)kullanma seçeneği C\# denetleyicileri, Swagger veya openapı belirtiminden ve hatta denetleyicileri içeren. dll dosyasını tarayarak, [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio)kullanarak.</span><span class="sxs-lookup"><span data-stu-id="74fef-237">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), that can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="74fef-238">Swashbuckle NuGet paketi ile API Swagger meta veri üretimini otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="74fef-238">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="74fef-239">Swagger meta verilerinin el ile oluşturulması (bir JSON veya YAML dosyasında) sıkıcı bir iş olabilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-239">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="74fef-240">Bununla birlikte, dinamik olarak Swagger API meta verilerini oluşturmak için [swashbuckle NuGet paketini](https://aka.ms/swashbuckledotnetcore) kullanarak ASP.NET Web API hizmetlerinin API bulmayı otomatik hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-240">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="74fef-241">Swashbuckle, ASP.NET Web API projeleriniz için Swagger meta verilerini otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74fef-241">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="74fef-242">ASP.NET Core Web API projelerini ve geleneksel ASP.NET Web API 'sini ve ASP.NET tabanlı Azure API uygulaması, Azure mobil uygulaması, Azure Service Fabric mikro hizmetleri gibi diğer tüm tercihleri destekler.</span><span class="sxs-lookup"><span data-stu-id="74fef-242">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="74fef-243">Ayrıca, başvuru uygulamasındaki gibi kapsayıcılarda dağıtılan düz Web API 'sini de destekler.</span><span class="sxs-lookup"><span data-stu-id="74fef-243">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="74fef-244">Swashbuckle, API Gezginini ve Swagger ya da [Swagger arabirimini](https://github.com/swagger-api/swagger-ui) birleştirerek API Tüketicileriniz için zengin bir keşif ve belge deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="74fef-244">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="74fef-245">Sashbuckle, Swagger meta veri Oluşturucu altyapısına ek olarak, swashbuckle yüklendikten sonra otomatik olarak sunulacak olan Swagger-UI ' nin ekli bir sürümünü de içerir.</span><span class="sxs-lookup"><span data-stu-id="74fef-245">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="74fef-246">Bu, geliştiricilerin API 'nizi kullanmasına yardımcı olmak için iyi bir keşif Kullanıcı arabirimi ile API 'nizi tamamlayoluşturabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="74fef-246">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="74fef-247">Otomatik olarak oluşturulduğundan, API 'nizi oluşturmaya odaklanmanızı sağlayan çok az miktarda kod ve bakım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="74fef-247">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="74fef-248">API Explorer için sonuç Şekil 6-8 gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="74fef-248">The result for the API Explorer looks like Figure 6-8.</span></span>

![Swashbuckle tarafından oluşturulan Swagger Kullanıcı arabirimi API 'SI belgeleri, yayımlanan tüm eylemleri içerir.](./media/image9.png)

<span data-ttu-id="74fef-250">**Şekil 6-8**.</span><span class="sxs-lookup"><span data-stu-id="74fef-250">**Figure 6-8**.</span></span> <span data-ttu-id="74fef-251">Swagger meta verileri tabanlı swashbuckle API Explorer — eShopOnContainers Catalog mikro hizmeti</span><span class="sxs-lookup"><span data-stu-id="74fef-251">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="74fef-252">API Explorer buradaki en önemli şey değildir.</span><span class="sxs-lookup"><span data-stu-id="74fef-252">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="74fef-253">Swagger meta verilerde kendisini betimleyen bir Web API 'niz olduktan sonra, API 'niz birçok platformu hedefleyen istemci proxy sınıfı kod oluşturucuları dahil olmak üzere Swagger tabanlı araçlardan sorunsuz bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74fef-253">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="74fef-254">Örneğin, belirtildiği gibi, otomatik [rest](https://github.com/Azure/AutoRest) otomatik olarak .NET istemci sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74fef-254">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="74fef-255">Ancak, API istemci kitaplıklarının, sunucu saplamalarının ve belgelerinin otomatik olarak kod oluşturmaya izin veren [Swagger-CodeGen](https://github.com/swagger-api/swagger-codegen) gibi ek araçlar da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="74fef-255">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="74fef-256">Şu anda, swashbuckle, ASP.NET Core uygulamalar için üst düzey meta-paket [swashbuckle. AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) altında beş iç NuGet paketinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="74fef-256">Currently, Swashbuckle consists of five internal NuGet packages under the high-level meta- package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="74fef-257">Bu NuGet paketlerini Web API Projenize yükledikten sonra, başlangıç sınıfında, aşağıdaki kodda olduğu gibi Swagger 'yi yapılandırmanız gerekir (Basitleştirilmiş):</span><span class="sxs-lookup"><span data-stu-id="74fef-257">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code (simplified):</span></span>

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

<span data-ttu-id="74fef-258">Bu işlem tamamlandıktan sonra, aşağıdaki gibi URL 'Leri kullanarak uygulamanızı başlatabilir ve aşağıdaki Swagger JSON ve UI uç noktalarına gidebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74fef-258">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```url
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="74fef-259">Daha önce, gibi `http://<your-root-url>/swagger`bir URL Için swashbuckle tarafından oluşturulan oluşturulan kullanıcı arabirimini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="74fef-259">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="74fef-260">Şekil 6-9 ' de, herhangi bir API yöntemini nasıl test kullanabileceğinizi da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74fef-260">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Swagger Kullanıcı arabirimi API 'SI ayrıntısı yanıtın bir örneğini gösterir ve geliştirici keşfi için harika olan gerçek API 'yi yürütmek için kullanılabilir.](./media/image10.png)

<span data-ttu-id="74fef-262">**Şekil 6-9**.</span><span class="sxs-lookup"><span data-stu-id="74fef-262">**Figure 6-9**.</span></span> <span data-ttu-id="74fef-263">Sashbuckle Kullanıcı arabirimi Katalog/öğe API yöntemini test etme</span><span class="sxs-lookup"><span data-stu-id="74fef-263">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="74fef-264">Şekil 6-10, `http://<your-root-url>/swagger/v1/swagger.json` [Postman](https://www.getpostman.com/)kullanarak istek yaptığınızda eshoponcontainers mikro hizmetinden oluşturulan Swagger JSON meta verilerini gösterir (araçların altında kullanıldığı Özellikler).</span><span class="sxs-lookup"><span data-stu-id="74fef-264">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![Swagger JSON meta verilerini gösteren örnek Postman Kullanıcı arabirimi](./media/image11.png)

<span data-ttu-id="74fef-266">**Şekil 6-10**.</span><span class="sxs-lookup"><span data-stu-id="74fef-266">**Figure 6-10**.</span></span> <span data-ttu-id="74fef-267">Swagger JSON meta verileri</span><span class="sxs-lookup"><span data-stu-id="74fef-267">Swagger JSON metadata</span></span>

<span data-ttu-id="74fef-268">Bu basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="74fef-268">It is that simple.</span></span> <span data-ttu-id="74fef-269">Otomatik olarak oluşturulduğu için, API 'nize daha fazla işlevsellik eklediğinizde Swagger meta verileri büyüyecektir.</span><span class="sxs-lookup"><span data-stu-id="74fef-269">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="74fef-270">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="74fef-270">Additional resources</span></span>

- <span data-ttu-id="74fef-271">**Swagger kullanarak ASP.NET Web API Yardım sayfaları** </span><span class="sxs-lookup"><span data-stu-id="74fef-271">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="74fef-272">**Swashbuckle ve ASP.NET Core kullanmaya başlayın** </span><span class="sxs-lookup"><span data-stu-id="74fef-272">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="74fef-273">**NSwag ve ASP.NET Core kullanmaya başlayın** </span><span class="sxs-lookup"><span data-stu-id="74fef-273">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="74fef-274">[Önceki](microservice-application-design.md)İleri
> [](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="74fef-274">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
