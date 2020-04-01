---
title: Entity Framework Core ile altyapı kalıcılık katmanını uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Entity Framework Core'u kullanarak altyapı kalıcılığı katmanının uygulama ayrıntılarını keşfedin.
ms.date: 01/30/2020
ms.openlocfilehash: 2d28d9246be3e102625ed5bb67ee1ccede03c942
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523319"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="f57a9-103">Entity Framework Core ile altyapı kalıcılığı katmanını uygulayın</span><span class="sxs-lookup"><span data-stu-id="f57a9-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="f57a9-104">SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanlarını kullandığınızda, önerilen bir yaklaşım Varlık Çerçevesi 'ne (EF) dayalı kalıcılık katmanını uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="f57a9-105">EF, LINQ'yi destekler ve modeliniz için güçlü şekilde yazılan nesnelerin yanı sıra veritabanınıza basitleştirilmiş kalıcılık sağlar.</span><span class="sxs-lookup"><span data-stu-id="f57a9-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="f57a9-106">Varlık Çerçevesi.NET Çerçevesi'nin bir parçası olarak uzun bir geçmişe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="f57a9-107">.NET Core'u kullandığınızda, Windows veya Linux'ta .NET Core ile aynı şekilde çalışan Entity Framework Core'u da kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="f57a9-108">EF Core, çok daha küçük bir ayak izi ve performansta önemli iyileştirmelerle uygulanan Entity Framework'ün tam bir yeniden yazılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="f57a9-109">Varlık Çerçeve Çekirdeğine Giriş</span><span class="sxs-lookup"><span data-stu-id="f57a9-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="f57a9-110">Entity Framework (EF) Core, popüler Entity Framework veri erişim teknolojisinin hafif, genişletilebilir ve çapraz platformlu bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f57a9-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="f57a9-111">2016 ortalarında .NET Core ile tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="f57a9-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="f57a9-112">EF Core'a giriş zaten Microsoft belgelerinde mevcut olduğundan, burada sadece bu bilgilere bağlantılar salıyoruz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f57a9-113">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f57a9-113">Additional resources</span></span>

- <span data-ttu-id="f57a9-114">**Varlık Çerçeve Çekirdeği** </span><span class="sxs-lookup"><span data-stu-id="f57a9-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="f57a9-115">**Visual Studio'ASP.NET Core ve Entity Framework Core ile başlarken** </span><span class="sxs-lookup"><span data-stu-id="f57a9-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="f57a9-116">**DbContext Sınıfı** </span><span class="sxs-lookup"><span data-stu-id="f57a9-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="f57a9-117">**EF Çekirdek & EF6.x karşılaştırın** </span><span class="sxs-lookup"><span data-stu-id="f57a9-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="f57a9-118">DDD perspektifinden Varlık Çerçeve Çekirdeğinde Altyapı</span><span class="sxs-lookup"><span data-stu-id="f57a9-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="f57a9-119">DDD açısından bakıldığında, EF'nin önemli bir özelliği, EF terminolojisinde POCO *kod ilk varlıkları*olarak da bilinen POCO etki alanı varlıklarını kullanabilmesidir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="f57a9-120">POCO etki alanı varlıklarını kullanıyorsanız, etki alanı modeli sınıflarınız [Kalıcılık Cehaleti](https://deviq.com/persistence-ignorance/) ve [Altyapı Cehaleti](https://ayende.com/blog/3137/infrastructure-ignorance) ilkelerini izleyerek kalıcılık-cahildir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="f57a9-121">DDD desenleri başına, etki alanı davranışını ve kurallarını varlık sınıfının içinde kapsüllemeniz gerekir, böylece herhangi bir koleksiyona erişirken değişmezleri, doğrulamaları ve kuralları denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="f57a9-122">Bu nedenle, DDD'de alt varlıkların veya değer nesnelerinin koleksiyonlarına genel erişime izin vermek iyi bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="f57a9-123">Bunun yerine, alanlarınızın ve özellik koleksiyonlarınızın nasıl ve ne zaman güncelleştirileceğini ve bu olduğunda hangi davranış ve eylemlerin oluşması gerektiğini denetleyen yöntemler ortaya çıkarmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="f57a9-124">EF Core 1.1'den bu yana, bu DDD gereksinimlerini karşılamak için, kamu malları yerine varlıklarınızda düz alanlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="f57a9-125">Bir varlık alanının dışarıdan erişilebilir olmasını istemiyorsanız, özellik yerine öznitelik veya alan oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="f57a9-126">Özel mülk ayarlayıcılarını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-126">You can also use private property setters.</span></span>

<span data-ttu-id="f57a9-127">Benzer bir şekilde, artık kalıcılık için EF'ye dayanan varlığınızdaki koleksiyon `IReadOnlyCollection<T>`için özel bir alan üyesi tarafından desteklenen bir `List<T>`kamu malı (örneğin) olarak yazılan bir kamu malı kullanarak koleksiyonlara salt okunur erişim elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="f57a9-128">Entity Framework'ün önceki sürümleri, `ICollection<T>`üst varlık sınıfını kullanan herhangi bir geliştiricinin özellik koleksiyonları aracılığıyla öğe ekleyebileceği veya kaldırabileceği anlamına gelen toplama özelliklerinin desteklenmesini gerektiriyordu.</span><span class="sxs-lookup"><span data-stu-id="f57a9-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="f57a9-129">Bu olasılık DDD önerilen desenlere karşı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="f57a9-130">Aşağıdaki kod örneğinde gösterildiği gibi, salt `IReadOnlyCollection<T>` okunur bir nesneyi ortaya çıkarırken özel bir koleksiyon kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f57a9-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="f57a9-131">`OrderItems` Özellik yalnızca salt okunur olarak `IReadOnlyCollection<OrderItem>`erişilebileni unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f57a9-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="f57a9-132">Bu tür salt okunur, böylece düzenli dış güncelleştirmeler karşı korunur.</span><span class="sxs-lookup"><span data-stu-id="f57a9-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="f57a9-133">EF Core, etki alanı modelini "kirletmeden" etki alanı modelini fiziksel veritabanıyla eşlemenin bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="f57a9-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="f57a9-134">Bu saf .NET POCO kodudur, çünkü eşleme eylemi kalıcılık katmanında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="f57a9-135">Bu eşleme eyleminde, alanlara veritabanı eşlemi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="f57a9-136">Yöntemden `OnModelCreating` `OrderingContext` ve sınıftan `OrderEntityTypeConfiguration` aşağıdaki örnekte, EF `SetPropertyAccessMode` Core'a `OrderItems` kendi alanı üzerinden özelliğe erişmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="f57a9-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

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

<span data-ttu-id="f57a9-137">Özellikler yerine alanları kullandığınızda, `OrderItem` varlık bir `List<OrderItem>` özelliği varmış gibi kalıcı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-137">When you use fields instead of properties, the `OrderItem` entity is persisted just as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="f57a9-138">Ancak, siparişe yeni öğeler eklemek `AddOrderItem` için tek bir erişimci, yöntem ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="f57a9-139">Sonuç olarak, davranış ve veriler birbirine bağlıdır ve etki alanı modelini kullanan tüm uygulama kodları boyunca tutarlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="f57a9-140">Entity Framework Core ile özel depoları uygulama</span><span class="sxs-lookup"><span data-stu-id="f57a9-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="f57a9-141">Uygulama düzeyinde, bir depo yalnızca aşağıdaki sınıfta gösterildiği gibi güncelleştirmeleri gerçekleştirirken bir çalışma birimi (EF Core'da DBContext) tarafından koordine edilen veri kalıcılık koduna sahip bir sınıftır:</span><span class="sxs-lookup"><span data-stu-id="f57a9-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

        public async Task<Buyer> FindAsync(string buyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == buyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="f57a9-142">IBuyerRepozitory arabiriminin bir sözleşme olarak etki alanı modeli katmanından geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f57a9-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="f57a9-143">Ancak, depo uygulaması kalıcılık ve altyapı katmanında yapılır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="f57a9-144">EF DbContext Bağımlılık Enjeksiyon u yoluyla yapıcı aracılığıyla gelir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="f57a9-145">IoC kapsayıcısındaki varsayılan ömrü ()`ServiceLifetime.Scoped`sayesinde aynı HTTP istek kapsamı içinde birden fazla depo arasında paylaşılır `services.AddDbContext<>`(bu da açıkça ayarlanabilir).</span><span class="sxs-lookup"><span data-stu-id="f57a9-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="f57a9-146">Bir depoda uygulanacak yöntemler (güncelleştirmeler veya hareketler sorgulara karşı)</span><span class="sxs-lookup"><span data-stu-id="f57a9-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="f57a9-147">Her depo sınıfı içinde, ilgili toplamı tarafından bulunan varlıkların durumunu güncelleştirmek kalıcılık yöntemleri ni koymalısınız.</span><span class="sxs-lookup"><span data-stu-id="f57a9-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="f57a9-148">Bir toplam ve ilgili depo arasında bire bir ilişki olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f57a9-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="f57a9-149">Bir toplu kök varlık nesnesinin EF grafiğinde alt varlıkları katıştırılmış olabileceğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f57a9-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="f57a9-150">Örneğin, bir alıcının ilgili alt varlıklar olarak birden çok ödeme yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="f57a9-151">eShopOnContainers sipariş microservice için yaklaşım da CQS / CQRS dayalı olduğundan, sorguların çoğu özel depolarda uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="f57a9-152">Geliştiriciler, agregalar, genel olarak özel depolar ve genel olarak DDD tarafından uygulanan kısıtlamalar olmadan sunu katmanı için gereksinim duydukları sorguları ve birleştirmeleri oluşturma özgürlüğüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="f57a9-153">Bu kılavuz tarafından önerilen özel depoların çoğunda birkaç güncelleştirme veya işlem yöntemi vardır, ancak verilerin güncelleştirilen için yalnızca sorgu yöntemleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="f57a9-154">Örneğin, AlıcıRepository deposu findasync yöntemini uygular, çünkü uygulamanın siparişle ilgili yeni bir alıcı oluşturmadan önce belirli bir alıcının var olup olmadığını bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="f57a9-155">Ancak, dapper kullanarak esnek sorguları temel alan CQRS sorgularında, söz konusu olduğu gibi, sunu katmanına veya istemci uygulamalarına gönderilecek verileri almak için gerçek sorgu yöntemleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="f57a9-156">EF DbContext'ı doğrudan kullanmanın karşısı özel bir depo kullanma</span><span class="sxs-lookup"><span data-stu-id="f57a9-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="f57a9-157">Entity Framework DbContext sınıfı Çalışma Birimi ve Depo desenleri'ni temel alınca, ASP.NET Core MVC denetleyicisi gibi doğrudan kodunuzdan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="f57a9-158">EShopOnContainers CRUD katalog microservice gibi, en basit kodu oluşturabilirsiniz yoludur.</span><span class="sxs-lookup"><span data-stu-id="f57a9-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="f57a9-159">Mümkün olan en basit kodu istediğiniz durumlarda, birçok geliştiricinin yaptığı gibi Doğrudan DbContext sınıfını kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="f57a9-160">Ancak, özel depoların uygulanması, daha karmaşık mikro hizmetler veya uygulamalar uygularken çeşitli avantajlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f57a9-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="f57a9-161">Çalışma Birimi ve Depo desenleri, uygulama ve etki alanı modeli katmanlarından ayrılması için altyapı kalıcılık katmanını kapsüllemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="f57a9-162">Bu desenlerin uygulanması, veritabanına erişimi taklit eden sahte depoların kullanımını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="f57a9-163">Şekil 7-18'de, depoları kullanmamak (doğrudan EF DbContext'ı kullanmamak) ile bu depolarla alay etmeyi kolaylaştıran depolar arasındaki farkları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-163">In Figure 7-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![İki depodaki bileşenleri ve veri akışını gösteren diyagram.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="f57a9-165">**Şekil 7-18**.</span><span class="sxs-lookup"><span data-stu-id="f57a9-165">**Figure 7-18**.</span></span> <span data-ttu-id="f57a9-166">Düz bir DbContext'a karşı özel depolar kullanma</span><span class="sxs-lookup"><span data-stu-id="f57a9-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="f57a9-167">Şekil 7-18, özel bir depo kullanarak, depoyla alay ederek testi kolaylaştırmak için kullanılabilecek bir soyutlama katmanı ekladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="f57a9-168">Alay ederken birden fazla alternatif vardır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="f57a9-169">Sadece depolarla alay edebilirsin ya da bütün bir iş birimiyle dalga geçebilirsin.</span><span class="sxs-lookup"><span data-stu-id="f57a9-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="f57a9-170">Genellikle sadece depoları alay yeterlidir ve soyut ve iş bütün bir birim alay karmaşıklığı genellikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="f57a9-171">Daha sonra, uygulama katmanına odaklandığımızda, Bağımlılık Enjeksiyonu'nun ASP.NET Core'da nasıl çalıştığını ve depoları kullanırken nasıl uygulandığını göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="f57a9-172">Kısacası, özel depolar, veri katmanı durumundan etkilenmemiş birim testleri ile kodu daha kolay sınamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f57a9-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="f57a9-173">Varlık Çerçevesi üzerinden gerçek veritabanına da erişen testler çalıştırıyorsanız, bunlar birim testleri değil, çok daha yavaş olan tümleştirme testleridir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="f57a9-174">DbContext'ı doğrudan kullanıyorsanız, birim testleri için öngörülebilir verilere sahip bir bellek içi SQL Server kullanarak onunla alay etmek veya birim testleri çalıştırmak zorunda kalırdınız.</span><span class="sxs-lookup"><span data-stu-id="f57a9-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="f57a9-175">Ancak DbContext ile alay etmek veya sahte verileri kontrol etmek, depo düzeyinde alay etmekten daha fazla iş gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="f57a9-176">Tabii ki, her zaman MVC denetleyicileri test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="f57a9-177">IoC kabınızda EF DbContext ve IUnitOfWork örnek ömrü</span><span class="sxs-lookup"><span data-stu-id="f57a9-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="f57a9-178">Nesne `DbContext` (nesne `IUnitOfWork` olarak açıkta) aynı HTTP istek kapsamı içinde birden çok depo arasında paylaşılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="f57a9-179">Örneğin, yürütülen işlemin birden çok toplamla ilgilenmesi gerektiğinde veya yalnızca birden çok depo örneği kullandığınızdan bu durum geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="f57a9-180">`IUnitOfWork` Arabirimin bir EF Core türü değil, etki alanı katmanınızın bir parçası olduğunu da belirtmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="f57a9-181">Bunu yapmak için, nesnenin `DbContext` örneğinin hizmet ömrü ServiceLifetime.Scoped olarak ayarlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="f57a9-182">Bu, ASP.NET Core Web `DbContext` API projenizdeki dosyanın `services.AddDbContext` `Startup.cs` ConfigureServices yönteminden IoC kapsayıcınızda bir ile birlikte kaydolurken varsayılan kullanım ömrüdür.</span><span class="sxs-lookup"><span data-stu-id="f57a9-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="f57a9-183">Aşağıdaki kod bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-183">The following code illustrates this.</span></span>

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

<span data-ttu-id="f57a9-184">DbContext anlık kullanım modu ServiceLifetime.Geçici veya ServiceLifetime.Singleton olarak yapılandırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="f57a9-185">IoC kabınızdaki depo örneği ömrü</span><span class="sxs-lookup"><span data-stu-id="f57a9-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="f57a9-186">Benzer bir şekilde, deponun ömrü genellikle kapsamlı olarak ayarlanmalıdır (Autofac'da InstancePerLifetimeScope).</span><span class="sxs-lookup"><span data-stu-id="f57a9-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="f57a9-187">Ayrıca geçici olabilir (Autofac InstancePerDependency), ancak hizmet kapsamı kullanırken bellek açısından daha verimli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="f57a9-188">Depo için singleton ömrünün kullanılmasının, DbContext'ınız kapsamlı (InstancePerLifetimeScope) ömür boyu (DBContext için varsayılan yaşam süreleri) olarak ayarlandığında ciddi eşzamanlılık sorunlarına neden olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f57a9-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f57a9-189">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f57a9-189">Additional resources</span></span>

- <span data-ttu-id="f57a9-190">**ASP.NET MVC Uygulamasında Çalışma Düzenlerinin Depo ve Biriminin Uygulanması** </span><span class="sxs-lookup"><span data-stu-id="f57a9-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="f57a9-191">**Jonathan Allen' ı. Varlık Çerçevesi, Dapper ve Zincirile Depo Deseni Uygulama Stratejileri** </span><span class="sxs-lookup"><span data-stu-id="f57a9-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="f57a9-192">**Cesar de la Torre. ASP.NET Core IoC konteyner hizmet ömürlerinin Autofac IoC konteyner örnek kapsamları ile karşılaştırılması** </span><span class="sxs-lookup"><span data-stu-id="f57a9-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="f57a9-193">Tablo eşleme</span><span class="sxs-lookup"><span data-stu-id="f57a9-193">Table mapping</span></span>

<span data-ttu-id="f57a9-194">Tablo eşleme, sorgulanacak ve veritabanına kaydedilecek tablo verilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f57a9-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="f57a9-195">Daha önce, etki alanı varlıklarının (örneğin, bir ürün veya sipariş etki alanı) ilgili bir veritabanı şeması oluşturmak için nasıl kullanılabileceğini gördünuz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="f57a9-196">EF güçlü *kongrekavramı*etrafında tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="f57a9-197">Kongreler "Tablonun adı ne olacak?" gibi soruları ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="f57a9-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="f57a9-198">veya "Birincil anahtar hangi özelliktir?"</span><span class="sxs-lookup"><span data-stu-id="f57a9-198">or “What property is the primary key?”</span></span> <span data-ttu-id="f57a9-199">Sözleşmeler genellikle geleneksel adlara dayanır(örneğin, birincil anahtarın Id ile biten bir özellik olması tipiktir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="f57a9-200">Kural olarak, her varlık, türetilmiş bağlamda varlığı ortaya `DbSet<TEntity>` çıkaran özellik ile aynı ada sahip bir tabloya eşlenecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-200">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="f57a9-201">Verilen `DbSet<TEntity>` varlık için değer sağlanmadıysa, sınıf adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-201">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="f57a9-202">Veri Ek Açıklamaları ve Akıcı API</span><span class="sxs-lookup"><span data-stu-id="f57a9-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="f57a9-203">Birçok ek EF Core kuralı vardır ve bunların çoğu, OnModelOluşturma yöntemi içinde uygulanan veri ek açıklamaları veya Akıcı API kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="f57a9-204">Veri ek açıklamaları, DDD açısından daha müdahaleci bir şekilde olan varlık modeli sınıflarının kendileri üzerinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="f57a9-205">Bunun nedeni, modelinizi altyapı veritabanıyla ilgili veri ek açıklamalarıyla kirletiyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="f57a9-206">Diğer taraftan, Akıcı API, veri kalıcılığı altyapı katmanınızdaki çoğu kuralı ve eşlemeyi değiştirmek için kullanışlı bir yoldur, böylece varlık modeli temiz olur ve kalıcıaltyapıdan ayrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="f57a9-207">Akıcı API ve OnModelOluşturma yöntemi</span><span class="sxs-lookup"><span data-stu-id="f57a9-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="f57a9-208">Belirtildiği gibi, kuralları ve eşlemeleri değiştirmek için, DbContext sınıfında OnModelOluşturma yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="f57a9-209">eShopOnContainers'daki sipariş mikrohizmeti, aşağıdaki kodda gösterildiği gibi gerektiğinde açık eşleme ve yapılandırma uygular.</span><span class="sxs-lookup"><span data-stu-id="f57a9-209">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

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

<span data-ttu-id="f57a9-210">Tüm Akıcı API eşlemelerini aynı `OnModelCreating` yöntem içinde ayarlayabilirsiniz, ancak bu kodu bölmek ve örnekte gösterildiği gibi varlık başına bir tane olmak üzere birden çok yapılandırma sınıfına sahip olması tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-210">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="f57a9-211">Özellikle büyük modellerde, farklı varlık türlerini yapılandırmak için ayrı yapılandırma sınıflarına sahip olması tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-211">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="f57a9-212">Örnekteki kod birkaç açık bildirimleri ve eşleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-212">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="f57a9-213">Ancak, EF Core kuralları bu eşlemelerin çoğunu otomatik olarak yapar, bu nedenle sizin durumunuzda gereksinim duymanız gereken gerçek kod daha küçük olabilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-213">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="f57a9-214">EF Core'da Hi/Lo algoritması</span><span class="sxs-lookup"><span data-stu-id="f57a9-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="f57a9-215">Yukarıdaki örnekte kodun ilginç bir yönü, anahtar oluşturma stratejisi olarak [Hi/Lo algoritmasını](https://vladmihalcea.com/the-hilo-algorithm/) kullanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="f57a9-216">Hi/Lo algoritması, değişiklik yapmadan önce benzersiz anahtarlara ihtiyacınız olduğunda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-216">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="f57a9-217">Özet olarak, Hi-Lo algoritması satırı veritabanında hemen depolamaya bağlı değilken tablo satırlarına benzersiz tanımlayıcılar atar.</span><span class="sxs-lookup"><span data-stu-id="f57a9-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="f57a9-218">Bu, düzenli sıralı veritabanı kimliklerinde olduğu gibi tanımlayıcıları hemen kullanmaya başlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f57a9-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="f57a9-219">Hi/Lo algoritması, ilgili veritabanı dizisinden bir dizi benzersiz iD almak için bir mekanizma açıklar.</span><span class="sxs-lookup"><span data-stu-id="f57a9-219">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="f57a9-220">Veritabanı benzersizliği garanti ettiği için bu iDillerin kullanımı güvenlidir, böylece kullanıcılar arasında çakışme olmaz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-220">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="f57a9-221">Bu algoritma bu nedenlerle ilginçtir:</span><span class="sxs-lookup"><span data-stu-id="f57a9-221">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="f57a9-222">İş Birimi deseni bozmaz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-222">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="f57a9-223">Veritabanına gidiş dönüş yolculuklarını en aza indirmek için toplu olarak sıralı t.c. alır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-223">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="f57a9-224">GuiD kullanan tekniklerden farklı olarak, insan tarafından okunabilir bir tanımlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f57a9-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="f57a9-225">EF Core, yukarıdaki `UseHiLo` örnekte gösterildiği gibi [HiLo'yu](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) yöntemle destekler.</span><span class="sxs-lookup"><span data-stu-id="f57a9-225">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="f57a9-226">Özellikler yerine alanları eşle</span><span class="sxs-lookup"><span data-stu-id="f57a9-226">Map fields instead of properties</span></span>

<span data-ttu-id="f57a9-227">EF Core 1.1'den beri kullanılabilen bu özellik sayesinde, sütunları doğrudan alanlara eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-227">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="f57a9-228">Varlık sınıfındaki özellikleri kullanmamak ve sütunları tablodan alanlara eşlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f57a9-228">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="f57a9-229">Bunun için ortak bir kullanım, varlık dışından erişilmesi gerekmeyen herhangi bir iç durum için özel alanlar olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f57a9-229">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="f57a9-230">Bunu tek alanlarla veya bir `List<>` alan gibi koleksiyonlarla da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-230">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="f57a9-231">Etki alanı modeli sınıflarını modellemeyi tartışırken bu noktadan daha önce bahsedildi, ancak `PropertyAccessMode.Field` burada bu eşlemenin önceki kodda vurgulanan yapılandırmayla nasıl gerçekleştirildiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="f57a9-232">ALTYAPı düzeyinde gizlenmiş EF Core'da gölge özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="f57a9-232">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="f57a9-233">EF Core'daki gölge özellikleri, varlık sınıfı modelinizde bulunmayan özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="f57a9-234">Bu özelliklerin değerleri ve durumları tamamen altyapı düzeyinde [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) sınıfında korunur.</span><span class="sxs-lookup"><span data-stu-id="f57a9-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="f57a9-235">Sorgu Belirtimi deseni uygulayın</span><span class="sxs-lookup"><span data-stu-id="f57a9-235">Implement the Query Specification pattern</span></span>

<span data-ttu-id="f57a9-236">Tasarım bölümünde daha önce de belirtildiği gibi, Sorgu Belirtimi deseni, isteğe bağlı sıralama ve sayfalama mantığıyla sorgu tanımını koyabileceğiniz yer olarak tasarlanmış etki alanı tabanlı bir tasarım desenidir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-236">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="f57a9-237">Sorgu Belirtimi deseni bir nesnedeki bir sorguyu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f57a9-237">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="f57a9-238">Örneğin, bazı ürünleri arayan sayfalı bir sorguyu kapsüllemek için gerekli giriş parametrelerini (pageNumber, pageSize, filtre, vb.) alan bir PagedProduct belirtimi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-238">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="f57a9-239">Daha sonra, herhangi bir Depo yöntemi (genellikle bir Liste() aşırı yükleme) içinde bir IQuerySpecification kabul eder ve bu belirtime dayalı beklenen sorgu yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f57a9-239">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="f57a9-240">Genel Bir Belirtim arabirimi örneği [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb)aşağıdaki kodudur.</span><span class="sxs-lookup"><span data-stu-id="f57a9-240">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

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

<span data-ttu-id="f57a9-241">Daha sonra, genel bir belirtim taban sınıfının uygulanması aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-241">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="f57a9-242">Aşağıdaki belirtim, sepetin kimliği veya sepetin ait olduğu alıcının kimliği verilen tek bir sepet tüzel kişiliğini yükler.</span><span class="sxs-lookup"><span data-stu-id="f57a9-242">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="f57a9-243">Sepetin Öğeler koleksiyonunu [hevesle yükler.](https://docs.microsoft.com/ef/core/querying/related-data)</span><span class="sxs-lookup"><span data-stu-id="f57a9-243">It will [eagerly load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

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

<span data-ttu-id="f57a9-244">Ve son olarak, genel bir EF Deposu'nun belirli bir varlık türü T ile ilgili verileri filtrelemek ve istekli yüklemek için böyle bir belirtimi nasıl kullanabileceğini aşağıda görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-244">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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

<span data-ttu-id="f57a9-245">Filtreleme mantığını kapsüllemenin yanı sıra, belirtim, hangi özelliklerin doldurulması gerektiği de dahil olmak üzere döndürülecek verilerin şeklini de belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="f57a9-245">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="f57a9-246">Bir depodan dönmenizi `IQueryable` önermesek de, bunları bir dizi sonuç oluşturmak için depo içinde kullanmak son derece iyi bir şey.</span><span class="sxs-lookup"><span data-stu-id="f57a9-246">Although we don’t recommend to return `IQueryable` from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="f57a9-247">Yukarıdaki Liste yönteminde kullanılan ve sorguyu son `IQueryable` satırda belirtim ölçütleri ile yürütmeden önce sorgunun içerir listesini oluşturmak için ara ifadeleri kullanan bu yaklaşımı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f57a9-247">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f57a9-248">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f57a9-248">Additional resources</span></span>

- <span data-ttu-id="f57a9-249">**Tablo Eşleme** </span><span class="sxs-lookup"><span data-stu-id="f57a9-249">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="f57a9-250">**Entity Framework Core ile anahtar oluşturmak için HiLo'u kullanın** </span><span class="sxs-lookup"><span data-stu-id="f57a9-250">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="f57a9-251">**Destek Alanları** </span><span class="sxs-lookup"><span data-stu-id="f57a9-251">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="f57a9-252">**Steve Smith' i. Varlık Çerçeve Çekirdeğinde Kapsüllenmiş Koleksiyonlar** </span><span class="sxs-lookup"><span data-stu-id="f57a9-252">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="f57a9-253">**Gölge Özellikleri** </span><span class="sxs-lookup"><span data-stu-id="f57a9-253">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="f57a9-254">**Belirtim deseni** </span><span class="sxs-lookup"><span data-stu-id="f57a9-254">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="f57a9-255">[Önceki](infrastructure-persistence-layer-design.md)
> [Sonraki](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="f57a9-255">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
