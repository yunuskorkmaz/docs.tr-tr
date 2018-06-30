---
title: Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 6003252d7e87428c7f954b57c3b67a041e3f3b15
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106482"
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama

SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanları kullandığınızda, önerilen yaklaşım Entity Framework (EF üzerinde) temel saklama katmanını uygulamaktır. EF LINQ destekler ve güçlü şekilde yazılan nesnelerin, model, aynı zamanda, veritabanına Basitleştirilmiş Kalıcılık sağlar.

Entity Framework .NET Framework'ün bir parçası olarak uzun bir geçmişi vardır. .NET Core kullandığınızda, Windows veya Linux .NET Core aynı şekilde çalıştırır Entity Framework Çekirdek kullanmanız gerekir. EF çekirdeği çok daha küçük bir yer ve önemli performans geliştirmeleri ile uygulanan Entity Framework'ün tam bir yeniden yazma olur.

## <a name="introduction-to-entity-framework-core"></a>Entity Framework Çekirdek giriş

Hafif, Genişletilebilir, Entity Framework (EF) çekirdeği olur ve platformlar arası sürümü popüler Entity Framework verilerine erişim teknolojisini. Mid-2016'da ile .NET Core sunulmuştur.

EF çekirdek giriş zaten Microsoft belgelerinde mevcut olduğundan, burada yalnızca bu bilgilere bağlantılar sunuyoruz.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Entity Framework Çekirdek**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

-   **ASP.NET Core ve Entity Framework Visual Studio kullanarak çekirdek ile çalışmaya başlama**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **DbContext sınıfı**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **EF çekirdek & EF6.x karşılaştırma**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Entity Framework Çekirdek altyapısında DDD açısından

Bir DDD açısından bakıldığında, önemli bir özelliği EF, POCO olarak EF terminolojisi olarak da bilinen POCO etki alanı varlıklar kullanma yeteneğini olan *kod ilk varlıklar*. POCO etki alanı varlıklar kullanırsanız, etki alanı model sınıflarınızı Kalıcılık-aşağıdaki kullanmayan, [Kalıcılık kullanmayan](http://deviq.com/persistence-ignorance/) ve [altyapı kullanmayan](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri.

DDD desenleri etki alanı davranışını ve varlık sınıfı kendisini içinde kurallar, invariants, doğrulama ve kurallardan herhangi bir koleksiyonu erişirken denetleyebilirsiniz şekilde kapsülleyen. Bu nedenle, bu varlık veya değer nesnelerini alt koleksiyonlar genel erişime izin vermek için DDD iyi bir uygulama değil. Bunun yerine, bu durum oluştuğunda nasıl ve ne zaman alanları ve özellik koleksiyonları güncelleştirilebilir, denetleme yöntemleri ve hangi davranışı ve Eylemler gerçekleşeceğini kullanıma sunmak istediğiniz.

EF çekirdek 1.1 itibaren bu DDD gereksinimleri karşılamak için düz alanları varlıklarınızı ortak özellikleri yerine de olabilir. Bir varlık alanı dışarıdan erişilebilir olmasını istemiyorsanız, yalnızca özellik veya alan bir özellik yerine oluşturabilirsiniz. Özel özellik ayarlayıcıları de kullanabilirsiniz.

Benzer şekilde, şimdi salt okunur koleksiyonlara olarak yazılan ortak bir özelliğini kullanarak erişebilirsiniz `IReadOnlyCollection<T>`, koleksiyon için bir özel alan üye tarafından desteklenen (gibi bir `List<T>`) varlığınızdaki üzerinde EF kalıcılığını kullanır. Entity Framework'ün önceki sürümlerini koleksiyon özellikleri desteklemek için gereken `ICollection<T>`, üst varlık sınıfı kullanarak herhangi bir geliştirici ekleme veya onun özellik koleksiyonları aracılığıyla öğeleri kaldırmak istediğinizi. Bu olasılığı DDD önerilen düzenleri karşı olacaktır.

Salt okunur gösterme sırasında özel bir koleksiyonunu kullanabilirsiniz `IReadOnlyCollection<T>` nesnesi, aşağıdaki kod örneğinde gösterildiği gibi:

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

Unutmayın `OrderItems` özelliği yalnızca erişilebilir salt okunur kullanarak olarak `IReadOnlyCollection<OrderItem>`. Normal dış güncelleştirmeleri karşı korumalı şekilde bu tür salt okunurdur. 

EF çekirdek "etki alanı modeli contaminating olmadan" fiziksel veritabanı etki alanı modeline eşlemek için bir yol sağlar. Eşleme eylem Kalıcılık katmanında uygulanır saf .NET POCO kod, demektir. Bu eşleme eylemde alanları veritabanı eşleme yapılandırmanız gerekir. Bir OnModelCreating metodunun aşağıdaki örnekte vurgulanmış kodu EF OrderItems özelliği aracılığıyla kendi alana erişmek için çekirdek söyler.

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

Alanları yerine özellikleri kullandığınızda, yalnızca, bir liste sahipmiş ÖgeSipariş varlık kalıcı&lt;ÖgeSipariş&gt; özelliği. Ancak, tek bir erişimci sunan `AddOrderItem` siparişe yeni öğeler eklemek için yöntem. Sonuç olarak, davranışı ve veri birbirine bağlıdır ve etki alanı modeli kullanan herhangi bir uygulama kodu tutarlı olur.

## <a name="implementing-custom-repositories-with-entity-framework-core"></a>Entity Framework Çekirdek ile özel depoları uygulama

Uygulama düzeyinde bir iş (EF çekirdek içinde DBContext) birimine tarafından denetlenen veri kalıcılığı kodunu yalnızca bir sınıfla depodur güncelleştirmeleri, aşağıdaki sınıfında gösterildiği gibi gerçekleştirirken:

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

IBuyerRepository arabirimi bir sözleşme olarak etki alanı modeli katmandan geldiğini unutmayın. Ancak, depo uygulaması Kalıcılık ve altyapı katman yapılır.

Oluşturucu bağımlılık ekleme kullanılarak aracılığıyla EF DbContext gelir. Varsayılan ömrü (ServiceLifetime.Scoped) (aynı zamanda açıkça hizmetleriyle ayarlanabilir. IOC container sayesinde aynı HTTP istek kapsamı içinde birden çok depoları arasında paylaşılan AddDbContext&lt;&gt;).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Bir havuzda (güncelleştirmeleri veya sorgular ve işlemler) uygulamaya yönelik yöntemleri

Her bir havuz sınıfı içinde kendi ilgili toplama tarafından bulunan varlıkların durumunu güncelleştirme Kalıcılık yöntemleri moduna geçirmelisiniz. Bir toplama ve ilgili deposu arasındaki birebir ilişki olduğunu unutmayın. Birleşik kök varlık nesne EF grafik alt varlıkları katıştırılmış dikkate alın. Örneğin, bir alıcı birden çok ödeme yöntemi ilgili alt varlıkları sahip olabilir.

Sıralama mikro hizmet eShopOnContainers içinde bir yaklaşım CQS/CQRS üzerinde dayalı olduğundan çoğu sorgu içinde özel depoları uygulanmadı. Geliştiriciler için sunu katmanı toplamalar, toplama ve DDD başına özel depoları tarafından genel olarak uygulanan kısıtlamalar ihtiyaç duydukları birleştirmeler ve sorguları oluşturmak için serbestçe. Bu kılavuzda önerilen özel depoları çoğunu birkaç güncelleştirme veya işlem yöntemlerini sahip ancak güncelleştirilecek veri için sorgu yöntemler gerekiyor. Örneğin, uygulamanın belirli bir alıcı sırasıyla ilişkili yeni bir alıcı oluşturmadan önce mevcut olup olmadığını bilmek gerektiğinden BuyerRepository depo zaman uyumsuz olarak bulur yöntemi uygular.

Ancak, sunu katmanı veya istemci uygulamalara göndermek için veri almak için gerçek sorgu yöntemleri, Dapper kullanarak esnek sorguları temel alan CQRS sorgular bölümünde belirtildiği gibi uygulanır.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>EF DbContext kullanarak doğrudan karşı özel bir depo kullanma

Entity Framework DbContext sınıfına iş birimi ve depo düzenlerini esas alarak ve doğrudan kodunuzdan, gibi bir ASP.NET Core MVC denetleyicisinden kullanılabilir. Diğer bir deyişle şekilde CRUD katalog mikro hizmet eShopOnContainers içinde olduğu gibi basit kod oluşturabilirsiniz. Çoğu geliştiricinin gibi basit kod olası istediğiniz durumlarda, doğrudan bir DbContext sınıfı kullanmak isteyebilirsiniz.

Ancak, özel depoları uygulama birkaç avantaj daha karmaşık mikro hizmetler veya uygulamalar uygularken'sağlar. İş birimi ve depo desenleri uygulama ve etki alanı modeli katmanları ayrılmış şekilde altyapı saklama katmanını kapsüllemek için tasarlanmıştır. Bu desenleri uygulama veritabanına erişimi benzetimi sahte depoları kullanımını kolaylaştırabilir.

Şekil 9-18'de bu depoları mock kolaylaştırmak depoları kullanarak karşılaştırması (EF DbContext doğrudan kullanarak) depoları kullanmayan arasındaki farklar görebilirsiniz.

![](./media/image19.png)

**Şekil 9-18**. Düz bir DbContext karşı özel depoları kullanma

Mocking, birden çok alternatifleri vardır. Yalnızca depoları mock veya tam bir iş birimine mock. Genellikle yalnızca depoları mocking yeterli olduğunu ve soyut ve tam bir iş birimine mock karmaşıklığını genellikle gerekli değildir.

Daha sonra biz uygulama katmanına odaklanmanıza, bağımlılık ekleme ASP.NET Core nasıl çalıştığını ve nasıl depoları kullanırken uygulandığı görürsünüz.

Kısacası, özel depoları kodu daha kolay veri katmanı durumuna göre etkilenmez birim testleri test olanak sağlar. Ayrıca asıl veritabanını Entity Framework erişim testler çalıştırırsanız, bunlar birim testleri ancak çok daha yavaş tümleştirme testleri olup olmadığı.

DbContext doğrudan kullanıyorsanız, olurdu tek seçim için birim testleri tahmin edilebilir verilerle bir bellek içi SQL Server kullanarak birim testlerini çalıştırmak için olacaktır. Depo düzeyinde aynı şekilde sahte nesneler ve sahte veri denetimi mümkün olmayacaktır. Elbette, MVC denetleyicileri her zaman test edebilirsiniz.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>IOC kapsayıcısında EF DbContext ve IUnitOfWork örneği ömrü

(Bir IUnitOfWork nesne olarak gösterilen) DbContext nesnesi aynı HTTP istek kapsamı içinde birden çok depoları arasında paylaşılan gerekebilir. Yürütülen işlem birden çok toplamalar veya yalnızca gerekir dağıttığınızda Örneğin, bu durum geçerlidir birden çok havuz örnekleri kullandığından. IUnitOfWork arabirimi EF çekirdek türü, etki alanı katmanının bir parçası olduğunu belirttiğinizden önemlidir.

Bunu yapmak için DbContext nesnesinin örneği hizmet yaşam süresi ayarlamak için ServiceLifetime.Scoped sahip olması gerekir. Ne zaman bir DbContext ile kayıt hizmetleri varsayılan yaşam süresi budur. AddDbContext, IOC kapsayıcısında ASP.NET çekirdek Web API projenizdeki haline dosyasının ConfigureServices yönteminden. Aşağıdaki kod bunu göstermektedir.

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

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>IOC kapsayıcı depo örneği yaşam süresi

Benzer şekilde, deponun yaşam süresi genellikle kapsamlı (Autofac içinde InstancePerLifetimeScope) olarak ayarlanmalıdır. Ayrıca olabilir kapsamlı ömrü kullanırken geçici (InstancePerDependency Autofac içinde), hizmetiniz ancak bakımından bellekte daha etkili olacaktır.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

DbContext ayarlandığında depo için singleton ömrü kullanarak ciddi eşzamanlılık sorunlara neden olabilecek unutmayın (InstancePerLifetimeScope) yaşam süresi (varsayılan yaşam süreleri bir DBContext) kapsamlı.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Bir ASP.NET MVC uygulamasındaki depo ve iş desenleri ölçü uygulama**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen. Depo düzeni Entity Framework, Dapper, uygulama stratejileri ve zinciri**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Cesar de la Torre. ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamları ile karşılaştırma**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>Tablo eşlemesi

Tablo eşlemesi gelen Sorgulanacak tablo verileri tanımlar ve veritabanına kaydedilir. Daha önce ilgili veritabanı şeması oluşturmak için etki alanı varlıkları (örneğin, bir ürün veya sırasını etki alanı)'ın nasıl kullanılabileceğini gördünüz. EF kavramı kesinlikle tasarlanmış *kuralları*. "Ne bir tablonun adı olacak?" gibi kuralları adresi soruları veya "hangi özellik birincil anahtar?" Kuralları genellikle geleneksel adlarına dayalı — Örneğin, tipik kimliği ile biten bir özellik olarak birincil anahtarı.

Kurala göre her bir varlık DbSet aynı ada sahip bir tabloya eşlemek için ayarlanır&lt;TEntity&gt; türetilmiş bağlam varlıkta gösteren özelliği. Hiçbir DbSet,&lt;TEntity&gt; değerdir verilen varlık için kullanılan sınıf adı sağlanan.

### <a name="data-annotations-versus-fluent-api"></a>Veri ek açıklamaları Fluent API'si ile karşılaştırması

Birçok ek EF çekirdek kuralları vardır ve bunların çoğu veri ek açıklamaları veya OnModelCreating metodunun içinde uygulanan Fluent API kullanılarak değiştirilebilir.

Veri ek açıklamaları açısından bir DDD daha kullanışsız bir yol olduğu varlık modeli sınıflarında kendileri kullanılmalıdır. Altyapı veritabanı ile ilgili veri ek açıklamaları ile modelinizi contaminating olmasıdır. Diğer taraftan, Fluent API varlık modeli temiz ve kalıcılığı altyapısından ayrılmış olması için çoğu kuralları ve veri saklama altyapı katmanını içinde eşlemelerini değiştirmek için uygun bir yoludur.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Fluent API ve OnModelCreating yöntemi

Kuralları ve eşlemelerini değiştirmek için belirtildiği gibi DbContext sınıfında OnModelCreating metodunun kullanabilirsiniz. 

Sıralama mikro hizmet eShopOnContainers içinde açık eşleme ve yapılandırma, gerekli olduğunda, aşağıdaki kodda gösterildiği gibi uygular.

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

Aynı OnModelCreating metodunun içinde tüm Fluent API eşlemelerini ayarlayabilir, ancak bu örnekte gösterildiği gibi bu kodu bölüm ve birden çok yapılandırma sınıfları, varlık, her bir sahip önerilir. Özellikle özellikle büyük modelleri için farklı varlık türlerinin yapılandırılması için ayrı yapılandırma sınıfları olması önerilir.

Örnek kodda birkaç açık bildirimler ve eşleme gösterir. Sizin durumunuzda gereken gerçek bir kod küçük olabilir ancak EF çekirdek kuralları bu eşlemeleri çoğunu otomatik olarak, bunun.


### <a name="the-hilo-algorithm-in-ef-core"></a>EF çekirdek Hi/Lo algoritması

Bir ilginç Yukarıdaki örnekteki kod bunu kullandığını yönüdür [Hi/Lo algoritması](https://vladmihalcea.com/the-hilo-algorithm/) anahtar oluşturma stratejisini olarak.

Hi/Lo algoritması benzersiz anahtarlar gerektiğinde kullanışlıdır. Bir Özet, Hi-Aet.aet algoritması satır veritabanında hemen depolamayın sırada bağlı olarak tablo satırlarının benzersiz tanımlayıcıları atar. Bu, normal sıralı veritabanıyla kimlikleri olduğu sürece tanımlayıcıları hemen kullanmaya başlamak sağlar.

Hi/Lo algoritması veritabanı yerine istemci tarafında güvenli kimlikleri oluşturmak için bir mekanizma açıklar. *Güvenli* bu bağlamda çakışma anlamına gelir. Bu algoritma bu nedenlerle ilginç şöyledir:

-   İş birimi düzeni kesmez.

-   Gidiş dönüş yolu dizisi oluşturucuları diğer DBMS yapmak gerektirmez.

-   GUID'ler kullanımı aksine bir insan okunabilir tanımlayıcı oluşturur.

EF çekirdek destekleyen [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo yöntemiyle önceki örnekte gösterildiği gibi.

### <a name="mapping-fields-instead-of-properties"></a>Özellikleri yerine alanlarını eşleme

Bu özellik ile EF çekirdek 1.1 sürümünden itibaren kullanılabilir, doğrudan sütunları alanlarına eşleyebilirsiniz. Varlık sınıfı özellikleri kullanmamayı ve yalnızca bir tablodaki sütunları alanlarla eşlemek için mümkündür. Yaygın kullanımı söz konusu varlığı erişilecek gerekmez özel alanlar herhangi bir iç durumu için olacaktır. 

Bu tek alanları veya Ayrıca koleksiyonları ile gibi yapabileceğiniz bir `List<>` alan. Bu noktaya daha önce etki alanı modeli sınıflarını modelleme ele, ancak bu eşlemenin ile nasıl gerçekleştirildiğini burada görebilirsiniz değinilen `PropertyAccessMode.Field` önceki kodda vurgulanan yapılandırma.

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>EF çekirdek Gölge Özellikleri'ni kullanarak altyapı düzeyinde gizli

EF çekirdek gölge özelliklerinde varlık sınıfı modelinizde var olmayan özelliklerdir. Bu özelliklerin durumları ve değerlerini tamamen içinde tutulur [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) altyapı düzeyinde sınıfı.


## <a name="implementing-the-specification-pattern"></a>Belirtimi düzeni uygulama

Önceki tasarım bölümünde sunulan gibi burada bir sorgu tanımını sıralama ve mantıksal disk belleği isteğe bağlı koyabilirsiniz yer olarak tasarlanmış bir Domain-Driven tasarım deseni (tam adını sorgu belirtimi düzeni olur) belirtimi düzeni gereklidir. Belirtimi düzeni sorguda bir nesne tanımlar. Örneğin, bazı ürünler için arayan bir disk belleğine alınan sorgu kapsüllemek için gerekli giriş parametreleri (pageNumber, pageSize, filtre, vb.) alır PagedProduct belirtimi oluşturabilirsiniz. Sonra tüm deponun yöntemi (genellikle bir List() aşırı), bir ISpecification kabul ve bu belirtimine dayalı beklenen sorgusunu çalıştırın.

Bir genel belirtimi arabirimi, aşağıdaki kod örneğidir [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb). 

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

Ardından, bir genel belirtimi temel sınıfın aşağıdaki uygulamasıdır.

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

Şu belirtime Sepet'ın kimliği veya Kime Sepeti ait alıcı Kimliğini verilen tek sepet varlık yükler. İçinde [istekli yük](https://docs.microsoft.com/en-us/ef/core/querying/related-data) Sepet'ın öğeleri koleksiyonu.

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

Son olarak, belirtilen varlık türünü T. ilgili filtre ve eager yük verileri bir tür belirtimine genel EF depo nasıl kullanabileceğinizi aşağıda görebilirsiniz

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
Filtreleme mantığını Kapsüllenen yanı sıra belirtimi doldurmak için hangi özelliklerin de dahil olmak üzere döndürülecek, veri şekli belirtebilirsiniz. 

Biz Iqueryable bir depodan dönmek için önerilen yoktur ancak bunları deposu içinde bir dizi sonucu oluşturmak için kullanılacak mükemmel daha uygundur. Bu yaklaşım, sorgunun listesini oluşturmak için Ara Iqueryable ifadeler kullanan bir yöntem yukarıdaki son satırında belirtimi 's ölçütlerle sorguyu çalıştırmadan önce içerir listesinde kullanılan görebilirsiniz.


#### <a name="additional-resources"></a>Ek kaynaklar

-   **Tablo eşlemesi**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **Entity Framework Çekirdek ile anahtarları oluşturmak için HiLo kullanın**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **Destekleyen alanlar**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith. Entity Framework Çekirdek kapsüllenmiş koleksiyonları**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **Gölge Özellikleri**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Belirtimi düzeni**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)
    

>[!div class="step-by-step"]
[Önceki](infrastructure-persistence-layer-design.md)
[sonraki](nosql-database-persistence-infrastructure.md)
