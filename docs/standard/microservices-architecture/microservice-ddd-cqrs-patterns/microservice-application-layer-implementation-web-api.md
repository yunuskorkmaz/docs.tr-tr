---
title: Web API'si kullanarak mikro hizmet uygulama katmanı uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Bağımlılık ekleme ve Dünyası desenleri ve Web API'sini uygulama katmanı, uygulama ayrıntılarını anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: d37660d3e2a7640383347071adfe969325ddd77b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152118"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="162a2-103">Web API'si kullanarak mikro hizmet uygulama katmanı</span><span class="sxs-lookup"><span data-stu-id="162a2-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="162a2-104">Altyapı nesnelerin uygulama katmanınızdaki eklemesine kullanım bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="162a2-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="162a2-105">Daha önce belirtildiği gibi uygulama katmanı oluşturduğunuz, örneğin bir Web API projesi veya bir MVC web uygulaması projesi gibi yapıtı (derleme) bir parçası olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="162a2-106">ASP.NET Core ile oluşturulmuş bir mikro hizmet söz konusu olduğunda, uygulama katmanı Web API kitaplığınızı genellikle olacaktır.</span><span class="sxs-lookup"><span data-stu-id="162a2-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="162a2-107">ASP.NET Core (altyapısını artı denetleyicilerinizi) özel uygulama katman kodunuzdan beklenenler ayırmak istiyorsanız, uygulama katmanınızdaki ayrı sınıf kitaplığında yerleştirebilirsiniz, ancak bu isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="162a2-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="162a2-108">Örneğin, sipariş mikro hizmet uygulama katmanı kodunu bir parçası olarak doğrudan uygulanır **Ordering.API** proje (bir ASP.NET Core Web API projesi) olarak gösterilen Şekil 7-23.</span><span class="sxs-lookup"><span data-stu-id="162a2-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

![Ordering.API mikro hizmet uygulama klasörü altında alt klasörleri gösteren Çözüm Gezgini görünümü: Davranışlar, komutları, DomainEventHandlers, IntegrationEvents, modelleri, sorguları ve doğrulama.](./media/image20.png)

<span data-ttu-id="162a2-110">**Şekil 7-23**.</span><span class="sxs-lookup"><span data-stu-id="162a2-110">**Figure 7-23**.</span></span> <span data-ttu-id="162a2-111">Uygulama katmanı Ordering.API ASP.NET Core Web API projesinde</span><span class="sxs-lookup"><span data-stu-id="162a2-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="162a2-112">ASP.NET Core içeren basit bir [yerleşik IOC kapsayıcı](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (IServiceProvider arabirimi tarafından temsil edilir), oluşturucu ekleme varsayılan olarak destekler ve ASP.NET belirli hizmetleri DI aracılığıyla kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="162a2-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="162a2-113">ASP.NET Core kullanan terimi *hizmet* DI eklenen kayıt türlerinden herhangi birini için.</span><span class="sxs-lookup"><span data-stu-id="162a2-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="162a2-114">Yerleşik kapsayıcının hizmetler, uygulamanızın başlangıç sınıfındaki Createservicereplicalisteners() yöntemi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="162a2-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="162a2-115">Bağımlılıklarınızı türü gerektiren ve IOC kapsayıcısında kaydeden Hizmetleri için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="162a2-115">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="162a2-116">Genellikle, altyapı nesneler uygulama bağımlılıkları eklemesine istersiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="162a2-117">Bir depo eklemek oldukça tipik bir bağımlılıktır.</span><span class="sxs-lookup"><span data-stu-id="162a2-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="162a2-118">Ancak, bilgisayarınızda yüklü olmayabilir herhangi bir altyapı bağımlılığı ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="162a2-119">DBContext altyapı Kalıcılık nesnelerinizi uygulanması da olduğundan daha basit uygulamalar için doğrudan iş birimi deseni nesnenizin (EF DbContext nesnesini) ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="162a2-120">Aşağıdaki örnekte, .NET Core Oluşturucu gerekli depo nesnelerde nasıl çalıştırıyorsunuzdur görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="162a2-121">Sonraki bölümde ele bir komut işleyici sınıftır.</span><span class="sxs-lookup"><span data-stu-id="162a2-121">The class is a command handler, which we will cover in the next section.</span></span>

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

<span data-ttu-id="162a2-122">Sınıfı, işlemi yürütmek ve durum değişiklikleri kalıcı hale getirmek için eklenen depoları kullanır.</span><span class="sxs-lookup"><span data-stu-id="162a2-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="162a2-123">Bu sınıf, bir komut işleyici, bir ASP.NET Core Web API denetleyicisi yöntemi olup olmadığını veya önemli değildir [DDD uygulama hizmeti](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="162a2-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="162a2-124">Sonuç olarak, bir komut işleyici için benzer bir biçimde depoları, etki alanı varlıklarının ve diğer uygulama koordinasyon kullanan basit bir sınıf durumdur.</span><span class="sxs-lookup"><span data-stu-id="162a2-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="162a2-125">Belirtilen sınıfların tümü, DI kullanarak örnekte olduğu gibi aynı şekilde Oluşturucu tabanlı bağımlılık ekleme çalışır.</span><span class="sxs-lookup"><span data-stu-id="162a2-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="162a2-126">Bağımlılık uygulama türleri ve arabirimleri veya soyutlama kaydedin</span><span class="sxs-lookup"><span data-stu-id="162a2-126">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="162a2-127">Oluşturucular eklenen nesneleri kullanabilmeniz dı aracılığıyla uygulama sınıflarınızı içine eklenen nesneleri üreten sınıfları ve arabirimleri kaydetme yeri bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="162a2-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="162a2-128">(Dı gibi temel oluşturucu, daha önce gösterildiği gibi.)</span><span class="sxs-lookup"><span data-stu-id="162a2-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="162a2-129">ASP.NET Core tarafından sağlanan yerleşik IOC kapsayıcı kullanın</span><span class="sxs-lookup"><span data-stu-id="162a2-129">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="162a2-130">ASP.NET Core tarafından sağlanan yerleşik IOC kapsayıcı kullandığınızda Createservicereplicalisteners() yönteminde aşağıdaki kodu olduğu gibi Startup.cs dosyasındaki eklemesine türlerini kaydedin:</span><span class="sxs-lookup"><span data-stu-id="162a2-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

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

<span data-ttu-id="162a2-131">En yaygın desen bir IOC kapsayıcısında türlerini kaydetme türleri çifti kaydedilecek olduğunda — bir arabirim ve kendi ilgili uygulama sınıfı.</span><span class="sxs-lookup"><span data-stu-id="162a2-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="162a2-132">Herhangi bir oluşturucu üzerinden IOC kapsayıcısından nesneyi istediğinde, belirli bir arabirim türünden bir nesne isteyin.</span><span class="sxs-lookup"><span data-stu-id="162a2-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="162a2-133">Örneği için önceki örnekte, Oluşturucular, herhangi bir bağımlılık IMyCustomRepository (arabirimi veya soyutlama) sahip olduğunuzda, IOC kapsayıcı MyCustomSQLServerRepository uygulama örneğini ekleyecektir son satır durumları sınıf.</span><span class="sxs-lookup"><span data-stu-id="162a2-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="162a2-134">Otomatik türleri kayıt için Scrutor kitaplığını kullanma</span><span class="sxs-lookup"><span data-stu-id="162a2-134">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="162a2-135">DI'de .NET Core kullanırken, bir derlemeyi tarayın ve türlerinden kurala göre otomatik olarak kaydetmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="162a2-136">ASP.NET Core bu özellik şu anda kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="162a2-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="162a2-137">Ancak, kullanabileceğiniz [Scrutor](https://github.com/khellang/Scrutor) kitaplığı konusu.</span><span class="sxs-lookup"><span data-stu-id="162a2-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="162a2-138">IOC kapsayıcınızı kaydedilmesi gereken türleri onlarca olduğunda bu yaklaşım uygundur.</span><span class="sxs-lookup"><span data-stu-id="162a2-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="162a2-139">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="162a2-139">Additional resources</span></span>

- <span data-ttu-id="162a2-140">**Matthew King. Hizmetleri ile Scrutor kaydediliyor** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-140">**Matthew King. Registering services with Scrutor** \\</span></span>
  [*https://www.mking.net/blog/registering-services-with-scrutor*](https://www.mking.net/blog/registering-services-with-scrutor)

- <span data-ttu-id="162a2-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="162a2-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="162a2-142">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="162a2-142">GitHub repo.</span></span> \
  [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="162a2-143">Bir IOC kapsayıcısı Autofac kullanın</span><span class="sxs-lookup"><span data-stu-id="162a2-143">Use Autofac as an IoC container</span></span>

<span data-ttu-id="162a2-144">Ayrıca ek IOC kapsayıcılar kullanma ve ASP.NET Core ardışık düzen, sıralama mikro hizmet kullanan hizmetine olduğu gibi takın [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="162a2-144">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="162a2-145">Autofac kullanırken aracılığıyla kayıt türleri, birden çok sınıf kitaplıkları dağıtılmış uygulama türleri olabilir gibi türlerinizi nerede olduğunuza bağlı olarak birden çok dosya arasında bölmek olanak tanıyan modüller, türler genellikle kaydedin.</span><span class="sxs-lookup"><span data-stu-id="162a2-145">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="162a2-146">Örneğin, aşağıdaki gibidir [Autofac uygulama modülü](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) için [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) proje türleriyle eklemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-146">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

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

<span data-ttu-id="162a2-147">Autofac ayrıca bir özelliğe sahip [tarama derlemeleri ve türlerini adı kuralları kaydetmeye](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span><span class="sxs-lookup"><span data-stu-id="162a2-147">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="162a2-148">Kavramlar ve kayıt işlemine çok benzer şekilde türleri ile yerleşik ASP.NET Core IOC kapsayıcı kaydedebilirsiniz, ancak Autofac kullanırken söz dizimi biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="162a2-149">Örnek kodda IOrderRepository soyutlama uygulama sınıfımızın OrderRepository birlikte kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="162a2-150">Başka bir deyişle, bir oluşturucu, bir bağımlılık IOrderRepository soyutlama veya arabirimi aracılığıyla bildirme her IOC kapsayıcı OrderRepository sınıfının bir örneğini ekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="162a2-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="162a2-151">Örnek kapsamı türü örneği aynı hizmet veya bağımlılık istekleri arasında nasıl paylaşılacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="162a2-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="162a2-152">Bir bağımlılık için bir istek yapıldığında, IOC kapsayıcı aşağıdaki döndürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="162a2-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="162a2-153">Ömrü kapsam başına tek bir örnek (ASP.NET Core IOC kapsayıcısı olarak anılacaktır *kapsamlı*).</span><span class="sxs-lookup"><span data-stu-id="162a2-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="162a2-154">Bağımlılık başına yeni bir örnek (ASP.NET Core IOC kapsayıcısı olarak anılacaktır *geçici*).</span><span class="sxs-lookup"><span data-stu-id="162a2-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="162a2-155">IOC kapsayıcıyı kullanan tüm nesneleri arasında paylaşılan tek bir örnek (ASP.NET Core IOC kapsayıcısı olarak anılacaktır *singleton*).</span><span class="sxs-lookup"><span data-stu-id="162a2-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="162a2-156">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="162a2-156">Additional resources</span></span>

- <span data-ttu-id="162a2-157">**ASP.NET core'da bağımlılık ekleme giriş** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-157">**Introduction to Dependency Injection in ASP.NET Core** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="162a2-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="162a2-158">**Autofac.**</span></span> <span data-ttu-id="162a2-159">Resmi belgeleri.</span><span class="sxs-lookup"><span data-stu-id="162a2-159">Official documentation.</span></span> \
  [*http://docs.autofac.org/en/latest/*](http://docs.autofac.org/en/latest/)

- <span data-ttu-id="162a2-160">**ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamlı - Cesar de la Torre karşılaştırma.**</span><span class="sxs-lookup"><span data-stu-id="162a2-160">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="162a2-161">Komut ve komut işleyicisi desenlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="162a2-161">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="162a2-162">Oluşturucusu aracılığıyla DI örnekte, önceki bölümde gösterilenle IOC kapsayıcı bir sınıftaki bir oluşturucu üzerinden depoları ekleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="162a2-162">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="162a2-163">Ancak, tam olarak nerede bunlar eklenmiş?</span><span class="sxs-lookup"><span data-stu-id="162a2-163">But exactly where were they injected?</span></span> <span data-ttu-id="162a2-164">Bir basit Web API'SİNDE (örneğin, katalog mikro hizmetine), bunları MVC denetleyicileri düzeyinde, ASP.NET Core istek ardışık düzenini bir parçası olarak bir denetleyici oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="162a2-164">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers’ level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="162a2-165">Ancak, bu bölümün ilk kod içinde ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) hizmetine Ordering.API hizmetinden sınıfı), bağımlılık ekleme belirli bir komut Oluşturucu gerçekleştirilir işleyici.</span><span class="sxs-lookup"><span data-stu-id="162a2-165">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="162a2-166">Bize açıklayan bir komut işleyici ve neden kullanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="162a2-166">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="162a2-167">Komut desen, doğası gereği, bu kılavuzun önceki bölümlerinde sunulan CQRS modelinin ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="162a2-167">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="162a2-168">CQRS iki kenara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="162a2-168">CQRS has two sides.</span></span> <span data-ttu-id="162a2-169">Basitleştirilmiş sorguları kullanarak sorguları, ilk alanıdır [Dapper](https://github.com/StackExchange/dapper-dot-net) daha önce açıklanan mikro ORM.</span><span class="sxs-lookup"><span data-stu-id="162a2-169">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="162a2-170">İşlemler için başlangıç noktası ve giriş kanaldan hizmetin dışında olan komutları ikinci bir alandır.</span><span class="sxs-lookup"><span data-stu-id="162a2-170">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="162a2-171">Şekil 7-24'te gösterildiği gibi deseni istemci tarafında, komutları kabul üzerinde alan etki alanı modeli kurallara göre işlenmesi ve son olarak işlem durumlarıyla kalıcı.</span><span class="sxs-lookup"><span data-stu-id="162a2-171">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![CQRS, yazma tarafı üst düzey Görünüm: Kullanıcı Arabirimi uygulama için etki alanı modeli ve veritabanını güncellemek için altyapı bağlıdır CommandHandler, alır API'sinden bir komut gönderir.](./media/image21.png)

<span data-ttu-id="162a2-173">**Şekil 7-24**.</span><span class="sxs-lookup"><span data-stu-id="162a2-173">**Figure 7-24**.</span></span> <span data-ttu-id="162a2-174">Üst düzey görünümünü komutları veya "işlem tarafta" bir CQRS düzeni</span><span class="sxs-lookup"><span data-stu-id="162a2-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="162a2-175">Komut sınıfı</span><span class="sxs-lookup"><span data-stu-id="162a2-175">The command class</span></span>

<span data-ttu-id="162a2-176">Bir istek sistemin sistem durumunu değiştiren bir eylem gerçekleştirmek bir komuttur.</span><span class="sxs-lookup"><span data-stu-id="162a2-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="162a2-177">Komutlar, kesinlik temelli ve hemen bir kerelik işlenmesi.</span><span class="sxs-lookup"><span data-stu-id="162a2-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="162a2-178">Komutları imperatives olduğundan, bunlar genellikle bir fiil kesinlik temelli ruh (örneğin, "oluşturma" veya "güncelleştir") ile adlandırılır ve CreateOrderCommand gibi toplama türünü içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="162a2-179">Bir olay, bir komut Geçmişten bir olgu değil; yalnızca bir istek ve bu nedenle reddetti.</span><span class="sxs-lookup"><span data-stu-id="162a2-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="162a2-180">İşlem Yöneticisi, bir eylemi gerçekleştirmek için bir toplama yönlendiren olduğunda komutları sonucunda bir isteği bir kullanıcı arabiriminden veya bir işlem yöneticisi tarafından gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="162a2-181">Bir önemli bir komutu tek bir alıcı tarafından yalnızca bir kez işlenmesi gerektiğini özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="162a2-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="162a2-182">Bir komutun tek bir eylem veya uygulamada gerçekleştirmek istediğiniz işlem olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="162a2-183">Örneğin, aynı sipariş oluşturma komutu kereden fazla işlenmemesi.</span><span class="sxs-lookup"><span data-stu-id="162a2-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="162a2-184">Komutlar ve olayları arasındaki önemli bir fark budur.</span><span class="sxs-lookup"><span data-stu-id="162a2-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="162a2-185">Olayda birçok sistemleri veya mikro hizmetler ilgilenebilecek çünkü birden çok kez işlenen olaylar.</span><span class="sxs-lookup"><span data-stu-id="162a2-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="162a2-186">Ayrıca, komut etkili değilse, komut yalnızca bir kez işlenmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="162a2-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="162a2-187">Birden çok kez sonucu komutu niteliği nedeniyle veya sistem komut işleme biçimi nedeniyle değiştirmeden yürütülmek üzere ise bir komut etkili olur.</span><span class="sxs-lookup"><span data-stu-id="162a2-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="162a2-188">Komutlarınızın yapmak iyi bir uygulamadır ve etki alanının iş kurallarını ve okuduğunuzda altında mantıklıdır ıdempotent güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="162a2-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="162a2-189">Örneğin, herhangi bir nedenle (yeniden deneme mantığı, yazılım korsanlığı, vb.) sisteminizi birden çok kez aynı CreateOrder komutu ulaşırsa aynı örneği kullanmak için tanımlamak ve birden çok sipariş oluşturmamanızı sağlar olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="162a2-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="162a2-190">Bunu yapmak için bir tür işlemlerinde kimlik eklemek ve komut veya güncelleştirme işlenmiş olup olmadığını belirlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="162a2-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="162a2-191">Tek alıcı için komut gönderebilirsiniz; bir komut yayımlamayın.</span><span class="sxs-lookup"><span data-stu-id="162a2-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="162a2-192">Yayımlama olduğu bir olgu durum olayları için — bir sorun oluştu ve olabilir Olay alıcıları için ilginç.</span><span class="sxs-lookup"><span data-stu-id="162a2-192">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="162a2-193">Olaylar söz konusu olduğunda, yayımcı hangi olay veya bunu ne alıcılar almak hiçbir sorunları vardır.</span><span class="sxs-lookup"><span data-stu-id="162a2-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="162a2-194">Ancak etki alanı ya da tümleştirme olayları zaten önceki bölümlerinde sunulan farklı bir öykü.</span><span class="sxs-lookup"><span data-stu-id="162a2-194">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="162a2-195">Veri alanlarını veya koleksiyonları bu komutu yürütmek için gerekli tüm bilgileri içeren bir sınıf ile birlikte bir komut uygulanır.</span><span class="sxs-lookup"><span data-stu-id="162a2-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="162a2-196">Özel bir tür, veri aktarım nesnesini (DTO), özellikle değişiklikleri veya işlemleri istemek için kullanılan bir komuttur.</span><span class="sxs-lookup"><span data-stu-id="162a2-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="162a2-197">Komut, tam komut ve hiçbir şey daha fazla işlemek için gerekli bilgileri temel alır.</span><span class="sxs-lookup"><span data-stu-id="162a2-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="162a2-198">Aşağıdaki örnek, Basitleştirilmiş CreateOrderCommand sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="162a2-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="162a2-199">Bu sıralama mikro hizmetine kullanılan değişmez bir komuttur.</span><span class="sxs-lookup"><span data-stu-id="162a2-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

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

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
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

<span data-ttu-id="162a2-200">Temel olarak, komut sınıfı, etki alanı model nesneleri kullanarak, bir iş işlemi gerçekleştirmek için gereken tüm verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="162a2-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="162a2-201">Bu nedenle, yalnızca salt okunur veri ve davranışı yok içeren veri yapılarını komutlardır.</span><span class="sxs-lookup"><span data-stu-id="162a2-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="162a2-202">Amacı, komutun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="162a2-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="162a2-203">C gibi birçok dilde\#komutları sınıf olarak temsil edilir ancak doğru nesne yönelimli gerçek anlamda sınıflarda değildir.</span><span class="sxs-lookup"><span data-stu-id="162a2-203">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="162a2-204">Beklenen kullanım, doğrudan etki alanı modeli tarafından işlenen olduğu için ek bir özellik komutları, sabittir.</span><span class="sxs-lookup"><span data-stu-id="162a2-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="162a2-205">Öngörülen kendi ömrü boyunca değişiklik gerekmez.</span><span class="sxs-lookup"><span data-stu-id="162a2-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="162a2-206">Bir c\# sınıfı, tüm ayarlayıcılar ya da iç durum değişikliği diğer yöntemleri zorunluluğunu ortadan kaldırarak değiştirilemezlik gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-206">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="162a2-207">Amaçladığınız ya da beklediğiniz komutları bir seri hale getirme deserializing sürecinden geçmeden, özelliklerini özel ayarlayıcı olmalıdır unutmayın ve `[DataMemeber]` (veya `[JsonProperty]`) özniteliği, aksi takdirde seri durumdan çıkarıcı için mümkün olmayacak gerekli değerlerle hedef nesne yeniden yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="162a2-207">Bear in mind that if you intend or expect commands will be going through a serializing/deserializing process, the properties must have private setter, and the `[DataMemeber]` (or `[JsonProperty]`) attribute, otherwise the deserializer will not be able to reconstruct the object at destination with the required values.</span></span>

<span data-ttu-id="162a2-208">Örneğin, bir sipariş oluşturmak için komut sınıfı oluşturmak istediğiniz siparişin veri açısından büyük olasılıkla benzer, ancak büyük olasılıkla aynı öznitelikleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="162a2-208">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="162a2-209">Örneğin, sipariş henüz oluşturulmamış çünkü CreateOrderCommand bir sipariş kimliği yok.</span><span class="sxs-lookup"><span data-stu-id="162a2-209">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="162a2-210">Birçok komut sınıfları yalnızca birkaç alan değiştirilmesi gereken bazı durumu hakkında gerektirme, basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-210">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="162a2-211">Bu durum yalnızca "işlem" bir sıra durumunu değiştiriyorsanız "Ücretli" veya "aşağıdakine benzer bir komut kullanarak sevk" olacaktır:</span><span class="sxs-lookup"><span data-stu-id="162a2-211">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

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

<span data-ttu-id="162a2-212">Bazı geliştiriciler kendi UI istek nesneleri kendi komut Dto'lar ayrı hale getirir, ancak adımlarından tercih olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-212">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="162a2-213">Can sıkıcı bir ayrım ölçüde eklenen değerine sahip olan ve hemen hemen aynı şekilde nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="162a2-213">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="162a2-214">Örneğin, hizmetine bazı komutlar doğrudan istemci tarafında gelir.</span><span class="sxs-lookup"><span data-stu-id="162a2-214">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="162a2-215">Komut işleyici sınıfı</span><span class="sxs-lookup"><span data-stu-id="162a2-215">The Command Handler class</span></span>

<span data-ttu-id="162a2-216">Her komut için belirli bir komut işleyici sınıfı uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-216">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="162a2-217">Düzeni nasıl çalışır, ve burada komut nesnesi, etki alanı nesnelerini ve altyapı depo nesneleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="162a2-217">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="162a2-218">Komut işleyici aslında CQRS ve DDD açısından uygulama katmanı kalbidir.</span><span class="sxs-lookup"><span data-stu-id="162a2-218">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="162a2-219">Ancak tüm etki alanı mantığı alan sınıfları içinde yer almalıdır; toplama kökleri (kök varlıklar) içinde alt varlıklar veya [etki alanı Hizmetleri](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ancak değildir komut işleyicisinin içerisinde olduğu uygulama öğesinden bir sınıf Katman.</span><span class="sxs-lookup"><span data-stu-id="162a2-219">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="162a2-220">Komut işleyici sınıfı, bir önceki bölümde belirtilen tek Resposibility İlkesi (SRP) yapmanın bir yolu, güçlü bir atlama taşı sunar.</span><span class="sxs-lookup"><span data-stu-id="162a2-220">The command handler class offers a strong stepping stone in the way to achieve the Single Resposibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="162a2-221">Bir komut işleyici, bir komut alır ve bir sonuç kullanılan toplam alır.</span><span class="sxs-lookup"><span data-stu-id="162a2-221">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="162a2-222">Sonuç başarılı yürütme komut veya özel bir durum olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-222">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="162a2-223">Bir özel durum söz konusu olduğunda sistem durumu değiştirilmeden olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-223">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="162a2-224">Komut işleyici, genellikle aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="162a2-224">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="162a2-225">Komut nesnesi gibi bir DTO alır (gelen [Dünyası](https://en.wikipedia.org/wiki/Mediator_pattern) veya diğer altyapı nesne).</span><span class="sxs-lookup"><span data-stu-id="162a2-225">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="162a2-226">Bu komut (Dünyası tarafından doğrulanmamış varsa) geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="162a2-226">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="162a2-227">Bu, geçerli komut hedefi olan toplama kök örneği başlatır.</span><span class="sxs-lookup"><span data-stu-id="162a2-227">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="162a2-228">Toplama kök örneğinde komuttan gerekli verileri alma yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="162a2-228">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="162a2-229">Bu, yeni durum toplama için ilgili veritabanını devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="162a2-229">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="162a2-230">Bu son işlem gerçek bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="162a2-230">This last operation is the actual transaction.</span></span>

<span data-ttu-id="162a2-231">Genellikle, bir komut işleyici toplama, kök (kök varlık) tarafından yönetilen tek bir toplamada ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="162a2-231">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="162a2-232">Birden çok toplamalar alımını tek bir komut tarafından etkilenir, durumları veya eylemler arasında birden çok toplamalar yaymak için etki alanı olayları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-232">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="162a2-233">Burada önemli olan nokta bir komutu işlenirken, tüm etki alanı mantığı içinde etki alanı modeli (toplama), tamamen yalıtılmış ve birim testi için hazır olması gerekliliğidir.</span><span class="sxs-lookup"><span data-stu-id="162a2-233">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="162a2-234">Komut işleyici yalnızca etki alanı modeli veritabanından almanın bir yolunu ve model değiştirildiğinde, değişiklikleri kalıcı hale getirmek için altyapı katmanını (depo) bildirmek için son adım olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="162a2-234">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="162a2-235">Bu yaklaşımın avantajı uygulama veya tesisat düzeyi (komut işleyicileri, Web API'si, altyapı katmanlarının, kodda değişiklik yapmadan etki alanı mantığı bir yalıtılmış, tam olarak kapsüllenmiş, zengin, davranışsal bir etki alanı modeli içinde yeniden düzenleyebilirsiniz olduğu depoları, vb.).</span><span class="sxs-lookup"><span data-stu-id="162a2-235">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="162a2-236">Komut işleyicileri çok fazla mantık ile karmaşık aldığınızda, bir kod kokusu olabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-236">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="162a2-237">Bunları gözden geçirin ve etki alanı mantığı bulursanız, o etki alanı davranışını (toplama kök ve alt varlık) etki alanı nesnelerin yöntemlere taşımak için kodu yeniden düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="162a2-237">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="162a2-238">Bir komut işleyici sınıfı, örnek olarak, aşağıdaki kod, bu bölümün başında gördüğünüz aynı CreateOrderCommandHandler sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="162a2-238">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="162a2-239">Bu durumda, Handle yöntemini ve etki alanı model nesneleri/toplama işlemleri vurgulamak istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="162a2-239">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

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

<span data-ttu-id="162a2-240">Bir komut işleyici gerçekleştirmeniz ek adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="162a2-240">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="162a2-241">Toplama kökünün yöntemleri ve davranışı ile çalışması için komutun verileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="162a2-241">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

- <span data-ttu-id="162a2-242">Dahili olarak etki alanı nesnelerinde hareket yürütülür, ancak bir komut işleyici açısından saydam etki alanı olayları tetikleyebilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-242">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="162a2-243">İşlem sonucu toplama'nın başarılı olursa ve işlem tamamlandıktan sonra tümleştirme olayları tetikleyebilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-243">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="162a2-244">(Bunlar da depoları gibi altyapı sınıflar tarafından oluşturulması.)</span><span class="sxs-lookup"><span data-stu-id="162a2-244">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="162a2-245">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="162a2-245">Additional resources</span></span>

- <span data-ttu-id="162a2-246">**İşareti Seemann. Sınırlarında değil nesne yönelimli uygulamalar** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-246">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** \\</span></span>
  [<span data-ttu-id="162a2-247">*https://blog.ploeh.dk/2011/05/31/AttheBoundaries, ApplicationsareNotObject odaklı /*</span><span class="sxs-lookup"><span data-stu-id="162a2-247">*https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*</span></span>](https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

- <span data-ttu-id="162a2-248">**Komutlar ve olayları** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-248">**Commands and events** \\</span></span>
  [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

- <span data-ttu-id="162a2-249">**Bir komut işleyici ne yapar?**</span><span class="sxs-lookup"><span data-stu-id="162a2-249">**What does a command handler do?**</span></span> \
  [*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

- <span data-ttu-id="162a2-250">**Jimmy Bogard. Etki alanı komutu desenleri – işleyicileri** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-250">**Jimmy Bogard. Domain Command Patterns – Handlers** \\</span></span>
  [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

- <span data-ttu-id="162a2-251">**Jimmy Bogard. Etki alanı komutu desenleri – doğrulama** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-251">**Jimmy Bogard. Domain Command Patterns – Validation** \\</span></span>
  [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="162a2-252">Komut işlemi işlem hattı: bir komut işleyici tetikleme</span><span class="sxs-lookup"><span data-stu-id="162a2-252">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="162a2-253">Sonraki soruya komut işleyicisi çağırma şeklidir.</span><span class="sxs-lookup"><span data-stu-id="162a2-253">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="162a2-254">El ile ilgili her ASP.NET Core denetleyicisinden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-254">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="162a2-255">Ancak, yaklaşım çok İmparatoru eşleşmiş ve ideal değildir.</span><span class="sxs-lookup"><span data-stu-id="162a2-255">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="162a2-256">Önerilen seçenek olan diğer iki ana seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="162a2-256">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="162a2-257">Bir bellek içi Dünyası deseni yapıt.</span><span class="sxs-lookup"><span data-stu-id="162a2-257">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="162a2-258">Zaman uyumsuz ileti kuyruğunu ile denetleyicileri ile işleyicileri aralığındaki.</span><span class="sxs-lookup"><span data-stu-id="162a2-258">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="162a2-259">Komut işlem hattında Dünyası düzeni (bellek içi) kullanın</span><span class="sxs-lookup"><span data-stu-id="162a2-259">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="162a2-260">Şekil 7-25 gösterildiği gibi bir CQRS yaklaşım, komutun veya alınan DTO türüne göre doğru komut işleyici yeniden yönlendirmek akıllı bir bellek içi bus benzer akıllı bir Dünyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="162a2-260">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="162a2-261">Bileşenler arasındaki tek siyah okları kendi ilgili etkileşim (dı ile eklenen çoğu durumda,) nesneler arasındaki bağımlılıkları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="162a2-261">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Önceki görüntüde bulunan yakınlaştırma: bunlar için uygun tanıtıcının alabilmeniz ASP.NET Core denetleyici komut MediatR'ın komut işlem hattına gönderir.](./media/image22.png)

<span data-ttu-id="162a2-263">**Şekil 7-25**.</span><span class="sxs-lookup"><span data-stu-id="162a2-263">**Figure 7-25**.</span></span> <span data-ttu-id="162a2-264">Tek bir CQRS mikro hizmet işleminde Dünyası desenini kullanarak</span><span class="sxs-lookup"><span data-stu-id="162a2-264">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="162a2-265">Kurumsal uygulamalar, istekleri işlemek için karmaşık alabilirsiniz, Dünyası desenini kullanarak, anlamlı nedeni olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-265">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="162a2-266">Açık bir günlük kaydı, doğrulama, Denetim ve güvenlik gibi çapraz kesme konuları sayısı eklemek yönetebilmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="162a2-266">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="162a2-267">Bu durumlarda, bir Dünyası işlem hattını güvenebilirsiniz (bkz [Dünyası deseni](https://en.wikipedia.org/wiki/Mediator_pattern)) bu ek davranışları veya çapraz kesme konuları için bir yol sağlamak.</span><span class="sxs-lookup"><span data-stu-id="162a2-267">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="162a2-268">Bir Dünyası "nasıl" Bu işlemin sarmalayan bir nesnedir: yürütme durumuna göre düzenler, bir komut işleyici şekilde çağrılır veya yükü işleyicisine sağlayın.</span><span class="sxs-lookup"><span data-stu-id="162a2-268">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="162a2-269">Dünyası bileşeniyle geniş kapsamlı kritik konular merkezi ve saydam bir şekilde dekoratörler uygulayarak uygulayabilirsiniz (veya [işlem hattı davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) beri [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="162a2-269">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="162a2-270">Daha fazla bilgi için [Dekoratör deseni](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="162a2-270">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="162a2-271">Dekoratörler ve davranışları için benzer [en boy yönelimli programlama (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)yalnızca Dünyası bileşeni tarafından yönetilen bir özel işlem ardışık düzeni uygulanır.</span><span class="sxs-lookup"><span data-stu-id="162a2-271">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="162a2-272">Geniş kapsamlı kritik konular uygulayan AOP yönlerine göre uygulanır *en boy weavers* nesne çağrısı yakalanması temelinde ya da derleme zamanında eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="162a2-272">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="162a2-273">AOP çalışmasını nasıl yaptığını görmek kolay olmadığı için her iki tipik AOP yaklaşım bazen "Sihirli gibi" çalışmaya söylenir.</span><span class="sxs-lookup"><span data-stu-id="162a2-273">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="162a2-274">Ciddi sorunlar veya hatalar ile ilgilenirken, AOP hata ayıklaması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-274">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="162a2-275">Diğer taraftan, çok daha öngörülebilir ve kolayca hata ayıklama, bu nedenle bu dekoratörler/davranışlar açık ve yalnızca Dünyası bağlamında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="162a2-275">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="162a2-276">Örneğin, mikro hizmet sıralama hizmetine içinde iki örnek davranışları uyguladık bir [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı ve [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="162a2-276">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="162a2-277">Hizmetine nasıl kullandığını gösteren davranışları uygulamasını sonraki bölümde açıklanmıştır [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors).</span><span class="sxs-lookup"><span data-stu-id="162a2-277">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="162a2-278">Kullanım iletisini (giden işlem dışı), komutun ardışık düzende sıralar</span><span class="sxs-lookup"><span data-stu-id="162a2-278">Use message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="162a2-279">Başka bir seçimi aracılarını veya ileti kuyrukları, Şekil 7-26 gösterildiği göre zaman uyumsuz iletiler kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="162a2-279">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="162a2-280">Bu seçenek ayrıca komut işleyici hemen önce Dünyası bileşeni ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-280">That option could also be combined with the mediator component right before the command handler.</span></span>

![Komutun işlem hattı, ayrıca komutlar için uygun tanıtıcının sunmak için yüksek kullanılabilirlik ileti kuyruğu tarafından işlenebilir.](./media/image23.png)

<span data-ttu-id="162a2-282">**Şekil 7-26**.</span><span class="sxs-lookup"><span data-stu-id="162a2-282">**Figure 7-26**.</span></span> <span data-ttu-id="162a2-283">CQRS komutlarıyla (dışında işlem ve işlemler arası iletişimi) ileti kuyrukları kullanma</span><span class="sxs-lookup"><span data-stu-id="162a2-283">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="162a2-284">İşlem hattı iki süreçlerine bölme gerekecektir ileti kuyrukları komutları daha da aşağı çekebilirsiniz kabul etmek için komutun işlem hattı, karmaşık kullanarak dış ileti kuyruğu üzerinden bağlı.</span><span class="sxs-lookup"><span data-stu-id="162a2-284">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="162a2-285">Yine de, ölçeklenebilirlik ve zaman uyumsuz Mesajlaşma temel performans geliştirildi ihtiyacınız varsa kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-285">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="162a2-286">Şekil 7-26 söz konusu olduğunda göz önünde bulundurun, denetleyici yalnızca komut ileti kuyruğuna gönderir ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="162a2-286">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="162a2-287">Daha sonra komut işleyicileri kendi hızlarında iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="162a2-287">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="162a2-288">Yani harika bir yararı kuyruklar: hiper ölçeklenebilirlik gerekli, stocks veya herhangi bir giriş veri hacmi yüksek senaryosuyla gibi olduğunda ileti kuyruğu durumlarda bir arabellek olarak görev yapabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-288">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="162a2-289">Ancak, zaman uyumsuz ileti kuyrukları yapısı nedeniyle, başarı veya başarısızlık komut işleminin hakkında istemci uygulamasıyla iletişim kurmak nasıl ekleyeceğimi gerekir.</span><span class="sxs-lookup"><span data-stu-id="162a2-289">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="162a2-290">Bir kural olarak, hiçbir zaman "Başlat ve unut" komutları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="162a2-290">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="162a2-291">Her iş uygulaması, bir komut başarıyla, işlenen veya en az doğrulandı ve kabul durumunda bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="162a2-291">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="162a2-292">Bu nedenle, bir zaman uyumsuz kuyruğa gönderildiği bir komut iletisi doğruladıktan sonra istemci taleplerine yanıt işaretleyebilmesine karmaşıklık işlem çalıştırdıktan sonra işlemin sonucunu döndürür. bir işlemdeki komutu işlemi karşılaştırıldığında sisteminize ekler.</span><span class="sxs-lookup"><span data-stu-id="162a2-292">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="162a2-293">Kuyrukları kullanma, ek bileşenleri ve özel iletişim sisteminizde gerektirecek diğer işlem sonucu iletileri komut sürecinde sonuç gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-293">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="162a2-294">Ayrıca, zaman uyumsuz, çoğu durumda, aşağıdaki ilginç exchange Burtsev Alexey arasındaki Greg Young'içinde açıklandığı şekilde gerekebilecek değil, tek yönlü komutlar komutlardır bir [çevrimiçi konuşma](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="162a2-294">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="162a2-295">\[Burtsev Alexey\] kişiler, zaman uyumsuz komut işleme veya tek yönlü komut Bunu yapmak için herhangi bir nedenle olmadan Mesajlaşma burada kullanır kodu çok sayıda bulabilirim (uzun bir işlemin yapılması değil, bunlar dış zaman uyumsuz kod yürütülmüyor, bile uygulama geçmez ileti veri yoluna bitvise sınırı).</span><span class="sxs-lookup"><span data-stu-id="162a2-295">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="162a2-296">Neden bu gereksiz karmaşıklık tanıtmak?</span><span class="sxs-lookup"><span data-stu-id="162a2-296">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="162a2-297">Ve aslında, sorgunuz çoğu durumda çalışır ancak ben komut işleyicileri şu ana kadar engelleme ile bir CQRS kod örneği göremedik.</span><span class="sxs-lookup"><span data-stu-id="162a2-297">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="162a2-298">\[Greg Young\] \[... \] zaman uyumsuz bir komutu yok; aslında başka bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="162a2-298">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="162a2-299">Gereken ne bana gönderdiğiniz kabul ediyorum ve etmiyorum ise bir olay tetikleyebilir, artık, bana bir şeyler belirten değildir \[diğer bir deyişle, bir komut değil\].</span><span class="sxs-lookup"><span data-stu-id="162a2-299">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it’s not a command\].</span></span> <span data-ttu-id="162a2-300">Bana bir şey bitti belirten olduğunu.</span><span class="sxs-lookup"><span data-stu-id="162a2-300">It's you telling me something has been done.</span></span> <span data-ttu-id="162a2-301">Bu küçük bir fark ilk gibi görünüyor, ancak birçok etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="162a2-301">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="162a2-302">Hataları göstermek için basit bir yolu yoktur çünkü zaman uyumsuz komutları bir sistem karmaşıklığını büyük ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-302">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="162a2-303">Bu nedenle, zaman uyumsuz komutları dışında ölçeklendirme gereksinimlerini gerektiğinde veya özel durumlarda Mesajlaşma aracılığıyla iç mikro hizmetler kurarken önerilmez.</span><span class="sxs-lookup"><span data-stu-id="162a2-303">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="162a2-304">Bu gibi durumlarda, hatalar için ayrı bir raporlama ve kurtarma sistemi tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="162a2-304">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="162a2-305">Hizmetine ilk sürümünde, zaman uyumlu bir komut işleme, HTTP isteklerinden kullanmaya ve odaklı Dünyası deseni tarafından kullanılacak verdik.</span><span class="sxs-lookup"><span data-stu-id="162a2-305">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="162a2-306">Kolayca sağlayan başarısı veya başarısızlığı işlemin olarak döndürülecek [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) uygulaması.</span><span class="sxs-lookup"><span data-stu-id="162a2-306">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="162a2-307">Herhangi bir durumda, bu uygulamanın veya mikro hizmet'ın iş gereksinimlerine göre bir karar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-307">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="162a2-308">Dünyası desen (MediatR) komut işlem hattıyla uygulayın</span><span class="sxs-lookup"><span data-stu-id="162a2-308">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="162a2-309">Örnek uygulama, bu kılavuz, sürücü komut alımı ve bellekte doğru komut işleyicileri için rota komutları Dünyası düzene göre işlem içi işlem hattını kullanarak önerir.</span><span class="sxs-lookup"><span data-stu-id="162a2-309">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="162a2-310">Kılavuz, ayrıca uygulama önerir [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) geniş kapsamlı kritik konular ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="162a2-310">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="162a2-311">.NET Core için uygulama, Dünyası desen uygulayan birden fazla açık kaynak kitaplıkları kullanılabilir vardır.</span><span class="sxs-lookup"><span data-stu-id="162a2-311">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="162a2-312">Bu kılavuzda kullanılan kitaplık [MediatR](https://github.com/jbogard/MediatR) açık kaynak kitaplığı (Jimmy Bogard tarafından oluşturulan), ancak başka bir yaklaşım kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-312">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="162a2-313">MediatR dekoratörler veya davranışlardan uygulanırken bir komutu gibi bellek içi iletiler işlemenize imkan tanıyan küçük ve basit bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="162a2-313">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="162a2-314">Dünyası desenini kullanarak, yardımcı bağlantısından azaltmak ve bu işi gerçekleştiren işleyicinin otomatik olarak bağlanma sırasında istenen iş sorunları yalıtmak için — bu durumda, için komut işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="162a2-314">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="162a2-315">Dünyası desen kullanmak için başka bir nedeni Jimmy Bogard tarafından bu kılavuzu gözden geçirdikleri sırada açıklamaları:</span><span class="sxs-lookup"><span data-stu-id="162a2-315">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="162a2-316">Sanırım burada test söz olabilir – sisteminizi davranışını iyi tutarlı bir pencere sağlar.</span><span class="sxs-lookup"><span data-stu-id="162a2-316">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="162a2-317">İstek, yanıt genişletme. Biz bu yönü testleri tutarlı bir şekilde davrandığından binada oldukça değerli buldunuz.</span><span class="sxs-lookup"><span data-stu-id="162a2-317">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="162a2-318">İlk olarak örnek Webapı denetleyicisi Dünyası nesne aslında burada kullanacağınız bakalım.</span><span class="sxs-lookup"><span data-stu-id="162a2-318">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="162a2-319">Dünyası nesne kullanmadıysanız, tüm bağımlılıkları söz konusu denetleyici için bir Günlükçü nesnesi ve diğerleri gibi eklemesine gerekir.</span><span class="sxs-lookup"><span data-stu-id="162a2-319">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="162a2-320">Bu nedenle, oluşturucu oldukça karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-320">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="162a2-321">Öte yandan, oluşturucu denetleyicinizin Dünyası nesnesi kullanıyorsanız, aşağıdaki örnekte olduğu gibi çapraz kesme işlemi başına bir tablonuz varsa birçok bağımlılıkları yerine yalnızca birkaç bağımlılıkları olan çok basit olabilir:</span><span class="sxs-lookup"><span data-stu-id="162a2-321">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator, 
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

<span data-ttu-id="162a2-322">Dünyası temizleme ve akıllı bir Web API denetleyicisi Oluşturucusu sağladığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-322">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="162a2-323">Ayrıca, denetleyici yöntemlerinde Dünyası nesne için bir komut göndermek için kod neredeyse bir satırı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="162a2-323">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

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

### <a name="implement-idempotent-commands"></a><span data-ttu-id="162a2-324">Uygulama kere etkili olacak komutlar</span><span class="sxs-lookup"><span data-stu-id="162a2-324">Implement idempotent Commands</span></span>

<span data-ttu-id="162a2-325">İçinde **hizmetine**, yukarıdaki değerinden daha gelişmiş bir örnek, sıralama mikro hizmet CreateOrderCommand nesneden gönderiliyor.</span><span class="sxs-lookup"><span data-stu-id="162a2-325">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="162a2-326">Ancak sıralama iş süreci biraz daha karmaşıktır ve bu örnekte, aslında sepet mikro başladıktan sonra bu eylem CreateOrderCommand nesne gönderme adlı bir tümleştirme olay işleyicisinden gerçekleştirilir > UserCheckoutAcceptedIntegrationEvent.cs] (https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) yerine basit Webapı denetleyicisi adlı basit bir önceki örnekte olduğu gibi uygulama istemciden.</span><span class="sxs-lookup"><span data-stu-id="162a2-326">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="162a2-327">Bununla birlikte, gönderme MediatR komutu aşağıdaki kodda gösterildiği gibi oldukça benzer eylemdir.</span><span class="sxs-lookup"><span data-stu-id="162a2-327">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

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

<span data-ttu-id="162a2-328">Ancak, bu da durumda biz de kere etkili olacak komutlar uygulama için biraz daha fazla Gelişmiş.</span><span class="sxs-lookup"><span data-stu-id="162a2-328">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="162a2-329">CreateOrderCommand işlemini bir kez etkili, olmalıdır şekilde aynı ileti yeniden deneme gibi herhangi bir nedenle nedeniyle ağ üzerinden yinelenen geliyorsa, yalnızca bir kez aynı iş sırada işlenir.</span><span class="sxs-lookup"><span data-stu-id="162a2-329">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="162a2-330">Bu işlem, bir kez etkili olması için olan ağ üzerinden gelen her ileti kimliği tarafından izlenen bir genel IdentifiedCommand içine ekleme ve iş komut (Bu durumda CreateOrderCommand) sarmalama tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="162a2-330">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="162a2-331">Aşağıdaki kod IdentifiedCommand ile bir DTO kimliği ve yanı sıra Sarmalanan iş komut nesnesi başka bir şey olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-331">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

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

<span data-ttu-id="162a2-332">Ardından adlı IdentifiedCommand için CommandHandler [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) temel iletisinin bir parçası zaten gelen kimliği bir tablodaki olup olmadığını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="162a2-332">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="162a2-333">Bu nedenle, komutu yeniden işlenmez varsa, bir kez etkili komut olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="162a2-333">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="162a2-334">Altyapı kodu tarafından gerçekleştirilen `_requestManager.ExistAsync` aşağıdaki yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="162a2-334">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

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

<span data-ttu-id="162a2-335">Yinelenen kimliği olmadığından işlenecek iş komutu gerektiğinde IdentifiedCommand iş komutun Zarf gibi davranır, iç iş komutu alır ve bunu ne zaman gösterilen kod son parçası olduğu gibi Dünyası için yeniden gönderir çalışan `_mediator.Send(message.Command)`, gelen [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="162a2-335">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="162a2-336">Bunu yaparken, bu bağlantı ve iş komut işleyici bu durumda çalıştırın, [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) çalıştığı işlem sıralama veritabanında aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="162a2-336">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

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

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="162a2-337">MediatR tarafından kullanılan türleri kaydetme</span><span class="sxs-lookup"><span data-stu-id="162a2-337">Register the types used by MediatR</span></span>

<span data-ttu-id="162a2-338">Komut işleyici sınıflarınızı dikkat etmeniz MediatR IOC kapsayıcınızı Dünyası sınıfları ve komut işleyici sınıflarını kaydettirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="162a2-338">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="162a2-339">Varsayılan olarak, MediatR Autofac IOC kapsayıcı olarak kullanılır, ancak yerleşik ASP.NET Core IOC kapsayıcı ya da MediatR tarafından desteklenen herhangi bir kapsayıcı da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-339">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="162a2-340">Aşağıdaki kod, Dünyası'nın türleri ve komutlar Autofac modülleri kullanırken kaydettirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="162a2-340">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

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

<span data-ttu-id="162a2-341">Burada "ile MediatR sihrin".</span><span class="sxs-lookup"><span data-stu-id="162a2-341">This is where “the magic happens” with MediatR.</span></span>

<span data-ttu-id="162a2-342">Her komut işleyici genel uyguladığından `IAsyncRequestHandler<T>` arabirimi, derlemeleri, kaydolurken kodunu kaydeder ile `RegisteredAssemblyTypes` tüm türleri olarak işaretlenmiş `IAsyncRequestHandler` ilgili çalışırken `CommandHandlers` ile kendi `Commands`, teşekkür ederiz konumunda belirtilen ilişkiye `CommandHandler` aşağıdaki örnekteki gibi bir sınıfı:</span><span class="sxs-lookup"><span data-stu-id="162a2-342">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="162a2-343">Komutları komut işleyicileri karşılık gelen kod olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="162a2-343">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="162a2-344">Basit bir sınıf işleyici olduğu halde devraldığı `RequestHandler<T>`, burada T komut türü ve MediatR doğru Yükü (komut) çağrıldığında emin yapar.</span><span class="sxs-lookup"><span data-stu-id="162a2-344">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="162a2-345">Geniş kapsamlı kritik konular MediatR davranışları komutlarıyla işlerken Uygula</span><span class="sxs-lookup"><span data-stu-id="162a2-345">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="162a2-346">Bir şey daha vardır: geniş kapsamlı kritik konular Dünyası işlem hattına uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="162a2-346">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="162a2-347">Ayrıca, nasıl bunu bir davranış türü özel olarak kaydeder, özel bir LoggingBehavior sınıf ve ValidatorBehavior sınıfı Autofac kayıt modülü kodu sonunda görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-347">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="162a2-348">Ancak özel davranışları çok ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-348">But you could add other custom behaviors, too.</span></span>

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

<span data-ttu-id="162a2-349">Olduğunu [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı ve yürütülen komut işleyici değil başarılı olup hakkındaki bilgileri kaydeder aşağıdaki kodu olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="162a2-349">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

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

<span data-ttu-id="162a2-350">Bu davranış sınıfı uygulama tarafından ve işlem hattı (yukarıdaki MediatorModule) içinde kaydederek MediatR işlenen tüm komutları yürütme hakkında bilgi günlüğe kaydetme.</span><span class="sxs-lookup"><span data-stu-id="162a2-350">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="162a2-351">Mikro hizmet, ikinci bir davranış temel doğrulamaları için de geçerlidir sıralama hizmetine [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) dayanan sınıfı [FluentValidation](https://github.com/JeremySkinner/FluentValidation) gösterildiği kitaplığı Aşağıdaki kodu:</span><span class="sxs-lookup"><span data-stu-id="162a2-351">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

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

<span data-ttu-id="162a2-352">Doğrulama başarısız olursa, bir özel durum davranışını buraya oluşturur, ancak sonuç nesnesi da döndürebilir, işe yaramadı durumunda başarılı komutu sonucu içeren veya doğrulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="162a2-352">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn’t.</span></span> <span data-ttu-id="162a2-353">Bu büyük olasılıkla doğrulama sonuçları kullanıcıya görüntülenecek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="162a2-353">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="162a2-354">Ardından, temel [FluentValidation](https://github.com/JeremySkinner/FluentValidation) kitaplığı, oluşturduğumuz CreateOrderCommand ile olduğu gibi aşağıdaki kodu geçirilen veriler için doğrulama:</span><span class="sxs-lookup"><span data-stu-id="162a2-354">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

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

<span data-ttu-id="162a2-355">Ek doğrulama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-355">You could create additional validations.</span></span> <span data-ttu-id="162a2-356">Komut doğrulamaları uygulamak için çok temiz ve şık bir yolu budur.</span><span class="sxs-lookup"><span data-stu-id="162a2-356">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="162a2-357">Benzer şekilde, ek unsurları veya bunları işlerken komutları uygulamak istediğiniz çapraz kesme konuları için diğer davranışları uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="162a2-357">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="162a2-358">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="162a2-358">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="162a2-359">Dünyası deseni</span><span class="sxs-lookup"><span data-stu-id="162a2-359">The mediator pattern</span></span>

- <span data-ttu-id="162a2-360">**Dünyası deseni** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-360">**Mediator pattern** \\</span></span>
  [*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="162a2-361">Dekoratör düzeni</span><span class="sxs-lookup"><span data-stu-id="162a2-361">The decorator pattern</span></span>

- <span data-ttu-id="162a2-362">**Dekoratör düzeni** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-362">**Decorator pattern** \\</span></span>
  [*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="162a2-363">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="162a2-363">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="162a2-364">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="162a2-364">**MediatR.**</span></span> <span data-ttu-id="162a2-365">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="162a2-365">GitHub repo.</span></span> \
  [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

- <span data-ttu-id="162a2-366">**CQRS MediatR ve AutoMapper** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-366">**CQRS with MediatR and AutoMapper** \\</span></span>
  [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

- <span data-ttu-id="162a2-367">**Denetleyicilerinizi Diyet uyguluyoruz yerleştirin: Gönderileri ve komutları.**</span><span class="sxs-lookup"><span data-stu-id="162a2-367">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  [*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

- <span data-ttu-id="162a2-368">**Bir işlem hattıyla Dünyası kuruluşlarda geniş kapsamlı kritik konular** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-368">**Tackling cross-cutting concerns with a mediator pipeline** \\</span></span>
  [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

- <span data-ttu-id="162a2-369">**CQRS ve REST: mükemmel** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-369">**CQRS and REST: the perfect match** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

- <span data-ttu-id="162a2-370">**MediatR ardışık örnekler** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-370">**MediatR Pipeline Examples** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

- <span data-ttu-id="162a2-371">**Dikey dilim Test armatürleri MediatR ve ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-371">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/*](https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/)

- <span data-ttu-id="162a2-372">**MediatR uzantıları için yayımlanan Microsoft bağımlılık ekleme** \\</span><span class="sxs-lookup"><span data-stu-id="162a2-372">**MediatR Extensions for Microsoft Dependency Injection Released** \\</span></span>
  [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a><span data-ttu-id="162a2-373">Fluent doğrulama</span><span class="sxs-lookup"><span data-stu-id="162a2-373">Fluent validation</span></span>

- <span data-ttu-id="162a2-374">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="162a2-374">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="162a2-375">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="162a2-375">GitHub repo.</span></span> \
  [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
><span data-ttu-id="162a2-376">[Önceki](microservice-application-layer-web-api-design.md)
>[İleri](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="162a2-376">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
