---
title: Mikro hizmet uygulama katmanı Web API kullanarak uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet uygulama katmanı Web API kullanarak uygulama
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cfca93dca0ec9d05936f4be676e27135c581de94
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="da6c1-104">Mikro hizmet uygulama katmanı Web API kullanarak uygulama</span><span class="sxs-lookup"><span data-stu-id="da6c1-104">Implementing the microservice application layer using the Web API</span></span>

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="da6c1-105">Uygulama katmana altyapı nesnelerinden eklemesine bağımlılık ekleme kullanılarak</span><span class="sxs-lookup"><span data-stu-id="da6c1-105">Using Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="da6c1-106">Daha önce belirtildiği gibi uygulama katmanı oluşturduğunuz, örneğin bir Web API projesi veya bir MVC web uygulaması projesi olarak içinde yapının parçası olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-106">As mentioned previously, the application layer can be implemented as part of the artifact you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="da6c1-107">ASP.NET Core ile yerleşik bir mikro hizmet söz konusu olduğunda, uygulama katmanı Web API kitaplığınızın genellikle olacaktır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-107">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="da6c1-108">ASP.NET Core (alt yapısına artı denetleyicilerinizi) özel uygulama katman kodunuzdan yakında ayırmak istiyorsanız, uygulama katmanı ayrı Sınıf Kitaplığı'nda koyabilir, ancak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-108">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="da6c1-109">Örneğin, uygulama katmanı kodunu sıralama mikro hizmet parçası olarak doğrudan uygulanır **Ordering.API** proje (bir ASP.NET çekirdek Web API projesi) olarak gösterildiği Şekil 9-23.</span><span class="sxs-lookup"><span data-stu-id="da6c1-109">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 9-23.</span></span>

![](./media/image20.png)

<span data-ttu-id="da6c1-110">**Şekil 9-23**.</span><span class="sxs-lookup"><span data-stu-id="da6c1-110">**Figure 9-23**.</span></span> <span data-ttu-id="da6c1-111">Uygulama katmanı Ordering.API ASP.NET çekirdek Web API projesi '</span><span class="sxs-lookup"><span data-stu-id="da6c1-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="da6c1-112">ASP.NET Core içeren basit bir [yerleşik IOC kapsayıcı](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (IServiceProvider arabirimi tarafından temsil edilen) Oluşturucu ekleme varsayılan destekleyen ve ASP.NET belirli hizmetleri dı aracılığıyla kullanılabilir yapar.</span><span class="sxs-lookup"><span data-stu-id="da6c1-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="da6c1-113">ASP.NET Core kullanan terimi *hizmet* dı eklenecek kaydettiğiniz türlerinden herhangi birini için.</span><span class="sxs-lookup"><span data-stu-id="da6c1-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="da6c1-114">Yerleşik kapsayıcının Hizmetleri, uygulamanızın başlangıç sınıfı ConfigureServices yönteminde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="da6c1-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="da6c1-115">Bağımlılıklarınız türü gerektiren hizmetlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-115">Your dependencies are implemented in the services that a type needs.</span></span>

<span data-ttu-id="da6c1-116">Tipik olarak, altyapı nesnelerinden uygulama bağımlılıkları ekleme istersiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="da6c1-117">Eklemesine oldukça tipik bir bağımlılık bir depodur.</span><span class="sxs-lookup"><span data-stu-id="da6c1-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="da6c1-118">Ancak, yaptığınız herhangi bir altyapı Bağımlılığı Ekle.</span><span class="sxs-lookup"><span data-stu-id="da6c1-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="da6c1-119">DBContext altyapı Kalıcılık nesnelerinizi uyarlamasını de olduğundan daha basit uygulamalar için doğrudan iş birimi düzeni nesnenizin (EF DbContext nesnesi) ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="da6c1-120">Aşağıdaki örnekte, .NET Core Oluşturucusu gerekli depo nesnelerde nasıl injecting görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="da6c1-121">Sonraki bölümde ele alınacaktır bir komut işleyici sınıftır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-121">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator, 
                                     IOrderRepository orderRepository, 
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ?? 
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? 
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? 
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic 
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, 
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId, 
                              message.CardNumber, message.CardSecurityNumber, 
                              message.CardHolderName, message.CardExpiration);
            
        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="da6c1-122">İşlem yürütme ve durum değişiklikleri kalıcı hale getirmek için eklenen depoları sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="da6c1-123">Bu sınıf bir komut işleyici, bir ASP.NET çekirdek Web API denetleyicisi yöntemi olup olmadığını veya önemli değildir [DDD uygulama hizmeti](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="da6c1-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="da6c1-124">Sonuç olarak, bir komut işleyici benzer bir şekilde depoları, etki alanı varlıkları ve diğer uygulama koordinasyon kullanan basit bir sınıf değil.</span><span class="sxs-lookup"><span data-stu-id="da6c1-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="da6c1-125">Tüm sözü edilen sınıflar dı kullanarak örnekte olduğu gibi aynı şekilde Oluşturucu tabanlı bağımlılık ekleme çalışır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="da6c1-126">Bağımlılık uygulama türleri ve arabirimleri veya soyutlamalar kaydetme</span><span class="sxs-lookup"><span data-stu-id="da6c1-126">Registering the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="da6c1-127">Oluşturucular eklenen nesneleri kullanmadan önce arabirimleri ve uygulama sınıflarınızı dı aracılığıyla içine eklenen nesneleri üretmek sınıfları kaydedileceği yeri bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="da6c1-128">(Dı gibi temel oluşturucu, daha önce gösterildiği gibi.)</span><span class="sxs-lookup"><span data-stu-id="da6c1-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="da6c1-129">ASP.NET Core tarafından sağlanan yerleşik IOC kapsayıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="da6c1-129">Using the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="da6c1-130">ASP.NET Core tarafından sağlanan yerleşik IOC kapsayıcı kullandığınızda, aşağıdaki kod olduğu gibi haline dosyasındaki ConfigureServices yöntemi Ekle istediğiniz türlerini kaydedin:</span><span class="sxs-lookup"><span data-stu-id="da6c1-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="da6c1-131">En yaygın düzeni IOC kapsayıcısında türlerini kaydetme türleri çifti kaydetmek için olduğunda — bir arabirim ve onun ilişkili uygulama sınıfı.</span><span class="sxs-lookup"><span data-stu-id="da6c1-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="da6c1-132">Ardından herhangi Oluşturucusu aracılığıyla IOC kapsayıcısından bir nesne istediğinde, belirli bir arabirim türünde bir nesne isteyin.</span><span class="sxs-lookup"><span data-stu-id="da6c1-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="da6c1-133">Örneği için oluşturucular herhangi bir bağımlılık IMyCustomRepository (arabirimi veya soyutlama) varsa, IOC kapsayıcı MyCustomSQLServerRepository uygulama örneğini ekleme, önceki örnekte, son satır durumları sınıf.</span><span class="sxs-lookup"><span data-stu-id="da6c1-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="da6c1-134">Otomatik türleri kaydı için Scrutor kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="da6c1-134">Using the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="da6c1-135">DI .NET Core kullanırken, bir derlemeyi tarayın ve türlerinden kurala göre otomatik olarak kaydetmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="da6c1-136">ASP.NET Core bu özellik şu anda kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="da6c1-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="da6c1-137">Ancak, kullanabileceğiniz [Scrutor](https://github.com/khellang/Scrutor) kitaplığı konusu.</span><span class="sxs-lookup"><span data-stu-id="da6c1-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="da6c1-138">IOC kapsayıcısında kayıtlı olması gereken türleri düzinelerce olduğunda bu kullanışlı bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="da6c1-139">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="da6c1-139">Additional resources</span></span>

-   <span data-ttu-id="da6c1-140">**Matthew King. Hizmetleri Scrutor ile kaydediliyor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span><span class="sxs-lookup"><span data-stu-id="da6c1-140">**Matthew King. Registering services with Scrutor**
[*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span></span>

<!-- -->

-   <span data-ttu-id="da6c1-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="da6c1-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="da6c1-142">GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="da6c1-142">GitHub repo.</span></span>
    [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a><span data-ttu-id="da6c1-143">Autofac IOC kapsayıcı olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="da6c1-143">Using Autofac as an IoC container</span></span>

<span data-ttu-id="da6c1-144">Ayrıca ek IOC kapsayıcılar kullanma ve sıralama mikro hizmet kullanan eShopOnContainers içinde olduğu gibi ASP.NET Core kanalının takın [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="da6c1-144">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="da6c1-145">Autofac kullanırken, genellikle kayıt türleri arasında birden fazla sınıf kitaplıkları dağıtılmış uygulama türleri sahip olduğunuz, türlerinizi nerede olduğunuza bağlı olarak birden çok dosya arasında bölmek izin modülleri aracılığıyla türleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="da6c1-145">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="da6c1-146">Örneğin, aşağıdaki gibidir [Autofac uygulama modülü](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) için [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) eklemesine istediğiniz türleriyle projesi.</span><span class="sxs-lookup"><span data-stu-id="da6c1-146">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="da6c1-147">Kavramları ve kayıt işlemine çok benzer şekilde, yerleşik ASP.NET Core iOS kapsayıcıyla türleri kaydedebilirsiniz, ancak Autofac kullanırken sözdizimi biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-147">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core iOS container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="da6c1-148">Örnek kodda IOrderRepository soyutlama uygulama sınıfı OrderRepository birlikte kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-148">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="da6c1-149">Bu, bağımlılık IOrderRepository soyutlama veya arabirimi aracılığıyla bir kurucusu bildirme her IOC kapsayıcı OrderRepository sınıfının bir örneğini ekleme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-149">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="da6c1-150">Bir örneği aynı hizmet veya bağımlılık istekler arasında nasıl paylaşılacağını örneği kapsam türü belirler.</span><span class="sxs-lookup"><span data-stu-id="da6c1-150">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="da6c1-151">Bir istek için bağımlılık yapıldığında IOC kapsayıcı aşağıdaki döndürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="da6c1-151">When a request is made for a dependency, the IoC container can return the following:</span></span>

-   <span data-ttu-id="da6c1-152">Ömür kapsam başına tek bir örnek (ASP.NET Core IOC kapsayıcı olarak başvurulan *kapsamlı*).</span><span class="sxs-lookup"><span data-stu-id="da6c1-152">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

-   <span data-ttu-id="da6c1-153">Yeni bir örneğini bağımlılık başına (ASP.NET Core IOC kapsayıcı olarak başvurulan *geçici*).</span><span class="sxs-lookup"><span data-stu-id="da6c1-153">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

-   <span data-ttu-id="da6c1-154">IOC kapsayıcı kullanan tüm nesneler arasında paylaşılan tek bir örnek (ASP.NET Core IOC kapsayıcı olarak başvurulan *singleton*).</span><span class="sxs-lookup"><span data-stu-id="da6c1-154">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="da6c1-155">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="da6c1-155">Additional resources</span></span>

-   <span data-ttu-id="da6c1-156">**ASP.NET Core bağımlılık ekleme giriş**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span><span class="sxs-lookup"><span data-stu-id="da6c1-156">**Introduction to Dependency Injection in ASP.NET Core**
[*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span></span>

-   <span data-ttu-id="da6c1-157">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="da6c1-157">**Autofac.**</span></span> <span data-ttu-id="da6c1-158">Resmi belge.</span><span class="sxs-lookup"><span data-stu-id="da6c1-158">Official documentation.</span></span>
    [*http://docs.autofac.org/en/latest/*](http://docs.autofac.org/en/latest/)

-   <span data-ttu-id="da6c1-159">**ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamlarla - Cesar de la Torre karşılaştırma.**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-159">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="implementing-the-command-and-command-handler-patterns"></a><span data-ttu-id="da6c1-160">Komut ve komut işleyici desenleri uygulama</span><span class="sxs-lookup"><span data-stu-id="da6c1-160">Implementing the Command and Command Handler patterns</span></span>

<span data-ttu-id="da6c1-161">Önceki bölümde gösterilen Oluşturucusu aracılığıyla dı örnekte IOC kapsayıcı bir sınıf oluşturucuda aracılığıyla depoları injecting oluştu.</span><span class="sxs-lookup"><span data-stu-id="da6c1-161">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="da6c1-162">Ancak, tam olarak burada bunlar eklenmiş?</span><span class="sxs-lookup"><span data-stu-id="da6c1-162">But exactly where were they injected?</span></span> <span data-ttu-id="da6c1-163">Bir basit Web API'si (örneğin, katalog mikro hizmet eShopOnContainers içinde), siz bunları MVC denetleyicileri düzeyinde bir denetleyici Oluşturucu yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-163">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers level, in a controller constructor.</span></span> <span data-ttu-id="da6c1-164">Bu bölümde, ancak ilk kodda ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) eShopOnContainers Ordering.API hizmetinde sınıfından), bağımlılıklar ekleme belirli bir komut oluşturucu kullanılarak yapılır işleyici.</span><span class="sxs-lookup"><span data-stu-id="da6c1-164">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="da6c1-165">Bize açıklayan bir komut işleyici ne olduğunu ve neden bunu kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-165">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="da6c1-166">Komut düzeni, bu kılavuzun önceki bölümlerinde sunulan CQRS düzeni doğası gereği ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-166">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="da6c1-167">CQRS iki kenara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-167">CQRS has two sides.</span></span> <span data-ttu-id="da6c1-168">Basitleştirilmiş sorgularıyla kullanarak sorguları, ilk alanıdır [Dapper](https://github.com/StackExchange/dapper-dot-net) daha önce açıklanan mikro ORM.</span><span class="sxs-lookup"><span data-stu-id="da6c1-168">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="da6c1-169">İşlemler için başlangıç noktası ve giriş kanaldan hizmetin dışında olan komutları ikinci bir alandır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-169">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="da6c1-170">Şekil 9-24'te gösterildiği gibi düzeni istemci tarafında, komutları kabul dayalıdır etki alanı modeli kurallara göre işlemeden ve son olarak durumları işlemleri ile kalıcı yapma.</span><span class="sxs-lookup"><span data-stu-id="da6c1-170">As shown in Figure 9-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![](./media/image21.png)

<span data-ttu-id="da6c1-171">**Şekil 9-24**.</span><span class="sxs-lookup"><span data-stu-id="da6c1-171">**Figure 9-24**.</span></span> <span data-ttu-id="da6c1-172">Komutları veya CQRS desende "işlem yan" üst düzey görünümü</span><span class="sxs-lookup"><span data-stu-id="da6c1-172">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="da6c1-173">Komut sınıfı</span><span class="sxs-lookup"><span data-stu-id="da6c1-173">The command class</span></span>

<span data-ttu-id="da6c1-174">Sistem durumunu değiştiren bir eylem gerçekleştirmek üzere sistem için bir istek komuttur.</span><span class="sxs-lookup"><span data-stu-id="da6c1-174">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="da6c1-175">Komutlar, kesinlik temelli ve yalnızca bir kez işlenmesi.</span><span class="sxs-lookup"><span data-stu-id="da6c1-175">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="da6c1-176">Komutları imperatives olduğundan, bunlar genellikle bir fiil kesinlik temelli ruh (örneğin, "oluşturma" veya "güncelleştir") olarak adlandırılır ve CreateOrderCommand gibi toplama türü içerebilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-176">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="da6c1-177">Bir olay, bir komut bir olgu Geçmişten değil; yalnızca bir istek ve böylece reddetti.</span><span class="sxs-lookup"><span data-stu-id="da6c1-177">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="da6c1-178">İşlem Yöneticisi'ni bir eylemi gerçekleştirmek için bir toplama yönlendirerek, komutları bir isteği başlatan kullanıcı sonucunda UI veya bir işlem yöneticisi kaynaklanan.</span><span class="sxs-lookup"><span data-stu-id="da6c1-178">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="da6c1-179">Bir önemli bir komutu tek bir alıcı tarafından yalnızca bir kez işlenmesi gerektiğini özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-179">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="da6c1-180">Bir komut tek eylem veya uygulamada gerçekleştirmek istediğiniz işlem olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-180">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="da6c1-181">Örneğin, aynı sırası oluşturma komutunu birden çok kez işlenmesi gerektiğini değil.</span><span class="sxs-lookup"><span data-stu-id="da6c1-181">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="da6c1-182">Komutlar ve olayları arasında önemli bir fark budur.</span><span class="sxs-lookup"><span data-stu-id="da6c1-182">This is an important difference between commands and events.</span></span> <span data-ttu-id="da6c1-183">Birçok sistemleri veya mikro olayda ilgileniyor çünkü olayları birden çok kez işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-183">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="da6c1-184">Ayrıca, komut ıdempotent kullanılamaz durumda olduğunda bir komutu yalnızca bir kez işlenmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-184">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="da6c1-185">Birden çok kez sonucu komut yapısını nedeniyle veya sistem komut işleme biçimi nedeniyle değiştirmeden yürütülmek üzere ise bir komut ıdempotent olur.</span><span class="sxs-lookup"><span data-stu-id="da6c1-185">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="da6c1-186">Komutlarınızı yapmak için iyi bir uygulamadır ve etki alanınızın iş kuralları ve invariants altında mantıklıdır ıdempotent güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-186">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="da6c1-187">Örneğin, herhangi bir nedenle (yeniden deneme mantığı, korsan, vb.), sisteminizi birden çok kez aynı CreateOrder komutu ulaşırsa aynı örneği kullanmak için tanımlamak ve birden çok sipariş oluşturmayın sağlamak mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-187">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="da6c1-188">Bunu yapmak için bir tür kimlik işlemlerinin ekleme ve komut veya güncelleştirme işlenmiş olup olmadığını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-188">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="da6c1-189">Tek bir alıcı bir komut Gönder; bir komut yayımlamayın.</span><span class="sxs-lookup"><span data-stu-id="da6c1-189">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="da6c1-190">Yayımlama olan bir olgu durum tümleştirme olaylarını — bir şey gerçekleştirilmedi ve olabilir Olay alıcıları için ilginç.</span><span class="sxs-lookup"><span data-stu-id="da6c1-190">Publishing is for integration events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="da6c1-191">Olayları söz konusu olduğunda, publisher hakkında olay veya bunların yerine getirebileceği alıcıları almak hiçbir sorunları vardır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-191">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="da6c1-192">Ancak zaten önceki bölümlerinde sunulan farklı bir öykü tümleştirme olaylardır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-192">But integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="da6c1-193">Bir komut, veri alanları veya koleksiyonları bu komutu yürütmek için gerekli tüm bilgileri içeren bir sınıf ile uygulanır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-193">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="da6c1-194">Özel bir tür, veri aktarım nesnesini (DTO), özellikle istek değişiklikleri veya işlemleri için kullanılan bir komuttur.</span><span class="sxs-lookup"><span data-stu-id="da6c1-194">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="da6c1-195">Komutu tam olarak komut ve hiçbir şey daha fazla işlemek için gerekli bilgileri temel alır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-195">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="da6c1-196">Aşağıdaki örnek, Basitleştirilmiş CreateOrderCommand sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-196">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="da6c1-197">Bu sipariş mikro hizmet eShopOnContainers içinde kullanılan sabit bir komuttur.</span><span class="sxs-lookup"><span data-stu-id="da6c1-197">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="da6c1-198">Temel olarak, komut sınıfı etki alanı model nesneleri kullanarak bir iş işlemi gerçekleştirmek için gereken tüm verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-198">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="da6c1-199">Bu nedenle, yalnızca salt okunur veri ve davranışı yok içeren veri yapılarını komutlardır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-199">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="da6c1-200">Komut adını amacını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-200">The command’s name indicates its purpose.</span></span> <span data-ttu-id="da6c1-201">C gibi birden çok dilde\#, komutları sınıfları olarak temsil, ancak bunlar gerçek nesne yönelimli algılama true sınıflarda değildir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-201">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="da6c1-202">Beklenen kullanım doğrudan etki alanı modeli tarafından işlenen olduğundan ek bir özellik komutları, sabittir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-202">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="da6c1-203">Kendi tahmini ömrü boyunca değiştirmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="da6c1-203">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="da6c1-204">Bir c\# sınıfı, girişi elde edilebilir herhangi ayarlayıcılar veya iç durum değişikliği diğer yöntemleri zorunluluğunu ortadan kaldırarak.</span><span class="sxs-lookup"><span data-stu-id="da6c1-204">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="da6c1-205">Örneğin, bir sıra oluşturmak için komut sınıfı oluşturmak istediğiniz sipariş veri açısından büyük olasılıkla benzer, ancak aynı öznitelikleri muhtemelen gerekmez.</span><span class="sxs-lookup"><span data-stu-id="da6c1-205">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="da6c1-206">Örneği için CreateOrderCommand sırasını henüz oluşturulmadı çünkü bir sıra kimliği yok.</span><span class="sxs-lookup"><span data-stu-id="da6c1-206">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="da6c1-207">Birçok komut sınıfları basit, yalnızca birkaç alanları değiştirilmesi gereken bazı durumu hakkında gerektiren olabilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-207">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="da6c1-208">Bu durumda, "işlem" için bir sıra durumunu yalnızca değiştiriyorsanız "Ücretli" veya "aşağıdakine benzer bir komut kullanarak sevk edilen" olacaktır:</span><span class="sxs-lookup"><span data-stu-id="da6c1-208">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="da6c1-209">Bazı geliştiriciler kendi kullanıcı Arabirimi isteği nesneleri kendi komut DTOs ayrı yapın, ancak sağlasa da, yalnızca tercih olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-209">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="da6c1-210">Can sıkıcı ayrımı konuya eklenen değerine sahip olan ve neredeyse tam olarak aynı şekilde nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-210">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="da6c1-211">Örneğin, eShopOnContainers içinde bazı komutlar doğrudan istemci tarafındaki gelir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-211">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="da6c1-212">Komut işleyici sınıfı</span><span class="sxs-lookup"><span data-stu-id="da6c1-212">The Command Handler class</span></span>

<span data-ttu-id="da6c1-213">Her komut için bir özel bir komut işleyici sınıfı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-213">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="da6c1-214">Düzeni nasıl çalıştığını ve burada komut nesnesi, etki alanı nesnelerini ve altyapı depo nesneleri kullanacağı adrestir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-214">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="da6c1-215">Komut gerçekte CQRS ve DDD açısından uygulama katmanı Kalp işleyicidir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-215">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="da6c1-216">Ancak, tüm etki alanı mantığı içinde yer alan etki alanı sınıfları yer almalıdır — toplama kökleri (kök varlıklar) içinde alt varlıkları veya [etki alanı Hizmetleri](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ancak komut işleyici değil içinde olduğu uygulamadan sınıfı katmanı.</span><span class="sxs-lookup"><span data-stu-id="da6c1-216">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="da6c1-217">Bir komut işleyici komutu alır ve bir sonuç kullanılan toplam değer alır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-217">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="da6c1-218">Sonuç, komutun başarılı yürütme ya da bir özel durum olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-218">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="da6c1-219">Bir özel durum söz konusu olduğunda sistem durumu değiştirilmeden olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-219">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="da6c1-220">Komut işleyici genellikle aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="da6c1-220">The command handler usually takes the following steps:</span></span>

-   <span data-ttu-id="da6c1-221">Komut nesnesi bir DTO gibi alır (gelen [Dünyası](https://en.wikipedia.org/wiki/Mediator_pattern) veya başka bir altyapı nesne).</span><span class="sxs-lookup"><span data-stu-id="da6c1-221">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

-   <span data-ttu-id="da6c1-222">Bu komutu (Dünyası tarafından doğrulanmamış varsa) geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="da6c1-222">It validates that the command is valid (if not validated by the mediator).</span></span>

-   <span data-ttu-id="da6c1-223">Geçerli komut hedefi olan birleşik kök örneği başlatır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-223">It instantiates the aggregate root instance that is the target of the current command.</span></span>

-   <span data-ttu-id="da6c1-224">Komuttan gerekli verileri alma toplama kök örneğinde yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="da6c1-224">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

-   <span data-ttu-id="da6c1-225">Bu toplama, ilgili veritabanı için yeni durumu devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-225">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="da6c1-226">Bu son işlem gerçek bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-226">This last operation is the actual transaction.</span></span>

<span data-ttu-id="da6c1-227">Genellikle, bir komut işleyici toplama kökü (kök varlık) tarafından yönetilen tek bir toplama ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-227">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="da6c1-228">Birden çok toplamalar tek bir komut alma tarafından etkilenir, durumları veya eylemler arasında birden çok toplamalar yaymak için etki alanı olayları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-228">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="da6c1-229">Burada önemli olan nokta, bir komut işlenirken, tüm etki alanı mantığı etki alanı model içinde (toplamalar) tam olarak kapsüllenmiş ve birim testi için hazır olması gerektiğini ' dir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-229">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="da6c1-230">Komut işleyici yalnızca etki alanı modeli veritabanından almanın bir yolu olarak ve model değiştirildiğinde değişiklikleri kalıcı hale getirmek için altyapı katman (depoları) bildirmek için son adımı olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-230">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="da6c1-231">Bu yaklaşımın avantajı uygulama veya tesisat düzeyi (komut işleyicileri, Web API altyapı Katmanlar kodunu değiştirmeden bir yalıtılmış, tam olarak kapsüllenmiş, zengin, davranış etki alanı modelinde etki alanı mantığı yeniden emin olan depoları, vb.).</span><span class="sxs-lookup"><span data-stu-id="da6c1-231">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="da6c1-232">Komut işleyicileri çok fazla mantığı ile karmaşık aldığınızda, kod kokusu olabilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-232">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="da6c1-233">Bunları gözden geçirin ve etki alanı mantığı bulursanız, o etki alanı davranışı etki alanı nesnelerini (Birleşik kök ve alt varlık) yöntemlerinin taşımak için kodu yeniden düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="da6c1-233">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="da6c1-234">Bir komut işleyici sınıfın örnek olarak, aşağıdaki kod bu bölümün başında gördüğünüz aynı CreateOrderCommandHandler sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-234">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="da6c1-235">Bu durumda, tanıtıcı yöntem ve etki alanı model nesneleri/toplamalar işlemleriyle vurgulamak istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-235">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator, 
                                     IOrderRepository orderRepository, 
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ?? 
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? 
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? 
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic 
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, 
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId, 
                              message.CardNumber, message.CardSecurityNumber, 
                              message.CardHolderName, message.CardExpiration);
            
        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="da6c1-236">Bir komut işleyici gerçekleştirmeniz ek adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="da6c1-236">These are additional steps a command handler should take:</span></span>

-   <span data-ttu-id="da6c1-237">Komutunun veri toplama kökün yöntemleri ve davranış ile çalışması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="da6c1-237">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

-   <span data-ttu-id="da6c1-238">Dahili olarak etki alanı nesnelerinde işlem yürütülür, ancak bir komut işleyici açısından saydam olan etki alanı olayları yükseltin.</span><span class="sxs-lookup"><span data-stu-id="da6c1-238">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

-   <span data-ttu-id="da6c1-239">Toplama 's işlem sonucu başarılı olursa ve işlem tamamlandıktan sonra tümleştirme olayları komut işleyici yükseltin.</span><span class="sxs-lookup"><span data-stu-id="da6c1-239">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events command handler.</span></span> <span data-ttu-id="da6c1-240">(Bu da depoları gibi altyapı sınıflar tarafından oluşturulması.)</span><span class="sxs-lookup"><span data-stu-id="da6c1-240">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="da6c1-241">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="da6c1-241">Additional resources</span></span>

-   <span data-ttu-id="da6c1-242">**İşareti Seemann. Değil nesne odaklı uygulamalar sınırlarında**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, ApplicationsareNotObject dayalı /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-242">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented**
[*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span></span>

-   <span data-ttu-id="da6c1-243">**Komutlar ve olayları**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span><span class="sxs-lookup"><span data-stu-id="da6c1-243">**Commands and events**
[*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span></span>

-   <span data-ttu-id="da6c1-244">**Bir komut işleyici ne yapar?**
    [*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span><span class="sxs-lookup"><span data-stu-id="da6c1-244">**What does a command handler do?**
[*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span></span>

-   <span data-ttu-id="da6c1-245">**Jimmy Bogard. Etki alanı komutu desenleri – işleyicileri**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-245">**Jimmy Bogard. Domain Command Patterns – Handlers**
[*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span></span>

-   <span data-ttu-id="da6c1-246">**Jimmy Bogard. Etki alanı komutu desenleri – doğrulama**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-246">**Jimmy Bogard. Domain Command Patterns – Validation**
[*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span></span>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="da6c1-247">Komut işlemi ardışık: bir komut işleyici tetikleme</span><span class="sxs-lookup"><span data-stu-id="da6c1-247">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="da6c1-248">Sonraki Soru bir komut işleyici çağırma şeklidir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-248">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="da6c1-249">El ile ilgili her ASP.NET Core denetleyicisinden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-249">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="da6c1-250">Ancak, bir yaklaşım çok olacaktır eşleşmiş ve ideal değil.</span><span class="sxs-lookup"><span data-stu-id="da6c1-250">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="da6c1-251">Önerilen seçenek olan diğer iki ana seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="da6c1-251">The other two main options, which are the recommended options, are:</span></span>

-   <span data-ttu-id="da6c1-252">Bellek içi Dünyası düzeni yapı.</span><span class="sxs-lookup"><span data-stu-id="da6c1-252">Through an in-memory Mediator pattern artifact.</span></span>

-   <span data-ttu-id="da6c1-253">Bir zaman uyumsuz ileti sırası ile denetleyicileri ve işleyicileri Between.</span><span class="sxs-lookup"><span data-stu-id="da6c1-253">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="da6c1-254">Komut ardışık düzeninde Dünyası deseni (bellek içi) kullanma</span><span class="sxs-lookup"><span data-stu-id="da6c1-254">Using the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="da6c1-255">Şekil 9-25 gösterildiği gibi bir CQRS yaklaşım, komutun veya alınma DTO türüne göre sağ komut işleyici yeniden yönlendirmek akıllı bir bellek içi veri yoluna benzer akıllı bir Dünyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="da6c1-255">As shown in Figure 9-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="da6c1-256">Bileşenler arasındaki tek siyah oklar (dı eklenen çoğu durumda,) nesneler arasındaki bağımlılıkları ile ilgili kendi etkileşimleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="da6c1-256">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![](./media/image22.png)

<span data-ttu-id="da6c1-257">**Şekil 9-25**.</span><span class="sxs-lookup"><span data-stu-id="da6c1-257">**Figure 9-25**.</span></span> <span data-ttu-id="da6c1-258">Tek bir CQRS mikro hizmet işleminde Dünyası desen kullanma</span><span class="sxs-lookup"><span data-stu-id="da6c1-258">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="da6c1-259">Kullanmakta Dünyası düzeni mantıklı Kurumsal uygulamalarda istekleri işlemek karmaşık alabilirsiniz nedenidir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-259">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="da6c1-260">Çapraz kesme sorunları günlüğe kaydetme, doğrulama, Denetim ve güvenlik gibi açık bir sayısı eklemek kullanabilmek ister.</span><span class="sxs-lookup"><span data-stu-id="da6c1-260">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="da6c1-261">Bu durumlarda, bir Dünyası ardışık kullanır (bkz [Dünyası düzeni](https://en.wikipedia.org/wiki/Mediator_pattern)) bu ek davranışları veya çapraz kesme sorunları için bir yol sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="da6c1-261">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="da6c1-262">"Nasıl" Bu işlemi yalıtan bir nesne bir Dünyası olduğu: durumuna bağlı yürütme koordinatları, bir komut işleyici yolu çağrılır ya da yük işleyicisine sağlayın.</span><span class="sxs-lookup"><span data-stu-id="da6c1-262">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="da6c1-263">Dünyası bileşeniyle arası kesme sorunları merkezi ve saydam bir şekilde dekoratörler uygulayarak uygulayabilirsiniz (veya [kanal davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) beri [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="da6c1-263">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="da6c1-264">Daha fazla bilgi için bkz: [oluşturma öğesi düzeni](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="da6c1-264">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="da6c1-265">Dekoratörler ve davranışları benzer [en boy odaklı programlama (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)Dünyası bileşen tarafından yönetilen bir özel işlem ardışık düzene uygulanan yalnızca.</span><span class="sxs-lookup"><span data-stu-id="da6c1-265">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="da6c1-266">Çapraz kesme sorunları uygulayan AOP yönlerine göre uygulanır *en boy weavers* nesne araması yakalanması temelinde ya da derleme zamanında eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="da6c1-266">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="da6c1-267">Nasıl AOP çalıştığını görmek kolay değildir çünkü her iki tipik AOP yaklaşım bazen "Sihirli gibi" iş söylenir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-267">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="da6c1-268">Önemli sorunları veya hatalar ile ilgilenirken, AOP hata ayıklaması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-268">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="da6c1-269">Öte yandan, hata ayıklama çok daha tahmin edilebilir ve kolay şekilde bu dekoratörler/davranışları açık ve yalnızca Dünyası bağlamında uygulandı.</span><span class="sxs-lookup"><span data-stu-id="da6c1-269">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="da6c1-270">Örneğin, mikro hizmet sıralama eShopOnContainers şu iki örnek davranışları, uygulanan bir [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı ve bir [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="da6c1-270">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="da6c1-271">Uygulama davranışları eShopOnContainers nasıl uyguladığını gösteren sonraki bölümde anlatılmıştır [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors).</span><span class="sxs-lookup"><span data-stu-id="da6c1-271">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers implements [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="da6c1-272">İleti kuyrukları (giden işlem dışı) komutunun ardışık düzeninde kullanma</span><span class="sxs-lookup"><span data-stu-id="da6c1-272">Using message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="da6c1-273">Aracıların veya ileti kuyrukları, Şekil 9-26'da gösterildiği gibi göre zaman uyumsuz iletileri kullanan başka bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-273">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 9-26.</span></span> <span data-ttu-id="da6c1-274">Bu seçenek ayrıca komut işleyici önceki Dünyası bileşeni ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-274">That option could also be combined with the mediator component right before the command handler.</span></span>

![](./media/image23.png)

<span data-ttu-id="da6c1-275">**Şekil 9-26**.</span><span class="sxs-lookup"><span data-stu-id="da6c1-275">**Figure 9-26**.</span></span> <span data-ttu-id="da6c1-276">İleti kuyrukları (dışında işlem ve işlemler arası iletişim) CQRS komutları ile kullanma</span><span class="sxs-lookup"><span data-stu-id="da6c1-276">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="da6c1-277">Ardışık düzen iki süreçleriyle bölme gerekecek çünkü komutları daha kabul edecek şekilde sıralar, komutunun ardışık düzen, karmaşık hale iletiyi kullanarak dış ileti sırası yoluyla bağlı.</span><span class="sxs-lookup"><span data-stu-id="da6c1-277">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="da6c1-278">Yine de, ölçeklenebilirlik ve performans zaman uyumsuz Mesajlaşma göre iyileştirilmiştir ihtiyacınız varsa kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-278">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="da6c1-279">Şekil 9-26 durumunda göz önünde bulundurun, denetleyici yalnızca sıraya komutu ileti gönderir ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="da6c1-279">Consider that in the case of Figure 9-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="da6c1-280">Ardından komut işleyicileri kendi hızlarında iletileri işleyin.</span><span class="sxs-lookup"><span data-stu-id="da6c1-280">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="da6c1-281">Diğer bir deyişle harika bir avantajı sıraların: hiper ölçeklenebilirlik gerekli, istediğiniz hisse veya herhangi bir giriş veri hacmi yüksek senaryoyla gibi olduğunda ileti sırası durumlarda bir arabellek olarak çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-281">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="da6c1-282">Ancak, zaman uyumsuz ileti kuyrukları yapısı nedeniyle, başarı veya başarısızlık komutunun işleminin hakkında istemci uygulamasıyla iletişim kurmak nasıl ekleneceğini gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-282">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="da6c1-283">Bir kural olarak, hiçbir zaman "yangın ve unut" komutları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-283">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="da6c1-284">Her iş uygulamasının bir komutu başarıyla, işlenen veya en az doğrulandı ve kabul durumunda bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-284">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="da6c1-285">Bu nedenle, bir zaman uyumsuz kuyruğa gönderilen bir komut iletisi doğrulandıktan sonra istemciye yanıt yapamamasına karmaşıklık işlem çalıştırdıktan sonra işlemin sonucunu döndürür bir işlemdeki komutu işlemi ile karşılaştırıldığında, sisteminizi ekler.</span><span class="sxs-lookup"><span data-stu-id="da6c1-285">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="da6c1-286">Kuyrukları kullanma, ek bileşenleri ve özel iletişim sisteminizde gerektirecektir diğer işlem sonucu iletileri komutu sürecinde sonuç gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-286">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="da6c1-287">Ayrıca, zaman uyumsuz, çoğu durumda, aşağıdaki ilginç exchange Burtsev Alexey Greg Young arasındaki açıklandığı şekilde gerekebilecek değil tek yönlü komutları komutlardır bir [çevrimiçi konuşma](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="da6c1-287">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

<span data-ttu-id="da6c1-288">\[Burtsev Alexey\] burada kişiler zaman uyumsuz komut işleme veya bunu yapmak için herhangi bir nedenle Mesajlaşma tek yönlü komutunu kullanın kodu çok sayıda bulabilirim (bazı uzun işlemi yaptıklarını değil, dış zaman uyumsuz kod yürütme değil, bile uygulama geçmez ileti veri yolu kullanılmasını sınır).</span><span class="sxs-lookup"><span data-stu-id="da6c1-288">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="da6c1-289">Neden bu gereksiz karmaşıklığı tanıtmak?</span><span class="sxs-lookup"><span data-stu-id="da6c1-289">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="da6c1-290">Ve gerçekte, çoğu durumda düzgün çalışır ancak ı komut işleyicileri o ana kadarki engelleme ile CQRS kod örneği görmediyseniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-290">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>

<span data-ttu-id="da6c1-291">\[Greg Young\] \[... \] zaman uyumsuz bir komutu yok; gerçekten başka bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-291">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="da6c1-292">I ne bana gönderdiğiniz kabul ediyor ve kabul etmiyorum bir olay oluştur gerekir artık, bana bir şeyler belirten değildir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-292">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something.</span></span> <span data-ttu-id="da6c1-293">Bana bir şey bitti söyleyen olduğunu.</span><span class="sxs-lookup"><span data-stu-id="da6c1-293">It's you telling me something has been done.</span></span> <span data-ttu-id="da6c1-294">Bu bir hafif fark ilk gibi görünüyor, ancak birçok etkilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-294">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="da6c1-295">Hataları göstermek için basit bir yolu olduğundan zaman uyumsuz komutları bir sistem karmaşıklığını önemli ölçüde artırır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-295">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="da6c1-296">Bu nedenle, zaman uyumsuz komutları dışındaki ölçekleme gereksinimleri gerektiğinde veya özel durumlarda Mesajlaşma aracılığıyla iç mikro iletişim kurarken önerilmez.</span><span class="sxs-lookup"><span data-stu-id="da6c1-296">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="da6c1-297">Bu durumda, hatalar için ayrı bir raporlama ve kurtarma sistemi tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-297">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="da6c1-298">EShopOnContainers ilk sürümünde, biz alınan HTTP isteklerini başlatıldı ve Dünyası düzeni tarafından yönlendirilen zaman uyumlu komut işleme kullanmaya karar vermiştir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-298">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="da6c1-299">Kolayca sağlayan başarı veya başarısızlık işlemin olarak döndürmek [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) uygulaması.</span><span class="sxs-lookup"><span data-stu-id="da6c1-299">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="da6c1-300">Herhangi bir durumda, bu uygulamanın veya mikro'nın iş gereksinimlerine göre kararı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-300">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="da6c1-301">Komut işlemi ardışık düzen Dünyası deseniyle (MediatR) uygulama</span><span class="sxs-lookup"><span data-stu-id="da6c1-301">Implementing the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="da6c1-302">Örnek uygulama, bu kılavuz kullanılarak sürücü komutu alımı ve rota komutlarda sağ komut işleyicileri için bellek Dünyası düzene göre işlem içi ardışık düzeni önerir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-302">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="da6c1-303">Kılavuz, ayrıca uygulama önerir [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) arası kesme sorunları ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="da6c1-303">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="da6c1-304">.NET Core uygulama için Dünyası deseni uygulayan birden fazla açık kaynak kitaplıkları kullanılabilir vardır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-304">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="da6c1-305">Bu kılavuzda kullanılan kitaplık [MediatR](https://github.com/jbogard/MediatR) açık kaynak kitaplığı (Jimmy Bogard tarafından oluşturulan), ancak başka bir yaklaşım kullanır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-305">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="da6c1-306">MediatR dekoratörler veya davranışları uygulanırken bir komutu gibi bellek içi iletileri işlemek izin veren küçük ve basit bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-306">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="da6c1-307">Dünyası desenini kullanarak ve yardımcı olur bağ azaltmak için otomatik olarak o çalışma gerçekleştirir işleyici bağlanma sırasında istenen iş sorunları yalıtmak için — bu durumda, komut işleyicileri için.</span><span class="sxs-lookup"><span data-stu-id="da6c1-307">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="da6c1-308">Bu kılavuzu gözden geçirirken Dünyası deseni kullanılacak başka bir iyi neden Jimmy Bogard tarafından açıklandığı:</span><span class="sxs-lookup"><span data-stu-id="da6c1-308">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

<span data-ttu-id="da6c1-309">Düşünüyorum burada sınama tümleştirilmediği olabilir – sisteminizi davranışını iyi tutarlı penceresi sağlar.</span><span class="sxs-lookup"><span data-stu-id="da6c1-309">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="da6c1-310">İstek içinde yanıt genişletme. Biz bu en boy tutarlı bir şekilde testleri davranmakta binada oldukça değerli buldunuz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-310">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="da6c1-311">İlk olarak, bir örnek Webapı denetleyicisinde burada gerçekten Dünyası nesne kullanırsınız bakalım.</span><span class="sxs-lookup"><span data-stu-id="da6c1-311">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="da6c1-312">Dünyası nesne kullanmadıysanız, tüm bağımlılıkları Bu denetleyici için bir Günlükçü nesnesi ve diğerleri gibi eklemesine gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-312">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="da6c1-313">Bu nedenle, Oluşturucusu oldukça karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-313">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="da6c1-314">Diğer taraftan, denetleyicinizin Oluşturucusu Dünyası nesne kullanırsanız, çok daha basit, yalnızca birkaç bağımlılıklar aşağıdaki örnekteki gibi çapraz kesme işlemi her sahipse, pek çok bağımlılık yerine olabilir:</span><span class="sxs-lookup"><span data-stu-id="da6c1-314">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator, 
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

<span data-ttu-id="da6c1-315">Dünyası temiz ve yalın bir Web API denetleyicisi yapıcı sağlar görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-315">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="da6c1-316">Ayrıca, denetleyici yöntemlerinde Dünyası nesnesine bir komut göndermek için kodu neredeyse tek bir çizgi bulunur:</span><span class="sxs-lookup"><span data-stu-id="da6c1-316">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost] 
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand 
                                                               runOperationCommand) 
{
    var commandResult = await _mediator.SendAsync(runOperationCommand); 

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implementing-idempotent-commands"></a><span data-ttu-id="da6c1-317">Idempotent komutları uygulama</span><span class="sxs-lookup"><span data-stu-id="da6c1-317">Implementing idempotent Commands</span></span>

<span data-ttu-id="da6c1-318">EShopOnContainers içinde yukarıdaki'den daha gelişmiş bir örnek sıralama mikro hizmet CreateOrderCommand nesnesinden gönderilemedi.</span><span class="sxs-lookup"><span data-stu-id="da6c1-318">In eShopOnContainers, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="da6c1-319">Ancak sıralama iş sürecini biraz daha karmaşıktır ve Örneğimizde, aslında Sepeti mikro başlar olduğundan, bu eylem CreateOrderCommand nesne gönderilmesi adlı bir entegrasyonu olay işleyiciden gerçekleştirilir [ UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) yerine basit bir Webapı denetleyicisi adlı daha basit önceki örnekte olduğu gibi istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="da6c1-319">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named [UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span> 

<span data-ttu-id="da6c1-320">Bununla birlikte, MediatR komutu gönderme işlemi aşağıdaki kodda gösterildiği gibi oldukça benzerdir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-320">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,     
                                                eventMsg.UserId, eventMsg.City, 
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber, 
                                                eventMsg.CardHolderName, 
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,  
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand, 
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="da6c1-321">Ancak, bu da durumda biz de ıdempotent komutları uygulama olduğundan biraz daha gelişmiş.</span><span class="sxs-lookup"><span data-stu-id="da6c1-321">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="da6c1-322">Idempotent, CreateOrderCommand işlemi olması gerekir böylece aynı ileti yeniden denemeleri gibi herhangi bir nedenle nedeniyle ağ üzerinden yinelenen geliyorsa, yalnızca bir kez aynı iş sırada işlenir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-322">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="da6c1-323">Bu iş komutta (Bu örnek CreateOrderCommand) ve embeding kaydırma tarafından uygulanır, ıdempotent sahip ağ üzerinden gelen her ileti kimliği tarafından izlenen bir genel IdentifiedCommand içine.</span><span class="sxs-lookup"><span data-stu-id="da6c1-323">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embeding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="da6c1-324">Aşağıdaki kodu IdentifiedCommand ile DTO ve kimliği artı Sarmalanan iş komut nesnesi'den fazla bir şey olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-324">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="da6c1-325">Ardından adlı IdentifiedCommand için CommandHandler [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) temelde iletisinin bir parçası zaten gelen kimliği bir tabloda var olup olmadığını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="da6c1-325">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="da6c1-326">Bu nedenle, komutu yeniden işlenmez zaten varsa ıdempotent komut olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="da6c1-326">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="da6c1-327">Altyapı kodu tarafından gerçekleştirilen `_requestManager.ExistAsync` aşağıdaki yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="da6c1-327">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> : 
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator, 
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embeded business command to mediator 
            // so it runs its related CommandHandler 
            var result = await _mediator.Send(message.Command);
                
            return result;
        }
    }
}
```

<span data-ttu-id="da6c1-328">İş komutu yinelenen kimliği olmadığından işlenmek üzere gerektiğinde IdentifiedCommand iş komutunun Zarf gibi davranan olduğundan, iç iş komut alır ve bunu Dünyası zaman gösterilen koddan son parçası olduğu için yeniden gönderir çalışan `_mediator.Send(message.Command)`, gelen [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="da6c1-328">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="da6c1-329">Bunu yaparken, bağlantı ve iş komut işleyici, bu durumda, işlemleri sıralama veritabanında aşağıdaki kodda gösterildiği gibi çalışan CreateOrderCommandHandler çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="da6c1-329">When doing that, it will link and run the business command handler, in this case, the CreateOrderCommandHandler which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator, 
                                     IOrderRepository orderRepository, 
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ?? 
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? 
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? 
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,  
                              message.CardNumber, message.CardSecurityNumber, 
                              message.CardHolderName, message.CardExpiration);
            
        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="registering-the-types-used-by-mediatr"></a><span data-ttu-id="da6c1-330">MediatR tarafından kullanılan türlerini kaydetme</span><span class="sxs-lookup"><span data-stu-id="da6c1-330">Registering the types used by MediatR</span></span>

<span data-ttu-id="da6c1-331">Komut işleyici sınıfları unutmayın MediatR Dünyası sınıfları ve komut işleyici sınıfları IOC kapsayıcısında kaydetmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-331">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="da6c1-332">Varsayılan olarak, MediatR IOC kapsayıcı olarak Autofac kullanır, ancak yerleşik ASP.NET Core IOC kapsayıcı veya MediatR tarafından desteklenen herhangi bir kapsayıcısına de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-332">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="da6c1-333">Aşağıdaki kod Dünyası'nın türleri ve komutları Autofac modülleri kullanırken nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-333">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="da6c1-334">Bu yerdir "Sihirli MediatR olur".</span><span class="sxs-lookup"><span data-stu-id="da6c1-334">This is where “the magic happens” with MediatR.</span></span> 

<span data-ttu-id="da6c1-335">Her komut işleyici generic IAsyncRequestHandler uyguladığından&lt;T&gt; arabirim, derlemeler kaydedilirken kodunu RegisteredAssemblyTypes ile maked tüm türleri RequestHandlers ilgili sırasında kaydeder CommandHandler sınıfı, aşağıdaki örnekte olduğu gibi belirtilen ilişki sayesinde kullanıcıların komutlarla CommandHandlers:</span><span class="sxs-lookup"><span data-stu-id="da6c1-335">Because each command handler implements the generic IAsyncRequestHandler&lt;T&gt; interface, when registering the assemblies, the code registers with RegisteredAssemblyTypes all the types maked as RequestHandlers while relating the CommandHandlers with their Commands, thanks to the relationship stated at the CommandHandler class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="da6c1-336">Bu komutları ile komut işleyicileri karşılık gelen kodudur.</span><span class="sxs-lookup"><span data-stu-id="da6c1-336">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="da6c1-337">Yalnızca basit bir sınıf işleyicisidir ancak RequestHandler devralan&lt;T&gt;, ve MediatR ile doğru yükü çağrıldığında emin yapar.</span><span class="sxs-lookup"><span data-stu-id="da6c1-337">The handler is just a simple class, but it inherits from RequestHandler&lt;T&gt;, and MediatR makes sure it is invoked with the correct payload.</span></span>

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-meadiatr"></a><span data-ttu-id="da6c1-338">Çapraz kesme sorunları MeadiatR davranışları komutlarıyla işlerken uygulama</span><span class="sxs-lookup"><span data-stu-id="da6c1-338">Applying cross-cutting concerns when processing commands with the Behaviors in MeadiatR</span></span>

<span data-ttu-id="da6c1-339">Daha fazla bir şey yok: arası kesme sorunlarının Dünyası ardışık düzene geçerli durum.</span><span class="sxs-lookup"><span data-stu-id="da6c1-339">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="da6c1-340">Autofac kayıt modülü kod sonunda nasıl bunu bir davranış türü özellikle kaydeder, özel bir LoggingBehavior sınıf ve ValidatorBehavior sınıfı de görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-340">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="da6c1-341">Ancak, diğer özel behaviours çok ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-341">But you could add other custom behaviours, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...        
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="da6c1-342">Olduğunu [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı, yürütülmekte olan komut işleyici ve olup olmadığını başarılı olup hakkındaki bilgileri kaydeder aşağıdaki kodu olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="da6c1-342">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse> 
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="da6c1-343">Bu oluşturma öğesi sınıf uygulama tarafından ve onunla ardışık dekorasyon tarafından MediatR işlenen tüm komutları yürütme hakkında bilgi kaydetme.</span><span class="sxs-lookup"><span data-stu-id="da6c1-343">Just by implementing this decorator class and by decorating the pipeline with it, all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="da6c1-344">Mikro hizmet de temel doğrulama için ikinci bir davranış geçerlidir sıralama eShopOnContainers [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) dayanan sınıfı [FluentValidation](https://github.com/JeremySkinner/FluentValidation) gösterildiği gibi kitaplığı Aşağıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="da6c1-344">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

<span data-ttu-id="da6c1-345">Ardından, temel [FluentValidation](https://github.com/JeremySkinner/FluentValidation) kitaplığı oluşturduğumuz doğrulama CreateOrderCommand ile olduğu gibi aşağıdaki kodu geçirilen verileri için:</span><span class="sxs-lookup"><span data-stu-id="da6c1-345">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse> 
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="da6c1-346">Ardından, FluentValidation kitaplıkta bağlı olarak, doğrulama CreateOrderCommand ile olduğu gibi aşağıdaki kodu geçirilen verileri için oluşturduğumuz:</span><span class="sxs-lookup"><span data-stu-id="da6c1-346">Then, based on the FluentValidation library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19); 
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date"); 
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3); 
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found"); 
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

<span data-ttu-id="da6c1-347">Ek doğrulama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da6c1-347">You could create additional validations.</span></span> <span data-ttu-id="da6c1-348">Komut doğrulamaları uygulamak için çok temiz ve zarif bir yolu budur.</span><span class="sxs-lookup"><span data-stu-id="da6c1-348">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="da6c1-349">Benzer şekilde, ek unsurları veya bunları işlerken komutları uygulamak istediğiniz arası kesme sorunları için diğer davranışlarını uygulamak.</span><span class="sxs-lookup"><span data-stu-id="da6c1-349">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="da6c1-350">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="da6c1-350">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="da6c1-351">Dünyası düzeni</span><span class="sxs-lookup"><span data-stu-id="da6c1-351">The mediator pattern</span></span>

-   <span data-ttu-id="da6c1-352">**Dünyası düzeni**
    [*https://en.wikipedia.org/wiki/Mediator\_düzeni*](https://en.wikipedia.org/wiki/Mediator_pattern)</span><span class="sxs-lookup"><span data-stu-id="da6c1-352">**Mediator pattern**
[*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)</span></span>

##### <a name="the-decorator-pattern"></a><span data-ttu-id="da6c1-353">Oluşturma öğesi düzeni</span><span class="sxs-lookup"><span data-stu-id="da6c1-353">The decorator pattern</span></span>

-   <span data-ttu-id="da6c1-354">**Oluşturma öğesi düzeni**
    [*https://en.wikipedia.org/wiki/Decorator\_düzeni*](https://en.wikipedia.org/wiki/Decorator_pattern)</span><span class="sxs-lookup"><span data-stu-id="da6c1-354">**Decorator pattern**
[*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)</span></span>

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="da6c1-355">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="da6c1-355">MediatR (Jimmy Bogard)</span></span>

-   <span data-ttu-id="da6c1-356">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="da6c1-356">**MediatR.**</span></span> <span data-ttu-id="da6c1-357">GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="da6c1-357">GitHub repo.</span></span>
    [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

-   <span data-ttu-id="da6c1-358">**MediatR ve AutoMapper CQRS**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-358">**CQRS with MediatR and AutoMapper**
[*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span></span>

-   <span data-ttu-id="da6c1-359">**Üzerinde bir Diyet denetleyicilerinizi put: gönderileri ve komutları.**
    [*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-359">**Put your controllers on a diet: POSTs and commands.**
[*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span></span>

-   <span data-ttu-id="da6c1-360">**Dünyası ardışık düzen ile kuruluşlarda arası kesme sorunları**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-360">**Tackling cross-cutting concerns with a mediator pipeline**
[*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span></span>

-   <span data-ttu-id="da6c1-361">**CQRS ve REST: mükemmel**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-361">**CQRS and REST: the perfect match**
[*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span></span>

-   <span data-ttu-id="da6c1-362">**MediatR ardışık örnekler**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-362">**MediatR Pipeline Examples**
[*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span></span>

-   <span data-ttu-id="da6c1-363">**Dikey dilim Test Mobilyalar MediatR ve ASP.NET Core için**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span><span class="sxs-lookup"><span data-stu-id="da6c1-363">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core**
*<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span></span>

-   <span data-ttu-id="da6c1-364">**İçin yayımlanan Microsoft bağımlılık ekleme MediatR uzantıları**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span><span class="sxs-lookup"><span data-stu-id="da6c1-364">**MediatR Extensions for Microsoft Dependency Injection Released**
[*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span></span>

##### <a name="fluent-validation"></a><span data-ttu-id="da6c1-365">Fluent doğrulama</span><span class="sxs-lookup"><span data-stu-id="da6c1-365">Fluent validation</span></span>

-   <span data-ttu-id="da6c1-366">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="da6c1-366">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="da6c1-367">GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="da6c1-367">GitHub repo.</span></span>
    [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
<span data-ttu-id="da6c1-368">[Önceki] (microservice-application-layer-web-api-design.md) [sonraki] (.. /implement-resilient-Applications/index.MD)</span><span class="sxs-lookup"><span data-stu-id="da6c1-368">[Previous] (microservice-application-layer-web-api-design.md) [Next] (../implement-resilient-applications/index.md)</span></span>
