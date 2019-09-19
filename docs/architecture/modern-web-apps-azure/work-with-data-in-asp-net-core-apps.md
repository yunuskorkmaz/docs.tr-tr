---
title: ASP.NET Core uygulamalarda verilerle çalışma
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın ASP.NET Core uygulamalarında verilerle çalışma
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 9d9e75767f5ed5010f618d5dbe1e58fe79454597
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117294"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="8a30b-103">ASP.NET Core uygulamalarında verilerle çalışma</span><span class="sxs-lookup"><span data-stu-id="8a30b-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="8a30b-104">"Veriler, en çok değerli bir şeydir ve sistemlerden daha uzun süre sonra kalır."</span><span class="sxs-lookup"><span data-stu-id="8a30b-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="8a30b-105">Tim Beranlar-eser</span><span class="sxs-lookup"><span data-stu-id="8a30b-105">Tim Berners-Lee</span></span>

<span data-ttu-id="8a30b-106">Veri erişimi, neredeyse tüm yazılım uygulamalarının önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="8a30b-107">ASP.NET Core, Entity Framework Core (ve Entity Framework 6 de) dahil olmak üzere çeşitli veri erişim seçeneklerini destekler ve tüm .NET veri erişim çerçevesiyle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="8a30b-108">Hangi veri erişimi çerçevesinin kullanılacağı seçimi uygulamanın ihtiyaçlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="8a30b-109">Bu seçeneklerin ApplicationCore ve UI projelerinden soyutlanmasıdır ve altyapıdaki uygulama ayrıntılarının kapsüllenmesi, gevşek olarak bağlanmış, test edilebilir yazılımlar üretmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="8a30b-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="8a30b-110">Entity Framework Core (ilişkisel veritabanları için)</span><span class="sxs-lookup"><span data-stu-id="8a30b-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="8a30b-111">İlişkisel verilerle çalışması gereken yeni bir ASP.NET Core uygulaması yazıyorsanız, uygulamanızın verilerine erişmesi için önerilen yol Entity Framework Core (EF Core).</span><span class="sxs-lookup"><span data-stu-id="8a30b-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="8a30b-112">EF Core, .NET geliştiricilerin nesneleri bir veri kaynağından ve veritabanından kalıcı hale getirebilmesine olanak tanıyan bir nesne ilişkisel Eşleyici (O/RM).</span><span class="sxs-lookup"><span data-stu-id="8a30b-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="8a30b-113">Geliştiricilerin genellikle yazması gereken çoğu veri erişim kodu gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="8a30b-114">ASP.NET Core gibi EF Core, modüler platformlar arası uygulamaları desteklemek için baştan sona yeniden yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="8a30b-115">Bunu uygulamanıza bir NuGet paketi olarak ekleyin, başlangıçta yapılandırın ve ihtiyacınız olduğunda bağımlılık ekleme yoluyla isteyin.</span><span class="sxs-lookup"><span data-stu-id="8a30b-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="8a30b-116">Bir SQL Server veritabanıyla EF Core kullanmak için aşağıdaki DotNet CLı komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="8a30b-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="8a30b-117">Test için bir InMemory veri kaynağına yönelik destek eklemek için:</span><span class="sxs-lookup"><span data-stu-id="8a30b-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="8a30b-118">DbContext</span><span class="sxs-lookup"><span data-stu-id="8a30b-118">The DbContext</span></span>

<span data-ttu-id="8a30b-119">EF Core çalışmak için bir alt sınıfının <xref:Microsoft.EntityFrameworkCore.DbContext>olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="8a30b-120">Bu sınıf, uygulamanızın birlikte çalıştığı varlıkların koleksiyonlarını temsil eden özellikleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="8a30b-121">EShopOnWeb örneği, öğeler, markalar ve türler için koleksiyonlarla bir CatalogContext içerir:</span><span class="sxs-lookup"><span data-stu-id="8a30b-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="8a30b-122">DbContext 'in DbContextOptions kabul eden bir oluşturucusu olmalıdır ve bu bağımsız değişkeni temel DbContext oluşturucusuna geçirin.</span><span class="sxs-lookup"><span data-stu-id="8a30b-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="8a30b-123">Uygulamanızda yalnızca bir DbContext varsa, dbcontextoptions 'ın bir örneğini geçirebileceğinizi unutmayın, ancak birden fazla tane varsa, DbContext türünü genel parametre olarak geçirerek, genel dbcontextoptions\<T > türünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-123">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="8a30b-124">EF Core yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8a30b-124">Configuring EF Core</span></span>

<span data-ttu-id="8a30b-125">ASP.NET Core uygulamanızda, genellikle ConfigureServices yönteminizin EF Core yapılandıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="8a30b-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="8a30b-126">EF Core, yapılandırmasını kolaylaştırmak için çeşitli faydalı uzantı yöntemlerini destekleyen bir DbContextOptionsBuilder kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="8a30b-127">Yapılandırmada tanımlı bir bağlantı dizesiyle SQL Server bir veritabanı kullanmak üzere CatalogContext yapılandırmak için, ConfigureServices 'e aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8a30b-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="8a30b-128">Bellek içi veritabanını kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="8a30b-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="8a30b-129">EF Core yükledikten sonra bir DbContext alt türü oluşturdunuz ve bunu ConfigureServices içinde yapılandırdıktan sonra, EF Core kullanmaya hazırsınızdır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="8a30b-130">DbContext türünün bir örneğini, ihtiyacı olan herhangi bir hizmette isteyebilir ve yalnızca bir koleksiyonda olmaları gibi LINQ kullanarak kalıcı varlıklarınız ile çalışmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="8a30b-131">EF Core, verileri depolamak ve almak için LINQ ifadelerinizi SQL sorgularına çevirme işi yapar.</span><span class="sxs-lookup"><span data-stu-id="8a30b-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="8a30b-132">Bir günlükçü yapılandırarak EF Core sorguları, Şekil 8-1 ' de gösterildiği gibi, düzeyinin en az bilgi olarak ayarlandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![EF Core sorguları konsola kaydetme](./media/image8-1.png)

<span data-ttu-id="8a30b-134">**Şekil 8-1**.</span><span class="sxs-lookup"><span data-stu-id="8a30b-134">**Figure 8-1**.</span></span> <span data-ttu-id="8a30b-135">EF Core sorguları konsola kaydetme</span><span class="sxs-lookup"><span data-stu-id="8a30b-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="8a30b-136">Verileri getirme ve depolama</span><span class="sxs-lookup"><span data-stu-id="8a30b-136">Fetching and storing Data</span></span>

<span data-ttu-id="8a30b-137">EF Core verileri almak için, uygun özelliğe erişir ve sonucu filtrelemek için LINQ 'yi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8a30b-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="8a30b-138">Ayrıca, bir türden diğerine sonucu dönüştürmek için de LINQ 'ı projeksiyonu yapmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="8a30b-139">Aşağıdaki örnek, adlandırma markalarını, ada göre sıralanmış, etkin özelliklerine göre filtrelenmiş ve bir SelectListItem türü üzerine yansıtılan bir şekilde alır:</span><span class="sxs-lookup"><span data-stu-id="8a30b-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="8a30b-140">Sorguyu hemen yürütmek için, yukarıdaki örnekte ToListAsync çağrısını eklemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="8a30b-141">Aksi takdirde, ifade, numaralandırılmadıkça yürütülemeyecek bir IQueryable\<SelectListItem > atayacaktır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="8a30b-142">Metotlardan IQueryable sonuçlarının döndürülmesinin olumlu ve olumsuz yönleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="8a30b-143">Sorgu EF Core daha fazla değiştirilecek şekilde oluşturulmasına izin verir, ancak sorguya EF Core çevrilemediği bir işleme eklenirse, yalnızca çalışma zamanında oluşan hatalara de yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="8a30b-144">Veri erişimi gerçekleştiren yönteme filtre geçirmek genellikle daha güvenlidir ve sonuç olarak bir bellek içi toplamayı (örneğin, liste\<T >) geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a30b-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="8a30b-145">EF Core, kalıcılığı yaptığı varlıklarda yapılan değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="8a30b-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="8a30b-146">İzlenen bir varlıktaki değişiklikleri kaydetmek için, yalnızca DbContext üzerinde SaveChanges metodunu çağırın, bu da varlığı getirmek için kullanılan DbContext örneğinin aynı olduğundan emin olur.</span><span class="sxs-lookup"><span data-stu-id="8a30b-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="8a30b-147">Varlık ekleme ve kaldırma, doğrudan uygun DbSet özelliğinde, veritabanı komutlarını yürütmek için SaveChanges çağrısı ile birlikte yapılır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="8a30b-148">Aşağıdaki örnek, kalıcılığı ekleme, güncelleştirme ve kalıcılığın kaldırılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="8a30b-149">EF Core getirme ve kaydetme için hem zaman uyumlu hem de zaman uyumsuz yöntemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="8a30b-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="8a30b-150">Web uygulamalarında, zaman uyumsuz yöntemlerle zaman uyumsuz/await deseninin kullanılması önerilir. bu sayede, veri erişim işlemlerinin tamamlanmasını beklerken Web sunucusu iş parçacıklarının engellenmez.</span><span class="sxs-lookup"><span data-stu-id="8a30b-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="8a30b-151">İlgili verileri getirme</span><span class="sxs-lookup"><span data-stu-id="8a30b-151">Fetching related data</span></span>

<span data-ttu-id="8a30b-152">EF Core varlıkları aldığında, veritabanında bu varlıkla doğrudan depolanan tüm özellikleri doldurur.</span><span class="sxs-lookup"><span data-stu-id="8a30b-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="8a30b-153">İlgili varlıkların listeleri gibi gezinti özellikleri doldurulmaz ve değerleri null olarak ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="8a30b-154">Bu, EF Core gerekenden daha fazla veri getirmemesini sağlar ve bu, istekleri hızlı bir şekilde işlemek ve yanıtları verimli bir şekilde döndürmesi gereken Web uygulamaları için özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="8a30b-155">_Ekip yükleme_kullanarak bir varlıkla ilişkiler dahil etmek için, özelliği gösterildiği gibi, sorgu üzerinde Include Extension metodunu kullanarak belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8a30b-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="8a30b-156">Birden çok ilişki ekleyebilirsiniz ve Thenınclude kullanarak alt ilişkileri de dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-156">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="8a30b-157">EF Core, sonuçta elde edilen varlık kümesini almak için tek bir sorgu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8a30b-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="8a30b-158">Alternatif olarak, gezinti özelliklerinin gezinti özelliklerini bir '. ' geçirerek dahil edebilirsiniz. `.Include()` uzantı yöntemine ayrılmış dize, örneğin:</span><span class="sxs-lookup"><span data-stu-id="8a30b-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include(“Items.Products”)
```

<span data-ttu-id="8a30b-159">Bir belirtim, filtreleme mantığının yanı sıra döndürülecek verilerin şeklini belirtebilir ve bu da doldurulacak özellikler de dahildir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="8a30b-160">EShopOnWeb örneği, belirtim içinde bilgi yüklemeyi kapsayan çeşitli özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="8a30b-161">Sorgunun bir parçası olarak belirtiminin nasıl kullanıldığını görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8a30b-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="8a30b-162">İlgili verileri yüklemeye yönelik başka bir seçenek de _açık yükleme_kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="8a30b-163">Açık yükleme, daha önce alınmış bir varlığa ek veri yüklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a30b-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="8a30b-164">Bu, veritabanına ayrı bir istek içerdiğinden Web uygulamaları için önerilmez, bu da istek başına yapılan veritabanı gidiş dönüş sayısını en aza indirmelidir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-164">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="8a30b-165">_Yavaş yükleme_ , uygulama tarafından başvurulduğundan ilgili verileri otomatik olarak yükleyen bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="8a30b-166">EF Core sürüm 2,1 ' de geç yükleme desteği eklendi.</span><span class="sxs-lookup"><span data-stu-id="8a30b-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="8a30b-167">Geç yükleme varsayılan olarak etkin değildir ve yüklemesi `Microsoft.EntityFrameworkCore.Proxies`gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="8a30b-168">Açık yüklemede olduğu gibi, kullanımı genellikle Web uygulamaları için devre dışı bırakılmalıdır, çünkü kullanımı her Web isteği içinde ek veritabanı sorgularının oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8a30b-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="8a30b-169">Ne yazık ki, yavaş yükleme tarafından tahakkuk eden ek yük, gecikme küçük olduğunda ve genellikle test için kullanılan veri kümelerinin küçük olması durumunda geliştirme sırasında fark etmez.</span><span class="sxs-lookup"><span data-stu-id="8a30b-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="8a30b-170">Ancak üretimde, daha fazla Kullanıcı, daha fazla veri ve daha fazla gecikmeyle, ek veritabanı istekleri genellikle yavaş yüklemeyi yoğun bir şekilde kullanan Web uygulamaları için düşük performansa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="8a30b-171">Web uygulamalarında yavaş yükleme varlıklarının olmaması</span><span class="sxs-lookup"><span data-stu-id="8a30b-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="8a30b-172">Verileri kapsülleme</span><span class="sxs-lookup"><span data-stu-id="8a30b-172">Encapsulating data</span></span>

<span data-ttu-id="8a30b-173">EF Core, modelinizin durumunu doğru bir şekilde kapsüllemek için birkaç özelliği destekler.</span><span class="sxs-lookup"><span data-stu-id="8a30b-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="8a30b-174">Etki alanı modellerinde yaygın bir sorun, koleksiyon gezinti özelliklerini herkese açık olarak erişilebilen liste türleri olarak kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="8a30b-175">Bu, tüm ortak çalışmalardan bu koleksiyon türlerinin içeriğini işlemesini sağlar. Bu, koleksiyon ile ilgili önemli iş kurallarını atlayarak, büyük olasılıkla nesneyi geçersiz bir durumda bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-175">This allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="8a30b-176">Bunun çözümü, ilgili koleksiyonlara salt okuma erişimi sunmak ve bu örnekte olduğu gibi istemcilerin bunları işleyebilecekleri yolları tanımlamaya yönelik yöntemleri açıkça sağlamaktır:</span><span class="sxs-lookup"><span data-stu-id="8a30b-176">The solution to this is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

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

<span data-ttu-id="8a30b-177">Bu varlık türünün bir public `List` veya `ICollection` Property sunmaz, bunun yerine temel alınan liste türünü sarmalayan bir `IReadOnlyCollection` tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-177">Note that this entity type doesn’t expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="8a30b-178">Bu model kullanılırken, şu şekilde bir yedekleme alanı kullanacağınızı Entity Framework Core belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8a30b-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="8a30b-179">Etki alanı modelinizi iyileştirebilmeniz için bir başka yol da, kimlik olmayan türler için değer nesnelerinin kullanımı ve yalnızca özelliklerine göre ayırt edilebilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="8a30b-180">Bu tür türler, varlıklarınızın özellikleri olarak kullanılması, mantığın ait olduğu değer nesnesine özgü mantığı tutmaya yardımcı olabilir ve aynı kavramı kullanan birden fazla varlık arasında yinelenen mantığdan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="8a30b-181">Entity Framework Core, türü sahipli bir varlık olarak yapılandırarak aynı tablodaki değer nesnelerini sahip oldukları varlıkla kalıcı hale getirebilirsiniz, örneğin:</span><span class="sxs-lookup"><span data-stu-id="8a30b-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="8a30b-182">Bu örnekte, `ShipToAddress` özelliği türündedir `Address`.</span><span class="sxs-lookup"><span data-stu-id="8a30b-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="8a30b-183">`Address`, `Street` ve`City`gibi çeşitli özelliklere sahip bir değer nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="8a30b-184">EF Core, `Order` nesneyi özelliği başına `Address` tek sütunlu, her sütun adının özelliğin adıyla sonuna ekleyerek tablosuna eşler.</span><span class="sxs-lookup"><span data-stu-id="8a30b-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="8a30b-185">Bu örnekte, `Order` tablosu `ShipToAddress_Street` ve `ShipToAddress_City`gibi sütunları içerir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span>

[<span data-ttu-id="8a30b-186">EF Core 2,2, sahip olunan varlıkların koleksiyonları için destek sunar</span><span class="sxs-lookup"><span data-stu-id="8a30b-186">EF Core 2.2 introduces support for collections of owned entities</span></span>](https://docs.microsoft.com/ef/core/what-is-new/ef-core-2.2#collections-of-owned-entities)

### <a name="resilient-connections"></a><span data-ttu-id="8a30b-187">Dayanıklı bağlantılar</span><span class="sxs-lookup"><span data-stu-id="8a30b-187">Resilient connections</span></span>

<span data-ttu-id="8a30b-188">SQL veritabanları gibi dış kaynaklar zaman zaman kullanılabilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-188">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="8a30b-189">Geçici kullanım durumunda uygulamalar, bir özel durum oluşmasını önlemek için yeniden deneme mantığını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-189">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="8a30b-190">Bu teknik genellikle _bağlantı dayanıklılığı_olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-190">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="8a30b-191">En fazla yeniden deneme sayısına ulaşılana kadar, bir üstel bekleme süresi ile yeniden denemeye çalışırken, üstel geri alma tekniğinden [kendi yeniden denelerinizi](https://docs.microsoft.com/azure/architecture/patterns/retry) uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-191">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="8a30b-192">Bu teknik, bulut kaynaklarının kısa süreler boyunca zaman zaman kullanılamamasına yol açabilir ve bazı isteklerin başarısız olmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-192">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="8a30b-193">Azure SQL DB için Entity Framework Core, iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığını zaten sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="8a30b-193">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="8a30b-194">Ancak dayanıklı EF Core bağlantılarına sahip olmak istiyorsanız her DbContext bağlantısı için Entity Framework yürütme stratejisini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-194">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="8a30b-195">Örneğin, EF Core bağlantı düzeyindeki aşağıdaki kod, bağlantı başarısız olursa yeniden denenen dayanıklı SQL bağlantılarına izin verir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-195">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="8a30b-196">BeginTransaction ve birden çok Dbbağlamlarını kullanarak yürütme stratejileri ve açık işlemler</span><span class="sxs-lookup"><span data-stu-id="8a30b-196">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="8a30b-197">EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden kullanılabilir işlem haline gelir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-197">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="8a30b-198">Her bir sorgu ve her SaveChanges çağrısı, geçici bir hata oluşursa bir birim olarak yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-198">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="8a30b-199">Ancak, kodunuz BeginTransaction kullanarak bir işlem başlatırsa, birim olarak değerlendirilmesi gereken kendi işlem grubunuzu tanımlamanız gerekir; bir hata oluşursa işlem içindeki her şeyin geri alınması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8a30b-199">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="8a30b-200">Bir EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu işlemi yürütmeye çalışırsanız ve içinde birden fazla Dbbağlamdan birkaç SaveChanges eklerseniz, aşağıdaki gibi bir özel durum görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-200">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="8a30b-201">System. InvalidOperationException: Yapılandırılan ' Sqlserverretryingexecutionstrateji ' yürütme stratejisi, Kullanıcı tarafından başlatılan işlemleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="8a30b-201">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="8a30b-202">İşlemdeki tüm işlemleri yeniden kullanılabilir bir birim olarak yürütmek için ' DbContext. Database. Createexecutionstrateji () ' tarafından döndürülen yürütme stratejisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a30b-202">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="8a30b-203">Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-203">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="8a30b-204">Geçici bir hata oluşursa, yürütme stratejisi temsilciyi tekrar çağıracaktır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-204">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="8a30b-205">Aşağıdaki kod, bu yaklaşımın nasıl uygulanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8a30b-205">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="8a30b-206">İlk DbContext \_, catalogcontext ve ikinci DbContext, \_ıntegrationeventlogservice nesnesi içindedir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-206">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="8a30b-207">Son olarak, yürütme eylemi birden fazla Dbbağlamı ve EF yürütme stratejisi kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-207">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="8a30b-208">Başvurular – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="8a30b-208">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="8a30b-209">**EF Core docs**</span><span class="sxs-lookup"><span data-stu-id="8a30b-209">**EF Core Docs**</span></span>  
>   <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="8a30b-210">**EF Core: İlgili veriler**</span><span class="sxs-lookup"><span data-stu-id="8a30b-210">**EF Core: Related Data**</span></span>  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="8a30b-211">**ASPNET uygulamalarında daha yavaş yükleme varlıklarını önleyin**</span><span class="sxs-lookup"><span data-stu-id="8a30b-211">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="8a30b-212">EF Core veya Micro-ORM?</span><span class="sxs-lookup"><span data-stu-id="8a30b-212">EF Core or micro-ORM?</span></span>

<span data-ttu-id="8a30b-213">EF Core, kalıcılığı yönetmek için harika bir seçimdir ve çoğu bölüm uygulama geliştiricilerinden veritabanı ayrıntılarını kapsüller, tek seçim değildir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-213">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="8a30b-214">Diğer bir popüler açık kaynak alternatifi [, mikro](https://github.com/StackExchange/Dapper)-ORM adlı bir, yani olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-214">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="8a30b-215">Mikro-ORM, nesneleri veri yapılarına eşlemek için hafif ve daha az bir tam özellikli araçtır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-215">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="8a30b-216">Paber söz konusu olduğunda, tasarım hedefleri, verileri almak ve güncelleştirmek için kullandığı temeldeki sorguları tamamen kapsüllemek yerine performansa odaklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-216">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="8a30b-217">Geliştiriciden SQL soyut olmadığından, kaber "metal 'ya yakındır" ve geliştiricilerin belirli bir veri erişim işlemi için kullanmak istedikleri tam sorguları yazmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-217">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="8a30b-218">EF Core, bu iki önemli özelliğe sahiptir ve bu, bunu bir yandan da kendi performans yüklerine ekler.</span><span class="sxs-lookup"><span data-stu-id="8a30b-218">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="8a30b-219">İlki LINQ ifadelerinden SQL 'e çevirmesidir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-219">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="8a30b-220">Bu çeviriler önbelleğe alınır, ancak bunu ilk kez gerçekleştirmede ek yük vardır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-220">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="8a30b-221">İkincisi, varlıklarda değişiklik izleme (etkin güncelleştirme deyimlerinin üretilebilmesi için).</span><span class="sxs-lookup"><span data-stu-id="8a30b-221">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="8a30b-222">Bu davranış, AsNotTracking uzantısı kullanılarak belirli sorgular için kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-222">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="8a30b-223">EF Core Ayrıca genellikle çok verimli olan ve performans açısından kusursuz bir şekilde kabul edilebilir olan SQL sorguları üretir, ancak yürütülecek kesin sorgu üzerinde iyi denetime ihtiyacınız varsa, EF kullanarak özel SQL (veya saklı yordam yürütme) geçirebilirsiniz Çekirdek, çok.</span><span class="sxs-lookup"><span data-stu-id="8a30b-223">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="8a30b-224">Bu durumda, kaber hala EF Core, ancak biraz daha fazlasını gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-224">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="8a30b-225">Julie Lerman, Mayıs 2016 MSDN makalesi [kaber, Entity Framework ve hibrit uygulamalarında](https://msdn.microsoft.com/magazine/mt703432.aspx)bazı performans verileri sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-225">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="8a30b-226">Çeşitli veri erişim yöntemlerine yönelik ek performans kıyaslama verileri [, kaber sitesinde](https://github.com/StackExchange/Dapper)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-226">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="8a30b-227">Kaber için sözdiziminin EF Core nasıl değiştiğini görmek için, öğelerin bir listesini almak için aynı yöntemin bu iki sürümünü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="8a30b-227">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="8a30b-228">Kaber ile daha karmaşık nesne grafikleri oluşturmanız gerekiyorsa, ilişkili sorguları kendiniz yazmanız gerekir (EF Core gibi bir Içerme eklemek yerine).</span><span class="sxs-lookup"><span data-stu-id="8a30b-228">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="8a30b-229">Bu, tek tek satırları birden çok eşlenmiş nesne ile eşlemenizi sağlayan çoklu eşleme adlı bir özellik dahil olmak üzere çeşitli sözdizimleri aracılığıyla desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-229">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="8a30b-230">Örneğin, Kullanıcı türünde bir özellik sahibi olan bir sınıf gönderisi verildiğinde, aşağıdaki SQL gerekli verilerin tümünü döndürür:</span><span class="sxs-lookup"><span data-stu-id="8a30b-230">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="8a30b-231">Döndürülen her satır hem Kullanıcı hem de veri Gönder ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-231">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="8a30b-232">Kullanıcı verilerinin, sahibi özelliği aracılığıyla Post verilerine bağlanması gerektiğinden aşağıdaki işlev kullanılır:</span><span class="sxs-lookup"><span data-stu-id="8a30b-232">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="8a30b-233">İlişkili kullanıcı verileriyle doldurulmuş bir gönderilerin bir koleksiyonunu döndüren tam kod listesi şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="8a30b-233">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="8a30b-234">Paber, daha az kapsülleme sağladığından, geliştiricilerin verilerinin nasıl depolandığı, nasıl verimli bir şekilde sorgulanacağı ve bunu getirmek için daha fazla kod yazabileceği hakkında daha fazla bilgi sahibi olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-234">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="8a30b-235">Model değiştiğinde, yalnızca yeni bir geçiş (başka bir EF Core özelliği) oluşturmak ve/veya eşleme bilgilerini bir DbContext içinde tek bir yerde güncelleştirmek yerine, etkilenen her sorgunun güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-235">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="8a30b-236">Bu sorgularda derleme zamanı garantisi yoktur, bu nedenle model veya veritabanındaki değişikliklere yanıt olarak çalışma zamanında kesintiye uğrarabilir ve hataları hızla algılamaya daha zor hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-236">These queries have no compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="8a30b-237">Bu avantajları için Exchange 'de, kaber son derece hızlı performans sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-237">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="8a30b-238">Çoğu uygulama ve neredeyse tüm uygulamaların birçok bölümü için EF Core, kabul edilebilir performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a30b-238">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="8a30b-239">Bu nedenle, geliştirici üretkenlik avantajları büyük olasılıkla performans yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-239">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="8a30b-240">Önbelleğe alma işleminden faydalanabilir sorgular için, gerçek sorgu yalnızca büyük bir yüzde oranında yürütülebilir ve görece küçük sorgu performansı farklılıklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-240">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="8a30b-241">SQL veya NoSQL</span><span class="sxs-lookup"><span data-stu-id="8a30b-241">SQL or NoSQL</span></span>

<span data-ttu-id="8a30b-242">Geleneksel olarak, SQL Server gibi ilişkisel veritabanları kalıcı veri depolama alanı için Market 'e sahiptir, ancak bunlar kullanılabilir tek çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-242">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="8a30b-243">[MongoDB](https://www.mongodb.com/what-is-mongodb) gibi NoSQL veritabanları, nesneleri depolamanın farklı bir yaklaşımını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-243">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="8a30b-244">Nesneleri tablo ve satırlara eşlemek yerine, diğer bir seçenek de nesne grafiğinin tamamını seri hale getirmek ve sonucu depolar.</span><span class="sxs-lookup"><span data-stu-id="8a30b-244">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="8a30b-245">En azından başlangıçta bu yaklaşımın avantajları basitlik ve performanslardır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-245">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="8a30b-246">Tek bir seri hale getirilmiş bir nesneyi, bir anahtarla, nesnenin veritabanından en son alınmasından bu yana değişmiş olabilecek ilişkiler ve güncelleştirmeler ve satırlar içeren çok sayıda tabloya parçalanmaya kıyasla bir anahtarla depolamak kesinlikle daha basittir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-246">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="8a30b-247">Benzer şekilde, anahtar tabanlı bir mağazadan tek bir nesneyi getirme ve serisini kaldırma genellikle karmaşık birleşimlerden çok daha hızlı ve daha kolay ve aynı nesneyi ilişkisel bir veritabanından tamamen oluşturmak için gereken birden çok veritabanı sorgusuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-247">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="8a30b-248">Kilitleri veya işlemleri ya da sabit bir şemanın olmaması, NoSQL veritabanlarının çok büyük veri kümelerini destekleyen birçok makine genelinde ölçeklendirilmesine çok daha fazla değişiklik yapabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a30b-248">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="8a30b-249">Diğer taraftan, NoSQL veritabanlarının (genellikle çağrıldığı gibi) dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-249">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="8a30b-250">İlişkisel veritabanları, tutarlılığı zorlamak ve verilerin çoğaltılmasını önlemek için normalleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-250">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="8a30b-251">Bu, veritabanının toplam boyutunu azaltır ve paylaşılan veriler için güncelleştirmelerin hemen veritabanının tamamında kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a30b-251">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="8a30b-252">İlişkisel bir veritabanında, bir ülke/bölge adı değiştirilirse adres kayıtları güncelleştirmeden önce güncelleştirilmesi gerekmeden, bir ülke tablosuna KIMLIĞE göre başvurabilir. bu şekilde,</span><span class="sxs-lookup"><span data-stu-id="8a30b-252">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="8a30b-253">Ancak, bir NoSQL veritabanında, adreste ve ilişkili ülkede birçok saklı nesnenin parçası olarak serileştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-253">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="8a30b-254">Ülke/bölge adına yapılan bir güncelleştirme, bu gibi tüm nesnelerin tek bir satır yerine güncelleştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-254">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="8a30b-255">İlişkisel veritabanları, yabancı anahtarlar gibi kuralları zorunlu tutarak ilişkisel bütünlüğünden de emin olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-255">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="8a30b-256">NoSQL veritabanları genellikle verileri üzerinde böyle kısıtlamalar sunmaz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-256">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="8a30b-257">Başka bir karmaşıklık NoSQL veritabanlarının sürümü oluşturma ile uğraşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-257">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="8a30b-258">Bir nesnenin özellikleri değiştiğinde, bu, depolanan eski sürümlerden seri durumdan çıkarılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-258">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="8a30b-259">Bu nedenle, nesnenin serileştirilmiş (önceki) sürümüne sahip tüm var olan nesnelerin yeni şemasına uymak için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-259">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="8a30b-260">Bu, ilişkisel bir veritabanından kavramsal olarak farklılık içermez, burada şema değişiklikleri bazen güncelleştirme betikleri veya eşleme güncelleştirmeleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-260">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="8a30b-261">Ancak, daha fazla veri yinelemesi olduğundan, değiştirilmesi gereken giriş sayısı NoSQL yaklaşımında genellikle çok daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="8a30b-261">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="8a30b-262">Nesnelerin birden çok sürümünü depolamak için NoSQL veritabanlarında, sabit bir şema ilişkisel veritabanları genellikle desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8a30b-262">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="8a30b-263">Bununla birlikte, bu durumda, uygulama kodunuzun önceki nesne sürümlerinin varlığını hesaba getirmeniz gerekir, ek karmaşıklık ekliyor.</span><span class="sxs-lookup"><span data-stu-id="8a30b-263">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="8a30b-264">NoSQL veritabanları genellikle, ilişkisel veritabanları üzerinde performans ve ölçeklenebilirlik avantajları olan [ACID](https://en.wikipedia.org/wiki/ACID)'yi zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-264">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="8a30b-265">Bunlara çok büyük veri kümeleri ve normalleştirilmiş tablo yapılarında depolamaya uygun olmayan nesneler de uygundur.</span><span class="sxs-lookup"><span data-stu-id="8a30b-265">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="8a30b-266">Tek bir uygulamanın hem ilişkisel hem de NoSQL veritabanlarından yararlanması, her yerde en iyi şekilde yararlanamaması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8a30b-266">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="8a30b-267">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="8a30b-267">Azure DocumentDB</span></span>

<span data-ttu-id="8a30b-268">Azure DocumentDB, bulut tabanlı şemaya ücretsiz veri depolaması sağlayan, tam olarak yönetilen bir NoSQL veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-268">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="8a30b-269">DocumentDB hızlı ve tahmin edilebilir performans, yüksek kullanılabilirlik, esnek ölçeklendirme ve küresel dağıtım için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="8a30b-269">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="8a30b-270">Geliştiriciler NoSQL veritabanı olmasına rağmen JSON verilerinde zengin ve tanıdık SQL sorgu yeteneklerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-270">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="8a30b-271">DocumentDB 'deki tüm kaynaklar JSON belgeleri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-271">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="8a30b-272">Kaynaklar, meta verileri içeren belgeler ve öğe koleksiyonları olan _akışlar_olan _öğeler_olarak yönetilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-272">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="8a30b-273">Şekil 8-2, farklı DocumentDB kaynakları arasındaki ilişkiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-273">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>

![Bir NoSQL JSON veritabanı olan DocumentDB 'de kaynaklar arasındaki hiyerarşik ilişki](./media/image8-2.png)

<span data-ttu-id="8a30b-275">**Şekil 8-2.**</span><span class="sxs-lookup"><span data-stu-id="8a30b-275">**Figure 8-2.**</span></span> <span data-ttu-id="8a30b-276">DocumentDB kaynak organizasyonu.</span><span class="sxs-lookup"><span data-stu-id="8a30b-276">DocumentDB resource organization.</span></span>

<span data-ttu-id="8a30b-277">DocumentDB sorgu dili, JSON belgelerini sorgulamak için basit ancak güçlü bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-277">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="8a30b-278">Dil, ANSI SQL dilbilgisi 'nin bir alt kümesini destekler ve JavaScript nesnesi, diziler, nesne oluşturma ve işlev çağırma için derin tümleştirme ekler.</span><span class="sxs-lookup"><span data-stu-id="8a30b-278">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="8a30b-279">**Başvurular – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="8a30b-279">**References – DocumentDB**</span></span>

- <span data-ttu-id="8a30b-280">DocumentDB tanıtımı</span><span class="sxs-lookup"><span data-stu-id="8a30b-280">DocumentDB Introduction</span></span>  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="8a30b-281">Diğer kalıcılık seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8a30b-281">Other persistence options</span></span>

<span data-ttu-id="8a30b-282">İlişkisel ve NoSQL depolama seçeneklerine ek olarak ASP.NET Core uygulamalar, çeşitli veri biçimlerini ve dosyalarını bulut tabanlı, ölçeklenebilir bir biçimde depolamak için Azure Storage 'ı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-282">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="8a30b-283">Azure Storage, büyük miktarlarda ölçeklenebilir hale gelir. bu nedenle, uygulamanız gerektiriyorsa yüzlerce veya terabayta varan miktarda veri depolamayı başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-283">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="8a30b-284">Azure Storage dört tür veriyi destekler:</span><span class="sxs-lookup"><span data-stu-id="8a30b-284">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="8a30b-285">Yapılandırılmamış metin veya ikili depolama için, nesne depolama olarak da adlandırılan BLOB depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="8a30b-285">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="8a30b-286">Yapılandırılmış veri kümeleri için satır anahtarları aracılığıyla erişilebilen tablo depolaması.</span><span class="sxs-lookup"><span data-stu-id="8a30b-286">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="8a30b-287">Sıradan sıra tabanlı mesajlaşma için kuyruk depolama.</span><span class="sxs-lookup"><span data-stu-id="8a30b-287">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="8a30b-288">Azure sanal makineler ve şirket içi uygulamalar arasında paylaşılan dosya erişimi için dosya depolama.</span><span class="sxs-lookup"><span data-stu-id="8a30b-288">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="8a30b-289">**Başvurular – Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="8a30b-289">**References – Azure Storage**</span></span>

- <span data-ttu-id="8a30b-290">Azure depolama giriş</span><span class="sxs-lookup"><span data-stu-id="8a30b-290">Azure Storage Introduction</span></span>  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="8a30b-291">Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="8a30b-291">Caching</span></span>

<span data-ttu-id="8a30b-292">Web uygulamalarında, her Web isteği mümkün olan en kısa sürede tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-292">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="8a30b-293">Bunu gerçekleştirmenin bir yolu, sunucunun isteği tamamlaması için yapması gereken dış çağrı sayısını sınırlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-293">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="8a30b-294">Önbelleğe alma işlemi, sunucuda verilerin bir kopyasının depolanmasını (veya verilerin kaynağından daha kolay sorgulanan başka bir veri deposu) içerir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-294">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="8a30b-295">Web uygulamaları ve özellikle de non-SPA geleneksel olmayan Web uygulamaları, her istekle birlikte Kullanıcı arabiriminin tamamını oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-295">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="8a30b-296">Bu sıklıkla, bir Kullanıcı isteğinden bir sonrakine aynı veritabanı sorgularının birçok kez oluşturulmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-296">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="8a30b-297">Çoğu durumda, bu veriler nadiren değişir, bu yüzden sürekli olarak veritabanından isteme nedenidir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-297">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="8a30b-298">ASP.NET Core, tüm sayfaların önbelleğe alınması ve daha ayrıntılı önbelleğe alma davranışını destekleyen veri önbelleğe alma işlemleri için yanıt önbelleğe almayı destekler.</span><span class="sxs-lookup"><span data-stu-id="8a30b-298">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="8a30b-299">Önbelleğe alma uygularken, kaygıları göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-299">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="8a30b-300">Veri erişim mantığınızdaki veya Kullanıcı arabiriminizdeki önbelleğe alma mantığını uygulamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="8a30b-300">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="8a30b-301">Bunun yerine, önbelleğe almayı kendi sınıflarında kapsülle ve davranışını yönetmek için yapılandırma kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a30b-301">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="8a30b-302">Bu, açık/kapalı ve tek sorumluluk ilkelerini izler ve uygulamanızda önbelleğe alma işlemini nasıl kullanacağınızı yönetmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-302">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="8a30b-303">ASP.NET Core yanıtı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="8a30b-303">ASP.NET Core response caching</span></span>

<span data-ttu-id="8a30b-304">ASP.NET Core iki yanıt önbelleği düzeyini destekler.</span><span class="sxs-lookup"><span data-stu-id="8a30b-304">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="8a30b-305">İlk düzey sunucu üzerinde herhangi bir şeyi önbelleğe almaz, ancak istemcilerin ve proxy sunucularının yanıtları önbelleğe almasını sağlayan HTTP üstbilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="8a30b-305">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="8a30b-306">Bu, bireysel denetleyicilere veya eylemlere ResponseCache özniteliği eklenerek uygulanır:</span><span class="sxs-lookup"><span data-stu-id="8a30b-306">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="8a30b-307">Önceki örnek, istemciye, sonucu 60 saniyeye kadar önbelleğe almak için, bu üst bilginin yanıta eklenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="8a30b-307">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="8a30b-308">Cache-Control: PUBLIC, max-age = 60</span><span class="sxs-lookup"><span data-stu-id="8a30b-308">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="8a30b-309">Uygulamaya sunucu tarafı bellek içi önbelleğe alma eklemek için Microsoft. AspNetCore. ResponseCaching NuGet paketine başvurmanız ve ardından yanıt önbelleğe alma ara yazılımını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-309">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="8a30b-310">Bu ara yazılım hem ConfigureServices hem de başlangıçta yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="8a30b-310">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

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

<span data-ttu-id="8a30b-311">Yanıt önbelleğe alma ara yazılımı, özelleştirmeleri, özelleştirebileceğiniz bir dizi koşula göre otomatik olarak önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-311">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="8a30b-312">Varsayılan olarak, GET veya HEAD yöntemleri aracılığıyla istenen yalnızca 200 (Tamam) yanıt önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-312">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="8a30b-313">Ayrıca, isteklerin Cache-Control: public üst bilgisine sahip bir yanıtı olmalıdır ve yetkilendirme ya da set-Cookie üst bilgisini içeremez.</span><span class="sxs-lookup"><span data-stu-id="8a30b-313">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="8a30b-314">[Yanıt önbelleğe alma ara yazılımı tarafından kullanılan önbelleğe alma koşullarının tüm listesini](/aspnet/core/performance/caching/middleware#conditions-for-caching)görün.</span><span class="sxs-lookup"><span data-stu-id="8a30b-314">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="8a30b-315">Veri önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="8a30b-315">Data caching</span></span>

<span data-ttu-id="8a30b-316">(Veya buna ek olarak) tam Web yanıtlarını önbelleğe alma yerine, bireysel veri sorgularının sonuçlarını önbelleğe alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-316">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="8a30b-317">Bunun için, Web sunucusunda bellek önbelleklemesi veya [Dağıtılmış önbellek](/aspnet/core/performance/caching/distributed)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-317">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="8a30b-318">Bu bölüm, bellek önbelleğe alma işleminde nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-318">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="8a30b-319">ConfigureServices 'e bellek (veya dağıtılmış) önbelleği desteği eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="8a30b-319">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="8a30b-320">Microsoft. Extensions. Caching. Memory NuGet paketini de eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="8a30b-320">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="8a30b-321">Hizmeti ekledikten sonra, önbelleğe erişmeniz gereken her yerde, bağımlılık ekleme yoluyla ımemorycache istek duyarsınız.</span><span class="sxs-lookup"><span data-stu-id="8a30b-321">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="8a30b-322">Bu örnekte, CachedCatalogService, temel alınan CatalogService uygulamasına erişimi denetleyen (veya davranışı ekleyen) ıconalogservice 'in alternatif bir uygulamasını sağlayarak proxy (veya dekoratör) tasarım modelini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="8a30b-322">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="8a30b-323">Uygulamayı, hizmetin önbelleğe alınmış sürümünü kullanacak şekilde yapılandırmak için, ancak hala hizmetin oluşturucuda ihtiyacı olan CatalogService örneğini almaya izin vermek için, ConfigureServices 'e şunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8a30b-323">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="8a30b-324">Bu şekilde, katalog verilerini getirmek için veritabanı çağrıları her istek yerine yalnızca dakikada bir kez yapılır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-324">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="8a30b-325">Site trafiğine bağlı olarak, bu, veritabanına yapılan sorgu sayısı üzerinde çok önemli bir etkiye ve ana sayfa için o anda bu hizmetin açığa çıkarılan her birine bağlı olan ortalama sayfa yükleme süresine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-325">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="8a30b-326">Önbelleğe alma işlemi uygulandığında ortaya çıkan bir sorun _eski veri_ , diğer bir deyişle, kaynakta Değiştirilen ancak güncel olmayan bir sürümü önbellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-326">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="8a30b-327">Bu sorunu hafifletmenin basit bir yolu, yoğun bir uygulama için, verilerin uzatılması için sınırlı sayıda daha fazla avantaj olduğundan, küçük önbellek süreleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8a30b-327">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="8a30b-328">Örneğin, tek bir veritabanı sorgusu oluşturan ve saniyede 10 kez istenen bir sayfa düşünün.</span><span class="sxs-lookup"><span data-stu-id="8a30b-328">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="8a30b-329">Bu sayfa bir dakika boyunca önbelleğe alınmışsa, 600 ' dan 1 ' e düşürülmesi için dakika başına yapılan Veritabanı sorgularının sayısına,% 99,8 oranında bir azalmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="8a30b-329">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="8a30b-330">Bunun yerine önbellek süresi bir saat yapılırsa, genel azaltma% 99,997 olur, ancak artık eski verilerin olasılığı ve potansiyel yaşı önemli ölçüde artar.</span><span class="sxs-lookup"><span data-stu-id="8a30b-330">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="8a30b-331">Diğer bir yaklaşım, içerdikleri veriler güncelleştirilirken önbellek girişlerini önceden kaldırmak olur.</span><span class="sxs-lookup"><span data-stu-id="8a30b-331">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="8a30b-332">Anahtarı biliniyorsa her bir giriş kaldırılabilir:</span><span class="sxs-lookup"><span data-stu-id="8a30b-332">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="8a30b-333">Uygulamanız, önbelleğe aldığı girdileri güncelleştirmek için işlevselliği kullanıma sunuyorsa, kodunuzda güncelleştirmeleri gerçekleştiren karşılık gelen önbellek girdilerini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-333">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="8a30b-334">Bazen belirli bir veri kümesine bağımlı birçok farklı giriş olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-334">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="8a30b-335">Bu durumda, CancellationChangeToken kullanarak önbellek girişleri arasında bağımlılıklar oluşturmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-335">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="8a30b-336">Bir CancellationChangeToken ile, belirteci iptal ederek birden çok önbellek girdisini bir kez sona erdirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a30b-336">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

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

<span data-ttu-id="8a30b-337">Önbelleğe alma, veritabanından aynı değerleri tekrar tekrar isteyen web sayfalarının performansını önemli ölçüde iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-337">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="8a30b-338">Önbelleğe almayı uygulamadan önce veri erişimi ve sayfa performansını ölçdiğinizden emin olun ve yalnızca geliştirme gereksinimi olduğunu gördüğünüz önbelleğe alma işlemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8a30b-338">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="8a30b-339">Önbelleğe alma, Web sunucusu bellek kaynaklarını tüketir ve uygulamanın karmaşıklığını artırır. bu sayede, bu tekniği kullanarak erken iyileştirmemenizi önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="8a30b-339">Caching consumes web server memory resources and increases the complexity of the application, so it’s important you don’t prematurely optimize using this technique.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8a30b-340">[Önceki](develop-asp-net-core-mvc-apps.md)İleri
>[](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="8a30b-340">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
