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
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="65ba0-103">Basit bir veri temelli CRUD mikro hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="65ba0-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="65ba0-104">Bu bölümde, bir veri kaynağında oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemlerini gerçekleştiren basit bir mikro hizmetin nasıl oluşturulacak olduğu açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="65ba0-105">Basit bir CRUD microservice tasarımı</span><span class="sxs-lookup"><span data-stu-id="65ba0-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="65ba0-106">Bakış bir tasarım açısından, konteyner microservice bu tür çok basittir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="65ba0-107">Belki de çözmek için sorun basit, ya da belki de uygulama kavramının sadece bir kanıtıdır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Basit bir CRUD microservice iç tasarım deseni gösteren diyagram.](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

<span data-ttu-id="65ba0-109">**Şekil 6-4**.</span><span class="sxs-lookup"><span data-stu-id="65ba0-109">**Figure 6-4**.</span></span> <span data-ttu-id="65ba0-110">Basit CRUD mikroservisleri için dahili tasarım</span><span class="sxs-lookup"><span data-stu-id="65ba0-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="65ba0-111">Basit veri sürücü hizmeti bu tür bir örnek eShopOnContainers örnek uygulamadan katalog microservice olduğunu.</span><span class="sxs-lookup"><span data-stu-id="65ba0-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="65ba0-112">Bu hizmet türü, tüm işlevselliğini veri modeli, iş mantığı ve veri erişim kodu için sınıflar içeren tek bir ASP.NET Çekirdek Web API projesinde uygular.</span><span class="sxs-lookup"><span data-stu-id="65ba0-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="65ba0-113">Ayrıca, ilgili verilerini SQL Server'da çalışan bir veritabanında (dev/test amacıyla başka bir kapsayıcı olarak) de polar, ancak Şekil 6-5'te gösterildiği gibi normal bir SQL Server ana bilgisayarı da olabilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Veri odaklı/CRUD microservice konteynerini gösteren diyagram.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

<span data-ttu-id="65ba0-115">**Şekil 6-5**.</span><span class="sxs-lookup"><span data-stu-id="65ba0-115">**Figure 6-5**.</span></span> <span data-ttu-id="65ba0-116">Basit veri odaklı/CRUD microservice tasarım</span><span class="sxs-lookup"><span data-stu-id="65ba0-116">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="65ba0-117">Önceki diyagram, aynı Docker ana bilgisayarda olabilir veya olmayabilir katalog veritabanını içeren mantıksal Katalog microservice gösterir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-117">The previous diagram shows the logical Catalog microservice, that includes its Catalog database, which can be or not in the same Docker host.</span></span> <span data-ttu-id="65ba0-118">Veritabanının aynı Docker ana bilgisayarda olması geliştirme için iyi olabilir, ancak üretim için iyi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-118">Having the database in the same Docker host might be good for development, but not for production.</span></span> <span data-ttu-id="65ba0-119">Bu tür bir hizmet geliştirirken, yalnızca [ASP.NET Core'a](https://docs.microsoft.com/aspnet/core/) ve [Entity Framework Core](https://docs.microsoft.com/ef/core/index)gibi veri erişim API veya ORM'ye ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-119">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="65ba0-120">Ayrıca, bir sonraki bölümde açıklandığı gibi, hizmetinizin neler sunduğunun açıklamasını sağlamak için [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) üzerinden otomatik olarak [Swagger](https://swagger.io/) meta verileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-120">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="65ba0-121">Bir Docker kapsayıcısı içinde SQL Server gibi bir veritabanı sunucusu çalıştırmanın geliştirme ortamları için harika olduğunu unutmayın, çünkü bulutta veya şirket içinde bir veritabanı sağlamanıza gerek kalmadan tüm bağımlılıklarınızı çalışır duruma getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-121">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="65ba0-122">Bu, tümleştirme testlerini çalıştırırken çok kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-122">This is very convenient when running integration tests.</span></span> <span data-ttu-id="65ba0-123">Ancak, üretim ortamları için, genellikle bu yaklaşımla yüksek kullanılabilirlik elde etmediğiniz için bir kapsayıcıda veritabanı sunucusu çalıştırmak önerilmez.</span><span class="sxs-lookup"><span data-stu-id="65ba0-123">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="65ba0-124">Azure'daki bir üretim ortamı için, Yüksek kullanılabilirlik ve yüksek ölçeklenebilirlik sağlayabilen Azure SQL DB veya başka bir veritabanı teknolojisi kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-124">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="65ba0-125">Örneğin, Bir NoSQL yaklaşımı için CosmosDB'yi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-125">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="65ba0-126">Son olarak, Dockerfile ve docker-compose.yml meta veri dosyalarını düzenleyerek, bu kapsayıcının görüntüsünün nasıl oluşturulacağını-hangi temel görüntüyü kullanacağını ve iç ve dış adlar ve TCP bağlantı noktaları gibi tasarım ayarlarını yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-126">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="65ba0-127">ASP.NET Core ile basit bir CRUD microservice uygulama</span><span class="sxs-lookup"><span data-stu-id="65ba0-127">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="65ba0-128">.NET Core ve Visual Studio'yu kullanarak basit bir CRUD microservice uygulamak için, Şekil 6-6'da gösterildiği gibi basit bir ASP.NET Core Web API projesi (.NET Core'da çalışan ve böylece Bir Linux Docker ana bilgisayarda çalıştırılabilen) oluşturarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="65ba0-128">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Projenin kurulumlarını gösteren Görsel Stüdyoların ekran görüntüsü.](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

<span data-ttu-id="65ba0-130">**Şekil 6-6**.</span><span class="sxs-lookup"><span data-stu-id="65ba0-130">**Figure 6-6**.</span></span> <span data-ttu-id="65ba0-131">Visual Studio 2019'da ASP.NET Core Web API projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="65ba0-131">Creating an ASP.NET Core Web API project in Visual Studio 2019</span></span>

<span data-ttu-id="65ba0-132">ASP.NET Çekirdek Web API Projesi oluşturmak için önce ASP.NET Bir Web Uygulaması seçin ve ardından API türünü seçin.</span><span class="sxs-lookup"><span data-stu-id="65ba0-132">To create an ASP.NET Core Web API Project, first select an ASP.NET Core Web Application and then select the API type.</span></span> <span data-ttu-id="65ba0-133">Projeyi oluşturduktan sonra, Varlık Çerçevesi API'sini veya diğer API'yi kullanarak MVC denetleyicilerinizi diğer Web API projesinde olduğu gibi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-133">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="65ba0-134">Yeni bir Web API projesinde, bu mikro hizmetteki tek bağımlılığın ASP.NET Core'un kendisi olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-134">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="65ba0-135">Dahili olarak, *Microsoft.AspNetCore.All* bağımlılığı içinde, Şekil 6-7'de gösterildiği gibi Varlık Çerçevesi ve diğer birçok .NET Core NuGet paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="65ba0-135">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core NuGet packages, as shown in Figure 6-7.</span></span>

![Catalog.Api'nin NuGet bağımlılıklarını gösteren VS ekran görüntüsü.](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

<span data-ttu-id="65ba0-137">**Şekil 6-7**.</span><span class="sxs-lookup"><span data-stu-id="65ba0-137">**Figure 6-7**.</span></span> <span data-ttu-id="65ba0-138">Basit bir CRUD Web API microservice bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="65ba0-138">Dependencies in a simple CRUD Web API microservice</span></span>

<span data-ttu-id="65ba0-139">API projesi, gerekli tüm paketlere yapılan başvuruları içeren Microsoft.AspNetCore.App NuGet paketine yapılan başvuruları içerir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-139">The API project includes references to the Microsoft.AspNetCore.App NuGet package, that includes references to all essential packages.</span></span> <span data-ttu-id="65ba0-140">Diğer bazı paketleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-140">It could include some other packages as well.</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="65ba0-141">Entity Framework Core ile CRUD Web API hizmetlerinin uygulanması</span><span class="sxs-lookup"><span data-stu-id="65ba0-141">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="65ba0-142">Entity Framework (EF) Core, popüler Entity Framework veri erişim teknolojisinin hafif, genişletilebilir ve çapraz platformlu bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="65ba0-142">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="65ba0-143">EF Core, .NET geliştiricilerin .NET nesnelerini kullanarak bir veritabanıyla çalışmasını sağlayan bir nesne ilişkisisel mapper (ORM) dir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-143">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="65ba0-144">Veritabanı Linux Docker görüntü için SQL Server ile bir kapsayıcıda çalışıyor çünkü katalog microservice EF ve SQL Server sağlayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-144">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="65ba0-145">Ancak, veritabanı Windows şirket içi veya Azure SQL DB gibi herhangi bir SQL Server'da dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-145">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="65ba0-146">Değiştirmek için gereken tek şey ASP.NET Web API microservice bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="65ba0-146">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="65ba0-147">Veri modeli</span><span class="sxs-lookup"><span data-stu-id="65ba0-147">The data model</span></span>

<span data-ttu-id="65ba0-148">EF Core ile veri erişimi bir model kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-148">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="65ba0-149">Bir model, (etki alanı modeli) varlık sınıfları ve veritabanıyla bir oturumu temsil eden ve verileri sorgulayıp kaydetmenize olanak tanıyan türemiş bir bağlam (DbContext) oluşur.</span><span class="sxs-lookup"><span data-stu-id="65ba0-149">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="65ba0-150">Varolan bir veritabanından bir model oluşturabilir, veritabanınızla eşleşecek bir modeli el ile kodlayabilir veya modelinizden bir veritabanı oluşturmak için EF geçişlerini kodlama yaklaşımını kullanarak (modeliniz zaman içinde değiştikçe veritabanını geliştirmeyi kolaylaştırır).</span><span class="sxs-lookup"><span data-stu-id="65ba0-150">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="65ba0-151">Katalog microservice için son yaklaşımı kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-151">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="65ba0-152">Aşağıdaki kod örneğinde CatalogItem varlık sınıfının bir örneğini görebilirsiniz, basit bir Düz Eski CLR Nesnesi ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) varlık sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-152">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="65ba0-153">Ayrıca, veritabanıyla ilgili bir oturumu temsil eden bir DbContext'a da ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-153">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="65ba0-154">Katalog microservice için CatalogContext sınıfı aşağıdaki örnekte gösterildiği gibi DbContext taban sınıfından türetilmiştir:</span><span class="sxs-lookup"><span data-stu-id="65ba0-154">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="65ba0-155">Ek `DbContext` uygulamalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-155">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="65ba0-156">Örneğin, örnek Catalog.API microservice'de, veritabanına `DbContext` `CatalogContextSeed` ilk kez erişmeye çalıştığında örnek verileri otomatik olarak doldurduğu ikinci bir ad vardır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-156">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="65ba0-157">Bu yöntem demo verileri ve otomatik test senaryoları için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-157">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="65ba0-158">Içinde, nesne / veritabanı varlık eşlemeleri ve diğer [EF genişletilebilirlik noktaları](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)özelleştirmek için `OnModelCreating` yöntemi kullanın. `DbContext`</span><span class="sxs-lookup"><span data-stu-id="65ba0-158">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="65ba0-159">Web API denetleyicilerinden veri sorgulama</span><span class="sxs-lookup"><span data-stu-id="65ba0-159">Querying data from Web API controllers</span></span>

<span data-ttu-id="65ba0-160">Varlık sınıflarınızın örnekleri genellikle aşağıdaki örnekte gösterildiği gibi, Dil Tümleşik Sorgusu (LINQ) kullanılarak veritabanından alınır:</span><span class="sxs-lookup"><span data-stu-id="65ba0-160">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="65ba0-161">Verileri kaydetme</span><span class="sxs-lookup"><span data-stu-id="65ba0-161">Saving data</span></span>

<span data-ttu-id="65ba0-162">Veriler, varlık sınıflarınızın örnekleri kullanılarak veritabanında oluşturulur, silinir ve değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-162">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="65ba0-163">Web API denetleyicilerinize aşağıdaki sabit kodlu örnek (bu durumda sahte veri) gibi kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-163">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="65ba0-164">ASP.NET Çekirdek ve Web API denetleyicilerinde Bağımlılık Enjeksiyonu</span><span class="sxs-lookup"><span data-stu-id="65ba0-164">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="65ba0-165">CoreASP.NET de Bağımlılık Enjeksiyonu'nu (DI) kutunun dışında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-165">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="65ba0-166">İsterseniz tercih ettiğiniz IoC kapsayıcısını ASP.NET Core altyapısına takabilirsiniz, ancak üçüncü taraf Bir Denetim Ters Çevirme (IoC) kapsayıcısı kurmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="65ba0-166">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="65ba0-167">Bu durumda, denetleyici oluşturucu aracılığıyla gerekli EF DBContext veya ek depoları doğrudan enjekte edebilirsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-167">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="65ba0-168">`CatalogController` Sınıfın yukarıdaki örneğinde, `CatalogController()` bir tür nesnesi `CatalogContext` ve diğer nesneleri oluşturucu aracılığıyla enjekte ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-168">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="65ba0-169">Web API projesinde ayarlanan önemli bir yapılandırma, hizmetin IoC kapsayıcısına DbContext sınıf kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-169">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="65ba0-170">`Startup` Bunu genellikle aşağıdaki **basitleştirilmiş** örnekte `services.AddDbContext<DbContext>()` gösterildiği gibi yöntemin içindeki `ConfigureServices()` yöntemi çağırarak sınıfta yaparsınız:</span><span class="sxs-lookup"><span data-stu-id="65ba0-170">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following **simplified** example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="65ba0-171">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="65ba0-171">Additional resources</span></span>

- <span data-ttu-id="65ba0-172">**Verileri Sorgulama** </span><span class="sxs-lookup"><span data-stu-id="65ba0-172">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="65ba0-173">**Veri Kaydetme** </span><span class="sxs-lookup"><span data-stu-id="65ba0-173">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="65ba0-174">Docker kapları tarafından kullanılan DB bağlantı dizesi ve ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="65ba0-174">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="65ba0-175">ASP.NET Core ayarlarını kullanabilir ve aşağıdaki örnekte gösterildiği gibi settings.json dosyanıza bir ConnectionString özelliği ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65ba0-175">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="65ba0-176">settings.json dosyası, ConnectionString özelliği veya başka bir özellik için varsayılan değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-176">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="65ba0-177">Ancak, bu özellikler Docker kullanırken docker-compose.override.yml dosyasında belirttiğiniz ortam değişkenlerinin değerleri tarafından geçersiz kılınacaktır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-177">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="65ba0-178">Docker-compose.yml veya docker-compose.override.yml dosyalarınızdan, docker'ın aşağıdaki docker-compose.override.yml dosyasında gösterildiği gibi, bunları sizin için işletim sistemi ortam değişkenleri olarak ayarlaması için bu ortam değişkenlerini başlangıç olarak verebilirsiniz (bağlantı dize ve diğer satırları bu örnekte sarın, ancak kendi dosyanızda kaydırma olmaz).</span><span class="sxs-lookup"><span data-stu-id="65ba0-178">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

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

<span data-ttu-id="65ba0-179">Çözüm düzeyindeki docker-compose.yml dosyaları yalnızca proje veya microservice düzeyindeki yapılandırma dosyalarından daha esnek olmakla kalmıyor, aynı zamanda docker-compose dosyalarında belirtilen değerlere sahip ortam değişkenlerini geçersiz kılarsanız daha güvenlidir. Azure DevOps Services Docker dağıtım görevlerinden olduğu gibi dağıtım araçlarınız.</span><span class="sxs-lookup"><span data-stu-id="65ba0-179">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="65ba0-180">Son olarak, daha önceki bir kod\[örneğinde ConfigureServices yönteminde gösterildiği gibi Yapılandırma "ConnectionString"\]kullanarak bu değeri kodunuzdan alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-180">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="65ba0-181">Ancak, üretim ortamları için bağlantı dizeleri gibi sırları niçin depolayabildiğinize ilişkin ek yollar keşfetmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-181">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="65ba0-182">Uygulama sırlarını yönetmenin mükemmel bir yolu [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-182">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="65ba0-183">Azure Key Vault, bulut uygulamalarınız ve hizmetleriniz tarafından kullanılan şifreleme anahtarlarını ve sırlarını depolamaya ve korumaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="65ba0-183">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="65ba0-184">Bir sır, API tuşları, bağlantı dizeleri, parolalar, vb gibi sıkı kontrol tutmak istediğiniz bir şey ve sıkı kontrol kullanım günlüğü içerir, sona erme ayarı, erişim yönetmek, *diğerleri arasında*.</span><span class="sxs-lookup"><span data-stu-id="65ba0-184">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="65ba0-185">Azure Key Vault, uygulama sırlarını niçin herkesin tanımasına gerek kalmadan kullanımının çok ayrıntılı bir kontrol düzeyine izin verir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-185">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="65ba0-186">Sırlar, geliştirme veya işlemleri kesintiye uğratmadan gelişmiş güvenlik için döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-186">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="65ba0-187">Anahtar Kasası'nı kullanabilmeleri için başvuruların kuruluşun Active Directory'sine kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-187">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="65ba0-188">Daha fazla bilgi için *Key Vault Concepts belgelerini* kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-188">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="65ba0-189">ASP.NET Web API'lerinde sürüm uygulama</span><span class="sxs-lookup"><span data-stu-id="65ba0-189">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="65ba0-190">İş gereksinimleri değiştikçe, yeni kaynak koleksiyonları eklenebilir, kaynaklar arasındaki ilişkiler değişebilir ve kaynaklardaki verilerin yapısı değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-190">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="65ba0-191">Yeni gereksinimleri işlemek için bir Web API'sini güncelleştirmek nispeten basit bir işlemdir, ancak bu tür değişikliklerin Web API'sını tüketen istemci uygulamaları üzerindeki etkilerini göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-191">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="65ba0-192">Bir Web API'sini tasarlayan ve uygulayan geliştirici bu API üzerinde tam denetime sahip olsa da, geliştirici uzaktan çalışan üçüncü taraf kuruluşlar tarafından oluşturulabilecek istemci uygulamaları üzerinde aynı denetim derecesine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-192">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="65ba0-193">Sürüm, bir Web API'sinin açığa çıkardığı özellikleri ve kaynakları göstermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="65ba0-193">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="65ba0-194">İstemci uygulaması daha sonra bir özellik veya kaynağın belirli bir sürümüne istek gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-194">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="65ba0-195">Sürüm uygulamak için çeşitli yaklaşımlar vardır:</span><span class="sxs-lookup"><span data-stu-id="65ba0-195">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="65ba0-196">URI sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="65ba0-196">URI versioning</span></span>

- <span data-ttu-id="65ba0-197">Sorgu dizesi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="65ba0-197">Query string versioning</span></span>

- <span data-ttu-id="65ba0-198">Üst bilgi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="65ba0-198">Header versioning</span></span>

<span data-ttu-id="65ba0-199">Sorgu dizesi ve URI sürümü uygulamak için en basit olandır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-199">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="65ba0-200">Üstbilgi sürümü iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-200">Header versioning is a good approach.</span></span> <span data-ttu-id="65ba0-201">Ancak, üstbilgi sürümü URI sürümü kadar açık ve basit değildir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-201">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="65ba0-202">URL sürümü en basit ve en açık olduğundan, eShopOnContainers örnek uygulama URI sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-202">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="65ba0-203">URI sürümünde, eShopOnContainers örnek uygulamasında olduğu gibi, Web API'sını her değiştirdiğinizde veya kaynakların şemasını değiştirdiğinizde, her kaynak için URI'ye bir sürüm numarası eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-203">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="65ba0-204">Varolan URI'ler, istenen sürümle eşleşen şemaya uygun kaynakları döndürerek eskisi gibi çalışmaya devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-204">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="65ba0-205">Aşağıdaki kod örneğinde gösterildiği gibi, sürüm, Web API denetleyicisindeki Rota özniteliği kullanılarak ayarlanabilir ve bu da sürümü URI'de açık hale getirir (bu durumda v1).</span><span class="sxs-lookup"><span data-stu-id="65ba0-205">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="65ba0-206">Bu sürüm mekanizması basittir ve isteği uygun bitiş noktasına yönlendiren sunucuya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-206">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="65ba0-207">Ancak, REST kullanırken daha sofistike bir sürüm ve en iyi yöntem için, hipermedya kullanmanız ve [HATEOAS (Uygulama Durumu Motoru olarak Hypertext)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)uygulamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-207">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="65ba0-208">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="65ba0-208">Additional resources</span></span>

- <span data-ttu-id="65ba0-209">**Scott Hanselman' ı. ASP.NET Çekirdek RESTful Web API sürümü kolay** </span><span class="sxs-lookup"><span data-stu-id="65ba0-209">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="65ba0-210">**RESTful web API'yi sürümleme** </span><span class="sxs-lookup"><span data-stu-id="65ba0-210">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="65ba0-211">**Roy Fielding' i. Sürüm, Hipermedya ve REST** </span><span class="sxs-lookup"><span data-stu-id="65ba0-211">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="65ba0-212">ASP.NET Core Web API'nızdan Swagger açıklama meta verileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="65ba0-212">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="65ba0-213">[Swagger,](https://swagger.io/) restful API'lerinizi tasarlamanıza, oluşturmanıza, belgelemenize ve tüketmenize yardımcı olan büyük bir araç ekosistemi tarafından desteklenen yaygın olarak kullanılan bir açık kaynak çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-213">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="65ba0-214">API açıklama meta veri etki alanı için standart haline gelmektedir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-214">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="65ba0-215">Swagger açıklama meta verilerini, veri odaklı mikro hizmetler veya daha gelişmiş etki alanına dayalı mikro hizmetler (aşağıdaki bölümde açıklandığı gibi) her türlü mikro hizmete eklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-215">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="65ba0-216">Swagger'ın kalbi, JSON veya YAML dosyasındaki API açıklama meta verileri olan Swagger belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-216">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="65ba0-217">Belirtim, KOLAY geliştirme, keşif ve tümleştirme için tüm kaynaklarını ve işlemlerini hem insan hem de makine tarafından okunabilir bir biçimde ayrıntılı olarak açıklayan API'niz için yeniden kullanılabilir sözleşme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65ba0-217">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="65ba0-218">Belirtim, OpenAPI Belirtimi'nin (OAS) temelini oluşturur ve yeniden yapılan arabirimlerin tanımlanma biçimini standartlaştırmak için açık, şeffaf ve işbirlikçi bir topluluk içinde geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-218">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="65ba0-219">Belirtim, bir hizmetin nasıl keşfedilebildiğini ve yeteneklerinin nasıl anlaşıldığının yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="65ba0-219">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="65ba0-220">Spotify, Uber, Slack ve Microsoft gibi şirketlerden bir web editörü ve Swagger belirtimleri örnekleri<https://swagger.io>dahil olmak üzere daha fazla bilgi için Swagger sitesine bakın ( ).</span><span class="sxs-lookup"><span data-stu-id="65ba0-220">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="65ba0-221">Neden Swagger kullanıyorsun?</span><span class="sxs-lookup"><span data-stu-id="65ba0-221">Why use Swagger?</span></span>

<span data-ttu-id="65ba0-222">API'leriniz için Swagger meta verileri oluşturmanın başlıca nedenleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-222">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="65ba0-223">**Diğer ürünlerin API'lerinizi otomatik olarak tüketme ve tümleştirme yeteneği.**</span><span class="sxs-lookup"><span data-stu-id="65ba0-223">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="65ba0-224">Düzinelerce ürün ve [ticari araç](https://swagger.io/commercial-tools/) ve birçok kütüphane ve çerçeveSwagger'ı desteklemez. [libraries and frameworks](https://swagger.io/open-source-integrations/)</span><span class="sxs-lookup"><span data-stu-id="65ba0-224">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="65ba0-225">Microsoft, aşağıdakiler gibi Swagger tabanlı API'leri otomatik olarak tüketebilen üst düzey ürünlere ve araçlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="65ba0-225">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="65ba0-226">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="65ba0-226">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="65ba0-227">Swagger'ı aramak için otomatik olarak .NET istemci sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-227">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="65ba0-228">Bu araç CLI'den kullanılabilir ve GUI aracılığıyla kolay kullanım için Visual Studio ile entegre olur.</span><span class="sxs-lookup"><span data-stu-id="65ba0-228">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="65ba0-229">[Microsoft Akışı](https://flow.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="65ba0-229">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="65ba0-230">[API'nizi](https://flow.microsoft.com/blog/integrating-custom-api/) programlama becerisi gerektirmeden otomatik olarak kullanabilir ve üst düzey bir Microsoft Flow iş akışına entegre edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-230">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="65ba0-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="65ba0-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="65ba0-232">[PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/)ile oluşturulmuş [PowerApps mobil uygulamalarından](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) API'nizi programlama becerisi gerektirmeden otomatik olarak tüketebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-232">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="65ba0-233">[Azure Uygulama Hizmeti Mantık Uygulamaları](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="65ba0-233">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="65ba0-234">Programlama becerisi gerektirmeden [API'nizi](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)otomatik olarak kullanabilir ve Azure Uygulaması Logic App'e entegre edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-234">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="65ba0-235">**API belgelerini otomatik olarak oluşturabilme.**</span><span class="sxs-lookup"><span data-stu-id="65ba0-235">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="65ba0-236">Karmaşık mikro hizmet tabanlı uygulamalar gibi büyük ölçekli YENIDEN kullanılabilir API'ler oluşturduğunuzda, istek ve yanıt yüklerinde kullanılan farklı veri modelleri ile birçok uç noktayı işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-236">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="65ba0-237">Uygun belgelere sahip olmak ve sağlam bir API gezginine sahip olmak, Swagger ile birlikte olsun, API'nizin başarısı ve geliştiriciler tarafından benimsenmesi için anahtardır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-237">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="65ba0-238">Swagger'ın meta verileri, Microsoft Flow, PowerApps ve Azure Logic Apps'ın API'lerin nasıl kullanılacağını ve bunlara nasıl bağlanış yapılacağını anlamak için kullandığı verilerdir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-238">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="65ba0-239">*Swagger-ui*dayalı fonksiyonel API yardım sayfaları şeklinde, ASP.NET Core REST API uygulamaları için Swagger meta veri üretimi otomatikleştirmek için çeşitli seçenekler vardır.</span><span class="sxs-lookup"><span data-stu-id="65ba0-239">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="65ba0-240">Muhtemelen en iyi bilmek Şu anda [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) kullanılan [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) ve biz bu kılavuzda bazı ayrıntılı olarak ele alırsınız ama aynı\# zamanda [NSwag](https://github.com/RSuter/NSwag)kullanmak için seçenek var , Typescript ve C API istemcileri üretebilir, yanı sıra C\# denetleyicileri, bir Swagger veya OpenAPI belirtimi ve hatta kontrolörleri içeren .dll tarayarak, [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio)kullanarak .</span><span class="sxs-lookup"><span data-stu-id="65ba0-240">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), which can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="65ba0-241">Swashbuckle NuGet paketi ile API Swagger meta veri oluşturma otomatikleştirin nasıl</span><span class="sxs-lookup"><span data-stu-id="65ba0-241">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="65ba0-242">Swagger meta verilerini el ile (JSON veya YAML dosyasında) oluşturmak sıkıcı bir iş olabilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-242">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="65ba0-243">Ancak, Swagger API meta verilerini dinamik olarak oluşturmak için [Swashbuckle NuGet paketini](https://aka.ms/swashbuckledotnetcore) kullanarak ASP.NET Web API hizmetlerinin API keşfini otomatikleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-243">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="65ba0-244">Swashbuckle, ASP.NET Web API projeleriniz için otomatik olarak Swagger meta verilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65ba0-244">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="65ba0-245">ASP.NET Core Web API projelerini ve geleneksel ASP.NET Web API'sını ve Azure API Uygulaması, Azure Mobil Uygulaması, Azure Hizmet Dokusu mikro hizmetleri gibi diğer lezzetleri ASP.NET dayalı olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="65ba0-245">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="65ba0-246">Ayrıca, başvuru uygulamasında olduğu gibi kapsayıcılarda dağıtılan düz Web API'sini de destekler.</span><span class="sxs-lookup"><span data-stu-id="65ba0-246">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="65ba0-247">Swashbuckle, API tüketicileriniz için zengin bir keşif ve dokümantasyon deneyimi sağlamak için API Explorer ve [Swagger veya swagger-ui'yi](https://github.com/swagger-api/swagger-ui) birleştirir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-247">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="65ba0-248">Onun Swagger meta veri jeneratör motoruna ek olarak, Swashbuckle da swagger-ui gömülü bir sürümünü içerir, Hangi otomatik olarak swashbuckle yüklü bir kez hizmet verecek.</span><span class="sxs-lookup"><span data-stu-id="65ba0-248">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="65ba0-249">Bu, geliştiricilerin API'nizi kullanmasına yardımcı olmak için API'nizi güzel bir keşif ui'si ile tamamlayabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-249">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="65ba0-250">Otomatik olarak oluşturulduğu için çok az miktarda kod ve bakım gerektirir ve böylece API'nizi oluşturmaya odaklanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="65ba0-250">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="65ba0-251">API Explorer'ın sonucu Şekil 6-8'e benzer.</span><span class="sxs-lookup"><span data-stu-id="65ba0-251">The result for the API Explorer looks like Figure 6-8.</span></span>

![eShopOContainers API gösteren Swagger API Explorer ekran görüntüsü.](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

<span data-ttu-id="65ba0-253">**Şekil 6-8**.</span><span class="sxs-lookup"><span data-stu-id="65ba0-253">**Figure 6-8**.</span></span> <span data-ttu-id="65ba0-254">Swagger meta verilere dayalı Swashbuckle API Explorer—eShopOnContainers katalog microservice</span><span class="sxs-lookup"><span data-stu-id="65ba0-254">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="65ba0-255">Swashbuckle oluşturulan Swagger UI API belgeleri tüm yayımlanmış eylemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-255">The Swashbuckle generated Swagger UI API documentation includes all published actions.</span></span> <span data-ttu-id="65ba0-256">API explorer burada en önemli şey değildir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-256">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="65ba0-257">Swagger meta verilerinde kendisini tanımlayabilen bir Web API'niz olduktan sonra, API'niz birçok platformu hedef alabilecek istemci proxy sınıfı kod üreteçleri de dahil olmak üzere Swagger tabanlı araçlardan sorunsuz bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-257">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="65ba0-258">Örneğin, belirtildiği gibi, [AutoRest](https://github.com/Azure/AutoRest) otomatik olarak .NET istemci sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65ba0-258">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="65ba0-259">Ancak api istemci kitaplıklarının, sunucu saplamalarının ve belgelerin kod oluşturmalarına otomatik olarak izin veren [swagger-codegen](https://github.com/swagger-api/swagger-codegen) gibi ek araçlar da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="65ba0-259">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="65ba0-260">Şu anda, Swashbuckle ASP.NET Core uygulamaları için üst düzey meta paketi [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) altında beş dahili NuGet paketleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="65ba0-260">Currently, Swashbuckle consists of five internal NuGet packages under the high-level meta- package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="65ba0-261">Bu NuGet paketlerini Web API projenize yükledikten sonra, Aşağıdaki **basitleştirilmiş** kodda olduğu gibi Başlangıç sınıfında Swagger'ı yapılandırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="65ba0-261">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following **simplified** code:</span></span>

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

<span data-ttu-id="65ba0-262">Bu işlem yapıldıktan sonra, uygulamanızı başlatabilir ve aşağıdaki Gibi URL'leri kullanarak aşağıdaki Swagger JSON ve Kullanıcı Altı Kullanıcı Tarafından kullanıcı tarafından kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="65ba0-262">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="65ba0-263">Daha önce swashbuckle tarafından oluşturulan oluşturulan ui `http://<your-root-url>/swagger`gibi bir URL gördüm.</span><span class="sxs-lookup"><span data-stu-id="65ba0-263">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="65ba0-264">Şekil 6-9'da herhangi bir API yöntemini nasıl test edebileceğinizi de görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65ba0-264">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Kullanılabilir test araçlarını gösteren Swagger UI ekran görüntüsü.](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

<span data-ttu-id="65ba0-266">**Şekil 6-9**.</span><span class="sxs-lookup"><span data-stu-id="65ba0-266">**Figure 6-9**.</span></span> <span data-ttu-id="65ba0-267">Katalog/Öğeler API yöntemini test eden Swashbuckle UI</span><span class="sxs-lookup"><span data-stu-id="65ba0-267">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="65ba0-268">Swagger UI API ayrıntısı yanıtın bir örneğini gösterir ve geliştirici keşfi için harika olan gerçek API'yi çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="65ba0-268">The Swagger UI API detail shows a sample of the response and can be used to execute the real API, which is great for developer discovery.</span></span> <span data-ttu-id="65ba0-269">Şekil 6-10 `http://<your-root-url>/swagger/v1/swagger.json` [Postacı](https://www.getpostman.com/)kullanarak talep ettiğinizde eShopOnContainers microservice oluşturulan Swagger JSON meta verileri gösterir (hangi araçları altında kullanmak) .</span><span class="sxs-lookup"><span data-stu-id="65ba0-269">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![Swagger JSON meta verilerini gösteren örnek postacı ui ekran görüntüsü.](./media/data-driven-crud-microservice/swagger-json-metadata.png)

<span data-ttu-id="65ba0-271">**Şekil 6-10**.</span><span class="sxs-lookup"><span data-stu-id="65ba0-271">**Figure 6-10**.</span></span> <span data-ttu-id="65ba0-272">Swagger JSON meta verileri</span><span class="sxs-lookup"><span data-stu-id="65ba0-272">Swagger JSON metadata</span></span>

<span data-ttu-id="65ba0-273">Bu kadar basit.</span><span class="sxs-lookup"><span data-stu-id="65ba0-273">It is that simple.</span></span> <span data-ttu-id="65ba0-274">Ve otomatik olarak oluşturulduğundan, API'nize daha fazla işlevsellik eklediğinizde Swagger meta verileri büyür.</span><span class="sxs-lookup"><span data-stu-id="65ba0-274">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="65ba0-275">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="65ba0-275">Additional resources</span></span>

- <span data-ttu-id="65ba0-276">**Swagger kullanarak ASP.NET Web API Yardım Sayfaları** </span><span class="sxs-lookup"><span data-stu-id="65ba0-276">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="65ba0-277">**Swashbuckle ve ASP.NET Core ile başlayın** </span><span class="sxs-lookup"><span data-stu-id="65ba0-277">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="65ba0-278">**NSwag ve ASP.NET Core ile başlayın** </span><span class="sxs-lookup"><span data-stu-id="65ba0-278">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="65ba0-279">[Önceki](microservice-application-design.md)
> [Sonraki](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="65ba0-279">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
