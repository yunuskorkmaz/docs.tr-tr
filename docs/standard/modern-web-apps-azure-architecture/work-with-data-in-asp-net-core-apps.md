---
title: ASP.NET Core uygulamalardaki verileri ile çalışma
description: ASP.NET Core ve Azure ile modern Web uygulamaları mimari | ASP verilerle çalışma
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: c9f1350f57ed649b9bf53968c19ab652b3c74384
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106181"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>ASP.NET Core uygulamalardaki verileri ile çalışma

> "Veri değerli bir şeydir ve sistemler kendilerini daha uzun sürer."

Tim Berners-Lee

## <a name="summary"></a>Özet

Veri erişimi, neredeyse her yazılım uygulamanın önemli bir parçasıdır. ASP.NET Core veri erişim seçenekleri, Entity Framework Çekirdek (ve de Entity Framework 6) dahil olmak üzere çeşitli destekler ve tüm .NET veri erişim framework ile çalışabilirsiniz. Hangisinin kullanılacağını framework verilere seçim uygulamanın gereksinimlerine bağlıdır. Bu seçenek ApplicationCore ve kullanıcı Arabirimi projelerden özetleyen ve yalıtma altyapısında, uygulama ayrıntılarını geniş eşleşmiş, sınanabilir yazılım üretmek için yardımcı olur.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Çekirdek (için ilişkisel veritabanları)

İlişkisel verilerle çalışmak için gereken yeni bir ASP.NET Core uygulama yazıyorsanız, Entity Framework Çekirdek (EF çekirdek), verilere erişmek, uygulamanız için önerilen yöntem olduğu. EF çekirdeği .NET geliştiricilerinin nesneleri için ve bir veri kaynağı kalıcı hale getirmek bir nesne ilişkisel Eşleyici (O/RM) olur. Bu, veri erişim geliştiriciler genellikle yazmak zorunda kalırsınız kodu çoğunu gereksinimini ortadan kaldırır. ASP.NET Core gibi destek modüler platformlar arası uygulamalar kadar sıfırdan EF çekirdek yazılmıştır. Bir NuGet paketi olarak uygulamanıza ekleyin, başlangıç yapılandırmak ve ihtiyacınız olduğunda bağımlılık ekleme isteği.

SQL Server veritabanı ile EF çekirdek kullanmak için aşağıdaki dotnet CLI komutu çalıştırın:

DotNet paket Microsoft.EntityFrameworkCore.SqlServer Ekle

Test etmek için bir Inmemory veri kaynağı için destek eklemek için:

DotNet paket Microsoft.EntityFrameworkCore.InMemory Ekle

### <a name="the-dbcontext"></a>DbContext

EF çekirdek ile çalışmak için DbContext öğesinin bir alt kümesi gerekir. Bu sınıf, uygulama ile çalışıp çalışmayacağını varlıkların koleksiyonları özellikler içerir. EShopOnWeb örnek CatalogContext öğeleri, markalar ve türleri için koleksiyonlarıyla içerir:

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

DbContext DbContextOptions kabul eden bir oluşturucuya sahip olması ve bu bağımsız değişken temel DbContext oluşturucusunun geçmesi gerekir. Yalnızca bir DbContext uygulamanızda varsa, DbContextOptions örneği geçirebilirsiniz ancak varsa, birden fazla genel DbContextOptions kullanmalısınız unutmayın<T> DbContext tür genel parametre olarak geçirme türü.

### <a name="configuring-ef-core"></a>EF çekirdek yapılandırma

ASP.NET çekirdeği uygulamanızda ConfigureServices yönteminizi EF çekirdek genellikle yapılandıracaksınız. EF Çekirdek yapılandırmasını kolaylaştırmak için çeşitli yararlı genişletme yöntemleri destekleyen bir DbContextOptionsBuilder kullanır. CatalogContext yapılandırmasında tanımlı bir bağlantı dizesini bir SQL Server veritabanını kullanmak üzere yapılandırmak için ConfigureServices için aşağıdaki kodu ekleyin:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Bellek içi veritabanı kullanmak için:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

DbContext alt türü oluşturulan EF çekirdek yüklenip ConfigureServices içinde yapılandırılmış sonra EF çekirdek kullanıma hazır. Gerekli herhangi bir hizmeti, DbContext türünün bir örneği isteyin ve yalnızca bir koleksiyondaki değilmiş gibi LINQ kullanarak, kalıcı varlıklarla çalışmaya başlayabilirsiniz. EF çekirdek, depolamak ve verilerinizi almak için SQL sorguları LINQ ifadelere çevirme çalışır.

Günlükçü yapılandırma ve alt düzey ayarlanmış en az sağlamayı EF çekirdek yürütme sorguları görebilirsiniz Şekil 8-1'de gösterildiği gibi bilgiler.

![](./media/image8-1.png)

Şekil 8-1 günlüğü EF çekirdek sorguları konsoluna

### <a name="fetching-and-storing-data"></a>Getirme ve veri depolama

EF çekirdek veri almak için uygun özelliğine erişmek ve LINQ sonucu filtre uygulamak için kullanın. LINQ, yansıtma, bir türden diğerine sonucu dönüştürme gerçekleştirmek için de kullanabilirsiniz. Aşağıdaki örnek adına göre sıralanmış, bunların etkin özelliği tarafından filtre ve Selectlistıtem türü öngörülen CatalogBrands almak:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Sorgu hemen yürütmek için ToListAsync çağrısı eklemek için yukarıdaki örnekte önemlidir. Aksi takdirde, deyim Iqueryable atar<SelectListItem> brandItems için hangi çalıştırılmayacak numaralandırılan kadar. Artıları ve eksileri yöntemleri Iqueryable sonuçları döndürmek için vardır. Daha fazla değiştirilmesi, ancak EF çekirdek çeviremez sorgu işlemleri eklediyseniz yalnızca çalışma zamanında oluşan hataları sonucunda da yapabilirsiniz EF çekirdek de oluşturmak sorgusu tanır. Veri erişim gerçekleştirme yönteme herhangi bir filtre geçirmek genellikle güvenlidir ve return geri bir bellek içi koleksiyonu (örneğin, liste<T>) sonucu olarak.

EF çekirdek Kalıcılık getirir varlıklar üzerinde değişiklikleri izler. İzlenen bir varlığa değişiklikleri kaydetmek için yalnızca varlık getirmek için kullanılan aynı DbContext örnek olduğundan emin DbContext üzerinde SaveChanges yöntemini çağırın gerekir. Ekleme ve kaldırma varlıklar doğrudan veritabanı komutlarını çalıştırmak için yeniden çağrısıyla SaveChanges uygun DbSet özelliği açıktır. Aşağıdaki örnek, ekleme, güncelleştirme ve varlıklar kalıcı kaldırma gösterir.

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

EF çekirdek destekler zaman uyumlu ve zaman uyumsuz yöntemleri getirme ve kaydetme. Böylece Web sunucu iş parçacığı için veri erişim işlemleri tamamlamak için beklenirken engellenmez web uygulamalarında bu zaman uyumsuz ve bekleme düzeni zaman uyumsuz yöntemlerle kullanılması önerilir.

### <a name="fetching-related-data"></a>İlgili veri getirme

EF çekirdek varlıklar aldığında, veritabanındaki varlık ile doğrudan depolanan özelliklerin tümünü doldurur. İlgili varlık listeleri gibi Gezinti özellikleri değil doldurulur ve değerlerine ayarlayın olabilir null. Bu EF çekirdek gerekli olandan daha fazla veri olduğu hızla istekleri işleyen gerekir ve verimli bir şekilde yanıtlar dönmek web uygulamaları için özellikle önemlidir: getiriliyor değil sağlar. Kullanarak bir varlık ile ilişkileri dahil etmek için *istekli yükleme*, gösterildiği gibi sorguya dayalı INCLUDE genişletme yöntemi kullanarak özelliğini belirtin:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Birden çok ilişki içerebilir ve bu da alt ilişkileri içerebilir ThenInclude kullanarak. EF çekirdek varlıklar sonuç kümesini almak için tek bir sorgu yürütülür.

İlgili verileri yüklemek için başka bir seçenek kullanmaktır *açık yükleme*. Açık yükleme, ek veri zaten alınan bir varlık kümesine yüklemenizi sağlar. Bu veritabanı için ayrı bir istek gerektirdiğinden, veritabanı sayısını en aza indirmeniz gerekir web uygulamaları için önerilmez gidiş dönüş istekte.

*Yavaş Yükleniyor* özelliğini uygulama tarafından başvurulduğu, ilgili verileri otomatik olarak yükler. EF çekirdek tarafından şu anda desteklenmez, ancak olarak açık yükleme ile bu genellikle web uygulamaları için devre dışı bırakılması gerekir.

### <a name="resilient-connections"></a>Esnek bağlantıları

SQL veritabanları gibi dış kaynaklara bazen kullanılamıyor olabilir. Geçici olarak kullanım dışı kalması durumunda, uygulamaların bir özel durum yükseltme önlemek için yeniden deneme mantığı kullanın. Bu yöntem, yaygın olarak adlandırılır *bağlantı dayanıklılığı*. Uygulayabileceğiniz, [üstel geri alma kendi Denemeyle](https://docs.microsoft.com/azure/architecture/patterns/retry) en fazla yeniden deneme sayısı üst sınırına kadar rety üstel olarak artan bir bekleme süresi ile çalışırken tarafından tekniği. Bu teknik bulut kaynakları aralıklı kısa sürelerle bazı isteklerin karşılanamamasına, için kullanılamıyor olabilir, olgu çalışır.

Azure SQL DB için Entity Framework Çekirdek zaten iç veritabanı bağlantısı dayanıklılık ve yeniden deneme mantığı sağlar. Ancak istediğinizde dayanıklı EF çekirdek bağlantınız Entity Framework yürütme stratejisi her DbContext bağlantı etkinleştirmeniz gerekir.

Örneği için aşağıdaki kodu EF çekirdek bağlantı düzeyinde bağlantı başarısız olursa yeniden denenir dayanıklı SQL bağlantıları sağlar.

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

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Yürütme stratejilerini ve BeginTransaction ve birden çok DbContexts kullanarak açık işlemleri 
  
  EF çekirdek bağlantıları yeniden deneme etkinleştirildiğinde, EF çekirdek kullanarak gerçekleştirdiğiniz her işlem yeniden denenebilir çalışması haline gelir. Geçici bir hata oluşursa, her sorgu ve her çağrı SaveChanges bir birim olarak yeniden denenecek.
  
  Ancak, kodunuzu BeginTransaction kullanarak bir işlem başlatır, bir birim olarak kabul edilmesi için gereken işlemleri kendi grubunun tanımlıyorsanız — işlem içinde her şeyi sahip olması alındı geri bir hata oluşursa. EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu işlemi yürütme girişimi ve birden çok DbContexts gelen birkaç SaveChanges bunu aşağıdaki gibi bir özel durum görürsünüz.

System.InvalidOperationException: 'SqlServerRetryingExecutionStrategy' yapılandırılmış yürütme stratejisi kullanıcı tarafından başlatılan işlemleri desteklemez. İşlem yeniden denenebilir bir birim olarak tüm işlemleri yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisi kullanın.

Çözüm, yürütülecek gereken her şeyi temsil eden bir temsilci ile EF yürütme stratejisi el ile çağırmaktır. Geçici bir hata oluşursa, yürütme stratejisi temsilci yeniden çağırır. Aşağıdaki kod, bu yaklaşımı uygulamak gösterilmektedir:

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

İlk DbContext olan \_catalogContext ve ikinci DbContext içinde olduğunu \_integrationEventLogService nesnesi. Son olarak, eylem olacaktır yürütme birden çok DbContexts ve EF yürütme stratejisi kullanılarak gerçekleştirilir.

> ### <a name="references--entity-framework-core"></a>Başvuruları – Entity Framework Çekirdek
> - **EF Core belgeleri**  
> <https://docs.microsoft.com/ef/>
> - **EF Çekirdek: İlgili veriler**  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - **ASP.NET uygulamalarında yavaş yükleniyor varlıklar kaçının**  
> <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF çekirdek veya mikro ORM?

EF çekirdek Kalıcılık yönetmek için harika bir seçenektir ve çoğunlukla uygulama geliştiricileri veritabanı ayrıntılarının Kapsüller olsa da, tek seçim değil. Başka bir popüler açık kaynak alternatif [Dapper](https://github.com/StackExchange/Dapper), bir sözde mikro ORM. Mikro ORM daha az veri yapılarını nesneleri eşleme için aracı tam özellikli bir basit ' dir. Dapper söz konusu olduğunda, arka plandaki tam olarak Kapsüllenen sorgular yerine hedefleri performans üzerinde odaklanmak tasarımı almak ve verileri güncelleştirmek için kullanır. Bu SQL geliştiriciden soyut değil çünkü Dapper "metal" daha yakındır ve tam yazma geliştiricilerinin erişim işlemi için verilen veri kullanmak istedikleri sorgular.

EF çekirdek Dapper ayrı ancak kendi performansını yükü de eklemeniz sağlayan iki önemli özelliklere sahiptir. İlk LINQ SQL ifadelere çevrilmesi ' dir. Bu çevirileri önbelleğe alınır, ancak buna rağmen yok yükü ilk kez gerçekleştirmede. (Verimli güncelleştirme deyimleri oluşturulabilir böylece) üzerinde varlıklar değişiklik izleme saniyedir. Bu davranış özel sorgular için AsNotTracking uzantısını kullanarak kapatılabilir. EF çekirdek genellikle çok verimli ve herhangi bir durumda edilebilir performans açısından SQL sorguları da oluşturur, ancak yürütülecek kesin sorgu denetime ince varsa, özel SQL'de geçirebilirsiniz (veya bir saklı yordamı yürütme) EF kullanma , Çok çekirdek. Bu durumda, Dapper hala EF çekirdek sürümlerden üstünlüğü ancak yalnızca biraz. Bazı performans verilerini her olabilir 2016 MSDN makalesine Julie Lerman sunar [Dapper, Entity Framework ve karma uygulamalar](https://msdn.microsoft.com/magazine/mt703432.aspx). Ek performans Kıyaslama verileri çeşitli veri erişim yöntemler için üzerinde bulunabilir [Dapper site](https://github.com/StackExchange/Dapper).

Dapper sözdizimi EF çekirdek nasıl değişeceğini görmek için bu iki sürümü öğelerinin bir listesini almak için aynı yöntemi göz önünde bulundurun:

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

Dapper daha karmaşık nesne grafiklerle yapı gerekiyorsa, ilişkili sorgular (EF çekirdek gibi bir dahil etme ekleme aksine) kendiniz yazmanız gerekir. Bu, sözdizimi, tek tek satır birden çok eşlenen nesnelere eşlemenize olanak sağlayan çoklu eşleme adlı bir özelliği de dahil olmak üzere çeşitli desteklenir. Örneğin, bir sınıf Post özelliğiyle sahibi kullanıcı türünde verildiğinde, aşağıdaki SQL tüm gerekli verileri döndürür:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Döndürülen her satır, hem kullanıcı hem de Post verileri içerir. Kullanıcı verileri kendi Owner özelliği aracılığıyla gönderme verisi eklenmesi gereken olduğundan, aşağıdaki işlev kullanılır:

```csharp
(post, user) => { post.Owner = user; return post; }
```

İlişkili kullanıcı verilerle doldurmuş kendi Owner özelliği ile gönderileri koleksiyonu döndürmek için tam kod listesi olacaktır:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Daha az kapsülleme sağladığından, geliştiricilerin kendi verilerin depolanma şeklini hakkında daha fazla bilmeniz Dapper gerektirir nasıl verimli bir şekilde sorgulamak ve onu getirmek için daha fazla kod yazın. Model, yalnızca yeni bir geçiş (başka bir EF çekirdek özelliği) oluşturma ve/veya bir DbContext tek bir yerde eşleme bilgilerin güncelleştirilmesini yerine değiştiğinde etkilenir her sorgu güncelleştirilmesi gerekir. Bu sorguları değil derleme zamanı garanti sahip, bu nedenle bunlar çalışma zamanında değişikliklere yanıt modeli ya da veritabanı, hataları hızla algılaması daha zor hale kesilebilir. Bu bileşim karşılığında Dapper son derece hızlı performans sağlar.

EF çekirdek çoğu uygulama ve neredeyse tüm uygulamaların çoğu bölümleri için kabul edilebilir performans sunar. Bu nedenle, geliştirici üretkenliği faydalarını kendi performansa ağır olasılığı yüksektir. Önbelleğe alınan yararlanabilir sorguları için gerçek sorgu yalnızca yürütülebilecek görece küçük yapma zamanı, küçük bir yüzdesi performans farklar tartışmalı sorgu.

## <a name="sql-or-nosql"></a>SQL veya NoSQL

Geleneksel olarak, SQL Server gibi ilişkisel veritabanları kalıcı veri depolama için Market hâkim, ancak bunlar yalnızca çözüm kullanılabilir değildir. NoSQL veritabanları ister [MongoDB](https://www.mongodb.com/what-is-mongodb) nesneleri depolamak için farklı bir yaklaşım sunar. Tabloları ve satır nesneleri eşleme yerine başka bir tüm nesne grafiğinin seri hale getirmek ve sonucu depolamak için bir seçenektir. Bu yaklaşımın avantajları en az bir başlangıçta, Basitlik ve Performans'dır. Nesne ilişkileri olan birçok tablolara parçalayın daha anahtar ile tek bir serileştirilmiş nesne depolamak kesinlikle basittir ve güncelleştirme ve nesne son başlatıldığından bu yana değişmiş olabilir satırları veritabanından alınır. Benzer şekilde, getirme ve bir anahtar tabanlı depolama alanından tek bir nesne seri durumdan genellikle çok daha hızlı ve daha kolay karmaşık birleştirmeler veya birden çok veritabanı sorguları tam olarak aynı nesne ilişkisel bir veritabanındaki oluşturmak için gerekli. Kilitleri veya işlemleri ya da sabit bir şema eksikliği de NoSQL veritabanları çok büyük veri kümeleri destekleyen birçok makineler arasında ölçeklendirme için çok uygun hale getirir.

Diğer taraftan, (bunlar genellikle olarak adlandırılan) belirli sakıncaları NoSQL veritabanlarına sahip. İlişkisel veritabanları normalleştirme tutarlılığı zorlamak ve verilerin yinelenmesini engellemek için kullanın. Bu veritabanının toplam boyutunu azaltır ve paylaşılan veri güncelleştirmeleri hemen veritabanı kullanılabilir olmasını sağlar. Bir ülkenin adı değiştirildiyse, adres kayıtları Update'ten kendilerini güncelleştirmeye gerek yararlanabileceğini şekilde ilişkisel bir veritabanında bir adres tablosu kimliği, bir ülke tablo başvurabilir. Ancak, bir NoSQL veritabanı adresi ve onun ilişkili ülke birçok depolanan nesneleri bir parçası olarak seri hale. Bir ülke adı için bir güncelleştirme yerine tek bir satır güncelleştirilmesi gibi nesnelerin tümünü gerektirir. İlişkisel veritabanları yabancı anahtarlar gibi kuralları zorunlu tutarak ilişkisel bütünlüğü de emin olabilirsiniz. NoSQL veritabanları verilerine böyle kısıtlamalar genellikle sağlamaz.

Başka bir karmaşıklık veritabanları uğraşmanız gereken NoSQL Sürüm ' dir. Bir nesnenin özelliklerini değiştirdiğinizde, depolanan önceki sürümlerden seri durumdan çıkarılacak mümkün olmayabilir. Bu nedenle, bir nesne seri hale getirilmiş (önceki) sürümüne sahip tüm var olan nesneleri yeni şemaya uyacak şekilde güncelleştirilmesi gerekir. İlişkisel bir veritabanından farklı kavramsal olarak değil, bazen şema değişiklikleri güncelleştirme kodları gerektiren veya güncelleştirmeleri eşleme. Ancak, değiştirilmelidir girdi sayısı çok görülür NoSQL yaklaşımda büyük olduğu için daha fazla çoğaltma veri.

Birden fazla sürümünü nesneleri depolamak için NoSQL veritabanlarında mümkündür, bir şey sabit şemasına ilişkisel veritabanları genellikle desteklemez. Ancak, bu durumda uygulama kodunuz nesneleri, karmaşıklık ekleme önceki sürümlerini varlığını hesabı gerekir.

NoSQL veritabanları genellikle zorla [ACID](https://en.wikipedia.org/wiki/ACID), sahip oldukları performans ve ölçeklenebilirlik avantajlarını ilişkisel veritabanları anlamına gelir. Bunlar, son derece büyük veri kümelerini ve depolama normalleştirilmiş tablo yapılarında için oldukça uygun olmayan nesneler için oldukça uygun. Neden tek bir uygulama hem ilişkisel yararlanamaz ve her en iyi olduğu kullanarak NoSQL veritabanlarını uygun bir neden yoktur.

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB şemasız verileri bulut tabanlı depolama sunan tam olarak yönetilen bir NoSQL veritabanı hizmetidir. DocumentDB hızlı ve tahmin edilebilir performans, yüksek kullanılabilirlik, esnek ölçeklendirme ve genel dağıtım için yerleşik olarak bulunur. Geliştiriciler, bir NoSQL veritabanı olmaya rağmen JSON verilerini zengin ve tanıdık SQL sorgu özellikleri kullanabilir. Documentdb'deki tüm kaynaklar JSON belgeleri olarak depolanır. Olarak yönetilen kaynakları *öğeleri*, hangi meta veriler içeren belge ve *akışları*, öğe koleksiyonunu olduğu. Şekil 8-2 farklı DocumentDB kaynakları arasındaki ilişkiyi gösterir.


![Bir NoSQL JSON veritabanı olan documentdb'de kaynaklar arasındaki hiyerarşi ilişkisi](./media/image8-2.png)

**Şekil 8-2.** DocumentDB kaynak kuruluş.

DocumentDB sorgu dili, JSON belgelerini sorgulamak için basit ancak güçlü bir arabirimdir. Dil, ANSI SQL dil bilgisinin kümesini destekler ve JavaScript nesnesi, dizileri, nesne oluşturması ve işlev çağrısını derin tümleştirme ekler.

**Başvuruları – DocumentDB**

-   DocumentDB Introduction\
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Diğer Kalıcılık seçenekleri

İlişkisel eklemeyi ve NoSQL depolama seçenekleri, ASP.NET Core uygulamaları bir bulut tabanlı ve ölçeklenebilir şekilde çeşitli veri biçimleri ve dosyalarını depolamak için Azure Storage kullanabilir. Azure depolama yüksek düzeyde ölçeklenebilir olduğundan küçük miktarda veri ve uygulamanızı gerektiriyorsa, yüzlerce veya terabayt depolama kadar ölçek depolama çıkışı başlatabilirsiniz. Azure Storage dört veri türlerini destekler:

-   BLOB Storage yapılandırılmamış metin veya ikili depolama, nesne depolama olarak adlandırılır.

-   Table Storage yapılandırılmış veri kümeleri için satır anahtarları erişilebilir.

-   Sıra tabanlı güvenilir Mesajlaşma için kuyruk depolama.

-   Azure sanal makineler ve şirket içi uygulamalar arasında paylaşılan dosya erişimi için dosya depolama alanı.

**Başvuruları – Azure depolama**

-   Azure depolama Introduction\
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Önbelleğe alma

Web uygulamalarında her web isteğini olası en kısa sürede tamamlanmalıdır. Bunu elde etmenin bir yolu, sunucunun isteği tamamlamak için olmalısınız dış çağrılarının sayısını çalıştırmanız gerekir. Önbelleğe alma sunucuda verilerin bir kopyasını saklamak içerir (veya başka bir veri diğer bir deyişle daha fazla veri kaynağını kolayca sorgulanan depolayın). Web uygulamaları ve özellikle SPA olmayan geleneksel web uygulamaları, tüm kullanıcı arabirimi her istek ile oluşturmanız gerekir. Bu, genellikle aynı veritabanı sorgularından sürekli olarak bir kullanıcı isteği sonraki çoğunu yapılmasını gerektirir. Bu yüzden sürekli veritabanından istemek için çok az neden çoğu durumda, bu verileri nadiren, değiştirir. ASP.NET Core yanıt, tüm sayfaları ve verileri önbelleğe alma, önbelleğe alma işlemi için önbelleğe alma konusunda daha ayrıntılı önbelleğe alma davranışını destekleyen destekler.

Önbelleğe alma uygularken, sorunları göz ayrılması içinde tutmak önemlidir. Veri erişim mantığınızı ya da Kullanıcı Arabiriminizin önbelleğe alma mantığını uygulamak kaçının. Bunun yerine, kendi sınıflarda önbelleğe alma şifreleyebilir ve yapılandırma davranışını yönetmek için kullanın. Bu açık/kapalı ve tek sorumluluk ilkeler izler ve onu büyüdükçe, uygulamanızda önbelleğe almayı kullanma yönetebilmeniz için daha kolay hale getirir.

### <a name="aspnet-core-response-caching"></a>ASP.NET Core yanıt önbelleğe alma

ASP.NET Core yanıt önbelleğe alma iki düzeylerini destekler. İlk düzeyi sunucu üzerindeki herhangi bir şey önbelleğe almaz, ancak, istemciler ve proxy sunucular önbellek yanıtları yönlendiren HTTP üstbilgileri ekler. Bu, tek tek denetleyicileri veya Eylemler ResponseCache özniteliği ekleyerek uygulanır:

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

Yanıt önbelleğe alma Ara yanıtları özelleştirebileceğiniz koşullar kümesine göre otomatik olarak önbelleğe alır. Varsayılan olarak, GET veya HEAD yöntemleri istenen yalnızca 200 (Tamam) yanıtlarını önbelleğe alınır. Ayrıca, istekleri Cache-Control yanıtta olması gerekir: ortak üstbilgi ve üstbilgileri yetkilendirme veya Set-Cookie içeremez. Bkz: bir [ara yazılım önbelleğe alma yanıt tarafından kullanılan önbelleğe alma koşullar tam listesi](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Veri önbelleğe alma

Yerine (veya ek olarak) tam web yanıtlarını önbelleğe alma, tek tek veri sorguların sonuçlarını önbelleğe alabilir. Bunun için bellek web sunucusunda önbelleğe alma veya kullanabilirsiniz kullanmak [dağıtılmış önbellek](https://docs.microsoft.com/aspnet/core/performance/caching/distributed). Bu bölümde nasıl bellek önbelleğe alma uygulanacağı gösterilmektedir.

Bellek desteği ekleme (veya dağıtılmış) içinde ConfigureServices önbelleğe alma:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Microsoft.Extensions.Caching.Memory NuGet paketini de eklediğinizden emin olun.

Hizmet ekledikten sonra önbellek erişmesi gereken her yerde bağımlılık ekleme IMemoryCache isteyin. Bu örnekte, erişimi kontrol (veya davranışına ekler) ICatalogService alternatif uygulaması sağlayarak CachedCatalogService Proxy (veya oluşturma öğesi) tasarım deseni kullanan temel CatalogService uygulaması.

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

Önbelleğe alınan hizmet sürümünü kullanın, ancak hala kurucusunda gereken CatalogService örneğini almak hizmetin izin için uygulamayı yapılandırmak için ConfigureServices aşağıdakileri ekleyin:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Bu yerinde katalog verilerini getirmek için veritabanı çağrılarını yalnızca dakikada bir kez yerine her istekte yapılacaktır. Site trafiği bağlı olarak, bu veritabanı ve ortalama sayfa yükleme süresi şu anda bu hizmet tarafından kullanıma sunulan sorguları üçünü bağlıdır giriş sayfası için yapılan sorguları sayısının çok önemli bir etkisi olabilir.

Önbelleğe alma uygulandığında ortaya bir sorun olduğunu *eski veri* – başka bir deyişle, kaynak ancak eski bir sürümü değişti veri önbellekte kalır. Bu sorunu azaltmak için basit bir yol için meşgul bir uygulama olduğundan verileri önbelleğe uzunluğu genişletme için sınırlı ek avantajı küçük önbellek süreleri kullanmaktır. Örneğin, bir tek veritabanı sorgusu yapan bir sayfa göz önünde bulundurun ve 10 kez saniyede istenecek. Bu sayfa bir dakika için önbelleğe alınmışsa dakika başına 1, azaltma %99.8 600 bırakma yapılan veritabanı sorguları sayısı sonuçlanır. Bunun yerine önbellek süresi bir saat yapılmışsa, genel azaltma %99.997 olacaktır, ancak artık eski veri olasılığı ve olası yaşını her ikisi de önemli ölçüde artırılır.

Başka bir yaklaşım içerdikleri veriler güncelleştirildiğinde önceden önbellek girişlerinin kaldırmaktır. Herhangi bir girişe anahtarıyla biliniyorsa kaldırılabilir:

```csharp
_cache.Remove(cacheKey);
```

Uygulamanızı önbelleğe alır girişleri güncelleştirmek için işlevselliği kullanıma sunan, karşılık gelen önbellek girişlerinin güncelleştirmeleri gerçekleştirir, kodunuzda kaldırabilirsiniz. Bazen belirli bir veri kümesine bağımlı birçok farklı girdi olabilir. Bu durumda, bir CancellationChangeToken kullanarak önbellek girişlerinin arasındaki bağımlılıkları oluşturmak yararlı olabilir. Bir CancellationChangeToken ile birden fazla önbellek girişlerinin aynı anda belirteci iptal edildiğinde dolabilir.

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
[Önceki](develop-asp-net-core-mvc-apps.md)
[sonraki](test-asp-net-core-mvc-apps.md)
