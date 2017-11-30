---
title: "Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 508d60d73eb7c0f0cc2cc909613cc4f8712b4aba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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

-   **ASP.NET Core ve Entity Framework Visual Studio kullanarak çekirdek Başlarken**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **DbContext sınıfı**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **EF çekirdek & EF6.x karşılaştırmak**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Entity Framework Çekirdek altyapısında DDD açısından

Bir DDD açısından bakıldığında, önemli bir özelliği EF, POCO olarak EF terminolojisi olarak da bilinen POCO etki alanı varlıklar kullanma yeteneğini olan *kod ilk varlıklar*. POCO etki alanı varlıklar kullanırsanız, etki alanı model sınıflarınızı Kalıcılık-aşağıdaki kullanmayan, [Kalıcılık kullanmayan](http://deviq.com/persistence-ignorance/) ve [altyapı kullanmayan](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri.

DDD desenleri etki alanı davranışını ve varlık sınıfı kendisini içinde kurallar, invariants, doğrulama ve kurallardan herhangi bir koleksiyonu erişirken denetleyebilirsiniz şekilde kapsülleyen. Bu nedenle, bu varlık veya değer nesnelerini alt koleksiyonlar genel erişime izin vermek için DDD iyi bir uygulama değil. Bunun yerine, bu durum oluştuğunda nasıl ve ne zaman alanları ve özellik koleksiyonları güncelleştirilebilir, denetleme yöntemleri ve hangi davranışı ve Eylemler gerçekleşeceğini kullanıma sunmak istediğiniz.

EF çekirdek 1.1 Bu DDD gereksinimleri karşılamak için düz alanları varlıklarınızı ortak ve özel ayarlayıcılar özelliklerle yerine de olabilir. Bir varlık alanı dışarıdan erişilebilir olmasını istemiyorsanız, yalnızca özellik veya alan bir özellik yerine oluşturabilirsiniz. Temizleyici bu yaklaşımı tercih ederseniz, özel ayarlayıcılar kullanmaya gerek yoktur.

Benzer şekilde, şimdi salt okunur koleksiyonlara IEnumerable yazılan ortak bir özelliğini kullanarak erişebilirsiniz&lt;T&gt;, koleksiyon için bir özel alan üye tarafından desteklenen (ister listesini&lt;&gt;) içinde EF üzerinde kalıcılığını dayanır varlık. Entity Framework'ün önceki sürümlerini gerekli ICollection desteklemek için koleksiyon özelliklerini&lt;T&gt;, üst varlık sınıfı kullanarak herhangi bir geliştirici ekleme veya onun özellik koleksiyonları öğeleri kaldırmak istediğinizi. Bu olasılığı DDD önerilen düzenleri karşı olacaktır.

Aşağıdaki kod örneğinde gösterildiği gibi bir salt okunur IEnumerable nesnesi gösterme sırasında özel bir koleksiyon kullanabilirsiniz:

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...
    private readonly List<OrderItem> _orderItems;

    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();

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
        var orderItem = new OrderItem(productId, productName, unitPrice, discount,
            pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

OrderItems özelliği yalnızca salt okunur olarak listesini kullanarak erişilebilir olduğunu unutmayın&lt;&gt;. AsReadOnly(). Bu yöntemi özel listenin etrafında salt okunur bir sarmalayıcı oluşturur, böylece dış güncelleştirmeleri karşı korunur. Yeni bir koleksiyondaki tüm öğeleri kopyalamak olmadığından ToList yöntemi kullanmaktan daha ucuz; Bunun yerine, sarmalayıcı örneği için tek bir yığın ayırma işlemi gerçekleştirir.

EF çekirdek etki alanı modeli contaminating olmadan fiziksel veritabanı etki alanı modeline eşlemek için bir yol sağlar. Eşleme eylem Kalıcılık katmanında uygulanır saf .NET POCO kod, demektir. Bu eşleme eylemde alanları veritabanı eşleme yapılandırmanız gerekir. Bir OnModelCreating metodunun aşağıdaki örnekte vurgulanmış kodu EF OrderItems özelliği aracılığıyla kendi alana erişmek için çekirdek söyler.

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    // ...
    modelBuilder.Entity<Order>(ConfigureOrder);
    // Other entities ...
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    // Other configuration ...
    var navigation = orderConfiguration.Metadata.
    FindNavigation(nameof(Order.OrderItems));
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
    // Other configuration ...
}
```

Alanları yerine özellikleri kullandığınızda, yalnızca, bir liste sahipmiş ÖgeSipariş varlık kalıcı&lt;ÖgeSipariş&gt; özelliği. Ancak, sıralı olarak yeni öğeler eklemek için tek bir erişimci (AddOrderItem yöntemi) gösterir. Sonuç olarak, davranışı ve veri birbirine bağlıdır ve etki alanı modeli kullanan herhangi bir uygulama kodu tutarlı olur.

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
    }

    public BuyerRepository(OrderingContext context)
    {
        if (context == null)
        {
            throw new ArgumentNullException(
                nameof(context));
        }
        _context = context;
    }

    public Buyer Add(Buyer buyer)
    {
        return _context.Buyers.Add(buyer).Entity;
    }

    public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
    {
        var buyer = await _context.Buyers.Include(b => b.Payments)
            .Where(b => b.FullName == BuyerIdentityGuid)
            .SingleOrDefaultAsync();
        return buyer;
    }
}
```

IBuyerRepository arabirimi etki alanı modeli katmandan geldiğini unutmayın. Ancak, depo uygulaması Kalıcılık ve altyapı katman yapılır.

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

(Bir IUnitOfWork nesne olarak gösterilen) DbContext nesnesi aynı HTTP istek kapsamı içinde birden çok depoları arasında paylaşılan gerekebilir. Yürütülen işlem birden çok toplamalar veya yalnızca gerekir dağıttığınızda Örneğin, bu durum geçerlidir birden çok havuz örnekleri kullandığından. IUnitOfWork arabirimi EF türü etki alanının parçası olduğunu belirttiğinizden önemlidir.

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
        sqlop => sqlop.MigrationsAssembly(typeof(Startup).GetTypeInfo().
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
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ implementing-the-Repository-and-Unit-of-Work-Patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen. Depo için uygulama stratejileri desen ile Entity Framework, Dapper ve zincir**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Cesar de la Torre. ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamlarla karşılaştırma**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ comparing-ASP-NET-Core-ioc-Service-Life-Times-and-autofac-ioc-instance-Scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>Tablo eşlemesi

Tablo eşlemesi gelen Sorgulanacak tablo verileri tanımlar ve veritabanına kaydedilir. Daha önce ilgili veritabanı şeması oluşturmak için etki alanı varlıkları (örneğin, bir ürün veya sırasını etki alanı)'ın nasıl kullanılabileceğini gördünüz. EF kavramı kesinlikle tasarlanmış *kuralları*. "Ne bir tablonun adı olacak?" gibi kuralları adresi soruları veya "hangi özellik birincil anahtar?" Kuralları genellikle geleneksel adlarına dayalı — Örneğin, tipik kimliği ile biten bir özellik olarak birincil anahtarı.

Kurala göre her bir varlık DbSet aynı ada sahip bir tabloya eşlemek için ayarlanır&lt;TEntity&gt; türetilmiş bağlam varlıkta gösteren özelliği. Hiçbir DbSet,&lt;TEntity&gt; değerdir verilen varlık için kullanılan sınıf adı sağlanan.

### <a name="data-annotations-versus-fluent-api"></a>Veri ek açıklamaları Fluent API'si ile karşılaştırması

Birçok ek EF çekirdek kuralları vardır ve bunların çoğu veri ek açıklamaları veya OnModelCreating metodunun içinde uygulanan Fluent API kullanılarak değiştirilebilir.

Veri ek açıklamaları açısından bir DDD daha kullanışsız bir yol olduğu varlık modeli sınıflarında kendileri kullanılmalıdır. Altyapı veritabanı ile ilgili veri ek açıklamaları ile modelinizi contaminating olmasıdır. Diğer taraftan, Fluent API varlık modeli temiz ve kalıcılığı altyapısından ayrılmış olması için çoğu kuralları ve veri saklama altyapı katmanını içinde eşlemelerini değiştirmek için uygun bir yoludur.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Fluent API ve OnModelCreating yöntemi

Kuralları ve eşlemelerini değiştirmek için belirtildiği gibi DbContext sınıfında OnModelCreating metodunun kullanabilirsiniz. Aşağıdaki örnek, biz eShopOnContainers içinde sıralama mikro hizmet olarak bunu nasıl gösterir.

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    //Other entities
    modelBuilder.Entity<OrderStatus>(ConfigureOrderStatus);
    //Other entities
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Property(o => o.Id).ForSqlServerUseSequenceHiLo("orderseq", DEFAULT_SCHEMA);
    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    orderConfiguration.Property<string>("Street").IsRequired();
    orderConfiguration.Property<string>("State").IsRequired();
    orderConfiguration.Property<string>("City").IsRequired();
    orderConfiguration.Property<string>("ZipCode").IsRequired();
    orderConfiguration.Property<string>("Country").IsRequired();
    orderConfiguration.Property<int>("BuyerId").IsRequired();
    orderConfiguration.Property<int>("OrderStatusId").IsRequired();
    orderConfiguration.Property<int>("PaymentMethodId").IsRequired();

    var navigation =
    orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
    // DDD Patterns comment:
    // Set as Field (new since EF 1.1) to access
    // the OrderItem collection property as a field
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

    orderConfiguration.HasOne(o => o.PaymentMethod)
        .WithMany()
        .HasForeignKey("PaymentMethodId")
        .OnDelete(DeleteBehavior.Restrict);
        orderConfiguration.HasOne(o => o.Buyer)
        .WithMany()
        .HasForeignKey("BuyerId");
        orderConfiguration.HasOne(o => o.OrderStatus)
        .WithMany()
        .HasForeignKey("OrderStatusId");
}
```

Aynı OnModelCreating metodunun içinde tüm Fluent API eşlemelerini ayarlayabilir, ancak bu örnekte gösterildiği gibi bu kodu bölüm ve varlık başına birden çok submethods olması önerilir. Özellikle büyük modelleri için bu bile farklı varlık türlerinin yapılandırılması için ayrı bir kaynak dosyaları (statik sınıflar) sağlamak için önerilir olabilir.

Açık örnekte kodudur. Ancak, aynısını elde etmek yazmak için gereken gerçek bir kod çok daha küçük olacak şekilde EF çekirdek kuralları otomatik olarak bu çoğunu yapın.

### <a name="the-hilo-algorithm-in-ef-core"></a>EF çekirdek Hi/Lo algoritması

Bir ilginç Yukarıdaki örnekteki kod bunu kullandığını yönüdür [Hi/Lo algoritması](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) anahtar oluşturma stratejisini olarak.

Hi/Lo algoritması benzersiz anahtarlar gerektiğinde kullanışlıdır. Bir Özet, Hi-Aet.aet algoritması satır veritabanında hemen depolamayın sırada bağlı olarak tablo satırlarının benzersiz tanımlayıcıları atar. Bu, normal sıralı veritabanıyla kimlikleri olduğu sürece tanımlayıcıları hemen kullanmaya başlamak sağlar.

Hi/Lo algoritması veritabanı yerine istemci tarafında güvenli kimlikleri oluşturmak için bir mekanizma açıklar. *Güvenli* bu bağlamda çakışma anlamına gelir. Bu algoritma bu nedenlerle ilginç şöyledir:

-   İş birimi düzeni kesmez.

-   Gidiş dönüş yolu dizisi oluşturucuları diğer DBMS yapmak gerektirmez.

-   GUID'ler kullanımı aksine bir insan okunabilir tanımlayıcı oluşturur.

EF çekirdek destekleyen [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo yöntemiyle önceki örnekte gösterildiği gibi.

### <a name="mapping-fields-instead-of-properties"></a>Özellikleri yerine alanlarını eşleme

Sütunları alanlarına eşlemeleri EF çekirdek 1.1 özelliğiyle varlık sınıfında herhangi bir özelliği kullanmamayı ve yalnızca bir tablodaki sütunları alanlarla eşlemek için mümkündür. Yaygın kullanımı söz konusu varlığı erişilecek gerekmez özel alanlar herhangi bir iç durumu için olacaktır.

EF 1.1 ilgili bir özellik olmayan bir alan veritabanında bir sütunun eşlemek için bir yol destekler. Tek alanlarla veya bir listesi gibi koleksiyonlar ile de bunu yapabilirsiniz&lt; &gt; alan. Bu noktaya belirtildiği daha önce etki alanı modeli sınıflarını modelleme ele, ancak bu eşlemenin önceki kodda vurgulanan PropertyAccessMode.Field yapılandırmasıyla nasıl gerçekleştirildiğini burada görebilirsiniz.

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a>Altyapı düzeyinde gizli kimlikleri için değer nesnelerini gölge özelliklerini kullanma

EF çekirdek gölge özelliklerinde varlık sınıfı modelinizde var olmayan özelliklerdir. Bu özelliklerin durumları ve değerlerini tamamen içinde tutulur [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) altyapı düzeyinde sınıfı.

Bir DDD açısından bakıldığında, gölge gölge özelliği birincil anahtarı olarak kimliği gizleme tarafından değeri nesneleri uygulamak için kolay bir yol özelliklerdir. Bir değer nesnesi kimliği olmaması gereken bu önemlidir, çünkü (en azından, kimliği etki alanı modeli katmanında değer nesnelerini şekillendirme zaman sahip olmamalıdır). Burada EF çekirdek geçerli sürümü itibariyle EF Çekirdek değer nesneler olarak uygulamak için bir yol yok noktasıdır [karmaşık türler](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), içinde EF mümkün 6.x. Şu anda bir değer nesnesi bir gölge özelliği ayarlamak, gizli bir kimliği (birincil anahtar) sahip bir varlık olarak uygulamak gereken nedeni budur.

İçinde gördüğünüz [adresi değer nesnesi](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) eShopOnContainers içinde adresi modelinde, bir kimlik görmezsiniz:

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }
    //Constructor initializing, etc
}
```

Ancak perde arkasında biz böylece EF çekirdek bu veriler veritabanı tablolarındaki kalıcı bir kimliği sağlamanız gerekir. ConfigureAddress yönteminde bunu [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) biz EF altyapı kodu ile etki alanı modeli pollute olmayan şekilde altyapı düzeyinde sınıfı.

```csharp
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    // DDD pattern comment:
    // Implementing the Address ID as a shadow property, because the
    // address is a value object and an identity is not required for a
    // value object
    // EF Core just needs the ID so it can store it in a database table
    // See: https://docs.microsoft.com/ef/core/modeling/shadow-properties
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Tablo eşleme**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **Entity Framework Çekirdek ile anahtarları oluşturmak için HiLo kullanmak**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **Alanları yedekleme**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith. Entity Framework Çekirdek koleksiyonlarda kapsüllenmiş**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **Gölge Özellikleri**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)


>[!div class="step-by-step"]
[Önceki] (altyapı-Kalıcılık-katman-design.md) [sonraki] (nosql-veritabanı-Kalıcılık-infrastructure.md)
