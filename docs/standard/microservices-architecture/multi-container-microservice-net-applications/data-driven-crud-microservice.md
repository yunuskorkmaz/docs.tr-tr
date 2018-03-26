---
title: Bir basit veri güdümlü CRUD mikro hizmet oluşturma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Bir basit veri güdümlü CRUD mikro hizmet oluşturma
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: be8644e45be8db88c99332476e74c5c968764c74
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="f7ada-104">Bir basit veri güdümlü CRUD mikro hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7ada-104">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="f7ada-105">Bu bölüm anahatları basit bir oluşturmak için gerçekleştirdiği mikro hizmet oluşturun nasıl okuma, güncelleştirme ve bir veri kaynağında Sil (CRUD) işlemleri.</span><span class="sxs-lookup"><span data-stu-id="f7ada-105">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="f7ada-106">Basit bir CRUD mikro hizmet tasarlama</span><span class="sxs-lookup"><span data-stu-id="f7ada-106">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="f7ada-107">Bir tasarım açısından bakıldığında, bu tür kapsayıcılı mikro çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-107">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="f7ada-108">Belki de sorunu çözmek için basit bir işlemdir veya yalnızca bir kavram kanıtı belki de uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-108">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="f7ada-109">**Şekil 8-4**.</span><span class="sxs-lookup"><span data-stu-id="f7ada-109">**Figure 8-4**.</span></span> <span data-ttu-id="f7ada-110">Basit CRUD mikro için iç tasarımı</span><span class="sxs-lookup"><span data-stu-id="f7ada-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="f7ada-111">Bu tür bir basit veri sürücüsü hizmet Kataloğu mikro hizmet eShopOnContainers örnek uygulamadan örnektir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="f7ada-112">Bu tür bir hizmet kendi veri modeli, iş mantığı ve kendi veri erişim kodu için sınıflar içerir tek bir ASP.NET çekirdek Web API projesinde tüm işlevlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="f7ada-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="f7ada-113">Ayrıca, ilgili verilerini (olarak geliştirme ve test amaçları için başka bir kapsayıcı) SQL Server çalıştıran bir veritabanında depolar ancak normal herhangi bir SQL Server ana Şekil 8-5'te gösterildiği gibi de olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="f7ada-114">**Şekil 8-5**.</span><span class="sxs-lookup"><span data-stu-id="f7ada-114">**Figure 8-5**.</span></span> <span data-ttu-id="f7ada-115">Basit veri-güdümlü/CRUD mikro hizmet tasarım</span><span class="sxs-lookup"><span data-stu-id="f7ada-115">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="f7ada-116">Bu tür bir hizmet geliştirirken, yalnızca ihtiyacınız [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) ve veri erişimi API veya ORM gibi [Entity Framework Çekirdek](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="f7ada-116">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="f7ada-117">Ayrıca üretebilir [Swagger](http://swagger.io/) meta verileri otomatik olarak ile [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) ne hizmetiniz sunar, açıklaması bir sonraki bölümde açıklandığı gibi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="f7ada-117">You could also generate [Swagger](http://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="f7ada-118">Tüm bağımlılıklarınızı sahip için SQL Server'ın bir Docker kapsayıcısı içinde geliştirme ortamları için harikadır gibi bir veritabanı sunucusunu çalıştıran ve bir veritabanı bulutta veya şirket içi sağlamak zorunda kalmadan çalışan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f7ada-118">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="f7ada-119">Tümleştirme testleri, bu çok kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="f7ada-119">This is very convenient when running integration tests.</span></span> <span data-ttu-id="f7ada-120">Bu yaklaşım ile yüksek kullanılabilirlik genellikle almazsanız olduğundan ancak üretim ortamları için bir veritabanı sunucusu bir kapsayıcıda çalışan, önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f7ada-120">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="f7ada-121">Azure'da bir üretim ortamı için Azure SQL DB veya yüksek kullanılabilirlik ve yüksek ölçeklenebilirlik sağlayabilir herhangi bir veritabanı teknolojisini kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-121">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="f7ada-122">Örneğin, bir NoSQL yaklaşım için DocumentDB seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ada-122">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="f7ada-123">Son olarak, Dockerfile ve docker-compose.yml meta veri dosyaları düzenleyerek, bu kapsayıcı görüntüsünü nasıl oluşturulacak yapılandırabileceğiniz — hangi temel görüntü, kullanın, artı tasarım iç ve dış adlar ve TCP bağlantı noktaları gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7ada-123">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="f7ada-124">ASP.NET Core ile basit bir CRUD mikro hizmet uygulama</span><span class="sxs-lookup"><span data-stu-id="f7ada-124">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="f7ada-125">.NET Core ve Visual Studio kullanarak basit bir CRUD mikro hizmet uygulamak için (Linux Docker ana bilgisayarda çalıştırabilmeniz için .NET Core üzerinde çalışan), basit bir ASP.NET çekirdek Web API projesi oluşturarak gösterildiği Şekil 8-6 olarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="f7ada-125">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="f7ada-126">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="f7ada-126">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="f7ada-127">**Şekil 8-6**.</span><span class="sxs-lookup"><span data-stu-id="f7ada-127">**Figure 8-6**.</span></span> <span data-ttu-id="f7ada-128">Visual Studio'da ASP.NET çekirdek Web API projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7ada-128">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="f7ada-129">Projesi oluşturduktan sonra Entity Framework API veya diğer API kullanarak tüm diğer Web API projesinde, olduğu gibi MVC denetleyicileri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ada-129">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="f7ada-130">Yeni bir Web API projesinde, mikro hizmet ASP.NET Core üzerinde kendisini bakımından, yalnızca bağımlılık, olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ada-130">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="f7ada-131">Dahili olarak, içinde `Microsoft.AspNetCore.All` bağımlılık, onu başvurduğu Entity Framework ve diğer birçok .NET Core Nuget paketleri, Şekil 8-7'de gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f7ada-131">Internally, within the `Microsoft.AspNetCore.All` dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="f7ada-132">**Şekil 8-7**.</span><span class="sxs-lookup"><span data-stu-id="f7ada-132">**Figure 8-7**.</span></span> <span data-ttu-id="f7ada-133">Basit bir CRUD Web API mikro Hizmet bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="f7ada-133">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="f7ada-134">Entity Framework Çekirdek ile uygulama CRUD Web API Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="f7ada-134">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="f7ada-135">Hafif, Genişletilebilir, Entity Framework (EF) çekirdeği olur ve platformlar arası sürümü popüler Entity Framework verilerine erişim teknolojisini.</span><span class="sxs-lookup"><span data-stu-id="f7ada-135">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="f7ada-136">EF çekirdeği .NET geliştiricilerinin .NET nesneleri kullanarak bir veritabanı ile çalışmak bir nesne ilişkisel Eşleyici (ORM) olur.</span><span class="sxs-lookup"><span data-stu-id="f7ada-136">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="f7ada-137">Veritabanını bir kapsayıcıda Linux Docker görüntüsü için SQL Server ile çalıştığı için katalog mikro hizmet EF ve SQL Server sağlayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-137">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="f7ada-138">Ancak, veritabanı içine Windows Şirket içi veya Azure SQL DB gibi herhangi bir SQL sunucusuna dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-138">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="f7ada-139">Değiştirmek için gereken tek şey, ASP.NET Web API mikro hizmet bağlantı dizesinde.</span><span class="sxs-lookup"><span data-stu-id="f7ada-139">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>


#### <a name="the-data-model"></a><span data-ttu-id="f7ada-140">Veri modeli</span><span class="sxs-lookup"><span data-stu-id="f7ada-140">The data model</span></span>

<span data-ttu-id="f7ada-141">EF çekirdek ile veri erişim modeli kullanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-141">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="f7ada-142">Bir model sınıflar ve sorgu ve veri kaydetmenize olanak veren veritabanı, oturumla temsil eden bir türetilmiş bağlamı oluşur.</span><span class="sxs-lookup"><span data-stu-id="f7ada-142">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="f7ada-143">Varolan bir veritabanından bir model oluşturmak, el ile veritabanınızı eşleştirmek için bir model kod veya EF geçişler modelinizin dışında bir veritabanı oluşturmak için (ve modelinizi zaman içinde değiştikçe gelişmesi için) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7ada-143">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="f7ada-144">Katalog mikro hizmet için son yaklaşım kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="f7ada-144">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="f7ada-145">Basit bir düz eski CLR nesnesi aşağıdaki kod örneğinde, CatalogItem varlık sınıfı örneği görebilirsiniz ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) varlık sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7ada-145">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="f7ada-146">Ayrıca veritabanı oturumla temsil eden bir DbContext gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-146">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="f7ada-147">Katalog mikro hizmet için CatalogContext sınıfı aşağıdaki örnekte gösterildiği gibi DbContext temel sınıfından türetilen:</span><span class="sxs-lookup"><span data-stu-id="f7ada-147">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="f7ada-148">Ek olabilir `DbContext` uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="f7ada-148">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="f7ada-149">Örneğin, örnek Catalog.API mikro yoktur saniyenin `DbContext` adlı `CatalogContextSeed` burada bunu otomatik olarak doldurur örnek verileri çalışır veritabanına erişmek için ilk kez.</span><span class="sxs-lookup"><span data-stu-id="f7ada-149">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="f7ada-150">Bu yöntem, demo verileri ve otomatikleştirilmiş test senaryoları için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-150">This method is useful for demo data and for automated testing scenarios, as well.</span></span> <span data-ttu-id="f7ada-151">İçinde `DbContext`, kullandığınız `OnModelCreating` nesne/veritabanı varlık eşlemeleri ile ve diğer özelleştirmek için yöntemi [EF genişletilebilirlik noktaları](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="f7ada-151">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings with and other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="f7ada-152">Web API denetleyicilerinin verileri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="f7ada-152">Querying data from Web API controllers</span></span>

<span data-ttu-id="f7ada-153">Varlık sınıfları, genellikle aşağıdaki örnekte gösterildiği gibi dil tümleşik sorgu (LINQ), kullanarak veritabanından alınır:</span><span class="sxs-lookup"><span data-stu-id="f7ada-153">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="f7ada-154">Verileri kaydetme</span><span class="sxs-lookup"><span data-stu-id="f7ada-154">Saving data</span></span>

<span data-ttu-id="f7ada-155">Veri oluşturulur, silinmiş ve varlık sınıfların örneklerini kullanarak veritabanında değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="f7ada-155">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="f7ada-156">Kod aşağıdaki sabit kodlanmış örneği (Bu durumda sahte veriler), Web API denetleyicilerinin gibi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ada-156">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="f7ada-157">ASP.NET Core ve Web API denetleyicilerinin bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="f7ada-157">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="f7ada-158">ASP.NET Core kutu dışı bağımlılık ekleme (dı) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ada-158">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="f7ada-159">İsterseniz, tercih edilen IOC kapsayıcı ASP.NET Core altyapısını ekleyebilirsiniz ancak bir üçüncü taraf denetimi tersine çevirme (IOC) kapsayıcı ayarlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f7ada-159">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="f7ada-160">Bu durumda, doğrudan gerekli EF DBContext veya denetleyicisi Oluşturucusu aracılığıyla ek depoları ekleyemezsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-160">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="f7ada-161">Örnekte `CatalogController` sınıfı, biz injecting bir nesnenin `CatalogContext` yazın diğer nesneler arasında artı `CatalogController()` Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="f7ada-161">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="f7ada-162">DbContext sınıf kaydı hizmetin IOC kapsayıcı içine Web API projesinde ayarlamak için önemli bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-162">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="f7ada-163">Bu nedenle, genellikle yaptığınız `Startup` çağırarak sınıfı `services.AddDbContext<DbContext>()` yönteminin içinde `ConfigureServices()` yöntemi, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="f7ada-163">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="f7ada-164">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f7ada-164">Additional resources</span></span>

-   <span data-ttu-id="f7ada-165">**Veri sorgulama**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="f7ada-165">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="f7ada-166">**Verileri kaydetme**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="f7ada-166">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="f7ada-167">Docker kapsayıcıları tarafından kullanılan DB bağlantı dizesi ve ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f7ada-167">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="f7ada-168">ASP.NET Core ayarları kullanmak ve ConnectionString özelliğini settings.json dosyanıza aşağıdaki örnekte gösterildiği gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7ada-168">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="f7ada-169">Settings.json dosyası ConnectionString özelliği için veya başka bir özellik için varsayılan değerleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-169">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="f7ada-170">Ancak, bu özellikleri Docker kullanırken, docker compose.override.yml dosyasında belirlediğiniz ortam değişkenleri değerlerle geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-170">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="f7ada-171">Bu Docker bunları işletim sistemi ortam değişkenleri olarak sizin için ayarlamanız şekilde, docker-compose.yml veya docker compose.override.yml dosyalarından, bu ortam değişkenleri aşağıdaki docker compose.override.yml dosyasında (bağlantı gösterildiği gibi başlatabilir Bu örnekte, dize ve diğer satırlar sarmalama, ancak bunu kendi kod dosyasında kaydırılacak).</span><span class="sxs-lookup"><span data-stu-id="f7ada-171">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own code file).</span></span>

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

<span data-ttu-id="f7ada-172">Çözüm düzeyinde docker-compose.yml dosyaları yalnızca proje veya mikro hizmet düzeyi, ancak daha da yapılandırma dosyaları ancak docker-compose dosyalarıyla adresindeki bildirilen ortam değişkenleri geçersiz kılarsanız daha da güvenli çok daha esnektir değil değerleri, dağıtım araçlarından VSTS Docker dağıtım görevleri gibi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f7ada-172">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from VSTS Docker deployment tasks.</span></span> 

<span data-ttu-id="f7ada-173">Son olarak, bu değeri kodunuzdan yapılandırmayı kullanarak alabileceğiniz\["ConnectionString"\]ConfigureServices yöntemi bir önceki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f7ada-173">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="f7ada-174">Ancak, üretim ortamları için başka bir yolu Gezgini bağlantı dizeleri gibi parolaları depolamak nasıl isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ada-174">However, for production environments, you might want to explorer additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="f7ada-175">Genellikle, yönetilecek, seçilen orchestrator tarafından ile yapabileceğiniz gibi [Docker Swarm gizli Yönetim](https://docs.docker.com/engine/swarm/secrets/).</span><span class="sxs-lookup"><span data-stu-id="f7ada-175">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="f7ada-176">ASP.NET Web API uygulama sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7ada-176">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="f7ada-177">İş gereksinimleri değişirken kaynakların yeni koleksiyonları eklenebilir, kaynakları arasındaki ilişkileri değişebilir ve veri kaynaklarında yapısını dayanıklıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-177">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="f7ada-178">Yeni gereksinimleri işlemek için bir Web API güncelleştirme görece basit bir işlemdir, ancak bu değişiklikleri Web API'sini kullanan istemci uygulamaları üzerinde sahip olacağı etkilerini dikkate almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-178">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="f7ada-179">Tasarlama ve bir Web API Uygulama geliştirici bu API üzerinde tam denetime sahip olsa da, geliştirici aynı derecede uzaktan işletim üçüncü taraf kuruluşlar tarafından oluşturulan istemci uygulamaları denetime sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f7ada-179">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="f7ada-180">Sürüm oluşturma, sunar kaynaklarını ve Özellikler belirtmek bir Web API sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7ada-180">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="f7ada-181">Bir istemci uygulaması sonra bir özellik veya kaynak belirli bir sürümünü istekleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ada-181">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="f7ada-182">Sürüm oluşturma uygulamak için birçok yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="f7ada-182">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="f7ada-183">URI sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7ada-183">URI versioning</span></span>

-   <span data-ttu-id="f7ada-184">Sorgu dizesi sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7ada-184">Query string versioning</span></span>

-   <span data-ttu-id="f7ada-185">Üstbilgi sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7ada-185">Header versioning</span></span>

<span data-ttu-id="f7ada-186">Sorgu dizesi ve URI sürüm basit uygulamak markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-186">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="f7ada-187">Üstbilgi sürüm iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-187">Header versioning is a good approach.</span></span> <span data-ttu-id="f7ada-188">Ancak, üstbilgi sürüm olarak açık ve URI sürüm olarak kolay.</span><span class="sxs-lookup"><span data-stu-id="f7ada-188">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="f7ada-189">URL sürüm en basit ve en açık olduğundan, eShopOnContainers örnek uygulama URI sürüm kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-189">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="f7ada-190">EShopOnContainers örnek uygulama olduğu gibi URI sürüm ile Web API değiştirmek veya kaynakları, şema değiştirme her zaman, bir sürüm numarası için her kaynak için URI ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7ada-190">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="f7ada-191">Varolan URI, uygun kaynaklar istenen sürümüyle eşleşen şemanın dönmeden önce gibi çalışmaya devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-191">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="f7ada-192">Aşağıdaki kod örneğinde gösterildiği gibi sürüm rota özniteliğinin sürüm URI açık hale getirir Web API kullanılarak ayarlanabilir (Bu durumda v1).</span><span class="sxs-lookup"><span data-stu-id="f7ada-192">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="f7ada-193">Bu sürüm oluşturma mekanizması basittir ve uygun uç noktasına istek yönlendirme sunucusu bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-193">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="f7ada-194">Ancak, daha karmaşık bir sürüm oluşturma ve REST kullanırken en iyi yöntemi için iletilir kullanın ve uygulamak [HATEOAS (köprü metni olarak uygulama altyapısı durumu)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="f7ada-194">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f7ada-195">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f7ada-195">Additional resources</span></span>

-   <span data-ttu-id="f7ada-196">**Scott Hanselman. Kolay ASP.NET Core RESTful Web API'si sürüm oluşturma**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="f7ada-196">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="f7ada-197">**Sürüm oluşturma bir RESTful web API'si**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span><span class="sxs-lookup"><span data-stu-id="f7ada-197">**Versioning a RESTful web API**
[*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span></span>

-   <span data-ttu-id="f7ada-198">**Roy Fielding. Sürüm oluşturma, iletilir ve REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="f7ada-198">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="f7ada-199">Oluşturma Swagger açıklama meta verilerini, ASP.NET çekirdek Web API</span><span class="sxs-lookup"><span data-stu-id="f7ada-199">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="f7ada-200">[Swagger](http://swagger.io/) olan yaygın olarak kullanılan açık kaynak framework tasarımı, yapı, belge yardımcı olan bir büyük ekosistemi araçları tarafından desteklenen ve RESTful API'lerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="f7ada-200">[Swagger](http://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="f7ada-201">API tanımı meta verileri etki alanı için standart durumundadır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-201">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="f7ada-202">Mikro hizmet, veri tabanlı mikro veya daha fazla etki alanı tabanlı mikro (aşağıdaki bölümde açıklandığı gibi) Gelişmiş herhangi bir tür ile Swagger açıklama meta verileri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-202">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="f7ada-203">Swagger Kalp API açıklama meta veriler JSON veya YAML dosyasında Swagger belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-203">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="f7ada-204">Belirtimi tüm kaynakları ve işlemleri hem bir biçimde İnsan ve machine readable kolay geliştirme, bulma ve tümleştirme için ayrıntılı API'nizi RESTful sözleşmesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7ada-204">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="f7ada-205">Belirtimi OpenAPI belirtimi'nın (OAS) temelini ve RESTful arabirimlerinden tanımlanan şekilde standart hale getirmek için bir açık, saydam ve işbirliği topluluğuna geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-205">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="f7ada-206">Belirtimi nasıl bir hizmeti bulunan ve nasıl yeteneklerini anladım yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7ada-206">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="f7ada-207">Daha fazla bilgi için bir web Düzenleyicisi'ni ve Swagger belirtimleri Spotify, Uber, boşluk ve Microsoft, gibi şirketlerden örnekleri dahil olmak üzere Swagger sitesine bakın (<http://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="f7ada-207">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<http://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="f7ada-208">Swagger neden kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f7ada-208">Why use Swagger?</span></span>

<span data-ttu-id="f7ada-209">API için Swagger meta verileri oluşturmak için nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f7ada-209">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="f7ada-210">**Otomatik olarak kullanabilir ve Apı'lerinizi tümleştirmek diğer ürünleri yeteneği**.</span><span class="sxs-lookup"><span data-stu-id="f7ada-210">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="f7ada-211">Ürünler onlarca ve [ticari Araçları](http://swagger.io/commercial-tools/) ve birçok [kitaplıklarını ve çerçevelerini](http://swagger.io/open-source-integrations/) Swagger destekler.</span><span class="sxs-lookup"><span data-stu-id="f7ada-211">Dozens of products and [commercial tools](http://swagger.io/commercial-tools/) and many [libraries and frameworks](http://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="f7ada-212">Microsoft, üst düzey ürünleri ve otomatik olarak aşağıdaki gibi Swagger tabanlı API'ler tüketebileceği araçlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f7ada-212">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="f7ada-213">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="f7ada-213">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="f7ada-214">.NET istemci sınıfları Swagger çağırmak için otomatik olarak oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-214">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="f7ada-215">CLI üzerinden bu aracı kullanılabilir ve GUI aracılığıyla kolay kullanım için de Visual Studio ile tümleştirir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-215">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="f7ada-216">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="f7ada-216">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="f7ada-217">Otomatik olarak [kullanın ve API'nizi tümleştirme](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) üst düzey bir Microsoft Flow akışına olmadan programlama gerekli niteliklere.</span><span class="sxs-lookup"><span data-stu-id="f7ada-217">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="f7ada-218">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="f7ada-218">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="f7ada-219">Otomatik olarak API öğesinden tüketebileceği [PowerApps mobil uygulamaları](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) ile oluşturulan [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), gerekli hiçbir programlama becerilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="f7ada-219">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="f7ada-220">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="f7ada-220">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="f7ada-221">Otomatik olarak [kullanın ve Azure App Service Logic uygulamaya API'nizi tümleştirme](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), gerekli herhangi bir programlama becerilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="f7ada-221">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="f7ada-222">**API belgelerine otomatik olarak oluşturma yeteneği**.</span><span class="sxs-lookup"><span data-stu-id="f7ada-222">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="f7ada-223">Mikro hizmet tabanlı karmaşık uygulamalar gibi büyük ölçekli RESTful API'lerini oluşturduğunuzda, istek ve yanıt yükleri kullanılır farklı veri modelleri ile çok sayıda uç noktaları ele almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-223">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="f7ada-224">API ve benimseme geliştiriciler tarafından başarısı için uygun belgeleri olması ve Swagger ile aldıkça düz bir API Gezgini sahip anahtardır.</span><span class="sxs-lookup"><span data-stu-id="f7ada-224">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="f7ada-225">Swagger ait meta verileri ne Microsoft Flow, PowerApps ve Azure mantıksal uygulamaları API'leri kullanan ve kendilerine bağlanması nasıl anlamak için kullandığınız yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-225">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="f7ada-226">API Swagger meta verileri oluşturma Swashbuckle NuGet paketi ile otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="f7ada-226">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="f7ada-227">Swagger meta verilerde el ile (JSON veya YAML dosyası) oluşturma can sıkıcı iş olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-227">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="f7ada-228">Ancak, ASP.NET Web API hizmetlerinin API bulma kullanarak otomatik hale getirebilir [Swashbuckle NuGet paketi](http://aka.ms/swashbuckledotnetcore) dinamik olarak Swagger API'si meta verileri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f7ada-228">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="f7ada-229">Swashbuckle, ASP.NET Web API projeleri için Swagger meta verileri otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7ada-229">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="f7ada-230">ASP.NET Core Web API projeleri ve geleneksel ASP.NET Web API ve Azure API uygulaması, Azure mobil uygulaması, ASP Azure Service Fabric mikro gibi diğer tüm özellik destekler.</span><span class="sxs-lookup"><span data-stu-id="f7ada-230">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="f7ada-231">Ayrıca, kapsayıcılarında olarak başvuru uygulaması için Dağıtılmış düz Web API destekler.</span><span class="sxs-lookup"><span data-stu-id="f7ada-231">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="f7ada-232">Swashbuckle birleştirir API'si Gezgini ve Swagger veya [swagger kullanıcı arabirimi](https://github.com/swagger-api/swagger-ui) zengin bulma ve belgeleri API tüketicileriniz için deneyimi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="f7ada-232">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="f7ada-233">Kendi Swagger meta verileri Oluşturucu Altyapısı'na ek olarak, Swashbuckle swagger Swashbuckle yüklendikten sonra onu otomatik olarak hizmet verecektir yukarı kullanıcı arabirimi, katıştırılmış bir sürümünü de içerir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-233">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="f7ada-234">Başka bir deyişle, API'nizi iyi bulma API'nizi kullanmak için geliştiricilere yardımcı olmak için kullanıcı Arabirimi ile tamamlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-234">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="f7ada-235">Bu otomatik olarak, API'nizi oluşturmaya odaklanmanıza olanak tanıyan üretildiği için çok küçük miktarda kod ve bakım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-235">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="f7ada-236">Sonucun API'si Gezgini için Şekil 8-8 gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="f7ada-236">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="f7ada-237">**Şekil 8-8**.</span><span class="sxs-lookup"><span data-stu-id="f7ada-237">**Figure 8-8**.</span></span> <span data-ttu-id="f7ada-238">Swashbuckle API'si Gezgini Swagger meta verilerini temel — eShopOnContainers mikro hizmet Kataloğu</span><span class="sxs-lookup"><span data-stu-id="f7ada-238">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="f7ada-239">API explorer en önemli şey burada değil.</span><span class="sxs-lookup"><span data-stu-id="f7ada-239">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="f7ada-240">Kendisini Swagger meta verilerde açıklayan bir Web API oluşturduktan sonra API birçok platformda hedefleyebilirsiniz istemci proxy sınıfı kod oluşturucuları dahil olmak üzere Swagger tabanlı Araçları'ndan, sorunsuz bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-240">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="f7ada-241">Örneğin, söz edildiği gibi [AutoRest](https://github.com/Azure/AutoRest) otomatik olarak .NET istemci sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7ada-241">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="f7ada-242">Ancak ek araçlar [swagger codegen](https://github.com/swagger-api/swagger-codegen) kod oluşturma API İstemci kitaplıkları, sunucu saplamalar ve belgeleri otomatik olarak izin veren öğeler de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-242">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="f7ada-243">Şu anda Swashbuckle iki üst düzey meta paket altındaki çeşitli iç NuGet paketlerini oluşur [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) sürümü 1.0.0 veya ASP.NET Core uygulamaları daha yeni.</span><span class="sxs-lookup"><span data-stu-id="f7ada-243">Currently, Swashbuckle consists of two several internal NuGet packages under the high-level meta- package [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) version 1.0.0 or later for ASP.NET Core applications.</span></span>

<span data-ttu-id="f7ada-244">Web API projesinde bu NuGet paketleri yükledikten sonra aşağıdaki kodu olduğu gibi başlangıç sınıftaki Swagger yapılandırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="f7ada-244">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

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

<span data-ttu-id="f7ada-245">Bunu yaptıktan sonra uygulamanızı başlatın ve bu benzer URL'ler kullanarak aşağıdaki Swagger JSON ve kullanıcı Arabirimi uç noktaları göz atın:</span><span class="sxs-lookup"><span data-stu-id="f7ada-245">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

<span data-ttu-id="f7ada-246">Daha önce oluşturulan kullanıcı arabirimini http:// URL için Swashbuckle tarafından oluşturulan gördüğünüz&lt;kök URL'si bilgisayarınızı &gt; /swagger/kullanıcı arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f7ada-246">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="f7ada-247">Şekil 8-9'da herhangi bir API yöntemi test nasıl de görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ada-247">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="f7ada-248">**Şekil 8-9**.</span><span class="sxs-lookup"><span data-stu-id="f7ada-248">**Figure 8-9**.</span></span> <span data-ttu-id="f7ada-249">Swashbuckle katalog/öğeleri API yöntemi sınama UI</span><span class="sxs-lookup"><span data-stu-id="f7ada-249">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="f7ada-250">Şekil 8-10 eShopOnContainers mikro oluşturulan Swagger JSON meta verileri gösterir (olduğu Araçları altında kullanın) olduğunda, isteği &lt;kök URL'si bilgisayarınızı&gt;/swagger/v1/swagger.json kullanarak [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="f7ada-250">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="f7ada-251">**Şekil 8-10**.</span><span class="sxs-lookup"><span data-stu-id="f7ada-251">**Figure 8-10**.</span></span> <span data-ttu-id="f7ada-252">Swagger JSON meta verileri</span><span class="sxs-lookup"><span data-stu-id="f7ada-252">Swagger JSON metadata</span></span>

<span data-ttu-id="f7ada-253">Bu basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-253">It is that simple.</span></span> <span data-ttu-id="f7ada-254">Ve otomatik olarak oluşturulduğundan, API için daha fazla işlevsellik eklediğinizde, Swagger meta verileri büyüyecektir.</span><span class="sxs-lookup"><span data-stu-id="f7ada-254">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f7ada-255">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f7ada-255">Additional resources</span></span>

-   <span data-ttu-id="f7ada-256">**ASP.NET Web API Yardım Swagger kullanarak sayfaları**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="f7ada-256">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f7ada-257">[Önceki] (mikro hizmet-uygulama-design.md) [sonraki] (çok-container-uygulamalar-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="f7ada-257">[Previous] (microservice-application-design.md) [Next] (multi-container-applications-docker-compose.md)</span></span>
