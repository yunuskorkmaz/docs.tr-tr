---
title: Entity Framework Core ile altyapı kalıcılık katmanını uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Entity Framework Core kullanarak altyapı kalıcılığı katmanının uygulama ayrıntılarını bulun.
ms.date: 01/30/2020
ms.openlocfilehash: 63579dc74ba52551bc1ee02a57337c1b17fdf396
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502491"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="64194-103">Altyapı kalıcılığı katmanını Entity Framework Core ile uygulama</span><span class="sxs-lookup"><span data-stu-id="64194-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="64194-104">SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanları kullandığınızda önerilen bir yaklaşım, Entity Framework (EF) temelinde Kalıcılık katmanını uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="64194-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="64194-105">EF, LINQ 'i destekler ve modelinize yönelik kesin olarak belirlenmiş nesneler sağlar ve veritabanınıza basit kalıcı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="64194-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="64194-106">Entity Framework .NET Framework bir parçası olarak uzun bir geçmişi vardır.</span><span class="sxs-lookup"><span data-stu-id="64194-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="64194-107">.NET Core kullandığınızda, .NET Core ile aynı şekilde Windows veya Linux üzerinde çalışan Entity Framework Core de kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="64194-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="64194-108">EF Core, daha küçük bir ayak ya da performans açısından önemli geliştirmelerle uygulanan Entity Framework tamamen yeniden yazma işlemi olur.</span><span class="sxs-lookup"><span data-stu-id="64194-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="64194-109">Entity Framework Core giriş</span><span class="sxs-lookup"><span data-stu-id="64194-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="64194-110">Entity Framework (EF) Core, popüler Entity Framework veri erişim teknolojisinin basit, genişletilebilir ve platformlar arası bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="64194-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="64194-111">Bu, m2016 ' de .NET Core ile tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="64194-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="64194-112">EF Core giriş Microsoft belgelerinde zaten mevcut olduğundan, bu bilgilere yönelik bağlantılar sağlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="64194-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="64194-113">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="64194-113">Additional resources</span></span>

- <span data-ttu-id="64194-114">**Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="64194-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="64194-115">**Visual Studio 'yu kullanarak ASP.NET Core ve Entity Framework Core** kullanmaya başlama </span><span class="sxs-lookup"><span data-stu-id="64194-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="64194-116">**DbContext sınıfı** </span><span class="sxs-lookup"><span data-stu-id="64194-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="64194-117">**EF Core &AMP; EF6. x \ karşılaştırın**</span><span class="sxs-lookup"><span data-stu-id="64194-117">**Compare EF Core & EF6.x** \</span></span>
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="64194-118">Bir DDD perspektifinden Entity Framework Core altyapısı</span><span class="sxs-lookup"><span data-stu-id="64194-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="64194-119">DDD türünde, önemli bir özellik olan POCO etki alanı varlıklarını, POCO *kodu-ilk varlıkları*olarak EF terimlerinde de bilinen bir şekilde kullanma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="64194-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="64194-120">POCO etki alanı varlıklarını kullanıyorsanız, etki alanı model sınıflarınız Kalıcılık [Ignorance](https://deviq.com/persistence-ignorance/) ve [altyapı Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) ilkelerine göre Kalıcılık-Ignorant ' dir.</span><span class="sxs-lookup"><span data-stu-id="64194-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="64194-121">DDD desenleri başına, varlık sınıfı içinde etki alanı davranışını ve kurallarını kapsüllemek gerekir, bu sayede herhangi bir koleksiyona erişirken ınvaryantlar, doğrulamaları ve kuralları kontrol edebilir.</span><span class="sxs-lookup"><span data-stu-id="64194-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="64194-122">Bu nedenle, alt varlıkların veya değer nesnelerinin koleksiyonlarına genel erişime izin vermek için DDD 'da iyi bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="64194-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="64194-123">Bunun yerine, alanlar ve özellik koleksiyonlarınızın nasıl ve ne zaman güncelleştirileceğini ve ne zaman meydana gelir ve eylemlerin ne zaman gerçekleşeceğini denetleyen yöntemleri göstermek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="64194-124">EF Core 1,1 ' den itibaren bu DDD gereksinimlerini karşılayacak şekilde, varlıklarınızda ortak özellikler yerine düz alanlara sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="64194-125">Bir varlık alanının dışarıdan erişilebilir olmasını istemiyorsanız, bir özellik yerine yalnızca özniteliği veya alanı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="64194-126">Özel özellik ayarlayıcıları da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-126">You can also use private property setters.</span></span>

<span data-ttu-id="64194-127">Benzer bir şekilde, artık `IReadOnlyCollection<T>`olarak yazılmış bir ortak özelliği kullanarak koleksiyonlara salt okuma erişimine sahip olabilirsiniz. Bu, bir özel alan üyesi tarafından (örneğin, bir `List<T>`gibi), kalıcılık için EF 'i temel alan varlıkınızda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="64194-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="64194-128">Entity Framework önceki sürümleri, üst varlık sınıfını kullanan herhangi bir geliştiricinin özellik koleksiyonları aracılığıyla öğe eklemesine veya kaldırmasına olanak tanıyan `ICollection<T>`desteklemek için gerekli koleksiyon özelliklerinin.</span><span class="sxs-lookup"><span data-stu-id="64194-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="64194-129">Bu olasılık, DDD 'daki önerilen desenlere karşı bir yaklaşımlar.</span><span class="sxs-lookup"><span data-stu-id="64194-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="64194-130">Aşağıdaki kod örneğinde gösterildiği gibi, salt okunurdur `IReadOnlyCollection<T>` nesnesini kullanıma alırken özel bir koleksiyon kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="64194-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="64194-131">`OrderItems` özelliğine yalnızca `IReadOnlyCollection<OrderItem>`kullanılarak salt okunurdur erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="64194-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="64194-132">Bu tür salt okunurdur, bu nedenle normal dış güncelleştirmelere karşı korunur.</span><span class="sxs-lookup"><span data-stu-id="64194-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="64194-133">EF Core, etki alanı modelini "kirmadan", etki alanı modelini fiziksel veritabanıyla eşlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="64194-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="64194-134">Bu saf .NET POCO kodudur çünkü eşleme eylemi Kalıcılık katmanında uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="64194-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="64194-135">Bu eşleme eyleminde, alanları veritabanına eşlemeyi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="64194-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="64194-136">`OrderingContext` ve `OrderEntityTypeConfiguration` sınıfından `OnModelCreating` yönteminin aşağıdaki örneğinde, `SetPropertyAccessMode` çağrısı EF Core `OrderItems` özelliğine kendi alanı aracılığıyla erişmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="64194-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

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

<span data-ttu-id="64194-137">Özellikler yerine alanları kullandığınızda `OrderItem` varlığı, tıpkı bir `List<OrderItem>` özelliğine sahip gibi kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="64194-137">When you use fields instead of properties, the `OrderItem` entity is persisted just as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="64194-138">Ancak, sıraya yeni öğeler eklemek için `AddOrderItem` yöntemi olan tek bir erişimci sunar.</span><span class="sxs-lookup"><span data-stu-id="64194-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="64194-139">Sonuç olarak, davranış ve veriler birlikte birbirlerine bağlanır ve etki alanı modelini kullanan tüm uygulama kodları boyunca tutarlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="64194-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="64194-140">Entity Framework Core ile özel depolar uygulama</span><span class="sxs-lookup"><span data-stu-id="64194-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="64194-141">Uygulama düzeyinde, bir depo, aşağıdaki sınıfta gösterildiği gibi, güncelleştirmeleri gerçekleştirirken bir iş birimi (EF Core 'de DBContext) tarafından koordine edilen veri Kalıcılık koduna sahip bir sınıftır:</span><span class="sxs-lookup"><span data-stu-id="64194-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="64194-142">Isusırepository arabiriminin, etki alanı modeli katmanından bir sözleşme olarak geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="64194-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="64194-143">Ancak, depo uygulama kalıcı ve altyapı katmanında yapılır.</span><span class="sxs-lookup"><span data-stu-id="64194-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="64194-144">EF DbContext, Oluşturucu aracılığıyla bağımlılık ekleme yoluyla gelir.</span><span class="sxs-lookup"><span data-stu-id="64194-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="64194-145">Aynı HTTP istek kapsamındaki birden çok depo arasında paylaşılır ve IOC kapsayıcısında varsayılan yaşam süresi (`ServiceLifetime.Scoped`) ile (Ayrıca `services.AddDbContext<>`açıkça ayarlanabilir).</span><span class="sxs-lookup"><span data-stu-id="64194-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="64194-146">Bir depoda uygulanacak Yöntemler (güncelleştirmeler veya işlemler ve sorgular)</span><span class="sxs-lookup"><span data-stu-id="64194-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="64194-147">Her bir depo sınıfı içinde, ilgili toplamanın içerdiği varlıkların durumunu güncelleştiren Kalıcılık yöntemlerini koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="64194-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="64194-148">Bir toplama ve ilgili depo arasında bire bir ilişki olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="64194-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="64194-149">Bir toplama kök varlık nesnesinin EF grafiğinde gömülü alt varlıkların olabileceğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="64194-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="64194-150">Örneğin, bir alıcı ilgili alt varlıklar olarak birden fazla ödeme yöntemine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="64194-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="64194-151">EShopOnContainers 'da, mikro hizmet sıralaması için yaklaşım ayrıca CQS/CQRS 'yi temel aldığı için sorguların çoğu özel depolarda uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="64194-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="64194-152">Geliştiriciler, toplamalar tarafından uygulanan kısıtlamalar, toplama başına özel depolar ve genel olarak DDD, sunum katmanı için gereken sorguları ve birleştirmeleri oluşturma özgürlüğü sunar.</span><span class="sxs-lookup"><span data-stu-id="64194-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="64194-153">Bu kılavuzda önerilen özel depoların çoğu, birkaç güncelleştirme ya da işlem yöntemine sahiptir ancak yalnızca güncelleştirilecek verileri almak için gereken sorgu yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="64194-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="64194-154">Örneğin, BuyerRepository deposu bir Findadsync yöntemi uygular, çünkü uygulamanın siparişle ilgili yeni bir alıcı oluşturmadan önce belirli bir alıcının mevcut olup olmadığını bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="64194-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="64194-155">Ancak, sunum katmanına veya istemci uygulamalarına gönderilmek üzere verileri almak için gerçek sorgu yöntemleri,, kaber kullanılarak esnek sorgulara dayanan CQRS sorgularında belirtilen şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="64194-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="64194-156">Özel bir depoyu kullanarak doğrudan EF DbContext kullanma</span><span class="sxs-lookup"><span data-stu-id="64194-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="64194-157">Entity Framework DbContext sınıfı Iş ve depo desenlerini temel alır ve doğrudan kodunuzdan (örneğin, bir ASP.NET Core MVC denetleyicisinden) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64194-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="64194-158">Bu, eShopOnContainers içindeki CRUD Katalog mikro hizmetinde olduğu gibi, en basit kodu oluşturabileceğiniz yoldur.</span><span class="sxs-lookup"><span data-stu-id="64194-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="64194-159">En basit kodun mümkün olmasını istediğiniz durumlarda, çoğu geliştirici olduğu için DbContext sınıfını doğrudan kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="64194-160">Ancak, özel depoları uygulamak, daha karmaşık mikro hizmetler veya uygulamalar uygularken çeşitli avantajlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="64194-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="64194-161">Çalışma birimi ve depo desenlerinin, uygulama ve etki alanı model katmanlarından ayrılması için altyapı kalıcılığı katmanını kapsüllemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="64194-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="64194-162">Bu desenleri uygulamak, veritabanına erişimi taklit eden sahte depoların kullanımını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="64194-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="64194-163">Şekil 7-18 ' de, bu depoları daha kolay hale getirmek için depoları kullanma (doğrudan EF DbContext kullanarak) ile ilgili farklılıkları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-163">In Figure 7-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![İki depodaki bileşenlerin ve veri akışının gösterildiği diyagram.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="64194-165">**Şekil 7-18**.</span><span class="sxs-lookup"><span data-stu-id="64194-165">**Figure 7-18**.</span></span> <span data-ttu-id="64194-166">Özel depoları kullanma, düz bir DbContext</span><span class="sxs-lookup"><span data-stu-id="64194-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="64194-167">Şekil 7-18, özel bir depoyu kullanmanın, depoyu test ederek testi kolaylaştırmak için kullanılabilecek bir soyutlama katmanı ekler.</span><span class="sxs-lookup"><span data-stu-id="64194-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="64194-168">Mocking için birden çok alternatif vardır.</span><span class="sxs-lookup"><span data-stu-id="64194-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="64194-169">Yalnızca depoların tamamını veya bir bütün çalışma birimini sahte bir şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="64194-170">Genellikle depolarda bulunan depolar yeterlidir ve tüm iş birimi için soyut ve anlamlı olan karmaşıklık genellikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="64194-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="64194-171">Daha sonra uygulama katmanına odaklandığımızda, bağımlılık ekleme 'nın ASP.NET Core içinde nasıl çalıştığını ve depoları kullanırken nasıl uygulandığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="64194-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="64194-172">Kısacası, özel depolar, veri katmanı durumundan etkilenmeyenler olan birim testleri ile kodu daha kolay test edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="64194-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="64194-173">Gerçek veritabanına aynı zamanda Entity Framework aracılığıyla erişen testler çalıştırırsanız, bunlar birim testleri, ancak çok daha yavaş olan tümleştirme sınamalarından değildir.</span><span class="sxs-lookup"><span data-stu-id="64194-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="64194-174">DbContext 'i doğrudan kullanıyorsanız, birim testleri için öngörülebilir verilerle bellek içi SQL Server kullanarak birim testlerini bir veya daha fazla şekilde çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="64194-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="64194-175">Ancak DbContext 'e göz at veya sahte verilerin denetlenmesi, depo düzeyinde sahte işlem 'ten daha fazla çalışma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="64194-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="64194-176">Kuşkusuz, her zaman MVC denetleyicilerini test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="64194-177">IFC kapsayıcıda EF DbContext ve IUnitOfWork örnek ömrü</span><span class="sxs-lookup"><span data-stu-id="64194-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="64194-178">`DbContext` nesnesi (bir `IUnitOfWork` nesnesi olarak gösterilir), aynı HTTP istek kapsamındaki birden çok depo arasında paylaşılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64194-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="64194-179">Örneğin, yürütülmekte olan işlem birden çok toplama ile uğraşmak veya birden çok depo örneği kullandığınız için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="64194-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="64194-180">`IUnitOfWork` arabirimin, EF Core bir tür değil, etki alanı katmanınızdaki bir parçası olduğunu bahsetmek de önemlidir.</span><span class="sxs-lookup"><span data-stu-id="64194-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="64194-181">Bunu yapmak için, `DbContext` nesnesinin örneğinin hizmet ömrü ServiceLifetime. kapsamlıdır olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64194-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="64194-182">Bu, ASP.NET Core Web API projenizdeki `Startup.cs` dosyasının ConfigureServices yönteminden IBC kapsayıcısındaki `services.AddDbContext` bir `DbContext` kaydederken varsayılan yaşam süresidir.</span><span class="sxs-lookup"><span data-stu-id="64194-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="64194-183">Aşağıdaki kod bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="64194-183">The following code illustrates this.</span></span>

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

<span data-ttu-id="64194-184">DbContext örnek oluşturma modu ServiceLifetime. geçici veya ServiceLifetime. Singleton olarak yapılandırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="64194-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="64194-185">IoC kapsayıcıınızda depo örneği ömrü</span><span class="sxs-lookup"><span data-stu-id="64194-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="64194-186">Benzer şekilde, deponun ömrü genellikle kapsam olarak ayarlanmalıdır (Autofac içinde InstancePerLifetimeScope).</span><span class="sxs-lookup"><span data-stu-id="64194-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="64194-187">Ayrıca geçici (Autofac ' de ınstanceperdependency) olabilir, ancak ağınız kapsamlı ömür kullanılırken belleği dikkate alarak daha verimli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="64194-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="64194-188">Depo için tek yaşam süresinin kullanılması, DbContext kapsam (InstancePerLifetimeScope) yaşam süresi (bir DBContext için varsayılan yaşam süreleri) olarak ayarlandığında ciddi eşzamanlılık sorunları oluşmasına neden olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="64194-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="64194-189">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="64194-189">Additional resources</span></span>

- <span data-ttu-id="64194-190">**Bir ASP.NET MVC uygulamasında depo ve Iş deseni birimi uygulama** </span><span class="sxs-lookup"><span data-stu-id="64194-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="64194-191">**Jonathan Allen. Entity Framework, kaber ve zincirle depo deseninin uygulama stratejileri** </span><span class="sxs-lookup"><span data-stu-id="64194-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="64194-192">**Cesar de La Torre. Autofac IoC kapsayıcı örneği kapsamları ile ASP.NET Core IOC kapsayıcı hizmeti yaşam sürelerinin karşılaştırması** </span><span class="sxs-lookup"><span data-stu-id="64194-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="64194-193">Tablo eşleme</span><span class="sxs-lookup"><span data-stu-id="64194-193">Table mapping</span></span>

<span data-ttu-id="64194-194">Tablo eşleme, sorgulanacak tablo verilerini tanımlar ve veritabanına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="64194-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="64194-195">Daha önce etki alanı varlıklarının (örneğin, bir ürün veya sipariş etki alanı) ilgili veritabanı şeması oluşturmak için nasıl kullanılabileceğini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="64194-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="64194-196">EF, *kural*kavramı etrafında kesin olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="64194-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="64194-197">Kurallar, "bir tablonun adı ne olacak?" gibi soruları ele alacak.</span><span class="sxs-lookup"><span data-stu-id="64194-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="64194-198">or "birincil anahtar nedir?"</span><span class="sxs-lookup"><span data-stu-id="64194-198">or “What property is the primary key?”</span></span> <span data-ttu-id="64194-199">Kurallar genellikle geleneksel adlara dayalıdır — Örneğin, birincil anahtarın kimlik ile biten bir özellik olması normaldir.</span><span class="sxs-lookup"><span data-stu-id="64194-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="64194-200">Kurala göre, her varlık türetilmiş bağlamda varlığı sunan `DbSet<TEntity>` özelliği ile aynı ada sahip bir tabloya eşlenecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="64194-200">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="64194-201">Verilen varlık için `DbSet<TEntity>` değeri sağlanmazsa, sınıf adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64194-201">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="64194-202">Veri ek açıklamaları ve akıcı API</span><span class="sxs-lookup"><span data-stu-id="64194-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="64194-203">Birçok ek EF Core kuralı vardır ve bunların çoğu, Onmodeloluþturma yöntemi içinde uygulanan veri ek açıklamaları veya Floent API kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="64194-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="64194-204">Veri ek açıklamaları, bir DDD bir görünüm noktasından daha kolay bir şekilde olan varlık modeli sınıflarının kendileri üzerinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64194-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="64194-205">Bunun nedeni, modelinizi altyapı veritabanıyla ilgili veri ek açıklamalarıyla kirmaktan kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="64194-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="64194-206">Öte yandan, akıcı API, veri Kalıcılık altyapısı katmanınızdaki birçok kuralı ve eşlemeyi değiştirmek için kullanışlı bir yoldur. bu nedenle, varlık modeli temiz ve kalıcılık altyapısından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="64194-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="64194-207">Akıcı API ve Onmodeloluþturma yöntemi</span><span class="sxs-lookup"><span data-stu-id="64194-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="64194-208">Belirtildiği gibi, kuralları ve eşlemeleri değiştirmek için DbContext sınıfında Onmodeloluþturma yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="64194-209">EShopOnContainers 'daki sıralama mikro hizmeti, gerektiğinde aşağıdaki kodda gösterildiği gibi açık eşleme ve yapılandırma uygular.</span><span class="sxs-lookup"><span data-stu-id="64194-209">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

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

<span data-ttu-id="64194-210">Tüm akıcı API eşlemelerini aynı `OnModelCreating` yöntemi içinde ayarlayabilirsiniz, ancak örnekte gösterildiği gibi bu kodu bölümlemek ve varlık başına birden çok yapılandırma sınıfı olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="64194-210">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="64194-211">Özellikle büyük modellerde, farklı varlık türlerini yapılandırmak için ayrı yapılandırma sınıfları olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="64194-211">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="64194-212">Örnekteki kodda birkaç açık bildirim ve eşleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="64194-212">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="64194-213">Ancak, EF Core kuralları bu eşlemelerin çoğunu otomatik olarak bir şekilde yapın, bu nedenle, büyük/küçük harfli ihtiyacınız olan gerçek kod daha küçük olabilir.</span><span class="sxs-lookup"><span data-stu-id="64194-213">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="64194-214">EF Core 'daki Hi/Lo algoritması</span><span class="sxs-lookup"><span data-stu-id="64194-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="64194-215">Önceki örnekteki kodun ilginç bir yönü, anahtar oluşturma stratejisi olarak [Hi/Lo algoritmasını](https://vladmihalcea.com/the-hilo-algorithm/) kullanmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="64194-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="64194-216">Merhaba/Lo algoritması, değişiklikleri uygulamadan önce benzersiz anahtarlara ihtiyacınız olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="64194-216">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="64194-217">Özet olarak, Hi-Lo algoritması, satırı veritabanında depolamaya bağlı olarak tablo satırlarına benzersiz tanımlayıcılar atar.</span><span class="sxs-lookup"><span data-stu-id="64194-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="64194-218">Bu, normal sıralı veritabanı kimlikleri gibi olduğu gibi, tanımlayıcıları hemen kullanmaya başlayabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64194-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="64194-219">Merhaba/Lo algoritması, ilgili bir veritabanı sırasından benzersiz kimlik toplu kimliklerini alma mekanizmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="64194-219">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="64194-220">Veritabanı benzersizlik sağladığından, bu kimlikler kullanım açısından güvenlidir, bu nedenle kullanıcılar arasında çakışma olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="64194-220">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="64194-221">Bu algoritma şu nedenlerle ilginç olur:</span><span class="sxs-lookup"><span data-stu-id="64194-221">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="64194-222">Iş deseninin birimini bozmaz.</span><span class="sxs-lookup"><span data-stu-id="64194-222">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="64194-223">Veritabanına gidiş dönüşleri en aza indirmek için dizi kimliklerini toplu olarak alır.</span><span class="sxs-lookup"><span data-stu-id="64194-223">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="64194-224">GUID kullanan tekniklerin aksine, okunabilir bir tanımlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64194-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="64194-225">EF Core, yukarıdaki örnekte gösterildiği gibi, `UseHiLo` yöntemiyle [Tepo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) 'u destekler.</span><span class="sxs-lookup"><span data-stu-id="64194-225">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="64194-226">Özellikler yerine harita alanları</span><span class="sxs-lookup"><span data-stu-id="64194-226">Map fields instead of properties</span></span>

<span data-ttu-id="64194-227">Bu özellik ile EF Core 1,1 ' den bu yana, sütunları doğrudan alanlarla eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-227">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="64194-228">Varlık sınıfında özellikler kullanılamaz ve yalnızca tablodaki sütunları alanlarla eşlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="64194-228">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="64194-229">İçin ortak bir kullanım, varlığın dışından erişilmesi gerekmeyen herhangi bir iç durum için özel alanlar olacaktır.</span><span class="sxs-lookup"><span data-stu-id="64194-229">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="64194-230">Bunu tek alanlarla veya `List<>` alanı gibi koleksiyonlarla yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-230">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="64194-231">Bu nokta, etki alanı model sınıflarını modelleyen daha önce bahsedildiği halde, bu eşlemenin önceki kodda vurgulanan `PropertyAccessMode.Field` yapılandırmasıyla nasıl gerçekleştirileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="64194-232">Altyapı düzeyinde gizlenen EF Core gölge özelliklerini kullanın</span><span class="sxs-lookup"><span data-stu-id="64194-232">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="64194-233">EF Core 'daki gölge özellikler, varlık sınıfı modelinizde bulunmayan özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="64194-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="64194-234">Bu özelliklerin değerleri ve durumları, yalnızca altyapı düzeyindeki [Changetracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) sınıfında saklanır.</span><span class="sxs-lookup"><span data-stu-id="64194-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="64194-235">Sorgu belirtim modelini uygulama</span><span class="sxs-lookup"><span data-stu-id="64194-235">Implement the Query Specification pattern</span></span>

<span data-ttu-id="64194-236">Daha önce tasarım bölümünde sunulan sorgu belirtim şekli, isteğe bağlı sıralama ve sayfalama mantığı ile bir sorgunun tanımını koyabileceğiniz yer olarak tasarlanan bir etki alanı odaklı tasarım modelidir.</span><span class="sxs-lookup"><span data-stu-id="64194-236">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="64194-237">Sorgu belirtim stili bir nesne içindeki bir sorguyu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64194-237">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="64194-238">Örneğin, bazı ürünleri arayan bir disk belleğine alınmış sorguyu kapsüllemek için gerekli giriş parametrelerini (pageNumber, pageSize, filtre, vb.) alan bir PagedProduct belirtimi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-238">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="64194-239">Ardından, herhangi bir depo yönteminde (genellikle bir liste () aşırı yüklemesi) bir ıqueryspecification kabul eder ve beklenen sorguyu bu belirtiye göre çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="64194-239">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="64194-240">Genel belirtim arabirimine bir örnek, [Eshoponweb](https://github.com/dotnet-architecture/eShopOnWeb)'den aşağıdaki koddur.</span><span class="sxs-lookup"><span data-stu-id="64194-240">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

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

<span data-ttu-id="64194-241">Daha sonra, Genel belirtim temel sınıfının uygulanması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="64194-241">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="64194-242">Aşağıdaki belirtim, sepetin KIMLIĞI veya sepetinin ait olduğu alıcının KIMLIĞI verildiğinde tek bir sepet varlığı yükler.</span><span class="sxs-lookup"><span data-stu-id="64194-242">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="64194-243">Sepetin Items toplamasını yeniden [yükler](https://docs.microsoft.com/ef/core/querying/related-data) .</span><span class="sxs-lookup"><span data-stu-id="64194-243">It will [eagerly load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

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

<span data-ttu-id="64194-244">Son olarak, bir genel EF deposunun belirli bir varlık türü T ile ilgili verileri filtrelemek ve bunlara göre yüklemek için bu belirtimi nasıl kullanabileceği hakkında daha fazla bilgi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64194-244">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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

<span data-ttu-id="64194-245">Filtre mantığını kapsüllemenin yanı sıra belirtim, doldurulacak verilerin şeklini belirtebilir ve bu da doldurulacak özellikler de dahil olmak üzere döndürülür.</span><span class="sxs-lookup"><span data-stu-id="64194-245">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="64194-246">Bir depodan `IQueryable` döndürmemenizi önermeyiz olsa da, bir dizi sonuç oluşturmak için bunları depoda kullanmak çok güzel.</span><span class="sxs-lookup"><span data-stu-id="64194-246">Although we don’t recommend to return `IQueryable` from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="64194-247">Bu yaklaşımı Yukarıdaki liste yönteminde görebilirsiniz. Bu yaklaşım, sorguyu son satırda belirtim ölçütlerine göre yürütmeden önce sorgunun dahil olduğu bir sorgu listesini oluşturmak için ara `IQueryable` ifadelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="64194-247">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="64194-248">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="64194-248">Additional resources</span></span>

- <span data-ttu-id="64194-249">**Tablo eşleme** </span><span class="sxs-lookup"><span data-stu-id="64194-249">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="64194-250">**Entity Framework Core \ anahtar oluşturmak Için Tepo kullanın**</span><span class="sxs-lookup"><span data-stu-id="64194-250">**Use HiLo to generate keys with Entity Framework Core** \</span></span>
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="64194-251">**Alanları yedekleme** </span><span class="sxs-lookup"><span data-stu-id="64194-251">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="64194-252">**Steve Smith. Entity Framework Core \ kapsüllenmiş koleksiyonlar**</span><span class="sxs-lookup"><span data-stu-id="64194-252">**Steve Smith. Encapsulated Collections in Entity Framework Core** \</span></span>
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="64194-253">**Gölge özellikleri** </span><span class="sxs-lookup"><span data-stu-id="64194-253">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="64194-254">**Belirtim deseninin** </span><span class="sxs-lookup"><span data-stu-id="64194-254">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="64194-255">[Önceki](infrastructure-persistence-layer-design.md)
> [İleri](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="64194-255">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
