---
title: Web API’si kullanarak mikro hizmet uygulama katmanını uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Bağımlılık ekleme ve Dünyası desenleri ve Web API'sini uygulama katmanı, uygulama ayrıntılarını anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: c8447cfcd3155a873d61ee9287f58774392c279d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640804"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Web API'si kullanarak mikro hizmet uygulama katmanı

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Altyapı nesnelerin uygulama katmanınızdaki eklemesine kullanım bağımlılık ekleme

Daha önce belirtildiği gibi uygulama katmanı oluşturduğunuz, örneğin bir Web API projesi veya bir MVC web uygulaması projesi gibi yapıtı (derleme) bir parçası olarak uygulanabilir. ASP.NET Core ile oluşturulmuş bir mikro hizmet söz konusu olduğunda, uygulama katmanı Web API kitaplığınızı genellikle olacaktır. ASP.NET Core (altyapısını artı denetleyicilerinizi) özel uygulama katman kodunuzdan beklenenler ayırmak istiyorsanız, uygulama katmanınızdaki ayrı sınıf kitaplığında yerleştirebilirsiniz, ancak bu isteğe bağlı.

Örneğin, sipariş mikro hizmet uygulama katmanı kodunu bir parçası olarak doğrudan uygulanır **Ordering.API** proje (bir ASP.NET Core Web API projesi) olarak gösterilen Şekil 7-23.

![Ordering.API mikro hizmet uygulama klasörü altında alt klasörleri gösteren Çözüm Gezgini görünümü: Davranışlar, komutları, DomainEventHandlers, IntegrationEvents, modelleri, sorguları ve doğrulama.](./media/image20.png)

**Şekil 7-23**. Uygulama katmanı Ordering.API ASP.NET Core Web API projesinde

ASP.NET Core içeren basit bir [yerleşik IOC kapsayıcı](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (IServiceProvider arabirimi tarafından temsil edilir), oluşturucu ekleme varsayılan olarak destekler ve ASP.NET belirli hizmetleri DI aracılığıyla kullanıma sunar. ASP.NET Core kullanan terimi *hizmet* DI eklenen kayıt türlerinden herhangi birini için. Yerleşik kapsayıcının hizmetler, uygulamanızın başlangıç sınıfındaki Createservicereplicalisteners() yöntemi yapılandırın. Bağımlılıklarınızı türü gerektiren ve IOC kapsayıcısında kaydeden Hizmetleri için uygulanır.

Genellikle, altyapı nesneler uygulama bağımlılıkları eklemesine istersiniz. Bir depo eklemek oldukça tipik bir bağımlılıktır. Ancak, bilgisayarınızda yüklü olmayabilir herhangi bir altyapı bağımlılığı ekleyebilir. DBContext altyapı Kalıcılık nesnelerinizi uygulanması da olduğundan daha basit uygulamalar için doğrudan iş birimi deseni nesnenizin (EF DbContext nesnesini) ekleyebilir.

Aşağıdaki örnekte, .NET Core Oluşturucu gerekli depo nesnelerde nasıl çalıştırıyorsunuzdur görebilirsiniz. Sonraki bölümde ele bir komut işleyici sınıftır.

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

Sınıfı, işlemi yürütmek ve durum değişiklikleri kalıcı hale getirmek için eklenen depoları kullanır. Bu sınıf, bir komut işleyici, bir ASP.NET Core Web API denetleyicisi yöntemi olup olmadığını veya önemli değildir [DDD uygulama hizmeti](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Sonuç olarak, bir komut işleyici için benzer bir biçimde depoları, etki alanı varlıklarının ve diğer uygulama koordinasyon kullanan basit bir sınıf durumdur. Belirtilen sınıfların tümü, DI kullanarak örnekte olduğu gibi aynı şekilde Oluşturucu tabanlı bağımlılık ekleme çalışır.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Bağımlılık uygulama türleri ve arabirimleri veya soyutlama kaydedin

Oluşturucular eklenen nesneleri kullanabilmeniz dı aracılığıyla uygulama sınıflarınızı içine eklenen nesneleri üreten sınıfları ve arabirimleri kaydetme yeri bilmeniz gerekir. (Dı gibi temel oluşturucu, daha önce gösterildiği gibi.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>ASP.NET Core tarafından sağlanan yerleşik IOC kapsayıcı kullanın

ASP.NET Core tarafından sağlanan yerleşik IOC kapsayıcı kullandığınızda Createservicereplicalisteners() yönteminde aşağıdaki kodu olduğu gibi Startup.cs dosyasındaki eklemesine türlerini kaydedin:

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

En yaygın desen bir IOC kapsayıcısında türlerini kaydetme türleri çifti kaydedilecek olduğunda — bir arabirim ve kendi ilgili uygulama sınıfı. Herhangi bir oluşturucu üzerinden IOC kapsayıcısından nesneyi istediğinde, belirli bir arabirim türünden bir nesne isteyin. Örneği için önceki örnekte, Oluşturucular, herhangi bir bağımlılık IMyCustomRepository (arabirimi veya soyutlama) sahip olduğunuzda, IOC kapsayıcı MyCustomSQLServerRepository uygulama örneğini ekleyecektir son satır durumları sınıf.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Otomatik türleri kayıt için Scrutor kitaplığını kullanma

DI'de .NET Core kullanırken, bir derlemeyi tarayın ve türlerinden kurala göre otomatik olarak kaydetmek isteyebilirsiniz. ASP.NET Core bu özellik şu anda kullanılamıyor. Ancak, kullanabileceğiniz [Scrutor](https://github.com/khellang/Scrutor) kitaplığı konusu. IOC kapsayıcınızı kaydedilmesi gereken türleri onlarca olduğunda bu yaklaşım uygundur.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Matthew King. Hizmetleri ile Scrutor kaydediliyor** \
  <https://www.mking.net/blog/registering-services-with-scrutor>

- **Kristian Hellang. Scrutor.** GitHub deposu. \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a>Bir IOC kapsayıcısı Autofac kullanın

Ayrıca ek IOC kapsayıcılar kullanma ve ASP.NET Core ardışık düzen, sıralama mikro hizmet kullanan hizmetine olduğu gibi takın [Autofac](https://autofac.org/). Autofac kullanırken aracılığıyla kayıt türleri, birden çok sınıf kitaplıkları dağıtılmış uygulama türleri olabilir gibi türlerinizi nerede olduğunuza bağlı olarak birden çok dosya arasında bölmek olanak tanıyan modüller, türler genellikle kaydedin.

Örneğin, aşağıdaki gibidir [Autofac uygulama modülü](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) için [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) proje türleriyle eklemek istediğiniz.

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

Autofac ayrıca bir özelliğe sahip [tarama derlemeleri ve türlerini adı kuralları kaydetmeye](https://autofac.readthedocs.io/en/latest/register/scanning.html).

Kavramlar ve kayıt işlemine çok benzer şekilde türleri ile yerleşik ASP.NET Core IOC kapsayıcı kaydedebilirsiniz, ancak Autofac kullanırken söz dizimi biraz farklıdır.

Örnek kodda IOrderRepository soyutlama uygulama sınıfımızın OrderRepository birlikte kaydedilir. Başka bir deyişle, bir oluşturucu, bir bağımlılık IOrderRepository soyutlama veya arabirimi aracılığıyla bildirme her IOC kapsayıcı OrderRepository sınıfının bir örneğini ekleyecektir.

Örnek kapsamı türü örneği aynı hizmet veya bağımlılık istekleri arasında nasıl paylaşılacağını belirler. Bir bağımlılık için bir istek yapıldığında, IOC kapsayıcı aşağıdaki döndürebilirsiniz:

- Ömrü kapsam başına tek bir örnek (ASP.NET Core IOC kapsayıcısı olarak anılacaktır *kapsamlı*).

- Bağımlılık başına yeni bir örnek (ASP.NET Core IOC kapsayıcısı olarak anılacaktır *geçici*).

- IOC kapsayıcıyı kullanan tüm nesneleri arasında paylaşılan tek bir örnek (ASP.NET Core IOC kapsayıcısı olarak anılacaktır *singleton*).

#### <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET core'da bağımlılık ekleme giriş** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** Resmi belgeleri. \
  <https://docs.autofac.org/en/latest/>

- **ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamlı - Cesar de la Torre karşılaştırma.** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a>Komut ve komut işleyicisi desenlerini uygulama

Oluşturucusu aracılığıyla DI örnekte, önceki bölümde gösterilenle IOC kapsayıcı bir sınıftaki bir oluşturucu üzerinden depoları ekleme oluştu. Ancak, tam olarak nerede bunlar eklenmiş? Bir basit Web API'SİNDE (örneğin, katalog mikro hizmetine), bunları MVC denetleyicileri düzeyinde, ASP.NET Core istek ardışık düzenini bir parçası olarak bir denetleyici oluşturucu ekleyin. Ancak, bu bölümün ilk kod içinde ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) hizmetine Ordering.API hizmetinden sınıfı), bağımlılık ekleme belirli bir komut Oluşturucu gerçekleştirilir işleyici. Bize açıklayan bir komut işleyici ve neden kullanmak istiyorsunuz.

Komut desen, doğası gereği, bu kılavuzun önceki bölümlerinde sunulan CQRS modelinin ilgilidir. CQRS iki kenara sahiptir. Basitleştirilmiş sorguları kullanarak sorguları, ilk alanıdır [Dapper](https://github.com/StackExchange/dapper-dot-net) daha önce açıklanan mikro ORM. İşlemler için başlangıç noktası ve giriş kanaldan hizmetin dışında olan komutları ikinci bir alandır.

Şekil 7-24'te gösterildiği gibi deseni istemci tarafında, komutları kabul üzerinde alan etki alanı modeli kurallara göre işlenmesi ve son olarak işlem durumlarıyla kalıcı.

![CQRS, yazma tarafı üst düzey Görünüm: Kullanıcı Arabirimi uygulama için etki alanı modeli ve veritabanını güncellemek için altyapı bağlıdır CommandHandler, alır API'sinden bir komut gönderir.](./media/image21.png)

**Şekil 7-24**. Üst düzey görünümünü komutları veya "işlem tarafta" bir CQRS düzeni

### <a name="the-command-class"></a>Komut sınıfı

Bir istek sistemin sistem durumunu değiştiren bir eylem gerçekleştirmek bir komuttur. Komutlar, kesinlik temelli ve hemen bir kerelik işlenmesi.

Komutları imperatives olduğundan, bunlar genellikle bir fiil kesinlik temelli ruh (örneğin, "oluşturma" veya "güncelleştir") ile adlandırılır ve CreateOrderCommand gibi toplama türünü içeriyor olabilir. Bir olay, bir komut Geçmişten bir olgu değil; yalnızca bir istek ve bu nedenle reddetti.

İşlem Yöneticisi, bir eylemi gerçekleştirmek için bir toplama yönlendiren olduğunda komutları sonucunda bir isteği bir kullanıcı arabiriminden veya bir işlem yöneticisi tarafından gönderilebilir.

Bir önemli bir komutu tek bir alıcı tarafından yalnızca bir kez işlenmesi gerektiğini özelliğidir. Bir komutun tek bir eylem veya uygulamada gerçekleştirmek istediğiniz işlem olmasıdır. Örneğin, aynı sipariş oluşturma komutu kereden fazla işlenmemesi. Komutlar ve olayları arasındaki önemli bir fark budur. Olayda birçok sistemleri veya mikro hizmetler ilgilenebilecek çünkü birden çok kez işlenen olaylar.

Ayrıca, komut etkili değilse, komut yalnızca bir kez işlenmesi önemlidir. Birden çok kez sonucu komutu niteliği nedeniyle veya sistem komut işleme biçimi nedeniyle değiştirmeden yürütülmek üzere ise bir komut etkili olur.

Komutlarınızın yapmak iyi bir uygulamadır ve etki alanının iş kurallarını ve okuduğunuzda altında mantıklıdır ıdempotent güncelleştirir. Örneğin, herhangi bir nedenle (yeniden deneme mantığı, yazılım korsanlığı, vb.) sisteminizi birden çok kez aynı CreateOrder komutu ulaşırsa aynı örneği kullanmak için tanımlamak ve birden çok sipariş oluşturmamanızı sağlar olması gerekir. Bunu yapmak için bir tür işlemlerinde kimlik eklemek ve komut veya güncelleştirme işlenmiş olup olmadığını belirlemek gerekir.

Tek alıcı için komut gönderebilirsiniz; bir komut yayımlamayın. Yayımlama olduğu bir olgu durum olayları için — bir sorun oluştu ve olabilir Olay alıcıları için ilginç. Olaylar söz konusu olduğunda, yayımcı hangi olay veya bunu ne alıcılar almak hiçbir sorunları vardır. Ancak etki alanı ya da tümleştirme olayları zaten önceki bölümlerinde sunulan farklı bir öykü.

Veri alanlarını veya koleksiyonları bu komutu yürütmek için gerekli tüm bilgileri içeren bir sınıf ile birlikte bir komut uygulanır. Özel bir tür, veri aktarım nesnesini (DTO), özellikle değişiklikleri veya işlemleri istemek için kullanılan bir komuttur. Komut, tam komut ve hiçbir şey daha fazla işlemek için gerekli bilgileri temel alır.

Aşağıdaki örnek, Basitleştirilmiş CreateOrderCommand sınıfı gösterir. Bu sıralama mikro hizmetine kullanılan değişmez bir komuttur.

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

Temel olarak, komut sınıfı, etki alanı model nesneleri kullanarak, bir iş işlemi gerçekleştirmek için gereken tüm verileri içerir. Bu nedenle, yalnızca salt okunur veri ve davranışı yok içeren veri yapılarını komutlardır. Amacı, komutun adını belirtir. Gibi birçok dilde C#komutları sınıf olarak temsil edilir ancak doğru nesne yönelimli gerçek anlamda sınıflarda değildir.

Beklenen kullanım, doğrudan etki alanı modeli tarafından işlenen olduğu için ek bir özellik komutları, sabittir. Öngörülen kendi ömrü boyunca değişiklik gerekmez. İçinde bir C# sınıfı, tüm ayarlayıcılar ya da iç durum değişikliği diğer yöntemleri zorunluluğunu ortadan kaldırarak değiştirilemezlik gerçekleştirilebilir.

Amaçladığınız ya da beklediğiniz komutları bir seri hale getirme deserializing sürecinden geçmeden, özelliklerini özel ayarlayıcı olmalıdır unutmayın ve `[DataMember]` (veya `[JsonProperty]`) özniteliği, aksi takdirde seri durumdan çıkarıcı için mümkün olmayacak gerekli değerlerle hedef nesne yeniden yapılandırma.

Örneğin, bir sipariş oluşturmak için komut sınıfı oluşturmak istediğiniz siparişin veri açısından büyük olasılıkla benzer, ancak büyük olasılıkla aynı öznitelikleri gerekmez. Örneğin, sipariş henüz oluşturulmamış çünkü CreateOrderCommand bir sipariş kimliği yok.

Birçok komut sınıfları yalnızca birkaç alan değiştirilmesi gereken bazı durumu hakkında gerektirme, basit olabilir. Bu durum yalnızca "işlem" bir sıra durumunu değiştiriyorsanız "Ücretli" veya "aşağıdakine benzer bir komut kullanarak sevk" olacaktır:

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

Bazı geliştiriciler kendi UI istek nesneleri kendi komut Dto'lar ayrı hale getirir, ancak adımlarından tercih olmasıdır. Can sıkıcı bir ayrım ölçüde eklenen değerine sahip olan ve hemen hemen aynı şekilde nesneleridir. Örneğin, hizmetine bazı komutlar doğrudan istemci tarafında gelir.

### <a name="the-command-handler-class"></a>Komut işleyici sınıfı

Her komut için belirli bir komut işleyici sınıfı uygulamalıdır. Düzeni nasıl çalışır, ve burada komut nesnesi, etki alanı nesnelerini ve altyapı depo nesneleri kullanır. Komut işleyici aslında CQRS ve DDD açısından uygulama katmanı kalbidir. Ancak tüm etki alanı mantığı alan sınıfları içinde yer almalıdır; toplama kökleri (kök varlıklar) içinde alt varlıklar veya [etki alanı Hizmetleri](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ancak değildir komut işleyicisinin içerisinde olduğu uygulama öğesinden bir sınıf Katman.

Komut işleyici sınıfı, bir önceki bölümde belirtilen tek sorumluluk İlkesi (SRP) yapmanın bir yolu, güçlü bir atlama taşı sunar.

Bir komut işleyici, bir komut alır ve bir sonuç kullanılan toplam alır. Sonuç başarılı yürütme komut veya özel bir durum olmalıdır. Bir özel durum söz konusu olduğunda sistem durumu değiştirilmeden olmalıdır.

Komut işleyici, genellikle aşağıdaki adımları gerçekleştirir:

- Komut nesnesi gibi bir DTO alır (gelen [Dünyası](https://en.wikipedia.org/wiki/Mediator_pattern) veya diğer altyapı nesne).

- Bu komut (Dünyası tarafından doğrulanmamış varsa) geçerli olduğunu doğrular.

- Bu, geçerli komut hedefi olan toplama kök örneği başlatır.

- Toplama kök örneğinde komuttan gerekli verileri alma yöntemini yürütür.

- Bu, yeni durum toplama için ilgili veritabanını devam ettirir. Bu son işlem gerçek bir işlemdir.

Genellikle, bir komut işleyici toplama, kök (kök varlık) tarafından yönetilen tek bir toplamada ile ilgilidir. Birden çok toplamalar alımını tek bir komut tarafından etkilenir, durumları veya eylemler arasında birden çok toplamalar yaymak için etki alanı olayları kullanabilirsiniz.

Burada önemli olan nokta bir komutu işlenirken, tüm etki alanı mantığı içinde etki alanı modeli (toplama), tamamen yalıtılmış ve birim testi için hazır olması gerekliliğidir. Komut işleyici yalnızca etki alanı modeli veritabanından almanın bir yolunu ve model değiştirildiğinde, değişiklikleri kalıcı hale getirmek için altyapı katmanını (depo) bildirmek için son adım olarak görev yapar. Bu yaklaşımın avantajı uygulama veya tesisat düzeyi (komut işleyicileri, Web API'si, altyapı katmanlarının, kodda değişiklik yapmadan etki alanı mantığı bir yalıtılmış, tam olarak kapsüllenmiş, zengin, davranışsal bir etki alanı modeli içinde yeniden düzenleyebilirsiniz olduğu depoları, vb.).

Komut işleyicileri çok fazla mantık ile karmaşık aldığınızda, bir kod kokusu olabilir. Bunları gözden geçirin ve etki alanı mantığı bulursanız, o etki alanı davranışını (toplama kök ve alt varlık) etki alanı nesnelerin yöntemlere taşımak için kodu yeniden düzenleyin.

Bir komut işleyici sınıfı, örnek olarak, aşağıdaki kod, bu bölümün başında gördüğünüz aynı CreateOrderCommandHandler sınıfı gösterir. Bu durumda, Handle yöntemini ve etki alanı model nesneleri/toplama işlemleri vurgulamak istiyoruz.

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

Bir komut işleyici gerçekleştirmeniz ek adımlar şunlardır:

- Toplama kökünün yöntemleri ve davranışı ile çalışması için komutun verileri kullanın.

- Dahili olarak etki alanı nesnelerinde hareket yürütülür, ancak bir komut işleyici açısından saydam etki alanı olayları tetikleyebilir.

- İşlem sonucu toplama'nın başarılı olursa ve işlem tamamlandıktan sonra tümleştirme olayları tetikleyebilir. (Bunlar da depoları gibi altyapı sınıflar tarafından oluşturulması.)

#### <a name="additional-resources"></a>Ek kaynaklar

- **İşareti Seemann. Sınırlarında değil nesne yönelimli uygulamalar** \
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- **Komutlar ve olayları** \
  <http://cqrs.nu/Faq/commands-and-events>

- **Bir komut işleyici ne yapar?** \
  <http://cqrs.nu/Faq/command-handlers>

- **Jimmy Bogard. Etki alanı komutu desenleri – işleyicileri** \
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- **Jimmy Bogard. Etki alanı komutu desenleri – doğrulama** \
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Komut işlemi işlem hattı: bir komut işleyici tetikleme

Sonraki soruya komut işleyicisi çağırma şeklidir. El ile ilgili her ASP.NET Core denetleyicisinden çağırabilirsiniz. Ancak, yaklaşım çok İmparatoru eşleşmiş ve ideal değildir.

Önerilen seçenek olan diğer iki ana seçenekleri şunlardır:

- Bir bellek içi Dünyası deseni yapıt.

- Zaman uyumsuz ileti kuyruğunu ile denetleyicileri ile işleyicileri aralığındaki.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Komut işlem hattında Dünyası düzeni (bellek içi) kullanın

Şekil 7-25 gösterildiği gibi bir CQRS yaklaşım, komutun veya alınan DTO türüne göre doğru komut işleyici yeniden yönlendirmek akıllı bir bellek içi bus benzer akıllı bir Dünyası kullanın. Bileşenler arasındaki tek siyah okları kendi ilgili etkileşim (dı ile eklenen çoğu durumda,) nesneler arasındaki bağımlılıkları temsil eder.

![Önceki görüntüde bulunan yakınlaştırma: bunlar için uygun tanıtıcının alabilmeniz ASP.NET Core denetleyici komut MediatR'ın komut işlem hattına gönderir.](./media/image22.png)

**Şekil 7-25**. Tek bir CQRS mikro hizmet işleminde Dünyası desenini kullanarak

Kurumsal uygulamalar, istekleri işlemek için karmaşık alabilirsiniz, Dünyası desenini kullanarak, anlamlı nedeni olmasıdır. Açık bir günlük kaydı, doğrulama, Denetim ve güvenlik gibi çapraz kesme konuları sayısı eklemek yönetebilmek istiyorsunuz. Bu durumlarda, bir Dünyası işlem hattını güvenebilirsiniz (bkz [Dünyası deseni](https://en.wikipedia.org/wiki/Mediator_pattern)) bu ek davranışları veya çapraz kesme konuları için bir yol sağlamak.

Bir Dünyası "nasıl" Bu işlemin sarmalayan bir nesnedir: yürütme durumuna göre düzenler, bir komut işleyici şekilde çağrılır veya yükü işleyicisine sağlayın. Dünyası bileşeniyle geniş kapsamlı kritik konular merkezi ve saydam bir şekilde dekoratörler uygulayarak uygulayabilirsiniz (veya [işlem hattı davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) beri [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)). Daha fazla bilgi için [Dekoratör deseni](https://en.wikipedia.org/wiki/Decorator_pattern).

Dekoratörler ve davranışları için benzer [en boy yönelimli programlama (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)yalnızca Dünyası bileşeni tarafından yönetilen bir özel işlem ardışık düzeni uygulanır. Geniş kapsamlı kritik konular uygulayan AOP yönlerine göre uygulanır *en boy weavers* nesne çağrısı yakalanması temelinde ya da derleme zamanında eklenmiş. AOP çalışmasını nasıl yaptığını görmek kolay olmadığı için her iki tipik AOP yaklaşım bazen "Sihirli gibi" çalışmaya söylenir. Ciddi sorunlar veya hatalar ile ilgilenirken, AOP hata ayıklaması zor olabilir. Diğer taraftan, çok daha öngörülebilir ve kolayca hata ayıklama, bu nedenle bu dekoratörler/davranışlar açık ve yalnızca Dünyası bağlamında uygulanır.

Örneğin, mikro hizmet sıralama hizmetine içinde iki örnek davranışları uyguladık bir [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı ve [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) sınıfı. Hizmetine nasıl kullandığını gösteren davranışları uygulamasını sonraki bölümde açıklanmıştır [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors).

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Kullanım iletisini (giden işlem dışı), komutun ardışık düzende sıralar

Başka bir seçimi aracılarını veya ileti kuyrukları, Şekil 7-26 gösterildiği göre zaman uyumsuz iletiler kullanmaktır. Bu seçenek ayrıca komut işleyici hemen önce Dünyası bileşeni ile birleştirilir.

![Komutun işlem hattı, ayrıca komutlar için uygun tanıtıcının sunmak için yüksek kullanılabilirlik ileti kuyruğu tarafından işlenebilir.](./media/image23.png)

**Şekil 7-26**. CQRS komutlarıyla (dışında işlem ve işlemler arası iletişimi) ileti kuyrukları kullanma

İşlem hattı iki süreçlerine bölme gerekecektir ileti kuyrukları komutları daha da aşağı çekebilirsiniz kabul etmek için komutun işlem hattı, karmaşık kullanarak dış ileti kuyruğu üzerinden bağlı. Yine de, ölçeklenebilirlik ve zaman uyumsuz Mesajlaşma temel performans geliştirildi ihtiyacınız varsa kullanılmalıdır. Şekil 7-26 söz konusu olduğunda göz önünde bulundurun, denetleyici yalnızca komut ileti kuyruğuna gönderir ve döndürür. Daha sonra komut işleyicileri kendi hızlarında iletileri işler. Yani harika bir yararı kuyruklar: hiper ölçeklenebilirlik gerekli, stocks veya herhangi bir giriş veri hacmi yüksek senaryosuyla gibi olduğunda ileti kuyruğu durumlarda bir arabellek olarak görev yapabilir.

Ancak, zaman uyumsuz ileti kuyrukları yapısı nedeniyle, başarı veya başarısızlık komut işleminin hakkında istemci uygulamasıyla iletişim kurmak nasıl ekleyeceğimi gerekir. Bir kural olarak, hiçbir zaman "Başlat ve unut" komutları kullanmanız gerekir. Her iş uygulaması, bir komut başarıyla, işlenen veya en az doğrulandı ve kabul durumunda bilmesi gerekir.

Bu nedenle, bir zaman uyumsuz kuyruğa gönderildiği bir komut iletisi doğruladıktan sonra istemci taleplerine yanıt işaretleyebilmesine karmaşıklık işlem çalıştırdıktan sonra işlemin sonucunu döndürür. bir işlemdeki komutu işlemi karşılaştırıldığında sisteminize ekler. Kuyrukları kullanma, ek bileşenleri ve özel iletişim sisteminizde gerektirecek diğer işlem sonucu iletileri komut sürecinde sonuç gerekebilir.

Ayrıca, zaman uyumsuz, çoğu durumda, aşağıdaki ilginç exchange Burtsev Alexey arasındaki Greg Young'içinde açıklandığı şekilde gerekebilecek değil, tek yönlü komutlar komutlardır bir [çevrimiçi konuşma](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

> \[Burtsev Alexey\] kişiler, zaman uyumsuz komut işleme veya tek yönlü komut Bunu yapmak için herhangi bir nedenle olmadan Mesajlaşma burada kullanır kodu çok sayıda bulabilirim (uzun bir işlemin yapılması değil, bunlar dış zaman uyumsuz kod yürütülmüyor, bile uygulama geçmez ileti veri yoluna bitvise sınırı). Neden bu gereksiz karmaşıklık tanıtmak? Ve aslında, sorgunuz çoğu durumda çalışır ancak ben komut işleyicileri şu ana kadar engelleme ile bir CQRS kod örneği göremedik.
>
> \[Greg Young\] \[... \] zaman uyumsuz bir komutu yok; aslında başka bir olaydır. Gereken ne bana gönderdiğiniz kabul ediyorum ve etmiyorum ise bir olay tetikleyebilir, artık, bana bir şeyler belirten değildir \[diğer bir deyişle, bir komut değil\]. Bana bir şey bitti belirten olduğunu. Bu küçük bir fark ilk gibi görünüyor, ancak birçok etkileri vardır.

Hataları göstermek için basit bir yolu yoktur çünkü zaman uyumsuz komutları bir sistem karmaşıklığını büyük ölçüde artırabilir. Bu nedenle, zaman uyumsuz komutları dışında ölçeklendirme gereksinimlerini gerektiğinde veya özel durumlarda Mesajlaşma aracılığıyla iç mikro hizmetler kurarken önerilmez. Bu gibi durumlarda, hatalar için ayrı bir raporlama ve kurtarma sistemi tasarlamanız gerekir.

Hizmetine ilk sürümünde, zaman uyumlu bir komut işleme, HTTP isteklerinden kullanmaya ve odaklı Dünyası deseni tarafından kullanılacak verdik. Kolayca sağlayan başarısı veya başarısızlığı işlemin olarak döndürülecek [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) uygulaması.

Herhangi bir durumda, bu uygulamanın veya mikro hizmet'ın iş gereksinimlerine göre bir karar olmalıdır.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Dünyası desen (MediatR) komut işlem hattıyla uygulayın

Örnek uygulama, bu kılavuz, sürücü komut alımı ve bellekte doğru komut işleyicileri için rota komutları Dünyası düzene göre işlem içi işlem hattını kullanarak önerir. Kılavuz, ayrıca uygulama önerir [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) geniş kapsamlı kritik konular ayırmak için.

.NET Core için uygulama, Dünyası desen uygulayan birden fazla açık kaynak kitaplıkları kullanılabilir vardır. Bu kılavuzda kullanılan kitaplık [MediatR](https://github.com/jbogard/MediatR) açık kaynak kitaplığı (Jimmy Bogard tarafından oluşturulan), ancak başka bir yaklaşım kullanabilir. MediatR dekoratörler veya davranışlardan uygulanırken bir komutu gibi bellek içi iletiler işlemenize imkan tanıyan küçük ve basit bir kitaplıktır.

Dünyası desenini kullanarak, yardımcı bağlantısından azaltmak ve bu işi gerçekleştiren işleyicinin otomatik olarak bağlanma sırasında istenen iş sorunları yalıtmak için — bu durumda, için komut işleyicileri.

Dünyası desen kullanmak için başka bir nedeni Jimmy Bogard tarafından bu kılavuzu gözden geçirdikleri sırada açıklamaları:

> Sanırım burada test söz olabilir – sisteminizi davranışını iyi tutarlı bir pencere sağlar. İstek, yanıt genişletme. Biz bu yönü testleri tutarlı bir şekilde davrandığından binada oldukça değerli buldunuz.

İlk olarak örnek Webapı denetleyicisi Dünyası nesne aslında burada kullanacağınız bakalım. Dünyası nesne kullanmadıysanız, tüm bağımlılıkları söz konusu denetleyici için bir Günlükçü nesnesi ve diğerleri gibi eklemesine gerekir. Bu nedenle, oluşturucu oldukça karmaşık olabilir. Öte yandan, oluşturucu denetleyicinizin Dünyası nesnesi kullanıyorsanız, aşağıdaki örnekte olduğu gibi çapraz kesme işlemi başına bir tablonuz varsa birçok bağımlılıkları yerine yalnızca birkaç bağımlılıkları olan çok basit olabilir:

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

Dünyası temizleme ve akıllı bir Web API denetleyicisi Oluşturucusu sağladığını görebilirsiniz. Ayrıca, denetleyici yöntemlerinde Dünyası nesne için bir komut göndermek için kod neredeyse bir satırı verilmiştir:

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

### <a name="implement-idempotent-commands"></a>Uygulama kere etkili olacak komutlar

İçinde **hizmetine**, yukarıdaki değerinden daha gelişmiş bir örnek, sıralama mikro hizmet CreateOrderCommand nesneden gönderiliyor. Ancak sıralama iş süreci biraz daha karmaşıktır ve bu örnekte, aslında sepet mikro başladıktan sonra bu eylem CreateOrderCommand nesne gönderme adlı bir tümleştirme olay işleyicisinden gerçekleştirilir > UserCheckoutAcceptedIntegrationEvent.cs] (https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) yerine basit Webapı denetleyicisi adlı basit bir önceki örnekte olduğu gibi uygulama istemciden.

Bununla birlikte, gönderme MediatR komutu aşağıdaki kodda gösterildiği gibi oldukça benzer eylemdir.

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

Ancak, bu da durumda biz de kere etkili olacak komutlar uygulama için biraz daha fazla Gelişmiş. CreateOrderCommand işlemini bir kez etkili, olmalıdır şekilde aynı ileti yeniden deneme gibi herhangi bir nedenle nedeniyle ağ üzerinden yinelenen geliyorsa, yalnızca bir kez aynı iş sırada işlenir.

Bu işlem, bir kez etkili olması için olan ağ üzerinden gelen her ileti kimliği tarafından izlenen bir genel IdentifiedCommand içine ekleme ve iş komut (Bu durumda CreateOrderCommand) sarmalama tarafından uygulanır.

Aşağıdaki kod IdentifiedCommand ile bir DTO kimliği ve yanı sıra Sarmalanan iş komut nesnesi başka bir şey olduğunu görebilirsiniz.

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

Ardından adlı IdentifiedCommand için CommandHandler [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) temel iletisinin bir parçası zaten gelen kimliği bir tablodaki olup olmadığını kontrol eder. Bu nedenle, komutu yeniden işlenmez varsa, bir kez etkili komut olarak davranır. Altyapı kodu tarafından gerçekleştirilen `_requestManager.ExistAsync` aşağıdaki yöntem çağrısı.

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

Yinelenen kimliği olmadığından işlenecek iş komutu gerektiğinde IdentifiedCommand iş komutun Zarf gibi davranır, iç iş komutu alır ve bunu ne zaman gösterilen kod son parçası olduğu gibi Dünyası için yeniden gönderir çalışan `_mediator.Send(message.Command)`, gelen [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).

Bunu yaparken, bu bağlantı ve iş komut işleyici bu durumda çalıştırın, [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) çalıştığı işlem sıralama veritabanında aşağıdaki kodda gösterildiği gibi.

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

### <a name="register-the-types-used-by-mediatr"></a>MediatR tarafından kullanılan türleri kaydetme

Komut işleyici sınıflarınızı dikkat etmeniz MediatR IOC kapsayıcınızı Dünyası sınıfları ve komut işleyici sınıflarını kaydettirmek gerekir. Varsayılan olarak, MediatR Autofac IOC kapsayıcı olarak kullanılır, ancak yerleşik ASP.NET Core IOC kapsayıcı ya da MediatR tarafından desteklenen herhangi bir kapsayıcı da kullanabilirsiniz.

Aşağıdaki kod, Dünyası'nın türleri ve komutlar Autofac modülleri kullanırken kaydettirmek gösterilmektedir.

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

Burada "ile MediatR sihrin".

Her komut işleyici genel uyguladığından `IAsyncRequestHandler<T>` arabirimi, derlemeleri, kaydolurken kodunu kaydeder ile `RegisteredAssemblyTypes` tüm türleri olarak işaretlenmiş `IAsyncRequestHandler` ilgili çalışırken `CommandHandlers` ile kendi `Commands`, teşekkür ederiz konumunda belirtilen ilişkiye `CommandHandler` aşağıdaki örnekteki gibi bir sınıfı:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Komutları komut işleyicileri karşılık gelen kod olmasıdır. Basit bir sınıf işleyici olduğu halde devraldığı `RequestHandler<T>`, burada T komut türü ve MediatR doğru Yükü (komut) çağrıldığında emin yapar.

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>Geniş kapsamlı kritik konular MediatR davranışları komutlarıyla işlerken Uygula

Bir şey daha vardır: geniş kapsamlı kritik konular Dünyası işlem hattına uygulamak için. Ayrıca, nasıl bunu bir davranış türü özel olarak kaydeder, özel bir LoggingBehavior sınıf ve ValidatorBehavior sınıfı Autofac kayıt modülü kodu sonunda görebilirsiniz. Ancak özel davranışları çok ekleyebilirsiniz.

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

Olduğunu [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı ve yürütülen komut işleyici değil başarılı olup hakkındaki bilgileri kaydeder aşağıdaki kodu olarak uygulanabilir.

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

Bu davranış sınıfı uygulama tarafından ve işlem hattı (yukarıdaki MediatorModule) içinde kaydederek MediatR işlenen tüm komutları yürütme hakkında bilgi günlüğe kaydetme.

Mikro hizmet, ikinci bir davranış temel doğrulamaları için de geçerlidir sıralama hizmetine [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) dayanan sınıfı [FluentValidation](https://github.com/JeremySkinner/FluentValidation) gösterildiği kitaplığı Aşağıdaki kodu:

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

Doğrulama başarısız olursa, bir özel durum davranışını buraya oluşturur, ancak sonuç nesnesi da döndürebilir, işe yaramadı durumunda başarılı komutu sonucu içeren veya doğrulama iletileri. Bu büyük olasılıkla doğrulama sonuçları kullanıcıya görüntülenecek kolaylaştırır.

Ardından, temel [FluentValidation](https://github.com/JeremySkinner/FluentValidation) kitaplığı, oluşturduğumuz CreateOrderCommand ile olduğu gibi aşağıdaki kodu geçirilen veriler için doğrulama:

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

Ek doğrulama oluşturabilirsiniz. Komut doğrulamaları uygulamak için çok temiz ve şık bir yolu budur.

Benzer şekilde, ek unsurları veya bunları işlerken komutları uygulamak istediğiniz çapraz kesme konuları için diğer davranışları uygulayabilirsiniz.

#### <a name="additional-resources"></a>Ek kaynaklar

##### <a name="the-mediator-pattern"></a>Dünyası deseni

- **Dünyası deseni** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Dekoratör düzeni

- **Dekoratör düzeni** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

- **MediatR.** GitHub deposu. \
  <https://github.com/jbogard/MediatR>

- **CQRS MediatR ve AutoMapper** \
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- **Denetleyicilerinizi Diyet uyguluyoruz yerleştirin: Gönderileri ve komutları.** \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- **Bir işlem hattıyla Dünyası kuruluşlarda geniş kapsamlı kritik konular** \
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- **CQRS ve REST: mükemmel** \
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- **MediatR ardışık örnekler** \
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- **Dikey dilim Test armatürleri MediatR ve ASP.NET Core** \
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- **MediatR uzantıları için yayımlanan Microsoft bağımlılık ekleme** \
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a>Fluent doğrulama

- **Jeremy Skinner. FluentValidation.** GitHub deposu. \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> [Önceki](microservice-application-layer-web-api-design.md)
> [İleri](../implement-resilient-applications/index.md)
