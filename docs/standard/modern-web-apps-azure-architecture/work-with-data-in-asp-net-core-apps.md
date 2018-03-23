---
title: ASP.NET Core uygulamalardaki verileri ile çalışma
description: ASP.NET Core ve Azure ile modern Web uygulamaları mimari | ASP verilerle çalışma
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: df80dfb6029932c53e028bfb753dcfa94b548ba1
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="3e89e-103">ASP.NET Core uygulamalardaki verileri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="3e89e-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="3e89e-104">"Veri değerli bir şeydir ve sistemler kendilerini daha uzun sürer."</span><span class="sxs-lookup"><span data-stu-id="3e89e-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="3e89e-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="3e89e-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="3e89e-106">Özet</span><span class="sxs-lookup"><span data-stu-id="3e89e-106">Summary</span></span>

<span data-ttu-id="3e89e-107">Veri erişimi, neredeyse her yazılım uygulamanın önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="3e89e-108">ASP.NET Core veri erişim seçenekleri, Entity Framework Çekirdek (ve de Entity Framework 6) dahil olmak üzere çeşitli destekler ve tüm .NET veri erişim framework ile çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e89e-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="3e89e-109">Hangisinin kullanılacağını framework verilere seçim uygulamanın gereksinimlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="3e89e-110">Bu seçenek ApplicationCore ve kullanıcı Arabirimi projelerden özetleyen ve yalıtma altyapısında, uygulama ayrıntılarını geniş eşleşmiş, sınanabilir yazılım üretmek için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="3e89e-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="3e89e-111">Entity Framework Çekirdek (için ilişkisel veritabanları)</span><span class="sxs-lookup"><span data-stu-id="3e89e-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="3e89e-112">İlişkisel verilerle çalışmak için gereken yeni bir ASP.NET Core uygulama yazıyorsanız, Entity Framework Çekirdek (EF çekirdek), verilere erişmek, uygulamanız için önerilen yöntem olduğu.</span><span class="sxs-lookup"><span data-stu-id="3e89e-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="3e89e-113">EF çekirdeği .NET geliştiricilerinin nesneleri için ve bir veri kaynağı kalıcı hale getirmek bir nesne ilişkisel Eşleyici (O/RM) olur.</span><span class="sxs-lookup"><span data-stu-id="3e89e-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="3e89e-114">Bu, veri erişim geliştiriciler genellikle yazmak zorunda kalırsınız kodu çoğunu gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="3e89e-115">ASP.NET Core gibi destek modüler platformlar arası uygulamalar kadar sıfırdan EF çekirdek yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="3e89e-116">Bir NuGet paketi olarak uygulamanıza ekleyin, başlangıç yapılandırmak ve ihtiyacınız olduğunda bağımlılık ekleme isteği.</span><span class="sxs-lookup"><span data-stu-id="3e89e-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="3e89e-117">SQL Server veritabanı ile EF çekirdek kullanmak için aşağıdaki dotnet CLI komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3e89e-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="3e89e-118">DotNet paket Microsoft.EntityFrameworkCore.SqlServer Ekle</span><span class="sxs-lookup"><span data-stu-id="3e89e-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="3e89e-119">Test etmek için bir Inmemory veri kaynağı için destek eklemek için:</span><span class="sxs-lookup"><span data-stu-id="3e89e-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="3e89e-120">DotNet paket Microsoft.EntityFrameworkCore.InMemory Ekle</span><span class="sxs-lookup"><span data-stu-id="3e89e-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="3e89e-121">DbContext</span><span class="sxs-lookup"><span data-stu-id="3e89e-121">The DbContext</span></span>

<span data-ttu-id="3e89e-122">EF çekirdek ile çalışmak için DbContext öğesinin bir alt kümesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="3e89e-123">Bu sınıf, uygulama ile çalışıp çalışmayacağını varlıkların koleksiyonları özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="3e89e-124">EShopOnWeb örnek CatalogContext öğeleri, markalar ve türleri için koleksiyonlarıyla içerir:</span><span class="sxs-lookup"><span data-stu-id="3e89e-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="3e89e-125">DbContext DbContextOptions kabul eden bir oluşturucuya sahip olması ve bu bağımsız değişken temel DbContext oluşturucusunun geçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="3e89e-126">Yalnızca bir DbContext uygulamanızda varsa, DbContextOptions örneği geçirebilirsiniz ancak varsa, birden fazla genel DbContextOptions kullanmalısınız unutmayın<T> DbContext tür genel parametre olarak geçirme türü.</span><span class="sxs-lookup"><span data-stu-id="3e89e-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="3e89e-127">EF çekirdek yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e89e-127">Configuring EF Core</span></span>

<span data-ttu-id="3e89e-128">ASP.NET çekirdeği uygulamanızda ConfigureServices yönteminizi EF çekirdek genellikle yapılandıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="3e89e-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="3e89e-129">EF Çekirdek yapılandırmasını kolaylaştırmak için çeşitli yararlı genişletme yöntemleri destekleyen bir DbContextOptionsBuilder kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="3e89e-130">CatalogContext yapılandırmasında tanımlı bir bağlantı dizesini bir SQL Server veritabanını kullanmak üzere yapılandırmak için ConfigureServices için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3e89e-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="3e89e-131">Bellek içi veritabanı kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="3e89e-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="3e89e-132">DbContext alt türü oluşturulan EF çekirdek yüklenip ConfigureServices içinde yapılandırılmış sonra EF çekirdek kullanıma hazır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="3e89e-133">Gerekli herhangi bir hizmeti, DbContext türünün bir örneği isteyin ve yalnızca bir koleksiyondaki değilmiş gibi LINQ kullanarak, kalıcı varlıklarla çalışmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e89e-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="3e89e-134">EF çekirdek, depolamak ve verilerinizi almak için SQL sorguları LINQ ifadelere çevirme çalışır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="3e89e-135">Günlükçü yapılandırma ve alt düzey ayarlanmış en az sağlamayı EF çekirdek yürütme sorguları görebilirsiniz Şekil 8-1'de gösterildiği gibi bilgiler.</span><span class="sxs-lookup"><span data-stu-id="3e89e-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="3e89e-136">Şekil 8-1 günlüğü EF çekirdek sorguları konsoluna</span><span class="sxs-lookup"><span data-stu-id="3e89e-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="3e89e-137">Getirme ve veri depolama</span><span class="sxs-lookup"><span data-stu-id="3e89e-137">Fetching and Storing Data</span></span>

<span data-ttu-id="3e89e-138">EF çekirdek veri almak için uygun özelliğine erişmek ve LINQ sonucu filtre uygulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e89e-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="3e89e-139">LINQ, yansıtma, bir türden diğerine sonucu dönüştürme gerçekleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e89e-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="3e89e-140">Aşağıdaki örnek adına göre sıralanmış, bunların etkin özelliği tarafından filtre ve Selectlistıtem türü öngörülen CatalogBrands almak:</span><span class="sxs-lookup"><span data-stu-id="3e89e-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="3e89e-141">Sorgu hemen yürütmek için ToListAsync çağrısı eklemek için yukarıdaki örnekte önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="3e89e-142">Aksi takdirde, deyim Iqueryable atar<SelectListItem> brandItems için hangi çalıştırılmayacak numaralandırılan kadar.</span><span class="sxs-lookup"><span data-stu-id="3e89e-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="3e89e-143">Artıları ve eksileri yöntemleri Iqueryable sonuçları döndürmek için vardır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="3e89e-144">Daha fazla değiştirilmesi, ancak EF çekirdek çeviremez sorgu işlemleri eklediyseniz yalnızca çalışma zamanında oluşan hataları sonucunda da yapabilirsiniz EF çekirdek de oluşturmak sorgusu tanır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="3e89e-145">Veri erişim gerçekleştirme yönteme herhangi bir filtre geçirmek genellikle güvenlidir ve return geri bir bellek içi koleksiyonu (örneğin, liste<T>) sonucu olarak.</span><span class="sxs-lookup"><span data-stu-id="3e89e-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="3e89e-146">EF çekirdek Kalıcılık getirir varlıklar üzerinde değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="3e89e-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="3e89e-147">İzlenen bir varlığa değişiklikleri kaydetmek için yalnızca varlık getirmek için kullanılan aynı DbContext örnek olduğundan emin DbContext üzerinde SaveChanges yöntemini çağırın gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="3e89e-148">Ekleme ve kaldırma varlıklar doğrudan veritabanı komutlarını çalıştırmak için yeniden çağrısıyla SaveChanges uygun DbSet özelliği açıktır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="3e89e-149">Aşağıdaki örnek, ekleme, güncelleştirme ve varlıklar kalıcı kaldırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="3e89e-150">EF çekirdek destekler zaman uyumlu ve zaman uyumsuz yöntemleri getirme ve kaydetme.</span><span class="sxs-lookup"><span data-stu-id="3e89e-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="3e89e-151">Böylece Web sunucu iş parçacığı için veri erişim işlemleri tamamlamak için beklenirken engellenmez web uygulamalarında bu zaman uyumsuz ve bekleme düzeni zaman uyumsuz yöntemlerle kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="3e89e-152">İlgili veri getirme</span><span class="sxs-lookup"><span data-stu-id="3e89e-152">Fetching Related Data</span></span>

<span data-ttu-id="3e89e-153">EF çekirdek varlıklar aldığında, veritabanındaki varlık ile doğrudan depolanan özelliklerin tümünü doldurur.</span><span class="sxs-lookup"><span data-stu-id="3e89e-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="3e89e-154">İlgili varlık listeleri gibi Gezinti özellikleri değil doldurulur ve değerlerine ayarlayın olabilir null.</span><span class="sxs-lookup"><span data-stu-id="3e89e-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="3e89e-155">Bu EF çekirdek gerekli olandan daha fazla veri olduğu hızla istekleri işleyen gerekir ve verimli bir şekilde yanıtlar dönmek web uygulamaları için özellikle önemlidir: getiriliyor değil sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e89e-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="3e89e-156">Kullanarak bir varlık ile ilişkileri dahil etmek için *istekli yükleme*, gösterildiği gibi sorguya dayalı INCLUDE genişletme yöntemi kullanarak özelliğini belirtin:</span><span class="sxs-lookup"><span data-stu-id="3e89e-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="3e89e-157">Birden çok ilişki içerebilir ve bu da alt ilişkileri içerebilir ThenInclude kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3e89e-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="3e89e-158">EF çekirdek varlıklar sonuç kümesini almak için tek bir sorgu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3e89e-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="3e89e-159">İlgili verileri yüklemek için başka bir seçenek kullanmaktır *açık yükleme*.</span><span class="sxs-lookup"><span data-stu-id="3e89e-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="3e89e-160">Açık yükleme, ek veri zaten alınan bir varlık kümesine yüklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e89e-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="3e89e-161">Bu veritabanı için ayrı bir istek gerektirdiğinden, veritabanı sayısını en aza indirmeniz gerekir web uygulamaları için önerilmez gidiş dönüş istekte.</span><span class="sxs-lookup"><span data-stu-id="3e89e-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="3e89e-162">*Yavaş Yükleniyor* özelliğini uygulama tarafından başvurulduğu, ilgili verileri otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="3e89e-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="3e89e-163">EF çekirdek tarafından şu anda desteklenmez, ancak olarak açık yükleme ile bu genellikle web uygulamaları için devre dışı bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="3e89e-164">Esnek bağlantıları</span><span class="sxs-lookup"><span data-stu-id="3e89e-164">Resilient Connections</span></span>

<span data-ttu-id="3e89e-165">SQL veritabanları gibi dış kaynaklara bazen kullanılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="3e89e-166">Geçici olarak kullanım dışı kalması durumunda, uygulamaların bir özel durum yükseltme önlemek için yeniden deneme mantığı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e89e-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="3e89e-167">Bu yöntem, yaygın olarak adlandırılır *bağlantı dayanıklılığı*.</span><span class="sxs-lookup"><span data-stu-id="3e89e-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="3e89e-168">Uygulayabileceğiniz, [üstel geri alma kendi Denemeyle](https://docs.microsoft.com/azure/architecture/patterns/retry) en fazla yeniden deneme sayısı üst sınırına kadar rety üstel olarak artan bir bekleme süresi ile çalışırken tarafından tekniği.</span><span class="sxs-lookup"><span data-stu-id="3e89e-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="3e89e-169">Bu teknik bulut kaynakları aralıklı kısa sürelerle bazı isteklerin karşılanamamasına, için kullanılamıyor olabilir, olgu çalışır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="3e89e-170">Azure SQL DB için Entity Framework Çekirdek zaten iç veritabanı bağlantısı dayanıklılık ve yeniden deneme mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e89e-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="3e89e-171">Ancak istediğinizde dayanıklı EF çekirdek bağlantınız Entity Framework yürütme stratejisi her DbContext bağlantı etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="3e89e-172">Örneği için aşağıdaki kodu EF çekirdek bağlantı düzeyinde bağlantı başarısız olursa yeniden denenir dayanıklı SQL bağlantıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e89e-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="3e89e-173">Yürütme stratejilerini ve BeginTransaction ve birden çok DbContexts kullanarak açık işlemleri</span><span class="sxs-lookup"><span data-stu-id="3e89e-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="3e89e-174">EF çekirdek bağlantıları yeniden deneme etkinleştirildiğinde, EF çekirdek kullanarak gerçekleştirdiğiniz her işlem yeniden denenebilir çalışması haline gelir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="3e89e-175">Geçici bir hata oluşursa, her sorgu ve her çağrı SaveChanges bir birim olarak yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="3e89e-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="3e89e-176">Ancak, kodunuzu BeginTransaction kullanarak bir işlem başlatır, bir birim olarak kabul edilmesi için gereken işlemleri kendi grubunun tanımlıyorsanız — işlem içinde her şeyi sahip olması alındı geri bir hata oluşursa.</span><span class="sxs-lookup"><span data-stu-id="3e89e-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="3e89e-177">EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu işlemi yürütme girişimi ve birden çok DbContexts gelen birkaç SaveChanges bunu aşağıdaki gibi bir özel durum görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="3e89e-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="3e89e-178">System.InvalidOperationException: 'SqlServerRetryingExecutionStrategy' yapılandırılmış yürütme stratejisi kullanıcı tarafından başlatılan işlemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3e89e-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="3e89e-179">İşlem yeniden denenebilir bir birim olarak tüm işlemleri yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e89e-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="3e89e-180">Çözüm, yürütülecek gereken her şeyi temsil eden bir temsilci ile EF yürütme stratejisi el ile çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="3e89e-181">Geçici bir hata oluşursa, yürütme stratejisi temsilci yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="3e89e-182">Aşağıdaki kod, bu yaklaşımı uygulamak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e89e-182">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="3e89e-183">İlk DbContext olan \_catalogContext ve ikinci DbContext içinde olduğunu \_integrationEventLogService nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3e89e-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="3e89e-184">Son olarak, eylem olacaktır yürütme birden çok DbContexts ve EF yürütme stratejisi kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="3e89e-185">Başvuruları – Entity Framework Çekirdek</span><span class="sxs-lookup"><span data-stu-id="3e89e-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="3e89e-186">**EF Core belgeleri**</span><span class="sxs-lookup"><span data-stu-id="3e89e-186">**EF Core Docs**</span></span>  
> <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="3e89e-187">**EF Çekirdek: İlgili veriler**</span><span class="sxs-lookup"><span data-stu-id="3e89e-187">**EF Core: Related Data**</span></span>  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="3e89e-188">**ASP.NET uygulamalarında yavaş yükleniyor varlıklar kaçının**</span><span class="sxs-lookup"><span data-stu-id="3e89e-188">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="3e89e-189">EF çekirdek veya mikro ORM?</span><span class="sxs-lookup"><span data-stu-id="3e89e-189">EF Core or micro-ORM?</span></span>

<span data-ttu-id="3e89e-190">EF çekirdek Kalıcılık yönetmek için harika bir seçenektir ve çoğunlukla uygulama geliştiricileri veritabanı ayrıntılarının Kapsüller olsa da, tek seçim değil.</span><span class="sxs-lookup"><span data-stu-id="3e89e-190">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="3e89e-191">Başka bir popüler açık kaynak alternatif [Dapper](https://github.com/StackExchange/Dapper), bir sözde mikro ORM.</span><span class="sxs-lookup"><span data-stu-id="3e89e-191">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="3e89e-192">Mikro ORM daha az veri yapılarını nesneleri eşleme için aracı tam özellikli bir basit ' dir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-192">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="3e89e-193">Dapper söz konusu olduğunda, arka plandaki tam olarak Kapsüllenen sorgular yerine hedefleri performans üzerinde odaklanmak tasarımı almak ve verileri güncelleştirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-193">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="3e89e-194">Bu SQL geliştiriciden soyut değil çünkü Dapper "metal" daha yakındır ve tam yazma geliştiricilerinin erişim işlemi için verilen veri kullanmak istedikleri sorgular.</span><span class="sxs-lookup"><span data-stu-id="3e89e-194">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="3e89e-195">EF çekirdek Dapper ayrı ancak kendi performansını yükü de eklemeniz sağlayan iki önemli özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-195">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="3e89e-196">İlk LINQ SQL ifadelere çevrilmesi ' dir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-196">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="3e89e-197">Bu çevirileri önbelleğe alınır, ancak buna rağmen yok yükü ilk kez gerçekleştirmede.</span><span class="sxs-lookup"><span data-stu-id="3e89e-197">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="3e89e-198">(Verimli güncelleştirme deyimleri oluşturulabilir böylece) üzerinde varlıklar değişiklik izleme saniyedir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-198">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="3e89e-199">Bu davranış özel sorgular için AsNotTracking uzantısını kullanarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-199">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="3e89e-200">EF çekirdek genellikle çok verimli ve herhangi bir durumda edilebilir performans açısından SQL sorguları da oluşturur, ancak yürütülecek kesin sorgu denetime ince varsa, özel SQL'de geçirebilirsiniz (veya bir saklı yordamı yürütme) EF kullanma , Çok çekirdek.</span><span class="sxs-lookup"><span data-stu-id="3e89e-200">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="3e89e-201">Bu durumda, Dapper hala EF çekirdek sürümlerden üstünlüğü ancak yalnızca biraz.</span><span class="sxs-lookup"><span data-stu-id="3e89e-201">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="3e89e-202">Bazı performans verilerini her olabilir 2016 MSDN makalesine Julie Lerman sunar [Dapper, Entity Framework ve karma uygulamalar](https://msdn.microsoft.com/magazine/mt703432.aspx).</span><span class="sxs-lookup"><span data-stu-id="3e89e-202">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="3e89e-203">Ek performans Kıyaslama verileri çeşitli veri erişim yöntemler için üzerinde bulunabilir [Dapper site](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="3e89e-203">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="3e89e-204">Dapper sözdizimi EF çekirdek nasıl değişeceğini görmek için bu iki sürümü öğelerinin bir listesini almak için aynı yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3e89e-204">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="3e89e-205">Dapper daha karmaşık nesne grafiklerle yapı gerekiyorsa, ilişkili sorgular (EF çekirdek gibi bir dahil etme ekleme aksine) kendiniz yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-205">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="3e89e-206">Bu, sözdizimi, tek tek satır birden çok eşlenen nesnelere eşlemenize olanak sağlayan çoklu eşleme adlı bir özelliği de dahil olmak üzere çeşitli desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-206">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="3e89e-207">Örneğin, bir sınıf Post özelliğiyle sahibi kullanıcı türünde verildiğinde, aşağıdaki SQL tüm gerekli verileri döndürür:</span><span class="sxs-lookup"><span data-stu-id="3e89e-207">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="3e89e-208">Döndürülen her satır, hem kullanıcı hem de Post verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-208">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="3e89e-209">Kullanıcı verileri kendi Owner özelliği aracılığıyla gönderme verisi eklenmesi gereken olduğundan, aşağıdaki işlev kullanılır:</span><span class="sxs-lookup"><span data-stu-id="3e89e-209">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="3e89e-210">İlişkili kullanıcı verilerle doldurmuş kendi Owner özelliği ile gönderileri koleksiyonu döndürmek için tam kod listesi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="3e89e-210">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="3e89e-211">Daha az kapsülleme sağladığından, geliştiricilerin kendi verilerin depolanma şeklini hakkında daha fazla bilmeniz Dapper gerektirir nasıl verimli bir şekilde sorgulamak ve onu getirmek için daha fazla kod yazın.</span><span class="sxs-lookup"><span data-stu-id="3e89e-211">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="3e89e-212">Model, yalnızca yeni bir geçiş (başka bir EF çekirdek özelliği) oluşturma ve/veya bir DbContext tek bir yerde eşleme bilgilerin güncelleştirilmesini yerine değiştiğinde etkilenir her sorgu güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-212">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="3e89e-213">Bu sorguları değil derleme zamanı garanti sahip, bu nedenle bunlar çalışma zamanında değişikliklere yanıt modeli ya da veritabanı, hataları hızla algılaması daha zor hale kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-213">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="3e89e-214">Bu bileşim karşılığında Dapper son derece hızlı performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e89e-214">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="3e89e-215">EF çekirdek çoğu uygulama ve neredeyse tüm uygulamaların çoğu bölümleri için kabul edilebilir performans sunar.</span><span class="sxs-lookup"><span data-stu-id="3e89e-215">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="3e89e-216">Bu nedenle, geliştirici üretkenliği faydalarını kendi performansa ağır olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-216">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="3e89e-217">Önbelleğe alınan yararlanabilir sorguları için gerçek sorgu yalnızca yürütülebilecek görece küçük yapma zamanı, küçük bir yüzdesi performans farklar tartışmalı sorgu.</span><span class="sxs-lookup"><span data-stu-id="3e89e-217">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="3e89e-218">SQL veya NoSQL</span><span class="sxs-lookup"><span data-stu-id="3e89e-218">SQL or NoSQL</span></span>

<span data-ttu-id="3e89e-219">Geleneksel olarak, SQL Server gibi ilişkisel veritabanları kalıcı veri depolama için Market hâkim, ancak bunlar yalnızca çözüm kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-219">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="3e89e-220">NoSQL veritabanları ister [MongoDB](https://www.mongodb.com/what-is-mongodb) nesneleri depolamak için farklı bir yaklaşım sunar.</span><span class="sxs-lookup"><span data-stu-id="3e89e-220">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="3e89e-221">Tabloları ve satır nesneleri eşleme yerine başka bir tüm nesne grafiğinin seri hale getirmek ve sonucu depolamak için bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-221">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="3e89e-222">Bu yaklaşımın avantajları en az bir başlangıçta, Basitlik ve Performans'dır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-222">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="3e89e-223">Nesne ilişkileri olan birçok tablolara parçalayın daha anahtar ile tek bir serileştirilmiş nesne depolamak kesinlikle basittir ve güncelleştirme ve nesne son başlatıldığından bu yana değişmiş olabilir satırları veritabanından alınır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-223">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="3e89e-224">Benzer şekilde, getirme ve bir anahtar tabanlı depolama alanından tek bir nesne seri durumdan genellikle çok daha hızlı ve daha kolay karmaşık birleştirmeler veya birden çok veritabanı sorguları tam olarak aynı nesne ilişkisel bir veritabanındaki oluşturmak için gerekli.</span><span class="sxs-lookup"><span data-stu-id="3e89e-224">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="3e89e-225">Kilitleri veya işlemleri ya da sabit bir şema eksikliği de NoSQL veritabanları çok büyük veri kümeleri destekleyen birçok makineler arasında ölçeklendirme için çok uygun hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-225">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="3e89e-226">Diğer taraftan, (bunlar genellikle olarak adlandırılan) belirli sakıncaları NoSQL veritabanlarına sahip.</span><span class="sxs-lookup"><span data-stu-id="3e89e-226">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="3e89e-227">İlişkisel veritabanları normalleştirme tutarlılığı zorlamak ve verilerin yinelenmesini engellemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e89e-227">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="3e89e-228">Bu veritabanının toplam boyutunu azaltır ve paylaşılan veri güncelleştirmeleri hemen veritabanı kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e89e-228">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="3e89e-229">Bir ülkenin adı değiştirildiyse, adres kayıtları Update'ten kendilerini güncelleştirmeye gerek yararlanabileceğini şekilde ilişkisel bir veritabanında bir adres tablosu kimliği, bir ülke tablo başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-229">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="3e89e-230">Ancak, bir NoSQL veritabanı adresi ve onun ilişkili ülke birçok depolanan nesneleri bir parçası olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="3e89e-230">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="3e89e-231">Bir ülke adı için bir güncelleştirme yerine tek bir satır güncelleştirilmesi gibi nesnelerin tümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-231">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="3e89e-232">İlişkisel veritabanları yabancı anahtarlar gibi kuralları zorunlu tutarak ilişkisel bütünlüğü de emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e89e-232">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="3e89e-233">NoSQL veritabanları verilerine böyle kısıtlamalar genellikle sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="3e89e-233">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="3e89e-234">Başka bir karmaşıklık veritabanları uğraşmanız gereken NoSQL Sürüm ' dir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-234">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="3e89e-235">Bir nesnenin özelliklerini değiştirdiğinizde, depolanan önceki sürümlerden seri durumdan çıkarılacak mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-235">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="3e89e-236">Bu nedenle, bir nesne seri hale getirilmiş (önceki) sürümüne sahip tüm var olan nesneleri yeni şemaya uyacak şekilde güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-236">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="3e89e-237">İlişkisel bir veritabanından farklı kavramsal olarak değil, bazen şema değişiklikleri güncelleştirme kodları gerektiren veya güncelleştirmeleri eşleme.</span><span class="sxs-lookup"><span data-stu-id="3e89e-237">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="3e89e-238">Ancak, değiştirilmelidir girdi sayısı çok görülür NoSQL yaklaşımda büyük olduğu için daha fazla çoğaltma veri.</span><span class="sxs-lookup"><span data-stu-id="3e89e-238">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="3e89e-239">Birden fazla sürümünü nesneleri depolamak için NoSQL veritabanlarında mümkündür, bir şey sabit şemasına ilişkisel veritabanları genellikle desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3e89e-239">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="3e89e-240">Ancak, bu durumda uygulama kodunuz nesneleri, karmaşıklık ekleme önceki sürümlerini varlığını hesabı gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-240">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="3e89e-241">NoSQL veritabanları genellikle zorla [ACID](http://en.wikipedia.org/wiki/ACID), sahip oldukları performans ve ölçeklenebilirlik avantajlarını ilişkisel veritabanları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-241">NoSQL databases typically do not enforce [ACID](http://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="3e89e-242">Bunlar, son derece büyük veri kümelerini ve depolama normalleştirilmiş tablo yapılarında için oldukça uygun olmayan nesneler için oldukça uygun.</span><span class="sxs-lookup"><span data-stu-id="3e89e-242">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="3e89e-243">Neden tek bir uygulama hem ilişkisel yararlanamaz ve her en iyi olduğu kullanarak NoSQL veritabanlarını uygun bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e89e-243">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="3e89e-244">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="3e89e-244">Azure DocumentDB</span></span>

<span data-ttu-id="3e89e-245">Azure DocumentDB şemasız verileri bulut tabanlı depolama sunan tam olarak yönetilen bir NoSQL veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-245">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="3e89e-246">DocumentDB hızlı ve tahmin edilebilir performans, yüksek kullanılabilirlik, esnek ölçeklendirme ve genel dağıtım için yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="3e89e-246">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="3e89e-247">Geliştiriciler, bir NoSQL veritabanı olmaya rağmen JSON verilerini zengin ve tanıdık SQL sorgu özellikleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-247">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="3e89e-248">Documentdb'deki tüm kaynaklar JSON belgeleri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-248">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="3e89e-249">Olarak yönetilen kaynakları *öğeleri*, hangi meta veriler içeren belge ve *akışları*, öğe koleksiyonunu olduğu.</span><span class="sxs-lookup"><span data-stu-id="3e89e-249">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="3e89e-250">Şekil 8-2 farklı DocumentDB kaynakları arasındaki ilişkiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-250">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![Bir NoSQL JSON veritabanı olan documentdb'de kaynaklar arasındaki hiyerarşi ilişkisi](./media/image8-2.png)

<span data-ttu-id="3e89e-252">**Şekil 8-2.**</span><span class="sxs-lookup"><span data-stu-id="3e89e-252">**Figure 8-2.**</span></span> <span data-ttu-id="3e89e-253">DocumentDB kaynak kuruluş.</span><span class="sxs-lookup"><span data-stu-id="3e89e-253">DocumentDB resource organization.</span></span>

<span data-ttu-id="3e89e-254">DocumentDB sorgu dili, JSON belgelerini sorgulamak için basit ancak güçlü bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-254">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="3e89e-255">Dil, ANSI SQL dil bilgisinin kümesini destekler ve JavaScript nesnesi, dizileri, nesne oluşturması ve işlev çağrısını derin tümleştirme ekler.</span><span class="sxs-lookup"><span data-stu-id="3e89e-255">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="3e89e-256">**Başvuruları – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="3e89e-256">**References – DocumentDB**</span></span>

-   <span data-ttu-id="3e89e-257">DocumentDB Introduction\\</span><span class="sxs-lookup"><span data-stu-id="3e89e-257">DocumentDB Introduction\\</span></span>
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="3e89e-258">Diğer Kalıcılık seçenekleri</span><span class="sxs-lookup"><span data-stu-id="3e89e-258">Other Persistence Options</span></span>

<span data-ttu-id="3e89e-259">İlişkisel eklemeyi ve NoSQL depolama seçenekleri, ASP.NET Core uygulamaları bir bulut tabanlı ve ölçeklenebilir şekilde çeşitli veri biçimleri ve dosyalarını depolamak için Azure Storage kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-259">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="3e89e-260">Azure depolama yüksek düzeyde ölçeklenebilir olduğundan küçük miktarda veri ve uygulamanızı gerektiriyorsa, yüzlerce veya terabayt depolama kadar ölçek depolama çıkışı başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e89e-260">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="3e89e-261">Azure Storage dört veri türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="3e89e-261">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="3e89e-262">BLOB Storage yapılandırılmamış metin veya ikili depolama, nesne depolama olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-262">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="3e89e-263">Table Storage yapılandırılmış veri kümeleri için satır anahtarları erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-263">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="3e89e-264">Sıra tabanlı güvenilir Mesajlaşma için kuyruk depolama.</span><span class="sxs-lookup"><span data-stu-id="3e89e-264">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="3e89e-265">Azure sanal makineler ve şirket içi uygulamalar arasında paylaşılan dosya erişimi için dosya depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="3e89e-265">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="3e89e-266">**Başvuruları – Azure depolama**</span><span class="sxs-lookup"><span data-stu-id="3e89e-266">**References – Azure Storage**</span></span>

-   <span data-ttu-id="3e89e-267">Azure depolama Introduction\\</span><span class="sxs-lookup"><span data-stu-id="3e89e-267">Azure Storage Introduction\\</span></span>
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="3e89e-268">Önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="3e89e-268">Caching</span></span>

<span data-ttu-id="3e89e-269">Web uygulamalarında her web isteğini olası en kısa sürede tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-269">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="3e89e-270">Bunu elde etmenin bir yolu, sunucunun isteği tamamlamak için olmalısınız dış çağrılarının sayısını çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-270">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="3e89e-271">Önbelleğe alma sunucuda verilerin bir kopyasını saklamak içerir (veya başka bir veri diğer bir deyişle daha fazla veri kaynağını kolayca sorgulanan depolayın).</span><span class="sxs-lookup"><span data-stu-id="3e89e-271">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="3e89e-272">Web uygulamaları ve özellikle SPA olmayan geleneksel web uygulamaları, tüm kullanıcı arabirimi her istek ile oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-272">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="3e89e-273">Bu, genellikle aynı veritabanı sorgularından sürekli olarak bir kullanıcı isteği sonraki çoğunu yapılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-273">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="3e89e-274">Bu yüzden sürekli veritabanından istemek için çok az neden çoğu durumda, bu verileri nadiren, değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-274">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="3e89e-275">ASP.NET Core yanıt, tüm sayfaları ve verileri önbelleğe alma, önbelleğe alma işlemi için önbelleğe alma konusunda daha ayrıntılı önbelleğe alma davranışını destekleyen destekler.</span><span class="sxs-lookup"><span data-stu-id="3e89e-275">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="3e89e-276">Önbelleğe alma uygularken, sorunları göz ayrılması içinde tutmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-276">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="3e89e-277">Veri erişim mantığınızı ya da Kullanıcı Arabiriminizin önbelleğe alma mantığını uygulamak kaçının.</span><span class="sxs-lookup"><span data-stu-id="3e89e-277">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="3e89e-278">Bunun yerine, kendi sınıflarda önbelleğe alma şifreleyebilir ve yapılandırma davranışını yönetmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e89e-278">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="3e89e-279">Bu açık/kapalı ve tek sorumluluk ilkeler izler ve onu büyüdükçe, uygulamanızda önbelleğe almayı kullanma yönetebilmeniz için daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-279">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="3e89e-280">ASP.NET Core yanıt önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="3e89e-280">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="3e89e-281">ASP.NET Core yanıt önbelleğe alma iki düzeylerini destekler.</span><span class="sxs-lookup"><span data-stu-id="3e89e-281">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="3e89e-282">İlk düzeyi sunucu üzerindeki herhangi bir şey önbelleğe almaz, ancak, istemciler ve proxy sunucular önbellek yanıtları yönlendiren HTTP üstbilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="3e89e-282">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="3e89e-283">Bu, tek tek denetleyicileri veya Eylemler ResponseCache özniteliği ekleyerek uygulanır:</span><span class="sxs-lookup"><span data-stu-id="3e89e-283">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

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

<span data-ttu-id="3e89e-284">Yanıt önbelleğe alma Ara yanıtları özelleştirebileceğiniz koşullar kümesine göre otomatik olarak önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-284">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="3e89e-285">Varsayılan olarak, GET veya HEAD yöntemleri istenen yalnızca 200 (Tamam) yanıtlarını önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-285">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="3e89e-286">Ayrıca, istekleri Cache-Control yanıtta olması gerekir: ortak üstbilgi ve üstbilgileri yetkilendirme veya Set-Cookie içeremez.</span><span class="sxs-lookup"><span data-stu-id="3e89e-286">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="3e89e-287">Bkz: bir [ara yazılım önbelleğe alma yanıt tarafından kullanılan önbelleğe alma koşullar tam listesi](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="3e89e-287">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="3e89e-288">Veri önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="3e89e-288">Data Caching</span></span>

<span data-ttu-id="3e89e-289">Yerine (veya ek olarak) tam web yanıtlarını önbelleğe alma, tek tek veri sorguların sonuçlarını önbelleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-289">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="3e89e-290">Bunun için bellek web sunucusunda önbelleğe alma veya kullanabilirsiniz kullanmak [dağıtılmış önbellek](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="3e89e-290">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="3e89e-291">Bu bölümde nasıl bellek önbelleğe alma uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-291">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="3e89e-292">Bellek desteği ekleme (veya dağıtılmış) içinde ConfigureServices önbelleğe alma:</span><span class="sxs-lookup"><span data-stu-id="3e89e-292">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="3e89e-293">Microsoft.Extensions.Caching.Memory NuGet paketini de eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3e89e-293">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="3e89e-294">Hizmet ekledikten sonra önbellek erişmesi gereken her yerde bağımlılık ekleme IMemoryCache isteyin.</span><span class="sxs-lookup"><span data-stu-id="3e89e-294">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="3e89e-295">Bu örnekte, erişimi kontrol (veya davranışına ekler) ICatalogService alternatif uygulaması sağlayarak CachedCatalogService Proxy (veya oluşturma öğesi) tasarım deseni kullanan temel CatalogService uygulaması.</span><span class="sxs-lookup"><span data-stu-id="3e89e-295">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="3e89e-296">Önbelleğe alınan hizmet sürümünü kullanın, ancak hala kurucusunda gereken CatalogService örneğini almak hizmetin izin için uygulamayı yapılandırmak için ConfigureServices aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3e89e-296">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="3e89e-297">Bu yerinde katalog verilerini getirmek için veritabanı çağrılarını yalnızca dakikada bir kez yerine her istekte yapılacaktır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-297">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="3e89e-298">Site trafiği bağlı olarak, bu veritabanı ve ortalama sayfa yükleme süresi şu anda bu hizmet tarafından kullanıma sunulan sorguları üçünü bağlıdır giriş sayfası için yapılan sorguları sayısının çok önemli bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-298">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="3e89e-299">Önbelleğe alma uygulandığında ortaya bir sorun olduğunu *eski veri* – başka bir deyişle, kaynak ancak eski bir sürümü değişti veri önbellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-299">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="3e89e-300">Bu sorunu azaltmak için basit bir yol için meşgul bir uygulama olduğundan verileri önbelleğe uzunluğu genişletme için sınırlı ek avantajı küçük önbellek süreleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-300">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="3e89e-301">Örneğin, bir tek veritabanı sorgusu yapan bir sayfa göz önünde bulundurun ve 10 kez saniyede istenecek.</span><span class="sxs-lookup"><span data-stu-id="3e89e-301">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="3e89e-302">Bu sayfa bir dakika için önbelleğe alınmışsa dakika başına 1, azaltma %99.8 600 bırakma yapılan veritabanı sorguları sayısı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-302">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="3e89e-303">Bunun yerine önbellek süresi bir saat yapılmışsa, genel azaltma %99.997 olacaktır, ancak artık eski veri olasılığı ve olası yaşını her ikisi de önemli ölçüde artırılır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-303">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="3e89e-304">Başka bir yaklaşım içerdikleri veriler güncelleştirildiğinde önceden önbellek girişlerinin kaldırmaktır.</span><span class="sxs-lookup"><span data-stu-id="3e89e-304">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="3e89e-305">Herhangi bir girişe anahtarıyla biliniyorsa kaldırılabilir:</span><span class="sxs-lookup"><span data-stu-id="3e89e-305">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="3e89e-306">Uygulamanızı önbelleğe alır girişleri güncelleştirmek için işlevselliği kullanıma sunan, karşılık gelen önbellek girişlerinin güncelleştirmeleri gerçekleştirir, kodunuzda kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e89e-306">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="3e89e-307">Bazen belirli bir veri kümesine bağımlı birçok farklı girdi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-307">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="3e89e-308">Bu durumda, bir CancellationChangeToken kullanarak önbellek girişlerinin arasındaki bağımlılıkları oluşturmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-308">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="3e89e-309">Bir CancellationChangeToken ile birden fazla önbellek girişlerinin aynı anda belirteci iptal edildiğinde dolabilir.</span><span class="sxs-lookup"><span data-stu-id="3e89e-309">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

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

>[!div class="step-by-step"]
<span data-ttu-id="3e89e-310">[Önceki] (develop-asp-net-core-mvc-apps.md) [sonraki] (test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="3e89e-310">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span></span>
