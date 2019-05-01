---
title: Entity Framework Core ile altyapı kalıcılık katmanını uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Entity Framework Core kullanarak altyapı kalıcılığı katmanını uygulama ayrıntılarını keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: a84c5057b7a35c837f2c597cd3e60cd293a70009
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61817979"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Entity Framework Core ile altyapı Kalıcılık katmanını uygulama

SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanları kullandığınızda, önerilen bir yaklaşım Entity Framework (EF) üzerinde temel Kalıcılık katmanını uygulamaktır. EF LINQ destekleyen ve güçlü şekilde yazılan nesnelerin, model yanı sıra, veritabanına Basitleştirilmiş Kalıcılık sağlar.

Entity Framework, .NET Framework'ün bir parçası olarak uzun bir geçmişe sahiptir. .NET Core kullandığınızda, Windows veya Linux'ta .NET Core aynı şekilde çalışan Entity Framework Core de kullanmalısınız. EF Core, Entity Framework, bir çok daha küçük kaplama alanı ve önemli performans geliştirmeleri ile uygulanan tamamını yeniden yazmak ' dir.

## <a name="introduction-to-entity-framework-core"></a>Entity Framework Core giriş

Entity Framework (EF) Core hafif, Genişletilebilir, ve platformlar arası sürümüne popüler Entity Framework Veri erişim teknolojisi. Mid-2016'da .NET Core ile kullanılmaya başlandı.

EF Core giriş zaten Microsoft belgelerinde olduğundan, burada yalnızca bu bilgilere bağlantılar sağlıyoruz.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Entity Framework Core** \
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- **Visual Studio kullanarak Entity Framework Core ve ASP.NET Core ile çalışmaya başlama** \
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- **DbContext sınıfı** \
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- **EF Core ve EF6.x karşılaştırması** \
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Entity Framework Core DDD açısından altyapısı

Bir DDD açısından bakıldığında, EF terminolojisinde POCO olarak da bilinen POCO etki alanı varlıklarının kullanma olanağı EF, önemli bir özellik olan *kod öncelikli varlıkları*. POCO etki alanı varlıklarının kullanırsanız, etki alanı model sınıflarınızı Kalıcılık-aşağıdaki ignorant, [Kalıcılık Ignorance](https://deviq.com/persistence-ignorance/) ve [altyapı Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri.

DDD deseni, etki alanı davranışını ve varlık sınıfın kendisi kuralların, okuduğunuzda, doğrulama ve kuralları herhangi bir koleksiyonuna erişirken denetleyebilirsiniz şekilde kapsüllemesi gerekir. Bu nedenle, varlıklar veya değer nesneleri alt koleksiyonları genel erişime izin vermek için DDD iyi bir uygulama değil. Bunun yerine, bu durum oluştuğunda nasıl ve ne zaman özellik koleksiyonları ve alanlar güncelleştirilebilir, denetleyen yöntemleri ve hangi davranışı ve Eylemler gerçekleşmelidir kullanıma sunmak istediğiniz.

EF Core 1.1 beri bu DDD gereksinimleri karşılamak için düz alanları varlıklarınızı genel özellikleri yerine de olabilir. Dışarıdan erişilebilir olması için bir varlık alanı istemiyorsanız, yalnızca özellik veya alan bir özelliği yerine oluşturabilirsiniz. Özel özellik ayarlayıcılarına de kullanabilirsiniz.

Benzer şekilde, artık salt okunur erişim koleksiyonlara olarak yazılan genel bir özelliğini kullanarak olabilir `IReadOnlyCollection<T>`, koleksiyon için bir özel alanın üyesi tarafından desteklenen (gibi bir `List<T>`) varlığınızdaki EF üzerinde kalıcılığını kullanır. Entity Framework'ün önceki sürümlerinde, koleksiyon özellikleri desteklemek için gerekli `ICollection<T>`, üst varlık sınıfı kullanarak herhangi bir geliştirici ekleyebilir veya özellik koleksiyonları üzerinden öğeleri kaldırma, geliyordu. Bu olası önerilen DDD desenlerini karşı olacaktır.

Bir özel koleksiyon salt okunur gösterme çalışırken kullanabileceğiniz `IReadOnlyCollection<T>` nesne, aşağıdaki kod örneğinde gösterildiği gibi:

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
                             decimal unitPrice, decimal discount,
                             string pictureUrl, int units = 1)
    {
        // Validation logic...

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

Unutmayın `OrderItems` özelliği yalnızca erişilebilir salt okunur kullanılarak `IReadOnlyCollection<OrderItem>`. Bu tür, salt okunur normal dış güncelleştirmeleri karşı korunur.

EF Core "etki alanı modeli contaminating olmadan" etki alanı modeli fiziksel veritabanında eşlemek için bir yol sağlar. Eşleme eylem Kalıcılık katmanında uygulanır saf POCO .NET kodu olmasıdır. Bu eşleme eylem alanları veritabanı eşleme yapılandırmanız gerekir. Aşağıdaki örnekte `OnModelCreating` yönteminden `OrderingContext` ve `OrderEntityTypeConfiguration` sınıfı, çağrı `SetPropertyAccessMode` erişmeye EF Core söyler `OrderItems` özelliği aracılığıyla kendi alan.

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

Alanları özellikleri yerine kullandığınızda `OrderItem` yalnızca bu varmış gibi varlık kalıcı bir `List<OrderItem>` özelliği. Ancak, tek bir erişimci kullanıma sunduğu `AddOrderItem` siparişe yeni öğeler eklemek için yöntemi. Sonuç olarak, davranış ve veri birbirine bağlıdır ve etki alanı modeli kullanan herhangi bir uygulama kodu tutarlı olur.

## <a name="implement-custom-repositories-with-entity-framework-core"></a>Entity Framework Core ile uygulama özel depolar

Uygulama düzeyinde bir sınıf veri kalıcılığı kodla (EF Core içinde DBContext) iş birimi tarafından denetlenen bir depo olan güncelleştirmeler, aşağıdaki sınıfında gösterildiği gerçekleştirirken:

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;
        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == BuyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

Bir sözleşme olarak etki alanı modeli katmandan IBuyerRepository arabirimi geldiğini unutmayın. Bununla birlikte, havuz uygulama Kalıcılık ve altyapı katmanını gerçekleştirilir.

EF DbContext Oluşturucu bağımlılık ekleme kullanılarak aracılığıyla sunulur. Varsayılan yaşam süresi sayesinde aynı HTTP istek kapsamı içinde birden çok deposu arasında paylaşıldığından (`ServiceLifetime.Scoped`) IOC kapsayıcısındaki (Bu da açıkça ayarlayabilirsiniz ile `services.AddDbContext<>`).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>(Güncelleştirmeler veya sorgular ve işlemler) deposunda uygulamaya yönelik yöntemleri

Her bir depo sınıfına içinde kendi ilgili toplama tarafından bulunan varlıkların durumunu güncelleştirme Kalıcılık yöntemleri koymanız gerekir. Toplama ve onun ilişkili depo arasındaki birebir ilişkisi olduğunu unutmayın. Bir toplama kök varlık nesnesi EF grafiğini içindeki alt varlıklar katıştırılmış sahip göz önünde bulundurun. Örneğin, bir alıcı birden çok ödeme yöntemlerini ilgili alt varlıklar olarak sahip olabilir.

Çoğu sorgu hizmetine sıralama mikro hizmet yaklaşımı da CQS/CQRS tabanlı olduğundan, özel depolarda uygulanmadı. Geliştiriciler, birleşimler, toplamlar, toplama ve DDD başına özel depo tarafından genel olarak uygulanan kısıtlamaları sunu katmanı için ihtiyaç duydukları ve sorgular oluşturmak için özgürlüğüne sahipsiniz. Bu kılavuzda önerilen özel depolara çoğunu birkaç güncelleştirme veya işlem yöntemleri sahip ancak güncelleştirilecek veri almak yalnızca sorgu yöntemleri gerekli. Örneğin, uygulama belirli bir alıcı siparişle ilgili yeni bir alıcı oluşturmadan önce mevcut olup olmadığını bilmek gerektiğinden BuyerRepository deponun bir FindAsync yöntemi uygular.

Ancak, sunu katmanı veya istemci uygulamalarına göndermek için verileri almak için gerçek sorgu yöntemleri Dapper kullanarak esnek sorguları temel alan CQRS sorgular belirtildiği gibi uygulanır.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>EF DbContext doğrudan kullanmak yerine özel bir depo kullanmaya

Entity Framework DbContext sınıfına, iş birimi ve depo düzenlerini esas alarak ve doğrudan sizin kodunuzdan gibi bir ASP.NET Core MVC denetleyicisi kullanılabilir. Diğer bir deyişle şekilde CRUD Kataloğu mikro hizmetine olduğu gibi basit kod oluşturabilirsiniz. Birçok geliştirici gibi basit kod olası istediğiniz durumlarda DbContext sınıfını doğrudan kullanmak isteyebilirsiniz.

Ancak, özel depoları uygulama çeşitli avantajlar daha karmaşık mikro hizmetler veya uygulamalar uygularken'sağlar. İş birimi ve depo desenleri altyapı Kalıcılık katmanını uygulama ve etki alanı modeli katmanları ayrılmış şekilde kapsüllemek için tasarlanmıştır. Bu desenleri uygulama veritabanına erişimi benzetimi sahte depoları kullanımını kolaylaştırabilir.

Şekil 7-18 Bu depolar sahte kolaylaştıran depoları kullanmak yerine (EF DbContext doğrudan kullanarak) depoları kullanmayan arasındaki farklar görebilirsiniz.

![Özel bir depo ve düz bir DbContext kullanarak arasında karşılaştırma: özel depo depo sahte işlem tarafından test kolaylaştırmak için kullanılan bir soyutlama katmanı ekler.](./media/image19.png)

**Şekil 7-18**. Düz bir DbContext ve özel depoları kullanan

Sahte işlem, birden çok çok\r\nalternatif vardır. Yalnızca depoları sahte veya tam bir iş birimi sahte. Depolar genellikle sahte yeterli olur ve karmaşıklığını soyut ve tam bir iş birimi sahte genellikle gerekli değildir.

Daha sonra biz uygulama katmanına odaklanmak, bağımlılık ekleme'de ASP.NET Core nasıl çalıştığını ve nasıl depoları kullanırken uygulandığı görürsünüz.

Kısacası, özel depo tarafından veri katmanı durumu etkilenmez birim testleriyle kod daha kolay test olanak sağlar. Ayrıca varlık çerçevesi gerçek veritabanına erişim testleri çalıştırırsanız, bunlar değil, ancak çok daha yavaş tümleştirme testleri, birim testleri.

DbContext doğrudan kullanıyorsanız, bunu sahte ya da bir bellek içi SQL Server ile öngörülebilir veri için birim testleri kullanarak birim testlerini çalıştırmak için gerekir. Ancak depo düzeyinde sahte işlem daha fazla çalışma DbContext sahte işlem veya sahte veri denetimi gerektirir. Elbette, MVC denetleyicileri her zaman test edebilirsiniz.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>IOC kapsayıcınızda EF DbContext ve IUnitOfWork örneği ömrü

`DbContext` Nesne (olarak kullanıma sunulan bir `IUnitOfWork` nesne) aynı HTTP istek kapsamı içinde birden çok deposu arasında paylaşılması. Yürütülen işlem, birden çok toplamalar veya yalnızca işlem yapması gerekir, örneğin, böyle birden çok depo örneği kullandığından. Bu söz önemlidir `IUnitOfWork` arabirimi etki alanı katmanınızdaki EF Core türü bir parçasıdır.

Bu örneği yapmak için `DbContext` nenesindeki hizmet ömrü ServiceLifetime.Scoped için ayarlamak. Bu varsayılan yaşam süresi, kaydolurken bir `DbContext` ile `services.AddDbContext` IOC kapsayıcınızda Createservicereplicalisteners() yönteminden `Startup.cs` dosyasında, ASP.NET Core Web API projesi. Aşağıdaki kod bunu göstermektedir.

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
      .AddDbContext<OrderingContext>(options =>
      {
          options.UseSqlServer(Configuration["ConnectionString"],
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

DbContext örnek oluşturma modu ServiceLifetime.Transient veya ServiceLifetime.Singleton olarak yapılandırılmamalıdır.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>IOC kapsayıcınızda depo örneği ömrü

Benzer şekilde, deponun yaşam süresi genellikle kapsamlı (Autofac içinde InstancePerLifetimeScope) olarak ayarlanmalıdır. Ayrıca olabilir kapsamlı ömrü kullanırken geçici (InstancePerDependency Autofac içinde) hizmetinizi ancak gelince bellekte daha verimli olacaktır.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

DbContext ayarlandığında depo için singleton ömrü kullanarak ciddi eşzamanlılık sorunlara neden olabilecek unutmayın (InstancePerLifetimeScope) yaşam süresi (varsayılan yaşam süreleri bir DBContext) kapsamı.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Bir ASP.NET MVC uygulamasındaki depo ve iş birimi desenleri uygulama** \
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- **Jonathan Allen. Depo düzeni Dapper, Entity Framework ile uygulama stratejilerini ve zinciri** \
  <https://www.infoq.com/articles/repository-implementation-strategies>

- **Cesar de la Torre. ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamları ile karşılaştırma** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a>Tablo eşleme

Tablo eşleme, gelen Sorgulanacak tablo verilerini tanımlar ve veritabanına kaydedilir. Daha önce etki alanı varlıklarının (örneğin, bir ürün veya sipariş etki) ilgili veritabanı şema oluşturmak için nasıl kullanılabileceğini gördünüz. EF kavramı kesin tasarlanmış *kuralları*. "Ne bir tablonun adı olacak?" gibi kuralları adresi soruları veya "birincil anahtarı hangi özelliği nedir?" Kurallarına genellikle geleneksel adlarına dayalı — Örneğin, tipik kimliği ile biten bir özellik olarak birincil anahtar

Kural gereği, her bir varlık aynı ada sahip bir tablo eşlemek için ayarlanır `DbSet<TEntity>` sunan varlık üzerinde türetilmiş bağlam özelliği. Hayır ise `DbSet<TEntity>` değerdir sağlanan belirtilen varlık için sınıf adı kullanılır.

### <a name="data-annotations-versus-fluent-api"></a>Veri ek açıklamaları Fluent API'si ile karşılaştırması

Birçok ek EF Core kuralları vardır ve bunların çoğu veri ek açıklamaları veya OnModelCreating yöntemi içinde uygulanan Fluent API'si kullanılarak değiştirilebilir.

Veri ek açıklamaları bir DDD açısından daha duraklatıcı bir yolu olan varlık modeli sınıflarında kendileri kullanılmalıdır. Altyapı veritabanı ile ilgili veri açıklamalarla modelinizi contaminating olmasıdır. Öte yandan, Fluent API'si varlık modeli temiz ve ayrılmış Kalıcılık altyapısından böylece çoğu kuralları ve veri saklama altyapı katmanını eşlemelerini değiştirmek için kullanışlı bir yoldur.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Fluent API'si ve OnModelCreating yöntemi

Kuralları ve eşlemelerini değiştirmek için belirtildiği gibi DbContext sınıfında OnModelCreating yöntemi kullanabilirsiniz.

Sıralama mikro hizmetine açık eşleme ve yapılandırması, gerektiğinde, aşağıdaki kodda gösterildiği gibi uygular.

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
            orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

            orderConfiguration.HasKey(o => o.Id);

            orderConfiguration.Ignore(b => b.DomainEvents);

            orderConfiguration.Property(o => o.Id)
                .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

            //Address Value Object persisted as owned entity type supported since EF Core 2.0
            orderConfiguration.OwnsOne(o => o.Address);

            orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
            orderConfiguration.Property<int?>("BuyerId").IsRequired(false);
            orderConfiguration.Property<int>("OrderStatusId").IsRequired();
            orderConfiguration.Property<int?>("PaymentMethodId").IsRequired(false);
            orderConfiguration.Property<string>("Description").IsRequired(false);

            var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

            // DDD Patterns comment:
            //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
            navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

            orderConfiguration.HasOne<PaymentMethod>()
                .WithMany()
                .HasForeignKey("PaymentMethodId")
                .IsRequired(false)
                .OnDelete(DeleteBehavior.Restrict);

            orderConfiguration.HasOne<Buyer>()
                .WithMany()
                .IsRequired(false)
                .HasForeignKey("BuyerId");

            orderConfiguration.HasOne(o => o.OrderStatus)
                .WithMany()
                .HasForeignKey("OrderStatusId");
    }
}
```

Aynı OnModelCreating yöntemi içindeki tüm Fluent API'si eşlemeleri ayarlayabilirsiniz, ancak bu örnekte gösterildiği gibi her varlık, birden çok yapılandırma sınıfı bu kodu bölüm ve önerilir. Özellikle büyük modeller için özellikle, farklı varlık türleri yapılandırmak için ayrı yapılandırma sınıfları olması önerilir.

Örnek kodda, birkaç açık bildirimler ve eşleme gösterir. Sizin durumunuzda gerekir gerçek kod daha küçük olabilir ancak, EF Core kuralları çoğu bu eşlemelerin otomatik olarak yapabilir.

### <a name="the-hilo-algorithm-in-ef-core"></a>EF Core Merhaba/Lo algoritması

Bir ilgi çekici, yukarıdaki örnekteki kod bunu kullandığını yönüdür [yüksek/Lo algoritması](https://vladmihalcea.com/the-hilo-algorithm/) anahtar oluşturma stratejisi olarak.

Yüksek/Lo algoritması, değişiklikleri yapmadan önce benzersiz anahtarlar gerektiğinde faydalıdır. Bir Özet, yüksek-Lo algoritması satır veritabanında hemen depolamayın sırada bağlı olarak tablo satırları benzersiz tanımlayıcıları atar. Bu, normal sıralı veritabanı kimliklerine olduğu sürece tanımlayıcıları hemen kullanmaya başlamanıza olanak sağlar.

Yüksek/Lo algoritması benzersiz kimliklerinin toplu ilgili veritabanı dizisinden almaya yönelik bir mekanizma açıklar. Bu veritabanı benzersizliği garanti eder, bu olmayacaktır böylece kullanıcılar arasında hiçbir çakışma olduğundan güvenli Kimlikleridir. Bu algoritma Bu nedenlerden dolayı ilginçtir:

- İş birimi deseni kesmez.

- Veritabanı gidiş dönüş en aza indirmek için toplu kimlikleri dizisi alır.

- Bu, guid kullan teknikleri aksine insanlarca okunabilen tanımlayıcı oluşturur.

EF Core destekler [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo yöntemiyle yukarıdaki örnekte gösterildiği gibi.

### <a name="map-fields-instead-of-properties"></a>Harita alanları özellikleri yerine

Bu özellik, EF Core 1.1 sürümünden itibaren kullanılabilir, doğrudan sütunları alanlarına eşleyebilirsiniz. Bu, özellikleri varlık sınıfında kullanmayı ve yalnızca bir tablodaki sütunların alanlara eşlemek için mümkündür. Yaygın bir kullanımı söz konusu varlık dışında erişilmesi gerekmeyen özel alanlar için herhangi bir iç durum olacaktır.

Bu tek alanları veya Ayrıca koleksiyonları ile gibi yapabileceğiniz bir `List<>` alan. Bu nokta etki alanı model sınıfları modelleme konusuna değinmiştik, ancak burada, bu eşlemenin ile nasıl gerçekleştirildiğini görebilirsiniz daha önce bahsedilen `PropertyAccessMode.Field` önceki kodda vurgulanan yapılandırma.

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>EF Core, altyapı düzeyinde gizli gölge özellikleri kullanın

EF Core gölge özelliklerinde varlık sınıfı modelinizde var olmayan özelliklerdir. Bu özelliklerin durumları ve değerler tamamen içinde korunur [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) altyapı düzeyinde sınıfı.

## <a name="implement-the-query-specification-pattern"></a>Sorgu belirtimi desenini uygulama

Tasarım bölümünde daha önce sunulan gibi sorgu belirtimi burada bir sorgu tanımını sıralama ve mantıksal disk belleği isteğe bağlı koyabilirsiniz yer olarak tasarlanmış bir etki alanı Odaklı Tasarım deseni modelidir.

Sorgu belirtimi deseni bir sorgu bir nesneyi tanımlar. Örneğin, bazı ürünler için bir disk belleğine alınan sorgu kapsüllemek için gereken giriş parametrelerini (pageNumber, pageSize, filtre, vb.) alan bir PagedProduct belirtimi oluşturabilirsiniz. Sonra hiçbir depo yöntemi içinde (genellikle bir List() aşırı yük) bir IQuerySpecification kabul ve bu belirtimine göre beklenen sorgusunu çalıştırın.

Aşağıdaki kod, bir genel belirtimi arabirimi örnektir [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

Ardından, genel belirtimi temel sınıfın uygulaması verilmiştir.

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

Şu belirtime Sepet'ın Kimliğini veya sepete Kime ait alıcı kimliği verilen bir sepet tek varlık yükler. Götürür [eagerly yük](https://docs.microsoft.com/ef/core/querying/related-data) Sepet'ın öğeleri koleksiyonu.

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }
    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

Son olarak, belirtilen varlık türünü t ilgili filtre ve eager yük verileri için bir tür belirtimi genel bir EF depo nasıl kullanabileceğinizi aşağıda görebilirsiniz

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

Filtreleme mantığı Kapsüllenen yanı sıra belirtimi doldurmak için hangi özelliklerin dahil olmak üzere verilerin döndürülmesi için Şekil belirtebilirsiniz.

Bir depodan Iqueryable döndürülecek önermemekteyiz olsa da, bunları bir sonuç kümesini oluşturmak için depo içinde kullanmak mükemmel bir şekilde daha uygundur. Bu yaklaşım, sorgunun listesini oluşturmak için Ara Iqueryable ifadeler kullanan yukarıdaki son satırında belirtimi ölçütlerle sorguyu çalıştırmadan önce includes yöntemi listesinde kullanılan görebilirsiniz.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Tablo eşleme** \
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- **HiLo Entity Framework Core ile anahtarlar oluşturmak için kullanın** \
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- **Destek alanları** \
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- **Steve Smith. Entity Framework Core kapsüllenmiş koleksiyonları** \
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- **Gölge Özellikler** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Belirtimi deseni** \
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> [Önceki](infrastructure-persistence-layer-design.md)
> [İleri](nosql-database-persistence-infrastructure.md)
