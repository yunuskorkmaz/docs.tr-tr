---
title: Entity Framework Core ile altyapı kalıcılık katmanını uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Entity Framework Core kullanarak altyapı kalıcılığı katmanının uygulama ayrıntılarını keşfedebilirsiniz.
ms.date: 10/08/2018
ms.openlocfilehash: b70ede6b47cbf990d0435aef841416c68f6439b4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737904"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Altyapı kalıcılığı katmanını Entity Framework Core ile uygulama

SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanları kullandığınızda önerilen bir yaklaşım, Entity Framework (EF) temelinde Kalıcılık katmanını uygulamaktır. EF, LINQ 'i destekler ve modelinize yönelik kesin olarak belirlenmiş nesneler sağlar ve veritabanınıza basit kalıcı hale getirir.

Entity Framework .NET Framework bir parçası olarak uzun bir geçmişi vardır. .NET Core kullandığınızda, .NET Core ile aynı şekilde Windows veya Linux üzerinde çalışan Entity Framework Core de kullanmalısınız. EF Core, daha küçük bir ayak ya da performans açısından önemli geliştirmelerle uygulanan Entity Framework tamamen yeniden yazma işlemi olur.

## <a name="introduction-to-entity-framework-core"></a>Entity Framework Core giriş

Entity Framework (EF) Core, popüler Entity Framework veri erişim teknolojisinin basit, genişletilebilir ve platformlar arası bir sürümüdür. Bu, m2016 ' de .NET Core ile tanıtılmıştır.

EF Core giriş Microsoft belgelerinde zaten mevcut olduğundan, bu bilgilere yönelik bağlantılar sağlıyoruz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Entity Framework Core** \
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- **Visual Studio 'yu kullanarak ASP.NET Core ve Entity Framework Core** kullanmaya başlama \
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- **DbContext sınıfı** \
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- **EF Core & EF6. x \ karşılaştırın**
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Bir DDD perspektifinden Entity Framework Core altyapısı

DDD türünde, önemli bir özellik olan POCO etki alanı varlıklarını, POCO *kodu-ilk varlıkları*olarak EF terimlerinde de bilinen bir şekilde kullanma olanağıdır. POCO etki alanı varlıklarını kullanıyorsanız, etki alanı model sınıflarınız Kalıcılık [Ignorance](https://deviq.com/persistence-ignorance/) ve [altyapı Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) ilkelerine göre Kalıcılık-Ignorant ' dir.

DDD desenleri başına, varlık sınıfı içinde etki alanı davranışını ve kurallarını kapsüllemek gerekir, bu sayede herhangi bir koleksiyona erişirken ınvaryantlar, doğrulamaları ve kuralları kontrol edebilir. Bu nedenle, alt varlıkların veya değer nesnelerinin koleksiyonlarına genel erişime izin vermek için DDD 'da iyi bir uygulama değildir. Bunun yerine, alanlar ve özellik koleksiyonlarınızın nasıl ve ne zaman güncelleştirileceğini ve ne zaman meydana gelir ve eylemlerin ne zaman gerçekleşeceğini denetleyen yöntemleri göstermek istersiniz.

EF Core 1,1 ' den itibaren bu DDD gereksinimlerini karşılayacak şekilde, varlıklarınızda ortak özellikler yerine düz alanlara sahip olabilirsiniz. Bir varlık alanının dışarıdan erişilebilir olmasını istemiyorsanız, bir özellik yerine yalnızca özniteliği veya alanı oluşturabilirsiniz. Özel özellik ayarlayıcıları da kullanabilirsiniz.

Benzer bir şekilde, artık `IReadOnlyCollection<T>`olarak yazılmış bir ortak özelliği kullanarak koleksiyonlara salt okuma erişimine sahip olabilirsiniz. Bu, bir özel alan üyesi tarafından (örneğin, bir `List<T>`gibi), kalıcılık için EF 'i temel alan varlıkınızda desteklenir. Entity Framework önceki sürümleri, üst varlık sınıfını kullanan herhangi bir geliştiricinin özellik koleksiyonları aracılığıyla öğe eklemesine veya kaldırmasına olanak tanıyan `ICollection<T>`desteklemek için gerekli koleksiyon özelliklerinin. Bu olasılık, DDD 'daki önerilen desenlere karşı bir yaklaşımlar.

Aşağıdaki kod örneğinde gösterildiği gibi, salt okunurdur `IReadOnlyCollection<T>` nesnesini kullanıma alırken özel bir koleksiyon kullanabilirsiniz:

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

`OrderItems` özelliğine yalnızca `IReadOnlyCollection<OrderItem>`kullanılarak salt okunurdur erişilebilir. Bu tür salt okunurdur, bu nedenle normal dış güncelleştirmelere karşı korunur.

EF Core, etki alanı modelini "kirmadan", etki alanı modelini fiziksel veritabanıyla eşlemek için bir yol sağlar. Bu saf .NET POCO kodudur çünkü eşleme eylemi Kalıcılık katmanında uygulanmıştır. Bu eşleme eyleminde, alanları veritabanına eşlemeyi yapılandırmanız gerekir. `OrderingContext` ve `OrderEntityTypeConfiguration` sınıfından `OnModelCreating` yönteminin aşağıdaki örneğinde, `SetPropertyAccessMode` çağrısı EF Core `OrderItems` özelliğine kendi alanı aracılığıyla erişmesini söyler.

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

Özellikler yerine alanları kullandığınızda `OrderItem` varlığı, tıpkı bir `List<OrderItem>` özelliğine sahip gibi kalıcıdır. Ancak, sıraya yeni öğeler eklemek için `AddOrderItem` yöntemi olan tek bir erişimci sunar. Sonuç olarak, davranış ve veriler birlikte birbirlerine bağlanır ve etki alanı modelini kullanan tüm uygulama kodları boyunca tutarlı olacaktır.

## <a name="implement-custom-repositories-with-entity-framework-core"></a>Entity Framework Core ile özel depolar uygulama

Uygulama düzeyinde, bir depo, aşağıdaki sınıfta gösterildiği gibi, güncelleştirmeleri gerçekleştirirken bir iş birimi (EF Core 'de DBContext) tarafından koordine edilen veri Kalıcılık koduna sahip bir sınıftır:

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

Isusırepository arabiriminin, etki alanı modeli katmanından bir sözleşme olarak geldiğini unutmayın. Ancak, depo uygulama kalıcı ve altyapı katmanında yapılır.

EF DbContext, Oluşturucu aracılığıyla bağımlılık ekleme yoluyla gelir. Aynı HTTP istek kapsamındaki birden çok depo arasında paylaşılır ve IOC kapsayıcısında varsayılan yaşam süresi (`ServiceLifetime.Scoped`) ile (Ayrıca `services.AddDbContext<>`açıkça ayarlanabilir).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Bir depoda uygulanacak Yöntemler (güncelleştirmeler veya işlemler ve sorgular)

Her bir depo sınıfı içinde, ilgili toplamanın içerdiği varlıkların durumunu güncelleştiren Kalıcılık yöntemlerini koymanız gerekir. Bir toplama ve ilgili depo arasında bire bir ilişki olduğunu unutmayın. Bir toplama kök varlık nesnesinin EF grafiğinde gömülü alt varlıkların olabileceğini göz önünde bulundurun. Örneğin, bir alıcı ilgili alt varlıklar olarak birden fazla ödeme yöntemine sahip olabilir.

EShopOnContainers 'da, mikro hizmet sıralaması için yaklaşım ayrıca CQS/CQRS 'yi temel aldığı için sorguların çoğu özel depolarda uygulanmaz. Geliştiriciler, toplamalar tarafından uygulanan kısıtlamalar, toplama başına özel depolar ve genel olarak DDD, sunum katmanı için gereken sorguları ve birleştirmeleri oluşturma özgürlüğü sunar. Bu kılavuzda önerilen özel depoların çoğu, birkaç güncelleştirme ya da işlem yöntemine sahiptir ancak yalnızca güncelleştirilecek verileri almak için gereken sorgu yöntemleri vardır. Örneğin, BuyerRepository deposu bir Findadsync yöntemi uygular, çünkü uygulamanın siparişle ilgili yeni bir alıcı oluşturmadan önce belirli bir alıcının mevcut olup olmadığını bilmesi gerekir.

Ancak, sunum katmanına veya istemci uygulamalarına gönderilmek üzere verileri almak için gerçek sorgu yöntemleri,, kaber kullanılarak esnek sorgulara dayanan CQRS sorgularında belirtilen şekilde uygulanır.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Özel bir depoyu kullanarak doğrudan EF DbContext kullanma

Entity Framework DbContext sınıfı Iş ve depo desenlerini temel alır ve doğrudan kodunuzdan (örneğin, bir ASP.NET Core MVC denetleyicisinden) kullanılabilir. Bu, eShopOnContainers içindeki CRUD Katalog mikro hizmetinde olduğu gibi, en basit kodu oluşturabileceğiniz yoldur. En basit kodun mümkün olmasını istediğiniz durumlarda, çoğu geliştirici olduğu için DbContext sınıfını doğrudan kullanmak isteyebilirsiniz.

Ancak, özel depoları uygulamak, daha karmaşık mikro hizmetler veya uygulamalar uygularken çeşitli avantajlar sağlar. Çalışma birimi ve depo desenlerinin, uygulama ve etki alanı model katmanlarından ayrılması için altyapı kalıcılığı katmanını kapsüllemek üzere tasarlanmıştır. Bu desenleri uygulamak, veritabanına erişimi taklit eden sahte depoların kullanımını kolaylaştırabilir.

Şekil 7-18 ' de, bu depoları daha kolay hale getirmek için depoları kullanma (doğrudan EF DbContext kullanarak) ile ilgili farklılıkları görebilirsiniz.

![İki depodaki bileşenlerin ve veri akışının gösterildiği diyagram.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

**Şekil 7-18**. Özel depoları kullanma, düz bir DbContext

Şekil 7-18, özel bir depoyu kullanmanın, depoyu test ederek testi kolaylaştırmak için kullanılabilecek bir soyutlama katmanı ekler. Mocking için birden çok alternatif vardır. Yalnızca depoların tamamını veya bir bütün çalışma birimini sahte bir şekilde yapılandırabilirsiniz. Genellikle depolarda bulunan depolar yeterlidir ve tüm iş birimi için soyut ve anlamlı olan karmaşıklık genellikle gerekli değildir.

Daha sonra uygulama katmanına odaklandığımızda, bağımlılık ekleme 'nın ASP.NET Core içinde nasıl çalıştığını ve depoları kullanırken nasıl uygulandığını görürsünüz.

Kısacası, özel depolar, veri katmanı durumundan etkilenmeyenler olan birim testleri ile kodu daha kolay test edebilmesini sağlar. Gerçek veritabanına aynı zamanda Entity Framework aracılığıyla erişen testler çalıştırırsanız, bunlar birim testleri, ancak çok daha yavaş olan tümleştirme sınamalarından değildir.

DbContext 'i doğrudan kullanıyorsanız, birim testleri için öngörülebilir verilerle bellek içi SQL Server kullanarak birim testlerini bir veya daha fazla şekilde çalıştırmanız gerekir. Ancak DbContext 'e göz at veya sahte verilerin denetlenmesi, depo düzeyinde sahte işlem 'ten daha fazla çalışma gerektirir. Kuşkusuz, her zaman MVC denetleyicilerini test edebilirsiniz.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>IFC kapsayıcıda EF DbContext ve IUnitOfWork örnek ömrü

`DbContext` nesnesi (bir `IUnitOfWork` nesnesi olarak gösterilir), aynı HTTP istek kapsamındaki birden çok depo arasında paylaşılmalıdır. Örneğin, yürütülmekte olan işlem birden çok toplama ile uğraşmak veya birden çok depo örneği kullandığınız için geçerlidir. `IUnitOfWork` arabirimin, EF Core bir tür değil, etki alanı katmanınızdaki bir parçası olduğunu bahsetmek de önemlidir.

Bunu yapmak için, `DbContext` nesnesinin örneğinin hizmet ömrü ServiceLifetime. kapsamlıdır olarak ayarlanmalıdır. Bu, ASP.NET Core Web API projenizdeki `Startup.cs` dosyasının ConfigureServices yönteminden IBC kapsayıcısındaki `services.AddDbContext` bir `DbContext` kaydederken varsayılan yaşam süresidir. Aşağıdaki kod bunu göstermektedir.

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

DbContext örnek oluşturma modu ServiceLifetime. geçici veya ServiceLifetime. Singleton olarak yapılandırılmamalıdır.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>IoC kapsayıcıınızda depo örneği ömrü

Benzer şekilde, deponun ömrü genellikle kapsam olarak ayarlanmalıdır (Autofac içinde InstancePerLifetimeScope). Ayrıca geçici (Autofac ' de ınstanceperdependency) olabilir, ancak ağınız kapsamlı ömür kullanılırken belleği dikkate alarak daha verimli olacaktır.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Depo için tek yaşam süresinin kullanılması, DbContext kapsam (InstancePerLifetimeScope) yaşam süresi (bir DBContext için varsayılan yaşam süreleri) olarak ayarlandığında ciddi eşzamanlılık sorunları oluşmasına neden olabileceğini unutmayın.

### <a name="additional-resources"></a>Ek kaynaklar

- **Bir ASP.NET MVC uygulamasında depo ve Iş deseni birimi uygulama** \
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- **Jonathan Allen. Entity Framework, kaber ve zincirle depo deseninin uygulama stratejileri** \
  <https://www.infoq.com/articles/repository-implementation-strategies>

- **Cesar de La Torre. Autofac IoC kapsayıcı örneği kapsamları ile ASP.NET Core IOC kapsayıcı hizmeti yaşam sürelerinin karşılaştırması** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a>Tablo eşleme

Tablo eşleme, sorgulanacak tablo verilerini tanımlar ve veritabanına kaydedilir. Daha önce etki alanı varlıklarının (örneğin, bir ürün veya sipariş etki alanı) ilgili veritabanı şeması oluşturmak için nasıl kullanılabileceğini gördünüz. EF, *kural*kavramı etrafında kesin olarak tasarlanmıştır. Kurallar, "bir tablonun adı ne olacak?" gibi soruları ele alacak. or "birincil anahtar nedir?" Kurallar genellikle geleneksel adlara dayalıdır — Örneğin, birincil anahtarın kimlik ile biten bir özellik olması normaldir.

Kurala göre, her varlık türetilmiş bağlamda varlığı sunan `DbSet<TEntity>` özelliği ile aynı ada sahip bir tabloya eşlenecek şekilde ayarlanır. Verilen varlık için `DbSet<TEntity>` değeri sağlanmazsa, sınıf adı kullanılır.

### <a name="data-annotations-versus-fluent-api"></a>Veri ek açıklamaları ve akıcı API

Birçok ek EF Core kuralı vardır ve bunların çoğu, Onmodeloluþturma yöntemi içinde uygulanan veri ek açıklamaları veya Floent API kullanılarak değiştirilebilir.

Veri ek açıklamaları, bir DDD bir görünüm noktasından daha kolay bir şekilde olan varlık modeli sınıflarının kendileri üzerinde kullanılmalıdır. Bunun nedeni, modelinizi altyapı veritabanıyla ilgili veri ek açıklamalarıyla kirmaktan kaynaklanır. Öte yandan, akıcı API, veri Kalıcılık altyapısı katmanınızdaki birçok kuralı ve eşlemeyi değiştirmek için kullanışlı bir yoldur. bu nedenle, varlık modeli temiz ve kalıcılık altyapısından ayrılır.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Akıcı API ve Onmodeloluþturma yöntemi

Belirtildiği gibi, kuralları ve eşlemeleri değiştirmek için DbContext sınıfında Onmodeloluþturma yöntemini kullanabilirsiniz.

EShopOnContainers 'daki sıralama mikro hizmeti, gerektiğinde aşağıdaki kodda gösterildiği gibi açık eşleme ve yapılandırma uygular.

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

Aynı Onmodeloluþturma yöntemi içindeki tüm akıcı API eşlemelerini ayarlayabilirsiniz, ancak örnekte gösterildiği gibi, bu kodu bölümlemek ve varlık başına bir tane olmak üzere birden çok yapılandırma sınıfı olması önerilir. Özellikle büyük modeller için, farklı varlık türlerini yapılandırmak üzere ayrı yapılandırma sınıfları olması önerilir.

Örnekteki kodda birkaç açık bildirim ve eşleme gösterilmektedir. Ancak, EF Core kuralları bu eşlemelerin çoğunu otomatik olarak bir şekilde yapın, bu nedenle, büyük/küçük harfli ihtiyacınız olan gerçek kod daha küçük olabilir.

### <a name="the-hilo-algorithm-in-ef-core"></a>EF Core 'daki Hi/Lo algoritması

Önceki örnekteki kodun ilginç bir yönü, anahtar oluşturma stratejisi olarak [Hi/Lo algoritmasını](https://vladmihalcea.com/the-hilo-algorithm/) kullanmamasıdır.

Merhaba/Lo algoritması, değişiklikleri uygulamadan önce benzersiz anahtarlara ihtiyacınız olduğunda faydalıdır. Özet olarak, Hi-Lo algoritması, satırı veritabanında depolamaya bağlı olarak tablo satırlarına benzersiz tanımlayıcılar atar. Bu, normal sıralı veritabanı kimlikleri gibi olduğu gibi, tanımlayıcıları hemen kullanmaya başlayabilmenizi sağlar.

Merhaba/Lo algoritması, ilgili bir veritabanı sırasından benzersiz kimlik toplu kimliklerini alma mekanizmasını açıklar. Veritabanı benzersizlik sağladığından, bu kimlikler kullanım açısından güvenlidir, bu nedenle kullanıcılar arasında çakışma olmayacaktır. Bu algoritma şu nedenlerle ilginç olur:

- Iş deseninin birimini bozmaz.

- Veritabanına gidiş dönüşleri en aza indirmek için dizi kimliklerini toplu olarak alır.

- GUID kullanan tekniklerin aksine, okunabilir bir tanımlayıcı oluşturur.

EF Core, önceki örnekte gösterildiği gibi, Forsqlserverusesequencechild o yöntemiyle birlikte bulunan ' [yi destekler.](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm)

### <a name="map-fields-instead-of-properties"></a>Özellikler yerine harita alanları

Bu özellik ile EF Core 1,1 ' den bu yana, sütunları doğrudan alanlarla eşleyebilirsiniz. Varlık sınıfında özellikler kullanılamaz ve yalnızca tablodaki sütunları alanlarla eşlemek mümkündür. İçin ortak bir kullanım, varlığın dışından erişilmesi gerekmeyen herhangi bir iç durum için özel alanlar olacaktır.

Bunu tek alanlarla veya `List<>` alanı gibi koleksiyonlarla yapabilirsiniz. Bu nokta, etki alanı model sınıflarını modelleyen daha önce bahsedildiği halde, bu eşlemenin önceki kodda vurgulanan `PropertyAccessMode.Field` yapılandırmasıyla nasıl gerçekleştirileceğini görebilirsiniz.

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Altyapı düzeyinde gizlenen EF Core gölge özelliklerini kullanın

EF Core 'daki gölge özellikler, varlık sınıfı modelinizde bulunmayan özelliklerdir. Bu özelliklerin değerleri ve durumları, yalnızca altyapı düzeyindeki [Changetracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) sınıfında saklanır.

## <a name="implement-the-query-specification-pattern"></a>Sorgu belirtim modelini uygulama

Daha önce tasarım bölümünde sunulan sorgu belirtim şekli, isteğe bağlı sıralama ve sayfalama mantığı ile bir sorgunun tanımını koyabileceğiniz yer olarak tasarlanan bir etki alanı odaklı tasarım modelidir.

Sorgu belirtim stili bir nesne içindeki bir sorguyu tanımlar. Örneğin, bazı ürünleri arayan bir disk belleğine alınmış sorguyu kapsüllemek için gerekli giriş parametrelerini (pageNumber, pageSize, filtre, vb.) alan bir PagedProduct belirtimi oluşturabilirsiniz. Ardından, herhangi bir depo yönteminde (genellikle bir liste () aşırı yüklemesi) bir ıqueryspecification kabul eder ve beklenen sorguyu bu belirtiye göre çalıştırır.

Genel belirtim arabirimine bir örnek, [Eshoponweb](https://github.com/dotnet-architecture/eShopOnWeb)'den aşağıdaki koddur.

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

Daha sonra, Genel belirtim temel sınıfının uygulanması aşağıda verilmiştir.

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

Aşağıdaki belirtim, sepetin KIMLIĞI veya sepetinin ait olduğu alıcının KIMLIĞI verildiğinde tek bir sepet varlığı yükler. Sepetin Items toplamasını yeniden [yükler](https://docs.microsoft.com/ef/core/querying/related-data) .

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

Son olarak, bir genel EF deposunun belirli bir varlık türü T ile ilgili verileri filtrelemek ve bunlara göre yüklemek için bu belirtimi nasıl kullanabileceği hakkında daha fazla bilgi alabilirsiniz.

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

Filtre mantığını kapsüllemenin yanı sıra belirtim, doldurulacak verilerin şeklini belirtebilir ve bu da doldurulacak özellikler de dahil olmak üzere döndürülür.

Bir depodan IQueryable döndürmek önerilmese de, bir dizi sonuç oluşturmak için bunları depoda kullanmak çok güzel. Bu yaklaşımı, yukarıdaki List yönteminde, sorgunun son satırdaki belirtim ölçütlerine sahip Sorguyu yürütmeden önce sorgunun dahil olduğu bir sorgu listesini oluşturmak için kullandığını görebilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Tablo eşleme** \
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- **Entity Framework Core \ anahtar oluşturmak Için Tepo kullanın**
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- **Alanları yedekleme** \
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- **Steve Smith. Entity Framework Core \ kapsüllenmiş koleksiyonlar**
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- **Gölge özellikleri** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Belirtim deseninin** \
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> [Önceki](infrastructure-persistence-layer-design.md)
> [İleri](nosql-database-persistence-infrastructure.md)
