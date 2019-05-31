---
title: ASP.NET Core uygulamaları verilerle çalışın
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | ASP.NET Core uygulamalarında verilerle çalışma
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 9f765acce89bec1fd73e9c43a6e7d75d78be785d
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423994"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>ASP.NET Core uygulamaları verilerle çalışma

> "Veri değerli bir şeydir ve sistemler daha uzun süre gider."
>
> Tim Berners-Lee

Veri erişimi, neredeyse tüm yazılım uygulamanın önemli bir parçasıdır. ASP.NET Core, Entity Framework Core (ve Entity Framework 6 de) dahil olmak üzere, veri erişim seçenekleri çeşitli destekler ve tüm .NET veri erişim framework ile çalışabilir. Hangisinin kullanılacağını framework verilere seçimi, uygulamanın gereksinimlerine bağlıdır. Bu seçenekler ApplicationCore ve UI projelerindeki özetleyen ve altyapı, uygulama ayrıntılarını kapsüllemek gevşek, test edilebilir yazılım üretmeye yardımcı olur.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (için ilişkisel veritabanları)

İlişkisel verilerle çalışmak için gereken yeni bir ASP.NET Core uygulaması yazıyorsanız, Entity Framework Core (EF Core) uygulamanız kendi verilerine erişim için önerilen yöntem olduğu. EF Core, .NET geliştiricilerinin nesneleri için ve bir veri kaynağından kalıcı hale getirmek bir nesne ilişkisel eşleyicidir (O/RM) ' dir. Bu, çoğu, geliştiriciler genellikle yazmanız gerekirdi veri erişim kodu gereksinimini ortadan kaldırır. EF çekirdekli ASP.NET Core gibi destek modüler platformlar arası uygulamaları için baştan yazıldı. Bir NuGet paketi olarak uygulamanıza ekleyin, başlangıç yapılandırmak ve ihtiyaç duyduğunuz yerde, bağımlılık ekleme isteyin.

EF Core ile bir SQL Server veritabanını kullanmak için aşağıdaki dotnet CLI komutunu çalıştırın:

DotNet paketini Microsoft.EntityFrameworkCore.SqlServer ekleyin

Test etmek için bir Inmemory veri kaynağı için destek eklemek için:

DotNet paketini Microsoft.EntityFrameworkCore.InMemory ekleyin

### <a name="the-dbcontext"></a>DbContext

EF Core ile çalışmak için öğesinin gerekir. <xref:Microsoft.EntityFrameworkCore.DbContext>. Bu sınıf, uygulamanızın çalışacağı varlık koleksiyonları özellikler içerir. Koleksiyon öğeleri, markalar ve türlerini içeren bir CatalogContext eShopOnWeb örneği içerir:

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

DbContext DbContextOptions kabul eden bir oluşturucuya sahip olması ve bu bağımsız değişken temel DbContext oluşturucusuna geçirmeniz gerekir. Yalnızca bir DbContext uygulamanızda sahip olduğunuz, DbContextOptions örneğini geçirebilirsiniz, ancak varsa, birden fazla genel DbContextOptions kullanmalısınız unutmayın\<T > öğesinde DbContext tür genel parametre olarak geçen türü.

### <a name="configuring-ef-core"></a>EF Core yapılandırma

ASP.NET Core uygulamanızı Createservicereplicalisteners() yönteminizi EF Core genellikle yapılandıracaksınız. EF Core yapılandırmasını kolaylaştıran birçok yararlı genişletme yöntemleri destekleyen bir DbContextOptionsBuilder kullanır. CatalogContext yapılandırmasında tanımlı bir bağlantı dizesi ile bir SQL Server veritabanını kullanacak şekilde yapılandırmak için Createservicereplicalisteners() için aşağıdaki kodu ekleyin:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Bellek içi veritabanı kullanmak için:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

EF Core oluşturulan bir DbContext alt türü, yüklü ve Createservicereplicalisteners() içinde yapılandırılmış sonra EF Core kullanmaya hazır olursunuz. DbContext türünüz ihtiyaç duyduğu herhangi bir hizmeti örneğini istek ve yalnızca bir koleksiyonda değilmiş gibi LINQ kullanarak kalıcı varlıklarınızı ile çalışmaya başlayabilirsiniz. EF Core, verilerinizi almak ve depolamak için SQL sorgulara, LINQ ifade çevirme çalışır.

EF Core bir Günlükçü yapılandırma ve alt düzey ayarlandığında en az sağlama yürütüyordur sorguları gördüğünüz bilgileri, Şekil 8-1'de gösterildiği gibi.

![](./media/image8-1.png)

Şekil 8-1 konsola oturum EF Core sorguları

### <a name="fetching-and-storing-data"></a>Veri depolama ve alma

EF Core verileri almak için uygun bir özelliğe erişmek ve LINQ sonucu filtrelemek için kullanın. LINQ projeksiyonu, sonucu bir türden diğerine dönüştürme gerçekleştirmek için de kullanabilirsiniz. Aşağıdaki örnek adına göre sıralanmış, kendi etkin özellik tarafından filtrelendi ve bir Selectlistıtem türü öngörülen CatalogBrands alması:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Hemen bir sorgu yürütmek için ToListAsync çağrısı eklemek için yukarıdaki örnekte önemlidir. Aksi takdirde, deyim Iqueryable atar\<Selectlistıtem > brandItems için hangi yürütülmez numaralandırılana kadar. Artıları ve eksileri Iqueryable sonuçları döndüren yöntemler için vardır. Daha fazla değiştirilmesi, ancak operations EF Core çeviremez sorguya eklediyseniz yalnızca çalışma zamanında, oluşan hataları sonucunda ayrıca EF Core de oluşturmak sorgu sağlar. Herhangi bir filtre veri erişim gerçekleştirme yönteme geçirmek genellikle güvenlidir ve dönüş bir bellek içi koleksiyonu yeniden (örneğin, liste\<T >) sonucu.

EF Core Kalıcılık getirir varlıklardaki değişiklikleri izler. İzlenen bir varlığa değişiklikleri kaydetmek için yalnızca varlık getirmek için kullanılan aynı DbContext örneği olduğundan emin DbContext üzerinde SaveChanges yöntemi çağırın gerekir. Doğrudan ekleme ve kaldırma varlıkları çağrısıyla veritabanı komutlarını çalıştırmak için yeniden SaveChanges uygun olan DB özellik üzerinde gerçekleştirilir. Aşağıdaki örnek, ekleme, güncelleştirme, Kalıcılık varlıkları kaldırma gösterir.

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

EF Core destekler hem zaman uyumlu ve zaman uyumsuz yöntemler getirmeye ve kaydediliyor. Web sunucusu iş parçacığı için veri erişim işlemlerinin tamamlanması beklenirken engellenmediğinden emin web uygulamalarında async ve await deseni zaman uyumsuz yöntemlerle kullanmak için önerilir.

### <a name="fetching-related-data"></a>İlgili verileri getiriliyor

EF Core varlıkları aldığında, veritabanında bu varlıkla doğrudan depolanan tüm özellikler doldurur. İlgili varlık listeleri gibi Gezinti özellikleri değil doldurulur ve değerlerine ayarlanmış olabilir null. Bu, EF Core ihtiyaç duyduğundan daha fazla veri olduğu, hızlıca istekleri işlemesini ve verimli bir şekilde yanıtlarını döndürmek web uygulamaları için özellikle önemlidir getirip değil sağlar. Kullanarak bir varlık ile ilişkiler içerecek şekilde _istekli yükleme_, gösterildiği gibi sorguya dahil etme genişletme yöntemi kullanan özellik belirtin:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Birden çok ilişki içerebilir ve bu alt ilişkilerini de içerebilir ThenInclude kullanma. EF Core varlıkların sonuç kümesi almak için tek bir sorgu çalıştırır. Alternatif olarak geçirerek gezinme özelliklerinin gezinme özelliklerini dahil edebilirsiniz bir '.' -dizeye ayrılmış `.Include()` genişletme yöntemi, şu şekilde:

```csharp
    .Include(“Items.Products”)
```

Filtreleme mantığı Kapsüllenen yanı sıra bir belirtimi doldurmak için hangi özelliklerin dahil olmak üzere verilerin döndürülmesi için Şekil belirtebilirsiniz. EShopOnWeb örnek belirtimi içerisinde istekli yükleme bilgileri kapsüllemek gösteren çeşitli özellikleri içerir. Belirtimi burada bir sorgunun parçası olarak nasıl kullanıldığını görebilirsiniz:

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

İlgili verileri yükleme için başka bir seçenek kullanmaktır _açık yükleme_. Açık yükleme zaten alınmış bir varlığa, ek verileri sağlar. Bu veritabanı için ayrı bir istek gerektirdiğinden, veritabanı sayısını en aza indirmeniz gerekir web uygulamaları için önerilmez her istek için yapılan başvurular.

_Yavaş Yükleniyor_ uygulama tarafından başvurulduğu, ilgili verileri otomatik olarak yükleyen bir özelliktir. EF Core 2.1 sürümünde Gecikmeli yükleme için destek ekledi. Yavaş yükleniyor, varsayılan olarak etkin değildir ve yükleme gerektirir `Microsoft.EntityFrameworkCore.Proxies`. Her web isteğini içinde yapılan ek veritabanı sorguları kullanımını sonuçlanır beri gibi açık yükleme ile yavaş yükleniyor genellikle web uygulamaları için devre dışı bırakılması gerekir. Ne yazık ki, ne zaman gecikmesi küçüktür ve genellikle test etmek için kullanılan veri kümelerinin küçük geliştirme zamanında yavaş çoğunlukla yükleyerek sonucunda ek yükü gözden kaçan gider. Ancak, daha fazla kullanıcı, daha fazla veri ve daha fazla gecikme, bir üretim ortamında ek veritabanı istekler genellikle kötü performans yavaş yükleniyor ağır kullanan web uygulamaları için neden olabilir.

[Web uygulamalarında yavaş yükleniyor varlıkları kaçının](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a>Veri şifreleme

EF Core durumunu doğru şekilde yalıtılacak modelinizi sağlayan çeşitli özelliklerini destekler. Bir ortak etki alanı modelleri koleksiyon Gezinti özellikleri genel olarak erişilebilir liste türleri olarak ortaya sorunudur. Bu, büyük olasılıkla Nesne geçersiz bir durumda bırakarak koleksiyona ilgili önemli iş kuralları kullanmayan, bu koleksiyon türleri, içeriğini işlemek herhangi bir ortak çalışanı sağlar. İlişkili koleksiyonlar yalnızca okuma erişimi ve açıkça yolları, istemciler, bu örnekte olduğu gibi değiştirebilirsiniz tanımlama yöntemler sağlar, bu çözüme verilmiştir:

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

Bu varlık türünün ortak ortaya çıkarmıyor Not `List` veya `ICollection` özelliği, ancak bunun yerine sunan bir `IReadOnlyCollection` arka plandaki liste türü sarmalayan türü. Ne zaman destek alanı kullanmak için Entity Framework Core belirtebilir bu düzeni kullanmak şu şekilde:

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

Etki alanı modeliniz geliştirmek başka bir kimlik eksik olan ve yalnızca özelliklerine göre ayırt edilen türleri için değer nesneleri kullanarak yoludur. Bu türler varlıklarınızı özelliklerini kullanarak nereye ait ve aynı kavram kullanan birden çok varlık arasında yinelenen mantık kaçınabilirsiniz değer nesnesi için mantıksal belirli korunmasına yardımcı olabilirsiniz. Entity Framework Core içinde bunların sahibi olan varlık aynı tabloda değer nesnelerini türüne ait bir varlık olarak yapılandırarak kalıcı yapılabilir şu şekilde:

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

Bu örnekte, `ShipToAddress` özelliği türüdür `Address`. `Address` olduğu gibi çeşitli özelliklere sahip bir değer nesnesini `Street` ve `City`. EF Core eşler `Order` kendi tek sütunlu tablo nesnesine `Address` özelliği sütun adını her özelliğin adı. Bu örnekte, `Order` tabloda sütunları gibi dahil `ShipToAddress_Street` ve `ShipToAddress_City`.

[EF Core 2.2 sahip olunan varlık koleksiyonları için destek sunuyor](https://docs.microsoft.com/ef/core/what-is-new/ef-core-2.2#collections-of-owned-entities)

### <a name="resilient-connections"></a>Dayanıklı bağlantıları

SQL veritabanları gibi dış kaynaklara bazen kullanılamıyor olabilir. Geçici olarak kullanım dışı kalması durumunda, uygulamalar, bir özel durum oluşturma önlemek için yeniden deneme mantığı kullanabilirsiniz. Bu teknik, genellikle olarak adlandırılır _bağlantı dayanıklılığı_. Uygulayabileceğiniz, [üstel geri alma ile kendi yeniden deneme](https://docs.microsoft.com/azure/architecture/patterns/retry) maksimum yeniden deneme sayısına ulaşılana kadar bir üssel olarak artan bekleme süresi ile yeniden denemeden tarafından tekniği. Bu teknik bulut kaynaklarını aralıklı olarak bazı istekler hatasıyla sonuçlanan süresinin kısa süreler için kullanılamıyor olabilir, olgu kapsar.

Azure SQL DB için Entity Framework Core zaten iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığı sağlar. Ancak, EF Core bağlantıları dayanıklı olmasını istiyorsanız, her bir DbContext bağlantı için Entity Framework yürütme stratejisi etkinleştirmeniz gerekir.

Örneğin, aşağıdaki kodu EF Core bağlantı düzeyinde bağlantı başarısız olursa şartıyla dayanıklı SQL bağlantısı sağlar.

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Yürütme stratejileri ve BeginTransaction ve birden çok DbContexts kullanarak açık işlemleri

EF Core bağlantıları yeniden deneme etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem yeniden denenebilir kendi işlem olur. Geçici bir hata oluşursa, her sorgu ve SaveChanges yapılan her çağrı bir birim olarak yeniden denenecek.

Ancak, kodunuzu BeginTransaction'ı kullanarak bir işlem başlatırsa, bir birim olarak kabul edilmesi için gereken işlemleri kendi grubu tanımlıyorsanız; işlem içinde her şeyi bir hata oluşursa geri alınması gerekir. EF yürütme stratejisi (yeniden deneme ilkesi) kullanılırken, işlem yürütme girişimi ve birden çok DbContexts gelen birkaç SaveChanges bunu aşağıdaki gibi bir özel durum görürsünüz.

System.InvalidOperationException: 'SqlServerRetryingExecutionStrategy' yapılandırılmış yürütme stratejisi, kullanıcı tarafından başlatılan işlemleri desteklemiyor. İşlem yeniden denenebilir bir birim olarak tüm işlemleri yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisi kullanın.

El ile yürütülmesi gereken her şeyi temsil eden bir temsilci ile EF yürütme stratejisi çağırmak için kullanılan çözümüdür. Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır. Aşağıdaki kod, bu yaklaşımı uygulamak gösterilmektedir:

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

İlk DbContext olduğu \_catalogContext ve ikinci DbContext içinde olduğunu \_integrationEventLogService nesne. Son olarak, eylem olacaktır işleme, birden çok DbContexts ve bir EF yürütme stratejisi kullanarak gerçekleştirilir.

> ### <a name="references--entity-framework-core"></a>Başvuruları – Entity Framework Core
>
> - **EF Core belgeleri**  
>   <https://docs.microsoft.com/ef/>
> - **EF Core: İlgili verileri**  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **ASP.NET uygulamalarında yavaş yükleniyor varlıkları kaçının**  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core veya mikro ORM?

EF Core Kalıcılık yönetmek için harika bir seçenektir ve çoğunlukla uygulama geliştiricilerin veritabanı ayrıntılarını kapsayan tek bir seçim değil. Başka bir popüler açık kaynak alternatiftir [Dapper](https://github.com/StackExchange/Dapper), sözde micro-ORM. Bir mikro ORM basit, tam özellikli aracı veri yapılarını nesneleri eşleştirmek için daha az olur. Dapper söz konusu olduğunda, tam olarak temel alınan Kapsüllenen sorgular yerine hedefleri performans üzerinde odaklanmanıza tasarımı almak ve verileri güncelleştirmek için kullanır. SQL geliştiriciden soyutlamak değil çünkü Dapper "donanıma yakın" ve tam yazma geliştiricilerinin erişim işlemi için verilen bir veri kullanmak istedikleri sorgular.

EF Core Dapper ayrı, ancak Ayrıca, performansa ekleme sağladığı iki önemli özellikleri de vardır. İlk LINQ SQL ifadelere çevrilmesi ' dir. Bu çevirileri önbelleğe alınır, ancak buna rağmen ek yükü ilk kez gerçekleştirmek içinde var. Böylece (verimli update ifadeleriyle oluşturulabilir) varlıklarda değişiklik izleme saniyedir. Bu davranış için özel sorgular AsNotTracking uzantısını kullanarak kapatılabilir. EF Core, genellikle çok verimli ve her durumda edilebilir bir performans açısından SQL sorguları da oluşturur, ancak kesin bir sorgu yürütülecek bir denetime ince varsa, özel SQL'de geçirebilirsiniz (veya bir saklı yordamı yürütme) EF kullanma , Çok çekirdek. Bu durumda, EF Core Dapper hala çok daha iyi ancak çok az. Bazı performans verileri her olabilir 2016 MSDN makalesi Julie Lerman sunar [Dapper, Entity Framework ve karma uygulamalar](https://msdn.microsoft.com/magazine/mt703432.aspx). Veri erişim yöntemlerine çeşitli ek performans Kıyaslama veri çubuğunda bulunabilir [Dapper site](https://github.com/StackExchange/Dapper).

Dapper sözdizimi EF Core'a nasıl değiştiğini görmek için öğelerin listesini almak için aynı yöntemi bu iki sürümünü göz önünde bulundurun:

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

Dapper ile daha karmaşık nesne grafikler oluşturmak ihtiyacınız varsa, ilişkili sorgu kendiniz (EF Core gibi bir içerme eklemek yerine) yazmanız gerekir. Bu sözdizimi, birden fazla eşleştirilmiş nesne için ayrı satırlara eşlemenize olanak tanıyan çoklu eşleme denilen bir özelliği de dahil olmak üzere çeşitli aracılığıyla desteklenir. Örneğin, bir sınıf Post özelliğiyle sahibi kullanıcı türündeki göz önünde bulundurulduğunda, aşağıdaki SQL tüm gerekli verileri döndürür:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Döndürülen her satır, hem kullanıcı hem de Post veriler içerir. Kullanıcı verileri kendi Owner özelliği aracılığıyla gönderme verisi eklenmesi gereken aşağıdaki işlevi kullanılır:

```csharp
(post, user) => { post.Owner = user; return post; }
```

İlişkili kullanıcı verileriyle doldurulur bunların sahibi özelliğiyle gönderileri koleksiyonunu döndürmek için tam kod listesi şu şekilde olur:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Daha az kapsülleme sağladığından, geliştiriciler, verilerin depolanma şeklini hakkında daha fazla bilmeniz Dapper gerektirir nasıl verimli bir şekilde sorgulayın ve bu getirmek için daha fazla kod yazın. Etkilenir her sorgu modeli, yalnızca yeni bir geçiş (başka bir EF Core özelliği) oluşturma ve/veya tek bir yerde bir DbContext eşleme bilgilerini güncelleştirmek yerine değiştiğinde güncelleştirilmesi gerekir. Bu sorgular, derleme zamanı garanti sahip, bu nedenle, çalışma zamanında değişikliklere yanıt olarak model veya veritabanı, hataları hızlı bir şekilde algılaması daha zor hale bozabilir. Bu bileşim lisanslarınıza Dapper son derece hızlı performans sağlar.

EF Core, çoğu uygulama ve neredeyse tüm uygulamaların belirli kısımlarını çoğu için kabul edilebilir performans sunar. Bu nedenle, geliştirici üretkenliği faydalarını, performansa daha ağır basar olasılığı düşüktür. Önbelleğe alınan bir avantaj sorgular, gerçek sorgu yalnızca yürütülebilecek küçük bir yüzdesi görece küçük yapmadan zaman, sorgu performansı farklılıkları tartışmalı.

## <a name="sql-or-nosql"></a>SQL veya NoSQL

Geleneksel olarak, SQL Server gibi ilişkisel veritabanları kalıcı veri depolamayı Market direncin hakim olduğu, ancak bunlar yalnızca çözüm kullanılabilir değil. Gibi NoSQL veritabanları [MongoDB](https://www.mongodb.com/what-is-mongodb) nesneleri depolamak için farklı bir yaklaşım sunar. Tabloları ve satırları için nesne eşleme yerine başka bir tüm nesne grafiğinin seri hale getirmek ve sonucu depolamak için bir seçenektir. Bu yaklaşımın avantajları, Basitlik ve performans en azından başlangıçta markalarıdır. Nesne ilişkisi olan birçok tabloları içinde ayırmak daha bir anahtarla tek serileştirilmiş nesne depolamak kesinlikle basittir ve veritabanından güncelleştirme ve satırları, nesne, son başlatıldığından beri değişmiş olabilir. Benzer şekilde, yakalama ve anahtar tabanlı deposundan tek bir nesne seri durumdan çıkarılırken genellikle çok daha hızlı ve daha karmaşık birleştirmelerden veya birden çok veritabanı sorguları tam olarak aynı nesneden ilişkisel bir veritabanı oluşturmak için gereklidir. Kilitleri veya işlemler ya da sabit bir şema eksikliği NoSQL veritabanları da çok iletilmek için çok büyük veri kümeleri destekleyen birçok makineler arasında ölçeklendirme yapar.

Öte yandan, (bunlar genellikle olarak adlandırılan) NoSQL veritabanları sakıncaları vardır. İlişkisel veritabanları normalleştirme tutarlılığın ve verilerin yinelenmesini önlemek için kullanın. Bu, toplam veritabanı boyutunu azaltır ve paylaşılan veri güncelleştirmeleri hemen veritabanı kullanılabilir olmasını sağlar. Bir ülke/bölge adı değiştirildiyse, adresi kayıtlarını Update'ten kendilerini gerek avantaj elde edecektir, ilişkisel bir veritabanında bir adres tablosu kimliği, bir ülke tablo başvurabilir. Ancak, bir NoSQL veritabanı adresi ve onun ilişkili ülke birçok depolanan nesne bir parçası olarak seri hale. Bir ülke/bölge adı için bir güncelleştirme gibi tüm nesnelerin yerine tek bir satır güncelleştirilmesi gerekir. İlişkisel veritabanları, yabancı anahtarlar gibi kuralları zorunlu tutarak ilişkisel bütünlüğü de sağlayabilirsiniz. NoSQL veritabanları, bu tür kısıtlamalar verilerini genellikle sunmaz.

Başka bir karmaşıklık NoSQL veritabanları uğraşmanız gerekir, Sürüm ' dir. Bir nesnenin özelliklerini değiştirdiğinizde depolanırdı geçmiş sürümlerinden seri durumdan mümkün olmayabilir. Bu nedenle, bir nesne seri hale getirilmiş (önceki) sürümüne sahip tüm var olan nesneler, yeni şemaya uyacak şekilde güncelleştirilmesi gerekir. Kavramsal olarak ilişkisel bir veritabanındaki farklı değil, bazen şema değişiklikleri güncelleştirme betikleri gerektirir veya güncelleştirmeleri eşleme. Ancak değiştirilmelidir girdi sayısı genellikle büyük olup olmadığı için daha fazla çoğaltma verilerinin NoSQL yaklaşım daha.

Birden çok sürümünü nesneleri depolamak için NoSQL veritabanlarında mümkündür, sabit bir şey şema ilişkisel veritabanları genellikle desteklemez. Ancak, bu durumda uygulama kodunuz nesneleri, karmaşıklık ekleme önceki sürümleri varlığını hesabı gerekir.

NoSQL veritabanları genellikle mecbur kılmaz [ACID](https://en.wikipedia.org/wiki/ACID), sahip oldukları hem performans ve ölçeklenebilirlik avantajlarını ilişkisel veritabanları anlamına gelir. Bunlar, son derece büyük veri kümelerini ve depolama normalleştirilmiş tablo yapılardaki için çok uygun olmayan nesneler için uygundur. Neden tek bir uygulama hem de ilişkisel yararlanamaz ve NoSQL veritabanları, en iyi olduğu her kullanarak uygun bir neden yoktur.

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB, şemadan bağımsız veriler bulut tabanlı depolama sunan tam olarak yönetilen bir NoSQL veritabanı hizmetidir. DocumentDB hızlı ve tahmin edilebilir performans, yüksek kullanılabilirlik, esnek ölçeklendirme ve küresel dağıtım için oluşturulmuştur. Geliştiriciler, bir NoSQL veritabanı olan rağmen JSON verileri üzerinde zengin ve tanıdık SQL sorgu işlevleri kullanabilir. DocumentDB tüm kaynaklar JSON belgeleri olarak depolanır. Olarak yönetilen kaynakları _öğeleri_, meta veriler içeren belge ve _akışları_, öğe koleksiyonunu olduğu. Şekil 8-2 farklı DocumentDB kaynakları arasındaki ilişkiyi gösterir.

![Bir NoSQL JSON veritabanı olan documentdb'de kaynaklar arasındaki hiyerarşi ilişkisi](./media/image8-2.png)

**Şekil 8-2.** DocumentDB kaynak kuruluş.

DocumentDB sorgu dili, JSON belgelerini sorgulamak için basit ancak güçlü bir arabirimdir. Dil, ANSI SQL dil bilgisi kümesini destekler ve JavaScript nesnesi, dizileri, nesne oluşturması ve işlev çağrısını derin tümleştirme ekler.

**Başvuruları – DocumentDB**

- DocumentDB giriş  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Diğer Kalıcılık seçenekleri

Ek olarak ilişkisel ve NoSQL depolama seçenekleri, ASP.NET Core uygulamaları, bulut tabanlı, ölçeklenebilir bir şekilde çeşitli veri biçimleri ve dosyaları depolamak için Azure depolama kullanabilirsiniz. Azure depolama yüksek düzeyde ölçeklenebilir olduğundan küçük miktarda veri ve uygulamanız gerekiyorsa, yüzlerce ya da terabayt depolama kadar ölçek depolama kullanıma başlayabilirsiniz. Azure depolama, dört veri türlerini destekler:

- BLOB Depolama, yapılandırılmamış metin veya ikili depolama, aynı zamanda nesne depolama olarak adlandırılır.

- Tablo depolama için yapılandırılmış veri kümeleri, satır anahtarı erişilebilir.

- Kuyruk depolama, kuyruk tabanlı güvenilir Mesajlaşma için.

- Azure sanal makineler ve şirket içi uygulamalar arasında paylaşılan dosya erişimi için dosya depolama.

**Başvuru-Azure depolama**

- Azure depolama giriş  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Önbelleğe Alma

Web uygulamalarında, her web isteğini en kısa süre içinde tamamlanmalıdır. Bunu yapmanın bir yolu, sunucu, isteğini tamamlamak için yapmalısınız dış çağrı sayısı çalıştırmanız gerekir. Önbelleğe alma, sunucuda verilerin bir kopyasını depolayarak içerir (veya başka bir veri yani daha kolayca veri kaynağını sorguladı depolamak). Web uygulamaları ve özellikle SPA olmayan geleneksel web uygulamaları, tüm kullanıcı arabirimi her istek ile oluşturmanız gerekir. Bu, sık sorguların çoğu, aynı veritabanı sürekli bir kullanıcı isteğinden sonraki yapılmasını gerektirir. Çoğu durumda, sürekli, veritabanından istemek için çok az neden olduğundan bu veri nadiren de olsa değiştirir. ASP.NET Core tüm sayfaları ve verileri önbelleğe alma, önbelleğe alma işlemi için yanıt önbelleğe destekleyen daha ayrıntılı önbelleğe alma davranışını destekler.

Önbelleği uygularken dikkate ayrımı içinde tutmak önemlidir. Önbelleğe alma mantığını, veri erişim mantığı ya da kullanıcı arabiriminiz uygulamaktan kaçının. Bunun yerine, kendi sınıflarda önbelleğe alma kapsüllemek ve davranışını yönetmek için yapılandırma kullanın. Tek sorumluluk ilkeleri ve açık/kapalı izler ve büyüdükçe, uygulamanızda önbelleğe alma kullanımını yönetmek kolay hale getirir.

### <a name="aspnet-core-response-caching"></a>ASP.NET Core yanıt önbelleğe alma

ASP.NET Core yanıt önbelleğe alma iki düzeylerini destekler. İlk düzeyi, sunucu üzerindeki herhangi bir şey önbelleğe almaz, ancak istemciler ve proxy sunucular önbellek yanıtları isteyin HTTP üstbilgileri ekler. Bu, tek tek denetleyicileri veya Eylemler ResponseCache öznitelik ekleyerek uygulanır:

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

Önceki örnekte, sonuç 60 saniye için önbelleğe almak için istemcileri söyleyen yanıta eklenen aşağıdaki üst bilgisindeki neden olur.

Cache-Control: public,max-age=60

Sunucu tarafı uygulamayı bellek içi önbelleğe alma ekleme için başvuru Microsoft.AspNetCore.ResponseCaching NuGet paketini ve ardından yanıt önbelleğe alma ara yazılımı eklemeniz gerekir. Bu ara yazılımın Createservicereplicalisteners() hem de Yapılandırma başlangıç yapılandırılır:

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

Yanıtları önbelleğe alma ara yazılımı otomatik olarak özelleştirebileceğiniz koşul kümesine göre yanıtları önbelleğe alır. Varsayılan olarak, GET veya HEAD yöntemleri istenen yalnızca 200 (Tamam) yanıtlarını önbelleğe alınır. Ayrıca, istekleri bir Cache-Control ile bir yanıt olmalıdır: ortak üstbilgi ve yetkilendirme veya Set-Cookie üst bilgiler dahil edemezsiniz. Bkz: bir [yanıt önbelleğe alma ara yazılımı tarafından kullanılan önbellek koşullar tam listesi](/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Veri önbelleğe alma

Yerine (veya ek olarak) tam web yanıtları önbelleğe alma, tek tek veri sorguların sonuçlarını önbelleğe alabilir. Bu, bellek web sunucusunda önbelleğe alma kullanabilir, veya bu kullanın [dağıtılmış önbellek](/aspnet/core/performance/caching/distributed). Bu bölümde, bellek içinde önbelleğe alma ekleme gösterilecektir.

Bellek için destek eklendi (veya dağıtılmış) içinde Createservicereplicalisteners() önbelleğe alma:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Microsoft.Extensions.Caching.Memory NuGet paketini de eklediğinizden emin olun.

Hizmet ekledikten sonra önbelleğe erişmek ihtiyaç duyduğunuz her yerde bağımlılık ekleme IMemoryCache isteyin. Bu örnekte, erişimi denetleyen (ya da davranışı ekler) ICatalogService alternatif uygulaması sağlayarak CachedCatalogService Proxy (veya Dekoratör) tasarım deseni kullanan temel CatalogService uygulaması.

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

Hizmet önbelleğe alınmış sürümünü kullanabilirsiniz, ancak yine de oluşturucusunda gereken CatalogService örneğini almak için hizmeti izin uygulamasını yapılandırmak için içinde Createservicereplicalisteners() aşağıdakileri ekleyin:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Bu yerinde katalog verileri getirmek için veritabanı çağrıları yalnızca dakika başına bir kez yerine her istekte yapılır. Siteye trafiğe bağlı olarak, bunun veritabanına ve şu anda bu hizmet tarafından sunulan sorguları üç bağlı olduğu giriş sayfası için ortalama sayfa yükleme süresi yapılan sorguları sayısı çok önemli bir etkisi olabilir.

Önbelleğe alma uygulandığında, ortaya sorunu _getirse veri_ – diğer bir deyişle, kaynak ancak eski bir sürümü değişmiş verileri önbellekte kalır. Bu sorunu gidermek için basit bir yol için meşgul bir uygulama olduğundan verileri önbelleğe uzunluğu genişletme sınırlı ek faydası küçük önbellek süreleri kullanmaktır. Örneğin, bir tek veritabanı sorgusu yapan bir sayfa göz önünde bulundurun ve saniye başına 10 kez istendi. Bu sayfa bir dakika boyunca önbelleğe alınmışsa dakika başına 1, % 99,8 azaltma 600 ' açılan yapılan veritabanı sorgularının sayısı sonuçlanır. Bunun yerine, önbelleğe alma süresi bir saat yapıldı, genel azaltma %99.997 olacaktır, ancak artık eski veri olasılığını ve olası yaşını hem de önemli ölçüde artırıldı.

İçerdikleri veriler güncelleştirildiğinde önbellek girişlerini proaktif bir şekilde kaldırmak başka bir yaklaşımdır. Tek bir giriş anahtarıyla biliniyorsa kaldırılabilir:

```csharp
_cache.Remove(cacheKey);
```

Uygulamanızın, önbelleğe alan güncelleştirme işlevi sunarsa, kodunuzdaki güncelleştirmeler yapar karşılık gelen önbellek girişlerinin kaldırabilirsiniz. Bazen belirli bir veri kümesine bağlı olan birçok farklı girdi olabilir. Bu durumda, bir CancellationChangeToken kullanarak önbellek girişlerinin arasındaki bağımlılıkları oluşturmak yararlı olabilir. Bir CancellationChangeToken ile belirteci iptal ederek birden fazla önbellek girişi tek seferde dolabilir.

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

Önbelleğe alma işlemi sürekli olarak aynı değerleri veritabanından isteği gönderen web sayfaları performansını önemli ölçüde artırabilir. Geliştirme için ihtiyaç gördüğünüz önbelleğe alma uygulanmadan önce veri erişimi ve sayfa performansı ölçmek ve önbelleğe alma yalnızca geçerli emin olun. Önbelleğe alma, web sunucu bellek kaynaklarını tüketir ve bu tekniği kullanarak erken iyileştirme önemlidir uygulama karmaşıklığını artırır.

>[!div class="step-by-step"]
>[Önceki](develop-asp-net-core-mvc-apps.md)
>[İleri](test-asp-net-core-mvc-apps.md)
