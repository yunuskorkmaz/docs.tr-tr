---
title: ASP.NET Core Apps'taki verilerle çalışın
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | ASP.NET Core uygulamalarındaki verilerle çalışma
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 5a38ca94b6df676858e7cb058272e450aaf1572e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78241045"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>ASP.NET Çekirdek Uygulamalarda Verilerle Çalışma

> "Veri değerli bir şeydir ve sistemlerin kendisinden daha uzun süre dayanır."
>
> Tim Berners-Lee

Veri erişimi hemen hemen her yazılım uygulamasının önemli bir parçasıdır. ASP.NET Core, Entity Framework Core (ve Entity Framework 6 da dahil olmak üzere) dahil olmak üzere çeşitli veri erişim seçeneklerini destekler ve herhangi bir .NET veri erişim çerçevesi ile çalışabilir. Hangi veri erişim çerçevesinin kullanılacağının seçimi, uygulamanın gereksinimlerine bağlıdır. Bu seçenekleri ApplicationCore ve Kullanıcı Arabirimi projelerinden soyutlamak ve uygulama ayrıntılarını Altyapı'da kapsüllemek, gevşek bir şekilde birleştirilmiş, test edilebilir yazılımlar üretmeye yardımcı olur.

## <a name="entity-framework-core-for-relational-databases"></a>Varlık Framework Core (ilişkisel veritabanları için)

İlişkisel verilerle çalışması gereken yeni bir ASP.NET Core uygulaması yazıyorsanız, Uygulamanızın verilerine erişmesi için önerilen yoldur. EF Core, .NET geliştiricilerin nesneleri bir veri kaynağına ve kaynaktan kalıcı olarak yapmalarını sağlayan nesne ilişkisisel bir mapper 'dır (O/RM). Genellikle yazması gereken veri erişim kodu geliştiricilerin çoğu için ihtiyacı ortadan kaldırır. ASP.NET Core gibi, EF Core da modüler çapraz platform uygulamalarını desteklemek için sıfırdan yeniden yazılmıştır. Başvurunuza NuGet paketi olarak ekler, Başlangıç'ta yapılandırın ve ihtiyacınız olan her yerde bağımlılık enjeksiyonu yoluyla talep edeyim.

SQL Server veritabanıyla EF Core'u kullanmak için aşağıdaki dotnet CLI komutunu çalıştırın:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

Bir InMemory veri kaynağı için destek eklemek için, sınama için:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a>The DbContext

EF Core ile çalışmak için bir <xref:Microsoft.EntityFrameworkCore.DbContext>alt sınıfa ihtiyacınız var. Bu sınıf, uygulamanızın çalışacağı varlıkların koleksiyonlarını temsil eden özellikleri tutar. eShopOnWeb örneği, öğeler, markalar ve türler için koleksiyonlar içeren bir CatalogContext içerir:

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

DbContext'Inizin DbContextOptions'ı kabul eden bir oluşturucusu olmalı ve bu bağımsız değişkeni temel DbContext oluşturucuya aktarmalıdır. Uygulamanızda yalnızca bir DbContext varsa, DbContextOptions'ın bir örneğini geçirebilirsiniz, ancak birden fazla seçeneğiniz\<varsa, DbContext türünizde genel parametre olarak geçen genel DbContextOptions T> türünü kullanmanız gerekir.

### <a name="configuring-ef-core"></a>EF Çekirdeğini Yapılandırma

ASP.NET Core uygulamanızda, genellikle EF Core'u Yapılandırma Hizmetleri yönteminizde yapılandıracaksınız. EF Core, yapılandırmasını kolaylaştırmak için birkaç yararlı uzantı yöntemini destekleyen bir DbContextOptionsBuilder kullanır. CatalogContext'ı Yapılandırma'da tanımlanan bir bağlantı dizesine sahip bir SQL Server veritabanı kullanacak şekilde yapılandırmak için, ConfigureServices'e aşağıdaki kodu eklersiniz:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Bellek veritabanını kullanmak için:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

EF Core'u yükledikten, DbContext alt türünü oluşturduktan ve ConfigureServices'te yapılandırdıktan sonra EF Core'u kullanmaya hazırsınız. DbContext türünizin bir örneğini ihtiyacı olan herhangi bir hizmette isteyebilir ve kalıcı kuruluşlarınızla linq'i yalnızca bir koleksiyondaymış gibi kullanmaya başlayabilirsiniz. EF Core, verilerinizi depolamak ve almak için LINQ ifadelerinizi SQL sorgularına çevirme işini yapar.

EF Core'un yürüttüğü sorguları, bir kaydediciyi yapılandırarak ve düzeyin Şekil 8-1'de gösterildiği gibi en az Bilgi olarak ayarlanmasını sağlayarak görebilirsiniz.

![EF Core sorgularını konsola günlüğe kaydetme](./media/image8-1.png)

**Şekil 8-1**. EF Core sorgularını konsola günlüğe kaydetme

### <a name="fetching-and-storing-data"></a>Veri alma ve depolama

EF Core'dan veri almak için uygun özelliğe erişin ve sonucu filtrelemek için LINQ'yi kullanın. Ayrıca, sonucu bir türden diğerine dönüştürerek projeksiyon gerçekleştirmek için LINQ'yi de kullanabilirsiniz. Aşağıdaki örnek, adlarına göre sıralanan, Etkin özelliği tarafından filtrelenen ve SelectListItem türüne yansıtılan CatalogBrands'i alır:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Yukarıdaki örnekte, sorguyu hemen yürütmek için Çağrı'yı ToListAsync'e eklemek önemlidir. Aksi takdirde, ekstre, numaralandırılıncaya kadar yürütülmeyecek bir IQueryable\<SelectListItem> marka öğelere atar. Yöntemlerden IQueryable sonuçları dönen artıları ve eksileri vardır. EF Core sorgusunun daha da değiştirilmesini sağlar, ancak EF Core'un çeviremediği sorguya işlemler eklenirse yalnızca çalışma zamanında oluşan hatalara da neden olabilir. Herhangi bir filtreyi veri erişimini gerçekleştiren yönteme aktarmak ve sonuç olarak bellek içi bir koleksiyonu\<(örneğin, T> Listesi) döndürmek genellikle daha güvenlidir.

EF Core, kalıcılıktan aldığı varlıklardaki değişiklikleri izler. İzlenen bir varlıktaki değişiklikleri kaydetmek için, dbContext'da SaveChanges yöntemini arayarak varlığı almak için kullanılan DbContext örneğiyle aynı olduğundan emin olursunuz. Varlıkları ekleme ve kaldırma doğrudan uygun DbSet özelliği üzerinde, yine veritabanı komutları yürütmek için SaveChanges bir çağrı ile yapılır. Aşağıdaki örnek, varlıkların kalıcılıktan çıkarılmasını, güncellenmesini ve kaldırdığını gösterir.

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

EF Core, alma ve kaydetme için hem senkron hem de async yöntemlerini destekler. Web uygulamalarında, veri erişim işlemlerinin tamamlanmasını beklerken web sunucusu iş parçacıklarının engellenmemesi için async/await deseninin async/await deseni kullanılması önerilir.

### <a name="fetching-related-data"></a>İlgili verileri alma

EF Core varlıkları aldığında, veritabanında doğrudan bu varlıkla depolanan tüm özellikleri doldurur. İlgili varlıkların listeleri gibi gezinti özellikleri doldurulmaz ve değerleri null olarak ayarlanmış olabilir. Bu, EF Core'un gerekenden daha fazla veri getirmemesini sağlar, bu da özellikle web uygulamaları için önemlidir ve bu da istekleri hızlı bir şekilde işlemeli ve yanıtları verimli bir şekilde döndürmelidir. _Eager yüklemeyi_kullanarak bir varlıkla ilişkileri eklemek için, sorgudaki Uzantı Ekle yöntemini kullanarak özelliği gösterilir:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Birden çok ilişki ekleyebilirsiniz ve ThenInclude'ı kullanarak alt ilişkileri de ekleyebilirsiniz. EF Core, ortaya çıkan varlık kümesini almak için tek bir sorgu yürütür. Alternatif olarak bir '' geçerek navigasyon özellikleri navigasyon özellikleri ekleyebilirsiniz. `.Include()` -uzantısı yöntemine ayrılmış dize, böyle:

```csharp
    .Include(“Items.Products”)
```

Filtreleme mantığını kapsüllemenin yanı sıra, bir belirtim, hangi özelliklerin doldurulması gerektiği de dahil olmak üzere döndürülecek verilerin şeklini de belirtebilir. eShopOnWeb örnek belirtimi içinde istekli yükleme bilgileri kapsülleme gösteren çeşitli özellikleri içerir. Belirtimin sorgunun bir parçası olarak nasıl kullanıldığını burada görebilirsiniz:

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

İlgili verileri yüklemek için başka bir seçenek _açık yükleme_kullanmaktır. Açık yükleme, zaten alınmış bir varlığa ek veri yüklemenize olanak tanır. Bu veritabanına ayrı bir istek içerdiğinden, istek başına yapılan veritabanı turu sayısını en aza indirmek gerekir web uygulamaları için önerilmez.

_Tembel yükleme,_ uygulama tarafından başvurulan ilgili verileri otomatik olarak yükleyen bir özelliktir. EF Core sürüm 2.1 tembel yükleme için destek ekledi. Tembel yükleme varsayılan olarak etkin değildir `Microsoft.EntityFrameworkCore.Proxies`ve .' yi yüklemeyi gerektirir. Açık yüklemede olduğu gibi, kullanımı her web isteği içinde ek veritabanı sorguları yapılmasıyla sonuçlanacaktır, çünkü tembel yükleme genellikle web uygulamaları için devre dışı bırakılmalıdır. Ne yazık ki, tembel yükleme nin neden olduğu genel gider genellikle geliştirme sırasında fark edilmez, gecikme süresi küçük olduğunda ve genellikle test için kullanılan veri kümeleri küçükolduğunda. Ancak, üretimde, daha fazla kullanıcı, daha fazla veri ve daha fazla gecikme süresiyle, ek veritabanı istekleri genellikle tembel yüklemeden yoğun olarak kullanan web uygulamaları için düşük performansa neden olabilir.

[Web Uygulamalarında Tembel Yükleme Varlıklarından Kaçının](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a>Verileri kapsülleme

EF Core, modelinizin durumunu düzgün bir şekilde kapsüllemesine olanak tanıyan çeşitli özellikleri destekler. Etki alanı modellerinde sık karşılaşılan bir sorun, koleksiyon gezinti özelliklerini genel olarak erişilebilen liste türleri olarak ortaya çıkarmalarıdır. Bu, herhangi bir ortak bilgi nisabı, koleksiyonla ilgili önemli iş kurallarını atlayarak nesneyi geçersiz bir durumda bırakabilecek bu koleksiyon türlerinin içeriğini işlemesine olanak tanır. Bunun çözümü, ilgili koleksiyonlara salt okunur erişimi ortaya çıkarmak ve bu örnekte olduğu gibi istemcilerin bunları manipüle etme yollarını tanımlayan yöntemler açıkça sağlamaktır:

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

Bu varlık türü bir ortak `List` `ICollection` veya özellik ortaya çıkarmaz, ancak bunun yerine temel Liste türünü saran bir `IReadOnlyCollection` türü ortaya çıkarır. Bu deseni kullanırken, destek alanını aşağıdaki gibi kullanmak üzere Entity Framework Core'a belirtebilirsiniz:

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

Etki alanı modelinizi geliştirmenin başka bir yolu da, kimlik eksikliği olan ve yalnızca özellikleriyle ayırt edilen türler için değer nesnelerinin kullanılmasıdır. Varlıklarınızın özellikleri gibi türleri kullanmak, mantığıa ait olduğu değer nesnesine özgü tutmaya yardımcı olabilir ve aynı kavramı kullanan birden çok varlık arasında yinelenen mantıktan kaçınabilir. Varlık Framework Core'da, türü sahipolunan bir varlık olarak yapılandırarak, değer nesnelerini sahipleriyle aynı tabloda kalıcı olarak sürebilirsiniz:

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

Bu örnekte, `ShipToAddress` özellik türü. `Address` `Address`gibi çeşitli özelliklere sahip bir `Street` `City`değer nesnesidir. EF Core, `Order` nesneyi her özellik `Address` başına bir sütunla tablosuyla eşler ve her sütun adını özelliğin adıyla öne çözer. Bu örnekte, `Order` tablo gibi `ShipToAddress_Street` sütunlar `ShipToAddress_City`içerecektir ve . İstenirse, sahip olunan türleri ayrı tablolarda depolamak da mümkündür.

[EF Core'da](/ef/core/modeling/owned-entities)sahip olunan varlık desteği hakkında daha fazla bilgi edinin.

### <a name="resilient-connections"></a>Esnek bağlantılar

SQL veritabanları gibi dış kaynaklar bazen kullanılamayabilir. Geçici kullanılabilirlik durumlarında, uygulamalar bir özel durum yükseltmeyi önlemek için yeniden deneme mantığını kullanabilir. Bu teknik genellikle bağlantı _esnekliği_olarak adlandırılır. Üstel geri [leme tekniğiyle,](https://docs.microsoft.com/azure/architecture/patterns/retry) en yüksek yeniden deneme sayısına ulaşılıncaya kadar katlanarak artan bekleme süresiyle yeniden denemeyi deneyerek kendi yeniden denemenizi uygulayabilirsiniz. Bu teknik, bulut kaynaklarının kısa süreler için zaman zaman kullanılamayabileceği ve bazı isteklerin başarısız lığa yol açabileceği gerçeğini benimser.

Azure SQL DB için Entity Framework Core zaten dahili veritabanı bağlantısı esnekliği ve yeniden deneme mantığı sağlar. Ancak esnek EF Core bağlantılarına sahip olmak istiyorsanız, her DbContext bağlantısı için Varlık Çerçevesi yürütme stratejisini etkinleştirmeniz gerekir.

Örneğin, EF Core bağlantı düzeyindeki aşağıdaki kod, bağlantı başarısız olursa yeniden denenen esnek SQL bağlantılarını sağlar.

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>BeginTransaction ve birden çok DbContexts kullanarak yürütme stratejileri ve açık işlemler

EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden çalışılabilir işlemi haline gelir. Geçici bir hata oluşursa, SaveChanges'a yapılan her sorgu ve her çağrı birim olarak yeniden denenir.

Ancak, kodunuz BeginTransaction kullanarak bir işlem başlatıyorsa, birim olarak işlem yapılması gereken kendi işlem grubunuzu tanımlıyorsunuz; bir hata oluşursa, işlem içindeki her şeyin geri alınması gerekir. Bir EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu işlemi yürütmeye çalışırsanız ve içinde birden çok DbContexts'tan birkaç SaveChanges eklerseniz, aşağıdaki gibi bir özel durum görürsünüz.

System.InvalidOperationException: Yapılandırılan yürütme stratejisi 'SqlServerRetryingExecutionStrategy' kullanıcı tarafından başlatılan hareketleri desteklemez. İşlemdeki tüm işlemleri yeniden denilebilir bir birim olarak yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisini kullanın.

Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmaktır. Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır. Aşağıdaki kod, bu yaklaşımın nasıl uygulanacağını gösterir:

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

İlk DbContext \_catalogContext ve ikinci DbContext entegrasyonEventLogService nesneiçindedir. \_ Son olarak, Commit eylem birden çok DbContexts ve bir EF Yürütme Stratejisi kullanılarak gerçekleştirilir.

> ### <a name="references--entity-framework-core"></a>Referanslar – Varlık Çerçeve Çekirdeği
>
> - **EF Çekirdek Dokümanlar**
>   <https://docs.microsoft.com/ef/>
> - **EF Core: İlgili Veriler**
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **ASPNET Uygulamalarında Tembel Yükleme Varlıklarından Kaçının**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core veya mikro-ORM?

EF Core kalıcılığı yönetmek için mükemmel bir seçim olsa da ve çoğunlukla uygulama geliştiricilerin veritabanı ayrıntılarını kapsüller, tek seçenek değildir. Başka bir popüler açık kaynak alternatif [Dapper](https://github.com/StackExchange/Dapper), sözde mikro-ORM olduğunu. Mikro-ORM, nesneleri veri yapılarına eşlemek için daha hafif ve daha az özellikli bir araçtır. Dapper'ın durumunda, tasarım hedefleri verileri almak ve güncelleştirmek için kullandığı temel sorguları tam olarak kapsüllemek yerine performansa odaklanır. Sql'i geliştiriciden soyutlamadığı için, Dapper "metale daha yakındır" ve geliştiricilerin belirli bir veri erişim işlemi için tam olarak kullanmak istedikleri sorguları yazmalarına olanak tanır.

EF Core, dapper onu ayıran ama aynı zamanda performans yükü eklemek sağlayan iki önemli özelliklere sahiptir. Bunlardan ilki LINQ ifadelerinden SQL'e çevrilmedir. Bu çeviriler önbelleğe alınmış, ancak yine de ilk kez bunları gerçekleştirmek için havai vardır. İkincisi, varlıklar üzerinde değişiklik izleme (verimli güncelleştirme deyimleri oluşturulabilir. Bu davranış, AsNotTracking uzantısı kullanılarak belirli sorgular için kapatılabilir. EF Core ayrıca genellikle çok verimli ve her durumda mükemmel bir performans açısından kabul edilebilir SQL sorguları oluşturur, ancak yürütülecek kesin sorgu üzerinde ince kontrol gerekiyorsa, özel SQL (veya saklı bir yordam yürütmek) EF kullanarak geçirebilirsiniz Çekirdek de öyle. Bu durumda, Dapper hala EF Core daha iyi performans, ama sadece biraz. Julie Lerman, Mayıs 2016'daki MSDN makalesi [Dapper, Entity Framework ve Hybrid Apps'da](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps)bazı performans verileri sunar. Çeşitli veri erişim yöntemleri için ek performans kıyaslama verileri [Dapper sitesinde](https://github.com/StackExchange/Dapper)bulunabilir.

Dapper sözdiziminin EF Core'dan nasıl değiştiğini görmek için, öğelerin listesini almak için aynı yöntemin bu iki sürümü göz önünde bulundurun:

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

Dapper ile daha karmaşık nesne grafikleri oluşturmanız gerekiyorsa, ilişkili sorguları kendiniz yazmanız gerekir (EF Core'da yaptığınız gibi bir Include eklemek yerine). Bu, tek tek satırları birden çok eşlenen nesnelerle eşleştirmenize olanak tanıyan Çoklu Eşleme adlı bir özellik de dahil olmak üzere çeşitli sözdizimilerle desteklenir. Örneğin, bir özellik Sahibi Kullanıcı ile bir sınıf Post verilen, aşağıdaki SQL gerekli tüm verileri döndürür:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Döndürülen her satır hem Kullanıcı hem de Posta verilerini içerir. Kullanıcı verilerinin Sahibi özelliği aracılığıyla Posta verilerine eklenmesi gerektiğinden, aşağıdaki işlev kullanılır:

```csharp
(post, user) => { post.Owner = user; return post; }
```

İlişkili kullanıcı verileriyle dolu Sahibi mülkü olan gönderikoleksiyonunu döndürmek için tam kod listesi aşağıdakiler olacaktır:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Daha az kapsülleme sunduğundan, Dapper geliştiricilerin verilerinin nasıl depolandığı, verimli bir şekilde nasıl sorgulanacakları ve getirmek için daha fazla kod yazmaları hakkında daha fazla bilgi sahibi olmasını gerektirir. Model değiştiğinde, yalnızca yeni bir geçiş (başka bir EF Core özelliği) oluşturmak ve/veya eşleme bilgilerini DbContext'da tek bir yerde güncelleştirmek yerine, etkilenen her sorgu güncelleştirilmelidir. Bu sorguların derleme zamanı garantisi yoktur, bu nedenle model veya veritabanındaki değişikliklere yanıt olarak çalışma zamanında bozulabilir ve hataların hızlı bir şekilde algılatılması zorolabilir. Bu takaslar karşılığında Dapper son derece hızlı bir performans sergiliyor.

EF Core, çoğu uygulama ve hemen hemen tüm uygulamaların çoğu nda kabul edilebilir performans sunar. Böylece, geliştirici verimlilik yararları performans yükü ağır basması muhtemeldir. Önbelleğe alma dan yararlanabilir sorgular için, gerçek sorgu yalnızca zaman küçük bir yüzdesi yürütülebilir, nispeten küçük sorgu performans farkları tartışmalı hale.

## <a name="sql-or-nosql"></a>SQL veya NoSQL

Geleneksel olarak, SQL Server gibi ilişkisel veritabanları kalıcı veri depolama için pazar hakim, ancak tek çözüm mevcut değildir. [MongoDB](https://www.mongodb.com/what-is-mongodb) gibi NoSQL veritabanları nesneleri depolamak için farklı bir yaklaşım sunar. Nesneleri tablolarla ve satırlarla eşlemek yerine, başka bir seçenek tüm nesne grafiğini seri hale getirmek ve sonucu depolamaktır. Bu yaklaşımın yararları, en azından başlangıçta, basitlik ve performans vardır. Tek bir serileştirilmiş nesneyi anahtarla depolamak, nesneyi veritabanından en son alınan nesneden beri değişmiş olabilecek ilişkiler ve güncelleştirme ve satırlarla birçok tabloya ayırmaktan daha kolaydır. Benzer şekilde, tek bir nesneyi anahtar tabanlı bir depodan alma ve çıkarma genellikle karmaşık birleştirmelerden veya ilişkisel bir veritabanından aynı nesneyi tam olarak oluşturmak için gereken birden çok veritabanı sorgusundan çok daha hızlı ve kolaydır. Kilitlerin veya hareketlerin veya sabit bir şema nın olmaması, NoSQL veritabanlarını çok büyük veri kümelerini destekleyerek birçok makinede ölçeklenmeye elverişli hale getirir.

Öte yandan, NoSQL veritabanları (genellikle denir) kendi dezavantajları vardır. İlişkisel veritabanları tutarlılığı zorlamak ve verilerin çoğaltılmasını önlemek için normalleştirme kullanır. Bu, veritabanının toplam boyutunu azaltır ve paylaşılan verilere yapılan güncelleştirmelerin veritabanı nda hemen kullanılabilir olmasını sağlar. İlişkisel bir veritabanında, Adres tablosu, bir ülke/bölgenin adı değiştirilirse, adres kayıtlarının kendilerinin güncelleştirilmelerine gerek kalmadan güncelleştirmeden yararlanacağı şekilde, bir Ülke tablosuna kimlik le başvurulabilir. Ancak, Bir NoSQL veritabanında, Adres ve ilişkili Ülke birçok depolanan nesnelerin bir parçası olarak serileştirilmiş olabilir. Bir ülke/bölge adına yapılan bir güncelleştirme, tek bir satır yerine tüm bu nesnelerin güncelleştirilmesini gerektirir. İlişkisel veritabanları da yabancı anahtarlar gibi kuralları uygulayarak ilişkisel bütünlüğü sağlayabilir. NoSQL veritabanları genellikle verilerinde bu tür kısıtlamalar sunmuyoruz.

NoSQL veritabanlarının uğraşması gereken bir diğer karmaşıklık ise sürümdür. Bir nesnenin özellikleri değiştiğinde, depolanan geçmiş sürümlerden deserialed mümkün olmayabilir. Bu nedenle, nesnenin serileştirilmiş (önceki) sürümüne sahip varolan tüm nesnelerin yeni şemasına uyacak şekilde güncelleştirilmesi gerekir. Bu, şema değişikliklerinin bazen güncelleştirme komut dosyaları veya eşleme güncelleştirmeleri gerektirdiği ilişkisel bir veritabanından kavramsal olarak farklı değildir. Ancak, değiştirilmesi gereken giriş sayısı, daha fazla veri yinelemesi olduğundan, NoSQL yaklaşımında genellikle çok daha fazladır.

NoSQL veritabanlarında nesnelerin birden çok sürümlerini depolamak mümkündür, sabit şema ilişkisel veritabanları genellikle desteklemez. Ancak, bu durumda uygulama kodunuzu nesnelerin önceki sürümlerinin varlığını hesaba katmak gerekir, ek karmaşıklık ekleyerek.

NoSQL veritabanları genellikle [ACID](https://en.wikipedia.org/wiki/ACID)zorlamaz, bu da ilişkisel veritabanları üzerinde hem performans hem de ölçeklenebilirlik avantajları olduğu anlamına gelir. Bunlar, normalleştirilmiş tablo yapılarında depolamaiçin uygun olmayan son derece büyük veri kümeleri ve nesneler için uygundur. Tek bir uygulamanın hem ilişkisel hem de NoSQL veritabanlarından yararlanamaması için hiçbir neden yoktur.

## <a name="azure-cosmos-db"></a>Azure Cosmos DB

Azure Cosmos DB, bulut tabanlı şema içermeyen veri depolama sunan tam olarak yönetilen bir NoSQL veritabanı hizmetidir. Azure Cosmos DB, hızlı ve öngörülebilir performans, yüksek kullanılabilirlik, elastik ölçekleme ve küresel dağıtım için üretilmiştir. NoSQL veritabanı olmasına rağmen, geliştiriciler JSON verilerinde zengin ve tanıdık SQL sorgu özelliklerini kullanabilir. Azure Cosmos DB'deki tüm kaynaklar JSON belgeleri olarak depolanır. Kaynaklar, meta veri içeren belgeler ve öğelerin koleksiyonları olan _özet akışları_olan _öğeler_olarak yönetilir. Şekil 8-2, farklı Azure Cosmos DB kaynakları arasındaki ilişkiyi gösterir.

![NoSQL JSON veritabanı olan Azure Cosmos DB'deki kaynaklar arasındaki hiyerarşik ilişki](./media/image8-2.png)

**Şekil 8-2.** Azure Cosmos DB kaynak organizasyonu.

Azure Cosmos DB sorgu dili, JSON belgelerini sorgulamak için basit ama güçlü bir arayüzdür. Dil, ANSI SQL dil bilgisinin bir alt kümesini destekler ve JavaScript nesnesi, dizileri, nesne oluşturması ve işlev çağrısı için derin tümleştirme sağlar.

**Referanslar – Azure Cosmos DB**

- Azure Cosmos DB Giriş<https://docs.microsoft.com/azure/cosmos-db/introduction>

## <a name="other-persistence-options"></a>Diğer kalıcılık seçenekleri

İlişkisel ve NoSQL depolama seçeneklerine ek olarak, ASP.NET Core uygulamaları çeşitli veri biçimlerini ve dosyalarını bulut tabanlı, ölçeklenebilir bir şekilde depolamak için Azure Depolama'yı kullanabilir. Azure Depolama büyük ölçüde ölçeklenebilir, böylece küçük miktarlarda veri depolamaya başlayabilir ve uygulamanız gerektiriyorsa yüzlerce veya terabayt depolayacak kadar ölçeklendirebilirsiniz. Azure Depolama dört veri çeşidini destekler:

- Nesne depolama olarak da adlandırılan, yapılandırılmamış metin veya ikili depolama için Blob Depolama.

- Yapılandırılmış veri kümeleri için Tablo Depolama, satır tuşları ile erişilebilir.

- Güvenilir sıra tabanlı iletiler için Sıra Depolama.

- Azure sanal makineleri ve şirket içi uygulamalar arasında paylaşılan dosya erişimi için Dosya Depolama.

**Referanslar – Azure Depolama**

- Azure Depolama Girişi<https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Önbelleğe alma

Web uygulamalarında, her web isteği mümkün olan en kısa sürede tamamlanmalıdır. Bunu başarmanın bir yolu, sunucunun isteği tamamlamak için yapması gereken dış arama sayısını sınırlamaktır. Önbelleğe alma, sunucuda (veya veri kaynağından daha kolay sorgulanan başka bir veri deposunda) bir veri kopyasını depolamayı içerir. Web uygulamaları ve özellikle SPA olmayan geleneksel web uygulamaları, her istek ile tüm kullanıcı arabirimi oluşturmak gerekir. Bu, sık sık aynı veritabanı sorgularının çoğunu bir kullanıcı isteğinden diğerine tekrar tekrar yapmayı içerir. Çoğu durumda, bu veriler nadiren değişir, bu nedenle veritabanından sürekli olarak istemek için çok az neden vardır. ASP.NET Core, tüm sayfaların önbelleğe alınmış şekilde önbelleğe alınmış yanıtını ve daha ayrıntılı önbelleğe alma davranışını destekleyen veri önbelleğe alma özelliğini destekler.

Önbelleğe alma uygularken, endişeleri ayrıştırmayı göz önünde bulundurmak önemlidir. Veri erişim mantığınızda veya kullanıcı arabiriminizde önbelleğe alma mantığı uygulamaktan kaçının. Bunun yerine, önbelleğe alma kapamayı kendi sınıflarında saklar ve davranışını yönetmek için yapılandırmayı kullanın. Bu, Açık/Kapalı ve Tek Sorumluluk ilkelerini izler ve büyüdükçe uygulamanızda önbelleğe alma nızı yönetmenize kolaylaştırır.

### <a name="aspnet-core-response-caching"></a>ASP.NET Çekirdek yanıt önbelleğe alma

ASP.NET Core iki yanıt önbelleğe alma düzeylerini destekler. İlk düzey sunucuda hiçbir şeyi önbelleğe almaz, ancak istemcileri ve proxy sunucularını önbellek yanıtlarına öğreten HTTP üstbilgileri ekler. Bu, yanıt önbellek özniteliğini tek tek denetleyicilere veya eylemlere ekleyerek uygulanır:

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

Önceki örnek, aşağıdaki üstbilginin yanıta eklenmesiyle sonuçlanır ve istemcilere sonucu 60 saniyeye kadar önbelleğe almalarını bildirir.

Önbellek-Kontrol: kamu, max-age=60

Uygulamaya sunucu tarafı bellek önbelleğe almak için Microsoft.AspNetCore.ResponseCaching NuGet paketine başvurmanız ve ardından Yanıt Önbelleği ara takımını eklemeniz gerekir. Bu ara yazılım, Hem Yapılandırma Hizmetleri'nde hem de Başlangıç'ta Yapılandırıldığında yapılandırılır:

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

Yanıt Önbelleğe Alma Middleware, özelleştirebileceğiniz bir dizi koşula bağlı olarak yanıtları otomatik olarak önbelleğe alacaktır. Varsayılan olarak, GET veya HEAD yöntemleri yle istenen yalnızca 200 (Tamam) yanıt önbelleğe alınır. Buna ek olarak, isteklerin önbellek denetimi yle yanıt vermesi gerekir: genel üstbilgi ve Yetkilendirme veya Ayar-Çerez üstbilgi içeremez. Ara [yazılım önbelleğe alma yanıtı tarafından kullanılan önbelleğe alma koşullarının tam listesine](/aspnet/core/performance/caching/middleware#conditions-for-caching)bakın.

### <a name="data-caching"></a>Verileri önbelleğe alma

Tam web yanıtlarını önbelleğe almak (veya buna ek olarak) yerine, tek tek veri sorgularının sonuçlarını önbelleğe alabilirsiniz. Bunun için, bellek önbelleğe alma web sunucusunda kullanabilirsiniz veya [dağıtılmış bir önbellek](/aspnet/core/performance/caching/distributed)kullanabilirsiniz. Bu bölümde bellek önbelleğe nasıl uygulanacağını gösterecektir.

ConfigureServices'te bellek (veya dağıtılmış) önbelleğe alma desteği eklersiniz:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Microsoft.Extensions.Caching.Memory NuGet paketini de eklediğinizden emin olun.

Hizmeti ekledikten sonra, önbelleğe erişmek için ihtiyacınız olan her yerde bağımlılık enjeksiyonu yoluyla IMemoryCache'yi talep edeyim. Bu örnekte, CachedCatalogService, temel CatalogService uygulamasına erişimi kontrol eden (veya davranış ekleyen) ICatalogService'in alternatif bir uygulamasını sağlayarak Proxy (veya Dekoratör) tasarım deseni kullanır.

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

Uygulamayı hizmetin önbelleğe alınmış sürümünü kullanacak şekilde yapılandırmak, ancak yine de hizmetin, oluşturucusunda ihtiyaç duyduğu CatalogService örneğini almasına izin vermek için, ConfigureServices'e aşağıdakileri eklersiniz:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Bu durumda, veritabanı katalog verilerini almak için her istek yerine dakikada yalnızca bir kez yapılır. Siteye gelen trafiğe bağlı olarak, bu veritabanına yapılan sorguların sayısı ve şu anda bu hizmet tarafından maruz kalan sorguların üçüne de bağlı olan ana sayfanın ortalama sayfa yükleme süresi üzerinde önemli bir etkisi olabilir.

Önbelleğe alma uygulandığında ortaya çıkan bir sorun _eski verilerdir_ – yani kaynakta değişen ancak güncel olmayan bir sürüm önbellekte kalan verilerdir. Meşgul bir uygulama için önbelleğe alınan uzunluk verilerini genişletmenin sınırlı ek yararı olduğundan, bu sorunu azaltmanın basit bir yolu küçük önbellek süreleri kullanmaktır. Örneğin, tek bir veritabanı sorgusu yapan ve saniyede 10 kez istenen bir sayfayı düşünün. Bu sayfa bir dakika süreyle önbelleğe alınmışsa, dakikada yapılan veritabanı sorgularının sayısının 600'den 1'e düşmesine ve %99,8'lik bir azalmaya neden olur. Bunun yerine önbellek süresi bir saat yapılmış olsaydı, genel azaltma% 99.997 olurdu, ancak şimdi olasılık ve eski veri potansiyel yaş hem önemli ölçüde artmıştır.

Başka bir yaklaşım, içerdikleri veriler güncelleştirildiğinde önbellek girişlerini proaktif olarak kaldırmaktır. Anahtarı biliniyorsa, herhangi bir tek tek giriş kaldırılabilir:

```csharp
_cache.Remove(cacheKey);
```

Uygulamanız önbelleğe aldığı girişleri güncelleştirme işlevini ortaya çıkarırsa, kodunuzda güncelleştirmeleri gerçekleştiren ilgili önbellek girişlerini kaldırabilirsiniz. Bazen belirli bir veri kümesine bağlı birçok farklı giriş olabilir. Bu durumda, bir İptalChangeToken kullanarak önbellek girişleri arasında bağımlılıklar oluşturmak için yararlı olabilir. İptalChangeToken ile, belirteci iptal ederek aynı anda birden çok önbellek girişi nin süresi dolabilir.

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

Önbelleğe alma, veritabanından aynı değerleri tekrar tekrar isteyen web sayfalarının performansını önemli ölçüde artırabilir. Önbelleğe alma uygulamadan önce veri erişimini ve sayfa performansını ölçtüğüğünden ve yalnızca iyileştirme gereksinimini gördüğünüz durumlarda önbelleğe aldığınızdan emin olun. Önbelleğe alma, web sunucusu bellek kaynaklarını tüketir ve uygulamanın karmaşıklığını artırır, bu nedenle bu tekniği kullanarak zamanından önce optimize etmemeniz önemlidir.

>[!div class="step-by-step"]
>[Önceki](develop-asp-net-core-mvc-apps.md)
>[Sonraki](test-asp-net-core-mvc-apps.md)
