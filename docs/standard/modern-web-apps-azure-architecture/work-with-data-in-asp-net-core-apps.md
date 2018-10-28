---
title: ASP.NET Core uygulamaları verilerle çalışın
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | ASP.NET Core uygulamalarında verilerle çalışma
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 069bfacd1ae08b5c84d6e304b2f12f18e1eecb22
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49122857"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="e4456-103">ASP.NET Core uygulamaları verilerle çalışma</span><span class="sxs-lookup"><span data-stu-id="e4456-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="e4456-104">"Veri değerli bir şeydir ve sistemler daha uzun süre gider."</span><span class="sxs-lookup"><span data-stu-id="e4456-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="e4456-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="e4456-105">Tim Berners-Lee</span></span>

<span data-ttu-id="e4456-106">Veri erişimi, neredeyse tüm yazılım uygulamanın önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e4456-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="e4456-107">ASP.NET Core, Entity Framework Core (ve Entity Framework 6 de) dahil olmak üzere, veri erişim seçenekleri çeşitli destekler ve tüm .NET veri erişim framework ile çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="e4456-108">Hangisinin kullanılacağını framework verilere seçimi, uygulamanın gereksinimlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4456-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="e4456-109">Bu seçenekler ApplicationCore ve UI projelerindeki özetleyen ve altyapı, uygulama ayrıntılarını kapsüllemek gevşek, test edilebilir yazılım üretmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e4456-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="e4456-110">Entity Framework Core (için ilişkisel veritabanları)</span><span class="sxs-lookup"><span data-stu-id="e4456-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="e4456-111">İlişkisel verilerle çalışmak için gereken yeni bir ASP.NET Core uygulaması yazıyorsanız, Entity Framework Core (EF Core) uygulamanız kendi verilerine erişim için önerilen yöntem olduğu.</span><span class="sxs-lookup"><span data-stu-id="e4456-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="e4456-112">EF Core, .NET geliştiricilerinin nesneleri için ve bir veri kaynağından kalıcı hale getirmek bir nesne ilişkisel eşleyicidir (O/RM) ' dir.</span><span class="sxs-lookup"><span data-stu-id="e4456-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="e4456-113">Bu, çoğu, geliştiriciler genellikle yazmanız gerekirdi veri erişim kodu gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e4456-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="e4456-114">EF çekirdekli ASP.NET Core gibi destek modüler platformlar arası uygulamaları için baştan yazıldı.</span><span class="sxs-lookup"><span data-stu-id="e4456-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="e4456-115">Bir NuGet paketi olarak uygulamanıza ekleyin, başlangıç yapılandırmak ve ihtiyaç duyduğunuz yerde, bağımlılık ekleme isteyin.</span><span class="sxs-lookup"><span data-stu-id="e4456-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="e4456-116">EF Core ile bir SQL Server veritabanını kullanmak için aşağıdaki dotnet CLI komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e4456-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="e4456-117">DotNet paketini Microsoft.EntityFrameworkCore.SqlServer ekleyin</span><span class="sxs-lookup"><span data-stu-id="e4456-117">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="e4456-118">Test etmek için bir Inmemory veri kaynağı için destek eklemek için:</span><span class="sxs-lookup"><span data-stu-id="e4456-118">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="e4456-119">DotNet paketini Microsoft.EntityFrameworkCore.InMemory ekleyin</span><span class="sxs-lookup"><span data-stu-id="e4456-119">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="e4456-120">DbContext</span><span class="sxs-lookup"><span data-stu-id="e4456-120">The DbContext</span></span>

<span data-ttu-id="e4456-121">EF Core ile çalışmak için öğesinin gerekir. <xref:Microsoft.EntityFrameworkCore.DbContext>.</span><span class="sxs-lookup"><span data-stu-id="e4456-121">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="e4456-122">Bu sınıf, uygulamanızın çalışacağı varlık koleksiyonları özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="e4456-122">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="e4456-123">Koleksiyon öğeleri, markalar ve türlerini içeren bir CatalogContext eShopOnWeb örneği içerir:</span><span class="sxs-lookup"><span data-stu-id="e4456-123">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="e4456-124">DbContext DbContextOptions kabul eden bir oluşturucuya sahip olması ve bu bağımsız değişken temel DbContext oluşturucusuna geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-124">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="e4456-125">Yalnızca bir DbContext uygulamanızda sahip olduğunuz, DbContextOptions örneğini geçirebilirsiniz, ancak varsa, birden fazla genel DbContextOptions kullanmalısınız unutmayın<T> öğesinde DbContext tür genel parametre olarak geçen türü.</span><span class="sxs-lookup"><span data-stu-id="e4456-125">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="e4456-126">EF Core yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e4456-126">Configuring EF Core</span></span>

<span data-ttu-id="e4456-127">ASP.NET Core uygulamanızı Createservicereplicalisteners() yönteminizi EF Core genellikle yapılandıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="e4456-127">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="e4456-128">EF Core yapılandırmasını kolaylaştıran birçok yararlı genişletme yöntemleri destekleyen bir DbContextOptionsBuilder kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4456-128">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="e4456-129">CatalogContext yapılandırmasında tanımlı bir bağlantı dizesi ile bir SQL Server veritabanını kullanacak şekilde yapılandırmak için Createservicereplicalisteners() için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e4456-129">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="e4456-130">Bellek içi veritabanı kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="e4456-130">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="e4456-131">EF Core oluşturulan bir DbContext alt türü, yüklü ve Createservicereplicalisteners() içinde yapılandırılmış sonra EF Core kullanmaya hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e4456-131">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="e4456-132">DbContext türünüz ihtiyaç duyduğu herhangi bir hizmeti örneğini istek ve yalnızca bir koleksiyonda değilmiş gibi LINQ kullanarak kalıcı varlıklarınızı ile çalışmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4456-132">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="e4456-133">EF Core, verilerinizi almak ve depolamak için SQL sorgulara, LINQ ifade çevirme çalışır.</span><span class="sxs-lookup"><span data-stu-id="e4456-133">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="e4456-134">EF Core bir Günlükçü yapılandırma ve alt düzey ayarlandığında en az sağlama yürütüyordur sorguları gördüğünüz bilgileri, Şekil 8-1'de gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e4456-134">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="e4456-135">Şekil 8-1 konsola oturum EF Core sorguları</span><span class="sxs-lookup"><span data-stu-id="e4456-135">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="e4456-136">Veri depolama ve alma</span><span class="sxs-lookup"><span data-stu-id="e4456-136">Fetching and storing Data</span></span>

<span data-ttu-id="e4456-137">EF Core verileri almak için uygun bir özelliğe erişmek ve LINQ sonucu filtrelemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4456-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="e4456-138">LINQ projeksiyonu, sonucu bir türden diğerine dönüştürme gerçekleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4456-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="e4456-139">Aşağıdaki örnek adına göre sıralanmış, kendi etkin özellik tarafından filtrelendi ve bir Selectlistıtem türü öngörülen CatalogBrands alması:</span><span class="sxs-lookup"><span data-stu-id="e4456-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="e4456-140">Hemen bir sorgu yürütmek için ToListAsync çağrısı eklemek için yukarıdaki örnekte önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e4456-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="e4456-141">Aksi takdirde, deyim Iqueryable atar<SelectListItem> brandItems için hangi yürütülmez numaralandırılana kadar.</span><span class="sxs-lookup"><span data-stu-id="e4456-141">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="e4456-142">Artıları ve eksileri Iqueryable sonuçları döndüren yöntemler için vardır.</span><span class="sxs-lookup"><span data-stu-id="e4456-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="e4456-143">Daha fazla değiştirilmesi, ancak operations EF Core çeviremez sorguya eklediyseniz yalnızca çalışma zamanında, oluşan hataları sonucunda ayrıca EF Core de oluşturmak sorgu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4456-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="e4456-144">Herhangi bir filtre veri erişim gerçekleştirme yönteme geçirmek genellikle güvenlidir ve dönüş bir bellek içi koleksiyonu yeniden (örneğin, liste<T>) sonucu.</span><span class="sxs-lookup"><span data-stu-id="e4456-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="e4456-145">EF Core Kalıcılık getirir varlıklardaki değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="e4456-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="e4456-146">İzlenen bir varlığa değişiklikleri kaydetmek için yalnızca varlık getirmek için kullanılan aynı DbContext örneği olduğundan emin DbContext üzerinde SaveChanges yöntemi çağırın gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="e4456-147">Doğrudan ekleme ve kaldırma varlıkları çağrısıyla veritabanı komutlarını çalıştırmak için yeniden SaveChanges uygun olan DB özellik üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="e4456-148">Aşağıdaki örnek, ekleme, güncelleştirme, Kalıcılık varlıkları kaldırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4456-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="e4456-149">EF Core destekler hem zaman uyumlu ve zaman uyumsuz yöntemler getirmeye ve kaydediliyor.</span><span class="sxs-lookup"><span data-stu-id="e4456-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="e4456-150">Web sunucusu iş parçacığı için veri erişim işlemlerinin tamamlanması beklenirken engellenmediğinden emin web uygulamalarında async ve await deseni zaman uyumsuz yöntemlerle kullanmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="e4456-151">İlgili verileri getiriliyor</span><span class="sxs-lookup"><span data-stu-id="e4456-151">Fetching related data</span></span>

<span data-ttu-id="e4456-152">EF Core varlıkları aldığında, veritabanında bu varlıkla doğrudan depolanan tüm özellikler doldurur.</span><span class="sxs-lookup"><span data-stu-id="e4456-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="e4456-153">İlgili varlık listeleri gibi Gezinti özellikleri değil doldurulur ve değerlerine ayarlanmış olabilir null.</span><span class="sxs-lookup"><span data-stu-id="e4456-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="e4456-154">Bu, EF Core ihtiyaç duyduğundan daha fazla veri olduğu, hızlıca istekleri işlemesini ve verimli bir şekilde yanıtlarını döndürmek web uygulamaları için özellikle önemlidir getirip değil sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4456-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="e4456-155">Kullanarak bir varlık ile ilişkiler içerecek şekilde _istekli yükleme_, gösterildiği gibi sorguya dahil etme genişletme yöntemi kullanan özellik belirtin:</span><span class="sxs-lookup"><span data-stu-id="e4456-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="e4456-156">Birden çok ilişki içerebilir ve bu alt ilişkilerini de içerebilir ThenInclude kullanma.</span><span class="sxs-lookup"><span data-stu-id="e4456-156">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="e4456-157">EF Core varlıkların sonuç kümesi almak için tek bir sorgu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e4456-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="e4456-158">İlgili verileri yükleme için başka bir seçenek kullanmaktır _açık yükleme_.</span><span class="sxs-lookup"><span data-stu-id="e4456-158">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="e4456-159">Açık yükleme zaten alınmış bir varlığa, ek verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4456-159">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="e4456-160">Bu veritabanı için ayrı bir istek gerektirdiğinden, veritabanı sayısını en aza indirmeniz gerekir web uygulamaları için önerilmez her istek için yapılan başvurular.</span><span class="sxs-lookup"><span data-stu-id="e4456-160">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="e4456-161">_Yavaş Yükleniyor_ uygulama tarafından başvurulduğu, ilgili verileri otomatik olarak yükleyen bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e4456-161">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="e4456-162">EF Core 2.1 sürümünde Gecikmeli yükleme için destek ekledi.</span><span class="sxs-lookup"><span data-stu-id="e4456-162">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="e4456-163">Yavaş yükleniyor, varsayılan olarak etkin değildir ve yükleme gerektirir `Microsoft.EntityFrameworkCore.Proxies`.</span><span class="sxs-lookup"><span data-stu-id="e4456-163">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="e4456-164">Her web isteğini içinde yapılan ek veritabanı sorguları kullanımını sonuçlanır beri gibi açık yükleme ile yavaş yükleniyor genellikle web uygulamaları için devre dışı bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-164">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="e4456-165">Ne yazık ki, ne zaman gecikmesi küçüktür ve genellikle test etmek için kullanılan veri kümelerinin küçük geliştirme zamanında yavaş çoğunlukla yükleyerek sonucunda ek yükü gözden kaçan gider.</span><span class="sxs-lookup"><span data-stu-id="e4456-165">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="e4456-166">Ancak, daha fazla kullanıcı, daha fazla veri ve daha fazla gecikme, bir üretim ortamında ek veritabanı istekler genellikle kötü performans yavaş yükleniyor ağır kullanan web uygulamaları için neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-166">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="e4456-167">Web uygulamalarında yavaş yükleniyor varlıkları kaçının</span><span class="sxs-lookup"><span data-stu-id="e4456-167">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="resilient-connections"></a><span data-ttu-id="e4456-168">Dayanıklı bağlantıları</span><span class="sxs-lookup"><span data-stu-id="e4456-168">Resilient connections</span></span>

<span data-ttu-id="e4456-169">SQL veritabanları gibi dış kaynaklara bazen kullanılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-169">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="e4456-170">Geçici olarak kullanım dışı kalması durumunda, uygulamalar, bir özel durum oluşturma önlemek için yeniden deneme mantığı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4456-170">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="e4456-171">Bu teknik, genellikle olarak adlandırılır _bağlantı dayanıklılığı_.</span><span class="sxs-lookup"><span data-stu-id="e4456-171">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="e4456-172">Uygulayabileceğiniz, [üstel geri alma ile kendi yeniden deneme](https://docs.microsoft.com/azure/architecture/patterns/retry) maksimum yeniden deneme sayısına ulaşılana kadar bir üssel olarak artan bekleme süresi ile yeniden denemeden tarafından tekniği.</span><span class="sxs-lookup"><span data-stu-id="e4456-172">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="e4456-173">Bu teknik bulut kaynaklarını aralıklı olarak bazı istekler hatasıyla sonuçlanan süresinin kısa süreler için kullanılamıyor olabilir, olgu kapsar.</span><span class="sxs-lookup"><span data-stu-id="e4456-173">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="e4456-174">Azure SQL DB için Entity Framework Core zaten iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4456-174">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="e4456-175">Ancak, EF Core bağlantıları dayanıklı olmasını istiyorsanız, her bir DbContext bağlantı için Entity Framework yürütme stratejisi etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-175">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="e4456-176">Örneğin, aşağıdaki kodu EF Core bağlantı düzeyinde bağlantı başarısız olursa şartıyla dayanıklı SQL bağlantısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4456-176">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30),
            errorNumbersToAdd: null);
        });
    });
}
//...
```

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="e4456-177">Yürütme stratejileri ve BeginTransaction ve birden çok DbContexts kullanarak açık işlemleri</span><span class="sxs-lookup"><span data-stu-id="e4456-177">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="e4456-178">EF Core bağlantıları yeniden deneme etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem yeniden denenebilir kendi işlem olur.</span><span class="sxs-lookup"><span data-stu-id="e4456-178">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="e4456-179">Geçici bir hata oluşursa, her sorgu ve SaveChanges yapılan her çağrı bir birim olarak yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="e4456-179">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="e4456-180">Kodunuzu BeginTransaction'ı kullanarak bir işlem başlatır, ancak bir birim olarak kabul edilmesi için gereken işlemleri kendi grubu tanımladığınız — işlem içinde her şeyi sahip olması toplu geri bir arıza oluşması durumunda.</span><span class="sxs-lookup"><span data-stu-id="e4456-180">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="e4456-181">EF yürütme stratejisi (yeniden deneme ilkesi) kullanılırken, işlem yürütme girişimi ve birden çok DbContexts gelen birkaç SaveChanges bunu aşağıdaki gibi bir özel durum görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e4456-181">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="e4456-182">System.InvalidOperationException: 'SqlServerRetryingExecutionStrategy' yapılandırılmış yürütme stratejisi, kullanıcı tarafından başlatılan işlemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e4456-182">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="e4456-183">İşlem yeniden denenebilir bir birim olarak tüm işlemleri yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4456-183">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="e4456-184">El ile yürütülmesi gereken her şeyi temsil eden bir temsilci ile EF yürütme stratejisi çağırmak için kullanılan çözümüdür.</span><span class="sxs-lookup"><span data-stu-id="e4456-184">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="e4456-185">Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="e4456-185">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="e4456-186">Aşağıdaki kod, bu yaklaşımı uygulamak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e4456-186">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy();
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="e4456-187">İlk DbContext olduğu \_catalogContext ve ikinci DbContext içinde olduğunu \_integrationEventLogService nesne.</span><span class="sxs-lookup"><span data-stu-id="e4456-187">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="e4456-188">Son olarak, eylem olacaktır işleme, birden çok DbContexts ve bir EF yürütme stratejisi kullanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-188">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="e4456-189">Başvuruları – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="e4456-189">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="e4456-190">**EF Core belgeleri**</span><span class="sxs-lookup"><span data-stu-id="e4456-190">**EF Core Docs**</span></span>  
>   <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="e4456-191">**EF Core: İlgili verileri**</span><span class="sxs-lookup"><span data-stu-id="e4456-191">**EF Core: Related Data**</span></span>  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="e4456-192">**ASP.NET uygulamalarında yavaş yükleniyor varlıkları kaçının**</span><span class="sxs-lookup"><span data-stu-id="e4456-192">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="e4456-193">EF Core veya mikro ORM?</span><span class="sxs-lookup"><span data-stu-id="e4456-193">EF Core or micro-ORM?</span></span>

<span data-ttu-id="e4456-194">EF Core Kalıcılık yönetmek için harika bir seçenektir ve çoğunlukla uygulama geliştiricilerin veritabanı ayrıntılarını kapsayan tek bir seçim değil.</span><span class="sxs-lookup"><span data-stu-id="e4456-194">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="e4456-195">Başka bir popüler açık kaynak alternatiftir [Dapper](https://github.com/StackExchange/Dapper), sözde micro-ORM.</span><span class="sxs-lookup"><span data-stu-id="e4456-195">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="e4456-196">Bir mikro ORM basit, tam özellikli aracı veri yapılarını nesneleri eşleştirmek için daha az olur.</span><span class="sxs-lookup"><span data-stu-id="e4456-196">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="e4456-197">Dapper söz konusu olduğunda, tam olarak temel alınan Kapsüllenen sorgular yerine hedefleri performans üzerinde odaklanmanıza tasarımı almak ve verileri güncelleştirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4456-197">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="e4456-198">SQL geliştiriciden soyutlamak değil çünkü Dapper "donanıma yakın" ve tam yazma geliştiricilerinin erişim işlemi için verilen bir veri kullanmak istedikleri sorgular.</span><span class="sxs-lookup"><span data-stu-id="e4456-198">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="e4456-199">EF Core Dapper ayrı, ancak Ayrıca, performansa ekleme sağladığı iki önemli özellikleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="e4456-199">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="e4456-200">İlk LINQ SQL ifadelere çevrilmesi ' dir.</span><span class="sxs-lookup"><span data-stu-id="e4456-200">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="e4456-201">Bu çevirileri önbelleğe alınır, ancak buna rağmen ek yükü ilk kez gerçekleştirmek içinde var.</span><span class="sxs-lookup"><span data-stu-id="e4456-201">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="e4456-202">Böylece (verimli update ifadeleriyle oluşturulabilir) varlıklarda değişiklik izleme saniyedir.</span><span class="sxs-lookup"><span data-stu-id="e4456-202">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="e4456-203">Bu davranış için özel sorgular AsNotTracking uzantısını kullanarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-203">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="e4456-204">EF Core, genellikle çok verimli ve her durumda edilebilir bir performans açısından SQL sorguları da oluşturur, ancak kesin bir sorgu yürütülecek bir denetime ince varsa, özel SQL'de geçirebilirsiniz (veya bir saklı yordamı yürütme) EF kullanma , Çok çekirdek.</span><span class="sxs-lookup"><span data-stu-id="e4456-204">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="e4456-205">Bu durumda, EF Core Dapper hala çok daha iyi ancak çok az.</span><span class="sxs-lookup"><span data-stu-id="e4456-205">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="e4456-206">Bazı performans verileri her olabilir 2016 MSDN makalesi Julie Lerman sunar [Dapper, Entity Framework ve karma uygulamalar](https://msdn.microsoft.com/magazine/mt703432.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4456-206">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="e4456-207">Veri erişim yöntemlerine çeşitli ek performans Kıyaslama veri çubuğunda bulunabilir [Dapper site](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="e4456-207">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="e4456-208">Dapper sözdizimi EF Core'a nasıl değiştiğini görmek için öğelerin listesini almak için aynı yöntemi bu iki sürümünü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e4456-208">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="e4456-209">Dapper ile daha karmaşık nesne grafikler oluşturmak ihtiyacınız varsa, ilişkili sorgu kendiniz (EF Core gibi bir içerme eklemek yerine) yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-209">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="e4456-210">Bu sözdizimi, birden fazla eşleştirilmiş nesne için ayrı satırlara eşlemenize olanak tanıyan çoklu eşleme denilen bir özelliği de dahil olmak üzere çeşitli aracılığıyla desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4456-210">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="e4456-211">Örneğin, bir sınıf Post özelliğiyle sahibi kullanıcı türündeki göz önünde bulundurulduğunda, aşağıdaki SQL tüm gerekli verileri döndürür:</span><span class="sxs-lookup"><span data-stu-id="e4456-211">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="e4456-212">Döndürülen her satır, hem kullanıcı hem de Post veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="e4456-212">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="e4456-213">Kullanıcı verileri kendi Owner özelliği aracılığıyla gönderme verisi eklenmesi gereken aşağıdaki işlevi kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e4456-213">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="e4456-214">İlişkili kullanıcı verileriyle doldurulur bunların sahibi özelliğiyle gönderileri koleksiyonunu döndürmek için tam kod listesi şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="e4456-214">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="e4456-215">Daha az kapsülleme sağladığından, geliştiriciler, verilerin depolanma şeklini hakkında daha fazla bilmeniz Dapper gerektirir nasıl verimli bir şekilde sorgulayın ve bu getirmek için daha fazla kod yazın.</span><span class="sxs-lookup"><span data-stu-id="e4456-215">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="e4456-216">Etkilenir her sorgu modeli, yalnızca yeni bir geçiş (başka bir EF Core özelliği) oluşturma ve/veya tek bir yerde bir DbContext eşleme bilgilerini güncelleştirmek yerine değiştiğinde güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-216">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="e4456-217">Bu sorgular, derleme süresi garantileri değil, sahip, bu nedenle, çalışma zamanında değişikliklere yanıt olarak model veya veritabanı, hataları hızlı bir şekilde algılaması daha zor hale kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-217">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="e4456-218">Bu bileşim lisanslarınıza Dapper son derece hızlı performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4456-218">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="e4456-219">EF Core, çoğu uygulama ve neredeyse tüm uygulamaların belirli kısımlarını çoğu için kabul edilebilir performans sunar.</span><span class="sxs-lookup"><span data-stu-id="e4456-219">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="e4456-220">Bu nedenle, geliştirici üretkenliği faydalarını, performansa daha ağır basar olasılığı düşüktür.</span><span class="sxs-lookup"><span data-stu-id="e4456-220">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="e4456-221">Önbelleğe alınan bir avantaj sorgular, gerçek sorgu yalnızca yürütülebilecek küçük bir yüzdesi görece küçük yapmadan zaman, sorgu performansı farklılıkları tartışmalı.</span><span class="sxs-lookup"><span data-stu-id="e4456-221">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="e4456-222">SQL veya NoSQL</span><span class="sxs-lookup"><span data-stu-id="e4456-222">SQL or NoSQL</span></span>

<span data-ttu-id="e4456-223">Geleneksel olarak, SQL Server gibi ilişkisel veritabanları kalıcı veri depolamayı Market direncin hakim olduğu, ancak bunlar yalnızca çözüm kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="e4456-223">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="e4456-224">Gibi NoSQL veritabanları [MongoDB](https://www.mongodb.com/what-is-mongodb) nesneleri depolamak için farklı bir yaklaşım sunar.</span><span class="sxs-lookup"><span data-stu-id="e4456-224">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="e4456-225">Tabloları ve satırları için nesne eşleme yerine başka bir tüm nesne grafiğinin seri hale getirmek ve sonucu depolamak için bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="e4456-225">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="e4456-226">Bu yaklaşımın avantajları, Basitlik ve performans en azından başlangıçta markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="e4456-226">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="e4456-227">Nesne ilişkisi olan birçok tabloları içinde ayırmak daha bir anahtarla tek serileştirilmiş nesne depolamak kesinlikle basittir ve veritabanından güncelleştirme ve satırları, nesne, son başlatıldığından beri değişmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-227">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="e4456-228">Benzer şekilde, yakalama ve anahtar tabanlı deposundan tek bir nesne seri durumdan çıkarılırken genellikle çok daha hızlı ve daha karmaşık birleştirmelerden veya birden çok veritabanı sorguları tam olarak aynı nesneden ilişkisel bir veritabanı oluşturmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e4456-228">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="e4456-229">Kilitleri veya işlemler ya da sabit bir şema eksikliği NoSQL veritabanları da çok iletilmek için çok büyük veri kümeleri destekleyen birçok makineler arasında ölçeklendirme yapar.</span><span class="sxs-lookup"><span data-stu-id="e4456-229">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="e4456-230">Öte yandan, (bunlar genellikle olarak adlandırılan) NoSQL veritabanları sakıncaları vardır.</span><span class="sxs-lookup"><span data-stu-id="e4456-230">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="e4456-231">İlişkisel veritabanları normalleştirme tutarlılığın ve verilerin yinelenmesini önlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4456-231">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="e4456-232">Bu, toplam veritabanı boyutunu azaltır ve paylaşılan veri güncelleştirmeleri hemen veritabanı kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4456-232">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="e4456-233">Bir ülkenin adı değiştirildiyse, adresi kayıtlarını Update'ten kendilerini gerek avantaj elde edecektir, ilişkisel bir veritabanında bir adres tablosu kimliği, bir ülke tablo başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-233">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="e4456-234">Ancak, bir NoSQL veritabanı adresi ve onun ilişkili ülke birçok depolanan nesne bir parçası olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="e4456-234">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="e4456-235">Ülke adı için bir güncelleştirme gibi tüm nesnelerin yerine tek bir satır güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-235">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="e4456-236">İlişkisel veritabanları, yabancı anahtarlar gibi kuralları zorunlu tutarak ilişkisel bütünlüğü de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4456-236">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="e4456-237">NoSQL veritabanları, bu tür kısıtlamalar verilerini genellikle sunmaz.</span><span class="sxs-lookup"><span data-stu-id="e4456-237">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="e4456-238">Başka bir karmaşıklık NoSQL veritabanları uğraşmanız gerekir, Sürüm ' dir.</span><span class="sxs-lookup"><span data-stu-id="e4456-238">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="e4456-239">Bir nesnenin özelliklerini değiştirdiğinizde depolanırdı geçmiş sürümlerinden seri durumdan mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-239">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="e4456-240">Bu nedenle, bir nesne seri hale getirilmiş (önceki) sürümüne sahip tüm var olan nesneler, yeni şemaya uyacak şekilde güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-240">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="e4456-241">Kavramsal olarak ilişkisel bir veritabanındaki farklı değil, bazen şema değişiklikleri güncelleştirme betikleri gerektirir veya güncelleştirmeleri eşleme.</span><span class="sxs-lookup"><span data-stu-id="e4456-241">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="e4456-242">Ancak değiştirilmelidir girdi sayısı genellikle büyük olup olmadığı için daha fazla çoğaltma verilerinin NoSQL yaklaşım daha.</span><span class="sxs-lookup"><span data-stu-id="e4456-242">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="e4456-243">Birden çok sürümünü nesneleri depolamak için NoSQL veritabanlarında mümkündür, sabit bir şey şema ilişkisel veritabanları genellikle desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e4456-243">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="e4456-244">Ancak, bu durumda uygulama kodunuz nesneleri, karmaşıklık ekleme önceki sürümleri varlığını hesabı gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-244">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="e4456-245">NoSQL veritabanları genellikle mecbur kılmaz [ACID](https://en.wikipedia.org/wiki/ACID), sahip oldukları hem performans ve ölçeklenebilirlik avantajlarını ilişkisel veritabanları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e4456-245">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="e4456-246">Bunlar, son derece büyük veri kümelerini ve depolama normalleştirilmiş tablo yapılardaki için çok uygun olmayan nesneler için uygundur.</span><span class="sxs-lookup"><span data-stu-id="e4456-246">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="e4456-247">Neden tek bir uygulama hem de ilişkisel yararlanamaz ve NoSQL veritabanları, en iyi olduğu her kullanarak uygun bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="e4456-247">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="e4456-248">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="e4456-248">Azure DocumentDB</span></span>

<span data-ttu-id="e4456-249">Azure DocumentDB, şemadan bağımsız veriler bulut tabanlı depolama sunan tam olarak yönetilen bir NoSQL veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="e4456-249">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="e4456-250">DocumentDB hızlı ve tahmin edilebilir performans, yüksek kullanılabilirlik, esnek ölçeklendirme ve küresel dağıtım için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="e4456-250">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="e4456-251">Geliştiriciler, bir NoSQL veritabanı olan rağmen JSON verileri üzerinde zengin ve tanıdık SQL sorgu işlevleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-251">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="e4456-252">DocumentDB tüm kaynaklar JSON belgeleri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="e4456-252">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="e4456-253">Olarak yönetilen kaynakları _öğeleri_, meta veriler içeren belge ve _akışları_, öğe koleksiyonunu olduğu.</span><span class="sxs-lookup"><span data-stu-id="e4456-253">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="e4456-254">Şekil 8-2 farklı DocumentDB kaynakları arasındaki ilişkiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4456-254">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>

![Bir NoSQL JSON veritabanı olan documentdb'de kaynaklar arasındaki hiyerarşi ilişkisi](./media/image8-2.png)

<span data-ttu-id="e4456-256">**Şekil 8-2.**</span><span class="sxs-lookup"><span data-stu-id="e4456-256">**Figure 8-2.**</span></span> <span data-ttu-id="e4456-257">DocumentDB kaynak kuruluş.</span><span class="sxs-lookup"><span data-stu-id="e4456-257">DocumentDB resource organization.</span></span>

<span data-ttu-id="e4456-258">DocumentDB sorgu dili, JSON belgelerini sorgulamak için basit ancak güçlü bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="e4456-258">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="e4456-259">Dil, ANSI SQL dil bilgisi kümesini destekler ve JavaScript nesnesi, dizileri, nesne oluşturması ve işlev çağrısını derin tümleştirme ekler.</span><span class="sxs-lookup"><span data-stu-id="e4456-259">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="e4456-260">**Başvuruları – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="e4456-260">**References – DocumentDB**</span></span>

- <span data-ttu-id="e4456-261">DocumentDB giriş</span><span class="sxs-lookup"><span data-stu-id="e4456-261">DocumentDB Introduction</span></span>  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="e4456-262">Diğer Kalıcılık seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e4456-262">Other persistence options</span></span>

<span data-ttu-id="e4456-263">Ek olarak ilişkisel ve NoSQL depolama seçenekleri, ASP.NET Core uygulamaları, bulut tabanlı, ölçeklenebilir bir şekilde çeşitli veri biçimleri ve dosyaları depolamak için Azure depolama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4456-263">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="e4456-264">Azure depolama yüksek düzeyde ölçeklenebilir olduğundan küçük miktarda veri ve uygulamanız gerekiyorsa, yüzlerce ya da terabayt depolama kadar ölçek depolama kullanıma başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4456-264">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="e4456-265">Azure depolama, dört veri türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="e4456-265">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="e4456-266">BLOB Depolama, yapılandırılmamış metin veya ikili depolama, aynı zamanda nesne depolama olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e4456-266">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="e4456-267">Tablo depolama için yapılandırılmış veri kümeleri, satır anahtarı erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-267">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="e4456-268">Kuyruk depolama, kuyruk tabanlı güvenilir Mesajlaşma için.</span><span class="sxs-lookup"><span data-stu-id="e4456-268">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="e4456-269">Azure sanal makineler ve şirket içi uygulamalar arasında paylaşılan dosya erişimi için dosya depolama.</span><span class="sxs-lookup"><span data-stu-id="e4456-269">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="e4456-270">**Başvuru-Azure depolama**</span><span class="sxs-lookup"><span data-stu-id="e4456-270">**References – Azure Storage**</span></span>

- <span data-ttu-id="e4456-271">Azure depolama giriş</span><span class="sxs-lookup"><span data-stu-id="e4456-271">Azure Storage Introduction</span></span>  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="e4456-272">Önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="e4456-272">Caching</span></span>

<span data-ttu-id="e4456-273">Web uygulamalarında, her web isteğini en kısa süre içinde tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e4456-273">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="e4456-274">Bunu yapmanın bir yolu, sunucu, isteğini tamamlamak için yapmalısınız dış çağrı sayısı çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-274">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="e4456-275">Önbelleğe alma, sunucuda verilerin bir kopyasını depolayarak içerir (veya başka bir veri yani daha kolayca veri kaynağını sorguladı depolamak).</span><span class="sxs-lookup"><span data-stu-id="e4456-275">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="e4456-276">Web uygulamaları ve özellikle SPA olmayan geleneksel web uygulamaları, tüm kullanıcı arabirimi her istek ile oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-276">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="e4456-277">Bu, sık sorguların çoğu, aynı veritabanı sürekli bir kullanıcı isteğinden sonraki yapılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e4456-277">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="e4456-278">Çoğu durumda, sürekli, veritabanından istemek için çok az neden olduğundan bu veri nadiren de olsa değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e4456-278">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="e4456-279">ASP.NET Core tüm sayfaları ve verileri önbelleğe alma, önbelleğe alma işlemi için yanıt önbelleğe destekleyen daha ayrıntılı önbelleğe alma davranışını destekler.</span><span class="sxs-lookup"><span data-stu-id="e4456-279">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="e4456-280">Önbelleği uygularken dikkate ayrımı içinde tutmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e4456-280">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="e4456-281">Önbelleğe alma mantığını, veri erişim mantığı ya da kullanıcı arabiriminiz uygulamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="e4456-281">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="e4456-282">Bunun yerine, kendi sınıflarda önbelleğe alma kapsüllemek ve davranışını yönetmek için yapılandırma kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4456-282">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="e4456-283">Tek sorumluluk ilkeleri ve açık/kapalı izler ve büyüdükçe, uygulamanızda önbelleğe alma kullanımını yönetmek kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e4456-283">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="e4456-284">ASP.NET Core yanıt önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="e4456-284">ASP.NET Core response caching</span></span>

<span data-ttu-id="e4456-285">ASP.NET Core yanıt önbelleğe alma iki düzeylerini destekler.</span><span class="sxs-lookup"><span data-stu-id="e4456-285">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="e4456-286">İlk düzeyi, sunucu üzerindeki herhangi bir şey önbelleğe almaz, ancak istemciler ve proxy sunucular önbellek yanıtları isteyin HTTP üstbilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="e4456-286">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="e4456-287">Bu, tek tek denetleyicileri veya Eylemler ResponseCache öznitelik ekleyerek uygulanır:</span><span class="sxs-lookup"><span data-stu-id="e4456-287">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="e4456-288">Önceki örnekte, sonuç 60 saniye için önbelleğe almak için istemcileri söyleyen yanıta eklenen aşağıdaki üst bilgisindeki neden olur.</span><span class="sxs-lookup"><span data-stu-id="e4456-288">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="e4456-289">Cache-Control: Genel, max-age 60 =</span><span class="sxs-lookup"><span data-stu-id="e4456-289">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="e4456-290">Sunucu tarafı uygulamayı bellek içi önbelleğe alma ekleme için başvuru Microsoft.AspNetCore.ResponseCaching NuGet paketini ve ardından yanıt önbelleğe alma ara yazılımı eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4456-290">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="e4456-291">Bu ara yazılımın Createservicereplicalisteners() hem de Yapılandırma başlangıç yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="e4456-291">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="e4456-292">Yanıtları önbelleğe alma ara yazılımı otomatik olarak özelleştirebileceğiniz koşul kümesine göre yanıtları önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="e4456-292">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="e4456-293">Varsayılan olarak, GET veya HEAD yöntemleri istenen yalnızca 200 (Tamam) yanıtlarını önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="e4456-293">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="e4456-294">Ayrıca, istekleri bir Cache-Control ile bir yanıt olmalıdır: ortak üstbilgi ve yetkilendirme veya Set-Cookie üst bilgiler dahil edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4456-294">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="e4456-295">Bkz: bir [yanıt önbelleğe alma ara yazılımı tarafından kullanılan önbellek koşullar tam listesi](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="e4456-295">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="e4456-296">Veri önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="e4456-296">Data caching</span></span>

<span data-ttu-id="e4456-297">Yerine (veya ek olarak) tam web yanıtları önbelleğe alma, tek tek veri sorguların sonuçlarını önbelleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-297">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="e4456-298">Bu, bellek web sunucusunda önbelleğe alma kullanabilir, veya bu kullanın [dağıtılmış önbellek](/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="e4456-298">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="e4456-299">Bu bölümde, bellek içinde önbelleğe alma ekleme gösterilecektir.</span><span class="sxs-lookup"><span data-stu-id="e4456-299">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="e4456-300">Bellek için destek eklendi (veya dağıtılmış) içinde Createservicereplicalisteners() önbelleğe alma:</span><span class="sxs-lookup"><span data-stu-id="e4456-300">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="e4456-301">Microsoft.Extensions.Caching.Memory NuGet paketini de eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4456-301">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="e4456-302">Hizmet ekledikten sonra önbelleğe erişmek ihtiyaç duyduğunuz her yerde bağımlılık ekleme IMemoryCache isteyin.</span><span class="sxs-lookup"><span data-stu-id="e4456-302">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="e4456-303">Bu örnekte, erişimi denetleyen (ya da davranışı ekler) ICatalogService alternatif uygulaması sağlayarak CachedCatalogService Proxy (veya Dekoratör) tasarım deseni kullanan temel CatalogService uygulaması.</span><span class="sxs-lookup"><span data-stu-id="e4456-303">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }

    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }

    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }

    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="e4456-304">Hizmet önbelleğe alınmış sürümünü kullanabilirsiniz, ancak yine de oluşturucusunda gereken CatalogService örneğini almak için hizmeti izin uygulamasını yapılandırmak için içinde Createservicereplicalisteners() aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e4456-304">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="e4456-305">Bu yerinde katalog verileri getirmek için veritabanı çağrıları yalnızca dakika başına bir kez yerine her istekte yapılır.</span><span class="sxs-lookup"><span data-stu-id="e4456-305">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="e4456-306">Siteye trafiğe bağlı olarak, bunun veritabanına ve şu anda bu hizmet tarafından sunulan sorguları üç bağlı olduğu giriş sayfası için ortalama sayfa yükleme süresi yapılan sorguları sayısı çok önemli bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-306">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="e4456-307">Önbelleğe alma uygulandığında, ortaya sorunu _getirse veri_ – diğer bir deyişle, kaynak ancak eski bir sürümü değişmiş verileri önbellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="e4456-307">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="e4456-308">Bu sorunu gidermek için basit bir yol için meşgul bir uygulama olduğundan verileri önbelleğe uzunluğu genişletme sınırlı ek faydası küçük önbellek süreleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e4456-308">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="e4456-309">Örneğin, bir tek veritabanı sorgusu yapan bir sayfa göz önünde bulundurun ve saniye başına 10 kez istendi.</span><span class="sxs-lookup"><span data-stu-id="e4456-309">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="e4456-310">Bu sayfa bir dakika boyunca önbelleğe alınmışsa dakika başına 1, % 99,8 azaltma 600 ' açılan yapılan veritabanı sorgularının sayısı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e4456-310">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="e4456-311">Bunun yerine, önbelleğe alma süresi bir saat yapıldı, genel azaltma %99.997 olacaktır, ancak artık eski veri olasılığını ve olası yaşını hem de önemli ölçüde artırıldı.</span><span class="sxs-lookup"><span data-stu-id="e4456-311">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="e4456-312">İçerdikleri veriler güncelleştirildiğinde önbellek girişlerini proaktif bir şekilde kaldırmak başka bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="e4456-312">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="e4456-313">Tek bir giriş anahtarıyla biliniyorsa kaldırılabilir:</span><span class="sxs-lookup"><span data-stu-id="e4456-313">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="e4456-314">Uygulamanızın, önbelleğe alan güncelleştirme işlevi sunarsa, kodunuzdaki güncelleştirmeler yapar karşılık gelen önbellek girişlerinin kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4456-314">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="e4456-315">Bazen belirli bir veri kümesine bağlı olan birçok farklı girdi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-315">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="e4456-316">Bu durumda, bir CancellationChangeToken kullanarak önbellek girişlerinin arasındaki bağımlılıkları oluşturmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-316">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="e4456-317">Bir CancellationChangeToken ile belirteci iptal ederek birden fazla önbellek girişi tek seferde dolabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-317">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

<span data-ttu-id="e4456-318">Önbelleğe alma işlemi sürekli olarak aynı değerleri veritabanından isteği gönderen web sayfaları performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="e4456-318">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="e4456-319">Geliştirme için ihtiyaç gördüğünüz önbelleğe alma uygulanmadan önce veri erişimi ve sayfa performansı ölçmek ve önbelleğe alma yalnızca geçerli emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4456-319">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="e4456-320">Önbelleğe alma, web sunucu bellek kaynaklarını tüketir ve bu tekniği kullanarak erken iyileştirme önemlidir uygulama karmaşıklığını artırır.</span><span class="sxs-lookup"><span data-stu-id="e4456-320">Caching consumes web server memory resources and increases the complexity of the application, so it’s important you don’t prematurely optimize using this technique.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e4456-321">[Önceki](develop-asp-net-core-mvc-apps.md)
[İleri](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="e4456-321">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
