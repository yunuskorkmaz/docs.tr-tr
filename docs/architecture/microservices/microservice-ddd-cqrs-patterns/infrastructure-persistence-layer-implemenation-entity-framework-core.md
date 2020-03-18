---
title: Entity Framework Core ile altyapı kalıcılık katmanını uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Entity Framework Core'u kullanarak altyapı kalıcılığı katmanının uygulama ayrıntılarını keşfedin.
ms.date: 01/30/2020
ms.openlocfilehash: 63579dc74ba52551bc1ee02a57337c1b17fdf396
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401629"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Entity Framework Core ile altyapı kalıcılığı katmanını uygulayın

SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanlarını kullandığınızda, önerilen bir yaklaşım Varlık Çerçevesi 'ne (EF) dayalı kalıcılık katmanını uygulamaktır. EF, LINQ'yi destekler ve modeliniz için güçlü şekilde yazılan nesnelerin yanı sıra veritabanınıza basitleştirilmiş kalıcılık sağlar.

Varlık Çerçevesi.NET Çerçevesi'nin bir parçası olarak uzun bir geçmişe sahiptir. .NET Core'u kullandığınızda, Windows veya Linux'ta .NET Core ile aynı şekilde çalışan Entity Framework Core'u da kullanmanız gerekir. EF Core, çok daha küçük bir ayak izi ve performansta önemli iyileştirmelerle uygulanan Entity Framework'ün tam bir yeniden yazılmasıdır.

## <a name="introduction-to-entity-framework-core"></a>Varlık Çerçeve Çekirdeğine Giriş

Entity Framework (EF) Core, popüler Entity Framework veri erişim teknolojisinin hafif, genişletilebilir ve çapraz platformlu bir sürümüdür. 2016 ortalarında .NET Core ile tanıtıldı.

EF Core'a giriş zaten Microsoft belgelerinde mevcut olduğundan, burada sadece bu bilgilere bağlantılar salıyoruz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Varlık Çerçeve Çekirdeği** \
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- **Visual Studio'ASP.NET Core ve Entity Framework Core ile başlarken** \
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- **DbContext Sınıfı** \
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- **EF Çekirdek & EF6.x karşılaştırın** \
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>DDD perspektifinden Varlık Çerçeve Çekirdeğinde Altyapı

DDD açısından bakıldığında, EF'nin önemli bir özelliği, EF terminolojisinde POCO *kod ilk varlıkları*olarak da bilinen POCO etki alanı varlıklarını kullanabilmesidir. POCO etki alanı varlıklarını kullanıyorsanız, etki alanı modeli sınıflarınız [Kalıcılık Cehaleti](https://deviq.com/persistence-ignorance/) ve [Altyapı Cehaleti](https://ayende.com/blog/3137/infrastructure-ignorance) ilkelerini izleyerek kalıcılık-cahildir.

DDD desenleri başına, etki alanı davranışını ve kurallarını varlık sınıfının içinde kapsüllemeniz gerekir, böylece herhangi bir koleksiyona erişirken değişmezleri, doğrulamaları ve kuralları denetleyebilir. Bu nedenle, DDD'de alt varlıkların veya değer nesnelerinin koleksiyonlarına genel erişime izin vermek iyi bir uygulama değildir. Bunun yerine, alanlarınızın ve özellik koleksiyonlarınızın nasıl ve ne zaman güncelleştirileceğini ve bu olduğunda hangi davranış ve eylemlerin oluşması gerektiğini denetleyen yöntemler ortaya çıkarmak istiyorsunuz.

EF Core 1.1'den bu yana, bu DDD gereksinimlerini karşılamak için, kamu malları yerine varlıklarınızda düz alanlar olabilir. Bir varlık alanının dışarıdan erişilebilir olmasını istemiyorsanız, özellik yerine öznitelik veya alan oluşturabilirsiniz. Özel mülk ayarlayıcılarını da kullanabilirsiniz.

Benzer bir şekilde, artık kalıcılık için EF'ye dayanan varlığınızdaki koleksiyon `IReadOnlyCollection<T>`için özel bir alan üyesi tarafından desteklenen bir `List<T>`kamu malı (örneğin) olarak yazılan bir kamu malı kullanarak koleksiyonlara salt okunur erişim elde edebilirsiniz. Entity Framework'ün önceki sürümleri, `ICollection<T>`üst varlık sınıfını kullanan herhangi bir geliştiricinin özellik koleksiyonları aracılığıyla öğe ekleyebileceği veya kaldırabileceği anlamına gelen toplama özelliklerinin desteklenmesini gerektiriyordu. Bu olasılık DDD önerilen desenlere karşı olacaktır.

Aşağıdaki kod örneğinde gösterildiği gibi, salt `IReadOnlyCollection<T>` okunur bir nesneyi ortaya çıkarırken özel bir koleksiyon kullanabilirsiniz:

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

`OrderItems` Özellik yalnızca salt okunur olarak `IReadOnlyCollection<OrderItem>`erişilebileni unutmayın. Bu tür salt okunur, böylece düzenli dış güncelleştirmeler karşı korunur.

EF Core, etki alanı modelini "kirletmeden" etki alanı modelini fiziksel veritabanıyla eşlemenin bir yolunu sağlar. Bu saf .NET POCO kodudur, çünkü eşleme eylemi kalıcılık katmanında uygulanır. Bu eşleme eyleminde, alanlara veritabanı eşlemi yapılandırmanız gerekir. Yöntemden `OnModelCreating` `OrderingContext` ve sınıftan `OrderEntityTypeConfiguration` aşağıdaki örnekte, EF `SetPropertyAccessMode` Core'a `OrderItems` kendi alanı üzerinden özelliğe erişmesini söyler.

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

Özellikler yerine alanları kullandığınızda, `OrderItem` varlık bir `List<OrderItem>` özelliği varmış gibi kalıcı hale gelir. Ancak, siparişe yeni öğeler eklemek `AddOrderItem` için tek bir erişimci, yöntem ortaya çıkarır. Sonuç olarak, davranış ve veriler birbirine bağlıdır ve etki alanı modelini kullanan tüm uygulama kodları boyunca tutarlı olacaktır.

## <a name="implement-custom-repositories-with-entity-framework-core"></a>Entity Framework Core ile özel depoları uygulama

Uygulama düzeyinde, bir depo yalnızca aşağıdaki sınıfta gösterildiği gibi güncelleştirmeleri gerçekleştirirken bir çalışma birimi (EF Core'da DBContext) tarafından koordine edilen veri kalıcılık koduna sahip bir sınıftır:

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

IBuyerRepozitory arabiriminin bir sözleşme olarak etki alanı modeli katmanından geldiğini unutmayın. Ancak, depo uygulaması kalıcılık ve altyapı katmanında yapılır.

EF DbContext Bağımlılık Enjeksiyon u yoluyla yapıcı aracılığıyla gelir. IoC kapsayıcısındaki varsayılan ömrü ()`ServiceLifetime.Scoped`sayesinde aynı HTTP istek kapsamı içinde birden fazla depo arasında paylaşılır `services.AddDbContext<>`(bu da açıkça ayarlanabilir).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Bir depoda uygulanacak yöntemler (güncelleştirmeler veya hareketler sorgulara karşı)

Her depo sınıfı içinde, ilgili toplamı tarafından bulunan varlıkların durumunu güncelleştirmek kalıcılık yöntemleri ni koymalısınız. Bir toplam ve ilgili depo arasında bire bir ilişki olduğunu unutmayın. Bir toplu kök varlık nesnesinin EF grafiğinde alt varlıkları katıştırılmış olabileceğini göz önünde bulundurun. Örneğin, bir alıcının ilgili alt varlıklar olarak birden çok ödeme yöntemi olabilir.

eShopOnContainers sipariş microservice için yaklaşım da CQS / CQRS dayalı olduğundan, sorguların çoğu özel depolarda uygulanmaz. Geliştiriciler, agregalar, genel olarak özel depolar ve genel olarak DDD tarafından uygulanan kısıtlamalar olmadan sunu katmanı için gereksinim duydukları sorguları ve birleştirmeleri oluşturma özgürlüğüne sahiptir. Bu kılavuz tarafından önerilen özel depoların çoğunda birkaç güncelleştirme veya işlem yöntemi vardır, ancak verilerin güncelleştirilen için yalnızca sorgu yöntemleri gerekir. Örneğin, AlıcıRepository deposu findasync yöntemini uygular, çünkü uygulamanın siparişle ilgili yeni bir alıcı oluşturmadan önce belirli bir alıcının var olup olmadığını bilmesi gerekir.

Ancak, dapper kullanarak esnek sorguları temel alan CQRS sorgularında, söz konusu olduğu gibi, sunu katmanına veya istemci uygulamalarına gönderilecek verileri almak için gerçek sorgu yöntemleri uygulanır.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>EF DbContext'ı doğrudan kullanmanın karşısı özel bir depo kullanma

Entity Framework DbContext sınıfı Çalışma Birimi ve Depo desenleri'ni temel alınca, ASP.NET Core MVC denetleyicisi gibi doğrudan kodunuzdan kullanılabilir. EShopOnContainers CRUD katalog microservice gibi, en basit kodu oluşturabilirsiniz yoludur. Mümkün olan en basit kodu istediğiniz durumlarda, birçok geliştiricinin yaptığı gibi Doğrudan DbContext sınıfını kullanmak isteyebilirsiniz.

Ancak, özel depoların uygulanması, daha karmaşık mikro hizmetler veya uygulamalar uygularken çeşitli avantajlar sağlar. Çalışma Birimi ve Depo desenleri, uygulama ve etki alanı modeli katmanlarından ayrılması için altyapı kalıcılık katmanını kapsüllemek için tasarlanmıştır. Bu desenlerin uygulanması, veritabanına erişimi taklit eden sahte depoların kullanımını kolaylaştırabilir.

Şekil 7-18'de, depoları kullanmamak (doğrudan EF DbContext'ı kullanmamak) ile bu depolarla alay etmeyi kolaylaştıran depolar arasındaki farkları görebilirsiniz.

![İki depodaki bileşenleri ve veri akışını gösteren diyagram.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

**Şekil 7-18**. Düz bir DbContext'a karşı özel depolar kullanma

Şekil 7-18, özel bir depo kullanarak, depoyla alay ederek testi kolaylaştırmak için kullanılabilecek bir soyutlama katmanı ekladığını gösterir. Alay ederken birden fazla alternatif vardır. Sadece depolarla alay edebilirsin ya da bütün bir iş birimiyle dalga geçebilirsin. Genellikle sadece depoları alay yeterlidir ve soyut ve iş bütün bir birim alay karmaşıklığı genellikle gerekli değildir.

Daha sonra, uygulama katmanına odaklandığımızda, Bağımlılık Enjeksiyonu'nun ASP.NET Core'da nasıl çalıştığını ve depoları kullanırken nasıl uygulandığını göreceksiniz.

Kısacası, özel depolar, veri katmanı durumundan etkilenmemiş birim testleri ile kodu daha kolay sınamanızı sağlar. Varlık Çerçevesi üzerinden gerçek veritabanına da erişen testler çalıştırıyorsanız, bunlar birim testleri değil, çok daha yavaş olan tümleştirme testleridir.

DbContext'ı doğrudan kullanıyorsanız, birim testleri için öngörülebilir verilere sahip bir bellek içi SQL Server kullanarak onunla alay etmek veya birim testleri çalıştırmak zorunda kalırdınız. Ancak DbContext ile alay etmek veya sahte verileri kontrol etmek, depo düzeyinde alay etmekten daha fazla iş gerektirir. Tabii ki, her zaman MVC denetleyicileri test edebilirsiniz.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>IoC kabınızda EF DbContext ve IUnitOfWork örnek ömrü

Nesne `DbContext` (nesne `IUnitOfWork` olarak açıkta) aynı HTTP istek kapsamı içinde birden çok depo arasında paylaşılmalıdır. Örneğin, yürütülen işlemin birden çok toplamla ilgilenmesi gerektiğinde veya yalnızca birden çok depo örneği kullandığınızdan bu durum geçerlidir. `IUnitOfWork` Arabirimin bir EF Core türü değil, etki alanı katmanınızın bir parçası olduğunu da belirtmek önemlidir.

Bunu yapmak için, nesnenin `DbContext` örneğinin hizmet ömrü ServiceLifetime.Scoped olarak ayarlanmış olması gerekir. Bu, ASP.NET Core Web `DbContext` API projenizdeki dosyanın `services.AddDbContext` `Startup.cs` ConfigureServices yönteminden IoC kapsayıcınızda bir ile birlikte kaydolurken varsayılan kullanım ömrüdür. Aşağıdaki kod bunu göstermektedir.

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

DbContext anlık kullanım modu ServiceLifetime.Geçici veya ServiceLifetime.Singleton olarak yapılandırılmamalıdır.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>IoC kabınızdaki depo örneği ömrü

Benzer bir şekilde, deponun ömrü genellikle kapsamlı olarak ayarlanmalıdır (Autofac'da InstancePerLifetimeScope). Ayrıca geçici olabilir (Autofac InstancePerDependency), ancak hizmet kapsamı kullanırken bellek açısından daha verimli olacaktır.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Depo için singleton ömrünün kullanılmasının, DbContext'ınız kapsamlı (InstancePerLifetimeScope) ömür boyu (DBContext için varsayılan yaşam süreleri) olarak ayarlandığında ciddi eşzamanlılık sorunlarına neden olabileceğini unutmayın.

### <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET MVC Uygulamasında Çalışma Düzenlerinin Depo ve Biriminin Uygulanması** \
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- **Jonathan Allen' ı. Varlık Çerçevesi, Dapper ve Zincirile Depo Deseni Uygulama Stratejileri** \
  <https://www.infoq.com/articles/repository-implementation-strategies>

- **Cesar de la Torre. ASP.NET Core IoC konteyner hizmet ömürlerinin Autofac IoC konteyner örnek kapsamları ile karşılaştırılması** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a>Tablo eşleme

Tablo eşleme, sorgulanacak ve veritabanına kaydedilecek tablo verilerini tanımlar. Daha önce, etki alanı varlıklarının (örneğin, bir ürün veya sipariş etki alanı) ilgili bir veritabanı şeması oluşturmak için nasıl kullanılabileceğini gördünuz. EF güçlü *kongrekavramı*etrafında tasarlanmıştır. Kongreler "Tablonun adı ne olacak?" gibi soruları ele alıyor. veya "Birincil anahtar hangi özelliktir?" Sözleşmeler genellikle geleneksel adlara dayanır(örneğin, birincil anahtarın Id ile biten bir özellik olması tipiktir.

Kural olarak, her varlık, türetilmiş bağlamda varlığı ortaya `DbSet<TEntity>` çıkaran özellik ile aynı ada sahip bir tabloya eşlenecek şekilde ayarlanır. Verilen `DbSet<TEntity>` varlık için değer sağlanmadıysa, sınıf adı kullanılır.

### <a name="data-annotations-versus-fluent-api"></a>Veri Ek Açıklamaları ve Akıcı API

Birçok ek EF Core kuralı vardır ve bunların çoğu, OnModelOluşturma yöntemi içinde uygulanan veri ek açıklamaları veya Akıcı API kullanılarak değiştirilebilir.

Veri ek açıklamaları, DDD açısından daha müdahaleci bir şekilde olan varlık modeli sınıflarının kendileri üzerinde kullanılmalıdır. Bunun nedeni, modelinizi altyapı veritabanıyla ilgili veri ek açıklamalarıyla kirletiyor olmasıdır. Diğer taraftan, Akıcı API, veri kalıcılığı altyapı katmanınızdaki çoğu kuralı ve eşlemeyi değiştirmek için kullanışlı bir yoldur, böylece varlık modeli temiz olur ve kalıcıaltyapıdan ayrılacaktır.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Akıcı API ve OnModelOluşturma yöntemi

Belirtildiği gibi, kuralları ve eşlemeleri değiştirmek için, DbContext sınıfında OnModelOluşturma yöntemini kullanabilirsiniz.

eShopOnContainers'daki sipariş mikrohizmeti, aşağıdaki kodda gösterildiği gibi gerektiğinde açık eşleme ve yapılandırma uygular.

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
            .UseHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

        //Address value object persisted as owned entity type supported since EF Core 2.0
        orderConfiguration
            .OwnsOne(o => o.Address, a =>
            {
                a.WithOwner();
            });

        orderConfiguration
            .Property<int?>("_buyerId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("BuyerId")
            .IsRequired(false);

        orderConfiguration
            .Property<DateTime>("_orderDate")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderDate")
            .IsRequired();

        orderConfiguration
            .Property<int>("_orderStatusId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderStatusId")
            .IsRequired();

        orderConfiguration
            .Property<int?>("_paymentMethodId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("PaymentMethodId")
            .IsRequired(false);

        orderConfiguration.Property<string>("Description").IsRequired(false);

        var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        // DDD Patterns comment:
        //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        orderConfiguration.HasOne<PaymentMethod>()
            .WithMany()
            .HasForeignKey("_paymentMethodId")
            .IsRequired(false)
            .OnDelete(DeleteBehavior.Restrict);

        orderConfiguration.HasOne<Buyer>()
            .WithMany()
            .IsRequired(false)
            .HasForeignKey("_buyerId");

        orderConfiguration.HasOne(o => o.OrderStatus)
            .WithMany()
            .HasForeignKey("_orderStatusId");
    }
}
```

Tüm Akıcı API eşlemelerini aynı `OnModelCreating` yöntem içinde ayarlayabilirsiniz, ancak bu kodu bölmek ve örnekte gösterildiği gibi varlık başına bir tane olmak üzere birden çok yapılandırma sınıfına sahip olması tavsiye edilir. Özellikle büyük modellerde, farklı varlık türlerini yapılandırmak için ayrı yapılandırma sınıflarına sahip olması tavsiye edilir.

Örnekteki kod birkaç açık bildirimleri ve eşleme gösterir. Ancak, EF Core kuralları bu eşlemelerin çoğunu otomatik olarak yapar, bu nedenle sizin durumunuzda gereksinim duymanız gereken gerçek kod daha küçük olabilir.

### <a name="the-hilo-algorithm-in-ef-core"></a>EF Core'da Hi/Lo algoritması

Yukarıdaki örnekte kodun ilginç bir yönü, anahtar oluşturma stratejisi olarak [Hi/Lo algoritmasını](https://vladmihalcea.com/the-hilo-algorithm/) kullanmasıdır.

Hi/Lo algoritması, değişiklik yapmadan önce benzersiz anahtarlara ihtiyacınız olduğunda kullanışlıdır. Özet olarak, Hi-Lo algoritması satırı veritabanında hemen depolamaya bağlı değilken tablo satırlarına benzersiz tanımlayıcılar atar. Bu, düzenli sıralı veritabanı kimliklerinde olduğu gibi tanımlayıcıları hemen kullanmaya başlamanızı sağlar.

Hi/Lo algoritması, ilgili veritabanı dizisinden bir dizi benzersiz iD almak için bir mekanizma açıklar. Veritabanı benzersizliği garanti ettiği için bu iDillerin kullanımı güvenlidir, böylece kullanıcılar arasında çakışme olmaz. Bu algoritma bu nedenlerle ilginçtir:

- İş Birimi deseni bozmaz.

- Veritabanına gidiş dönüş yolculuklarını en aza indirmek için toplu olarak sıralı t.c. alır.

- GuiD kullanan tekniklerden farklı olarak, insan tarafından okunabilir bir tanımlayıcı oluşturur.

EF Core, yukarıdaki `UseHiLo` örnekte gösterildiği gibi [HiLo'yu](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) yöntemle destekler.

### <a name="map-fields-instead-of-properties"></a>Özellikler yerine alanları eşle

EF Core 1.1'den beri kullanılabilen bu özellik sayesinde, sütunları doğrudan alanlara eşleyebilirsiniz. Varlık sınıfındaki özellikleri kullanmamak ve sütunları tablodan alanlara eşlemek mümkündür. Bunun için ortak bir kullanım, varlık dışından erişilmesi gerekmeyen herhangi bir iç durum için özel alanlar olacaktır.

Bunu tek alanlarla veya bir `List<>` alan gibi koleksiyonlarla da yapabilirsiniz. Etki alanı modeli sınıflarını modellemeyi tartışırken bu noktadan daha önce bahsedildi, ancak `PropertyAccessMode.Field` burada bu eşlemenin önceki kodda vurgulanan yapılandırmayla nasıl gerçekleştirildiğini görebilirsiniz.

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>ALTYAPı düzeyinde gizlenmiş EF Core'da gölge özelliklerini kullanma

EF Core'daki gölge özellikleri, varlık sınıfı modelinizde bulunmayan özelliklerdir. Bu özelliklerin değerleri ve durumları tamamen altyapı düzeyinde [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) sınıfında korunur.

## <a name="implement-the-query-specification-pattern"></a>Sorgu Belirtimi deseni uygulayın

Tasarım bölümünde daha önce de belirtildiği gibi, Sorgu Belirtimi deseni, isteğe bağlı sıralama ve sayfalama mantığıyla sorgu tanımını koyabileceğiniz yer olarak tasarlanmış etki alanı tabanlı bir tasarım desenidir.

Sorgu Belirtimi deseni bir nesnedeki bir sorguyu tanımlar. Örneğin, bazı ürünleri arayan sayfalı bir sorguyu kapsüllemek için gerekli giriş parametrelerini (pageNumber, pageSize, filtre, vb.) alan bir PagedProduct belirtimi oluşturabilirsiniz. Daha sonra, herhangi bir Depo yöntemi (genellikle bir Liste() aşırı yükleme) içinde bir IQuerySpecification kabul eder ve bu belirtime dayalı beklenen sorgu yu çalıştırın.

Genel Bir Belirtim arabirimi örneği [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb)aşağıdaki kodudur.

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

Daha sonra, genel bir belirtim taban sınıfının uygulanması aşağıdaki gibidir.

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

Aşağıdaki belirtim, sepetin kimliği veya sepetin ait olduğu alıcının kimliği verilen tek bir sepet tüzel kişiliğini yükler. Sepetin Öğeler koleksiyonunu [hevesle yükler.](https://docs.microsoft.com/ef/core/querying/related-data)

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

Ve son olarak, genel bir EF Deposu'nun belirli bir varlık türü T ile ilgili verileri filtrelemek ve istekli yüklemek için böyle bir belirtimi nasıl kullanabileceğini aşağıda görebilirsiniz.

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

Filtreleme mantığını kapsüllemenin yanı sıra, belirtim, hangi özelliklerin doldurulması gerektiği de dahil olmak üzere döndürülecek verilerin şeklini de belirtebilir.

Bir depodan dönmenizi `IQueryable` önermesek de, bunları bir dizi sonuç oluşturmak için depo içinde kullanmak son derece iyi bir şey. Yukarıdaki Liste yönteminde kullanılan ve sorguyu son `IQueryable` satırda belirtim ölçütleri ile yürütmeden önce sorgunun içerir listesini oluşturmak için ara ifadeleri kullanan bu yaklaşımı görebilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Tablo Eşleme** \
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- **Entity Framework Core ile anahtar oluşturmak için HiLo'u kullanın** \
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- **Destek Alanları** \
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- **Steve Smith' i. Varlık Çerçeve Çekirdeğinde Kapsüllenmiş Koleksiyonlar** \
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- **Gölge Özellikleri** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Belirtim deseni** \
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> [Önceki](infrastructure-persistence-layer-design.md)
> [Sonraki](nosql-database-persistence-infrastructure.md)
