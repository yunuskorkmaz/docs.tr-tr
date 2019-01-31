---
title: Bir basit veri temelli CRUD mikro hizmeti oluşturma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Basit bir CRUD (Veri odaklı) oluşturulmasını anlamak bir mikro Hizmetler uygulaması bağlamında mikro hizmet.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 5d338834724c3c5733f2a8a3de1b236e270d28d2
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55480094"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="3ae8d-103">Bir basit veri temelli CRUD mikro hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ae8d-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="3ae8d-104">Bu bölümde anahatları basit bir şekilde gerçekleştirir mikro hizmet oluşturma nasıl okuma, güncelleştirme ve silme (CRUD) işlemleri veri kaynağında.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="3ae8d-105">Basit bir CRUD mikro hizmet tasarlama</span><span class="sxs-lookup"><span data-stu-id="3ae8d-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="3ae8d-106">Bir tasarım açısından bakıldığında, bu tür bir kapsayıcılı mikro hizmet çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="3ae8d-107">Belki de sorunu çözmek için basit veya belki de yalnızca bir kavram kanıtı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Basit bir CRUD mikro hizmeti bir iç tasarım örüntüsüdür.](./media/image4.png)

<span data-ttu-id="3ae8d-109">**Şekil 6-4**.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-109">**Figure 6-4**.</span></span> <span data-ttu-id="3ae8d-110">Basit CRUD mikro Hizmetleri için iç tasarım</span><span class="sxs-lookup"><span data-stu-id="3ae8d-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="3ae8d-111">Bu tür bir basit veri sürücüsü hizmet Kataloğu mikro hizmetine örnek uygulamadan örneğidir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="3ae8d-112">Bu tür bir hizmet sınıfları veri modeliyle, kendi iş mantığı ve veri erişim kodunu içeren tek bir ASP.NET Core Web API'si projede tüm işlevlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="3ae8d-113">Ayrıca, ilgili verileri (başka bir kapsayıcı geliştirme ve test amaçları için) olarak SQL Server çalıştıran bir veritabanında depolar ancak normal herhangi bir SQL Server ana Şekil 6-5'te gösterildiği gibi de olabilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Mantıksal Kataloğu mikro hizmet olabilir veya aynı Docker'da barındırma Katalog veritabanı içerir.](./media/image5.png)

<span data-ttu-id="3ae8d-116">**Şekil 6-5**.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-116">**Figure 6-5**.</span></span> <span data-ttu-id="3ae8d-117">Basit veri-driven/CRUD mikro hizmet tasarım</span><span class="sxs-lookup"><span data-stu-id="3ae8d-117">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="3ae8d-118">Bu tür bir hizmet geliştirirken, yalnızca gereksinim duyduğunuz [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) ve veri erişimi API'si veya ORM [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-118">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="3ae8d-119">Ayrıca üretebilir [Swagger](https://swagger.io/) meta verileri otomatik olarak ile [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) ne hizmetiniz sunar, açıklaması sonraki bölümde açıklandığı gibi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-119">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="3ae8d-120">Tüm bağımlılıklarınızı sahip için bir Docker kapsayıcısı içinde SQL Server geliştirme ortamları için harikadır gibi bir veritabanı sunucusunu çalıştıran ve bulutta veya şirket içi bir veritabanını sağlamak zorunda kalmadan çalıştıran unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-120">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="3ae8d-121">Tümleştirme testleri, bu kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-121">This is very convenient when running integration tests.</span></span> <span data-ttu-id="3ae8d-122">Genellikle bu yaklaşım sayesinde yüksek kullanılabilirlik elde ederim çünkü ancak üretim ortamları için bir veritabanı sunucusu çalıştıran bir kapsayıcıda, önerilmez.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-122">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="3ae8d-123">Azure'da bir üretim ortamı için Azure SQL DB veya yüksek kullanılabilirlik ve yüksek ölçeklenebilirlik sağlayabilir herhangi bir veritabanı teknolojisini kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-123">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="3ae8d-124">Örneğin, bir NoSQL yaklaşım için CosmosDB seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-124">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="3ae8d-125">Son olarak, Dockerfile ve docker-compose.yml meta veri dosyaları düzenleyerek, bu kapsayıcı görüntüsü nasıl oluşturulur yapılandırabileceğiniz — hangi temel görüntü kullanmak yanı tasarım iç ve dış adları ve TCP bağlantı noktaları gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-125">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="3ae8d-126">ASP.NET Core ile bir basit CRUD mikro hizmet uygulama</span><span class="sxs-lookup"><span data-stu-id="3ae8d-126">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="3ae8d-127">.NET Core ve Visual Studio kullanarak basit bir CRUD mikro hizmeti uygulamak için (.NET Core üzerinde bir Linux Docker konakta çalışabilecek şekilde çalışan), basit bir ASP.NET Core Web API projesi oluşturarak gösterildiği Şekil 6-6 olarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-127">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Bir ASP.NET Core Web API projesi oluşturmak için öncelikle bir ASP.NET Core Web uygulaması seçin ve ardından API türü seçin.](./media/image6.png)

<span data-ttu-id="3ae8d-129">**Şekil 6-6**.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-129">**Figure 6-6**.</span></span> <span data-ttu-id="3ae8d-130">Visual Studio'da bir ASP.NET Core Web API projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ae8d-130">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="3ae8d-131">Projeyi oluşturduktan sonra diğer Web API projesi içinde Entity Framework API veya diğer API'yi kullanarak yaptığınız gibi MVC denetleyicileri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-131">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="3ae8d-132">Yeni bir Web API projesinde, mikro hizmet üzerinde ASP.NET Core kendisini bakımından, yalnızca bağımlılık, olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-132">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="3ae8d-133">Dahili olarak, içindeki *Microsoft.AspNetCore.All* bağımlılık başvurduğu Entity Framework ve diğer birçok .NET Core Nuget paketi Şekil 6-7'de gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-133">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 6-7.</span></span>

![API projesinin tüm gerekli paket başvuruları içeren Microsoft.AspNetCore.App NuGet paketine başvuru içerir.](./media/image8.png)

<span data-ttu-id="3ae8d-136">**Şekil 6-7**.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-136">**Figure 6-7**.</span></span> <span data-ttu-id="3ae8d-137">Basit bir Web API'sini CRUD mikro Hizmet bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="3ae8d-137">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="3ae8d-138">Entity Framework Core ile uygulama CRUD Web API Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3ae8d-138">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="3ae8d-139">Entity Framework (EF) Core hafif, Genişletilebilir, ve platformlar arası sürümüne popüler Entity Framework Veri erişim teknolojisi.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-139">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="3ae8d-140">EF Core, .NET geliştiricilerinin .NET nesneleri kullanarak bir veritabanıyla çalışmasına imkan sağlayan bir nesne ilişkisel eşleyicidir (ORM) ' dir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-140">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="3ae8d-141">Veritabanını SQL Server Linux Docker görüntüsü için bir kapsayıcı içinde çalışmakta olduğundan katalog mikro hizmet EF ve SQL Server sağlayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-141">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="3ae8d-142">Ancak, veritabanı Windows Şirket içi veya Azure SQL DB gibi herhangi bir SQL Server olarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-142">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="3ae8d-143">Değiştirmeniz gereken tek şey, ASP.NET Web API mikro hizmet bağlantı dizesidir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-143">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="3ae8d-144">Veri modeli</span><span class="sxs-lookup"><span data-stu-id="3ae8d-144">The data model</span></span>

<span data-ttu-id="3ae8d-145">EF Core ile veri erişimi, bir model kullanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-145">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="3ae8d-146">Bir model (etki alanı modeli) varlık sınıfları ve böylece sorgu ve veri kaydetmek, veritabanı ile bir oturumu temsil eden türetilmiş bağlamı (DbContext) oluşur.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-146">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="3ae8d-147">Bir modeli varolan bir veritabanından üretebilir, el ile kod veritabanınızı eşleştirmek için bir model veya (veritabanı modelinizi zamanla değiştikçe geliştirilebilen kolaylaştırır) ilk kod yaklaşımı kullanarak EF geçişleri modelinizden, bir veritabanı oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-147">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="3ae8d-148">Katalog mikro hizmet için son yaklaşımı kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-148">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="3ae8d-149">Bir basit düz eski CLR nesnesi aşağıdaki kod örneğinde, Catalogıtem varlık sınıfı bir örneğini görebilirsiniz ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) varlık sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-149">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="3ae8d-150">Ayrıca veritabanı ile bir oturumu temsil eden DbContext gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-150">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="3ae8d-151">Katalog mikro hizmet için CatalogContext sınıfı aşağıdaki örnekte gösterildiği gibi DbContext temel sınıfından türetilir:</span><span class="sxs-lookup"><span data-stu-id="3ae8d-151">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="3ae8d-152">Ek olabilir `DbContext` uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-152">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="3ae8d-153">Örneğin, örnek Catalog.API mikro hizmet içinde olduğu ikinci `DbContext` adlı `CatalogContextSeed` nerede otomatik olarak doldurulur örnek verileri ilk kez çalıştığında veritabanına erişmek için.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-153">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="3ae8d-154">Bu yöntem, tanıtım verileri ve otomatikleştirilmiş test senaryoları için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-154">This method is useful for demo data and for automated testing scenarios, as well.</span></span> 

<span data-ttu-id="3ae8d-155">İçinde `DbContext`, kullandığınız `OnModelCreating` nesne/veritabanı varlık eşlemelerini ve diğer özelleştirme yöntemi [EF genişletilebilirlik noktaları](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-155">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="3ae8d-156">Web APİ'si denetleyicilerinin verileri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="3ae8d-156">Querying data from Web API controllers</span></span>

<span data-ttu-id="3ae8d-157">Aşağıdaki örnekte gösterildiği gibi varlık sınıflarının örneklerini genellikle dil tümleşik sorgu (LINQ), kullanarak veritabanından alınır:</span><span class="sxs-lookup"><span data-stu-id="3ae8d-157">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="3ae8d-158">Verileri kaydetme</span><span class="sxs-lookup"><span data-stu-id="3ae8d-158">Saving data</span></span>

<span data-ttu-id="3ae8d-159">Veri oluşturulan, silinen ve örnekleri, varlık sınıfları kullanarak veritabanında değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-159">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="3ae8d-160">Aşağıdaki örnekte olduğu gibi sabit kodlanmış (Bu örnekte sahte veriler), Web APİ'si denetleyicilerinin için kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-160">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="3ae8d-161">ASP.NET Core ve Web API denetleyicilerinin bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="3ae8d-161">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="3ae8d-162">ASP.NET Core, kullanıma hazır bağımlılık ekleme (dı) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-162">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="3ae8d-163">İsterseniz, tercih edilen IOC kapsayıcınızın ASP.NET Core altyapısına takılabilir rağmen bir üçüncü taraf denetimi tersine çevirme (IOC) kapsayıcısı ayarlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-163">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="3ae8d-164">Bu durumda, doğrudan gerekli EF DBContext veya ek depoları aracılığıyla denetleyici Oluşturucu ekleyebilir, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-164">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="3ae8d-165">Yukarıdaki örnekte `CatalogController` sınıfı, biz ekleme bir nesnenin `CatalogContext` türü diğer nesneler arasında artı `CatalogController()` Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-165">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="3ae8d-166">Hizmetin IOC kapsayıcısına DbContext sınıfı kaydı Web API projesinde ayarlamak için önemli bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-166">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="3ae8d-167">Genellikle, bu nedenle bunu `Startup` çağırarak sınıfı `services.AddDbContext<DbContext>()` yöntem içinde `ConfigureServices()` aşağıdaki örnekte gösterildiği gibi yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3ae8d-167">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="3ae8d-168">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3ae8d-168">Additional resources</span></span>

- <span data-ttu-id="3ae8d-169">**Verileri sorgulama** \\</span><span class="sxs-lookup"><span data-stu-id="3ae8d-169">**Querying Data** \\</span></span>
  [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

- <span data-ttu-id="3ae8d-170">**Verileri kaydetme** \\</span><span class="sxs-lookup"><span data-stu-id="3ae8d-170">**Saving Data** \\</span></span>
  [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="3ae8d-171">Docker kapsayıcıları tarafından kullanılan DB bağlantı dizesi ve ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="3ae8d-171">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="3ae8d-172">ASP.NET Core ayarları kullanın ve ConnectionString özelliğini aşağıdaki örnekte gösterildiği gibi settings.json dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3ae8d-172">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="3ae8d-173">ConnectionString özelliği için ya da başka bir özellik için varsayılan değerleri settings.json dosyasına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-173">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="3ae8d-174">Ancak, bu özellikleri Docker kullanarak docker-compose.override.yml dosyasında belirttiğiniz ortam değişkenlerinin değerlerini tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-174">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="3ae8d-175">Docker bunları işletim sistemi ortam değişkenleri olarak sizin için ayarlamanız, böylece docker-compose.yml ya da docker-compose.override.yml dosyalarından, bu ortam değişkenlerini aşağıdaki docker-compose.override.yml dosya (bağlantının gösterilen şekilde başlatabilirsiniz Bu örnekte, dize ve diğer satır kaydırma, ancak bunu kendi dosyasında kaydırılacak).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-175">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

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

<span data-ttu-id="3ae8d-176">Docker-compose.yml dosyaları çözüm düzeyinde yalnızca yapılandırma dosyalarını proje veya mikro hizmet düzeyinde daha esnek değildir, ancak docker-compose dosyalara kümeden değerlerle bildirilen ortam değişkenlerini geçersiz kılarsanız daha da güvenli Dağıtım Araçları, Azure DevOps Hizmetleri Docker dağıtım görevlerini ister.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-176">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span> 

<span data-ttu-id="3ae8d-177">Kodunuz aracılığıyla yapılandırmayı kullanarak bu değeri son olarak, alabilirsiniz\["ConnectionString"\]Createservicereplicalisteners() yöntemi bir önceki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-177">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="3ae8d-178">Ancak, üretim ortamları için bağlantı dizeleri gibi gizli dizileri depolamak nasıl ek yollarını keşfetmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-178">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="3ae8d-179">Uygulama gizli dizilerini yönetmek için mükemmel bir yoldur kullanarak [Azure anahtar kasası](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-179">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="3ae8d-180">Azure Key Vault depolamak ve şifreleme anahtarlarını ve gizli dizileri, bulut uygulamaları ve Hizmetleri tarafından kullanılan korunmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-180">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="3ae8d-181">API anahtarları, bağlantı dizeleri, parolalar vb. gibi katı denetimi, korumak istediğiniz her şeyi bir gizli dizidir ve sıkı denetim günlüğü, sona erme ayarı, erişimi yönetme kullanım içerir <span class="underline">diğerlerinin yanı sıra</span>.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-181">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, <span class="underline">among others</span>.</span></span>

<span data-ttu-id="3ae8d-182">Azure Key Vault, uygulama gizli anahtarları kullanım herkesin bunları biliyor olanak gerek kalmadan çok ayrıntılı denetim düzeyini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-182">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="3ae8d-183">Gizli dizileri, geliştirme veya işlemleri kesintiye uğratmadan Gelişmiş güvenlik için bile döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-183">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="3ae8d-184">Uygulamaların, anahtar Kasası'nı kullanabilmeleri kuruluşun Active Directory'de kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-184">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="3ae8d-185">Denetleyebilirsiniz <span class="underline">Key Vault kavramlarını belgeleri</span> daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-185">You can check the <span class="underline">Key Vault Concepts documentation</span> for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="3ae8d-186">ASP.NET Web API, uygulama sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ae8d-186">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="3ae8d-187">İş gereksinimleri değiştikçe yeni kaynak koleksiyonları eklenebilir, kaynaklar arasındaki ilişkiler değişebilir ve kaynaklardaki verilerin yapısını düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-187">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="3ae8d-188">Yeni gereksinimlerini karşılamak için bir Web API güncelleştiriliyor oldukça basit bir işlemdir ancak bu tür değişikliklerin Web API'sini kullanan istemci uygulamalar üzerinde olacak etkileri göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-188">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="3ae8d-189">Tasarlama ve uygulama bir Web API'sini bir geliştirici bu API üzerinde tam denetime sahip olsa da, geliştirici aynı derecede uzaktan çalışan üçüncü taraf kuruluşlar tarafından oluşturulabilir istemci uygulamalar üzerinde daha fazla denetime sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-189">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="3ae8d-190">Sürüm oluşturma, kullanıma sunduğu kaynaklar ve Özellikler belirtmek bir Web API'si sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-190">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="3ae8d-191">Bir istemci uygulaması daha sonra bir özellik ya da kaynağın belirli bir sürümünü istekleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-191">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="3ae8d-192">Sürüm oluşturma uygulamak için birçok yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="3ae8d-192">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="3ae8d-193">URI sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ae8d-193">URI versioning</span></span>

- <span data-ttu-id="3ae8d-194">Sorgu dizesi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ae8d-194">Query string versioning</span></span>

- <span data-ttu-id="3ae8d-195">Üst bilgi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ae8d-195">Header versioning</span></span>

<span data-ttu-id="3ae8d-196">Sorgu dizesi ve URI sürümü oluşturma uygulamak en basit olan.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-196">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="3ae8d-197">Üst bilgi sürümü oluşturma iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-197">Header versioning is a good approach.</span></span> <span data-ttu-id="3ae8d-198">Bununla birlikte, üst bilgi sürümü oluşturma gibi açık ve basit olarak URI sürümü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-198">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="3ae8d-199">URL sürüm oluşturma basit ve en açık olduğundan, URI sürümü oluşturma hizmetine örnek uygulamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-199">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="3ae8d-200">Hizmetine örnek uygulaması, olduğu gibi URI sürümü oluşturma ile Web API değiştirmek veya kaynak şemasını değiştirmek eklediğiniz her sefer bir sürüm numarası için her kaynak için URI.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-200">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="3ae8d-201">Mevcut bir URI'leri önce uygun kaynakları istenen sürümle eşleşen şemalarına gibi çalışmaya devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-201">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="3ae8d-202">Aşağıdaki kod örneğinde gösterildiği gibi sürüm sürüm urı'sindeki açık hale getirir denetleyicideki Web API'si rota özniteliği kullanılarak ayarlanabilir (Bu durumda v1).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-202">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="3ae8d-203">Bu sürüm oluşturma mekanizması basittir ve isteği uygun uç noktaya yönlendiren sunucuya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-203">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="3ae8d-204">Ancak, daha karmaşık bir sürüm oluşturma ve REST kullanırken en iyi yöntemi için hiper medya kullanma ve uygulamak [HATEOAS (uygulama durumu altyapısı olarak köprü metni)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-204">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3ae8d-205">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3ae8d-205">Additional resources</span></span>

- <span data-ttu-id="3ae8d-206">**Scott Hanselman. ASP.NET Core RESTful Web API'si sürümü oluşturma artık daha kolay** \\</span><span class="sxs-lookup"><span data-stu-id="3ae8d-206">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** \\</span></span>
  [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

- <span data-ttu-id="3ae8d-207">**RESTful web API'si sürümü oluşturma** \\</span><span class="sxs-lookup"><span data-stu-id="3ae8d-207">**Versioning a RESTful web API** \\</span></span>
  [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

- <span data-ttu-id="3ae8d-208">**Roy Fielding. Sürüm oluşturma, iletilir ve REST** \\</span><span class="sxs-lookup"><span data-stu-id="3ae8d-208">**Roy Fielding. Versioning, Hypermedia, and REST** \\</span></span>
  [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="3ae8d-209">Swagger tanım meta verileri, ASP.NET Core Web API'si oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ae8d-209">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="3ae8d-210">[Swagger](https://swagger.io/) olduğu bir yaygın olarak kullanılan açık kaynak çerçeve tasarım, derleme, belge yardımcı olan oluşan geniş ekosistem araçları tarafından desteklenen ve RESTful API'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-210">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="3ae8d-211">Bu API'leri açıklama meta verileri etki alanı için standart hale gelmektedir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-211">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="3ae8d-212">Swagger tanım meta verileri ile mikro hizmet, veri odaklı bir mikro hizmetler veya daha fazla etki alanı odaklı bir mikro hizmetler (aşağıdaki bölümde açıklandığı gibi) Gelişmiş herhangi bir türden içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-212">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="3ae8d-213">Swagger API tanımı meta veriler bir JSON veya YAML dosyasına Swagger belirtimi kalbidir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-213">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="3ae8d-214">Tüm kaynakları ve işlemleri hem İnsan ve machine readable biçimde kolay geliştirme, Keşif ve tümleştirme için gerçekleşen API'niz için RESTful sözleşme belirtimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-214">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="3ae8d-215">Belirtimi, Openapı belirtimi'nın (OAS) temelidir ve RESTful arabirimlerinden tanımlanma biçimini standart hale getirmek için bir açık, şeffaf ve işbirliğine dayalı topluluğuna geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-215">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="3ae8d-216">Belirtimi, bir hizmetin nasıl bulunabileceğini ve özelliklerini nasıl anladım yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-216">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="3ae8d-217">Daha fazla bilgi için bir web Düzenleyicisi ve Swagger belirtimlerinden Spotify, Uber, Slack ve Microsoft gibi şirketler örnekleri dahil olmak üzere Swagger sitesine bakın ([https://swagger.io](https://swagger.io)).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-217">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site ([https://swagger.io](https://swagger.io)).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="3ae8d-218">Swagger neden kullanmalısınız?</span><span class="sxs-lookup"><span data-stu-id="3ae8d-218">Why use Swagger?</span></span>

<span data-ttu-id="3ae8d-219">Apı'leriniz için Swagger meta verileri oluşturmak için temel neden aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-219">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="3ae8d-220">**Otomatik olarak kullanmak ve Apı'lerinizi tümleştirmek diğer ürünlere yönelik özelliği**.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-220">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="3ae8d-221">Ürünleri onlarca ve [ticari Araçları](https://swagger.io/commercial-tools/) ve birçok [kitaplıklar ve çerçeveler](https://swagger.io/open-source-integrations/) Swagger'ı destekler.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-221">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="3ae8d-222">Microsoft üst düzey ürün ve otomatik olarak aşağıdaki gibi Swagger tabanlı API'ler tüketebileceği araç vardır:</span><span class="sxs-lookup"><span data-stu-id="3ae8d-222">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="3ae8d-223">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-223">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="3ae8d-224">Swagger'ı çağırmak için .NET istemci sınıfları otomatik olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-224">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="3ae8d-225">Bu aracı CLI üzerinden kullanılabilir ve GUI aracılığıyla kolay kullanım için de Visual Studio ile tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-225">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="3ae8d-226">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-226">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="3ae8d-227">Otomatik olarak [kullanın ve API'nizi tümleştirme](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) üst düzey bir Microsoft Flow iş akışınıza olmadan programlama becerileri gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-227">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="3ae8d-228">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-228">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="3ae8d-229">Otomatik olarak, API'SİNDEN tüketebileceği [PowerApps mobil uygulamalar](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) ile oluşturulmuş [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), gerekli herhangi bir programlama becerilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-229">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="3ae8d-230">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-230">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="3ae8d-231">Otomatik olarak [kullanın ve API'nizi Azure App Service mantıksal uygulamalarla tümleştirme](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), gerekli herhangi bir programlama becerilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-231">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="3ae8d-232">**API belgelerini otomatik olarak oluşturma yeteneği**.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-232">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="3ae8d-233">Karmaşık mikro hizmet tabanlı uygulamalar gibi büyük ölçekli RESTful API'leri oluşturduğunuzda, istek ve yanıt yükleri kullanılan farklı veri modellerine sahip çok sayıda uç noktalar ele almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-233">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="3ae8d-234">API'NİZİN ve geliştiriciler tarafından benimseme başarısı için uygun belgelere sahip olunması ve Swagger ile aldıkça, sağlam bir API Gezgini sahip anahtardır.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-234">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="3ae8d-235">Microsoft Flow, PowerApps ve Logic Apps Azure API'leri ve bunlara nasıl kullanılacağını anlamak için kullandıklarınız swagger'ın meta verilerdir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-235">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="3ae8d-236">Temel işlevsel API Yardım sayfaları biçiminde ASP.NET Core REST API uygulamaları için Swagger meta verileri oluşturmayı otomatikleştirmek için birkaç seçenek vardır <span class="underline">swagger kullanıcı arabirimi</span>.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-236">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on <span class="underline">swagger-ui</span>.</span></span>

<span data-ttu-id="3ae8d-237">En iyi bilinen olabilir [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) şu anda kullanılan [eShopOnCntainers](https://github.com/dotnet-architecture/eShopOnContainers) ve bu kılavuzdaki bazı ayrıntılı şu konulara değineceğiz ancak kullanmak için bir seçenek de mevcuttur [NSwag](https://github.com/RSuter/NSwag), Typescript ve C oluşturabileceği\# C yanı sıra API istemciler\# denetleyicileri, Swagger veya Openapı belirtiminden ve kullanarak denetleyicileri içeren .dll tarayarak bile [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-237">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnCntainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), that can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="3ae8d-238">Swagger API meta verileri oluşturma Swashbuckle NuGet paketini ile otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="3ae8d-238">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="3ae8d-239">Swagger meta verilerde el ile (bir JSON veya YAML dosyası) oluşturmak zahmetli bir iş olabilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-239">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="3ae8d-240">Ancak, ASP.NET Web API Hizmetleri API bulma kullanarak otomatikleştirebileceğiniz [Swashbuckle NuGet paketini](https://aka.ms/swashbuckledotnetcore) dinamik olarak Swagger API'si meta verileri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-240">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="3ae8d-241">Swashbuckle, ASP.NET Web API projeleriniz için Swagger meta verileri otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-241">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="3ae8d-242">Bu, ASP.NET Core Web API projelerini ve geleneksel ASP.NET Web API ve Azure API uygulaması, Azure mobil uygulaması, ASP Azure Service Fabric mikro hizmetler gibi diğer tüm flavor destekler.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-242">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="3ae8d-243">Ayrıca, düz Web API'si için başvuru uygulaması olarak kapsayıcılarında, dağıtılan destekler.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-243">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="3ae8d-244">Swashbuckle birleştirir API Gezgini ve Swagger veya [swagger kullanıcı arabirimi](https://github.com/swagger-api/swagger-ui) zengin bulma ve belgeler için API tüketicilerinize deneyimi sağlamak.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-244">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="3ae8d-245">Kendi Swagger meta verileri Oluşturucu altyapısına ek olarak, Swashbuckle swagger-Swashbuckle yüklendikten sonra otomatik olarak hizmet verecek yukarı kullanıcı arabirimi, katıştırılmış bir sürümünü de içerir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-245">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="3ae8d-246">Bu, iyi bir bulma geliştiricilerin API'nizi kullanmasına yardımcı olmak için kullanıcı Arabirimi ile API'nizi tamamlayabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-246">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="3ae8d-247">Bu otomatik olarak, API'nizi geliştirmeye odaklanabilirsiniz oluşturulmuş olduğu için çok az miktarda kodu ve bakım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-247">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="3ae8d-248">API Gezgini için sonucu Şekil 6-8 gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-248">The result for the API Explorer looks like Figure 6-8.</span></span>

![Swashbuckle'ı üretilen Swagger kullanıcı Arabirimi API belgelerini içeren tüm eylemleri yayımladı.](./media/image9.png)

<span data-ttu-id="3ae8d-250">**Şekil 6-8**.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-250">**Figure 6-8**.</span></span> <span data-ttu-id="3ae8d-251">Swashbuckle API Gezgini Swagger meta verileri temel alarak — hizmetine mikro hizmet Kataloğu</span><span class="sxs-lookup"><span data-stu-id="3ae8d-251">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="3ae8d-252">API Gezgini burada en önemli şey değil.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-252">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="3ae8d-253">Kendisini Swagger meta verilerde açıklayan bir Web API'si aldıktan sonra birçok platformda hedefleyebilen istemci proxy sınıfı kod oluşturucuları dahil olmak üzere Swagger tabanlı araçlardan, API'nizi sorunsuz bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-253">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="3ae8d-254">Örneğin, bahsedildiği gibi [AutoRest](https://github.com/Azure/AutoRest) otomatik olarak .NET istemci sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-254">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="3ae8d-255">Ancak gibi ek araçlar [swagger codegen](https://github.com/swagger-api/swagger-codegen) kod oluşturma API'si istemci kitaplıkları, sunucu saptamalar ve belgeleri otomatik olarak izin olan de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-255">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="3ae8d-256">Üst düzey meta-package altında beş iç NuGet paketleri şu anda, Swashbuckle oluşan [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) ASP.NET Core uygulamaları için.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-256">Currently, Swashbuckle consists of five internal NuGet packages under the high-level meta- package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="3ae8d-257">Bu NuGet paketleri, Web API projesinde yükledikten sonra aşağıdaki kodu (Basitleştirilmiş) olduğu gibi bir başlangıç sınıfı Swagger yapılandırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="3ae8d-257">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code (simplified):</span></span>

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

<span data-ttu-id="3ae8d-258">Bunu yaptıktan sonra uygulamanızı başlatın ve bu gibi URL'leri kullanarak aşağıdaki Swagger JSON ve UI uç göz atın:</span><span class="sxs-lookup"><span data-stu-id="3ae8d-258">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```url
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

<span data-ttu-id="3ae8d-259">Daha önce oluşturulan kullanıcı arabirimini http:// gibi bir URL için Swashbuckle tarafından oluşturulan gördüğünüz\<kök URL'si your \> /swagger.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-259">You previously saw the generated UI created by Swashbuckle for a URL like http://\<your-root-url\>/swagger.</span></span> <span data-ttu-id="3ae8d-260">Şekil 6-9'da herhangi bir API yöntemini nasıl test görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-260">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Swagger kullanıcı Arabirimi API ayrıntılı bir yanıt örneği gösterilmektedir ve geliştirici bulma için harika olan gerçek API yürütmek için kullanılabilir.](./media/image10.png)

<span data-ttu-id="3ae8d-262">**Şekil 6-9**.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-262">**Figure 6-9**.</span></span> <span data-ttu-id="3ae8d-263">Swashbuckle UI testi katalog/öğeleri API yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ae8d-263">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="3ae8d-264">Şekil 6-10 hizmetine mikro hizmet oluşturulan Swagger JSON meta verileri gösterir (olan araçlar altında kullanın) olduğunda, isteği \<kök URL'si your\>/swagger/v1/swagger.json kullanarak [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="3ae8d-264">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request \<your-root-url\>/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![Swagger JSON meta verileri gösteren örnek Postman UI](./media/image11.png)

<span data-ttu-id="3ae8d-266">**Şekil 6-10**.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-266">**Figure 6-10**.</span></span> <span data-ttu-id="3ae8d-267">Swagger JSON meta verileri</span><span class="sxs-lookup"><span data-stu-id="3ae8d-267">Swagger JSON metadata</span></span>

<span data-ttu-id="3ae8d-268">Bu basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-268">It is that simple.</span></span> <span data-ttu-id="3ae8d-269">Ve daha fazla işlevsellik API'nize eklediğinizde otomatik olarak oluşturulduğundan, Swagger meta verileri büyüyecektir.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-269">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3ae8d-270">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3ae8d-270">Additional resources</span></span>

- <span data-ttu-id="3ae8d-271">**Swagger kullanan ASP.NET Web API Yardım sayfaları** \\</span><span class="sxs-lookup"><span data-stu-id="3ae8d-271">**ASP.NET Web API Help Pages using Swagger** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="3ae8d-272">**Swashbuckle'ı ve ASP.NET Core ile çalışmaya başlama** \\</span><span class="sxs-lookup"><span data-stu-id="3ae8d-272">**Get started with Swashbuckle and ASP.NET Core** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle?tabs=visual-studio*](https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle?tabs=visual-studio)

- <span data-ttu-id="3ae8d-273">**NSwag ve ASP.NET Core ile çalışmaya başlama** \\</span><span class="sxs-lookup"><span data-stu-id="3ae8d-273">**Get started with NSwag and ASP.NET Core** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag?tabs=visual-studio*](https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag?tabs=visual-studio)

>[!div class="step-by-step"]
><span data-ttu-id="3ae8d-274">[Önceki](microservice-application-design.md)
>[İleri](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="3ae8d-274">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
