---
title: Entity Framework Core ile altyapı Kalıcılık katmanını uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Entity Framework Core kullanarak altyapı kalıcılığı katmanını uygulama ayrıntılarını keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 5e0e7adad7ad2d679ccff2f1c6a421922ce2523d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151024"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="2f03b-103">Entity Framework Core ile altyapı Kalıcılık katmanını uygulama</span><span class="sxs-lookup"><span data-stu-id="2f03b-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="2f03b-104">SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanları kullandığınızda, önerilen bir yaklaşım Entity Framework (EF) üzerinde temel Kalıcılık katmanını uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="2f03b-105">EF LINQ destekleyen ve güçlü şekilde yazılan nesnelerin, model yanı sıra, veritabanına Basitleştirilmiş Kalıcılık sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f03b-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="2f03b-106">Entity Framework, .NET Framework'ün bir parçası olarak uzun bir geçmişe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="2f03b-107">.NET Core kullandığınızda, Windows veya Linux'ta .NET Core aynı şekilde çalışan Entity Framework Core de kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="2f03b-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="2f03b-108">EF Core, Entity Framework, bir çok daha küçük kaplama alanı ve önemli performans geliştirmeleri ile uygulanan tamamını yeniden yazmak ' dir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="2f03b-109">Entity Framework Core giriş</span><span class="sxs-lookup"><span data-stu-id="2f03b-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="2f03b-110">Entity Framework (EF) Core hafif, Genişletilebilir, ve platformlar arası sürümüne popüler Entity Framework Veri erişim teknolojisi.</span><span class="sxs-lookup"><span data-stu-id="2f03b-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="2f03b-111">Mid-2016'da .NET Core ile kullanılmaya başlandı.</span><span class="sxs-lookup"><span data-stu-id="2f03b-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="2f03b-112">EF Core giriş zaten Microsoft belgelerinde olduğundan, burada yalnızca bu bilgilere bağlantılar sağlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="2f03b-113">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2f03b-113">Additional resources</span></span>

- <span data-ttu-id="2f03b-114">**Entity Framework Core** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-114">**Entity Framework Core** \\</span></span>
  [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

- <span data-ttu-id="2f03b-115">**Visual Studio kullanarak Entity Framework Core ve ASP.NET Core ile çalışmaya başlama** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="2f03b-116">**DbContext sınıfı** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-116">**DbContext Class** \\</span></span>
  [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

- <span data-ttu-id="2f03b-117">**EF Core ve EF6.x karşılaştırması** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-117">**Compare EF Core & EF6.x** \\</span></span>
  [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="2f03b-118">Entity Framework Core DDD açısından altyapısı</span><span class="sxs-lookup"><span data-stu-id="2f03b-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="2f03b-119">Bir DDD açısından bakıldığında, EF terminolojisinde POCO olarak da bilinen POCO etki alanı varlıklarının kullanma olanağı EF, önemli bir özellik olan *kod öncelikli varlıkları*.</span><span class="sxs-lookup"><span data-stu-id="2f03b-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="2f03b-120">POCO etki alanı varlıklarının kullanırsanız, etki alanı model sınıflarınızı Kalıcılık-aşağıdaki ignorant, [Kalıcılık Ignorance](https://deviq.com/persistence-ignorance/) ve [altyapı Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri.</span><span class="sxs-lookup"><span data-stu-id="2f03b-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="2f03b-121">DDD deseni, etki alanı davranışını ve varlık sınıfın kendisi kuralların, okuduğunuzda, doğrulama ve kuralları herhangi bir koleksiyonuna erişirken denetleyebilirsiniz şekilde kapsüllemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="2f03b-122">Bu nedenle, varlıklar veya değer nesneleri alt koleksiyonları genel erişime izin vermek için DDD iyi bir uygulama değil.</span><span class="sxs-lookup"><span data-stu-id="2f03b-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="2f03b-123">Bunun yerine, bu durum oluştuğunda nasıl ve ne zaman özellik koleksiyonları ve alanlar güncelleştirilebilir, denetleyen yöntemleri ve hangi davranışı ve Eylemler gerçekleşmelidir kullanıma sunmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="2f03b-124">EF Core 1.1 beri bu DDD gereksinimleri karşılamak için düz alanları varlıklarınızı genel özellikleri yerine de olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="2f03b-125">Dışarıdan erişilebilir olması için bir varlık alanı istemiyorsanız, yalnızca özellik veya alan bir özelliği yerine oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="2f03b-126">Özel özellik ayarlayıcılarına de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-126">You can also use private property setters.</span></span>

<span data-ttu-id="2f03b-127">Benzer şekilde, artık salt okunur erişim koleksiyonlara olarak yazılan genel bir özelliğini kullanarak olabilir `IReadOnlyCollection<T>`, koleksiyon için bir özel alanın üyesi tarafından desteklenen (gibi bir `List<T>`) varlığınızdaki EF üzerinde kalıcılığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="2f03b-128">Entity Framework'ün önceki sürümlerinde, koleksiyon özellikleri desteklemek için gerekli `ICollection<T>`, üst varlık sınıfı kullanarak herhangi bir geliştirici ekleyebilir veya özellik koleksiyonları üzerinden öğeleri kaldırma, geliyordu.</span><span class="sxs-lookup"><span data-stu-id="2f03b-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="2f03b-129">Bu olası önerilen DDD desenlerini karşı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="2f03b-130">Bir özel koleksiyon salt okunur gösterme çalışırken kullanabileceğiniz `IReadOnlyCollection<T>` nesne, aşağıdaki kod örneğinde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="2f03b-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="2f03b-131">Unutmayın `OrderItems` özelliği yalnızca erişilebilir salt okunur kullanılarak `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="2f03b-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="2f03b-132">Bu tür, salt okunur normal dış güncelleştirmeleri karşı korunur.</span><span class="sxs-lookup"><span data-stu-id="2f03b-132">This type is read-only so it is protected against regular external updates.</span></span> 

<span data-ttu-id="2f03b-133">EF Core "etki alanı modeli contaminating olmadan" etki alanı modeli fiziksel veritabanında eşlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f03b-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="2f03b-134">Eşleme eylem Kalıcılık katmanında uygulanır saf POCO .NET kodu olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="2f03b-135">Bu eşleme eylem alanları veritabanı eşleme yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="2f03b-136">Aşağıdaki örnekte `OnModelCreating` yönteminden `OrderingContext` ve `OrderEntityTypeConfiguration` sınıfı, çağrı `SetPropertyAccessMode` erişmeye EF Core söyler `OrderItems` özelliği aracılığıyla kendi alan.</span><span class="sxs-lookup"><span data-stu-id="2f03b-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

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

<span data-ttu-id="2f03b-137">Alanları özellikleri yerine kullandığınızda `OrderItem` yalnızca bu varmış gibi varlık kalıcı bir `List<OrderItem>` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2f03b-137">When you use fields instead of properties, the `OrderItem` entity is persisted just as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="2f03b-138">Ancak, tek bir erişimci kullanıma sunduğu `AddOrderItem` siparişe yeni öğeler eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2f03b-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="2f03b-139">Sonuç olarak, davranış ve veri birbirine bağlıdır ve etki alanı modeli kullanan herhangi bir uygulama kodu tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="2f03b-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="2f03b-140">Entity Framework Core ile uygulama özel depolar</span><span class="sxs-lookup"><span data-stu-id="2f03b-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="2f03b-141">Uygulama düzeyinde bir sınıf veri kalıcılığı kodla (EF Core içinde DBContext) iş birimi tarafından denetlenen bir depo olan güncelleştirmeler, aşağıdaki sınıfında gösterildiği gerçekleştirirken:</span><span class="sxs-lookup"><span data-stu-id="2f03b-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="2f03b-142">Bir sözleşme olarak etki alanı modeli katmandan IBuyerRepository arabirimi geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2f03b-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="2f03b-143">Bununla birlikte, havuz uygulama Kalıcılık ve altyapı katmanını gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="2f03b-144">EF DbContext Oluşturucu bağımlılık ekleme kullanılarak aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="2f03b-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="2f03b-145">Varsayılan yaşam süresi sayesinde aynı HTTP istek kapsamı içinde birden çok deposu arasında paylaşıldığından (`ServiceLifetime.Scoped`) IOC kapsayıcısındaki (Bu da açıkça ayarlayabilirsiniz ile `services.AddDbContext<>`).</span><span class="sxs-lookup"><span data-stu-id="2f03b-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="2f03b-146">(Güncelleştirmeler veya sorgular ve işlemler) deposunda uygulamaya yönelik yöntemleri</span><span class="sxs-lookup"><span data-stu-id="2f03b-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="2f03b-147">Her bir depo sınıfına içinde kendi ilgili toplama tarafından bulunan varlıkların durumunu güncelleştirme Kalıcılık yöntemleri koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="2f03b-148">Toplama ve onun ilişkili depo arasındaki birebir ilişkisi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2f03b-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="2f03b-149">Bir toplama kök varlık nesnesi EF grafiğini içindeki alt varlıklar katıştırılmış sahip göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2f03b-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="2f03b-150">Örneğin, bir alıcı birden çok ödeme yöntemlerini ilgili alt varlıklar olarak sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="2f03b-151">Çoğu sorgu hizmetine sıralama mikro hizmet yaklaşımı da CQS/CQRS tabanlı olduğundan, özel depolarda uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="2f03b-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="2f03b-152">Geliştiriciler, birleşimler, toplamlar, toplama ve DDD başına özel depo tarafından genel olarak uygulanan kısıtlamaları sunu katmanı için ihtiyaç duydukları ve sorgular oluşturmak için özgürlüğüne sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="2f03b-153">Bu kılavuzda önerilen özel depolara çoğunu birkaç güncelleştirme veya işlem yöntemleri sahip ancak güncelleştirilecek veri almak yalnızca sorgu yöntemleri gerekli.</span><span class="sxs-lookup"><span data-stu-id="2f03b-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="2f03b-154">Örneğin, uygulama belirli bir alıcı siparişle ilgili yeni bir alıcı oluşturmadan önce mevcut olup olmadığını bilmek gerektiğinden BuyerRepository deponun bir FindAsync yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="2f03b-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="2f03b-155">Ancak, sunu katmanı veya istemci uygulamalarına göndermek için verileri almak için gerçek sorgu yöntemleri Dapper kullanarak esnek sorguları temel alan CQRS sorgular belirtildiği gibi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="2f03b-156">EF DbContext doğrudan kullanmak yerine özel bir depo kullanmaya</span><span class="sxs-lookup"><span data-stu-id="2f03b-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="2f03b-157">Entity Framework DbContext sınıfına, iş birimi ve depo düzenlerini esas alarak ve doğrudan sizin kodunuzdan gibi bir ASP.NET Core MVC denetleyicisi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="2f03b-158">Diğer bir deyişle şekilde CRUD Kataloğu mikro hizmetine olduğu gibi basit kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="2f03b-159">Birçok geliştirici gibi basit kod olası istediğiniz durumlarda DbContext sınıfını doğrudan kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="2f03b-160">Ancak, özel depoları uygulama çeşitli avantajlar daha karmaşık mikro hizmetler veya uygulamalar uygularken'sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f03b-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="2f03b-161">İş birimi ve depo desenleri altyapı Kalıcılık katmanını uygulama ve etki alanı modeli katmanları ayrılmış şekilde kapsüllemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="2f03b-162">Bu desenleri uygulama veritabanına erişimi benzetimi sahte depoları kullanımını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="2f03b-163">Şekil 7-18 Bu depolar sahte kolaylaştıran depoları kullanmak yerine (EF DbContext doğrudan kullanarak) depoları kullanmayan arasındaki farklar görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-163">In Figure 7-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![Özel bir depo ve düz bir DbContext kullanarak arasında karşılaştırma: özel depo depo sahte işlem tarafından test kolaylaştırmak için kullanılan bir soyutlama katmanı ekler.](./media/image19.png)

<span data-ttu-id="2f03b-165">**Şekil 7-18**.</span><span class="sxs-lookup"><span data-stu-id="2f03b-165">**Figure 7-18**.</span></span> <span data-ttu-id="2f03b-166">Düz bir DbContext ve özel depoları kullanan</span><span class="sxs-lookup"><span data-stu-id="2f03b-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="2f03b-167">Sahte işlem, birden çok çok\r\nalternatif vardır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-167">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="2f03b-168">Yalnızca depoları sahte veya tam bir iş birimi sahte.</span><span class="sxs-lookup"><span data-stu-id="2f03b-168">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="2f03b-169">Depolar genellikle sahte yeterli olur ve karmaşıklığını soyut ve tam bir iş birimi sahte genellikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-169">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="2f03b-170">Daha sonra biz uygulama katmanına odaklanmak, bağımlılık ekleme'de ASP.NET Core nasıl çalıştığını ve nasıl depoları kullanırken uygulandığı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-170">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="2f03b-171">Kısacası, özel depo tarafından veri katmanı durumu etkilenmez birim testleriyle kod daha kolay test olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f03b-171">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="2f03b-172">Ayrıca varlık çerçevesi gerçek veritabanına erişim testleri çalıştırırsanız, bunlar değil, ancak çok daha yavaş tümleştirme testleri, birim testleri.</span><span class="sxs-lookup"><span data-stu-id="2f03b-172">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="2f03b-173">DbContext doğrudan kullanıyorsanız, bunu sahte ya da bir bellek içi SQL Server ile öngörülebilir veri için birim testleri kullanarak birim testlerini çalıştırmak için gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-173">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="2f03b-174">Ancak depo düzeyinde sahte işlem daha fazla çalışma DbContext sahte işlem veya sahte veri denetimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-174">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="2f03b-175">Elbette, MVC denetleyicileri her zaman test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-175">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="2f03b-176">IOC kapsayıcınızda EF DbContext ve IUnitOfWork örneği ömrü</span><span class="sxs-lookup"><span data-stu-id="2f03b-176">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="2f03b-177">`DbContext` Nesne (olarak kullanıma sunulan bir `IUnitOfWork` nesne) aynı HTTP istek kapsamı içinde birden çok deposu arasında paylaşılması.</span><span class="sxs-lookup"><span data-stu-id="2f03b-177">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="2f03b-178">Yürütülen işlem, birden çok toplamalar veya yalnızca işlem yapması gerekir, örneğin, böyle birden çok depo örneği kullandığından.</span><span class="sxs-lookup"><span data-stu-id="2f03b-178">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="2f03b-179">Bu söz önemlidir `IUnitOfWork` arabirimi etki alanı katmanınızdaki EF Core türü bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-179">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="2f03b-180">Bu örneği yapmak için `DbContext` nenesindeki hizmet ömrü ServiceLifetime.Scoped için ayarlamak.</span><span class="sxs-lookup"><span data-stu-id="2f03b-180">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="2f03b-181">Bu varsayılan yaşam süresi, kaydolurken bir `DbContext` ile `services.AddDbContext` IOC kapsayıcınızda Createservicereplicalisteners() yönteminden `Startup.cs` dosyasında, ASP.NET Core Web API projesi.</span><span class="sxs-lookup"><span data-stu-id="2f03b-181">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="2f03b-182">Aşağıdaki kod bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-182">The following code illustrates this.</span></span>

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

<span data-ttu-id="2f03b-183">DbContext örnek oluşturma modu ServiceLifetime.Transient veya ServiceLifetime.Singleton olarak yapılandırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-183">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="2f03b-184">IOC kapsayıcınızda depo örneği ömrü</span><span class="sxs-lookup"><span data-stu-id="2f03b-184">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="2f03b-185">Benzer şekilde, deponun yaşam süresi genellikle kapsamlı (Autofac içinde InstancePerLifetimeScope) olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-185">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="2f03b-186">Ayrıca olabilir kapsamlı ömrü kullanırken geçici (InstancePerDependency Autofac içinde) hizmetinizi ancak gelince bellekte daha verimli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-186">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="2f03b-187">DbContext ayarlandığında depo için singleton ömrü kullanarak ciddi eşzamanlılık sorunlara neden olabilecek unutmayın (InstancePerLifetimeScope) yaşam süresi (varsayılan yaşam süreleri bir DBContext) kapsamı.</span><span class="sxs-lookup"><span data-stu-id="2f03b-187">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="2f03b-188">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2f03b-188">Additional resources</span></span>

- <span data-ttu-id="2f03b-189">**Bir ASP.NET MVC uygulamasındaki depo ve iş birimi desenleri uygulama** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-189">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** \\</span></span>
  [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

- <span data-ttu-id="2f03b-190">**Jonathan Allen. Depo düzeni Dapper, Entity Framework ile uygulama stratejilerini ve zinciri** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-190">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** \\</span></span>
  [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

- <span data-ttu-id="2f03b-191">**Cesar de la Torre. ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamları ile karşılaştırma** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-191">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** \\</span></span>
  [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a><span data-ttu-id="2f03b-192">Tablo eşleme</span><span class="sxs-lookup"><span data-stu-id="2f03b-192">Table mapping</span></span>

<span data-ttu-id="2f03b-193">Tablo eşleme, gelen Sorgulanacak tablo verilerini tanımlar ve veritabanına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-193">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="2f03b-194">Daha önce etki alanı varlıklarının (örneğin, bir ürün veya sipariş etki) ilgili veritabanı şema oluşturmak için nasıl kullanılabileceğini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-194">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="2f03b-195">EF kavramı kesin tasarlanmış *kuralları*.</span><span class="sxs-lookup"><span data-stu-id="2f03b-195">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="2f03b-196">"Ne bir tablonun adı olacak?" gibi kuralları adresi soruları</span><span class="sxs-lookup"><span data-stu-id="2f03b-196">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="2f03b-197">veya "birincil anahtarı hangi özelliği nedir?"</span><span class="sxs-lookup"><span data-stu-id="2f03b-197">or “What property is the primary key?”</span></span> <span data-ttu-id="2f03b-198">Kurallarına genellikle geleneksel adlarına dayalı — Örneğin, tipik kimliği ile biten bir özellik olarak birincil anahtar</span><span class="sxs-lookup"><span data-stu-id="2f03b-198">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="2f03b-199">Kural gereği, her bir varlık aynı ada sahip bir tablo eşlemek için ayarlanır `DbSet<TEntity>` sunan varlık üzerinde türetilmiş bağlam özelliği.</span><span class="sxs-lookup"><span data-stu-id="2f03b-199">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="2f03b-200">Hayır ise `DbSet<TEntity>` değerdir sağlanan belirtilen varlık için sınıf adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-200">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="2f03b-201">Veri ek açıklamaları Fluent API'si ile karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="2f03b-201">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="2f03b-202">Birçok ek EF Core kuralları vardır ve bunların çoğu veri ek açıklamaları veya OnModelCreating yöntemi içinde uygulanan Fluent API'si kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-202">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="2f03b-203">Veri ek açıklamaları bir DDD açısından daha duraklatıcı bir yolu olan varlık modeli sınıflarında kendileri kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-203">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="2f03b-204">Altyapı veritabanı ile ilgili veri açıklamalarla modelinizi contaminating olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-204">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="2f03b-205">Öte yandan, Fluent API'si varlık modeli temiz ve ayrılmış Kalıcılık altyapısından böylece çoğu kuralları ve veri saklama altyapı katmanını eşlemelerini değiştirmek için kullanışlı bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="2f03b-205">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="2f03b-206">Fluent API'si ve OnModelCreating yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f03b-206">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="2f03b-207">Kuralları ve eşlemelerini değiştirmek için belirtildiği gibi DbContext sınıfında OnModelCreating yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-207">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="2f03b-208">Sıralama mikro hizmetine açık eşleme ve yapılandırması, gerektiğinde, aşağıdaki kodda gösterildiği gibi uygular.</span><span class="sxs-lookup"><span data-stu-id="2f03b-208">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

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

<span data-ttu-id="2f03b-209">Aynı OnModelCreating yöntemi içindeki tüm Fluent API'si eşlemeleri ayarlayabilirsiniz, ancak bu örnekte gösterildiği gibi her varlık, birden çok yapılandırma sınıfı bu kodu bölüm ve önerilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-209">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="2f03b-210">Özellikle büyük modeller için özellikle, farklı varlık türleri yapılandırmak için ayrı yapılandırma sınıfları olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-210">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="2f03b-211">Örnek kodda, birkaç açık bildirimler ve eşleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-211">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="2f03b-212">Sizin durumunuzda gerekir gerçek kod daha küçük olabilir ancak, EF Core kuralları çoğu bu eşlemelerin otomatik olarak yapabilir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-212">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="2f03b-213">EF Core Merhaba/Lo algoritması</span><span class="sxs-lookup"><span data-stu-id="2f03b-213">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="2f03b-214">Bir ilgi çekici, yukarıdaki örnekteki kod bunu kullandığını yönüdür [yüksek/Lo algoritması](https://vladmihalcea.com/the-hilo-algorithm/) anahtar oluşturma stratejisi olarak.</span><span class="sxs-lookup"><span data-stu-id="2f03b-214">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="2f03b-215">Yüksek/Lo algoritması, değişiklikleri yapmadan önce benzersiz anahtarlar gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-215">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="2f03b-216">Bir Özet, yüksek-Lo algoritması satır veritabanında hemen depolamayın sırada bağlı olarak tablo satırları benzersiz tanımlayıcıları atar.</span><span class="sxs-lookup"><span data-stu-id="2f03b-216">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="2f03b-217">Bu, normal sıralı veritabanı kimliklerine olduğu sürece tanımlayıcıları hemen kullanmaya başlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f03b-217">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="2f03b-218">Yüksek/Lo algoritması benzersiz kimliklerinin toplu ilgili veritabanı dizisinden almaya yönelik bir mekanizma açıklar.</span><span class="sxs-lookup"><span data-stu-id="2f03b-218">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="2f03b-219">Bu veritabanı benzersizliği garanti eder, bu olmayacaktır böylece kullanıcılar arasında hiçbir çakışma olduğundan güvenli Kimlikleridir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-219">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="2f03b-220">Bu algoritma Bu nedenlerden dolayı ilginçtir:</span><span class="sxs-lookup"><span data-stu-id="2f03b-220">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="2f03b-221">İş birimi deseni kesmez.</span><span class="sxs-lookup"><span data-stu-id="2f03b-221">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="2f03b-222">Veritabanı gidiş dönüş en aza indirmek için toplu kimlikleri dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-222">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="2f03b-223">Bu, guid kullan teknikleri aksine insanlarca okunabilen tanımlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f03b-223">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="2f03b-224">EF Core destekler [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo yöntemiyle yukarıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="2f03b-224">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="2f03b-225">Harita alanları özellikleri yerine</span><span class="sxs-lookup"><span data-stu-id="2f03b-225">Map fields instead of properties</span></span>

<span data-ttu-id="2f03b-226">Bu özellik, EF Core 1.1 sürümünden itibaren kullanılabilir, doğrudan sütunları alanlarına eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-226">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="2f03b-227">Bu, özellikleri varlık sınıfında kullanmayı ve yalnızca bir tablodaki sütunların alanlara eşlemek için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="2f03b-227">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="2f03b-228">Yaygın bir kullanımı söz konusu varlık dışında erişilmesi gerekmeyen özel alanlar için herhangi bir iç durum olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2f03b-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="2f03b-229">Bu tek alanları veya Ayrıca koleksiyonları ile gibi yapabileceğiniz bir `List<>` alan.</span><span class="sxs-lookup"><span data-stu-id="2f03b-229">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="2f03b-230">Bu nokta etki alanı model sınıfları modelleme konusuna değinmiştik, ancak burada, bu eşlemenin ile nasıl gerçekleştirildiğini görebilirsiniz daha önce bahsedilen `PropertyAccessMode.Field` önceki kodda vurgulanan yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="2f03b-230">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="2f03b-231">EF Core, altyapı düzeyinde gizli gölge özellikleri kullanın</span><span class="sxs-lookup"><span data-stu-id="2f03b-231">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="2f03b-232">EF Core gölge özelliklerinde varlık sınıfı modelinizde var olmayan özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-232">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="2f03b-233">Bu özelliklerin durumları ve değerler tamamen içinde korunur [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) altyapı düzeyinde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2f03b-233">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="2f03b-234">Sorgu belirtimi desenini uygulama</span><span class="sxs-lookup"><span data-stu-id="2f03b-234">Implement the Query Specification pattern</span></span>

<span data-ttu-id="2f03b-235">Tasarım bölümünde daha önce sunulan gibi sorgu belirtimi burada bir sorgu tanımını sıralama ve mantıksal disk belleği isteğe bağlı koyabilirsiniz yer olarak tasarlanmış bir etki alanı Odaklı Tasarım deseni modelidir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-235">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="2f03b-236">Sorgu belirtimi deseni bir sorgu bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f03b-236">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="2f03b-237">Örneğin, bazı ürünler için bir disk belleğine alınan sorgu kapsüllemek için gereken giriş parametrelerini (pageNumber, pageSize, filtre, vb.) alan bir PagedProduct belirtimi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-237">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="2f03b-238">Sonra hiçbir depo yöntemi içinde (genellikle bir List() aşırı yük) bir IQuerySpecification kabul ve bu belirtimine göre beklenen sorgusunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2f03b-238">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="2f03b-239">Aşağıdaki kod, bir genel belirtimi arabirimi örnektir [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="2f03b-239">An example of a generic Specification interface is the following code from [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

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

<span data-ttu-id="2f03b-240">Ardından, genel belirtimi temel sınıfın uygulaması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2f03b-240">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="2f03b-241">Şu belirtime Sepet'ın Kimliğini veya sepete Kime ait alıcı kimliği verilen bir sepet tek varlık yükler.</span><span class="sxs-lookup"><span data-stu-id="2f03b-241">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="2f03b-242">Götürür [eagerly yük](https://docs.microsoft.com/ef/core/querying/related-data) Sepet'ın öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2f03b-242">It will [eagerly load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

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

<span data-ttu-id="2f03b-243">Son olarak, belirtilen varlık türünü t ilgili filtre ve eager yük verileri için bir tür belirtimi genel bir EF depo nasıl kullanabileceğinizi aşağıda görebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="2f03b-243">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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
<span data-ttu-id="2f03b-244">Filtreleme mantığı Kapsüllenen yanı sıra belirtimi doldurmak için hangi özelliklerin dahil olmak üzere verilerin döndürülmesi için Şekil belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-244">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="2f03b-245">Bir depodan Iqueryable döndürülecek önermemekteyiz olsa da, bunları bir sonuç kümesini oluşturmak için depo içinde kullanmak mükemmel bir şekilde daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="2f03b-245">Although we don’t recommend to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="2f03b-246">Bu yaklaşım, sorgunun listesini oluşturmak için Ara Iqueryable ifadeler kullanan yukarıdaki son satırında belirtimi ölçütlerle sorguyu çalıştırmadan önce includes yöntemi listesinde kullanılan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f03b-246">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="2f03b-247">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2f03b-247">Additional resources</span></span>

- <span data-ttu-id="2f03b-248">**Tablo eşleme** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-248">**Table Mapping** \\</span></span>
  [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

- <span data-ttu-id="2f03b-249">**HiLo Entity Framework Core ile anahtarlar oluşturmak için kullanın** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-249">**Use HiLo to generate keys with Entity Framework Core** \\</span></span>
  [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

- <span data-ttu-id="2f03b-250">**Destek alanları** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-250">**Backing Fields** \\</span></span>
  [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

- <span data-ttu-id="2f03b-251">**Steve Smith. Entity Framework Core kapsüllenmiş koleksiyonları** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-251">**Steve Smith. Encapsulated Collections in Entity Framework Core** \\</span></span>
  [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)

- <span data-ttu-id="2f03b-252">**Gölge Özellikler** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-252">**Shadow Properties** \\</span></span>
  [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

- <span data-ttu-id="2f03b-253">**Belirtimi deseni** \\</span><span class="sxs-lookup"><span data-stu-id="2f03b-253">**The Specification pattern** \\</span></span>
  [*https://deviq.com/specification-pattern/*](https://deviq.com/specification-pattern/)

>[!div class="step-by-step"]
><span data-ttu-id="2f03b-254">[Önceki](infrastructure-persistence-layer-design.md)
>[İleri](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="2f03b-254">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>