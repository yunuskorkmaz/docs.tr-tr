---
title: ASP.NET Core Apps'taki verilerle çalışın
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | ASP.NET Core uygulamalarındaki verilerle çalışma
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: b706332b28aec669a841f510046aa7b185be1373
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987848"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="b2a68-103">ASP.NET Çekirdek Uygulamalarda Verilerle Çalışma</span><span class="sxs-lookup"><span data-stu-id="b2a68-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="b2a68-104">"Veri değerli bir şeydir ve sistemlerin kendisinden daha uzun süre dayanır."</span><span class="sxs-lookup"><span data-stu-id="b2a68-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="b2a68-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="b2a68-105">Tim Berners-Lee</span></span>

<span data-ttu-id="b2a68-106">Veri erişimi hemen hemen her yazılım uygulamasının önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="b2a68-107">ASP.NET Core, Entity Framework Core (ve Entity Framework 6 da dahil olmak üzere) dahil olmak üzere çeşitli veri erişim seçeneklerini destekler ve herhangi bir .NET veri erişim çerçevesi ile çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="b2a68-108">Hangi veri erişim çerçevesinin kullanılacağının seçimi, uygulamanın gereksinimlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="b2a68-109">Bu seçenekleri ApplicationCore ve Kullanıcı Arabirimi projelerinden soyutlamak ve uygulama ayrıntılarını Altyapı'da kapsüllemek, gevşek bir şekilde birleştirilmiş, test edilebilir yazılımlar üretmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b2a68-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="b2a68-110">Varlık Framework Core (ilişkisel veritabanları için)</span><span class="sxs-lookup"><span data-stu-id="b2a68-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="b2a68-111">İlişkisel verilerle çalışması gereken yeni bir ASP.NET Core uygulaması yazıyorsanız, Uygulamanızın verilerine erişmesi için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="b2a68-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="b2a68-112">EF Core, .NET geliştiricilerin nesneleri bir veri kaynağına ve kaynaktan kalıcı olarak yapmalarını sağlayan nesne ilişkisisel bir mapper 'dır (O/RM).</span><span class="sxs-lookup"><span data-stu-id="b2a68-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="b2a68-113">Genellikle yazması gereken veri erişim kodu geliştiricilerin çoğu için ihtiyacı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="b2a68-114">ASP.NET Core gibi, EF Core da modüler çapraz platform uygulamalarını desteklemek için sıfırdan yeniden yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="b2a68-115">Başvurunuza NuGet paketi olarak ekler, Başlangıç'ta yapılandırın ve ihtiyacınız olan her yerde bağımlılık enjeksiyonu yoluyla talep edeyim.</span><span class="sxs-lookup"><span data-stu-id="b2a68-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="b2a68-116">SQL Server veritabanıyla EF Core'u kullanmak için aşağıdaki dotnet CLI komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b2a68-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="b2a68-117">Bir InMemory veri kaynağı için destek eklemek için, sınama için:</span><span class="sxs-lookup"><span data-stu-id="b2a68-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="b2a68-118">The DbContext</span><span class="sxs-lookup"><span data-stu-id="b2a68-118">The DbContext</span></span>

<span data-ttu-id="b2a68-119">EF Core ile çalışmak için bir <xref:Microsoft.EntityFrameworkCore.DbContext>alt sınıfa ihtiyacınız var.</span><span class="sxs-lookup"><span data-stu-id="b2a68-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="b2a68-120">Bu sınıf, uygulamanızın çalışacağı varlıkların koleksiyonlarını temsil eden özellikleri tutar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="b2a68-121">eShopOnWeb örneği, öğeler, markalar ve türler için koleksiyonlar içeren bir CatalogContext içerir:</span><span class="sxs-lookup"><span data-stu-id="b2a68-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="b2a68-122">DbContext'Inizin DbContextOptions'ı kabul eden bir oluşturucusu olmalı ve bu bağımsız değişkeni temel DbContext oluşturucuya aktarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="b2a68-123">Uygulamanızda yalnızca bir DbContext varsa, DbContextOptions'ın bir örneğini geçirebilirsiniz, ancak birden fazla seçeneğiniz\<varsa, DbContext türünizde genel parametre olarak geçen genel DbContextOptions T> türünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-123">If you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="b2a68-124">EF Çekirdeğini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b2a68-124">Configuring EF Core</span></span>

<span data-ttu-id="b2a68-125">ASP.NET Core uygulamanızda, genellikle EF Core'u Yapılandırma Hizmetleri yönteminizde yapılandıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="b2a68-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="b2a68-126">EF Core, yapılandırmasını kolaylaştırmak için birkaç yararlı uzantı yöntemini destekleyen bir DbContextOptionsBuilder kullanır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="b2a68-127">CatalogContext'ı Yapılandırma'da tanımlanan bir bağlantı dizesine sahip bir SQL Server veritabanı kullanacak şekilde yapılandırmak için, ConfigureServices'e aşağıdaki kodu eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="b2a68-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="b2a68-128">Bellek veritabanını kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="b2a68-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="b2a68-129">EF Core'u yükledikten, DbContext alt türünü oluşturduktan ve ConfigureServices'te yapılandırdıktan sonra EF Core'u kullanmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="b2a68-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="b2a68-130">DbContext türünizin bir örneğini ihtiyacı olan herhangi bir hizmette isteyebilir ve kalıcı kuruluşlarınızla linq'i yalnızca bir koleksiyondaymış gibi kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="b2a68-131">EF Core, verilerinizi depolamak ve almak için LINQ ifadelerinizi SQL sorgularına çevirme işini yapar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="b2a68-132">EF Core'un yürüttüğü sorguları, bir kaydediciyi yapılandırarak ve düzeyin Şekil 8-1'de gösterildiği gibi en az Bilgi olarak ayarlanmasını sağlayarak görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![EF Core sorgularını konsola günlüğe kaydetme](./media/image8-1.png)

<span data-ttu-id="b2a68-134">**Şekil 8-1**.</span><span class="sxs-lookup"><span data-stu-id="b2a68-134">**Figure 8-1**.</span></span> <span data-ttu-id="b2a68-135">EF Core sorgularını konsola günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="b2a68-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="b2a68-136">Veri alma ve depolama</span><span class="sxs-lookup"><span data-stu-id="b2a68-136">Fetching and storing Data</span></span>

<span data-ttu-id="b2a68-137">EF Core'dan veri almak için uygun özelliğe erişin ve sonucu filtrelemek için LINQ'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2a68-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="b2a68-138">Ayrıca, sonucu bir türden diğerine dönüştürerek projeksiyon gerçekleştirmek için LINQ'yi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="b2a68-139">Aşağıdaki örnek, adlarına göre sıralanan, Etkin özelliği tarafından filtrelenen ve SelectListItem türüne yansıtılan CatalogBrands'i alır:</span><span class="sxs-lookup"><span data-stu-id="b2a68-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="b2a68-140">Yukarıdaki örnekte, sorguyu hemen yürütmek için Çağrı'yı ToListAsync'e eklemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="b2a68-141">Aksi takdirde, ekstre, numaralandırılıncaya kadar yürütülmeyecek bir IQueryable\<SelectListItem> marka öğelere atar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="b2a68-142">Yöntemlerden IQueryable sonuçları dönen artıları ve eksileri vardır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="b2a68-143">EF Core sorgusunun daha da değiştirilmesini sağlar, ancak EF Core'un çeviremediği sorguya işlemler eklenirse yalnızca çalışma zamanında oluşan hatalara da neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="b2a68-144">Herhangi bir filtreyi veri erişimini gerçekleştiren yönteme aktarmak ve sonuç olarak bellek içi bir koleksiyonu\<(örneğin, T> Listesi) döndürmek genellikle daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="b2a68-145">EF Core, kalıcılıktan aldığı varlıklardaki değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="b2a68-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="b2a68-146">İzlenen bir varlıktaki değişiklikleri kaydetmek için, dbContext'da SaveChanges yöntemini arayarak varlığı almak için kullanılan DbContext örneğiyle aynı olduğundan emin olursunuz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="b2a68-147">Varlıkları ekleme ve kaldırma doğrudan uygun DbSet özelliği üzerinde, yine veritabanı komutları yürütmek için SaveChanges bir çağrı ile yapılır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="b2a68-148">Aşağıdaki örnek, varlıkların kalıcılıktan çıkarılmasını, güncellenmesini ve kaldırdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="b2a68-149">EF Core, alma ve kaydetme için hem senkron hem de async yöntemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="b2a68-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="b2a68-150">Web uygulamalarında, veri erişim işlemlerinin tamamlanmasını beklerken web sunucusu iş parçacıklarının engellenmemesi için async/await deseninin async/await deseni kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="b2a68-151">İlgili verileri alma</span><span class="sxs-lookup"><span data-stu-id="b2a68-151">Fetching related data</span></span>

<span data-ttu-id="b2a68-152">EF Core varlıkları aldığında, veritabanında doğrudan bu varlıkla depolanan tüm özellikleri doldurur.</span><span class="sxs-lookup"><span data-stu-id="b2a68-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="b2a68-153">İlgili varlıkların listeleri gibi gezinti özellikleri doldurulmaz ve değerleri null olarak ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="b2a68-154">Bu, EF Core'un gerekenden daha fazla veri getirmemesini sağlar, bu da özellikle web uygulamaları için önemlidir ve bu da istekleri hızlı bir şekilde işlemeli ve yanıtları verimli bir şekilde döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="b2a68-155">_Eager yüklemeyi_kullanarak bir varlıkla ilişkileri eklemek için, sorgudaki Uzantı Ekle yöntemini kullanarak özelliği gösterilir:</span><span class="sxs-lookup"><span data-stu-id="b2a68-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="b2a68-156">Birden çok ilişki ekleyebilirsiniz ve ThenInclude'ı kullanarak alt ilişkileri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-156">You can include multiple relationships, and you can also include subrelationships using ThenInclude.</span></span> <span data-ttu-id="b2a68-157">EF Core, ortaya çıkan varlık kümesini almak için tek bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="b2a68-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="b2a68-158">Alternatif olarak bir '' geçerek navigasyon özellikleri navigasyon özellikleri ekleyebilirsiniz. `.Include()` -uzantısı yöntemine ayrılmış dize, böyle:</span><span class="sxs-lookup"><span data-stu-id="b2a68-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include("Items.Products")
```

<span data-ttu-id="b2a68-159">Filtreleme mantığını kapsüllemenin yanı sıra, bir belirtim, hangi özelliklerin doldurulması gerektiği de dahil olmak üzere döndürülecek verilerin şeklini de belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="b2a68-160">eShopOnWeb örnek belirtimi içinde istekli yükleme bilgileri kapsülleme gösteren çeşitli özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="b2a68-161">Belirtimin sorgunun bir parçası olarak nasıl kullanıldığını burada görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2a68-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="b2a68-162">İlgili verileri yüklemek için başka bir seçenek _açık yükleme_kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="b2a68-163">Açık yükleme, zaten alınmış bir varlığa ek veri yüklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="b2a68-164">Bu veritabanına ayrı bir istek içerdiğinden, istek başına yapılan veritabanı turu sayısını en aza indirmek gerekir web uygulamaları için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b2a68-164">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="b2a68-165">_Tembel yükleme,_ uygulama tarafından başvurulan ilgili verileri otomatik olarak yükleyen bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="b2a68-166">EF Core sürüm 2.1 tembel yükleme için destek ekledi.</span><span class="sxs-lookup"><span data-stu-id="b2a68-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="b2a68-167">Tembel yükleme varsayılan olarak etkin değildir `Microsoft.EntityFrameworkCore.Proxies`ve .' yi yüklemeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="b2a68-168">Açık yüklemede olduğu gibi, kullanımı her web isteği içinde ek veritabanı sorguları yapılmasıyla sonuçlanacaktır, çünkü tembel yükleme genellikle web uygulamaları için devre dışı bırakılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="b2a68-169">Ne yazık ki, tembel yükleme nin neden olduğu genel gider genellikle geliştirme sırasında fark edilmez, gecikme süresi küçük olduğunda ve genellikle test için kullanılan veri kümeleri küçükolduğunda.</span><span class="sxs-lookup"><span data-stu-id="b2a68-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="b2a68-170">Ancak, üretimde, daha fazla kullanıcı, daha fazla veri ve daha fazla gecikme süresiyle, ek veritabanı istekleri genellikle tembel yüklemeden yoğun olarak kullanan web uygulamaları için düşük performansa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="b2a68-171">Web Uygulamalarında Tembel Yükleme Varlıklarından Kaçının</span><span class="sxs-lookup"><span data-stu-id="b2a68-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="b2a68-172">Verileri kapsülleme</span><span class="sxs-lookup"><span data-stu-id="b2a68-172">Encapsulating data</span></span>

<span data-ttu-id="b2a68-173">EF Core, modelinizin durumunu düzgün bir şekilde kapsüllemesine olanak tanıyan çeşitli özellikleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b2a68-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="b2a68-174">Etki alanı modellerinde sık karşılaşılan bir sorun, koleksiyon gezinti özelliklerini genel olarak erişilebilen liste türleri olarak ortaya çıkarmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="b2a68-175">Bu, herhangi bir ortak bilgi nisabı, koleksiyonla ilgili önemli iş kurallarını atlayarak nesneyi geçersiz bir durumda bırakabilecek bu koleksiyon türlerinin içeriğini işlemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-175">This allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="b2a68-176">Bunun çözümü, ilgili koleksiyonlara salt okunur erişimi ortaya çıkarmak ve bu örnekte olduğu gibi istemcilerin bunları manipüle etme yollarını tanımlayan yöntemler açıkça sağlamaktır:</span><span class="sxs-lookup"><span data-stu-id="b2a68-176">The solution to this is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

<span data-ttu-id="b2a68-177">Bu varlık türü bir ortak `List` `ICollection` veya özellik ortaya çıkarmaz, ancak bunun yerine temel Liste türünü saran bir `IReadOnlyCollection` türü ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-177">This entity type doesn't expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="b2a68-178">Bu deseni kullanırken, destek alanını aşağıdaki gibi kullanmak üzere Entity Framework Core'a belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2a68-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="b2a68-179">Etki alanı modelinizi geliştirmenin başka bir yolu da, kimlik eksikliği olan ve yalnızca özellikleriyle ayırt edilen türler için değer nesnelerinin kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="b2a68-180">Varlıklarınızın özellikleri gibi türleri kullanmak, mantığıa ait olduğu değer nesnesine özgü tutmaya yardımcı olabilir ve aynı kavramı kullanan birden çok varlık arasında yinelenen mantıktan kaçınabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="b2a68-181">Varlık Framework Core'da, türü sahipolunan bir varlık olarak yapılandırarak, değer nesnelerini sahipleriyle aynı tabloda kalıcı olarak sürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2a68-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="b2a68-182">Bu örnekte, `ShipToAddress` özellik türü. `Address`</span><span class="sxs-lookup"><span data-stu-id="b2a68-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="b2a68-183">`Address`gibi çeşitli özelliklere sahip bir `Street` `City`değer nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="b2a68-184">EF Core, `Order` nesneyi her özellik `Address` başına bir sütunla tablosuyla eşler ve her sütun adını özelliğin adıyla öne çözer.</span><span class="sxs-lookup"><span data-stu-id="b2a68-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="b2a68-185">Bu örnekte, `Order` tablo gibi `ShipToAddress_Street` sütunlar `ShipToAddress_City`içerecektir ve .</span><span class="sxs-lookup"><span data-stu-id="b2a68-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span> <span data-ttu-id="b2a68-186">İstenirse, sahip olunan türleri ayrı tablolarda depolamak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b2a68-186">It's also possible to store owned types in separate tables, if desired.</span></span>

<span data-ttu-id="b2a68-187">[EF Core'da](/ef/core/modeling/owned-entities)sahip olunan varlık desteği hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="b2a68-187">Learn more about owned [entity support in EF Core](/ef/core/modeling/owned-entities).</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="b2a68-188">Esnek bağlantılar</span><span class="sxs-lookup"><span data-stu-id="b2a68-188">Resilient connections</span></span>

<span data-ttu-id="b2a68-189">SQL veritabanları gibi dış kaynaklar bazen kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-189">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="b2a68-190">Geçici kullanılabilirlik durumlarında, uygulamalar bir özel durum yükseltmeyi önlemek için yeniden deneme mantığını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-190">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="b2a68-191">Bu teknik genellikle bağlantı _esnekliği_olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-191">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="b2a68-192">Üstel geri [leme tekniğiyle,](https://docs.microsoft.com/azure/architecture/patterns/retry) en yüksek yeniden deneme sayısına ulaşılıncaya kadar katlanarak artan bekleme süresiyle yeniden denemeyi deneyerek kendi yeniden denemenizi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-192">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="b2a68-193">Bu teknik, bulut kaynaklarının kısa süreler için zaman zaman kullanılamayabileceği ve bazı isteklerin başarısız lığa yol açabileceği gerçeğini benimser.</span><span class="sxs-lookup"><span data-stu-id="b2a68-193">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="b2a68-194">Azure SQL DB için Entity Framework Core zaten dahili veritabanı bağlantısı esnekliği ve yeniden deneme mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-194">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="b2a68-195">Ancak esnek EF Core bağlantılarına sahip olmak istiyorsanız, her DbContext bağlantısı için Varlık Çerçevesi yürütme stratejisini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-195">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="b2a68-196">Örneğin, EF Core bağlantı düzeyindeki aşağıdaki kod, bağlantı başarısız olursa yeniden denenen esnek SQL bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-196">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="b2a68-197">BeginTransaction ve birden çok DbContexts kullanarak yürütme stratejileri ve açık işlemler</span><span class="sxs-lookup"><span data-stu-id="b2a68-197">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="b2a68-198">EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden çalışılabilir işlemi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-198">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="b2a68-199">Geçici bir hata oluşursa, SaveChanges'a yapılan her sorgu ve her çağrı birim olarak yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-199">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="b2a68-200">Ancak, kodunuz BeginTransaction kullanarak bir işlem başlatıyorsa, birim olarak işlem yapılması gereken kendi işlem grubunuzu tanımlıyorsunuz; bir hata oluşursa, işlem içindeki her şeyin geri alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-200">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="b2a68-201">Bir EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu işlemi yürütmeye çalışırsanız ve içinde birden çok DbContexts'tan birkaç SaveChanges eklerseniz, aşağıdaki gibi bir özel durum görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-201">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="b2a68-202">System.InvalidOperationException: Yapılandırılan yürütme stratejisi 'SqlServerRetryingExecutionStrategy' kullanıcı tarafından başlatılan hareketleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b2a68-202">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="b2a68-203">İşlemdeki tüm işlemleri yeniden denilebilir bir birim olarak yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2a68-203">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retryable unit.</span></span>

<span data-ttu-id="b2a68-204">Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-204">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="b2a68-205">Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-205">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="b2a68-206">Aşağıdaki kod, bu yaklaşımın nasıl uygulanacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="b2a68-206">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="b2a68-207">İlk DbContext \_catalogContext ve ikinci DbContext entegrasyonEventLogService nesneiçindedir. \_</span><span class="sxs-lookup"><span data-stu-id="b2a68-207">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="b2a68-208">Son olarak, Commit eylem birden çok DbContexts ve bir EF Yürütme Stratejisi kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-208">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="b2a68-209">Referanslar – Varlık Çerçeve Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="b2a68-209">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="b2a68-210">**EF Çekirdek Dokümanlar**
>   <https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="b2a68-210">**EF Core Docs**
<https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="b2a68-211">**EF Core: İlgili Veriler**
>   <https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="b2a68-211">**EF Core: Related Data**
<https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="b2a68-212">**ASPNET Uygulamalarında Tembel Yükleme Varlıklarından Kaçının**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="b2a68-212">**Avoid Lazy Loading Entities in ASPNET Applications**
<https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="b2a68-213">EF Core veya mikro-ORM?</span><span class="sxs-lookup"><span data-stu-id="b2a68-213">EF Core or micro-ORM?</span></span>

<span data-ttu-id="b2a68-214">EF Core kalıcılığı yönetmek için mükemmel bir seçim olsa da ve çoğunlukla uygulama geliştiricilerin veritabanı ayrıntılarını kapsüller, tek seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-214">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn't the only choice.</span></span> <span data-ttu-id="b2a68-215">Başka bir popüler açık kaynak alternatif [Dapper](https://github.com/StackExchange/Dapper), sözde mikro-ORM olduğunu.</span><span class="sxs-lookup"><span data-stu-id="b2a68-215">Another popular open-source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="b2a68-216">Mikro-ORM, nesneleri veri yapılarına eşlemek için daha hafif ve daha az özellikli bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-216">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="b2a68-217">Dapper'ın durumunda, tasarım hedefleri verileri almak ve güncelleştirmek için kullandığı temel sorguları tam olarak kapsüllemek yerine performansa odaklanır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-217">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="b2a68-218">Sql'i geliştiriciden soyutlamadığı için, Dapper "metale daha yakındır" ve geliştiricilerin belirli bir veri erişim işlemi için tam olarak kullanmak istedikleri sorguları yazmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-218">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="b2a68-219">EF Core, dapper onu ayıran ama aynı zamanda performans yükü eklemek sağlayan iki önemli özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-219">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="b2a68-220">Bunlardan ilki LINQ ifadelerinden SQL'e çevrilmedir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-220">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="b2a68-221">Bu çeviriler önbelleğe alınmış, ancak yine de ilk kez bunları gerçekleştirmek için havai vardır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-221">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="b2a68-222">İkincisi, varlıklar üzerinde değişiklik izleme (verimli güncelleştirme deyimleri oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-222">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="b2a68-223">Bu davranış, AsNotTracking uzantısı kullanılarak belirli sorgular için kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-223">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="b2a68-224">EF Core ayrıca, genellikle çok verimli ve her durumda mükemmel bir performans açısından kabul edilebilir SQL sorguları oluşturur, ancak yürütülecek kesin sorgu üzerinde ince denetim gerekiyorsa, özel SQL (veya depolanmış bir yordam yürütmek) ef Core kullanarak da geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-224">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="b2a68-225">Bu durumda, Dapper hala EF Core daha iyi performans, ama sadece biraz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-225">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="b2a68-226">Julie Lerman, Mayıs 2016'daki MSDN makalesi [Dapper, Entity Framework ve Hybrid Apps'da](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps)bazı performans verileri sunar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-226">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span></span> <span data-ttu-id="b2a68-227">Çeşitli veri erişim yöntemleri için ek performans kıyaslama verileri [Dapper sitesinde](https://github.com/StackExchange/Dapper)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-227">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="b2a68-228">Dapper sözdiziminin EF Core'dan nasıl değiştiğini görmek için, öğelerin listesini almak için aynı yöntemin bu iki sürümü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b2a68-228">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="b2a68-229">Dapper ile daha karmaşık nesne grafikleri oluşturmanız gerekiyorsa, ilişkili sorguları kendiniz yazmanız gerekir (EF Core'da yaptığınız gibi bir Include eklemek yerine).</span><span class="sxs-lookup"><span data-stu-id="b2a68-229">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="b2a68-230">Bu, tek tek satırları birden çok eşlenen nesnelerle eşleştirmenize olanak tanıyan Çoklu Eşleme adlı bir özellik de dahil olmak üzere çeşitli sözdizimilerle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-230">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="b2a68-231">Örneğin, bir özellik Sahibi Kullanıcı ile bir sınıf Post verilen, aşağıdaki SQL gerekli tüm verileri döndürür:</span><span class="sxs-lookup"><span data-stu-id="b2a68-231">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="b2a68-232">Döndürülen her satır hem Kullanıcı hem de Posta verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-232">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="b2a68-233">Kullanıcı verilerinin Sahibi özelliği aracılığıyla Posta verilerine eklenmesi gerektiğinden, aşağıdaki işlev kullanılır:</span><span class="sxs-lookup"><span data-stu-id="b2a68-233">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="b2a68-234">İlişkili kullanıcı verileriyle dolu Sahibi mülkü olan gönderikoleksiyonunu döndürmek için tam kod listesi aşağıdakiler olacaktır:</span><span class="sxs-lookup"><span data-stu-id="b2a68-234">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="b2a68-235">Daha az kapsülleme sunduğundan, Dapper geliştiricilerin verilerinin nasıl depolandığı, verimli bir şekilde nasıl sorgulanacakları ve getirmek için daha fazla kod yazmaları hakkında daha fazla bilgi sahibi olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-235">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="b2a68-236">Model değiştiğinde, yalnızca yeni bir geçiş (başka bir EF Core özelliği) oluşturmak ve/veya eşleme bilgilerini DbContext'da tek bir yerde güncelleştirmek yerine, etkilenen her sorgu güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-236">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="b2a68-237">Bu sorguların derleme zamanı garantisi yoktur, bu nedenle model veya veritabanındaki değişikliklere yanıt olarak çalışma zamanında bozulabilir ve hataların hızlı bir şekilde algılatılması zorolabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-237">These queries have no compile-time guarantees, so they may break at run time in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="b2a68-238">Bu takaslar karşılığında Dapper son derece hızlı bir performans sergiliyor.</span><span class="sxs-lookup"><span data-stu-id="b2a68-238">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="b2a68-239">EF Core, çoğu uygulama ve hemen hemen tüm uygulamaların çoğu nda kabul edilebilir performans sunar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-239">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="b2a68-240">Böylece, geliştirici verimlilik yararları performans yükü ağır basması muhtemeldir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-240">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="b2a68-241">Önbelleğe alma dan yararlanabilir sorgular için, gerçek sorgu yalnızca zaman küçük bir yüzdesi yürütülebilir, nispeten küçük sorgu performans farkları tartışmalı hale.</span><span class="sxs-lookup"><span data-stu-id="b2a68-241">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="b2a68-242">SQL veya NoSQL</span><span class="sxs-lookup"><span data-stu-id="b2a68-242">SQL or NoSQL</span></span>

<span data-ttu-id="b2a68-243">Geleneksel olarak, SQL Server gibi ilişkisel veritabanları kalıcı veri depolama için pazar hakim, ancak tek çözüm mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-243">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="b2a68-244">[MongoDB](https://www.mongodb.com/what-is-mongodb) gibi NoSQL veritabanları nesneleri depolamak için farklı bir yaklaşım sunar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-244">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="b2a68-245">Nesneleri tablolarla ve satırlarla eşlemek yerine, başka bir seçenek tüm nesne grafiğini seri hale getirmek ve sonucu depolamaktır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-245">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="b2a68-246">Bu yaklaşımın yararları, en azından başlangıçta, basitlik ve performans vardır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-246">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="b2a68-247">Tek bir serileştirilmiş nesneyi anahtarla depolamak, nesneyi veritabanından en son alınan nesneden beri değişmiş olabilecek ilişkiler ve güncelleştirme ve satırlarla birçok tabloya ayırmaktan daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-247">It's simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="b2a68-248">Benzer şekilde, tek bir nesneyi anahtar tabanlı bir depodan alma ve çıkarma genellikle karmaşık birleştirmelerden veya ilişkisel bir veritabanından aynı nesneyi tam olarak oluşturmak için gereken birden çok veritabanı sorgusundan çok daha hızlı ve kolaydır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-248">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="b2a68-249">Kilitlerin veya hareketlerin veya sabit bir şema nın olmaması, NoSQL veritabanlarını çok büyük veri kümelerini destekleyerek birçok makinede ölçeklenmeye elverişli hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-249">The lack of locks or transactions or a fixed schema also makes NoSQL databases amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="b2a68-250">Öte yandan, NoSQL veritabanları (genellikle denir) kendi dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-250">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="b2a68-251">İlişkisel veritabanları tutarlılığı zorlamak ve verilerin çoğaltılmasını önlemek için normalleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-251">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="b2a68-252">Bu, veritabanının toplam boyutunu azaltır ve paylaşılan verilere yapılan güncelleştirmelerin veritabanı nda hemen kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-252">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="b2a68-253">İlişkisel bir veritabanında, Adres tablosu, bir ülke/bölgenin adı değiştirilirse, adres kayıtlarının kendilerinin güncelleştirilmelerine gerek kalmadan güncelleştirmeden yararlanacağı şekilde, bir Ülke tablosuna kimlik le başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-253">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="b2a68-254">Ancak, Bir NoSQL veritabanında, Adres ve ilişkili Ülke birçok depolanan nesnelerin bir parçası olarak serileştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-254">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="b2a68-255">Bir ülke/bölge adına yapılan bir güncelleştirme, tek bir satır yerine tüm bu nesnelerin güncelleştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-255">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="b2a68-256">İlişkisel veritabanları da yabancı anahtarlar gibi kuralları uygulayarak ilişkisel bütünlüğü sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-256">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="b2a68-257">NoSQL veritabanları genellikle verilerinde bu tür kısıtlamalar sunmuyoruz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-257">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="b2a68-258">NoSQL veritabanlarının uğraşması gereken bir diğer karmaşıklık ise sürümdür.</span><span class="sxs-lookup"><span data-stu-id="b2a68-258">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="b2a68-259">Bir nesnenin özellikleri değiştiğinde, depolanan geçmiş sürümlerden deserialed mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-259">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="b2a68-260">Bu nedenle, nesnenin serileştirilmiş (önceki) sürümüne sahip varolan tüm nesnelerin yeni şemasına uyacak şekilde güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-260">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="b2a68-261">Bu, şema değişikliklerinin bazen güncelleştirme komut dosyaları veya eşleme güncelleştirmeleri gerektirdiği ilişkisel bir veritabanından kavramsal olarak farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-261">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="b2a68-262">Ancak, değiştirilmesi gereken giriş sayısı, daha fazla veri yinelemesi olduğundan, NoSQL yaklaşımında genellikle çok daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-262">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="b2a68-263">NoSQL veritabanlarında nesnelerin birden çok sürümlerini depolamak mümkündür, sabit şema ilişkisel veritabanları genellikle desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b2a68-263">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="b2a68-264">Ancak, bu durumda uygulama kodunuzu nesnelerin önceki sürümlerinin varlığını hesaba katmak gerekir, ek karmaşıklık ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="b2a68-264">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="b2a68-265">NoSQL veritabanları genellikle [ACID](https://en.wikipedia.org/wiki/ACID)zorlamaz, bu da ilişkisel veritabanları üzerinde hem performans hem de ölçeklenebilirlik avantajları olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-265">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="b2a68-266">Bunlar, normalleştirilmiş tablo yapılarında depolamaiçin uygun olmayan son derece büyük veri kümeleri ve nesneler için uygundur.</span><span class="sxs-lookup"><span data-stu-id="b2a68-266">They're well suited to extremely large datasets and objects that are not well suited to storage in normalized table structures.</span></span> <span data-ttu-id="b2a68-267">Tek bir uygulamanın hem ilişkisel hem de NoSQL veritabanlarından yararlanamaması için hiçbir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="b2a68-267">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-cosmos-db"></a><span data-ttu-id="b2a68-268">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="b2a68-268">Azure Cosmos DB</span></span>

<span data-ttu-id="b2a68-269">Azure Cosmos DB, bulut tabanlı şema içermeyen veri depolama sunan tam olarak yönetilen bir NoSQL veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-269">Azure Cosmos DB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="b2a68-270">Azure Cosmos DB, hızlı ve öngörülebilir performans, yüksek kullanılabilirlik, elastik ölçekleme ve küresel dağıtım için üretilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-270">Azure Cosmos DB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="b2a68-271">NoSQL veritabanı olmasına rağmen, geliştiriciler JSON verilerinde zengin ve tanıdık SQL sorgu özelliklerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-271">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="b2a68-272">Azure Cosmos DB'deki tüm kaynaklar JSON belgeleri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-272">All resources in Azure Cosmos DB are stored as JSON documents.</span></span> <span data-ttu-id="b2a68-273">Kaynaklar, meta veri içeren belgeler ve öğelerin koleksiyonları olan _özet akışları_olan _öğeler_olarak yönetilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-273">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="b2a68-274">Şekil 8-2, farklı Azure Cosmos DB kaynakları arasındaki ilişkiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-274">Figure 8-2 shows the relationship between different Azure Cosmos DB resources.</span></span>

![NoSQL JSON veritabanı olan Azure Cosmos DB'deki kaynaklar arasındaki hiyerarşik ilişki](./media/image8-2.png)

<span data-ttu-id="b2a68-276">**Şekil 8-2.**</span><span class="sxs-lookup"><span data-stu-id="b2a68-276">**Figure 8-2.**</span></span> <span data-ttu-id="b2a68-277">Azure Cosmos DB kaynak organizasyonu.</span><span class="sxs-lookup"><span data-stu-id="b2a68-277">Azure Cosmos DB resource organization.</span></span>

<span data-ttu-id="b2a68-278">Azure Cosmos DB sorgu dili, JSON belgelerini sorgulamak için basit ama güçlü bir arayüzdür.</span><span class="sxs-lookup"><span data-stu-id="b2a68-278">The Azure Cosmos DB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="b2a68-279">Dil, ANSI SQL dil bilgisinin bir alt kümesini destekler ve JavaScript nesnesi, dizileri, nesne oluşturması ve işlev çağrısı için derin tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2a68-279">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="b2a68-280">**Referanslar – Azure Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="b2a68-280">**References – Azure Cosmos DB**</span></span>

- <span data-ttu-id="b2a68-281">Azure Cosmos DB Giriş<https://docs.microsoft.com/azure/cosmos-db/introduction></span><span class="sxs-lookup"><span data-stu-id="b2a68-281">Azure Cosmos DB Introduction <https://docs.microsoft.com/azure/cosmos-db/introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="b2a68-282">Diğer kalıcılık seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b2a68-282">Other persistence options</span></span>

<span data-ttu-id="b2a68-283">İlişkisel ve NoSQL depolama seçeneklerine ek olarak, ASP.NET Core uygulamaları çeşitli veri biçimlerini ve dosyalarını bulut tabanlı, ölçeklenebilir bir şekilde depolamak için Azure Depolama'yı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-283">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="b2a68-284">Azure Depolama büyük ölçüde ölçeklenebilir, böylece küçük miktarlarda veri depolamaya başlayabilir ve uygulamanız gerektiriyorsa yüzlerce veya terabayt depolayacak kadar ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-284">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="b2a68-285">Azure Depolama dört veri çeşidini destekler:</span><span class="sxs-lookup"><span data-stu-id="b2a68-285">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="b2a68-286">Nesne depolama olarak da adlandırılan, yapılandırılmamış metin veya ikili depolama için Blob Depolama.</span><span class="sxs-lookup"><span data-stu-id="b2a68-286">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="b2a68-287">Yapılandırılmış veri kümeleri için Tablo Depolama, satır tuşları ile erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-287">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="b2a68-288">Güvenilir sıra tabanlı iletiler için Sıra Depolama.</span><span class="sxs-lookup"><span data-stu-id="b2a68-288">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="b2a68-289">Azure sanal makineleri ve şirket içi uygulamalar arasında paylaşılan dosya erişimi için Dosya Depolama.</span><span class="sxs-lookup"><span data-stu-id="b2a68-289">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="b2a68-290">**Referanslar – Azure Depolama**</span><span class="sxs-lookup"><span data-stu-id="b2a68-290">**References – Azure Storage**</span></span>

- <span data-ttu-id="b2a68-291">Azure Depolama Girişi<https://docs.microsoft.com/azure/storage/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="b2a68-291">Azure Storage Introduction <https://docs.microsoft.com/azure/storage/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="b2a68-292">Önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="b2a68-292">Caching</span></span>

<span data-ttu-id="b2a68-293">Web uygulamalarında, her web isteği mümkün olan en kısa sürede tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-293">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="b2a68-294">Bunu başarmanın bir yolu, sunucunun isteği tamamlamak için yapması gereken dış arama sayısını sınırlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-294">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="b2a68-295">Önbelleğe alma, sunucuda (veya veri kaynağından daha kolay sorgulanan başka bir veri deposunda) bir veri kopyasını depolamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-295">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="b2a68-296">Web uygulamaları ve özellikle SPA olmayan geleneksel web uygulamaları, her istek ile tüm kullanıcı arabirimi oluşturmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-296">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="b2a68-297">Bu, sık sık aynı veritabanı sorgularının çoğunu bir kullanıcı isteğinden diğerine tekrar tekrar yapmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-297">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="b2a68-298">Çoğu durumda, bu veriler nadiren değişir, bu nedenle veritabanından sürekli olarak istemek için çok az neden vardır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-298">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="b2a68-299">ASP.NET Core, tüm sayfaların önbelleğe alınmış şekilde önbelleğe alınmış yanıtını ve daha ayrıntılı önbelleğe alma davranışını destekleyen veri önbelleğe alma özelliğini destekler.</span><span class="sxs-lookup"><span data-stu-id="b2a68-299">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="b2a68-300">Önbelleğe alma uygularken, endişeleri ayrıştırmayı göz önünde bulundurmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-300">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="b2a68-301">Veri erişim mantığınızda veya kullanıcı arabiriminizde önbelleğe alma mantığı uygulamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="b2a68-301">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="b2a68-302">Bunun yerine, önbelleğe alma kapamayı kendi sınıflarında saklar ve davranışını yönetmek için yapılandırmayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2a68-302">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="b2a68-303">Bu, Açık/Kapalı ve Tek Sorumluluk ilkelerini izler ve büyüdükçe uygulamanızda önbelleğe alma nızı yönetmenize kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-303">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="b2a68-304">ASP.NET Çekirdek yanıt önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="b2a68-304">ASP.NET Core response caching</span></span>

<span data-ttu-id="b2a68-305">ASP.NET Core iki yanıt önbelleğe alma düzeylerini destekler.</span><span class="sxs-lookup"><span data-stu-id="b2a68-305">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="b2a68-306">İlk düzey sunucuda hiçbir şeyi önbelleğe almaz, ancak istemcileri ve proxy sunucularını önbellek yanıtlarına öğreten HTTP üstbilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="b2a68-306">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="b2a68-307">Bu, yanıt önbellek özniteliğini tek tek denetleyicilere veya eylemlere ekleyerek uygulanır:</span><span class="sxs-lookup"><span data-stu-id="b2a68-307">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="b2a68-308">Önceki örnek, aşağıdaki üstbilginin yanıta eklenmesiyle sonuçlanır ve istemcilere sonucu 60 saniyeye kadar önbelleğe almalarını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-308">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="b2a68-309">Önbellek-Kontrol: kamu, max-age=60</span><span class="sxs-lookup"><span data-stu-id="b2a68-309">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="b2a68-310">Uygulamaya sunucu tarafı bellek önbelleğe almak için Microsoft.AspNetCore.ResponseCaching NuGet paketine başvurmanız ve ardından Yanıt Önbelleği ara takımını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-310">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="b2a68-311">Bu ara yazılım, Hem Yapılandırma Hizmetleri'nde hem de Başlangıç'ta Yapılandırıldığında yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="b2a68-311">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

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

<span data-ttu-id="b2a68-312">Yanıt Önbelleğe Alma Middleware, özelleştirebileceğiniz bir dizi koşula bağlı olarak yanıtları otomatik olarak önbelleğe alacaktır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-312">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="b2a68-313">Varsayılan olarak, GET veya HEAD yöntemleri yle istenen yalnızca 200 (Tamam) yanıt önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-313">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="b2a68-314">Buna ek olarak, isteklerin önbellek denetimi yle yanıt vermesi gerekir: genel üstbilgi ve Yetkilendirme veya Ayar-Çerez üstbilgi içeremez.</span><span class="sxs-lookup"><span data-stu-id="b2a68-314">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="b2a68-315">Ara [yazılım önbelleğe alma yanıtı tarafından kullanılan önbelleğe alma koşullarının tam listesine](/aspnet/core/performance/caching/middleware#conditions-for-caching)bakın.</span><span class="sxs-lookup"><span data-stu-id="b2a68-315">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="b2a68-316">Verileri önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="b2a68-316">Data caching</span></span>

<span data-ttu-id="b2a68-317">Tam web yanıtlarını önbelleğe almak (veya buna ek olarak) yerine, tek tek veri sorgularının sonuçlarını önbelleğe alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-317">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="b2a68-318">Bunun için, bellek önbelleğe alma web sunucusunda kullanabilirsiniz veya [dağıtılmış bir önbellek](/aspnet/core/performance/caching/distributed)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-318">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="b2a68-319">Bu bölümde bellek önbelleğe nasıl uygulanacağını gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-319">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="b2a68-320">ConfigureServices'te bellek (veya dağıtılmış) önbelleğe alma desteği eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="b2a68-320">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="b2a68-321">Microsoft.Extensions.Caching.Memory NuGet paketini de eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b2a68-321">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="b2a68-322">Hizmeti ekledikten sonra, önbelleğe erişmek için ihtiyacınız olan her yerde bağımlılık enjeksiyonu yoluyla IMemoryCache'yi talep edeyim.</span><span class="sxs-lookup"><span data-stu-id="b2a68-322">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="b2a68-323">Bu örnekte, CachedCatalogService, temel CatalogService uygulamasına erişimi kontrol eden (veya davranış ekleyen) ICatalogService'in alternatif bir uygulamasını sağlayarak Proxy (veya Dekoratör) tasarım deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-323">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
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
        string cacheKey = $"items-{pageIndex}-{itemsPage}-{brandID}-{typeId}";
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

<span data-ttu-id="b2a68-324">Uygulamayı hizmetin önbelleğe alınmış sürümünü kullanacak şekilde yapılandırmak, ancak yine de hizmetin, oluşturucusunda ihtiyaç duyduğu CatalogService örneğini almasına izin vermek için, ConfigureServices'e aşağıdakileri eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="b2a68-324">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="b2a68-325">Bu durumda, veritabanı katalog verilerini almak için her istek yerine dakikada yalnızca bir kez yapılır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-325">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="b2a68-326">Siteye gelen trafiğe bağlı olarak, bu veritabanına yapılan sorguların sayısı ve şu anda bu hizmet tarafından maruz kalan sorguların üçüne de bağlı olan ana sayfanın ortalama sayfa yükleme süresi üzerinde önemli bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-326">Depending on the traffic to the site, this can have a significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="b2a68-327">Önbelleğe alma uygulandığında ortaya çıkan bir sorun _eski verilerdir_ – yani kaynakta değişen ancak güncel olmayan bir sürüm önbellekte kalan verilerdir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-327">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out-of-date version remains in the cache.</span></span> <span data-ttu-id="b2a68-328">Meşgul bir uygulama için önbelleğe alınan uzunluk verilerini genişletmenin sınırlı ek yararı olduğundan, bu sorunu azaltmanın basit bir yolu küçük önbellek süreleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-328">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="b2a68-329">Örneğin, tek bir veritabanı sorgusu yapan ve saniyede 10 kez istenen bir sayfayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="b2a68-329">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="b2a68-330">Bu sayfa bir dakika süreyle önbelleğe alınmışsa, dakikada yapılan veritabanı sorgularının sayısının 600'den 1'e düşmesine ve %99,8'lik bir azalmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="b2a68-330">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="b2a68-331">Bunun yerine önbellek süresi bir saat yapılmış olsaydı, genel azaltma% 99.997 olurdu, ancak şimdi olasılık ve eski veri potansiyel yaş hem önemli ölçüde artmıştır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-331">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="b2a68-332">Başka bir yaklaşım, içerdikleri veriler güncelleştirildiğinde önbellek girişlerini proaktif olarak kaldırmaktır.</span><span class="sxs-lookup"><span data-stu-id="b2a68-332">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="b2a68-333">Anahtarı biliniyorsa, herhangi bir tek tek giriş kaldırılabilir:</span><span class="sxs-lookup"><span data-stu-id="b2a68-333">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="b2a68-334">Uygulamanız önbelleğe aldığı girişleri güncelleştirme işlevini ortaya çıkarırsa, kodunuzda güncelleştirmeleri gerçekleştiren ilgili önbellek girişlerini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a68-334">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="b2a68-335">Bazen belirli bir veri kümesine bağlı birçok farklı giriş olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-335">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="b2a68-336">Bu durumda, bir İptalChangeToken kullanarak önbellek girişleri arasında bağımlılıklar oluşturmak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-336">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="b2a68-337">İptalChangeToken ile, belirteci iptal ederek aynı anda birden çok önbellek girişi nin süresi dolabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-337">With a CancellationChangeToken, you can expire multiple cache entries at once by canceling the token.</span></span>

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

<span data-ttu-id="b2a68-338">Önbelleğe alma, veritabanından aynı değerleri tekrar tekrar isteyen web sayfalarının performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-338">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="b2a68-339">Önbelleğe alma uygulamadan önce veri erişimini ve sayfa performansını ölçtüğüğünden ve yalnızca iyileştirme gereksinimini gördüğünüz durumlarda önbelleğe aldığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b2a68-339">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="b2a68-340">Önbelleğe alma, web sunucusu bellek kaynaklarını tüketir ve uygulamanın karmaşıklığını artırır, bu nedenle bu tekniği kullanarak zamanından önce optimize etmemeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b2a68-340">Caching consumes web server memory resources and increases the complexity of the application, so it's important you don't prematurely optimize using this technique.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b2a68-341">[Önceki](develop-asp-net-core-mvc-apps.md)
>[Sonraki](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="b2a68-341">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
