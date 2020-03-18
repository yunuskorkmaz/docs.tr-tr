---
title: Web API’si kullanarak mikro hizmet uygulama katmanını uygulama
description: Bağımlılık Enjeksiyonu'nu ve Aracı desenlerini ve bunların uygulama ayrıntılarını Web API uygulama katmanında anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: a88f3bfd11ea06df085ca82ed7265cb37006fc31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502441"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="064da-103">Web API'sini kullanarak mikro hizmet uygulama katmanını uygulayın</span><span class="sxs-lookup"><span data-stu-id="064da-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="064da-104">Uygulama katmanınıza altyapı nesneleri enjekte etmek için Bağımlılık Enjeksiyonu'yu kullanma</span><span class="sxs-lookup"><span data-stu-id="064da-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="064da-105">Daha önce de belirtildiği gibi, uygulama katmanı, bir Web API projesi veya Bir MVC web uygulaması projesi gibi, oluşturmakta olduğunuz yapının (derlemenin) bir parçası olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="064da-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="064da-106">ASP.NET Core ile oluşturulmuş bir microservice durumunda, uygulama katmanı genellikle Web API kitaplığınız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="064da-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="064da-107">ASP.NET Core'dan (altyapısı ve denetleyicileriniz) gelenleri özel uygulama katmanı kodunuzdan ayırmak istiyorsanız, uygulama katmanınızı ayrı bir sınıf kitaplığına da yerleştirebilirsiniz, ancak bu isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="064da-108">Örneğin, sipariş mikrohizmetinin uygulama katmanı kodu, Şekil 7-23'te gösterildiği gibi **Ordering.API** projesinin (ASP.NET Core Web API projesi) bir parçası olarak doğrudan uygulanır.</span><span class="sxs-lookup"><span data-stu-id="064da-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Çözüm Gezgini'ndeki Ordering.API microservice ekran görüntüsü.":::
<span data-ttu-id="064da-110">Uygulama klasörünün altındaki alt klasörleri gösteren Ordering.API microservice Çözüm Gezgini görünümü: Davranışlar, Komutlar, DomainEventHandlers, EntegrasyonOlaylar, Modeller, Sorgular ve Doğrulamalar.</span><span class="sxs-lookup"><span data-stu-id="064da-110">The Solution Explorer view of the Ordering.API microservice, showing the sub-folders under the Application folder: Behaviors, Commands, DomainEventHandlers, IntegrationEvents, Models, Queries and Validations.</span></span>
:::image-end:::

<span data-ttu-id="064da-111">**Şekil 7-23**.</span><span class="sxs-lookup"><span data-stu-id="064da-111">**Figure 7-23**.</span></span> <span data-ttu-id="064da-112">Ordering.API ASP.NET Core Web API projesindeki uygulama katmanı</span><span class="sxs-lookup"><span data-stu-id="064da-112">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="064da-113">ASP.NET Core, varsayılan olarak yapıcı enjeksiyonu destekleyen basit bir [dahili IoC kapsayıcısı](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (IServiceProvider arabirimi tarafından temsil edilir) içerir ve ASP.NET belirli hizmetleri DI aracılığıyla kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="064da-113">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="064da-114">ASP.NET Core, DI aracılığıyla enjekte edilecek kayıt türlerinden herhangi biri için dönem *hizmetini* kullanır.</span><span class="sxs-lookup"><span data-stu-id="064da-114">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="064da-115">Yerleşik kapsayıcının hizmetlerini uygulamanızın Başlangıç sınıfındaki ConfigureServices yönteminde yapılandırAbilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-115">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="064da-116">Bağımlılıklarınız, bir türün ihtiyaç duyduğu ve IoC kapsayıcısında kaydettiğiniz hizmetlerde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="064da-116">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="064da-117">Genellikle, altyapı nesnelerini uygulayan bağımlılıkları enjekte etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="064da-117">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="064da-118">Enjekte etmek için çok tipik bir bağımlılık bir depodur.</span><span class="sxs-lookup"><span data-stu-id="064da-118">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="064da-119">Ama sahip olabileceğiniz diğer altyapı bağımlılığını enjekte edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-119">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="064da-120">Daha basit uygulamalar için, DBContext aynı zamanda altyapı kalıcılık nesnelerinizin de uygulanması olduğundan, Çalışma Birimi desen nesnenizi (EF DbContext nesnesi) doğrudan enjekte edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-120">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="064da-121">Aşağıdaki örnekte, .NET Core'un gerekli depo nesnelerini oluşturucu aracılığıyla nasıl enjekte ettiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-121">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="064da-122">Sınıf, bir sonraki bölümde ele alacağız bir komut işleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="064da-122">The class is a command handler, which we will cover in the next section.</span></span>

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

<span data-ttu-id="064da-123">Sınıf, işlemi yürütmek ve durum değişikliklerini sürdürmek için enjekte edilen depoları kullanır.</span><span class="sxs-lookup"><span data-stu-id="064da-123">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="064da-124">Bu sınıfın bir komut işleyicisi, ASP.NET Core Web API denetleyiciyöntemi veya [DDD Uygulama Hizmeti](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)olup olmadığı önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="064da-124">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="064da-125">Sonuçta bir komut işleyicisi benzer bir şekilde depoları, etki alanı varlıkları ve diğer uygulama koordinasyonu kullanan basit bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="064da-125">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="064da-126">Bağımlılık Enjeksiyonu, oluşturucuya dayalı DI'yi kullanan örnekte olduğu gibi, belirtilen tüm sınıflar için aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="064da-126">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="064da-127">Bağımlılık uygulama türlerini ve arayüzlerini veya soyutlamalarını kaydetme</span><span class="sxs-lookup"><span data-stu-id="064da-127">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="064da-128">Oluşturucular aracılığıyla enjekte edilen nesneleri kullanmadan önce, DI aracılığıyla uygulama sınıflarınıza enjekte edilen nesneleri üreten arabirimleri ve sınıfları nereye kaydedebileceğinizi bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="064da-128">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="064da-129">(Di gibi daha önce gösterildiği gibi, yapıcı dayalı.)</span><span class="sxs-lookup"><span data-stu-id="064da-129">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="064da-130">ASP.NET Core tarafından sağlanan dahili IoC kabını kullanın</span><span class="sxs-lookup"><span data-stu-id="064da-130">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="064da-131">ASP.NET Core tarafından sağlanan yerleşik IoC kapsayıcısını kullandığınızda, Startup.cs dosyasında aşağıdaki kodda olduğu gibi Yapılandırma Hizmetleri yönteminde enjekte etmek istediğiniz türleri kaydedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="064da-131">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
        c.UseSqlServer(Configuration["ConnectionString"]),
        ServiceLifetime.Scoped);

    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="064da-132">Bir IoC kapsayıcısında türleri kaydederken en yaygın desen, bir çift tür-bir arabirim ve ilgili uygulama sınıfı kaydetmektir.</span><span class="sxs-lookup"><span data-stu-id="064da-132">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="064da-133">Daha sonra herhangi bir oluşturucu aracılığıyla IoC kapsayıcısından bir nesne istediğinizde, belirli bir tür arabirim nesnesi istersiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-133">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="064da-134">Örneğin, önceki örnekte, son satır, oluşturucularınızın IMyCustomRepository'ye (arayüz veya soyutlama) bağımlı olduğunu belirtirken, IoC kapsayıcısının MyCustomSQLServerRepository uygulamasının bir örneğini enjekte edeceğini belirtir Sınıfı.</span><span class="sxs-lookup"><span data-stu-id="064da-134">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="064da-135">Otomatik tür kaydı için Scrutor kitaplığını kullanma</span><span class="sxs-lookup"><span data-stu-id="064da-135">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="064da-136">.NET Core'da DI kullanırken, bir derlemeyi tarayabilmek ve türlerini kuralkuralına göre otomatik olarak kaydedebilmeniz isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-136">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="064da-137">Bu özellik şu anda ASP.NET Core'da kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="064da-137">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="064da-138">Ancak, bunun için [Scrutor](https://github.com/khellang/Scrutor) kitaplığını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-138">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="064da-139">Bu yaklaşım, IoC kapsayıcınıza kaydedilmesi gereken düzinelerce türüolduğunda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-139">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="064da-140">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="064da-140">Additional resources</span></span>

- <span data-ttu-id="064da-141">**Matthew King. Hizmetleri Scrutor'a kaydetme** </span><span class="sxs-lookup"><span data-stu-id="064da-141">**Matthew King. Registering services with Scrutor** </span></span>\
  <https://www.mking.net/blog/registering-services-with-scrutor>

- <span data-ttu-id="064da-142">**Kristian Hellang. Scrutor, ne var?**</span><span class="sxs-lookup"><span data-stu-id="064da-142">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="064da-143">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="064da-143">GitHub repo.</span></span> \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="064da-144">Autofac'ı IoC kapsayıcısı olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="064da-144">Use Autofac as an IoC container</span></span>

<span data-ttu-id="064da-145">Ayrıca ek IoC kapları kullanabilirsiniz ve [autofac](https://autofac.org/)kullanan eShopOnContainers, sipariş microservice olduğu gibi, ASP.NET Core boru hattı na takabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="064da-146">Autofac kullanırken genellikle, uygulama türlerinin birden çok sınıf kitaplıklarına dağıtılabileceği gibi, türünüzün nerede olduğuna bağlı olarak kayıt türlerini birden çok dosya arasında bölmenize olanak tanıyan türleri modüller aracılığıyla kaydedersiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="064da-147">Örneğin, aşağıdaki leri, enjekte etmek isteyeceğiniz türleri içeren [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projesinin [Autofac uygulama modülüdür.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs)</span><span class="sxs-lookup"><span data-stu-id="064da-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

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

<span data-ttu-id="064da-148">Autofac ayrıca [derlemeleri tarayıp ad kurallarına göre türleri kaydetme özelliğine](https://autofac.readthedocs.io/en/latest/register/scanning.html)de sahiptir.</span><span class="sxs-lookup"><span data-stu-id="064da-148">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="064da-149">Kayıt işlemi ve kavramları, yerleşik ASP.NET Core IoC kapsayıcısı ile türleri kaydedebilirsiniz şekilde çok benzer, ancak Autofac kullanırken sözdizimi biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-149">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="064da-150">Örnek kodda, soyutlama IOrderRepository uygulama sınıfı OrderRepository ile birlikte kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="064da-150">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="064da-151">Bu, bir oluşturucu IOrderRepository soyutlama veya arabirim üzerinden bir bağımlılık beyan ettiğinde, IoC kapsayıcıorderRepository sınıfının bir örneğini enjekte edeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="064da-151">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="064da-152">Örnek kapsam türü, bir örneğin aynı hizmet veya bağımlılık istekleri arasında nasıl paylaşılbildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="064da-152">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="064da-153">Bağımlılık için bir istek yapıldığında, IoC kapsayıcıaşağıdakileri döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="064da-153">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="064da-154">Toplam kapsam başına tek bir örnek (ASP.NET Core IoC kapsayıcısında *kapsamlı*olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="064da-154">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="064da-155">Bağımlılık başına yeni bir örnek (ASP.NET Core IoC kapsayıcısında *geçici*olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="064da-155">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="064da-156">IoC kapsayıcısını kullanarak tüm nesneler arasında paylaşılan tek bir örnek (ASP.NET Core IoC kapsayıcısında *singleton*olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="064da-156">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="064da-157">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="064da-157">Additional resources</span></span>

- <span data-ttu-id="064da-158">**ASP.NET Çekirdekte Bağımlılık Enjeksiyonuna Giriş** </span><span class="sxs-lookup"><span data-stu-id="064da-158">**Introduction to Dependency Injection in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="064da-159">**Autofac mı?**</span><span class="sxs-lookup"><span data-stu-id="064da-159">**Autofac.**</span></span> <span data-ttu-id="064da-160">Resmi belgeler.</span><span class="sxs-lookup"><span data-stu-id="064da-160">Official documentation.</span></span> \
  <https://docs.autofac.org/en/latest/>

- <span data-ttu-id="064da-161">**Autofac IoC konteyner örnek kapsamları ile Core IoC konteyner hizmet ömürleri ASP.NET karşılaştırma - Cesar de la Torre.**</span><span class="sxs-lookup"><span data-stu-id="064da-161">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="064da-162">Komut ve Komut İşleyici sülelerini uygulama</span><span class="sxs-lookup"><span data-stu-id="064da-162">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="064da-163">Önceki bölümde gösterilen DI-through-constructor örneğinde, IoC kapsayıcı bir sınıfta bir oluşturucu aracılığıyla depoları enjekte edildi.</span><span class="sxs-lookup"><span data-stu-id="064da-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="064da-164">Ama tam olarak nereye enjekte edildi?</span><span class="sxs-lookup"><span data-stu-id="064da-164">But exactly where were they injected?</span></span> <span data-ttu-id="064da-165">Basit bir Web API'sinde (örneğin, eShopOnContainers'daki katalog microservice' te), bunları ASP.NET Core'un istek ardışık ardışık ardışık yapısının bir parçası olarak, bir denetleyici oluşturucuda MVC denetleyicileri düzeyinde enjekte elersiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers’ level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="064da-166">Ancak, bu bölümün ilk kodunda (eShopOnContainers'daki Ordering.API hizmetinden [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) sınıfı), bağımlılıkların enjeksiyonu belirli bir komut işleyicisinin oluşturucusu aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="064da-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="064da-167">Komut işleyicinin ne olduğunu ve neden kullanmak istediğinizi açıklayalım.</span><span class="sxs-lookup"><span data-stu-id="064da-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="064da-168">Komut deseni, bu kılavuzda daha önce tanıtılan CQRS deseni ile özünde ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="064da-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="064da-169">CQRS'nin iki tarafı vardır.</span><span class="sxs-lookup"><span data-stu-id="064da-169">CQRS has two sides.</span></span> <span data-ttu-id="064da-170">İlk alan, daha önce açıklanan [Dapper](https://github.com/StackExchange/dapper-dot-net) mikro ORM ile basitleştirilmiş sorgular kullanılarak yapılan sorgulardır.</span><span class="sxs-lookup"><span data-stu-id="064da-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="064da-171">İkinci alan, hareketler için başlangıç noktası olan komutlar ve hizmet dışından gelen giriş kanalıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="064da-172">Şekil 7-24'te gösterildiği gibi, desen istemci tarafından komutları kabul etmeye, etki alanı modeli kurallarına göre işlemeye ve son olarak durumları işlemlerle devam etmeye dayanır.</span><span class="sxs-lookup"><span data-stu-id="064da-172">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![İstemciden veritabanına üst düzey veri akışını gösteren diyagram.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

<span data-ttu-id="064da-174">**Şekil 7-24**.</span><span class="sxs-lookup"><span data-stu-id="064da-174">**Figure 7-24**.</span></span> <span data-ttu-id="064da-175">CQRS deseni ndeki komutların veya "işlem tarafının" üst düzey görünümü</span><span class="sxs-lookup"><span data-stu-id="064da-175">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

<span data-ttu-id="064da-176">Şekil 7-24, Kullanıcı Bira uygulamasının API aracılığıyla veritabanını güncelleştirmek için `CommandHandler`Etki Alanı modeline ve Altyapıya bağlı bir komut gönderdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="064da-176">Figure 7-24 shows that the UI app sends a command through the API that gets to a `CommandHandler`, that depends on the Domain model and the Infrastructure, to update the database.</span></span>

### <a name="the-command-class"></a><span data-ttu-id="064da-177">Komut sınıfı</span><span class="sxs-lookup"><span data-stu-id="064da-177">The command class</span></span>

<span data-ttu-id="064da-178">Komut, sistemin durumunu değiştiren bir eylemi gerçekleştirmesi için bir istektir.</span><span class="sxs-lookup"><span data-stu-id="064da-178">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="064da-179">Komutlar zorunludur ve sadece bir kez işlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="064da-179">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="064da-180">Komutlar zorunlu olduğundan, genellikle zorunlu ruh halinde bir fiille adlandırılırlar (örneğin, "oluştur" veya "güncelleştirme") ve CreateOrderCommand gibi toplu türü içerebilir.</span><span class="sxs-lookup"><span data-stu-id="064da-180">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="064da-181">Bir olayın aksine, bir komut geçmişten gelen bir gerçek değildir; bu sadece bir istektir ve bu nedenle reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="064da-181">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="064da-182">Komutlar, kullanıcının bir istek başlatması sonucunda kullanıcının ui'den veya işlem yöneticisi bir topluyu bir eylemi gerçekleştirmeye yönlendirirken bir işlem yöneticisinden kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="064da-182">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="064da-183">Bir komutun önemli bir özelliği, tek bir alıcı tarafından sadece bir kez işlenmesi gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="064da-183">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="064da-184">Bunun nedeni, komutun uygulamada gerçekleştirmek istediğiniz tek bir eylem veya işlem olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-184">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="064da-185">Örneğin, aynı sipariş oluşturma komutu birden fazla kez işlenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="064da-185">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="064da-186">Bu komutlar ve olaylar arasında önemli bir farktır.</span><span class="sxs-lookup"><span data-stu-id="064da-186">This is an important difference between commands and events.</span></span> <span data-ttu-id="064da-187">Birçok sistem veya mikro hizmet olayla ilgilenebileceğinden, olaylar birden çok kez işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="064da-187">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="064da-188">Buna ek olarak, komutun iktidarsız olmaması durumunda bir komutun yalnızca bir kez işlenmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="064da-188">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="064da-189">Bir komut, sonucu değiştirmeden birden çok kez yürütülebiliyorsa, komutun yapısı ndan veya sistemin komutu işleme biçiminden dolayı idempotenttir.</span><span class="sxs-lookup"><span data-stu-id="064da-189">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="064da-190">Etki alanınızın iş kuralları ve değişmezleri altında mantıklı olduğunda komutlarınızı ve güncelleştirmelerinizi iktidara getirmek iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="064da-190">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="064da-191">Örneğin, aynı örneği kullanmak için, herhangi bir nedenle (yeniden deneme mantığı, hackleme, vb.) aynı CreateOrder komutu sisteminize birden çok kez ulaşırsa, bu örneği tanımlayabilmeli ve birden çok sipariş oluşturmadığınızdan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="064da-191">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="064da-192">Bunu yapmak için, işlemlere bir tür kimlik eklemeniz ve komutun veya güncelleştirmenin zaten işlenip işlenmediğini belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="064da-192">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="064da-193">Tek bir alıcıya bir komut gönderirsiniz; bir komut yayımlamazsınız.</span><span class="sxs-lookup"><span data-stu-id="064da-193">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="064da-194">Yayımlama, bir şeyin olduğunu ve etkinlik alıcıları için ilginç olabileceğini belirten olaylar içindir.</span><span class="sxs-lookup"><span data-stu-id="064da-194">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="064da-195">Olaylar söz konusu olduğunda, yayımcının hangi alıcıların olayı aldığı veya ne yaptığı konusunda hiçbir endişesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="064da-195">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="064da-196">Ancak etki alanı veya tümleştirme olayları zaten önceki bölümlerde tanıtılan farklı bir hikaye vardır.</span><span class="sxs-lookup"><span data-stu-id="064da-196">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="064da-197">Bir komut, bu komutu yürütmek için gereken tüm bilgileri içeren veri alanları veya koleksiyonları içeren bir sınıf la birlikte uygulanır.</span><span class="sxs-lookup"><span data-stu-id="064da-197">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="064da-198">Komut, özellikle değişiklik veya hareket istemek için kullanılan özel bir Veri Aktarım Nesnesi (DTO) türüdür.</span><span class="sxs-lookup"><span data-stu-id="064da-198">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="064da-199">Komutun kendisi, komutu işlemek için gereken bilgilere dayanır ve başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="064da-199">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="064da-200">Aşağıdaki örnekbasitleştirilmiş `CreateOrderCommand` sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="064da-200">The following example shows the simplified `CreateOrderCommand` class.</span></span> <span data-ttu-id="064da-201">Bu eShopOnContainers sipariş microservice kullanılan değişmez bir komutdur.</span><span class="sxs-lookup"><span data-stu-id="064da-201">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

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
// https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties
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

<span data-ttu-id="064da-202">Temel olarak, komut sınıfı etki alanı modeli nesneleri kullanarak bir iş hareketi gerçekleştirmek için gereken tüm verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="064da-202">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="064da-203">Bu nedenle, komutlar salt okunur veri içeren ve hiçbir davranış sadece veri yapılarıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-203">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="064da-204">Komutun adı amacını gösterir.</span><span class="sxs-lookup"><span data-stu-id="064da-204">The command’s name indicates its purpose.</span></span> <span data-ttu-id="064da-205">C# gibi birçok dilde komutlar sınıf olarak temsil edilir, ancak gerçek nesne yönelimli anlamda gerçek sınıflar değildir.</span><span class="sxs-lookup"><span data-stu-id="064da-205">In many languages like C#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="064da-206">Ek bir özellik olarak, beklenen kullanım doğrudan etki alanı modeli tarafından işlenir, çünkü komutları değişmez.</span><span class="sxs-lookup"><span data-stu-id="064da-206">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="064da-207">Öngörülen yaşamları boyunca değişmelerine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="064da-207">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="064da-208">C# sınıfında, iç durumu değiştiren herhangi bir ayarlayıcı veya başka yöntemlerin olmamasıyla imkansızlık sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="064da-208">In a C# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="064da-209">Komutların serileştirme/deserializing işleminden geçmesini istiyorsanız veya bekliyorsanız, özelliklerin özel bir ayarlayıcısı ve `[DataMember]` (veya) `[JsonProperty]`özniteliği olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="064da-209">Keep in mind that if you intend or expect commands to go through a serializing/deserializing process, the properties must have a private setter, and the `[DataMember]` (or `[JsonProperty]`) attribute.</span></span> <span data-ttu-id="064da-210">Aksi takdirde, deserializer gerekli değerleri ile hedef nesneyi yeniden mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="064da-210">Otherwise, the deserializer won't be able to reconstruct the object at destination with the required values.</span></span> <span data-ttu-id="064da-211">Sınıfın tüm özellikleri için parametreleri olan bir oluşturucuvarsa, her zamanki camelCase adlandırma kuralıile gerçekten salt okunur özelliklerini `[JsonConstructor]`de kullanabilirsiniz ve oluşturucuyu .</span><span class="sxs-lookup"><span data-stu-id="064da-211">You can also use truly read-only properties if the class has a constructor with parameters for all properties, with the usual camelCase naming convention, and annotate the constructor as `[JsonConstructor]`.</span></span> <span data-ttu-id="064da-212">Ancak, bu seçenek daha fazla kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="064da-212">However, this option requires more code.</span></span>

<span data-ttu-id="064da-213">Örneğin, bir sipariş oluşturmak için komut sınıfı büyük olasılıkla oluşturmak istediğiniz sıraya veri açısından benzer, ancak büyük olasılıkla aynı öznitelikleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="064da-213">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="064da-214">Örneğin, `CreateOrderCommand` sipariş henüz oluşturulmadığından, sipariş kimliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="064da-214">For instance, `CreateOrderCommand` does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="064da-215">Birçok komut sınıfı, değiştirilmesi gereken bazı durum hakkında yalnızca birkaç alan gerektiren basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="064da-215">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="064da-216">Bir siparişin durumunu aşağıdakilere benzer bir komut kullanarak "işlemde" "ücretli" veya "sevk" olarak değiştiriyorsanız durum böyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="064da-216">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

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

<span data-ttu-id="064da-217">Bazı geliştiriciler, UI istek nesnelerini komut DT'lerinden ayrı hale getirsin, ancak bu yalnızca bir tercih konusudur.</span><span class="sxs-lookup"><span data-stu-id="064da-217">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="064da-218">Bu çok fazla katma değer ile sıkıcı bir ayrım, ve nesneleri hemen hemen aynı şekli vardır.</span><span class="sxs-lookup"><span data-stu-id="064da-218">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="064da-219">Örneğin, eShopOnContainers, bazı komutlar doğrudan istemci tarafında gelir.</span><span class="sxs-lookup"><span data-stu-id="064da-219">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="064da-220">Komut işleyicisınıfı</span><span class="sxs-lookup"><span data-stu-id="064da-220">The Command handler class</span></span>

<span data-ttu-id="064da-221">Her komut için belirli bir komut işleyicisi sınıfı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="064da-221">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="064da-222">Desen bu şekilde çalışır ve komut nesnesini, etki alanı nesnelerini ve altyapı deposu nesnelerini kullanacağınız yerdir.</span><span class="sxs-lookup"><span data-stu-id="064da-222">That is how the pattern works, and it's where you'll use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="064da-223">Komut işleyicisi aslında CQRS ve DDD açısından uygulama katmanının kalbidir.</span><span class="sxs-lookup"><span data-stu-id="064da-223">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="064da-224">Ancak, tüm etki alanı mantığı etki alanı sınıflarında-toplam kökleri (kök varlıklar), alt varlıklar veya [etki alanı hizmetleri](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)içinde içermelidir, ancak uygulama katmanından bir sınıf olan komut işleyicisi içinde değil.</span><span class="sxs-lookup"><span data-stu-id="064da-224">However, all the domain logic should be contained in the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="064da-225">Komut işleyicisınıfı, bir önceki bölümde belirtilen Tek Sorumluluk İlkesi'ni (SRP) elde etme yolunda güçlü bir basamak sunar.</span><span class="sxs-lookup"><span data-stu-id="064da-225">The command handler class offers a strong stepping stone in the way to achieve the Single Responsibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="064da-226">Bir komut işleyicisi bir komut alır ve kullanılan toplam bir sonuç alır.</span><span class="sxs-lookup"><span data-stu-id="064da-226">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="064da-227">Sonuç, komutun başarılı bir şekilde yürütülmesi veya bir özel durum olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-227">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="064da-228">Bir özel durum söz konusu olduğunda, sistem durumu değişmemelidir.</span><span class="sxs-lookup"><span data-stu-id="064da-228">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="064da-229">Komut işleyicisi genellikle aşağıdaki adımları alır:</span><span class="sxs-lookup"><span data-stu-id="064da-229">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="064da-230">DTO [(arabulucu](https://en.wikipedia.org/wiki/Mediator_pattern) veya diğer altyapı nesnesinden) gibi komut nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="064da-230">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="064da-231">Komutun geçerli olduğunu doğrular (arabulucu tarafından doğrulanmadıysa).</span><span class="sxs-lookup"><span data-stu-id="064da-231">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="064da-232">Geçerli komutun hedefi olan toplam kök örneğini anında alartır.</span><span class="sxs-lookup"><span data-stu-id="064da-232">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="064da-233">Bu komutu gerekli verileri alarak, toplam kök örnek üzerinde yöntemi yürütür.</span><span class="sxs-lookup"><span data-stu-id="064da-233">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="064da-234">Agreganın yeni durumunu ilgili veritabanında devam eder.</span><span class="sxs-lookup"><span data-stu-id="064da-234">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="064da-235">Bu son işlem gerçek işlemdir.</span><span class="sxs-lookup"><span data-stu-id="064da-235">This last operation is the actual transaction.</span></span>

<span data-ttu-id="064da-236">Genellikle, bir komut işleyicisi, toplam kökü (kök varlığı) tarafından yönlendirilen tek bir toplamla ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="064da-236">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="064da-237">Tek bir komutun alınmasından birden çok agrega etkilenecekse, durumları veya eylemleri birden çok toplama arasında yaymak için etki alanı olaylarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-237">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="064da-238">Burada önemli olan nokta, bir komut işlenirken, tüm etki alanı mantığının etki alanı modelinin (toplamlar) içinde, tamamen kapsüllenmiş ve birim testine hazır olması gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="064da-238">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="064da-239">Komut işleyicisi, etki alanı modelini veritabanından almanın bir yolu olarak ve son adım olarak, altyapı katmanına (depolar) model değiştirildiğinde değişiklikleri devam etmesini söylemek için hareket eder.</span><span class="sxs-lookup"><span data-stu-id="064da-239">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="064da-240">Bu yaklaşımın avantajı, tesisat düzeyi (komut işleyicileri, Web API, uygulama veya altyapı katmanlarında kod değiştirmeden yalıtılmış, tamamen kapsüllenmiş, zengin, davranışsal etki alanı modelinde etki alanı mantığını yeniden depolar, vb.)</span><span class="sxs-lookup"><span data-stu-id="064da-240">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="064da-241">Komut işleyicileri karmaşık hale geldiğinde, çok fazla mantıkla, bu bir kod kokusu olabilir.</span><span class="sxs-lookup"><span data-stu-id="064da-241">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="064da-242">Bunları gözden geçirin ve etki alanı mantığı bulursanız, etki alanı davranışını etki alanı nesnelerinin (toplam kök ve alt varlık) yöntemlerine taşımak için kodu yeniden düzenlemeyi.</span><span class="sxs-lookup"><span data-stu-id="064da-242">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="064da-243">Komut işleyicisi sınıfına örnek olarak, aşağıdaki `CreateOrderCommandHandler` kod bu bölümün başında gördüğünüz aynı sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="064da-243">As an example of a command handler class, the following code shows the same `CreateOrderCommandHandler` class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="064da-244">Bu durumda, Tutamaç yöntemini ve etki alanı modeli nesneleri/toplamları ile işlemleri vurgulamak istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="064da-244">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

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

<span data-ttu-id="064da-245">Bunlar, komut işleyicinin atması gereken ek adımlardır:</span><span class="sxs-lookup"><span data-stu-id="064da-245">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="064da-246">Toplam kökün yöntemleri ve davranışlarıyla çalışmak için komutverilerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="064da-246">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

- <span data-ttu-id="064da-247">Etki alanı nesneleri içinde dahili olarak, işlem yürütülürken etki alanı olaylarını yükseltmek, ancak bir komut işleyicisi bakış açısından saydamdır.</span><span class="sxs-lookup"><span data-stu-id="064da-247">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="064da-248">Agreganın işlem sonucu başarılı olursa ve işlem tamamlandıktan sonra tümleştirme olaylarını yükseltin.</span><span class="sxs-lookup"><span data-stu-id="064da-248">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="064da-249">(Bunlar, depolar gibi altyapı sınıfları tarafından da gündeme getirilebilir.)</span><span class="sxs-lookup"><span data-stu-id="064da-249">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="064da-250">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="064da-250">Additional resources</span></span>

- <span data-ttu-id="064da-251">**Mark Seemann. Sınırlarda, Uygulamalar Nesne Yönelimli Değildir** </span><span class="sxs-lookup"><span data-stu-id="064da-251">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** </span></span>\
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- <span data-ttu-id="064da-252">**Komutlar ve olaylar** </span><span class="sxs-lookup"><span data-stu-id="064da-252">**Commands and events** </span></span>\
  <https://cqrs.nu/Faq/commands-and-events>

- <span data-ttu-id="064da-253">**Bir komut işleyicisi ne yapar?**</span><span class="sxs-lookup"><span data-stu-id="064da-253">**What does a command handler do?**</span></span> \
  <https://cqrs.nu/Faq/command-handlers>

- <span data-ttu-id="064da-254">**Jimmy Bogard' ı. Etki Alanı Komut Desenleri - Işleyiciler** </span><span class="sxs-lookup"><span data-stu-id="064da-254">**Jimmy Bogard. Domain Command Patterns – Handlers** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- <span data-ttu-id="064da-255">**Jimmy Bogard' ı. Etki Alanı Komut Uyruğu Desenleri – Doğrulama** </span><span class="sxs-lookup"><span data-stu-id="064da-255">**Jimmy Bogard. Domain Command Patterns – Validation** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="064da-256">Komut işlemi ardışık hattı: komut işleyicisi nasıl tetiklenir</span><span class="sxs-lookup"><span data-stu-id="064da-256">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="064da-257">Bir sonraki soru, komut işleyicisi nasıl çağrılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-257">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="064da-258">İlgili her ASP.NET Core denetleyicisinden el ile arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-258">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="064da-259">Ancak, bu yaklaşım çok birleştiğinde ve ideal değildir.</span><span class="sxs-lookup"><span data-stu-id="064da-259">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="064da-260">Önerilen seçenekler olan diğer iki ana seçenek şunlardır:</span><span class="sxs-lookup"><span data-stu-id="064da-260">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="064da-261">Hafıza içi arabulucu desen objesi aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="064da-261">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="064da-262">Denetleyiciler ve işleyiciler arasında bir eşzamanlı ileti sırası ile.</span><span class="sxs-lookup"><span data-stu-id="064da-262">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="064da-263">Komut ardışık düzeninde Arabulucu deseni (bellekte) kullanma</span><span class="sxs-lookup"><span data-stu-id="064da-263">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="064da-264">Şekil 7-25'te gösterildiği gibi, CQRS yaklaşımında, alınan komut veya DTO'nun türüne göre sağ komut işleyicisine yönlendirilecek kadar akıllı olan bellek içi veri yoluna benzer akıllı bir arabulucu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="064da-264">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="064da-265">Bileşenler arasındaki tek siyah oklar, nesneler arasındaki bağımlılıkları (çoğu durumda, DI aracılığıyla enjekte edilen) ve ilgili etkileşimlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="064da-265">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![İstemciden veritabanına daha ayrıntılı bir veri akışını gösteren diyagram.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

<span data-ttu-id="064da-267">**Şekil 7-25.**</span><span class="sxs-lookup"><span data-stu-id="064da-267">**Figure 7-25**.</span></span> <span data-ttu-id="064da-268">Tek bir CQRS microservice sürecinde Arabulucu deseni kullanma</span><span class="sxs-lookup"><span data-stu-id="064da-268">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="064da-269">Yukarıdaki diyagram, resim 7-24'ten bir yakınlaştırma gösterir: ASP.NET Core denetleyicisi komutu MediatR'ın komut ardışık hattına gönderir, böylece uygun işleyiciye ulaşırlar.</span><span class="sxs-lookup"><span data-stu-id="064da-269">The above diagram shows a zoom-in from image 7-24: the ASP.NET Core controller sends the command to MediatR's command pipeline, so they get to the appropriate handler.</span></span>

<span data-ttu-id="064da-270">Arabulucu deseni kullanmanın mantıklı olmasının nedeni, kurumsal uygulamalarda işleme isteklerinin karmaşık hale gelebiliyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-270">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="064da-271">Oturum açma, doğrulama, denetim ve güvenlik gibi açık sayıda çapraz kesme yle ilgili açık bir sayı ekleyebilmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="064da-271">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="064da-272">Bu gibi durumlarda, bu ekstra davranışlar veya çapraz kesme endişeleri için bir araç sağlamak için bir arabulucu ardışık düzenine güvenebilirsiniz (bkz. [Arabulucu deseni).](https://en.wikipedia.org/wiki/Mediator_pattern)</span><span class="sxs-lookup"><span data-stu-id="064da-272">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="064da-273">Arabulucu, bu işlemin "nasıl" olduğunu kapsülleyen bir nesnedir: yürütmeyi duruma, komut işleyicisinin çağrılma şekline veya işleyiciye sağladığınız yükü temel alınabiliyor.</span><span class="sxs-lookup"><span data-stu-id="064da-273">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="064da-274">Bir arabulucu bileşeni ile dekoratörleri (veya [MediatR 3'ten](https://www.nuget.org/packages/MediatR/3.0.0)beri [boru hattı davranışlarını)](https://github.com/jbogard/MediatR/wiki/Behaviors) uygulayarak çapraz kesme endişelerini merkezi ve şeffaf bir şekilde uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-274">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="064da-275">Daha fazla bilgi için [Dekoratör desenine](https://en.wikipedia.org/wiki/Decorator_pattern)bakın.</span><span class="sxs-lookup"><span data-stu-id="064da-275">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="064da-276">Dekoratörler ve davranışlar [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)benzer, sadece aracı bileşeni tarafından yönetilen belirli bir işlem boru hattı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="064da-276">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="064da-277">AOP'de çapraz kesme endişeleri uygulayan yönler, derleme zamanında enjekte edilen *boy dokumacılarına* veya nesne çağrısı engellemeye dayalı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="064da-277">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="064da-278">Her iki tipik AOP yaklaşımının bazen "sihir gibi" çalıştığı söylenir, çünkü AOP'un işini nasıl yaptığını görmek kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="064da-278">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="064da-279">Ciddi sorunlar veya hatalarla uğraşırken Hata ayıklama zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="064da-279">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="064da-280">Öte yandan, bu dekoratörler / davranışlar açık ve sadece arabulucu bağlamında uygulanan, bu yüzden hata ayıklama çok daha öngörülebilir ve kolaydır.</span><span class="sxs-lookup"><span data-stu-id="064da-280">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="064da-281">Örneğin, mikrohizmet sipariş için eShopOnContainers' da iki örnek davranış, bir [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınırı ve [bir ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) sınırı uyguladık.</span><span class="sxs-lookup"><span data-stu-id="064da-281">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="064da-282">Davranışların uygulanması, eShopOnContainers'ın [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [davranışlarını](https://github.com/jbogard/MediatR/wiki/Behaviors)nasıl kullandığını göstererek bir sonraki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="064da-282">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="064da-283">Komutun ardışık durumunda ileti kuyruklarını (proc dışı) kullanma</span><span class="sxs-lookup"><span data-stu-id="064da-283">Use message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="064da-284">Başka bir seçenek, Şekil 7-26'da gösterildiği gibi, aracılara veya ileti kuyruklarına dayalı eşzamanlı iletiler kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="064da-284">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="064da-285">Bu seçenek, komut işleyicisi hemen önce aracı bileşeni ile de birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="064da-285">That option could also be combined with the mediator component right before the command handler.</span></span>

![HA ileti kuyruğunu kullanarak veri akışını gösteren diyagram.](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

<span data-ttu-id="064da-287">**Şekil 7-26.**</span><span class="sxs-lookup"><span data-stu-id="064da-287">**Figure 7-26**.</span></span> <span data-ttu-id="064da-288">CQRS komutları ile ileti kuyruklarını (işlem ve süreçler arası iletişim dışında) kullanma</span><span class="sxs-lookup"><span data-stu-id="064da-288">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="064da-289">Komutun ardışık hattı, komutları uygun işleyiciye teslim etmek için yüksek kullanılabilirlik iletisi kuyruğu tarafından da işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="064da-289">Command's pipeline can also be handled by a high availability message queue to deliver the commands to the appropriate handler.</span></span> <span data-ttu-id="064da-290">Komutları kabul etmek için ileti kuyruklarını kullanmak, büyük olasılıkla ardışık hattı dış ileti kuyruğu üzerinden bağlı iki işlemolarak bölmeniz gerektiğinden, komutunuzun ardışık hattını daha da karmaşık hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="064da-290">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="064da-291">Yine de, asynchronous iletidayalı gelişmiş ölçeklenebilirlik ve performans olması gerekiyorsa kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-291">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="064da-292">Şekil 7-26 durumunda, denetleyicinin komut iletisini kuyruğa gönderdiğini ve döndürtuğugöz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="064da-292">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="064da-293">Daha sonra komut işleyicileri iletileri kendi hızlarında işler.</span><span class="sxs-lookup"><span data-stu-id="064da-293">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="064da-294">Bu, kuyrukların büyük bir yararıdır: Ileti sırası, yüksek hacimli giriş verisi olan hisse senetleri veya başka bir senaryo gibi hiper ölçeklenebilirliğin gerekli olduğu durumlarda arabellek görevi görebilir.</span><span class="sxs-lookup"><span data-stu-id="064da-294">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="064da-295">Ancak, ileti kuyruklarının eşzamanlı yapısı nedeniyle, komut işleminin başarısı veya başarısızlığı hakkında istemci uygulamasıyla nasıl iletişim kurabileceğinizi bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="064da-295">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="064da-296">Kural olarak, asla "ateş ve unut" komutlarını kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="064da-296">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="064da-297">Her iş başvurusu, bir komutun başarılı bir şekilde işlenilip işlenmeden veya en azından doğrulanıp kabul edilip edilip edilemeden bilinmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="064da-297">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="064da-298">Bu nedenle, eşzamanlı bir sıraya gönderilen bir komut iletisini doğruladıktan sonra istemciye yanıt verebilmek, işlemi çalıştırdıktan sonra işlemin sonucunu döndüren bir işlem içi komut işlemiyle karşılaştırıldığında sisteminize karmaşıklık katar.</span><span class="sxs-lookup"><span data-stu-id="064da-298">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="064da-299">Kuyrukları kullanarak, sisteminizde ek bileşenler ve özel iletişim gerektirecek diğer işlem sonuç iletileri aracılığıyla komut işleminin sonucunu döndürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="064da-299">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="064da-300">Ayrıca, async komutları tek yönlü komutları, birçok durumda gerekli olmayabilir, bir [online konuşma](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ)Burtsev Alexey ve Greg Young arasında aşağıdaki ilginç alışverişinde açıklandığı gibi:</span><span class="sxs-lookup"><span data-stu-id="064da-300">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="064da-301">\[Burtsev Alexey\] Ben insanların bunu yapmak için herhangi bir neden olmadan async komut işleme veya tek yönlü komut mesajlaşma kullanmak kod çok bulmak (onlar bazı uzun işlem yapmıyoruz, onlar harici async kodu yürütülmez, hatta mesaj veri yolu kullanarak uygulama sınırını geçmez).</span><span class="sxs-lookup"><span data-stu-id="064da-301">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="064da-302">Neden bu gereksiz karmaşıklığı ortaya atıyorlar?</span><span class="sxs-lookup"><span data-stu-id="064da-302">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="064da-303">Ve aslında, çoğu durumda sadece iyi çalışacak olsa, şimdiye kadar komut işleyicileri engelleme ile bir CQRS kodu örneği görmedim.</span><span class="sxs-lookup"><span data-stu-id="064da-303">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="064da-304">\[Greg\] \[Genç ... \] bir eşzamanlı komut yoktur; Aslında başka bir olay.</span><span class="sxs-lookup"><span data-stu-id="064da-304">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="064da-305">Eğer bana gönderdiğin şeyi kabul edip, aynı fikirde değilsem bir etkinlik büyütmem \[gerekiyorsa, artık bana bir\]şey yapmamı söylemiyorsun, bu bir emir değil.</span><span class="sxs-lookup"><span data-stu-id="064da-305">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it’s not a command\].</span></span> <span data-ttu-id="064da-306">Bana bir şey yapıldığını söylüyorsun.</span><span class="sxs-lookup"><span data-stu-id="064da-306">It's you telling me something has been done.</span></span> <span data-ttu-id="064da-307">Bu ilk başta hafif bir fark gibi görünüyor, ama birçok etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="064da-307">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="064da-308">Asynchronous komutları bir sistemin karmaşıklığını büyük ölçüde artırır, çünkü hataları göstermenin basit bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="064da-308">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="064da-309">Bu nedenle, asenkron komutlar ölçekleme gereksinimleri gerekli olduğunda veya özel durumlarda dahili mikro hizmetleri mesajlaşma yoluyla ileterken dışında önerilmez.</span><span class="sxs-lookup"><span data-stu-id="064da-309">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="064da-310">Bu gibi durumlarda, hatalar için ayrı bir raporlama ve kurtarma sistemi tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="064da-310">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="064da-311">eShopOnContainers ilk sürümünde, senkron komut işleme kullanmaya karar verdi, HTTP istekleri başladı ve Arabulucu desen tarafından tahrik.</span><span class="sxs-lookup"><span data-stu-id="064da-311">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="064da-312">Bu, [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) uygulamasında olduğu gibi işlemin başarısını veya başarısızlığını kolayca döndürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="064da-312">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="064da-313">Her durumda, bu uygulamanızın veya microservice'in iş gereksinimlerine dayalı bir karar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="064da-313">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="064da-314">Arabulucu desenli komut işlemi ardışık hattını uygulayın (MediatR)</span><span class="sxs-lookup"><span data-stu-id="064da-314">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="064da-315">Örnek bir uygulama olarak, bu kılavuz, komut yutma ve rota komutları sürücü için Arabulucu desen dayalı süreç içi ardışık kullanarak önerir, bellekte, sağ komut işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="064da-315">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="064da-316">Kılavuz ayrıca çapraz kesme kaygılarını ayırmak için [davranışların](https://github.com/jbogard/MediatR/wiki/Behaviors) uygulanmasını da önerir.</span><span class="sxs-lookup"><span data-stu-id="064da-316">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="064da-317">.NET Core'da uygulama için Arabulucu deseni uygulayan birden çok açık kaynak kitaplık vardır.</span><span class="sxs-lookup"><span data-stu-id="064da-317">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="064da-318">Bu kılavuzda kullanılan kitaplık [MediatR](https://github.com/jbogard/MediatR) açık kaynak kitaplığı (Jimmy Bogard tarafından oluşturulmuştur), ancak başka bir yaklaşım kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-318">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="064da-319">MediatR, dekoratörleri veya davranışları uygularken bellek içi iletileri komut gibi işlemenizi sağlayan küçük ve basit bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="064da-319">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="064da-320">Arabulucu deseni kullanmak, bağlantıyı azaltmanıza ve istenen çalışmanın endişelerini yalıtmanıza yardımcı olurken, bu durumda işi gerçekleştiren işleyiciye otomatik olarak bağlanarak işleyicileri komut komutlarına bağlar.</span><span class="sxs-lookup"><span data-stu-id="064da-320">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="064da-321">Arabulucu desen kullanmak için başka bir iyi nedeni Jimmy Bogard tarafından bu kılavuzu gözden geçirerek açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="064da-321">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="064da-322">Ben burada test söz değer olabileceğini düşünüyorum - sisteminizin davranışı içine güzel bir tutarlı pencere sağlar.</span><span class="sxs-lookup"><span data-stu-id="064da-322">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="064da-323">İstek, yanıt-out. Bu yönü sürekli davranan testler inşa oldukça değerli bulduk.</span><span class="sxs-lookup"><span data-stu-id="064da-323">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="064da-324">İlk olarak, aracı nesneyi gerçekten kullanacağınız örnek bir WebAPI denetleyicisine bakalım.</span><span class="sxs-lookup"><span data-stu-id="064da-324">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="064da-325">Arabulucu nesnesini kullanmıyorsanız, bu denetleyicinin tüm bağımlılıklarını, logger nesnesi gibi şeyleri ve diğer şeyleri enjekte etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="064da-325">If you weren't using the mediator object, you'd need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="064da-326">Bu nedenle, yapıcı oldukça karmaşık olacaktır.</span><span class="sxs-lookup"><span data-stu-id="064da-326">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="064da-327">Diğer taraftan, arabulucu nesnesini kullanırsanız, denetleyicinizin oluşturucusu, aşağıdaki örnekte olduğu gibi, kesme işlemi başına bir tane varsa, birçok bağımlılık yerine yalnızca birkaç bağımlılıkla çok daha basit olabilir:</span><span class="sxs-lookup"><span data-stu-id="064da-327">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    {
        // ...
    }
}
```

<span data-ttu-id="064da-328">Arabulucunun temiz ve yalın bir Web API denetleyici oluşturucusu sağladığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-328">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="064da-329">Buna ek olarak, denetleyici yöntemleri içinde, arabulucu nesnesine komut göndermek için kod neredeyse bir satırdır:</span><span class="sxs-lookup"><span data-stu-id="064da-329">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

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

### <a name="implement-idempotent-commands"></a><span data-ttu-id="064da-330">Idempotent Komutları Uygulama</span><span class="sxs-lookup"><span data-stu-id="064da-330">Implement idempotent Commands</span></span>

<span data-ttu-id="064da-331">**eShopOnContainers**, yukarıdaki daha gelişmiş bir örnek Sipariş microservice bir CreateOrderCommand nesne siniyor.</span><span class="sxs-lookup"><span data-stu-id="064da-331">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="064da-332">Ancak Sipariş iş süreci biraz daha karmaşık olduğundan ve bizim durumumuzda aslında Sepet microservice başlar, CreateOrderCommand nesne gönderme bu eylem bir önceki basit örnekte olduğu gibi istemci App çağrılan basit bir WebAPI denetleyicisi yerine [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) adlı bir entegrasyon olay işleyicisi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="064da-332">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="064da-333">Bununla birlikte, Komut'u MediatR'a gönderme eylemi aşağıdaki kodda gösterildiği gibi oldukça benzerdir.</span><span class="sxs-lookup"><span data-stu-id="064da-333">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

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

<span data-ttu-id="064da-334">Ancak, bu durum da biraz daha gelişmiş çünkü biz de idempotent komutları uyguluyoruz.</span><span class="sxs-lookup"><span data-stu-id="064da-334">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="064da-335">CreateOrderCommand işlemi idempotent olmalıdır, bu nedenle aynı ileti ağ üzerinden çoğaltılır gelirse, herhangi bir nedenle, yeniden denemeler gibi, aynı iş sırası sadece bir kez işlenir.</span><span class="sxs-lookup"><span data-stu-id="064da-335">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="064da-336">Bu, iş komutunu sarmalayarak (bu durumda CreateOrderCommand) ve idempotent olması gereken ağ üzerinden gelen her iletinin bir kimliği tarafından izlenen genel bir IdentifiedCommand içine katıştırma tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="064da-336">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="064da-337">Aşağıdaki kodda, Tanımlanan Komut'un dto ve id artı sarılmış iş komutu nesnesinden başka bir şey olmadığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-337">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

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

<span data-ttu-id="064da-338">Daha sonra [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) adlı Tanımlanan Komut için CommandHandler temelde iletinin bir parçası olarak gelen kimliğin bir tabloda zaten var olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="064da-338">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="064da-339">Zaten varsa, bu komut tekrar işlenmez, bu nedenle bir idempotent komut olarak görev eder.</span><span class="sxs-lookup"><span data-stu-id="064da-339">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="064da-340">Bu altyapı kodu aşağıdaki `_requestManager.ExistAsync` yöntem çağrısı ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="064da-340">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

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

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

<span data-ttu-id="064da-341">IdentifiedCommand bir iş komutu zarfı gibi davranır, çünkü tekrarlanan bir Id değil iş komutu işlenmesi gerektiğinde, o zaman bu iç iş komutu alır ve arabulucu ya yeniden `_mediator.Send(message.Command)`gönderir, çalışırken yukarıda gösterilen kodun son bölümünde olduğu gibi , [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="064da-341">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="064da-342">Bunu yaparken, aşağıdaki kodda gösterildiği gibi, sipariş veritabanına karşı işlemleri yürüten [CreateOrderCommandHandler,](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) bu durumda, iş komut işleyicisi bağlayacak ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="064da-342">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

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

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="064da-343">MediatR tarafından kullanılan türleri kaydetme</span><span class="sxs-lookup"><span data-stu-id="064da-343">Register the types used by MediatR</span></span>

<span data-ttu-id="064da-344">MediatR'ın komut işleyici sınıflarınızı bilmesi için, ioC kapsayıcınızda arabulucu sınıflarını ve komut işleyici sınıflarını kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="064da-344">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="064da-345">Varsayılan olarak, MediatR IoC kapsayıcı olarak Autofac kullanır, ancak yerleşik ASP.NET Core IoC kapsayıcı veya MediatR tarafından desteklenen başka bir kapsayıcı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-345">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="064da-346">Aşağıdaki kod, Autofac modüllerini kullanırken Arabulucu türlerinin ve komutlarının nasıl kaydedileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="064da-346">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

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

<span data-ttu-id="064da-347">MediatR ile "büyü nün gerçekleştiği yer burası".</span><span class="sxs-lookup"><span data-stu-id="064da-347">This is where “the magic happens” with MediatR.</span></span>

<span data-ttu-id="064da-348">Her komut işleyicisi `IAsyncRequestHandler<T>` genel arabirimi uyguladığından, derlemeleri kaydederken, kod aşağıdaki `IAsyncRequestHandler` örnekte `CommandHandlers` olduğu `Commands` `CommandHandler` gibi, sınıfta belirtilen ilişki sayesinde, kendi , ile ilgili olarak işaretlenmiş tüm türleri ile `RegisteredAssemblyTypes` kaydeder:</span><span class="sxs-lookup"><span data-stu-id="064da-348">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="064da-349">Bu komutları komut işleyicileri ile ilişkilendiren koddur.</span><span class="sxs-lookup"><span data-stu-id="064da-349">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="064da-350">İşleyici sadece basit bir sınıftır, ancak `RequestHandler<T>`T komut türü olduğu yerden devralır ve MediatR doğru yük (komut) ile çağrıldığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="064da-350">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="064da-351">MediatR'daki Davranışlar ile komutları işlerken çapraz kesme endişeleri uygulayın</span><span class="sxs-lookup"><span data-stu-id="064da-351">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="064da-352">Bir şey daha var: arabulucu boru hattına çapraz kesme kaygılarını uygulayabilmek.</span><span class="sxs-lookup"><span data-stu-id="064da-352">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="064da-353">Autofac kayıt modülü kodunun sonunda, özellikle özel bir LoggingBehavior sınıfı ve ValidatorBehavior sınıfını nasıl kaydettiğini de görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-353">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="064da-354">Ama başka özel davranışlar da ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-354">But you could add other custom behaviors, too.</span></span>

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

<span data-ttu-id="064da-355">[Bu LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı, komut işleyicisinin yürütüldüğü ve başarılı olup olmadığı yla ilgili bilgileri günlüğe kaydeden aşağıdaki kod olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="064da-355">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

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

<span data-ttu-id="064da-356">Yalnızca bu davranış sınıfını uygulayarak ve ardışık (yukarıdaki Arabulucu Modülü'nde) kaydederek, MediatR aracılığıyla işlenen tüm komutlar yürütme hakkında bilgi günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="064da-356">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="064da-357">mikrohizmet sipariş ibareleri, aşağıdaki kodda gösterildiği gibi, [Akıcı Geçersiz lik](https://github.com/JeremySkinner/FluentValidation) kitaplığına dayanan [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) sınıfı olan temel doğrulamalar için ikinci bir davranış da uygular:</span><span class="sxs-lookup"><span data-stu-id="064da-357">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

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

<span data-ttu-id="064da-358">Buradaki davranış, doğrulama başarısız olursa bir özel durum yükseltiyor, ancak başarılı olursa komut sonucunu veya başarısız olması durumunda doğrulama iletilerini içeren bir sonuç nesnesi de döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-358">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn’t.</span></span> <span data-ttu-id="064da-359">Bu, doğrulama sonuçlarını kullanıcıya görüntülemeyi büyük olasılıkla kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="064da-359">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="064da-360">Daha sonra, [FluentValidation](https://github.com/JeremySkinner/FluentValidation) kitaplığını temel aldığımızda, aşağıdaki kodda olduğu gibi CreateOrderCommand ile aktarılan veriler için doğrulama oluşturduk:</span><span class="sxs-lookup"><span data-stu-id="064da-360">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

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

<span data-ttu-id="064da-361">Ek doğrulamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-361">You could create additional validations.</span></span> <span data-ttu-id="064da-362">Bu komut doğrulamaları uygulamak için çok temiz ve zarif bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="064da-362">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="064da-363">Benzer bir şekilde, komutları işlerken uygulamak istediğiniz ek yönler veya çapraz kesme kaygıları için diğer davranışları uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="064da-363">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="064da-364">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="064da-364">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="064da-365">Arabulucu deseni</span><span class="sxs-lookup"><span data-stu-id="064da-365">The mediator pattern</span></span>

- <span data-ttu-id="064da-366">**Arabulucu deseni** </span><span class="sxs-lookup"><span data-stu-id="064da-366">**Mediator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="064da-367">Dekoratör deseni</span><span class="sxs-lookup"><span data-stu-id="064da-367">The decorator pattern</span></span>

- <span data-ttu-id="064da-368">**Dekoratör deseni** </span><span class="sxs-lookup"><span data-stu-id="064da-368">**Decorator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="064da-369">Arabulucu (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="064da-369">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="064da-370">**MediatR' ı.**</span><span class="sxs-lookup"><span data-stu-id="064da-370">**MediatR.**</span></span> <span data-ttu-id="064da-371">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="064da-371">GitHub repo.</span></span> \
  <https://github.com/jbogard/MediatR>

- <span data-ttu-id="064da-372">**MediatR ve AutoMapper ile CQRS** </span><span class="sxs-lookup"><span data-stu-id="064da-372">**CQRS with MediatR and AutoMapper** </span></span>\
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- <span data-ttu-id="064da-373">**Kontrolörlerinizi bir diyete koyun: POSTs ve komutlar.**</span><span class="sxs-lookup"><span data-stu-id="064da-373">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- <span data-ttu-id="064da-374">**Arabulucu boru hattı ile çapraz kesme sorunlarıyla mücadele** </span><span class="sxs-lookup"><span data-stu-id="064da-374">**Tackling cross-cutting concerns with a mediator pipeline** </span></span>\
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- <span data-ttu-id="064da-375">**CQRS ve REST: mükemmel maç** </span><span class="sxs-lookup"><span data-stu-id="064da-375">**CQRS and REST: the perfect match** </span></span>\
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- <span data-ttu-id="064da-376">**MediatR Boru Hattı Örnekleri** </span><span class="sxs-lookup"><span data-stu-id="064da-376">**MediatR Pipeline Examples** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- <span data-ttu-id="064da-377">**MediatR ve ASP.NET Çekirdek için Dikey Dilim Test Armatürleri** </span><span class="sxs-lookup"><span data-stu-id="064da-377">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- <span data-ttu-id="064da-378">**Microsoft Bağımlılık Enjeksiyonu Için MediatR Uzantıları Yayınlandı** </span><span class="sxs-lookup"><span data-stu-id="064da-378">**MediatR Extensions for Microsoft Dependency Injection Released** </span></span>\
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a><span data-ttu-id="064da-379">Akıcı doğrulama</span><span class="sxs-lookup"><span data-stu-id="064da-379">Fluent validation</span></span>

- <span data-ttu-id="064da-380">**Jeremy Skinner' ı. Akıcı Doğrulama.**</span><span class="sxs-lookup"><span data-stu-id="064da-380">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="064da-381">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="064da-381">GitHub repo.</span></span> \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> <span data-ttu-id="064da-382">[Önceki](microservice-application-layer-web-api-design.md)
> [Sonraki](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="064da-382">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
