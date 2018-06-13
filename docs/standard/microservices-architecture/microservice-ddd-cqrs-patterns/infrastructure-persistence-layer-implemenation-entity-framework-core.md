---
title: Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 0f3b4539156f3ba437c77dea721ca53206d1ed40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579905"
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="ecaff-103">Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama</span><span class="sxs-lookup"><span data-stu-id="ecaff-103">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="ecaff-104">SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanları kullandığınızda, önerilen yaklaşım Entity Framework (EF üzerinde) temel saklama katmanını uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="ecaff-105">EF LINQ destekler ve güçlü şekilde yazılan nesnelerin, model, aynı zamanda, veritabanına Basitleştirilmiş Kalıcılık sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecaff-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="ecaff-106">Entity Framework .NET Framework'ün bir parçası olarak uzun bir geçmişi vardır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="ecaff-107">.NET Core kullandığınızda, Windows veya Linux .NET Core aynı şekilde çalıştırır Entity Framework Çekirdek kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="ecaff-108">EF çekirdeği çok daha küçük bir yer ve önemli performans geliştirmeleri ile uygulanan Entity Framework'ün tam bir yeniden yazma olur.</span><span class="sxs-lookup"><span data-stu-id="ecaff-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="ecaff-109">Entity Framework Çekirdek giriş</span><span class="sxs-lookup"><span data-stu-id="ecaff-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="ecaff-110">Hafif, Genişletilebilir, Entity Framework (EF) çekirdeği olur ve platformlar arası sürümü popüler Entity Framework verilerine erişim teknolojisini.</span><span class="sxs-lookup"><span data-stu-id="ecaff-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="ecaff-111">Mid-2016'da ile .NET Core sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ecaff-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="ecaff-112">EF çekirdek giriş zaten Microsoft belgelerinde mevcut olduğundan, burada yalnızca bu bilgilere bağlantılar sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="ecaff-113">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ecaff-113">Additional resources</span></span>

-   <span data-ttu-id="ecaff-114">**Entity Framework Çekirdek**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="ecaff-114">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="ecaff-115">**ASP.NET Core ve Entity Framework Visual Studio kullanarak çekirdek ile çalışmaya başlama**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="ecaff-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="ecaff-116">**DbContext sınıfı**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="ecaff-116">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="ecaff-117">**EF çekirdek & EF6.x karşılaştırma**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="ecaff-117">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="ecaff-118">Entity Framework Çekirdek altyapısında DDD açısından</span><span class="sxs-lookup"><span data-stu-id="ecaff-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="ecaff-119">Bir DDD açısından bakıldığında, önemli bir özelliği EF, POCO olarak EF terminolojisi olarak da bilinen POCO etki alanı varlıklar kullanma yeteneğini olan *kod ilk varlıklar*.</span><span class="sxs-lookup"><span data-stu-id="ecaff-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="ecaff-120">POCO etki alanı varlıklar kullanırsanız, etki alanı model sınıflarınızı Kalıcılık-aşağıdaki kullanmayan, [Kalıcılık kullanmayan](http://deviq.com/persistence-ignorance/) ve [altyapı kullanmayan](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri.</span><span class="sxs-lookup"><span data-stu-id="ecaff-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="ecaff-121">DDD desenleri etki alanı davranışını ve varlık sınıfı kendisini içinde kurallar, invariants, doğrulama ve kurallardan herhangi bir koleksiyonu erişirken denetleyebilirsiniz şekilde kapsülleyen.</span><span class="sxs-lookup"><span data-stu-id="ecaff-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="ecaff-122">Bu nedenle, bu varlık veya değer nesnelerini alt koleksiyonlar genel erişime izin vermek için DDD iyi bir uygulama değil.</span><span class="sxs-lookup"><span data-stu-id="ecaff-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="ecaff-123">Bunun yerine, bu durum oluştuğunda nasıl ve ne zaman alanları ve özellik koleksiyonları güncelleştirilebilir, denetleme yöntemleri ve hangi davranışı ve Eylemler gerçekleşeceğini kullanıma sunmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="ecaff-124">EF çekirdek 1.1 itibaren bu DDD gereksinimleri karşılamak için düz alanları varlıklarınızı ortak özellikleri yerine de olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="ecaff-125">Bir varlık alanı dışarıdan erişilebilir olmasını istemiyorsanız, yalnızca özellik veya alan bir özellik yerine oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="ecaff-126">Özel özellik ayarlayıcıları de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-126">You can also use private property setters.</span></span>

<span data-ttu-id="ecaff-127">Benzer şekilde, şimdi salt okunur koleksiyonlara olarak yazılan ortak bir özelliğini kullanarak erişebilirsiniz `IReadOnlyCollection<T>`, koleksiyon için bir özel alan üye tarafından desteklenen (gibi bir `List<T>`) varlığınızdaki üzerinde EF kalıcılığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="ecaff-128">Entity Framework'ün önceki sürümlerini koleksiyon özellikleri desteklemek için gereken `ICollection<T>`, üst varlık sınıfı kullanarak herhangi bir geliştirici ekleme veya onun özellik koleksiyonları aracılığıyla öğeleri kaldırmak istediğinizi.</span><span class="sxs-lookup"><span data-stu-id="ecaff-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="ecaff-129">Bu olasılığı DDD önerilen düzenleri karşı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="ecaff-130">Salt okunur gösterme sırasında özel bir koleksiyonunu kullanabilirsiniz `IReadOnlyCollection<T>` nesnesi, aşağıdaki kod örneğinde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="ecaff-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="ecaff-131">Unutmayın `OrderItems` özelliği yalnızca erişilebilir salt okunur kullanarak olarak `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="ecaff-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="ecaff-132">Normal dış güncelleştirmeleri karşı korumalı şekilde bu tür salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="ecaff-132">This type is read-only so it is protected against regular external updates.</span></span> 

<span data-ttu-id="ecaff-133">EF çekirdek "etki alanı modeli contaminating olmadan" fiziksel veritabanı etki alanı modeline eşlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecaff-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="ecaff-134">Eşleme eylem Kalıcılık katmanında uygulanır saf .NET POCO kod, demektir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="ecaff-135">Bu eşleme eylemde alanları veritabanı eşleme yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="ecaff-136">Bir OnModelCreating metodunun aşağıdaki örnekte vurgulanmış kodu EF OrderItems özelliği aracılığıyla kendi alana erişmek için çekirdek söyler.</span><span class="sxs-lookup"><span data-stu-id="ecaff-136">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

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

<span data-ttu-id="ecaff-137">Alanları yerine özellikleri kullandığınızda, yalnızca, bir liste sahipmiş ÖgeSipariş varlık kalıcı&lt;ÖgeSipariş&gt; özelliği.</span><span class="sxs-lookup"><span data-stu-id="ecaff-137">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="ecaff-138">Ancak, tek bir erişimci sunan `AddOrderItem` siparişe yeni öğeler eklemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ecaff-138">However, it exposes a single accessor, the `AddOrderItem` method for adding new items to the order.</span></span> <span data-ttu-id="ecaff-139">Sonuç olarak, davranışı ve veri birbirine bağlıdır ve etki alanı modeli kullanan herhangi bir uygulama kodu tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="ecaff-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="ecaff-140">Entity Framework Çekirdek ile özel depoları uygulama</span><span class="sxs-lookup"><span data-stu-id="ecaff-140">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="ecaff-141">Uygulama düzeyinde bir iş (EF çekirdek içinde DBContext) birimine tarafından denetlenen veri kalıcılığı kodunu yalnızca bir sınıfla depodur güncelleştirmeleri, aşağıdaki sınıfında gösterildiği gibi gerçekleştirirken:</span><span class="sxs-lookup"><span data-stu-id="ecaff-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="ecaff-142">IBuyerRepository arabirimi bir sözleşme olarak etki alanı modeli katmandan geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ecaff-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="ecaff-143">Ancak, depo uygulaması Kalıcılık ve altyapı katman yapılır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="ecaff-144">Oluşturucu bağımlılık ekleme kullanılarak aracılığıyla EF DbContext gelir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="ecaff-145">Varsayılan ömrü (ServiceLifetime.Scoped) (aynı zamanda açıkça hizmetleriyle ayarlanabilir. IOC container sayesinde aynı HTTP istek kapsamı içinde birden çok depoları arasında paylaşılan AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="ecaff-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="ecaff-146">Bir havuzda (güncelleştirmeleri veya sorgular ve işlemler) uygulamaya yönelik yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ecaff-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="ecaff-147">Her bir havuz sınıfı içinde kendi ilgili toplama tarafından bulunan varlıkların durumunu güncelleştirme Kalıcılık yöntemleri moduna geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="ecaff-148">Bir toplama ve ilgili deposu arasındaki birebir ilişki olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ecaff-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="ecaff-149">Birleşik kök varlık nesne EF grafik alt varlıkları katıştırılmış dikkate alın.</span><span class="sxs-lookup"><span data-stu-id="ecaff-149">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="ecaff-150">Örneğin, bir alıcı birden çok ödeme yöntemi ilgili alt varlıkları sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="ecaff-151">Sıralama mikro hizmet eShopOnContainers içinde bir yaklaşım CQS/CQRS üzerinde dayalı olduğundan çoğu sorgu içinde özel depoları uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="ecaff-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="ecaff-152">Geliştiriciler için sunu katmanı toplamalar, toplama ve DDD başına özel depoları tarafından genel olarak uygulanan kısıtlamalar ihtiyaç duydukları birleştirmeler ve sorguları oluşturmak için serbestçe.</span><span class="sxs-lookup"><span data-stu-id="ecaff-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="ecaff-153">Bu kılavuzda önerilen özel depoları çoğunu birkaç güncelleştirme veya işlem yöntemlerini sahip ancak güncelleştirilecek veri için sorgu yöntemler gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="ecaff-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="ecaff-154">Örneğin, uygulamanın belirli bir alıcı sırasıyla ilişkili yeni bir alıcı oluşturmadan önce mevcut olup olmadığını bilmek gerektiğinden BuyerRepository depo zaman uyumsuz olarak bulur yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="ecaff-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="ecaff-155">Ancak, sunu katmanı veya istemci uygulamalara göndermek için veri almak için gerçek sorgu yöntemleri, Dapper kullanarak esnek sorguları temel alan CQRS sorgular bölümünde belirtildiği gibi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="ecaff-156">EF DbContext kullanarak doğrudan karşı özel bir depo kullanma</span><span class="sxs-lookup"><span data-stu-id="ecaff-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="ecaff-157">Entity Framework DbContext sınıfına iş birimi ve depo düzenlerini esas alarak ve doğrudan kodunuzdan, gibi bir ASP.NET Core MVC denetleyicisinden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="ecaff-158">Diğer bir deyişle şekilde CRUD katalog mikro hizmet eShopOnContainers içinde olduğu gibi basit kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="ecaff-159">Çoğu geliştiricinin gibi basit kod olası istediğiniz durumlarda, doğrudan bir DbContext sınıfı kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="ecaff-160">Ancak, özel depoları uygulama birkaç avantaj daha karmaşık mikro hizmetler veya uygulamalar uygularken'sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecaff-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="ecaff-161">İş birimi ve depo desenleri uygulama ve etki alanı modeli katmanları ayrılmış şekilde altyapı saklama katmanını kapsüllemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="ecaff-162">Bu desenleri uygulama veritabanına erişimi benzetimi sahte depoları kullanımını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="ecaff-163">Şekil 9-18'de bu depoları mock kolaylaştırmak depoları kullanarak karşılaştırması (EF DbContext doğrudan kullanarak) depoları kullanmayan arasındaki farklar görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-163">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="ecaff-164">**Şekil 9-18**.</span><span class="sxs-lookup"><span data-stu-id="ecaff-164">**Figure 9-18**.</span></span> <span data-ttu-id="ecaff-165">Düz bir DbContext karşı özel depoları kullanma</span><span class="sxs-lookup"><span data-stu-id="ecaff-165">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="ecaff-166">Mocking, birden çok alternatifleri vardır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-166">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="ecaff-167">Yalnızca depoları mock veya tam bir iş birimine mock.</span><span class="sxs-lookup"><span data-stu-id="ecaff-167">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="ecaff-168">Genellikle yalnızca depoları mocking yeterli olduğunu ve soyut ve tam bir iş birimine mock karmaşıklığını genellikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-168">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="ecaff-169">Daha sonra biz uygulama katmanına odaklanmanıza, bağımlılık ekleme ASP.NET Core nasıl çalıştığını ve nasıl depoları kullanırken uygulandığı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-169">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="ecaff-170">Kısacası, özel depoları kodu daha kolay veri katmanı durumuna göre etkilenmez birim testleri test olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecaff-170">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="ecaff-171">Ayrıca asıl veritabanını Entity Framework erişim testler çalıştırırsanız, bunlar birim testleri ancak çok daha yavaş tümleştirme testleri olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="ecaff-171">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="ecaff-172">DbContext doğrudan kullanıyorsanız, olurdu tek seçim için birim testleri tahmin edilebilir verilerle bir bellek içi SQL Server kullanarak birim testlerini çalıştırmak için olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-172">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="ecaff-173">Depo düzeyinde aynı şekilde sahte nesneler ve sahte veri denetimi mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-173">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="ecaff-174">Elbette, MVC denetleyicileri her zaman test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-174">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="ecaff-175">IOC kapsayıcısında EF DbContext ve IUnitOfWork örneği ömrü</span><span class="sxs-lookup"><span data-stu-id="ecaff-175">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="ecaff-176">(Bir IUnitOfWork nesne olarak gösterilen) DbContext nesnesi aynı HTTP istek kapsamı içinde birden çok depoları arasında paylaşılan gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-176">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="ecaff-177">Yürütülen işlem birden çok toplamalar veya yalnızca gerekir dağıttığınızda Örneğin, bu durum geçerlidir birden çok havuz örnekleri kullandığından.</span><span class="sxs-lookup"><span data-stu-id="ecaff-177">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="ecaff-178">IUnitOfWork arabirimi EF çekirdek türü, etki alanı katmanının bir parçası olduğunu belirttiğinizden önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-178">It is also important to mention that the IUnitOfWork interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="ecaff-179">Bunu yapmak için DbContext nesnesinin örneği hizmet yaşam süresi ayarlamak için ServiceLifetime.Scoped sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-179">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="ecaff-180">Ne zaman bir DbContext ile kayıt hizmetleri varsayılan yaşam süresi budur. AddDbContext, IOC kapsayıcısında ASP.NET çekirdek Web API projenizdeki haline dosyasının ConfigureServices yönteminden.</span><span class="sxs-lookup"><span data-stu-id="ecaff-180">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="ecaff-181">Aşağıdaki kod bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-181">The following code illustrates this.</span></span>

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

<span data-ttu-id="ecaff-182">DbContext örnek oluşturma modu ServiceLifetime.Transient veya ServiceLifetime.Singleton olarak yapılandırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-182">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="ecaff-183">IOC kapsayıcı depo örneği yaşam süresi</span><span class="sxs-lookup"><span data-stu-id="ecaff-183">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="ecaff-184">Benzer şekilde, deponun yaşam süresi genellikle kapsamlı (Autofac içinde InstancePerLifetimeScope) olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-184">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="ecaff-185">Ayrıca olabilir kapsamlı ömrü kullanırken geçici (InstancePerDependency Autofac içinde), hizmetiniz ancak bakımından bellekte daha etkili olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-185">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="ecaff-186">DbContext ayarlandığında depo için singleton ömrü kullanarak ciddi eşzamanlılık sorunlara neden olabilecek unutmayın (InstancePerLifetimeScope) yaşam süresi (varsayılan yaşam süreleri bir DBContext) kapsamlı.</span><span class="sxs-lookup"><span data-stu-id="ecaff-186">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="ecaff-187">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ecaff-187">Additional resources</span></span>

-   <span data-ttu-id="ecaff-188">**Bir ASP.NET MVC uygulamasındaki depo ve iş desenleri ölçü uygulama**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="ecaff-188">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="ecaff-189">**Jonathan Allen. Depo düzeni Entity Framework, Dapper, uygulama stratejileri ve zinciri**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="ecaff-189">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="ecaff-190">**Cesar de la Torre. ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamları ile karşılaştırma**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="ecaff-190">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="ecaff-191">Tablo eşlemesi</span><span class="sxs-lookup"><span data-stu-id="ecaff-191">Table mapping</span></span>

<span data-ttu-id="ecaff-192">Tablo eşlemesi gelen Sorgulanacak tablo verileri tanımlar ve veritabanına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-192">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="ecaff-193">Daha önce ilgili veritabanı şeması oluşturmak için etki alanı varlıkları (örneğin, bir ürün veya sırasını etki alanı)'ın nasıl kullanılabileceğini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-193">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="ecaff-194">EF kavramı kesinlikle tasarlanmış *kuralları*.</span><span class="sxs-lookup"><span data-stu-id="ecaff-194">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="ecaff-195">"Ne bir tablonun adı olacak?" gibi kuralları adresi soruları</span><span class="sxs-lookup"><span data-stu-id="ecaff-195">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="ecaff-196">veya "hangi özellik birincil anahtar?"</span><span class="sxs-lookup"><span data-stu-id="ecaff-196">or “What property is the primary key?”</span></span> <span data-ttu-id="ecaff-197">Kuralları genellikle geleneksel adlarına dayalı — Örneğin, tipik kimliği ile biten bir özellik olarak birincil anahtarı.</span><span class="sxs-lookup"><span data-stu-id="ecaff-197">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="ecaff-198">Kurala göre her bir varlık DbSet aynı ada sahip bir tabloya eşlemek için ayarlanır&lt;TEntity&gt; türetilmiş bağlam varlıkta gösteren özelliği.</span><span class="sxs-lookup"><span data-stu-id="ecaff-198">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="ecaff-199">Hiçbir DbSet,&lt;TEntity&gt; değerdir verilen varlık için kullanılan sınıf adı sağlanan.</span><span class="sxs-lookup"><span data-stu-id="ecaff-199">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="ecaff-200">Veri ek açıklamaları Fluent API'si ile karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="ecaff-200">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="ecaff-201">Birçok ek EF çekirdek kuralları vardır ve bunların çoğu veri ek açıklamaları veya OnModelCreating metodunun içinde uygulanan Fluent API kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-201">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="ecaff-202">Veri ek açıklamaları açısından bir DDD daha kullanışsız bir yol olduğu varlık modeli sınıflarında kendileri kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-202">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="ecaff-203">Altyapı veritabanı ile ilgili veri ek açıklamaları ile modelinizi contaminating olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-203">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="ecaff-204">Diğer taraftan, Fluent API varlık modeli temiz ve kalıcılığı altyapısından ayrılmış olması için çoğu kuralları ve veri saklama altyapı katmanını içinde eşlemelerini değiştirmek için uygun bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="ecaff-204">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="ecaff-205">Fluent API ve OnModelCreating yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecaff-205">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="ecaff-206">Kuralları ve eşlemelerini değiştirmek için belirtildiği gibi DbContext sınıfında OnModelCreating metodunun kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-206">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> 

<span data-ttu-id="ecaff-207">Sıralama mikro hizmet eShopOnContainers içinde açık eşleme ve yapılandırma, gerekli olduğunda, aşağıdaki kodda gösterildiği gibi uygular.</span><span class="sxs-lookup"><span data-stu-id="ecaff-207">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

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

<span data-ttu-id="ecaff-208">Aynı OnModelCreating metodunun içinde tüm Fluent API eşlemelerini ayarlayabilir, ancak bu örnekte gösterildiği gibi bu kodu bölüm ve birden çok yapılandırma sınıfları, varlık, her bir sahip önerilir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-208">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="ecaff-209">Özellikle özellikle büyük modelleri için farklı varlık türlerinin yapılandırılması için ayrı yapılandırma sınıfları olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-209">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="ecaff-210">Örnek kodda birkaç açık bildirimler ve eşleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-210">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="ecaff-211">Sizin durumunuzda gereken gerçek bir kod küçük olabilir ancak EF çekirdek kuralları bu eşlemeleri çoğunu otomatik olarak, bunun.</span><span class="sxs-lookup"><span data-stu-id="ecaff-211">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>


### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="ecaff-212">EF çekirdek Hi/Lo algoritması</span><span class="sxs-lookup"><span data-stu-id="ecaff-212">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="ecaff-213">Bir ilginç Yukarıdaki örnekteki kod bunu kullandığını yönüdür [Hi/Lo algoritması](https://vladmihalcea.com/the-hilo-algorithm/) anahtar oluşturma stratejisini olarak.</span><span class="sxs-lookup"><span data-stu-id="ecaff-213">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="ecaff-214">Hi/Lo algoritması benzersiz anahtarlar gerektiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-214">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="ecaff-215">Bir Özet, Hi-Aet.aet algoritması satır veritabanında hemen depolamayın sırada bağlı olarak tablo satırlarının benzersiz tanımlayıcıları atar.</span><span class="sxs-lookup"><span data-stu-id="ecaff-215">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="ecaff-216">Bu, normal sıralı veritabanıyla kimlikleri olduğu sürece tanımlayıcıları hemen kullanmaya başlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecaff-216">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="ecaff-217">Hi/Lo algoritması veritabanı yerine istemci tarafında güvenli kimlikleri oluşturmak için bir mekanizma açıklar.</span><span class="sxs-lookup"><span data-stu-id="ecaff-217">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="ecaff-218">*Güvenli* bu bağlamda çakışma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-218">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="ecaff-219">Bu algoritma bu nedenlerle ilginç şöyledir:</span><span class="sxs-lookup"><span data-stu-id="ecaff-219">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="ecaff-220">İş birimi düzeni kesmez.</span><span class="sxs-lookup"><span data-stu-id="ecaff-220">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="ecaff-221">Gidiş dönüş yolu dizisi oluşturucuları diğer DBMS yapmak gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="ecaff-221">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="ecaff-222">GUID'ler kullanımı aksine bir insan okunabilir tanımlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ecaff-222">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="ecaff-223">EF çekirdek destekleyen [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo yöntemiyle önceki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ecaff-223">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="ecaff-224">Özellikleri yerine alanlarını eşleme</span><span class="sxs-lookup"><span data-stu-id="ecaff-224">Mapping fields instead of properties</span></span>

<span data-ttu-id="ecaff-225">Bu özellik ile EF çekirdek 1.1 sürümünden itibaren kullanılabilir, doğrudan sütunları alanlarına eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-225">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="ecaff-226">Varlık sınıfı özellikleri kullanmamayı ve yalnızca bir tablodaki sütunları alanlarla eşlemek için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ecaff-226">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="ecaff-227">Yaygın kullanımı söz konusu varlığı erişilecek gerekmez özel alanlar herhangi bir iç durumu için olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-227">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span> 

<span data-ttu-id="ecaff-228">Bu tek alanları veya Ayrıca koleksiyonları ile gibi yapabileceğiniz bir `List<>` alan.</span><span class="sxs-lookup"><span data-stu-id="ecaff-228">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="ecaff-229">Bu noktaya daha önce etki alanı modeli sınıflarını modelleme ele, ancak bu eşlemenin ile nasıl gerçekleştirildiğini burada görebilirsiniz değinilen `PropertyAccessMode.Field` önceki kodda vurgulanan yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="ecaff-229">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="ecaff-230">EF çekirdek Gölge Özellikleri'ni kullanarak altyapı düzeyinde gizli</span><span class="sxs-lookup"><span data-stu-id="ecaff-230">Using shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="ecaff-231">EF çekirdek gölge özelliklerinde varlık sınıfı modelinizde var olmayan özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-231">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="ecaff-232">Bu özelliklerin durumları ve değerlerini tamamen içinde tutulur [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) altyapı düzeyinde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ecaff-232">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>


## <a name="implementing-the-specification-pattern"></a><span data-ttu-id="ecaff-233">Belirtimi düzeni uygulama</span><span class="sxs-lookup"><span data-stu-id="ecaff-233">Implementing the Specification pattern</span></span>

<span data-ttu-id="ecaff-234">Önceki tasarım bölümünde sunulan gibi burada bir sorgu tanımını sıralama ve mantıksal disk belleği isteğe bağlı koyabilirsiniz yer olarak tasarlanmış bir Domain-Driven tasarım deseni (tam adını sorgu belirtimi düzeni olur) belirtimi düzeni gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ecaff-234">As introduced earlier in the design section, the Specification pattern (its full name would be Query-specification pattern) is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span> <span data-ttu-id="ecaff-235">Belirtimi düzeni sorguda bir nesne tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ecaff-235">The Specification pattern defines a query in an object.</span></span> <span data-ttu-id="ecaff-236">Örneğin, bazı ürünler için arayan bir disk belleğine alınan sorgu kapsüllemek için gerekli giriş parametreleri (pageNumber, pageSize, filtre, vb.) alır PagedProduct belirtimi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-236">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="ecaff-237">Sonra tüm deponun yöntemi (genellikle bir List() aşırı), bir ISpecification kabul ve bu belirtimine dayalı beklenen sorgusunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ecaff-237">Then, any Repository’s method (usually a List() overload) would accept an ISpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="ecaff-238">Bir genel belirtimi arabirimi, aşağıdaki kod örneğidir [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="ecaff-238">An example of a generic Specification interface is the following code from [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span> 

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

<span data-ttu-id="ecaff-239">Ardından, bir genel belirtimi temel sınıfın aşağıdaki uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ecaff-239">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="ecaff-240">Şu belirtime Sepet'ın kimliği veya Kime Sepeti ait alıcı Kimliğini verilen tek sepet varlık yükler.</span><span class="sxs-lookup"><span data-stu-id="ecaff-240">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="ecaff-241">İçinde [istekli yük](https://docs.microsoft.com/en-us/ef/core/querying/related-data) Sepet'ın öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ecaff-241">It will [eager load](https://docs.microsoft.com/en-us/ef/core/querying/related-data) the basket’s Items collection.</span></span>

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

<span data-ttu-id="ecaff-242">Son olarak, belirtilen varlık türünü T. ilgili filtre ve eager yük verileri bir tür belirtimine genel EF depo nasıl kullanabileceğinizi aşağıda görebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="ecaff-242">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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
<span data-ttu-id="ecaff-243">Filtreleme mantığını Kapsüllenen yanı sıra belirtimi doldurmak için hangi özelliklerin de dahil olmak üzere döndürülecek, veri şekli belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-243">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span> 

<span data-ttu-id="ecaff-244">Biz Iqueryable bir depodan dönmek için önerilen yoktur ancak bunları deposu içinde bir dizi sonucu oluşturmak için kullanılacak mükemmel daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="ecaff-244">Although we don't recommended to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="ecaff-245">Bu yaklaşım, sorgunun listesini oluşturmak için Ara Iqueryable ifadeler kullanan bir yöntem yukarıdaki son satırında belirtimi 's ölçütlerle sorguyu çalıştırmadan önce içerir listesinde kullanılan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecaff-245">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="ecaff-246">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ecaff-246">Additional resources</span></span>

-   <span data-ttu-id="ecaff-247">**Tablo eşlemesi**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="ecaff-247">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="ecaff-248">**Entity Framework Çekirdek ile anahtarları oluşturmak için HiLo kullanın**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="ecaff-248">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="ecaff-249">**Destekleyen alanlar**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="ecaff-249">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="ecaff-250">**Steve Smith. Entity Framework Çekirdek kapsüllenmiş koleksiyonları**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="ecaff-250">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="ecaff-251">**Gölge Özellikleri**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="ecaff-251">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="ecaff-252">**Belirtimi düzeni**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span><span class="sxs-lookup"><span data-stu-id="ecaff-252">**The Specification pattern**
[*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span></span>
    

>[!div class="step-by-step"]
<span data-ttu-id="ecaff-253">[Önceki] (altyapı-Kalıcılık-katman-design.md) [sonraki] (nosql-veritabanı-Kalıcılık-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="ecaff-253">[Previous] (infrastructure-persistence-layer-design.md) [Next] (nosql-database-persistence-infrastructure.md)</span></span>
