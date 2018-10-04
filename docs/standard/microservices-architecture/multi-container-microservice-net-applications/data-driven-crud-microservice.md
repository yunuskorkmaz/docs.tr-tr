---
title: Bir basit veri temelli CRUD mikro hizmeti oluşturma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Bir basit veri temelli CRUD mikro hizmeti oluşturma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: b443f1b066d3c8ef0e798206510616aace32b377
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582742"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="01caf-103">Bir basit veri temelli CRUD mikro hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="01caf-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="01caf-104">Bu bölümde anahatları basit bir şekilde gerçekleştirir mikro hizmet oluşturma nasıl okuma, güncelleştirme ve silme (CRUD) işlemleri veri kaynağında.</span><span class="sxs-lookup"><span data-stu-id="01caf-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="01caf-105">Basit bir CRUD mikro hizmet tasarlama</span><span class="sxs-lookup"><span data-stu-id="01caf-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="01caf-106">Bir tasarım açısından bakıldığında, bu tür bir kapsayıcılı mikro hizmet çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="01caf-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="01caf-107">Belki de sorunu çözmek için basit veya belki de yalnızca bir kavram kanıtı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="01caf-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="01caf-108">**Şekil 8-4**.</span><span class="sxs-lookup"><span data-stu-id="01caf-108">**Figure 8-4**.</span></span> <span data-ttu-id="01caf-109">Basit CRUD mikro Hizmetleri için iç tasarım</span><span class="sxs-lookup"><span data-stu-id="01caf-109">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="01caf-110">Bu tür bir basit veri sürücüsü hizmet Kataloğu mikro hizmetine örnek uygulamadan örneğidir.</span><span class="sxs-lookup"><span data-stu-id="01caf-110">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="01caf-111">Bu tür bir hizmet sınıfları veri modeliyle, kendi iş mantığı ve veri erişim kodunu içeren tek bir ASP.NET Core Web API'si projede tüm işlevlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="01caf-111">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="01caf-112">Ayrıca, ilgili verileri (başka bir kapsayıcı geliştirme ve test amaçları için) olarak SQL Server çalıştıran bir veritabanında depolar ancak normal herhangi bir SQL Server ana Şekil 8-5'te gösterildiği gibi de olabilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-112">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="01caf-113">**Şekil 8-5**.</span><span class="sxs-lookup"><span data-stu-id="01caf-113">**Figure 8-5**.</span></span> <span data-ttu-id="01caf-114">Basit veri-driven/CRUD mikro hizmet tasarım</span><span class="sxs-lookup"><span data-stu-id="01caf-114">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="01caf-115">Bu tür bir hizmet geliştirirken, yalnızca gereksinim duyduğunuz [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) ve veri erişimi API'si veya ORM [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="01caf-115">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="01caf-116">Ayrıca üretebilir [Swagger](https://swagger.io/) meta verileri otomatik olarak ile [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) ne hizmetiniz sunar, açıklaması sonraki bölümde açıklandığı gibi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="01caf-116">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="01caf-117">Tüm bağımlılıklarınızı sahip için bir Docker kapsayıcısı içinde SQL Server geliştirme ortamları için harikadır gibi bir veritabanı sunucusunu çalıştıran ve bulutta veya şirket içi bir veritabanını sağlamak zorunda kalmadan çalıştıran unutmayın.</span><span class="sxs-lookup"><span data-stu-id="01caf-117">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="01caf-118">Tümleştirme testleri, bu kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="01caf-118">This is very convenient when running integration tests.</span></span> <span data-ttu-id="01caf-119">Genellikle bu yaklaşım sayesinde yüksek kullanılabilirlik elde ederim çünkü ancak üretim ortamları için bir veritabanı sunucusu çalıştıran bir kapsayıcıda, önerilmez.</span><span class="sxs-lookup"><span data-stu-id="01caf-119">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="01caf-120">Azure'da bir üretim ortamı için Azure SQL DB veya yüksek kullanılabilirlik ve yüksek ölçeklenebilirlik sağlayabilir herhangi bir veritabanı teknolojisini kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-120">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="01caf-121">Örneğin, bir NoSQL yaklaşım için DocumentDB seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01caf-121">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="01caf-122">Son olarak, Dockerfile ve docker-compose.yml meta veri dosyaları düzenleyerek, bu kapsayıcı görüntüsü nasıl oluşturulur yapılandırabileceğiniz — hangi temel görüntü kullanmak yanı tasarım iç ve dış adları ve TCP bağlantı noktaları gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="01caf-122">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="01caf-123">ASP.NET Core ile bir basit CRUD mikro hizmet uygulama</span><span class="sxs-lookup"><span data-stu-id="01caf-123">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="01caf-124">.NET Core ve Visual Studio kullanarak basit bir CRUD mikro hizmeti uygulamak için (.NET Core üzerinde bir Linux Docker konakta çalışabilecek şekilde çalışan), basit bir ASP.NET Core Web API projesi oluşturarak gösterildiği Şekil 8-6 olarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="01caf-124">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="01caf-125">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="01caf-125">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="01caf-126">**Şekil 8-6**.</span><span class="sxs-lookup"><span data-stu-id="01caf-126">**Figure 8-6**.</span></span> <span data-ttu-id="01caf-127">Visual Studio'da bir ASP.NET Core Web API projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="01caf-127">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="01caf-128">Projeyi oluşturduktan sonra diğer Web API projesi içinde Entity Framework API veya diğer API'yi kullanarak yaptığınız gibi MVC denetleyicileri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01caf-128">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="01caf-129">Yeni bir Web API projesinde, mikro hizmet üzerinde ASP.NET Core kendisini bakımından, yalnızca bağımlılık, olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01caf-129">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="01caf-130">Dahili olarak, içinde `Microsoft.AspNetCore.All` bağımlılık başvurduğu Entity Framework ve diğer birçok .NET Core Nuget paketi, Şekil 8-7'de gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="01caf-130">Internally, within the `Microsoft.AspNetCore.All` dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="01caf-131">**Şekil 8-7**.</span><span class="sxs-lookup"><span data-stu-id="01caf-131">**Figure 8-7**.</span></span> <span data-ttu-id="01caf-132">Basit bir Web API'sini CRUD mikro Hizmet bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="01caf-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="01caf-133">Entity Framework Core ile uygulama CRUD Web API Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="01caf-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="01caf-134">Entity Framework (EF) Core hafif, Genişletilebilir, ve platformlar arası sürümüne popüler Entity Framework Veri erişim teknolojisi.</span><span class="sxs-lookup"><span data-stu-id="01caf-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="01caf-135">EF Core, .NET geliştiricilerinin .NET nesneleri kullanarak bir veritabanıyla çalışmasına imkan sağlayan bir nesne ilişkisel eşleyicidir (ORM) ' dir.</span><span class="sxs-lookup"><span data-stu-id="01caf-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="01caf-136">Veritabanını SQL Server Linux Docker görüntüsü için bir kapsayıcı içinde çalışmakta olduğundan katalog mikro hizmet EF ve SQL Server sağlayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="01caf-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="01caf-137">Ancak, veritabanı Windows Şirket içi veya Azure SQL DB gibi herhangi bir SQL Server olarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="01caf-138">Değiştirmeniz gereken tek şey, ASP.NET Web API mikro hizmet bağlantı dizesidir.</span><span class="sxs-lookup"><span data-stu-id="01caf-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>


#### <a name="the-data-model"></a><span data-ttu-id="01caf-139">Veri modeli</span><span class="sxs-lookup"><span data-stu-id="01caf-139">The data model</span></span>

<span data-ttu-id="01caf-140">EF Core ile veri erişimi, bir model kullanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-140">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="01caf-141">Bir modeli varlık sınıfları ve böylece sorgu ve veri kaydetmek, veritabanı ile bir oturumu temsil eden türetilmiş bir bağlam oluşur.</span><span class="sxs-lookup"><span data-stu-id="01caf-141">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="01caf-142">Varolan bir veritabanından bir model oluşturmak, el ile kod veritabanınızı eşleştirmek için bir model veya EF geçişleri modelinizden bir veritabanı oluşturmak (ve modelinizi zamanla değiştikçe evrim geçiren için) kullanın.</span><span class="sxs-lookup"><span data-stu-id="01caf-142">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="01caf-143">Katalog mikro hizmet için son yaklaşımı kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="01caf-143">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="01caf-144">Bir basit düz eski CLR nesnesi aşağıdaki kod örneğinde, Catalogıtem varlık sınıfı bir örneğini görebilirsiniz ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) varlık sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01caf-144">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="01caf-145">Ayrıca veritabanı ile bir oturumu temsil eden DbContext gerekir.</span><span class="sxs-lookup"><span data-stu-id="01caf-145">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="01caf-146">Katalog mikro hizmet için CatalogContext sınıfı aşağıdaki örnekte gösterildiği gibi DbContext temel sınıfından türetilir:</span><span class="sxs-lookup"><span data-stu-id="01caf-146">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="01caf-147">Ek olabilir `DbContext` uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="01caf-147">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="01caf-148">Örneğin, örnek Catalog.API mikro hizmet içinde olduğu ikinci `DbContext` adlı `CatalogContextSeed` nerede otomatik olarak doldurulur örnek verileri ilk kez çalıştığında veritabanına erişmek için.</span><span class="sxs-lookup"><span data-stu-id="01caf-148">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="01caf-149">Bu yöntem, tanıtım verileri ve otomatikleştirilmiş test senaryoları için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="01caf-149">This method is useful for demo data and for automated testing scenarios, as well.</span></span> <span data-ttu-id="01caf-150">İçinde `DbContext`, kullandığınız `OnModelCreating` nesne/veritabanı varlık eşlemelerini ile ve diğer özelleştirme yöntemi [EF genişletilebilirlik noktaları](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="01caf-150">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings with and other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="01caf-151">Web APİ'si denetleyicilerinin verileri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="01caf-151">Querying data from Web API controllers</span></span>

<span data-ttu-id="01caf-152">Aşağıdaki örnekte gösterildiği gibi varlık sınıflarının örneklerini genellikle dil tümleşik sorgu (LINQ), kullanarak veritabanından alınır:</span><span class="sxs-lookup"><span data-stu-id="01caf-152">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="01caf-153">Verileri kaydetme</span><span class="sxs-lookup"><span data-stu-id="01caf-153">Saving data</span></span>

<span data-ttu-id="01caf-154">Veri oluşturulan, silinen ve örnekleri, varlık sınıfları kullanarak veritabanında değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="01caf-154">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="01caf-155">Aşağıdaki örnekte olduğu gibi sabit kodlanmış (Bu örnekte sahte veriler), Web APİ'si denetleyicilerinin için kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01caf-155">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="01caf-156">ASP.NET Core ve Web API denetleyicilerinin bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="01caf-156">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="01caf-157">ASP.NET Core, kullanıma hazır bağımlılık ekleme (dı) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01caf-157">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="01caf-158">İsterseniz, tercih edilen IOC kapsayıcınızın ASP.NET Core altyapısına takılabilir rağmen bir üçüncü taraf denetimi tersine çevirme (IOC) kapsayıcısı ayarlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="01caf-158">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="01caf-159">Bu durumda, doğrudan gerekli EF DBContext veya ek depoları aracılığıyla denetleyici Oluşturucu ekleyebilir, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="01caf-159">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="01caf-160">Yukarıdaki örnekte `CatalogController` sınıfı, biz ekleme bir nesnenin `CatalogContext` türü diğer nesneler arasında artı `CatalogController()` Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="01caf-160">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="01caf-161">Hizmetin IOC kapsayıcısına DbContext sınıfı kaydı Web API projesinde ayarlamak için önemli bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="01caf-161">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="01caf-162">Genellikle, bu nedenle bunu `Startup` çağırarak sınıfı `services.AddDbContext<DbContext>()` yöntem içinde `ConfigureServices()` aşağıdaki örnekte gösterildiği gibi yöntemi:</span><span class="sxs-lookup"><span data-stu-id="01caf-162">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="01caf-163">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="01caf-163">Additional resources</span></span>

-   <span data-ttu-id="01caf-164">**Verileri sorgulama**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="01caf-164">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="01caf-165">**Verileri kaydetme**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="01caf-165">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="01caf-166">Docker kapsayıcıları tarafından kullanılan DB bağlantı dizesi ve ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="01caf-166">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="01caf-167">ASP.NET Core ayarları kullanın ve ConnectionString özelliğini aşağıdaki örnekte gösterildiği gibi settings.json dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="01caf-167">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="01caf-168">ConnectionString özelliği için ya da başka bir özellik için varsayılan değerleri settings.json dosyasına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-168">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="01caf-169">Ancak, bu özellikleri Docker kullanarak docker-compose.override.yml dosyasında belirttiğiniz ortam değişkenlerinin değerlerini tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="01caf-169">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="01caf-170">Docker bunları işletim sistemi ortam değişkenleri olarak sizin için ayarlamanız, böylece docker-compose.yml ya da docker-compose.override.yml dosyalarından, bu ortam değişkenlerini aşağıdaki docker-compose.override.yml dosya (bağlantının gösterilen şekilde başlatabilirsiniz Bu örnekte, dize ve diğer satır kaydırma, ancak bunu kendi kod dosyasında kaydırılacak).</span><span class="sxs-lookup"><span data-stu-id="01caf-170">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own code file).</span></span>

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

<span data-ttu-id="01caf-171">Docker-compose.yml dosyaları çözüm düzeyinde yalnızca yapılandırma dosyalarını proje veya mikro hizmet düzeyinde daha esnek değildir, ancak docker-compose dosyalara kümeden değerlerle bildirilen ortam değişkenlerini geçersiz kılarsanız daha da güvenli Dağıtım Araçları, Azure DevOps Hizmetleri Docker dağıtım görevlerini ister.</span><span class="sxs-lookup"><span data-stu-id="01caf-171">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span> 

<span data-ttu-id="01caf-172">Kodunuz aracılığıyla yapılandırmayı kullanarak bu değeri son olarak, alabilirsiniz\["ConnectionString"\]Createservicereplicalisteners() yöntemi bir önceki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="01caf-172">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="01caf-173">Ancak, üretim ortamları için bağlantı dizeleri gibi gizli dizileri depolamak nasıl ek yollarını keşfetmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01caf-173">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="01caf-174">Genellikle, yönetilecek an kullandığınız düzenleyici tarafından ile yapabildiğiniz gibi [Docker Swarm gizli dizileri Yönetim](https://docs.docker.com/engine/swarm/secrets/).</span><span class="sxs-lookup"><span data-stu-id="01caf-174">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="01caf-175">ASP.NET Web API, uygulama sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="01caf-175">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="01caf-176">İş gereksinimleri değiştikçe yeni kaynak koleksiyonları eklenebilir, kaynaklar arasındaki ilişkiler değişebilir ve kaynaklardaki verilerin yapısını düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-176">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="01caf-177">Yeni gereksinimlerini karşılamak için bir Web API güncelleştiriliyor oldukça basit bir işlemdir ancak bu tür değişikliklerin Web API'sini kullanan istemci uygulamalar üzerinde olacak etkileri göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01caf-177">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="01caf-178">Tasarlama ve uygulama bir Web API'sini bir geliştirici bu API üzerinde tam denetime sahip olsa da, geliştirici aynı derecede uzaktan çalışan üçüncü taraf kuruluşlar tarafından oluşturulabilir istemci uygulamalar üzerinde daha fazla denetime sahip değil.</span><span class="sxs-lookup"><span data-stu-id="01caf-178">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="01caf-179">Sürüm oluşturma, kullanıma sunduğu kaynaklar ve Özellikler belirtmek bir Web API'si sağlar.</span><span class="sxs-lookup"><span data-stu-id="01caf-179">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="01caf-180">Bir istemci uygulaması daha sonra bir özellik ya da kaynağın belirli bir sürümünü istekleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01caf-180">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="01caf-181">Sürüm oluşturma uygulamak için birçok yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="01caf-181">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="01caf-182">URI sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="01caf-182">URI versioning</span></span>

-   <span data-ttu-id="01caf-183">Sorgu dizesi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="01caf-183">Query string versioning</span></span>

-   <span data-ttu-id="01caf-184">Üst bilgi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="01caf-184">Header versioning</span></span>

<span data-ttu-id="01caf-185">Sorgu dizesi ve URI sürümü oluşturma uygulamak en basit olan.</span><span class="sxs-lookup"><span data-stu-id="01caf-185">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="01caf-186">Üst bilgi sürümü oluşturma iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="01caf-186">Header versioning is a good approach.</span></span> <span data-ttu-id="01caf-187">Bununla birlikte, üst bilgi sürümü oluşturma gibi açık ve basit olarak URI sürümü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="01caf-187">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="01caf-188">URL sürüm oluşturma basit ve en açık olduğundan, URI sürümü oluşturma hizmetine örnek uygulamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="01caf-188">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="01caf-189">Hizmetine örnek uygulaması, olduğu gibi URI sürümü oluşturma ile Web API değiştirmek veya kaynak şemasını değiştirmek eklediğiniz her sefer bir sürüm numarası için her kaynak için URI.</span><span class="sxs-lookup"><span data-stu-id="01caf-189">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="01caf-190">Mevcut bir URI'leri önce uygun kaynakları istenen sürümle eşleşen şemalarına gibi çalışmaya devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="01caf-190">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="01caf-191">Aşağıdaki kod örneğinde gösterildiği gibi sürüm sürüm urı'sindeki açık hale getirir Web API'sindeki rota özniteliği kullanılarak ayarlanabilir (Bu durumda v1).</span><span class="sxs-lookup"><span data-stu-id="01caf-191">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="01caf-192">Bu sürüm oluşturma mekanizması basittir ve isteği uygun uç noktaya yönlendiren sunucuya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="01caf-192">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="01caf-193">Ancak, daha karmaşık bir sürüm oluşturma ve REST kullanırken en iyi yöntemi için hiper medya kullanma ve uygulamak [HATEOAS (uygulama durumu altyapısı olarak köprü metni)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="01caf-193">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="01caf-194">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="01caf-194">Additional resources</span></span>

-   <span data-ttu-id="01caf-195">**Scott Hanselman. ASP.NET Core RESTful Web API'si sürümü oluşturma artık daha kolay**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="01caf-195">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="01caf-196">**RESTful web API'si sürümü oluşturma**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span><span class="sxs-lookup"><span data-stu-id="01caf-196">**Versioning a RESTful web API**
[*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span></span>

-   <span data-ttu-id="01caf-197">**Roy Fielding. Sürüm oluşturma, iletilir ve REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="01caf-197">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="01caf-198">Swagger tanım meta verileri, ASP.NET Core Web API'si oluşturma</span><span class="sxs-lookup"><span data-stu-id="01caf-198">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="01caf-199">[Swagger](https://swagger.io/) olduğu bir yaygın olarak kullanılan açık kaynak çerçeve tasarım, derleme, belge yardımcı olan oluşan geniş ekosistem araçları tarafından desteklenen ve RESTful API'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="01caf-199">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="01caf-200">Bu API'leri açıklama meta verileri etki alanı için standart hale gelmektedir.</span><span class="sxs-lookup"><span data-stu-id="01caf-200">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="01caf-201">Swagger tanım meta verileri ile mikro hizmet, veri odaklı bir mikro hizmetler veya daha fazla etki alanı odaklı bir mikro hizmetler (aşağıdaki bölümde açıklandığı gibi) Gelişmiş herhangi bir türden içermelidir.</span><span class="sxs-lookup"><span data-stu-id="01caf-201">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="01caf-202">Swagger API tanımı meta veriler bir JSON veya YAML dosyasına Swagger belirtimi kalbidir.</span><span class="sxs-lookup"><span data-stu-id="01caf-202">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="01caf-203">Tüm kaynakları ve işlemleri hem İnsan ve machine readable biçimde kolay geliştirme, Keşif ve tümleştirme için gerçekleşen API'niz için RESTful sözleşme belirtimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01caf-203">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="01caf-204">Belirtimi, Openapı belirtimi'nın (OAS) temelidir ve RESTful arabirimlerinden tanımlanma biçimini standart hale getirmek için bir açık, şeffaf ve işbirliğine dayalı topluluğuna geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01caf-204">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="01caf-205">Belirtimi, bir hizmetin nasıl bulunabileceğini ve özelliklerini nasıl anladım yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01caf-205">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="01caf-206">Daha fazla bilgi için bir web Düzenleyicisi ve Swagger belirtimlerinden Spotify, Uber, Slack ve Microsoft gibi şirketler örnekleri dahil olmak üzere Swagger sitesine bakın (<https://swagger.io/>).</span><span class="sxs-lookup"><span data-stu-id="01caf-206">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io/>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="01caf-207">Swagger neden kullanmalısınız?</span><span class="sxs-lookup"><span data-stu-id="01caf-207">Why use Swagger?</span></span>

<span data-ttu-id="01caf-208">Apı'leriniz için Swagger meta verileri oluşturmak için temel neden aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01caf-208">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="01caf-209">**Otomatik olarak kullanmak ve Apı'lerinizi tümleştirmek diğer ürünlere yönelik özelliği**.</span><span class="sxs-lookup"><span data-stu-id="01caf-209">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="01caf-210">Ürünleri onlarca ve [ticari Araçları](https://swagger.io/commercial-tools/) ve birçok [kitaplıklar ve çerçeveler](https://swagger.io/open-source-integrations/) Swagger'ı destekler.</span><span class="sxs-lookup"><span data-stu-id="01caf-210">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="01caf-211">Microsoft üst düzey ürün ve otomatik olarak aşağıdaki gibi Swagger tabanlı API'ler tüketebileceği araç vardır:</span><span class="sxs-lookup"><span data-stu-id="01caf-211">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="01caf-212">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="01caf-212">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="01caf-213">Swagger'ı çağırmak için .NET istemci sınıfları otomatik olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01caf-213">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="01caf-214">Bu aracı CLI üzerinden kullanılabilir ve GUI aracılığıyla kolay kullanım için de Visual Studio ile tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-214">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="01caf-215">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="01caf-215">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="01caf-216">Otomatik olarak [kullanın ve API'nizi tümleştirme](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) üst düzey bir Microsoft Flow iş akışınıza olmadan programlama becerileri gerekir.</span><span class="sxs-lookup"><span data-stu-id="01caf-216">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="01caf-217">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="01caf-217">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="01caf-218">Otomatik olarak, API'SİNDEN tüketebileceği [PowerApps mobil uygulamalar](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) ile oluşturulmuş [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), gerekli herhangi bir programlama becerilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="01caf-218">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="01caf-219">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="01caf-219">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="01caf-220">Otomatik olarak [kullanın ve API'nizi Azure App Service mantıksal uygulamalarla tümleştirme](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), gerekli herhangi bir programlama becerilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="01caf-220">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="01caf-221">**API belgelerini otomatik olarak oluşturma yeteneği**.</span><span class="sxs-lookup"><span data-stu-id="01caf-221">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="01caf-222">Karmaşık mikro hizmet tabanlı uygulamalar gibi büyük ölçekli RESTful API'leri oluşturduğunuzda, istek ve yanıt yükleri kullanılan farklı veri modellerine sahip çok sayıda uç noktalar ele almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01caf-222">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="01caf-223">API'NİZİN ve geliştiriciler tarafından benimseme başarısı için uygun belgelere sahip olunması ve Swagger ile aldıkça, sağlam bir API Gezgini sahip anahtardır.</span><span class="sxs-lookup"><span data-stu-id="01caf-223">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="01caf-224">Microsoft Flow, PowerApps ve Logic Apps Azure API'leri ve bunlara nasıl kullanılacağını anlamak için kullandıklarınız swagger'ın meta verilerdir.</span><span class="sxs-lookup"><span data-stu-id="01caf-224">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="01caf-225">Swagger API meta verileri oluşturma Swashbuckle NuGet paketini ile otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="01caf-225">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="01caf-226">Swagger meta verilerde el ile (bir JSON veya YAML dosyası) oluşturmak zahmetli bir iş olabilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-226">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="01caf-227">Ancak, ASP.NET Web API Hizmetleri API bulma kullanarak otomatikleştirebileceğiniz [Swashbuckle NuGet paketini](https://aka.ms/swashbuckledotnetcore) dinamik olarak Swagger API'si meta verileri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="01caf-227">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="01caf-228">Swashbuckle, ASP.NET Web API projeleriniz için Swagger meta verileri otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01caf-228">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="01caf-229">Bu, ASP.NET Core Web API projelerini ve geleneksel ASP.NET Web API ve Azure API uygulaması, Azure mobil uygulaması, ASP Azure Service Fabric mikro hizmetler gibi diğer tüm flavor destekler.</span><span class="sxs-lookup"><span data-stu-id="01caf-229">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="01caf-230">Ayrıca, düz Web API'si için başvuru uygulaması olarak kapsayıcılarında, dağıtılan destekler.</span><span class="sxs-lookup"><span data-stu-id="01caf-230">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="01caf-231">Swashbuckle birleştirir API Gezgini ve Swagger veya [swagger kullanıcı arabirimi](https://github.com/swagger-api/swagger-ui) zengin bulma ve belgeler için API tüketicilerinize deneyimi sağlamak.</span><span class="sxs-lookup"><span data-stu-id="01caf-231">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="01caf-232">Kendi Swagger meta verileri Oluşturucu altyapısına ek olarak, Swashbuckle swagger-Swashbuckle yüklendikten sonra otomatik olarak hizmet verecek yukarı kullanıcı arabirimi, katıştırılmış bir sürümünü de içerir.</span><span class="sxs-lookup"><span data-stu-id="01caf-232">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="01caf-233">Bu, iyi bir bulma geliştiricilerin API'nizi kullanmasına yardımcı olmak için kullanıcı Arabirimi ile API'nizi tamamlayabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="01caf-233">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="01caf-234">Bu otomatik olarak, API'nizi geliştirmeye odaklanabilirsiniz oluşturulmuş olduğu için çok az miktarda kodu ve bakım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="01caf-234">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="01caf-235">API Gezgini için sonucu Şekil 8-8 gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="01caf-235">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="01caf-236">**Şekil 8-8**.</span><span class="sxs-lookup"><span data-stu-id="01caf-236">**Figure 8-8**.</span></span> <span data-ttu-id="01caf-237">Swashbuckle API Gezgini Swagger meta verileri temel alarak — hizmetine mikro hizmet Kataloğu</span><span class="sxs-lookup"><span data-stu-id="01caf-237">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="01caf-238">API Gezgini burada en önemli şey değil.</span><span class="sxs-lookup"><span data-stu-id="01caf-238">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="01caf-239">Kendisini Swagger meta verilerde açıklayan bir Web API'si aldıktan sonra birçok platformda hedefleyebilen istemci proxy sınıfı kod oluşturucuları dahil olmak üzere Swagger tabanlı araçlardan, API'nizi sorunsuz bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-239">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="01caf-240">Örneğin, bahsedildiği gibi [AutoRest](https://github.com/Azure/AutoRest) otomatik olarak .NET istemci sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01caf-240">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="01caf-241">Ancak gibi ek araçlar [swagger codegen](https://github.com/swagger-api/swagger-codegen) kod oluşturma API'si istemci kitaplıkları, sunucu saptamalar ve belgeleri otomatik olarak izin olan de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01caf-241">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="01caf-242">Üst düzey meta-package altında çeşitli iç NuGet paketleri şu anda, Swashbuckle oluşan [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) sürüm 1.0.0 veya sonraki bir sürümü ASP.NET Core uygulamaları için.</span><span class="sxs-lookup"><span data-stu-id="01caf-242">Currently, Swashbuckle consists of several internal NuGet packages under the high-level meta-package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) version 1.0.0 or later for ASP.NET Core applications.</span></span>

<span data-ttu-id="01caf-243">Bu NuGet paketleri, Web API projesinde yükledikten sonra aşağıdaki kodu olduğu gibi bir başlangıç sınıfı Swagger yapılandırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="01caf-243">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

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

<span data-ttu-id="01caf-244">Bunu yaptıktan sonra uygulamanızı başlatın ve bu gibi URL'leri kullanarak aşağıdaki Swagger JSON ve UI uç göz atın:</span><span class="sxs-lookup"><span data-stu-id="01caf-244">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

<span data-ttu-id="01caf-245">Daha önce oluşturulan kullanıcı arabirimini http:// gibi bir URL için Swashbuckle tarafından oluşturulan gördüğünüz&lt;kök URL'si your &gt; /swagger/kullanıcı arabirimi.</span><span class="sxs-lookup"><span data-stu-id="01caf-245">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="01caf-246">Şekil 8-9'da herhangi bir API yöntemini nasıl test görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01caf-246">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="01caf-247">**Şekil 8-9**.</span><span class="sxs-lookup"><span data-stu-id="01caf-247">**Figure 8-9**.</span></span> <span data-ttu-id="01caf-248">Swashbuckle UI testi katalog/öğeleri API yöntemi</span><span class="sxs-lookup"><span data-stu-id="01caf-248">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="01caf-249">Şekil 8-10 hizmetine mikro hizmet oluşturulan Swagger JSON meta verileri gösterir (olan araçlar altında kullanın) olduğunda, isteği &lt;kök URL'si your&gt;/swagger/v1/swagger.json kullanarak [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="01caf-249">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="01caf-250">**Şekil 8-10**.</span><span class="sxs-lookup"><span data-stu-id="01caf-250">**Figure 8-10**.</span></span> <span data-ttu-id="01caf-251">Swagger JSON meta verileri</span><span class="sxs-lookup"><span data-stu-id="01caf-251">Swagger JSON metadata</span></span>

<span data-ttu-id="01caf-252">Bu basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="01caf-252">It is that simple.</span></span> <span data-ttu-id="01caf-253">Ve daha fazla işlevsellik API'nize eklediğinizde otomatik olarak oluşturulduğundan, Swagger meta verileri büyüyecektir.</span><span class="sxs-lookup"><span data-stu-id="01caf-253">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="01caf-254">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="01caf-254">Additional resources</span></span>

-   <span data-ttu-id="01caf-255">**Swagger kullanan ASP.NET Web API Yardım sayfaları**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="01caf-255">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="01caf-256">[Önceki](microservice-application-design.md)
[İleri](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="01caf-256">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
