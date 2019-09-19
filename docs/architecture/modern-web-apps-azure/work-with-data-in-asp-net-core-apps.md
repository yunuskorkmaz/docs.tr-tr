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
# <a name="working-with-data-in-aspnet-core-apps"></a>ASP.NET Core uygulamalarında verilerle çalışma

> "Veriler, en çok değerli bir şeydir ve sistemlerden daha uzun süre sonra kalır."
>
> Tim Beranlar-eser

Veri erişimi, neredeyse tüm yazılım uygulamalarının önemli bir parçasıdır. ASP.NET Core, Entity Framework Core (ve Entity Framework 6 de) dahil olmak üzere çeşitli veri erişim seçeneklerini destekler ve tüm .NET veri erişim çerçevesiyle çalışabilir. Hangi veri erişimi çerçevesinin kullanılacağı seçimi uygulamanın ihtiyaçlarına bağlıdır. Bu seçeneklerin ApplicationCore ve UI projelerinden soyutlanmasıdır ve altyapıdaki uygulama ayrıntılarının kapsüllenmesi, gevşek olarak bağlanmış, test edilebilir yazılımlar üretmenize yardımcı olur.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (ilişkisel veritabanları için)

İlişkisel verilerle çalışması gereken yeni bir ASP.NET Core uygulaması yazıyorsanız, uygulamanızın verilerine erişmesi için önerilen yol Entity Framework Core (EF Core). EF Core, .NET geliştiricilerin nesneleri bir veri kaynağından ve veritabanından kalıcı hale getirebilmesine olanak tanıyan bir nesne ilişkisel Eşleyici (O/RM). Geliştiricilerin genellikle yazması gereken çoğu veri erişim kodu gereksinimini ortadan kaldırır. ASP.NET Core gibi EF Core, modüler platformlar arası uygulamaları desteklemek için baştan sona yeniden yazılmıştır. Bunu uygulamanıza bir NuGet paketi olarak ekleyin, başlangıçta yapılandırın ve ihtiyacınız olduğunda bağımlılık ekleme yoluyla isteyin.

Bir SQL Server veritabanıyla EF Core kullanmak için aşağıdaki DotNet CLı komutunu çalıştırın:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

Test için bir InMemory veri kaynağına yönelik destek eklemek için:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a>DbContext

EF Core çalışmak için bir alt sınıfının <xref:Microsoft.EntityFrameworkCore.DbContext>olması gerekir. Bu sınıf, uygulamanızın birlikte çalıştığı varlıkların koleksiyonlarını temsil eden özellikleri barındırır. EShopOnWeb örneği, öğeler, markalar ve türler için koleksiyonlarla bir CatalogContext içerir:

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

DbContext 'in DbContextOptions kabul eden bir oluşturucusu olmalıdır ve bu bağımsız değişkeni temel DbContext oluşturucusuna geçirin. Uygulamanızda yalnızca bir DbContext varsa, dbcontextoptions 'ın bir örneğini geçirebileceğinizi unutmayın, ancak birden fazla tane varsa, DbContext türünü genel parametre olarak geçirerek, genel dbcontextoptions\<T > türünü kullanmanız gerekir.

### <a name="configuring-ef-core"></a>EF Core yapılandırma

ASP.NET Core uygulamanızda, genellikle ConfigureServices yönteminizin EF Core yapılandıracaksınız. EF Core, yapılandırmasını kolaylaştırmak için çeşitli faydalı uzantı yöntemlerini destekleyen bir DbContextOptionsBuilder kullanır. Yapılandırmada tanımlı bir bağlantı dizesiyle SQL Server bir veritabanı kullanmak üzere CatalogContext yapılandırmak için, ConfigureServices 'e aşağıdaki kodu ekleyin:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Bellek içi veritabanını kullanmak için:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

EF Core yükledikten sonra bir DbContext alt türü oluşturdunuz ve bunu ConfigureServices içinde yapılandırdıktan sonra, EF Core kullanmaya hazırsınızdır. DbContext türünün bir örneğini, ihtiyacı olan herhangi bir hizmette isteyebilir ve yalnızca bir koleksiyonda olmaları gibi LINQ kullanarak kalıcı varlıklarınız ile çalışmaya başlayabilirsiniz. EF Core, verileri depolamak ve almak için LINQ ifadelerinizi SQL sorgularına çevirme işi yapar.

Bir günlükçü yapılandırarak EF Core sorguları, Şekil 8-1 ' de gösterildiği gibi, düzeyinin en az bilgi olarak ayarlandığından emin olabilirsiniz.

![EF Core sorguları konsola kaydetme](./media/image8-1.png)

**Şekil 8-1**. EF Core sorguları konsola kaydetme

### <a name="fetching-and-storing-data"></a>Verileri getirme ve depolama

EF Core verileri almak için, uygun özelliğe erişir ve sonucu filtrelemek için LINQ 'yi kullanırsınız. Ayrıca, bir türden diğerine sonucu dönüştürmek için de LINQ 'ı projeksiyonu yapmak için kullanabilirsiniz. Aşağıdaki örnek, adlandırma markalarını, ada göre sıralanmış, etkin özelliklerine göre filtrelenmiş ve bir SelectListItem türü üzerine yansıtılan bir şekilde alır:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Sorguyu hemen yürütmek için, yukarıdaki örnekte ToListAsync çağrısını eklemek önemlidir. Aksi takdirde, ifade, numaralandırılmadıkça yürütülemeyecek bir IQueryable\<SelectListItem > atayacaktır. Metotlardan IQueryable sonuçlarının döndürülmesinin olumlu ve olumsuz yönleri vardır. Sorgu EF Core daha fazla değiştirilecek şekilde oluşturulmasına izin verir, ancak sorguya EF Core çevrilemediği bir işleme eklenirse, yalnızca çalışma zamanında oluşan hatalara de yol açabilir. Veri erişimi gerçekleştiren yönteme filtre geçirmek genellikle daha güvenlidir ve sonuç olarak bir bellek içi toplamayı (örneğin, liste\<T >) geri döndürür.

EF Core, kalıcılığı yaptığı varlıklarda yapılan değişiklikleri izler. İzlenen bir varlıktaki değişiklikleri kaydetmek için, yalnızca DbContext üzerinde SaveChanges metodunu çağırın, bu da varlığı getirmek için kullanılan DbContext örneğinin aynı olduğundan emin olur. Varlık ekleme ve kaldırma, doğrudan uygun DbSet özelliğinde, veritabanı komutlarını yürütmek için SaveChanges çağrısı ile birlikte yapılır. Aşağıdaki örnek, kalıcılığı ekleme, güncelleştirme ve kalıcılığın kaldırılmasını gösterir.

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

EF Core getirme ve kaydetme için hem zaman uyumlu hem de zaman uyumsuz yöntemleri destekler. Web uygulamalarında, zaman uyumsuz yöntemlerle zaman uyumsuz/await deseninin kullanılması önerilir. bu sayede, veri erişim işlemlerinin tamamlanmasını beklerken Web sunucusu iş parçacıklarının engellenmez.

### <a name="fetching-related-data"></a>İlgili verileri getirme

EF Core varlıkları aldığında, veritabanında bu varlıkla doğrudan depolanan tüm özellikleri doldurur. İlgili varlıkların listeleri gibi gezinti özellikleri doldurulmaz ve değerleri null olarak ayarlanmış olabilir. Bu, EF Core gerekenden daha fazla veri getirmemesini sağlar ve bu, istekleri hızlı bir şekilde işlemek ve yanıtları verimli bir şekilde döndürmesi gereken Web uygulamaları için özellikle önemlidir. _Ekip yükleme_kullanarak bir varlıkla ilişkiler dahil etmek için, özelliği gösterildiği gibi, sorgu üzerinde Include Extension metodunu kullanarak belirtirsiniz:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Birden çok ilişki ekleyebilirsiniz ve Thenınclude kullanarak alt ilişkileri de dahil edebilirsiniz. EF Core, sonuçta elde edilen varlık kümesini almak için tek bir sorgu yürütülür. Alternatif olarak, gezinti özelliklerinin gezinti özelliklerini bir '. ' geçirerek dahil edebilirsiniz. `.Include()` uzantı yöntemine ayrılmış dize, örneğin:

```csharp
    .Include(“Items.Products”)
```

Bir belirtim, filtreleme mantığının yanı sıra döndürülecek verilerin şeklini belirtebilir ve bu da doldurulacak özellikler de dahildir. EShopOnWeb örneği, belirtim içinde bilgi yüklemeyi kapsayan çeşitli özellikler içerir. Sorgunun bir parçası olarak belirtiminin nasıl kullanıldığını görebilirsiniz:

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

İlgili verileri yüklemeye yönelik başka bir seçenek de _açık yükleme_kullanmaktır. Açık yükleme, daha önce alınmış bir varlığa ek veri yüklemenize olanak sağlar. Bu, veritabanına ayrı bir istek içerdiğinden Web uygulamaları için önerilmez, bu da istek başına yapılan veritabanı gidiş dönüş sayısını en aza indirmelidir.

_Yavaş yükleme_ , uygulama tarafından başvurulduğundan ilgili verileri otomatik olarak yükleyen bir özelliktir. EF Core sürüm 2,1 ' de geç yükleme desteği eklendi. Geç yükleme varsayılan olarak etkin değildir ve yüklemesi `Microsoft.EntityFrameworkCore.Proxies`gerekir. Açık yüklemede olduğu gibi, kullanımı genellikle Web uygulamaları için devre dışı bırakılmalıdır, çünkü kullanımı her Web isteği içinde ek veritabanı sorgularının oluşmasına neden olur. Ne yazık ki, yavaş yükleme tarafından tahakkuk eden ek yük, gecikme küçük olduğunda ve genellikle test için kullanılan veri kümelerinin küçük olması durumunda geliştirme sırasında fark etmez. Ancak üretimde, daha fazla Kullanıcı, daha fazla veri ve daha fazla gecikmeyle, ek veritabanı istekleri genellikle yavaş yüklemeyi yoğun bir şekilde kullanan Web uygulamaları için düşük performansa neden olabilir.

[Web uygulamalarında yavaş yükleme varlıklarının olmaması](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a>Verileri kapsülleme

EF Core, modelinizin durumunu doğru bir şekilde kapsüllemek için birkaç özelliği destekler. Etki alanı modellerinde yaygın bir sorun, koleksiyon gezinti özelliklerini herkese açık olarak erişilebilen liste türleri olarak kullanıma sunmasıdır. Bu, tüm ortak çalışmalardan bu koleksiyon türlerinin içeriğini işlemesini sağlar. Bu, koleksiyon ile ilgili önemli iş kurallarını atlayarak, büyük olasılıkla nesneyi geçersiz bir durumda bırakabilir. Bunun çözümü, ilgili koleksiyonlara salt okuma erişimi sunmak ve bu örnekte olduğu gibi istemcilerin bunları işleyebilecekleri yolları tanımlamaya yönelik yöntemleri açıkça sağlamaktır:

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

Bu varlık türünün bir public `List` veya `ICollection` Property sunmaz, bunun yerine temel alınan liste türünü sarmalayan bir `IReadOnlyCollection` tür gösterir. Bu model kullanılırken, şu şekilde bir yedekleme alanı kullanacağınızı Entity Framework Core belirtebilirsiniz:

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

Etki alanı modelinizi iyileştirebilmeniz için bir başka yol da, kimlik olmayan türler için değer nesnelerinin kullanımı ve yalnızca özelliklerine göre ayırt edilebilir. Bu tür türler, varlıklarınızın özellikleri olarak kullanılması, mantığın ait olduğu değer nesnesine özgü mantığı tutmaya yardımcı olabilir ve aynı kavramı kullanan birden fazla varlık arasında yinelenen mantığdan kaçınabilirsiniz. Entity Framework Core, türü sahipli bir varlık olarak yapılandırarak aynı tablodaki değer nesnelerini sahip oldukları varlıkla kalıcı hale getirebilirsiniz, örneğin:

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

Bu örnekte, `ShipToAddress` özelliği türündedir `Address`. `Address`, `Street` ve`City`gibi çeşitli özelliklere sahip bir değer nesnesidir. EF Core, `Order` nesneyi özelliği başına `Address` tek sütunlu, her sütun adının özelliğin adıyla sonuna ekleyerek tablosuna eşler. Bu örnekte, `Order` tablosu `ShipToAddress_Street` ve `ShipToAddress_City`gibi sütunları içerir.

[EF Core 2,2, sahip olunan varlıkların koleksiyonları için destek sunar](https://docs.microsoft.com/ef/core/what-is-new/ef-core-2.2#collections-of-owned-entities)

### <a name="resilient-connections"></a>Dayanıklı bağlantılar

SQL veritabanları gibi dış kaynaklar zaman zaman kullanılabilir olmayabilir. Geçici kullanım durumunda uygulamalar, bir özel durum oluşmasını önlemek için yeniden deneme mantığını kullanabilir. Bu teknik genellikle _bağlantı dayanıklılığı_olarak adlandırılır. En fazla yeniden deneme sayısına ulaşılana kadar, bir üstel bekleme süresi ile yeniden denemeye çalışırken, üstel geri alma tekniğinden [kendi yeniden denelerinizi](https://docs.microsoft.com/azure/architecture/patterns/retry) uygulayabilirsiniz. Bu teknik, bulut kaynaklarının kısa süreler boyunca zaman zaman kullanılamamasına yol açabilir ve bazı isteklerin başarısız olmasıyla sonuçlanır.

Azure SQL DB için Entity Framework Core, iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığını zaten sağlıyor. Ancak dayanıklı EF Core bağlantılarına sahip olmak istiyorsanız her DbContext bağlantısı için Entity Framework yürütme stratejisini etkinleştirmeniz gerekir.

Örneğin, EF Core bağlantı düzeyindeki aşağıdaki kod, bağlantı başarısız olursa yeniden denenen dayanıklı SQL bağlantılarına izin verir.

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>BeginTransaction ve birden çok Dbbağlamlarını kullanarak yürütme stratejileri ve açık işlemler

EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden kullanılabilir işlem haline gelir. Her bir sorgu ve her SaveChanges çağrısı, geçici bir hata oluşursa bir birim olarak yeniden denenir.

Ancak, kodunuz BeginTransaction kullanarak bir işlem başlatırsa, birim olarak değerlendirilmesi gereken kendi işlem grubunuzu tanımlamanız gerekir; bir hata oluşursa işlem içindeki her şeyin geri alınması gerekmez. Bir EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu işlemi yürütmeye çalışırsanız ve içinde birden fazla Dbbağlamdan birkaç SaveChanges eklerseniz, aşağıdaki gibi bir özel durum görürsünüz.

System. InvalidOperationException: Yapılandırılan ' Sqlserverretryingexecutionstrateji ' yürütme stratejisi, Kullanıcı tarafından başlatılan işlemleri desteklemiyor. İşlemdeki tüm işlemleri yeniden kullanılabilir bir birim olarak yürütmek için ' DbContext. Database. Createexecutionstrateji () ' tarafından döndürülen yürütme stratejisini kullanın.

Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmalıdır. Geçici bir hata oluşursa, yürütme stratejisi temsilciyi tekrar çağıracaktır. Aşağıdaki kod, bu yaklaşımın nasıl uygulanacağını göstermektedir:

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

İlk DbContext \_, catalogcontext ve ikinci DbContext, \_ıntegrationeventlogservice nesnesi içindedir. Son olarak, yürütme eylemi birden fazla Dbbağlamı ve EF yürütme stratejisi kullanılarak gerçekleştirilir.

> ### <a name="references--entity-framework-core"></a>Başvurular – Entity Framework Core
>
> - **EF Core docs**  
>   <https://docs.microsoft.com/ef/>
> - **EF Core: İlgili veriler**  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **ASPNET uygulamalarında daha yavaş yükleme varlıklarını önleyin**  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core veya Micro-ORM?

EF Core, kalıcılığı yönetmek için harika bir seçimdir ve çoğu bölüm uygulama geliştiricilerinden veritabanı ayrıntılarını kapsüller, tek seçim değildir. Diğer bir popüler açık kaynak alternatifi [, mikro](https://github.com/StackExchange/Dapper)-ORM adlı bir, yani olarak adlandırılır. Mikro-ORM, nesneleri veri yapılarına eşlemek için hafif ve daha az bir tam özellikli araçtır. Paber söz konusu olduğunda, tasarım hedefleri, verileri almak ve güncelleştirmek için kullandığı temeldeki sorguları tamamen kapsüllemek yerine performansa odaklanmaktadır. Geliştiriciden SQL soyut olmadığından, kaber "metal 'ya yakındır" ve geliştiricilerin belirli bir veri erişim işlemi için kullanmak istedikleri tam sorguları yazmasına izin verir.

EF Core, bu iki önemli özelliğe sahiptir ve bu, bunu bir yandan da kendi performans yüklerine ekler. İlki LINQ ifadelerinden SQL 'e çevirmesidir. Bu çeviriler önbelleğe alınır, ancak bunu ilk kez gerçekleştirmede ek yük vardır. İkincisi, varlıklarda değişiklik izleme (etkin güncelleştirme deyimlerinin üretilebilmesi için). Bu davranış, AsNotTracking uzantısı kullanılarak belirli sorgular için kapatılabilir. EF Core Ayrıca genellikle çok verimli olan ve performans açısından kusursuz bir şekilde kabul edilebilir olan SQL sorguları üretir, ancak yürütülecek kesin sorgu üzerinde iyi denetime ihtiyacınız varsa, EF kullanarak özel SQL (veya saklı yordam yürütme) geçirebilirsiniz Çekirdek, çok. Bu durumda, kaber hala EF Core, ancak biraz daha fazlasını gerçekleştirir. Julie Lerman, Mayıs 2016 MSDN makalesi [kaber, Entity Framework ve hibrit uygulamalarında](https://msdn.microsoft.com/magazine/mt703432.aspx)bazı performans verileri sunmaktadır. Çeşitli veri erişim yöntemlerine yönelik ek performans kıyaslama verileri [, kaber sitesinde](https://github.com/StackExchange/Dapper)bulunabilir.

Kaber için sözdiziminin EF Core nasıl değiştiğini görmek için, öğelerin bir listesini almak için aynı yöntemin bu iki sürümünü göz önünde bulundurun:

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

Kaber ile daha karmaşık nesne grafikleri oluşturmanız gerekiyorsa, ilişkili sorguları kendiniz yazmanız gerekir (EF Core gibi bir Içerme eklemek yerine). Bu, tek tek satırları birden çok eşlenmiş nesne ile eşlemenizi sağlayan çoklu eşleme adlı bir özellik dahil olmak üzere çeşitli sözdizimleri aracılığıyla desteklenir. Örneğin, Kullanıcı türünde bir özellik sahibi olan bir sınıf gönderisi verildiğinde, aşağıdaki SQL gerekli verilerin tümünü döndürür:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Döndürülen her satır hem Kullanıcı hem de veri Gönder ' i içerir. Kullanıcı verilerinin, sahibi özelliği aracılığıyla Post verilerine bağlanması gerektiğinden aşağıdaki işlev kullanılır:

```csharp
(post, user) => { post.Owner = user; return post; }
```

İlişkili kullanıcı verileriyle doldurulmuş bir gönderilerin bir koleksiyonunu döndüren tam kod listesi şöyle olacaktır:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Paber, daha az kapsülleme sağladığından, geliştiricilerin verilerinin nasıl depolandığı, nasıl verimli bir şekilde sorgulanacağı ve bunu getirmek için daha fazla kod yazabileceği hakkında daha fazla bilgi sahibi olmasını gerektirir. Model değiştiğinde, yalnızca yeni bir geçiş (başka bir EF Core özelliği) oluşturmak ve/veya eşleme bilgilerini bir DbContext içinde tek bir yerde güncelleştirmek yerine, etkilenen her sorgunun güncelleştirilmesi gerekir. Bu sorgularda derleme zamanı garantisi yoktur, bu nedenle model veya veritabanındaki değişikliklere yanıt olarak çalışma zamanında kesintiye uğrarabilir ve hataları hızla algılamaya daha zor hale gelebilir. Bu avantajları için Exchange 'de, kaber son derece hızlı performans sunmaktadır.

Çoğu uygulama ve neredeyse tüm uygulamaların birçok bölümü için EF Core, kabul edilebilir performans sağlar. Bu nedenle, geliştirici üretkenlik avantajları büyük olasılıkla performans yükünü ortadan kaldırır. Önbelleğe alma işleminden faydalanabilir sorgular için, gerçek sorgu yalnızca büyük bir yüzde oranında yürütülebilir ve görece küçük sorgu performansı farklılıklarına sahiptir.

## <a name="sql-or-nosql"></a>SQL veya NoSQL

Geleneksel olarak, SQL Server gibi ilişkisel veritabanları kalıcı veri depolama alanı için Market 'e sahiptir, ancak bunlar kullanılabilir tek çözüm değildir. [MongoDB](https://www.mongodb.com/what-is-mongodb) gibi NoSQL veritabanları, nesneleri depolamanın farklı bir yaklaşımını sunmaktadır. Nesneleri tablo ve satırlara eşlemek yerine, diğer bir seçenek de nesne grafiğinin tamamını seri hale getirmek ve sonucu depolar. En azından başlangıçta bu yaklaşımın avantajları basitlik ve performanslardır. Tek bir seri hale getirilmiş bir nesneyi, bir anahtarla, nesnenin veritabanından en son alınmasından bu yana değişmiş olabilecek ilişkiler ve güncelleştirmeler ve satırlar içeren çok sayıda tabloya parçalanmaya kıyasla bir anahtarla depolamak kesinlikle daha basittir. Benzer şekilde, anahtar tabanlı bir mağazadan tek bir nesneyi getirme ve serisini kaldırma genellikle karmaşık birleşimlerden çok daha hızlı ve daha kolay ve aynı nesneyi ilişkisel bir veritabanından tamamen oluşturmak için gereken birden çok veritabanı sorgusuna sahiptir. Kilitleri veya işlemleri ya da sabit bir şemanın olmaması, NoSQL veritabanlarının çok büyük veri kümelerini destekleyen birçok makine genelinde ölçeklendirilmesine çok daha fazla değişiklik yapabilmesini sağlar.

Diğer taraftan, NoSQL veritabanlarının (genellikle çağrıldığı gibi) dezavantajları vardır. İlişkisel veritabanları, tutarlılığı zorlamak ve verilerin çoğaltılmasını önlemek için normalleştirme kullanır. Bu, veritabanının toplam boyutunu azaltır ve paylaşılan veriler için güncelleştirmelerin hemen veritabanının tamamında kullanılabilmesini sağlar. İlişkisel bir veritabanında, bir ülke/bölge adı değiştirilirse adres kayıtları güncelleştirmeden önce güncelleştirilmesi gerekmeden, bir ülke tablosuna KIMLIĞE göre başvurabilir. bu şekilde, Ancak, bir NoSQL veritabanında, adreste ve ilişkili ülkede birçok saklı nesnenin parçası olarak serileştirilmiş olabilir. Ülke/bölge adına yapılan bir güncelleştirme, bu gibi tüm nesnelerin tek bir satır yerine güncelleştirilmesini gerektirir. İlişkisel veritabanları, yabancı anahtarlar gibi kuralları zorunlu tutarak ilişkisel bütünlüğünden de emin olabilir. NoSQL veritabanları genellikle verileri üzerinde böyle kısıtlamalar sunmaz.

Başka bir karmaşıklık NoSQL veritabanlarının sürümü oluşturma ile uğraşmalıdır. Bir nesnenin özellikleri değiştiğinde, bu, depolanan eski sürümlerden seri durumdan çıkarılamayabilir. Bu nedenle, nesnenin serileştirilmiş (önceki) sürümüne sahip tüm var olan nesnelerin yeni şemasına uymak için güncelleştirilmeleri gerekir. Bu, ilişkisel bir veritabanından kavramsal olarak farklılık içermez, burada şema değişiklikleri bazen güncelleştirme betikleri veya eşleme güncelleştirmeleri gerektirir. Ancak, daha fazla veri yinelemesi olduğundan, değiştirilmesi gereken giriş sayısı NoSQL yaklaşımında genellikle çok daha büyüktür.

Nesnelerin birden çok sürümünü depolamak için NoSQL veritabanlarında, sabit bir şema ilişkisel veritabanları genellikle desteklemez. Bununla birlikte, bu durumda, uygulama kodunuzun önceki nesne sürümlerinin varlığını hesaba getirmeniz gerekir, ek karmaşıklık ekliyor.

NoSQL veritabanları genellikle, ilişkisel veritabanları üzerinde performans ve ölçeklenebilirlik avantajları olan [ACID](https://en.wikipedia.org/wiki/ACID)'yi zorlamaz. Bunlara çok büyük veri kümeleri ve normalleştirilmiş tablo yapılarında depolamaya uygun olmayan nesneler de uygundur. Tek bir uygulamanın hem ilişkisel hem de NoSQL veritabanlarından yararlanması, her yerde en iyi şekilde yararlanamaması gerekmez.

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB, bulut tabanlı şemaya ücretsiz veri depolaması sağlayan, tam olarak yönetilen bir NoSQL veritabanı hizmetidir. DocumentDB hızlı ve tahmin edilebilir performans, yüksek kullanılabilirlik, esnek ölçeklendirme ve küresel dağıtım için oluşturulmuştur. Geliştiriciler NoSQL veritabanı olmasına rağmen JSON verilerinde zengin ve tanıdık SQL sorgu yeteneklerini kullanabilir. DocumentDB 'deki tüm kaynaklar JSON belgeleri olarak depolanır. Kaynaklar, meta verileri içeren belgeler ve öğe koleksiyonları olan _akışlar_olan _öğeler_olarak yönetilir. Şekil 8-2, farklı DocumentDB kaynakları arasındaki ilişkiyi gösterir.

![Bir NoSQL JSON veritabanı olan DocumentDB 'de kaynaklar arasındaki hiyerarşik ilişki](./media/image8-2.png)

**Şekil 8-2.** DocumentDB kaynak organizasyonu.

DocumentDB sorgu dili, JSON belgelerini sorgulamak için basit ancak güçlü bir arabirimdir. Dil, ANSI SQL dilbilgisi 'nin bir alt kümesini destekler ve JavaScript nesnesi, diziler, nesne oluşturma ve işlev çağırma için derin tümleştirme ekler.

**Başvurular – DocumentDB**

- DocumentDB tanıtımı  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Diğer kalıcılık seçenekleri

İlişkisel ve NoSQL depolama seçeneklerine ek olarak ASP.NET Core uygulamalar, çeşitli veri biçimlerini ve dosyalarını bulut tabanlı, ölçeklenebilir bir biçimde depolamak için Azure Storage 'ı kullanabilir. Azure Storage, büyük miktarlarda ölçeklenebilir hale gelir. bu nedenle, uygulamanız gerektiriyorsa yüzlerce veya terabayta varan miktarda veri depolamayı başlatabilir. Azure Storage dört tür veriyi destekler:

- Yapılandırılmamış metin veya ikili depolama için, nesne depolama olarak da adlandırılan BLOB depolama alanı.

- Yapılandırılmış veri kümeleri için satır anahtarları aracılığıyla erişilebilen tablo depolaması.

- Sıradan sıra tabanlı mesajlaşma için kuyruk depolama.

- Azure sanal makineler ve şirket içi uygulamalar arasında paylaşılan dosya erişimi için dosya depolama.

**Başvurular – Azure Storage**

- Azure depolama giriş  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Önbelleğe Alma

Web uygulamalarında, her Web isteği mümkün olan en kısa sürede tamamlanmalıdır. Bunu gerçekleştirmenin bir yolu, sunucunun isteği tamamlaması için yapması gereken dış çağrı sayısını sınırlayacaktır. Önbelleğe alma işlemi, sunucuda verilerin bir kopyasının depolanmasını (veya verilerin kaynağından daha kolay sorgulanan başka bir veri deposu) içerir. Web uygulamaları ve özellikle de non-SPA geleneksel olmayan Web uygulamaları, her istekle birlikte Kullanıcı arabiriminin tamamını oluşturmanız gerekir. Bu sıklıkla, bir Kullanıcı isteğinden bir sonrakine aynı veritabanı sorgularının birçok kez oluşturulmasını içerir. Çoğu durumda, bu veriler nadiren değişir, bu yüzden sürekli olarak veritabanından isteme nedenidir. ASP.NET Core, tüm sayfaların önbelleğe alınması ve daha ayrıntılı önbelleğe alma davranışını destekleyen veri önbelleğe alma işlemleri için yanıt önbelleğe almayı destekler.

Önbelleğe alma uygularken, kaygıları göz önünde bulundurmanız önemlidir. Veri erişim mantığınızdaki veya Kullanıcı arabiriminizdeki önbelleğe alma mantığını uygulamaktan kaçının. Bunun yerine, önbelleğe almayı kendi sınıflarında kapsülle ve davranışını yönetmek için yapılandırma kullanın. Bu, açık/kapalı ve tek sorumluluk ilkelerini izler ve uygulamanızda önbelleğe alma işlemini nasıl kullanacağınızı yönetmenizi kolaylaştırır.

### <a name="aspnet-core-response-caching"></a>ASP.NET Core yanıtı önbelleğe alma

ASP.NET Core iki yanıt önbelleği düzeyini destekler. İlk düzey sunucu üzerinde herhangi bir şeyi önbelleğe almaz, ancak istemcilerin ve proxy sunucularının yanıtları önbelleğe almasını sağlayan HTTP üstbilgileri ekler. Bu, bireysel denetleyicilere veya eylemlere ResponseCache özniteliği eklenerek uygulanır:

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

Önceki örnek, istemciye, sonucu 60 saniyeye kadar önbelleğe almak için, bu üst bilginin yanıta eklenmesine neden olur.

Cache-Control: PUBLIC, max-age = 60

Uygulamaya sunucu tarafı bellek içi önbelleğe alma eklemek için Microsoft. AspNetCore. ResponseCaching NuGet paketine başvurmanız ve ardından yanıt önbelleğe alma ara yazılımını eklemeniz gerekir. Bu ara yazılım hem ConfigureServices hem de başlangıçta yapılandırılır:

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

Yanıt önbelleğe alma ara yazılımı, özelleştirmeleri, özelleştirebileceğiniz bir dizi koşula göre otomatik olarak önbelleğe alır. Varsayılan olarak, GET veya HEAD yöntemleri aracılığıyla istenen yalnızca 200 (Tamam) yanıt önbelleğe alınır. Ayrıca, isteklerin Cache-Control: public üst bilgisine sahip bir yanıtı olmalıdır ve yetkilendirme ya da set-Cookie üst bilgisini içeremez. [Yanıt önbelleğe alma ara yazılımı tarafından kullanılan önbelleğe alma koşullarının tüm listesini](/aspnet/core/performance/caching/middleware#conditions-for-caching)görün.

### <a name="data-caching"></a>Veri önbelleğe alma

(Veya buna ek olarak) tam Web yanıtlarını önbelleğe alma yerine, bireysel veri sorgularının sonuçlarını önbelleğe alabilirsiniz. Bunun için, Web sunucusunda bellek önbelleklemesi veya [Dağıtılmış önbellek](/aspnet/core/performance/caching/distributed)kullanabilirsiniz. Bu bölüm, bellek önbelleğe alma işleminde nasıl uygulanacağını gösterir.

ConfigureServices 'e bellek (veya dağıtılmış) önbelleği desteği eklersiniz:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Microsoft. Extensions. Caching. Memory NuGet paketini de eklediğinizden emin olun.

Hizmeti ekledikten sonra, önbelleğe erişmeniz gereken her yerde, bağımlılık ekleme yoluyla ımemorycache istek duyarsınız. Bu örnekte, CachedCatalogService, temel alınan CatalogService uygulamasına erişimi denetleyen (veya davranışı ekleyen) ıconalogservice 'in alternatif bir uygulamasını sağlayarak proxy (veya dekoratör) tasarım modelini kullanıyor.

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

Uygulamayı, hizmetin önbelleğe alınmış sürümünü kullanacak şekilde yapılandırmak için, ancak hala hizmetin oluşturucuda ihtiyacı olan CatalogService örneğini almaya izin vermek için, ConfigureServices 'e şunu ekleyin:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Bu şekilde, katalog verilerini getirmek için veritabanı çağrıları her istek yerine yalnızca dakikada bir kez yapılır. Site trafiğine bağlı olarak, bu, veritabanına yapılan sorgu sayısı üzerinde çok önemli bir etkiye ve ana sayfa için o anda bu hizmetin açığa çıkarılan her birine bağlı olan ortalama sayfa yükleme süresine sahip olabilir.

Önbelleğe alma işlemi uygulandığında ortaya çıkan bir sorun _eski veri_ , diğer bir deyişle, kaynakta Değiştirilen ancak güncel olmayan bir sürümü önbellekte kalır. Bu sorunu hafifletmenin basit bir yolu, yoğun bir uygulama için, verilerin uzatılması için sınırlı sayıda daha fazla avantaj olduğundan, küçük önbellek süreleri kullanmaktır. Örneğin, tek bir veritabanı sorgusu oluşturan ve saniyede 10 kez istenen bir sayfa düşünün. Bu sayfa bir dakika boyunca önbelleğe alınmışsa, 600 ' dan 1 ' e düşürülmesi için dakika başına yapılan Veritabanı sorgularının sayısına,% 99,8 oranında bir azalmaya neden olur. Bunun yerine önbellek süresi bir saat yapılırsa, genel azaltma% 99,997 olur, ancak artık eski verilerin olasılığı ve potansiyel yaşı önemli ölçüde artar.

Diğer bir yaklaşım, içerdikleri veriler güncelleştirilirken önbellek girişlerini önceden kaldırmak olur. Anahtarı biliniyorsa her bir giriş kaldırılabilir:

```csharp
_cache.Remove(cacheKey);
```

Uygulamanız, önbelleğe aldığı girdileri güncelleştirmek için işlevselliği kullanıma sunuyorsa, kodunuzda güncelleştirmeleri gerçekleştiren karşılık gelen önbellek girdilerini kaldırabilirsiniz. Bazen belirli bir veri kümesine bağımlı birçok farklı giriş olabilir. Bu durumda, CancellationChangeToken kullanarak önbellek girişleri arasında bağımlılıklar oluşturmak yararlı olabilir. Bir CancellationChangeToken ile, belirteci iptal ederek birden çok önbellek girdisini bir kez sona erdirebilirsiniz.

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

Önbelleğe alma, veritabanından aynı değerleri tekrar tekrar isteyen web sayfalarının performansını önemli ölçüde iyileştirebilir. Önbelleğe almayı uygulamadan önce veri erişimi ve sayfa performansını ölçdiğinizden emin olun ve yalnızca geliştirme gereksinimi olduğunu gördüğünüz önbelleğe alma işlemini uygulayın. Önbelleğe alma, Web sunucusu bellek kaynaklarını tüketir ve uygulamanın karmaşıklığını artırır. bu sayede, bu tekniği kullanarak erken iyileştirmemenizi önemli değildir.

>[!div class="step-by-step"]
>[Önceki](develop-asp-net-core-mvc-apps.md)İleri
>[](test-asp-net-core-mvc-apps.md)
