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
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="5d268-104">Entity Framework Çekirdek altyapı Kalıcılık katmanla uygulama</span><span class="sxs-lookup"><span data-stu-id="5d268-104">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="5d268-105">SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanları kullandığınızda, önerilen yaklaşım Entity Framework (EF üzerinde) temel saklama katmanını uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="5d268-105">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="5d268-106">EF LINQ destekler ve güçlü şekilde yazılan nesnelerin, model, aynı zamanda, veritabanına Basitleştirilmiş Kalıcılık sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d268-106">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="5d268-107">Entity Framework .NET Framework'ün bir parçası olarak uzun bir geçmişi vardır.</span><span class="sxs-lookup"><span data-stu-id="5d268-107">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="5d268-108">.NET Core kullandığınızda, Windows veya Linux .NET Core aynı şekilde çalıştırır Entity Framework Çekirdek kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d268-108">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="5d268-109">EF çekirdeği çok daha küçük bir yer ve önemli performans geliştirmeleri ile uygulanan Entity Framework'ün tam bir yeniden yazma olur.</span><span class="sxs-lookup"><span data-stu-id="5d268-109">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="5d268-110">Entity Framework Çekirdek giriş</span><span class="sxs-lookup"><span data-stu-id="5d268-110">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="5d268-111">Hafif, Genişletilebilir, Entity Framework (EF) çekirdeği olur ve platformlar arası sürümü popüler Entity Framework verilerine erişim teknolojisini.</span><span class="sxs-lookup"><span data-stu-id="5d268-111">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="5d268-112">Mid-2016'da ile .NET Core sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5d268-112">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="5d268-113">EF çekirdek giriş zaten Microsoft belgelerinde mevcut olduğundan, burada yalnızca bu bilgilere bağlantılar sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="5d268-113">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="5d268-114">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5d268-114">Additional resources</span></span>

-   <span data-ttu-id="5d268-115">**Entity Framework Çekirdek**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="5d268-115">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="5d268-116">**ASP.NET Core ve Entity Framework Visual Studio kullanarak çekirdek Başlarken**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="5d268-116">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="5d268-117">**DbContext sınıfı**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="5d268-117">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="5d268-118">**EF çekirdek & EF6.x karşılaştırmak**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="5d268-118">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="5d268-119">Entity Framework Çekirdek altyapısında DDD açısından</span><span class="sxs-lookup"><span data-stu-id="5d268-119">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="5d268-120">Bir DDD açısından bakıldığında, önemli bir özelliği EF, POCO olarak EF terminolojisi olarak da bilinen POCO etki alanı varlıklar kullanma yeteneğini olan *kod ilk varlıklar*.</span><span class="sxs-lookup"><span data-stu-id="5d268-120">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="5d268-121">POCO etki alanı varlıklar kullanırsanız, etki alanı model sınıflarınızı Kalıcılık-aşağıdaki kullanmayan, [Kalıcılık kullanmayan](http://deviq.com/persistence-ignorance/) ve [altyapı kullanmayan](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri.</span><span class="sxs-lookup"><span data-stu-id="5d268-121">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="5d268-122">DDD desenleri etki alanı davranışını ve varlık sınıfı kendisini içinde kurallar, invariants, doğrulama ve kurallardan herhangi bir koleksiyonu erişirken denetleyebilirsiniz şekilde kapsülleyen.</span><span class="sxs-lookup"><span data-stu-id="5d268-122">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="5d268-123">Bu nedenle, bu varlık veya değer nesnelerini alt koleksiyonlar genel erişime izin vermek için DDD iyi bir uygulama değil.</span><span class="sxs-lookup"><span data-stu-id="5d268-123">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="5d268-124">Bunun yerine, bu durum oluştuğunda nasıl ve ne zaman alanları ve özellik koleksiyonları güncelleştirilebilir, denetleme yöntemleri ve hangi davranışı ve Eylemler gerçekleşeceğini kullanıma sunmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="5d268-124">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="5d268-125">EF çekirdek 1.1 Bu DDD gereksinimleri karşılamak için düz alanları varlıklarınızı ortak ve özel ayarlayıcılar özelliklerle yerine de olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d268-125">In EF Core 1.1, to satisfy those DDD requirements you can have plain fields in your entities instead of properties with public and private setters.</span></span> <span data-ttu-id="5d268-126">Bir varlık alanı dışarıdan erişilebilir olmasını istemiyorsanız, yalnızca özellik veya alan bir özellik yerine oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d268-126">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="5d268-127">Temizleyici bu yaklaşımı tercih ederseniz, özel ayarlayıcılar kullanmaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="5d268-127">There is no need to use private setters if you prefer this cleaner approach.</span></span>

<span data-ttu-id="5d268-128">Benzer şekilde, şimdi salt okunur koleksiyonlara IEnumerable yazılan ortak bir özelliğini kullanarak erişebilirsiniz&lt;T&gt;, koleksiyon için bir özel alan üye tarafından desteklenen (ister listesini&lt;&gt;) içinde EF üzerinde kalıcılığını dayanır varlık.</span><span class="sxs-lookup"><span data-stu-id="5d268-128">In a similar way, you can now have read-only access to collections by using a public property typed as IEnumerable&lt;T&gt;, which is backed by a private field member for the collection (like a List&lt;&gt;) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="5d268-129">Entity Framework'ün önceki sürümlerini gerekli ICollection desteklemek için koleksiyon özelliklerini&lt;T&gt;, üst varlık sınıfı kullanarak herhangi bir geliştirici ekleme veya onun özellik koleksiyonları öğeleri kaldırmak istediğinizi.</span><span class="sxs-lookup"><span data-stu-id="5d268-129">Previous versions of Entity Framework required collection properties to support ICollection&lt;T&gt;, which meant that any developer using the parent entity class could add or remove items from its property collections.</span></span> <span data-ttu-id="5d268-130">Bu olasılığı DDD önerilen düzenleri karşı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5d268-130">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="5d268-131">Aşağıdaki kod örneğinde gösterildiği gibi bir salt okunur IEnumerable nesnesi gösterme sırasında özel bir koleksiyon kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5d268-131">You can use a private collection while exposing a read-only IEnumerable object, as shown in the following code example:</span></span>

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

<span data-ttu-id="5d268-132">OrderItems özelliği yalnızca salt okunur olarak listesini kullanarak erişilebilir olduğunu unutmayın&lt;&gt;. AsReadOnly().</span><span class="sxs-lookup"><span data-stu-id="5d268-132">Note that the OrderItems property can only be accessed as read-only using List&lt;&gt;.AsReadOnly().</span></span> <span data-ttu-id="5d268-133">Bu yöntemi özel listenin etrafında salt okunur bir sarmalayıcı oluşturur, böylece dış güncelleştirmeleri karşı korunur.</span><span class="sxs-lookup"><span data-stu-id="5d268-133">This method creates a read-only wrapper around the private list so that it is protected against external updates.</span></span> <span data-ttu-id="5d268-134">Yeni bir koleksiyondaki tüm öğeleri kopyalamak olmadığından ToList yöntemi kullanmaktan daha ucuz; Bunun yerine, sarmalayıcı örneği için tek bir yığın ayırma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5d268-134">It is much cheaper than using the ToList method, because it does not have to copy all the items in a new collection; instead, it performs just one heap alloc operation for the wrapper instance.</span></span>

<span data-ttu-id="5d268-135">EF çekirdek etki alanı modeli contaminating olmadan fiziksel veritabanı etki alanı modeline eşlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d268-135">EF Core provides a way to map the domain model to the physical database without contaminating the domain model.</span></span> <span data-ttu-id="5d268-136">Eşleme eylem Kalıcılık katmanında uygulanır saf .NET POCO kod, demektir.</span><span class="sxs-lookup"><span data-stu-id="5d268-136">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="5d268-137">Bu eşleme eylemde alanları veritabanı eşleme yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d268-137">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="5d268-138">Bir OnModelCreating metodunun aşağıdaki örnekte vurgulanmış kodu EF OrderItems özelliği aracılığıyla kendi alana erişmek için çekirdek söyler.</span><span class="sxs-lookup"><span data-stu-id="5d268-138">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

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

<span data-ttu-id="5d268-139">Alanları yerine özellikleri kullandığınızda, yalnızca, bir liste sahipmiş ÖgeSipariş varlık kalıcı&lt;ÖgeSipariş&gt; özelliği.</span><span class="sxs-lookup"><span data-stu-id="5d268-139">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="5d268-140">Ancak, sıralı olarak yeni öğeler eklemek için tek bir erişimci (AddOrderItem yöntemi) gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d268-140">However, it exposes a single accessor (the AddOrderItem method) for adding new items to the order.</span></span> <span data-ttu-id="5d268-141">Sonuç olarak, davranışı ve veri birbirine bağlıdır ve etki alanı modeli kullanan herhangi bir uygulama kodu tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="5d268-141">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="5d268-142">Entity Framework Çekirdek ile özel depoları uygulama</span><span class="sxs-lookup"><span data-stu-id="5d268-142">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="5d268-143">Uygulama düzeyinde bir iş (EF çekirdek içinde DBContext) birimine tarafından denetlenen veri kalıcılığı kodunu yalnızca bir sınıfla depodur güncelleştirmeleri, aşağıdaki sınıfında gösterildiği gibi gerçekleştirirken:</span><span class="sxs-lookup"><span data-stu-id="5d268-143">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="5d268-144">IBuyerRepository arabirimi etki alanı modeli katmandan geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5d268-144">Note that the IBuyerRepository interface comes from the domain model layer.</span></span> <span data-ttu-id="5d268-145">Ancak, depo uygulaması Kalıcılık ve altyapı katman yapılır.</span><span class="sxs-lookup"><span data-stu-id="5d268-145">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="5d268-146">Oluşturucu bağımlılık ekleme kullanılarak aracılığıyla EF DbContext gelir.</span><span class="sxs-lookup"><span data-stu-id="5d268-146">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="5d268-147">Varsayılan ömrü (ServiceLifetime.Scoped) (aynı zamanda açıkça hizmetleriyle ayarlanabilir. IOC container sayesinde aynı HTTP istek kapsamı içinde birden çok depoları arasında paylaşılan AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="5d268-147">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="5d268-148">Bir havuzda (güncelleştirmeleri veya sorgular ve işlemler) uygulamaya yönelik yöntemleri</span><span class="sxs-lookup"><span data-stu-id="5d268-148">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="5d268-149">Her bir havuz sınıfı içinde kendi ilgili toplama tarafından bulunan varlıkların durumunu güncelleştirme Kalıcılık yöntemleri moduna geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5d268-149">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="5d268-150">Bir toplama ve ilgili deposu arasındaki birebir ilişki olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5d268-150">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="5d268-151">Birleşik kök varlık nesne EF grafik alt varlıkları katıştırılmış dikkate alın.</span><span class="sxs-lookup"><span data-stu-id="5d268-151">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="5d268-152">Örneğin, bir alıcı birden çok ödeme yöntemi ilgili alt varlıkları sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d268-152">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="5d268-153">Sıralama mikro hizmet eShopOnContainers içinde bir yaklaşım CQS/CQRS üzerinde dayalı olduğundan çoğu sorgu içinde özel depoları uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="5d268-153">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="5d268-154">Geliştiriciler için sunu katmanı toplamalar, toplama ve DDD başına özel depoları tarafından genel olarak uygulanan kısıtlamalar ihtiyaç duydukları birleştirmeler ve sorguları oluşturmak için serbestçe.</span><span class="sxs-lookup"><span data-stu-id="5d268-154">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="5d268-155">Bu kılavuzda önerilen özel depoları çoğunu birkaç güncelleştirme veya işlem yöntemlerini sahip ancak güncelleştirilecek veri için sorgu yöntemler gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="5d268-155">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="5d268-156">Örneğin, uygulamanın belirli bir alıcı sırasıyla ilişkili yeni bir alıcı oluşturmadan önce mevcut olup olmadığını bilmek gerektiğinden BuyerRepository depo zaman uyumsuz olarak bulur yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="5d268-156">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="5d268-157">Ancak, sunu katmanı veya istemci uygulamalara göndermek için veri almak için gerçek sorgu yöntemleri, Dapper kullanarak esnek sorguları temel alan CQRS sorgular bölümünde belirtildiği gibi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5d268-157">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="5d268-158">EF DbContext kullanarak doğrudan karşı özel bir depo kullanma</span><span class="sxs-lookup"><span data-stu-id="5d268-158">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="5d268-159">Entity Framework DbContext sınıfına iş birimi ve depo düzenlerini esas alarak ve doğrudan kodunuzdan, gibi bir ASP.NET Core MVC denetleyicisinden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d268-159">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="5d268-160">Diğer bir deyişle şekilde CRUD katalog mikro hizmet eShopOnContainers içinde olduğu gibi basit kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d268-160">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="5d268-161">Çoğu geliştiricinin gibi basit kod olası istediğiniz durumlarda, doğrudan bir DbContext sınıfı kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d268-161">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="5d268-162">Ancak, özel depoları uygulama birkaç avantaj daha karmaşık mikro hizmetler veya uygulamalar uygularken'sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d268-162">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="5d268-163">İş birimi ve depo desenleri uygulama ve etki alanı modeli katmanları ayrılmış şekilde altyapı saklama katmanını kapsüllemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5d268-163">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="5d268-164">Bu desenleri uygulama veritabanına erişimi benzetimi sahte depoları kullanımını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="5d268-164">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="5d268-165">Şekil 9-18'de bu depoları mock kolaylaştırmak depoları kullanarak karşılaştırması (EF DbContext doğrudan kullanarak) depoları kullanmayan arasındaki farklar görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d268-165">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="5d268-166">**Şekil 9-18**.</span><span class="sxs-lookup"><span data-stu-id="5d268-166">**Figure 9-18**.</span></span> <span data-ttu-id="5d268-167">Düz bir DbContext karşı özel depoları kullanma</span><span class="sxs-lookup"><span data-stu-id="5d268-167">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="5d268-168">Mocking, birden çok alternatifleri vardır.</span><span class="sxs-lookup"><span data-stu-id="5d268-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="5d268-169">Yalnızca depoları mock veya tam bir iş birimine mock.</span><span class="sxs-lookup"><span data-stu-id="5d268-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="5d268-170">Genellikle yalnızca depoları mocking yeterli olduğunu ve soyut ve tam bir iş birimine mock karmaşıklığını genellikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5d268-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="5d268-171">Daha sonra biz uygulama katmanına odaklanmanıza, bağımlılık ekleme ASP.NET Core nasıl çalıştığını ve nasıl depoları kullanırken uygulandığı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="5d268-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="5d268-172">Kısacası, özel depoları kodu daha kolay veri katmanı durumuna göre etkilenmez birim testleri test olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d268-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="5d268-173">Ayrıca asıl veritabanını Entity Framework erişim testler çalıştırırsanız, bunlar birim testleri ancak çok daha yavaş tümleştirme testleri olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="5d268-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="5d268-174">DbContext doğrudan kullanıyorsanız, olurdu tek seçim için birim testleri tahmin edilebilir verilerle bir bellek içi SQL Server kullanarak birim testlerini çalıştırmak için olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5d268-174">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="5d268-175">Depo düzeyinde aynı şekilde sahte nesneler ve sahte veri denetimi mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5d268-175">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="5d268-176">Elbette, MVC denetleyicileri her zaman test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d268-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="5d268-177">IOC kapsayıcısında EF DbContext ve IUnitOfWork örneği ömrü</span><span class="sxs-lookup"><span data-stu-id="5d268-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="5d268-178">(Bir IUnitOfWork nesne olarak gösterilen) DbContext nesnesi aynı HTTP istek kapsamı içinde birden çok depoları arasında paylaşılan gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5d268-178">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="5d268-179">Yürütülen işlem birden çok toplamalar veya yalnızca gerekir dağıttığınızda Örneğin, bu durum geçerlidir birden çok havuz örnekleri kullandığından.</span><span class="sxs-lookup"><span data-stu-id="5d268-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="5d268-180">IUnitOfWork arabirimi EF türü etki alanının parçası olduğunu belirttiğinizden önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5d268-180">It is also important to mention that the IUnitOfWork interface is part of the domain, not an EF type.</span></span>

<span data-ttu-id="5d268-181">Bunu yapmak için DbContext nesnesinin örneği hizmet yaşam süresi ayarlamak için ServiceLifetime.Scoped sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d268-181">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="5d268-182">Ne zaman bir DbContext ile kayıt hizmetleri varsayılan yaşam süresi budur. AddDbContext, IOC kapsayıcısında ASP.NET çekirdek Web API projenizdeki haline dosyasının ConfigureServices yönteminden.</span><span class="sxs-lookup"><span data-stu-id="5d268-182">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="5d268-183">Aşağıdaki kod bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5d268-183">The following code illustrates this.</span></span>

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

<span data-ttu-id="5d268-184">DbContext örnek oluşturma modu ServiceLifetime.Transient veya ServiceLifetime.Singleton olarak yapılandırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d268-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="5d268-185">IOC kapsayıcı depo örneği yaşam süresi</span><span class="sxs-lookup"><span data-stu-id="5d268-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="5d268-186">Benzer şekilde, deponun yaşam süresi genellikle kapsamlı (Autofac içinde InstancePerLifetimeScope) olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d268-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="5d268-187">Ayrıca olabilir kapsamlı ömrü kullanırken geçici (InstancePerDependency Autofac içinde), hizmetiniz ancak bakımından bellekte daha etkili olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5d268-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="5d268-188">DbContext ayarlandığında depo için singleton ömrü kullanarak ciddi eşzamanlılık sorunlara neden olabilecek unutmayın (InstancePerLifetimeScope) yaşam süresi (varsayılan yaşam süreleri bir DBContext) kapsamlı.</span><span class="sxs-lookup"><span data-stu-id="5d268-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="5d268-189">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5d268-189">Additional resources</span></span>

-   <span data-ttu-id="5d268-190">**Bir ASP.NET MVC uygulamasındaki depo ve iş desenleri ölçü uygulama**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ implementing-the-Repository-and-Unit-of-Work-Patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="5d268-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="5d268-191">**Jonathan Allen. Depo için uygulama stratejileri desen ile Entity Framework, Dapper ve zincir**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="5d268-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="5d268-192">**Cesar de la Torre. ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamlarla karşılaştırma**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ comparing-ASP-NET-Core-ioc-Service-Life-Times-and-autofac-ioc-instance-Scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="5d268-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="5d268-193">Tablo eşlemesi</span><span class="sxs-lookup"><span data-stu-id="5d268-193">Table mapping</span></span>

<span data-ttu-id="5d268-194">Tablo eşlemesi gelen Sorgulanacak tablo verileri tanımlar ve veritabanına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5d268-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="5d268-195">Daha önce ilgili veritabanı şeması oluşturmak için etki alanı varlıkları (örneğin, bir ürün veya sırasını etki alanı)'ın nasıl kullanılabileceğini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="5d268-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="5d268-196">EF kavramı kesinlikle tasarlanmış *kuralları*.</span><span class="sxs-lookup"><span data-stu-id="5d268-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="5d268-197">"Ne bir tablonun adı olacak?" gibi kuralları adresi soruları</span><span class="sxs-lookup"><span data-stu-id="5d268-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="5d268-198">veya "hangi özellik birincil anahtar?"</span><span class="sxs-lookup"><span data-stu-id="5d268-198">or “What property is the primary key?”</span></span> <span data-ttu-id="5d268-199">Kuralları genellikle geleneksel adlarına dayalı — Örneğin, tipik kimliği ile biten bir özellik olarak birincil anahtarı.</span><span class="sxs-lookup"><span data-stu-id="5d268-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="5d268-200">Kurala göre her bir varlık DbSet aynı ada sahip bir tabloya eşlemek için ayarlanır&lt;TEntity&gt; türetilmiş bağlam varlıkta gösteren özelliği.</span><span class="sxs-lookup"><span data-stu-id="5d268-200">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="5d268-201">Hiçbir DbSet,&lt;TEntity&gt; değerdir verilen varlık için kullanılan sınıf adı sağlanan.</span><span class="sxs-lookup"><span data-stu-id="5d268-201">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="5d268-202">Veri ek açıklamaları Fluent API'si ile karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="5d268-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="5d268-203">Birçok ek EF çekirdek kuralları vardır ve bunların çoğu veri ek açıklamaları veya OnModelCreating metodunun içinde uygulanan Fluent API kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5d268-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="5d268-204">Veri ek açıklamaları açısından bir DDD daha kullanışsız bir yol olduğu varlık modeli sınıflarında kendileri kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d268-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="5d268-205">Altyapı veritabanı ile ilgili veri ek açıklamaları ile modelinizi contaminating olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5d268-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="5d268-206">Diğer taraftan, Fluent API varlık modeli temiz ve kalıcılığı altyapısından ayrılmış olması için çoğu kuralları ve veri saklama altyapı katmanını içinde eşlemelerini değiştirmek için uygun bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="5d268-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="5d268-207">Fluent API ve OnModelCreating yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d268-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="5d268-208">Kuralları ve eşlemelerini değiştirmek için belirtildiği gibi DbContext sınıfında OnModelCreating metodunun kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d268-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> <span data-ttu-id="5d268-209">Aşağıdaki örnek, biz eShopOnContainers içinde sıralama mikro hizmet olarak bunu nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d268-209">The following example shows how we do this in the ordering microservice in eShopOnContainers.</span></span>

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

<span data-ttu-id="5d268-210">Aynı OnModelCreating metodunun içinde tüm Fluent API eşlemelerini ayarlayabilir, ancak bu örnekte gösterildiği gibi bu kodu bölüm ve varlık başına birden çok submethods olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="5d268-210">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple submethods, one per entity, as shown in the example.</span></span> <span data-ttu-id="5d268-211">Özellikle büyük modelleri için bu bile farklı varlık türlerinin yapılandırılması için ayrı bir kaynak dosyaları (statik sınıflar) sağlamak için önerilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d268-211">For particularly large models, it can even be advisable to have separate source files (static classes) for configuring different entity types.</span></span>

<span data-ttu-id="5d268-212">Açık örnekte kodudur.</span><span class="sxs-lookup"><span data-stu-id="5d268-212">The code in the example is explicit.</span></span> <span data-ttu-id="5d268-213">Ancak, aynısını elde etmek yazmak için gereken gerçek bir kod çok daha küçük olacak şekilde EF çekirdek kuralları otomatik olarak bu çoğunu yapın.</span><span class="sxs-lookup"><span data-stu-id="5d268-213">However, EF Core conventions do most of this automatically, so the actual code you would need to write to achieve the same thing would be much smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="5d268-214">EF çekirdek Hi/Lo algoritması</span><span class="sxs-lookup"><span data-stu-id="5d268-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="5d268-215">Bir ilginç Yukarıdaki örnekteki kod bunu kullandığını yönüdür [Hi/Lo algoritması](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) anahtar oluşturma stratejisini olarak.</span><span class="sxs-lookup"><span data-stu-id="5d268-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="5d268-216">Hi/Lo algoritması benzersiz anahtarlar gerektiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5d268-216">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="5d268-217">Bir Özet, Hi-Aet.aet algoritması satır veritabanında hemen depolamayın sırada bağlı olarak tablo satırlarının benzersiz tanımlayıcıları atar.</span><span class="sxs-lookup"><span data-stu-id="5d268-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="5d268-218">Bu, normal sıralı veritabanıyla kimlikleri olduğu sürece tanımlayıcıları hemen kullanmaya başlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d268-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="5d268-219">Hi/Lo algoritması veritabanı yerine istemci tarafında güvenli kimlikleri oluşturmak için bir mekanizma açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d268-219">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="5d268-220">*Güvenli* bu bağlamda çakışma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5d268-220">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="5d268-221">Bu algoritma bu nedenlerle ilginç şöyledir:</span><span class="sxs-lookup"><span data-stu-id="5d268-221">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="5d268-222">İş birimi düzeni kesmez.</span><span class="sxs-lookup"><span data-stu-id="5d268-222">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="5d268-223">Gidiş dönüş yolu dizisi oluşturucuları diğer DBMS yapmak gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="5d268-223">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="5d268-224">GUID'ler kullanımı aksine bir insan okunabilir tanımlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d268-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="5d268-225">EF çekirdek destekleyen [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo yöntemiyle önceki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5d268-225">EF Core supports [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="5d268-226">Özellikleri yerine alanlarını eşleme</span><span class="sxs-lookup"><span data-stu-id="5d268-226">Mapping fields instead of properties</span></span>

<span data-ttu-id="5d268-227">Sütunları alanlarına eşlemeleri EF çekirdek 1.1 özelliğiyle varlık sınıfında herhangi bir özelliği kullanmamayı ve yalnızca bir tablodaki sütunları alanlarla eşlemek için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5d268-227">With the feature of EF Core 1.1 that maps columns to fields, it is possible to not use any properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="5d268-228">Yaygın kullanımı söz konusu varlığı erişilecek gerekmez özel alanlar herhangi bir iç durumu için olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5d268-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="5d268-229">EF 1.1 ilgili bir özellik olmayan bir alan veritabanında bir sütunun eşlemek için bir yol destekler.</span><span class="sxs-lookup"><span data-stu-id="5d268-229">EF 1.1 supports a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="5d268-230">Tek alanlarla veya bir listesi gibi koleksiyonlar ile de bunu yapabilirsiniz&lt; &gt; alan.</span><span class="sxs-lookup"><span data-stu-id="5d268-230">You can do this with single fields or also with collections, like a List&lt;&gt; field.</span></span> <span data-ttu-id="5d268-231">Bu noktaya belirtildiği daha önce etki alanı modeli sınıflarını modelleme ele, ancak bu eşlemenin önceki kodda vurgulanan PropertyAccessMode.Field yapılandırmasıyla nasıl gerçekleştirildiğini burada görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d268-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the PropertyAccessMode.Field configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a><span data-ttu-id="5d268-232">Altyapı düzeyinde gizli kimlikleri için değer nesnelerini gölge özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="5d268-232">Using shadow properties in value objects for hidden IDs at the infrastructure level</span></span>

<span data-ttu-id="5d268-233">EF çekirdek gölge özelliklerinde varlık sınıfı modelinizde var olmayan özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="5d268-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="5d268-234">Bu özelliklerin durumları ve değerlerini tamamen içinde tutulur [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) altyapı düzeyinde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5d268-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

<span data-ttu-id="5d268-235">Bir DDD açısından bakıldığında, gölge gölge özelliği birincil anahtarı olarak kimliği gizleme tarafından değeri nesneleri uygulamak için kolay bir yol özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="5d268-235">From a DDD point of view, shadow properties are a convenient way to implement value objects by hiding the ID as a shadow property primary key.</span></span> <span data-ttu-id="5d268-236">Bir değer nesnesi kimliği olmaması gereken bu önemlidir, çünkü (en azından, kimliği etki alanı modeli katmanında değer nesnelerini şekillendirme zaman sahip olmamalıdır).</span><span class="sxs-lookup"><span data-stu-id="5d268-236">This is important, because a value object should not have identity (at least, you should not have the ID in the domain model layer when shaping value objects).</span></span> <span data-ttu-id="5d268-237">Burada EF çekirdek geçerli sürümü itibariyle EF Çekirdek değer nesneler olarak uygulamak için bir yol yok noktasıdır [karmaşık türler](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), içinde EF mümkün 6.x.</span><span class="sxs-lookup"><span data-stu-id="5d268-237">The point here is that as of the current version of EF Core, EF Core does not have a way to implement value objects as [complex types](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), as is possible in EF 6.x.</span></span> <span data-ttu-id="5d268-238">Şu anda bir değer nesnesi bir gölge özelliği ayarlamak, gizli bir kimliği (birincil anahtar) sahip bir varlık olarak uygulamak gereken nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="5d268-238">That is why you currently need to implement a value object as an entity with a hidden ID (primary key) set as a shadow property.</span></span>

<span data-ttu-id="5d268-239">İçinde gördüğünüz [adresi değer nesnesi](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) eShopOnContainers içinde adresi modelinde, bir kimlik görmezsiniz:</span><span class="sxs-lookup"><span data-stu-id="5d268-239">As you can see in the [Address value object](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) in eShopOnContainers, in the Address model you do not see an ID:</span></span>

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

<span data-ttu-id="5d268-240">Ancak perde arkasında biz böylece EF çekirdek bu veriler veritabanı tablolarındaki kalıcı bir kimliği sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d268-240">But under the covers, we need to provide an ID so that EF Core is able to persist this data in the database tables.</span></span> <span data-ttu-id="5d268-241">ConfigureAddress yönteminde bunu [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) biz EF altyapı kodu ile etki alanı modeli pollute olmayan şekilde altyapı düzeyinde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5d268-241">We do that in the ConfigureAddress method of the [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) class at the infrastructure level, so we do not pollute the domain model with EF infrastructure code.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="5d268-242">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5d268-242">Additional resources</span></span>

-   <span data-ttu-id="5d268-243">**Tablo eşleme**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="5d268-243">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="5d268-244">**Entity Framework Çekirdek ile anahtarları oluşturmak için HiLo kullanmak**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="5d268-244">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="5d268-245">**Alanları yedekleme**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="5d268-245">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="5d268-246">**Steve Smith. Entity Framework Çekirdek koleksiyonlarda kapsüllenmiş**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="5d268-246">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="5d268-247">**Gölge Özellikleri**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="5d268-247">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5d268-248">[Önceki] (altyapı-Kalıcılık-katman-design.md) [sonraki] (nosql-veritabanı-Kalıcılık-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="5d268-248">[Previous] (infrastructure-persistence-layer-design.md) [Next] (nosql-database-persistence-infrastructure.md)</span></span>
