---
title: "Bir basit veri güdümlü CRUD mikro hizmet oluşturma"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Bir basit veri güdümlü CRUD mikro hizmet oluşturma"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b814d344f2c78e7cf57f9e2896cf1d6b52db38d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="d6a8c-104">Bir basit veri güdümlü CRUD mikro hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6a8c-104">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="d6a8c-105">Bu bölüm anahatları basit bir oluşturmak için gerçekleştirdiği mikro hizmet oluşturun nasıl okuma, güncelleştirme ve bir veri kaynağında Sil (CRUD) işlemleri.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-105">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="d6a8c-106">Basit bir CRUD mikro hizmet tasarlama</span><span class="sxs-lookup"><span data-stu-id="d6a8c-106">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="d6a8c-107">Bir tasarım açısından bakıldığında, bu tür kapsayıcılı mikro çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-107">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="d6a8c-108">Belki de sorunu çözmek için basit bir işlemdir veya yalnızca bir kavram kanıtı belki de uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-108">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="d6a8c-109">**Şekil 8-4**.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-109">**Figure 8-4**.</span></span> <span data-ttu-id="d6a8c-110">Basit CRUD mikro için iç tasarımı</span><span class="sxs-lookup"><span data-stu-id="d6a8c-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="d6a8c-111">Bu tür bir basit veri sürücüsü hizmet Kataloğu mikro hizmet eShopOnContainers örnek uygulamadan örnektir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="d6a8c-112">Bu tür bir hizmet kendi veri modeli, iş mantığı ve kendi veri erişim kodu için sınıflar içerir tek bir ASP.NET çekirdek Web API projesinde tüm işlevlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="d6a8c-113">Ayrıca, ilgili verilerini (olarak geliştirme ve test amaçları için başka bir kapsayıcı) SQL Server çalıştıran bir veritabanında depolar ancak normal herhangi bir SQL Server ana Şekil 8-5'te gösterildiği gibi de olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="d6a8c-114">**Şekil 8-5**.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-114">**Figure 8-5**.</span></span> <span data-ttu-id="d6a8c-115">Basit veri-güdümlü/CRUD mikro hizmet tasarım</span><span class="sxs-lookup"><span data-stu-id="d6a8c-115">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="d6a8c-116">Bu tür bir hizmet geliştirirken, yalnızca ihtiyacınız [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) ve veri erişimi API veya ORM gibi [Entity Framework Çekirdek](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-116">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="d6a8c-117">Ayrıca üretebilir [Swagger](http://swagger.io/) meta verileri otomatik olarak ile [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) ne hizmetiniz sunar, açıklaması bir sonraki bölümde açıklandığı gibi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-117">You could also generate [Swagger](http://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="d6a8c-118">Tüm bağımlılıklarınızı sahip için SQL Server'ın bir Docker kapsayıcısı içinde geliştirme ortamları için harikadır gibi bir veritabanı sunucusunu çalıştıran ve bir veritabanı bulutta veya şirket içi sağlamak zorunda kalmadan çalışan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-118">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="d6a8c-119">Tümleştirme testleri, bu çok kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-119">This is very convenient when running integration tests.</span></span> <span data-ttu-id="d6a8c-120">Bu yaklaşım ile yüksek kullanılabilirlik genellikle almazsanız olduğundan ancak üretim ortamları için bir veritabanı sunucusu bir kapsayıcıda çalışan, önerilmez.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-120">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="d6a8c-121">Azure'da bir üretim ortamı için Azure SQL DB veya yüksek kullanılabilirlik ve yüksek ölçeklenebilirlik sağlayabilir herhangi bir veritabanı teknolojisini kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-121">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="d6a8c-122">Örneğin, bir NoSQL yaklaşım için DocumentDB seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-122">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="d6a8c-123">Son olarak, Dockerfile ve docker-compose.yml meta veri dosyaları düzenleyerek, bu kapsayıcı görüntüsünü nasıl oluşturulacak yapılandırabileceğiniz — hangi temel görüntü, kullanın, artı tasarım iç ve dış adlar ve TCP bağlantı noktaları gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-123">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="d6a8c-124">ASP.NET Core ile basit bir CRUD mikro hizmet uygulama</span><span class="sxs-lookup"><span data-stu-id="d6a8c-124">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="d6a8c-125">.NET Core ve Visual Studio kullanarak basit bir CRUD mikro hizmet uygulamak için (Linux Docker ana bilgisayarda çalıştırabilmeniz için .NET Core üzerinde çalışan), basit bir ASP.NET çekirdek Web API projesi oluşturarak gösterildiği Şekil 8-6 olarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-125">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="d6a8c-126">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="d6a8c-126">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="d6a8c-127">**Şekil 8-6**.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-127">**Figure 8-6**.</span></span> <span data-ttu-id="d6a8c-128">Visual Studio'da ASP.NET çekirdek Web API projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6a8c-128">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="d6a8c-129">Projesi oluşturduktan sonra Entity Framework API veya diğer API kullanarak tüm diğer Web API projesinde, olduğu gibi MVC denetleyicileri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-129">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="d6a8c-130">EShopOnContainers.Catalog.API projesinde, o mikro hizmet ana bağımlılıkları yalnızca ASP.NET Core kendisi, Entity Framework ve Swashbuckle, olduğunu Şekil 8-7'de gösterildiği gibi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-130">In the eShopOnContainers.Catalog.API project, you can see that the main dependencies for that microservice are just ASP.NET Core itself, Entity Framework, and Swashbuckle, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="d6a8c-131">**Şekil 8-7**.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-131">**Figure 8-7**.</span></span> <span data-ttu-id="d6a8c-132">Basit bir CRUD Web API mikro Hizmet bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="d6a8c-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="d6a8c-133">Entity Framework Çekirdek ile uygulama CRUD Web API Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d6a8c-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="d6a8c-134">Hafif, Genişletilebilir, Entity Framework (EF) çekirdeği olur ve platformlar arası sürümü popüler Entity Framework verilerine erişim teknolojisini.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="d6a8c-135">EF çekirdeği .NET geliştiricilerinin .NET nesneleri kullanarak bir veritabanı ile çalışmak bir nesne ilişkisel Eşleyici (ORM) olur.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="d6a8c-136">Veritabanını bir kapsayıcıda Linux Docker görüntüsü için SQL Server ile çalıştığı için katalog mikro hizmet EF ve SQL Server sağlayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="d6a8c-137">Ancak, veritabanı içine Windows Şirket içi veya Azure SQL DB gibi herhangi bir SQL sunucusuna dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="d6a8c-138">Değiştirmek için gereken tek şey, ASP.NET Web API mikro hizmet bağlantı dizesinde.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="add-entity-framework-core-to-your-dependencies"></a><span data-ttu-id="d6a8c-139">Entity Framework Çekirdek, bağımlılıkları için ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-139">Add Entity Framework Core to your dependencies</span></span>

<span data-ttu-id="d6a8c-140">Bu durumda SQL Server ' dan Visual Studio IDE içinde veya NuGet konsolu ile kullanmak istediğiniz veritabanı sağlayıcısı için NuGet paketini yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-140">You can install the NuGet package for the database provider you want to use, in this case SQL Server, from within the Visual Studio IDE or with the NuGet console.</span></span> <span data-ttu-id="d6a8c-141">Aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-141">Use the following command:</span></span>

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a><span data-ttu-id="d6a8c-142">Veri modeli</span><span class="sxs-lookup"><span data-stu-id="d6a8c-142">The data model</span></span>

<span data-ttu-id="d6a8c-143">EF çekirdek ile veri erişim modeli kullanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-143">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="d6a8c-144">Bir model sınıflar ve sorgu ve veri kaydetmenize olanak veren veritabanı, oturumla temsil eden bir türetilmiş bağlamı oluşur.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-144">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="d6a8c-145">Varolan bir veritabanından bir model oluşturmak, el ile veritabanınızı eşleştirmek için bir model kod veya EF geçişler modelinizin dışında bir veritabanı oluşturmak için (ve modelinizi zaman içinde değiştikçe gelişmesi için) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-145">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="d6a8c-146">Katalog mikro hizmet için son yaklaşım kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-146">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="d6a8c-147">Basit bir düz eski CLR nesnesi aşağıdaki kod örneğinde, CatalogItem varlık sınıfı örneği görebilirsiniz ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) varlık sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-147">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public CatalogItem() { }
}
```

<span data-ttu-id="d6a8c-148">Ayrıca veritabanı oturumla temsil eden bir DbContext gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-148">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="d6a8c-149">Katalog mikro hizmet için CatalogContext sınıfı aşağıdaki örnekte gösterildiği gibi DbContext temel sınıfından türetilen:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-149">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="d6a8c-150">DbContext uygulamasında ek kod olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-150">You can have additional code in the DbContext implementation.</span></span> <span data-ttu-id="d6a8c-151">Örneğin, örnek uygulamasında OnModelCreating metodunun örnek verileri veritabanına erişmeye çalıştığında ilk kez otomatik olarak doldurur CatalogContext sınıfında sahibiz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-151">For example, in the sample application, we have an OnModelCreating method in the CatalogContext class that automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="d6a8c-152">Bu yöntem, tanıtım veriler için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-152">This method is useful for demo data.</span></span> <span data-ttu-id="d6a8c-153">Diğer birçok nesne/veritabanı varlık eşlemeleri özelleştirmek için OnModelCreating metodunun kullanabilirsiniz [EF genişletilebilirlik noktaları](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-153">You can also use the OnModelCreating method to customize object/database entity mappings with many other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

<span data-ttu-id="d6a8c-154">Daha fazla OnModelCreating içinde ayrıntılarını görebilirsiniz [Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama](#implementing_infrastructure_persistence) bölümde daha sonra bu kitap.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-154">You can see further details about OnModelCreating in the [Implementing the infrastructure-persistence layer with Entity Framework Core](#implementing_infrastructure_persistence) section later in this book.</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="d6a8c-155">Web API denetleyicilerinin verileri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="d6a8c-155">Querying data from Web API controllers</span></span>

<span data-ttu-id="d6a8c-156">Varlık sınıfları, genellikle aşağıdaki örnekte gösterildiği gibi dil tümleşik sorgu (LINQ), kullanarak veritabanından alınır:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-156">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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
        _catalogIntegrationEventService = catalogIntegrationEventService ??
           throw new ArgumentNullException(nameof(catalogIntegrationEventService));
        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
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

##### <a name="saving-data"></a><span data-ttu-id="d6a8c-157">Verileri kaydetme</span><span class="sxs-lookup"><span data-stu-id="d6a8c-157">Saving data</span></span>

<span data-ttu-id="d6a8c-158">Veri oluşturulur, silinmiş ve varlık sınıfların örneklerini kullanarak veritabanında değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-158">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="d6a8c-159">Kod aşağıdaki sabit kodlanmış örneği (Bu durumda sahte veriler), Web API denetleyicilerinin gibi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-159">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="d6a8c-160">ASP.NET Core ve Web API denetleyicilerinin bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="d6a8c-160">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="d6a8c-161">ASP.NET Core kutu dışı bağımlılık ekleme (dı) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-161">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="d6a8c-162">İsterseniz, tercih edilen IOC kapsayıcı ASP.NET Core altyapısını ekleyebilirsiniz ancak bir üçüncü taraf denetimi tersine çevirme (IOC) kapsayıcı ayarlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-162">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="d6a8c-163">Bu durumda, doğrudan gerekli EF DBContext veya denetleyicisi Oluşturucusu aracılığıyla ek depoları ekleyemezsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-163">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="d6a8c-164">Örnekte CatalogController sınıfının, biz CatalogContext türünde bir nesne ve diğer nesneleri CatalogController Oluşturucusu aracılığıyla injecting.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-164">In the example above of the CatalogController class, we are injecting an object of CatalogContext type plus other objects through the CatalogController constructor.</span></span>

<span data-ttu-id="d6a8c-165">DbContext sınıf kaydı hizmetin IOC kapsayıcı içine Web API projesinde ayarlamak için önemli bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-165">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="d6a8c-166">Genellikle başlangıç sınıfında Hizmetleri çağırarak bunu. Aşağıdaki örnekte gösterildiği gibi ConfigureServices yöntemi içinde AddDbContext yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-166">You typically do so in the Startup class by calling the services.AddDbContext method inside the ConfigureServices method, as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
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

### <a name="additional-resources"></a><span data-ttu-id="d6a8c-167">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d6a8c-167">Additional resources</span></span>

-   <span data-ttu-id="d6a8c-168">**Veri sorgulama**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="d6a8c-168">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="d6a8c-169">**Verileri kaydetme**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="d6a8c-169">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="d6a8c-170">Docker kapsayıcıları tarafından kullanılan DB bağlantı dizesi ve ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="d6a8c-170">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="d6a8c-171">ASP.NET Core ayarları kullanmak ve ConnectionString özelliğini settings.json dosyanıza aşağıdaki örnekte gösterildiği gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-171">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="d6a8c-172">Settings.json dosyası ConnectionString özelliği için veya başka bir özellik için varsayılan değerleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-172">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="d6a8c-173">Ancak, bu özellikleri docker compose.override.yml dosyasında belirttiğiniz ortam değişkenlerinin değerlerini tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-173">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file.</span></span>

<span data-ttu-id="d6a8c-174">Bu Docker bunları işletim sistemi ortam değişkenleri olarak sizin için ayarlamanız şekilde, docker-compose.yml veya docker compose.override.yml dosyalarından, bu ortam değişkenleri aşağıdaki docker compose.override.yml dosyasında (bağlantı gösterildiği gibi başlatabilir Bu örnekte, dize ve diğer satırlar sarmalama, ancak bunu kendi dosyasında kaydırılacak).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-174">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    - ExternalCatalogBaseUrl=http://10.0.75.1:5101
    #- ExternalCatalogBaseUrl=http://dockerhoststaging.westus.cloudapp.azure.com:5101
  
  ports:
    - "5101:5101"
```

<span data-ttu-id="d6a8c-175">Çözüm düzeyinde docker-compose.yml dosyaları yalnızca proje veya mikro hizmet düzeyinde yapılandırma dosyalarını daha esnek değildir, ancak aynı zamanda daha güvenli.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-175">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure.</span></span> <span data-ttu-id="d6a8c-176">Göz önünde bulundurun mikro hizmet yapı Docker görüntüleri docker-compose.yml içermeyen dosyaları, yalnızca ikili dosyaları ve yapılandırma dosyalarını Dockerfile dahil olmak üzere her mikro hizmet için.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-176">Consider that the Docker images that you build per microservice do not contain the docker-compose.yml files, only binary files and configuration files for each microservice, including the Dockerfile.</span></span> <span data-ttu-id="d6a8c-177">Ancak docker-compose.yml dosyası uygulamanız ile birlikte dağıtılmış durumda değil; Yalnızca dağıtım sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-177">But the docker-compose.yml file is not deployed along with your application; it is used only at deployment time.</span></span> <span data-ttu-id="d6a8c-178">Bu nedenle, ortam değişkenleri değerlerini (hatta değerleri şifrelemeden) bu docker-compose.yml dosyalarını yerleştirme kodunuzu ile dağıtılan normal .NET yapılandırma dosyalarında bu değerleri yerleştirme değerinden daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-178">Therefore, placing environment variables values in those docker-compose.yml files (even without encrypting the values) is more secure than placing those values in regular .NET configuration files that are deployed with your code.</span></span>

<span data-ttu-id="d6a8c-179">Son olarak, bu değeri kodunuzdan yapılandırmayı kullanarak alabileceğiniz\["ConnectionString"\]ConfigureServices yöntemi bir önceki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-179">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="d6a8c-180">Ancak, üretim ortamları için başka bir yolu Gezgini bağlantı dizeleri gibi parolaları depolamak nasıl isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-180">However, for production environments, you might want to explorer additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="d6a8c-181">Genellikle, yönetilecek, seçilen orchestrator tarafından ile yapabileceğiniz gibi [Docker Swarm gizli Yönetim](https://docs.docker.com/engine/swarm/secrets/).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-181">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="d6a8c-182">ASP.NET Web API uygulama sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6a8c-182">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="d6a8c-183">İş gereksinimleri değişirken kaynakların yeni koleksiyonları eklenebilir, kaynakları arasındaki ilişkileri değişebilir ve veri kaynaklarında yapısını dayanıklıdır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-183">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="d6a8c-184">Yeni gereksinimleri işlemek için bir Web API güncelleştirme görece basit bir işlemdir, ancak bu değişiklikleri Web API'sini kullanan istemci uygulamaları üzerinde sahip olacağı etkilerini dikkate almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-184">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="d6a8c-185">Tasarlama ve bir Web API Uygulama geliştirici bu API üzerinde tam denetime sahip olsa da, geliştirici aynı derecede uzaktan işletim üçüncü taraf kuruluşlar tarafından oluşturulan istemci uygulamaları denetime sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-185">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="d6a8c-186">Sürüm oluşturma, sunar kaynaklarını ve Özellikler belirtmek bir Web API sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-186">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="d6a8c-187">Bir istemci uygulaması sonra bir özellik veya kaynak belirli bir sürümünü istekleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-187">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="d6a8c-188">Sürüm oluşturma uygulamak için birçok yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-188">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="d6a8c-189">URI sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6a8c-189">URI versioning</span></span>

-   <span data-ttu-id="d6a8c-190">Sorgu dizesi sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6a8c-190">Query string versioning</span></span>

-   <span data-ttu-id="d6a8c-191">Üstbilgi sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6a8c-191">Header versioning</span></span>

<span data-ttu-id="d6a8c-192">Sorgu dizesi ve URI sürüm basit uygulamak markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-192">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="d6a8c-193">Üstbilgi sürüm iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-193">Header versioning is a good approach.</span></span> <span data-ttu-id="d6a8c-194">Ancak, üstbilgi sürüm olarak açık ve URI sürüm olarak kolay.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-194">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="d6a8c-195">URL sürüm en basit ve en açık olduğundan, eShopOnContainers örnek uygulama URI sürüm kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-195">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="d6a8c-196">EShopOnContainers örnek uygulama olduğu gibi URI sürüm ile Web API değiştirmek veya kaynakları, şema değiştirme her zaman, bir sürüm numarası için her kaynak için URI ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-196">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="d6a8c-197">Varolan URI, uygun kaynaklar istenen sürümüyle eşleşen şemanın dönmeden önce gibi çalışmaya devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-197">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="d6a8c-198">Aşağıdaki kod örneğinde gösterildiği gibi sürüm rota özniteliğinin sürüm URI açık hale getirir Web API kullanılarak ayarlanabilir (Bu durumda v1).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-198">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="d6a8c-199">Bu sürüm oluşturma mekanizması basittir ve uygun uç noktasına istek yönlendirme sunucusu bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-199">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="d6a8c-200">Ancak, daha karmaşık bir sürüm oluşturma ve REST kullanırken en iyi yöntemi için iletilir kullanın ve uygulamak [HATEOAS (köprü metni olarak uygulama altyapısı durumu)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-200">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d6a8c-201">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d6a8c-201">Additional resources</span></span>

-   <span data-ttu-id="d6a8c-202">**Scott Hanselman. ASP.NET Core RESTful Web API'si sürüm kolaylaştırılmış**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="d6a8c-202">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="d6a8c-203">**Sürüm oluşturma bir RESTful web API'si**</span><span class="sxs-lookup"><span data-stu-id="d6a8c-203">**Versioning a RESTful web API**</span></span>

    [<span data-ttu-id="d6a8c-204">*https://docs.microsoft.com/Azure/Architecture/Best-Practices/api-Design#Versioning-a-RESTful-Web-api*</span><span class="sxs-lookup"><span data-stu-id="d6a8c-204">*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   <span data-ttu-id="d6a8c-205">**Roy Fielding. Sürüm oluşturma, iletilir ve REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="d6a8c-205">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="d6a8c-206">Oluşturma Swagger açıklama meta verilerini, ASP.NET çekirdek Web API</span><span class="sxs-lookup"><span data-stu-id="d6a8c-206">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="d6a8c-207">[Swagger](http://swagger.io/) olan yaygın olarak kullanılan açık kaynak framework tasarımı, yapı, belge yardımcı olan bir büyük ekosistemi araçları tarafından desteklenen ve RESTful API'lerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-207">[Swagger](http://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="d6a8c-208">API tanımı meta verileri etki alanı için standart durumundadır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-208">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="d6a8c-209">Mikro hizmet, veri tabanlı mikro veya daha fazla etki alanı tabanlı mikro (aşağıdaki bölümde açıklandığı gibi) Gelişmiş herhangi bir tür ile Swagger açıklama meta verileri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-209">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="d6a8c-210">Swagger Kalp API açıklama meta veriler JSON veya YAML dosyasında Swagger belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-210">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="d6a8c-211">Belirtimi tüm kaynakları ve işlemleri hem bir biçimde İnsan ve machine readable kolay geliştirme, bulma ve tümleştirme için ayrıntılı API'nizi RESTful sözleşmesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-211">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="d6a8c-212">Belirtimi OpenAPI belirtimi'nın (OAS) temelini ve RESTful arabirimlerinden tanımlanan şekilde standart hale getirmek için bir açık, saydam ve işbirliği topluluğuna geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-212">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="d6a8c-213">Belirtimi nasıl bir hizmeti bulunan ve nasıl yeteneklerini anladım yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-213">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="d6a8c-214">Daha fazla bilgi için bir web Düzenleyicisi'ni ve Swagger belirtimleri Spotify, Uber, boşluk ve Microsoft, gibi şirketlerden örnekleri dahil olmak üzere Swagger sitesine bakın (<http://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-214">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<http://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="d6a8c-215">Swagger neden kullanılır?</span><span class="sxs-lookup"><span data-stu-id="d6a8c-215">Why use Swagger?</span></span>

<span data-ttu-id="d6a8c-216">API için Swagger meta verileri oluşturmak için nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-216">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="d6a8c-217">**Otomatik olarak kullanabilir ve Apı'lerinizi tümleştirmek diğer ürünleri yeteneği**.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-217">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="d6a8c-218">Ürünler onlarca ve [ticari Araçları](http://swagger.io/commercial-tools/) ve birçok [kitaplıklarını ve çerçevelerini](http://swagger.io/open-source-integrations/) Swagger destekler.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-218">Dozens of products and [commercial tools](http://swagger.io/commercial-tools/) and many [libraries and frameworks](http://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="d6a8c-219">Microsoft, üst düzey ürünleri ve otomatik olarak aşağıdaki gibi Swagger tabanlı API'ler tüketebileceği araçlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-219">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="d6a8c-220">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-220">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="d6a8c-221">.NET istemci sınıfları Swagger çağırmak için otomatik olarak oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-221">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="d6a8c-222">Bu</span><span class="sxs-lookup"><span data-stu-id="d6a8c-222">This</span></span>

-   <span data-ttu-id="d6a8c-223">Aracı CLI üzerinden kullanılabilir ve GUI aracılığıyla kolay kullanım için de Visual Studio ile tümleştirir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-223">tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="d6a8c-224">[Microsoft Akış](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-224">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="d6a8c-225">Otomatik olarak [kullanın ve API'nizi tümleştirme](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) üst düzey bir Microsoft Flow akışına olmadan programlama gerekli niteliklere.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-225">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="d6a8c-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="d6a8c-227">Otomatik olarak API öğesinden tüketebileceği [PowerApps mobil uygulamaları](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) ile oluşturulan [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), gerekli hiçbir programlama becerilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-227">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="d6a8c-228">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-228">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="d6a8c-229">Otomatik olarak [kullanın ve Azure App Service Logic uygulamaya API'nizi tümleştirme](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), gerekli herhangi bir programlama becerilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-229">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="d6a8c-230">**API belgelerine otomatik olarak oluşturma yeteneği**.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-230">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="d6a8c-231">Mikro hizmet tabanlı karmaşık uygulamalar gibi büyük ölçekli RESTful API'lerini oluşturduğunuzda, istek ve yanıt yükleri kullanılır farklı veri modelleri ile çok sayıda uç noktaları ele almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-231">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="d6a8c-232">API ve benimseme geliştiriciler tarafından başarısı için uygun belgeleri olması ve Swagger ile aldıkça düz bir API Gezgini sahip anahtardır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-232">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="d6a8c-233">Swagger ait meta verileri ne Microsoft Flow, PowerApps ve Azure mantıksal uygulamaları API'leri kullanan ve kendilerine bağlanması nasıl anlamak için kullandığınız yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-233">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="d6a8c-234">API Swagger meta verileri oluşturma Swashbuckle NuGet paketi ile otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="d6a8c-234">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="d6a8c-235">Swagger meta verilerde el ile (JSON veya YAML dosyası) oluşturma can sıkıcı iş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-235">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="d6a8c-236">Ancak, ASP.NET Web API hizmetlerinin API bulma kullanarak otomatik hale getirebilir [Swashbuckle NuGet paketi](http://aka.ms/swashbuckledotnetcore) dinamik olarak Swagger API'si meta verileri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-236">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="d6a8c-237">Swashbuckle, ASP.NET Web API projeleri için Swagger meta verileri otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-237">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="d6a8c-238">ASP.NET Core Web API projeleri ve geleneksel ASP.NET Web API ve Azure API uygulaması, Azure mobil uygulaması, ASP Azure Service Fabric mikro gibi diğer tüm özellik destekler.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-238">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="d6a8c-239">Ayrıca, kapsayıcılarında olarak başvuru uygulaması için Dağıtılmış düz Web API destekler.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-239">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="d6a8c-240">Swashbuckle birleştirir API'si Gezgini ve Swagger veya [swagger kullanıcı arabirimi](https://github.com/swagger-api/swagger-ui) zengin bulma ve belgeleri API tüketicileriniz için deneyimi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-240">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="d6a8c-241">Kendi Swagger meta verileri Oluşturucu Altyapısı'na ek olarak, Swashbuckle swagger Swashbuckle yüklendikten sonra onu otomatik olarak hizmet verecektir yukarı kullanıcı arabirimi, katıştırılmış bir sürümünü de içerir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-241">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="d6a8c-242">Başka bir deyişle, API'nizi iyi bulma API'nizi kullanmak için geliştiricilere yardımcı olmak için kullanıcı Arabirimi ile tamamlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-242">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="d6a8c-243">Bu otomatik olarak, API'nizi oluşturmaya odaklanmanıza olanak tanıyan üretildiği için çok küçük miktarda kod ve bakım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-243">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="d6a8c-244">Sonucun API'si Gezgini için Şekil 8-8 gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-244">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="d6a8c-245">**Şekil 8-8**.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-245">**Figure 8-8**.</span></span> <span data-ttu-id="d6a8c-246">Swashbuckle API'si Gezgini Swagger meta verilerini temel — eShopOnContainers mikro hizmet Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d6a8c-246">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="d6a8c-247">API explorer en önemli şey burada değil.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-247">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="d6a8c-248">Kendisini Swagger meta verilerde açıklayan bir Web API oluşturduktan sonra API birçok platformda hedefleyebilirsiniz istemci proxy sınıfı kod oluşturucuları dahil olmak üzere Swagger tabanlı Araçları'ndan, sorunsuz bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-248">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="d6a8c-249">Örneğin, söz edildiği gibi [AutoRest](https://github.com/Azure/AutoRest) otomatik olarak .NET istemci sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-249">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="d6a8c-250">Ancak ek araçlar [swagger codegen](https://github.com/swagger-api/swagger-codegen) kod oluşturma API İstemci kitaplıkları, sunucu saplamalar ve belgeleri otomatik olarak izin veren öğeler de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-250">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="d6a8c-251">Şu anda iki NuGet paketlerini Swashbuckle oluşur: Swashbuckle.SwaggerGen ve Swashbuckle.SwaggerUi.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-251">Currently, Swashbuckle consists of two NuGet packages: Swashbuckle.SwaggerGen and Swashbuckle.SwaggerUi.</span></span> <span data-ttu-id="d6a8c-252">Eski doğrudan API uygulamasından bir veya daha fazla Swagger belgeleri oluşturmak ve bunları JSON uç noktalar olarak kullanıma sunmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-252">The former provides functionality to generate one or more Swagger documents directly from your API implementation and expose them as JSON endpoints.</span></span> <span data-ttu-id="d6a8c-253">İkinci bir katıştırılmış aracın sürümü, uygulamanız tarafından sunulan ve API'nizi açıklamak için tarafından oluşturulan Swagger belge gücü swagger kullanıcı arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-253">The latter provides an embedded version of the swagger-ui tool that can be served by your application and powered by the generated Swagger documents to describe your API.</span></span> <span data-ttu-id="d6a8c-254">Ancak, en son sürümlerini Swashbuckle Swashbuckle.AspNetCore metapackage bunlarla sarılır.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-254">However, the latest versions of Swashbuckle wrap these with the Swashbuckle.AspNetCore metapackage.</span></span>

<span data-ttu-id="d6a8c-255">Kullanmanıza gerek .NET Core Web API projeleri için Not [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) sürümü 1.0.0 veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-255">Note that for .NET Core Web API projects, you need to use [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) version 1.0.0 or later.</span></span>

<span data-ttu-id="d6a8c-256">Web API projesinde bu NuGet paketleri yükledikten sonra aşağıdaki kodu olduğu gibi başlangıç sınıftaki Swagger yapılandırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-256">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...
        services.AddSwaggerGen();
        services.ConfigureSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SingleApiVersion(new Swashbuckle.Swagger.Model.Info()
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API",
                TermsOfService = "eShopOnContainers terms of service"
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
            .UseSwaggerUi();
    }
}
```

<span data-ttu-id="d6a8c-257">Bunu yaptıktan sonra uygulamanızı başlatın ve bu benzer URL'ler kullanarak aşağıdaki Swagger JSON ve kullanıcı Arabirimi uç noktaları göz atın:</span><span class="sxs-lookup"><span data-stu-id="d6a8c-257">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

<span data-ttu-id="d6a8c-258">Daha önce oluşturulan kullanıcı arabirimini http:// URL için Swashbuckle tarafından oluşturulan gördüğünüz&lt;kök URL'si bilgisayarınızı &gt; /swagger/kullanıcı arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-258">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="d6a8c-259">Şekil 8-9'da herhangi bir API yöntemi test nasıl de görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-259">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="d6a8c-260">**Şekil 8-9**.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-260">**Figure 8-9**.</span></span> <span data-ttu-id="d6a8c-261">Swashbuckle katalog/öğeleri API yöntemi sınama UI</span><span class="sxs-lookup"><span data-stu-id="d6a8c-261">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="d6a8c-262">Şekil 8-10 eShopOnContainers mikro oluşturulan Swagger JSON meta verileri gösterir (olduğu Araçları altında kullanın) olduğunda, isteği &lt;kök URL'si bilgisayarınızı&gt;/swagger/v1/swagger.json kullanarak [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="d6a8c-262">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="d6a8c-263">**Şekil 8-10**.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-263">**Figure 8-10**.</span></span> <span data-ttu-id="d6a8c-264">Swagger JSON meta verileri</span><span class="sxs-lookup"><span data-stu-id="d6a8c-264">Swagger JSON metadata</span></span>

<span data-ttu-id="d6a8c-265">Bu basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-265">It is that simple.</span></span> <span data-ttu-id="d6a8c-266">Ve otomatik olarak oluşturulduğundan, API için daha fazla işlevsellik eklediğinizde, Swagger meta verileri büyüyecektir.</span><span class="sxs-lookup"><span data-stu-id="d6a8c-266">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d6a8c-267">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d6a8c-267">Additional resources</span></span>

-   <span data-ttu-id="d6a8c-268">**ASP.NET Web API Yardım Swagger sayfalarını kullanarak**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="d6a8c-268">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d6a8c-269">[Önceki] (mikro hizmet-uygulama-design.md) [sonraki] (çok-container-uygulamalar-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="d6a8c-269">[Previous] (microservice-application-design.md) [Next] (multi-container-applications-docker-compose.md)</span></span>
