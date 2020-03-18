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
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Web API'sini kullanarak mikro hizmet uygulama katmanını uygulayın

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Uygulama katmanınıza altyapı nesneleri enjekte etmek için Bağımlılık Enjeksiyonu'yu kullanma

Daha önce de belirtildiği gibi, uygulama katmanı, bir Web API projesi veya Bir MVC web uygulaması projesi gibi, oluşturmakta olduğunuz yapının (derlemenin) bir parçası olarak uygulanabilir. ASP.NET Core ile oluşturulmuş bir microservice durumunda, uygulama katmanı genellikle Web API kitaplığınız olacaktır. ASP.NET Core'dan (altyapısı ve denetleyicileriniz) gelenleri özel uygulama katmanı kodunuzdan ayırmak istiyorsanız, uygulama katmanınızı ayrı bir sınıf kitaplığına da yerleştirebilirsiniz, ancak bu isteğe bağlıdır.

Örneğin, sipariş mikrohizmetinin uygulama katmanı kodu, Şekil 7-23'te gösterildiği gibi **Ordering.API** projesinin (ASP.NET Core Web API projesi) bir parçası olarak doğrudan uygulanır.

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Çözüm Gezgini'ndeki Ordering.API microservice ekran görüntüsü.":::
Uygulama klasörünün altındaki alt klasörleri gösteren Ordering.API microservice Çözüm Gezgini görünümü: Davranışlar, Komutlar, DomainEventHandlers, EntegrasyonOlaylar, Modeller, Sorgular ve Doğrulamalar.
:::image-end:::

**Şekil 7-23**. Ordering.API ASP.NET Core Web API projesindeki uygulama katmanı

ASP.NET Core, varsayılan olarak yapıcı enjeksiyonu destekleyen basit bir [dahili IoC kapsayıcısı](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (IServiceProvider arabirimi tarafından temsil edilir) içerir ve ASP.NET belirli hizmetleri DI aracılığıyla kullanılabilir hale getirir. ASP.NET Core, DI aracılığıyla enjekte edilecek kayıt türlerinden herhangi biri için dönem *hizmetini* kullanır. Yerleşik kapsayıcının hizmetlerini uygulamanızın Başlangıç sınıfındaki ConfigureServices yönteminde yapılandırAbilirsiniz. Bağımlılıklarınız, bir türün ihtiyaç duyduğu ve IoC kapsayıcısında kaydettiğiniz hizmetlerde uygulanır.

Genellikle, altyapı nesnelerini uygulayan bağımlılıkları enjekte etmek istiyorsunuz. Enjekte etmek için çok tipik bir bağımlılık bir depodur. Ama sahip olabileceğiniz diğer altyapı bağımlılığını enjekte edebilirsiniz. Daha basit uygulamalar için, DBContext aynı zamanda altyapı kalıcılık nesnelerinizin de uygulanması olduğundan, Çalışma Birimi desen nesnenizi (EF DbContext nesnesi) doğrudan enjekte edebilirsiniz.

Aşağıdaki örnekte, .NET Core'un gerekli depo nesnelerini oluşturucu aracılığıyla nasıl enjekte ettiğini görebilirsiniz. Sınıf, bir sonraki bölümde ele alacağız bir komut işleyicisidir.

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

Sınıf, işlemi yürütmek ve durum değişikliklerini sürdürmek için enjekte edilen depoları kullanır. Bu sınıfın bir komut işleyicisi, ASP.NET Core Web API denetleyiciyöntemi veya [DDD Uygulama Hizmeti](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)olup olmadığı önemli değildir. Sonuçta bir komut işleyicisi benzer bir şekilde depoları, etki alanı varlıkları ve diğer uygulama koordinasyonu kullanan basit bir sınıftır. Bağımlılık Enjeksiyonu, oluşturucuya dayalı DI'yi kullanan örnekte olduğu gibi, belirtilen tüm sınıflar için aynı şekilde çalışır.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Bağımlılık uygulama türlerini ve arayüzlerini veya soyutlamalarını kaydetme

Oluşturucular aracılığıyla enjekte edilen nesneleri kullanmadan önce, DI aracılığıyla uygulama sınıflarınıza enjekte edilen nesneleri üreten arabirimleri ve sınıfları nereye kaydedebileceğinizi bilmeniz gerekir. (Di gibi daha önce gösterildiği gibi, yapıcı dayalı.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>ASP.NET Core tarafından sağlanan dahili IoC kabını kullanın

ASP.NET Core tarafından sağlanan yerleşik IoC kapsayıcısını kullandığınızda, Startup.cs dosyasında aşağıdaki kodda olduğu gibi Yapılandırma Hizmetleri yönteminde enjekte etmek istediğiniz türleri kaydedebilirsiniz:

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

Bir IoC kapsayıcısında türleri kaydederken en yaygın desen, bir çift tür-bir arabirim ve ilgili uygulama sınıfı kaydetmektir. Daha sonra herhangi bir oluşturucu aracılığıyla IoC kapsayıcısından bir nesne istediğinizde, belirli bir tür arabirim nesnesi istersiniz. Örneğin, önceki örnekte, son satır, oluşturucularınızın IMyCustomRepository'ye (arayüz veya soyutlama) bağımlı olduğunu belirtirken, IoC kapsayıcısının MyCustomSQLServerRepository uygulamasının bir örneğini enjekte edeceğini belirtir Sınıfı.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Otomatik tür kaydı için Scrutor kitaplığını kullanma

.NET Core'da DI kullanırken, bir derlemeyi tarayabilmek ve türlerini kuralkuralına göre otomatik olarak kaydedebilmeniz isteyebilirsiniz. Bu özellik şu anda ASP.NET Core'da kullanılamıyor. Ancak, bunun için [Scrutor](https://github.com/khellang/Scrutor) kitaplığını kullanabilirsiniz. Bu yaklaşım, IoC kapsayıcınıza kaydedilmesi gereken düzinelerce türüolduğunda kullanışlıdır.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Matthew King. Hizmetleri Scrutor'a kaydetme** \
  <https://www.mking.net/blog/registering-services-with-scrutor>

- **Kristian Hellang. Scrutor, ne var?** GitHub deposu. \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a>Autofac'ı IoC kapsayıcısı olarak kullanma

Ayrıca ek IoC kapları kullanabilirsiniz ve [autofac](https://autofac.org/)kullanan eShopOnContainers, sipariş microservice olduğu gibi, ASP.NET Core boru hattı na takabilirsiniz. Autofac kullanırken genellikle, uygulama türlerinin birden çok sınıf kitaplıklarına dağıtılabileceği gibi, türünüzün nerede olduğuna bağlı olarak kayıt türlerini birden çok dosya arasında bölmenize olanak tanıyan türleri modüller aracılığıyla kaydedersiniz.

Örneğin, aşağıdaki leri, enjekte etmek isteyeceğiniz türleri içeren [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projesinin [Autofac uygulama modülüdür.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs)

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

Autofac ayrıca [derlemeleri tarayıp ad kurallarına göre türleri kaydetme özelliğine](https://autofac.readthedocs.io/en/latest/register/scanning.html)de sahiptir.

Kayıt işlemi ve kavramları, yerleşik ASP.NET Core IoC kapsayıcısı ile türleri kaydedebilirsiniz şekilde çok benzer, ancak Autofac kullanırken sözdizimi biraz farklıdır.

Örnek kodda, soyutlama IOrderRepository uygulama sınıfı OrderRepository ile birlikte kaydedilir. Bu, bir oluşturucu IOrderRepository soyutlama veya arabirim üzerinden bir bağımlılık beyan ettiğinde, IoC kapsayıcıorderRepository sınıfının bir örneğini enjekte edeceği anlamına gelir.

Örnek kapsam türü, bir örneğin aynı hizmet veya bağımlılık istekleri arasında nasıl paylaşılbildiğini belirler. Bağımlılık için bir istek yapıldığında, IoC kapsayıcıaşağıdakileri döndürebilir:

- Toplam kapsam başına tek bir örnek (ASP.NET Core IoC kapsayıcısında *kapsamlı*olarak adlandırılır).

- Bağımlılık başına yeni bir örnek (ASP.NET Core IoC kapsayıcısında *geçici*olarak adlandırılır).

- IoC kapsayıcısını kullanarak tüm nesneler arasında paylaşılan tek bir örnek (ASP.NET Core IoC kapsayıcısında *singleton*olarak adlandırılır).

#### <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Çekirdekte Bağımlılık Enjeksiyonuna Giriş** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- **Autofac mı?** Resmi belgeler. \
  <https://docs.autofac.org/en/latest/>

- **Autofac IoC konteyner örnek kapsamları ile Core IoC konteyner hizmet ömürleri ASP.NET karşılaştırma - Cesar de la Torre.** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a>Komut ve Komut İşleyici sülelerini uygulama

Önceki bölümde gösterilen DI-through-constructor örneğinde, IoC kapsayıcı bir sınıfta bir oluşturucu aracılığıyla depoları enjekte edildi. Ama tam olarak nereye enjekte edildi? Basit bir Web API'sinde (örneğin, eShopOnContainers'daki katalog microservice' te), bunları ASP.NET Core'un istek ardışık ardışık ardışık yapısının bir parçası olarak, bir denetleyici oluşturucuda MVC denetleyicileri düzeyinde enjekte elersiniz. Ancak, bu bölümün ilk kodunda (eShopOnContainers'daki Ordering.API hizmetinden [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) sınıfı), bağımlılıkların enjeksiyonu belirli bir komut işleyicisinin oluşturucusu aracılığıyla yapılır. Komut işleyicinin ne olduğunu ve neden kullanmak istediğinizi açıklayalım.

Komut deseni, bu kılavuzda daha önce tanıtılan CQRS deseni ile özünde ilişkilidir. CQRS'nin iki tarafı vardır. İlk alan, daha önce açıklanan [Dapper](https://github.com/StackExchange/dapper-dot-net) mikro ORM ile basitleştirilmiş sorgular kullanılarak yapılan sorgulardır. İkinci alan, hareketler için başlangıç noktası olan komutlar ve hizmet dışından gelen giriş kanalıdır.

Şekil 7-24'te gösterildiği gibi, desen istemci tarafından komutları kabul etmeye, etki alanı modeli kurallarına göre işlemeye ve son olarak durumları işlemlerle devam etmeye dayanır.

![İstemciden veritabanına üst düzey veri akışını gösteren diyagram.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

**Şekil 7-24**. CQRS deseni ndeki komutların veya "işlem tarafının" üst düzey görünümü

Şekil 7-24, Kullanıcı Bira uygulamasının API aracılığıyla veritabanını güncelleştirmek için `CommandHandler`Etki Alanı modeline ve Altyapıya bağlı bir komut gönderdiğini gösterir.

### <a name="the-command-class"></a>Komut sınıfı

Komut, sistemin durumunu değiştiren bir eylemi gerçekleştirmesi için bir istektir. Komutlar zorunludur ve sadece bir kez işlenmelidir.

Komutlar zorunlu olduğundan, genellikle zorunlu ruh halinde bir fiille adlandırılırlar (örneğin, "oluştur" veya "güncelleştirme") ve CreateOrderCommand gibi toplu türü içerebilir. Bir olayın aksine, bir komut geçmişten gelen bir gerçek değildir; bu sadece bir istektir ve bu nedenle reddedilebilir.

Komutlar, kullanıcının bir istek başlatması sonucunda kullanıcının ui'den veya işlem yöneticisi bir topluyu bir eylemi gerçekleştirmeye yönlendirirken bir işlem yöneticisinden kaynaklanabilir.

Bir komutun önemli bir özelliği, tek bir alıcı tarafından sadece bir kez işlenmesi gerektiğidir. Bunun nedeni, komutun uygulamada gerçekleştirmek istediğiniz tek bir eylem veya işlem olmasıdır. Örneğin, aynı sipariş oluşturma komutu birden fazla kez işlenmemelidir. Bu komutlar ve olaylar arasında önemli bir farktır. Birçok sistem veya mikro hizmet olayla ilgilenebileceğinden, olaylar birden çok kez işlenebilir.

Buna ek olarak, komutun iktidarsız olmaması durumunda bir komutun yalnızca bir kez işlenmesi önemlidir. Bir komut, sonucu değiştirmeden birden çok kez yürütülebiliyorsa, komutun yapısı ndan veya sistemin komutu işleme biçiminden dolayı idempotenttir.

Etki alanınızın iş kuralları ve değişmezleri altında mantıklı olduğunda komutlarınızı ve güncelleştirmelerinizi iktidara getirmek iyi bir uygulamadır. Örneğin, aynı örneği kullanmak için, herhangi bir nedenle (yeniden deneme mantığı, hackleme, vb.) aynı CreateOrder komutu sisteminize birden çok kez ulaşırsa, bu örneği tanımlayabilmeli ve birden çok sipariş oluşturmadığınızdan emin olmalısınız. Bunu yapmak için, işlemlere bir tür kimlik eklemeniz ve komutun veya güncelleştirmenin zaten işlenip işlenmediğini belirlemeniz gerekir.

Tek bir alıcıya bir komut gönderirsiniz; bir komut yayımlamazsınız. Yayımlama, bir şeyin olduğunu ve etkinlik alıcıları için ilginç olabileceğini belirten olaylar içindir. Olaylar söz konusu olduğunda, yayımcının hangi alıcıların olayı aldığı veya ne yaptığı konusunda hiçbir endişesi yoktur. Ancak etki alanı veya tümleştirme olayları zaten önceki bölümlerde tanıtılan farklı bir hikaye vardır.

Bir komut, bu komutu yürütmek için gereken tüm bilgileri içeren veri alanları veya koleksiyonları içeren bir sınıf la birlikte uygulanır. Komut, özellikle değişiklik veya hareket istemek için kullanılan özel bir Veri Aktarım Nesnesi (DTO) türüdür. Komutun kendisi, komutu işlemek için gereken bilgilere dayanır ve başka bir şey değildir.

Aşağıdaki örnekbasitleştirilmiş `CreateOrderCommand` sınıfı gösterir. Bu eShopOnContainers sipariş microservice kullanılan değişmez bir komutdur.

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

Temel olarak, komut sınıfı etki alanı modeli nesneleri kullanarak bir iş hareketi gerçekleştirmek için gereken tüm verileri içerir. Bu nedenle, komutlar salt okunur veri içeren ve hiçbir davranış sadece veri yapılarıdır. Komutun adı amacını gösterir. C# gibi birçok dilde komutlar sınıf olarak temsil edilir, ancak gerçek nesne yönelimli anlamda gerçek sınıflar değildir.

Ek bir özellik olarak, beklenen kullanım doğrudan etki alanı modeli tarafından işlenir, çünkü komutları değişmez. Öngörülen yaşamları boyunca değişmelerine gerek yoktur. C# sınıfında, iç durumu değiştiren herhangi bir ayarlayıcı veya başka yöntemlerin olmamasıyla imkansızlık sağlanabilir.

Komutların serileştirme/deserializing işleminden geçmesini istiyorsanız veya bekliyorsanız, özelliklerin özel bir ayarlayıcısı ve `[DataMember]` (veya) `[JsonProperty]`özniteliği olması gerektiğini unutmayın. Aksi takdirde, deserializer gerekli değerleri ile hedef nesneyi yeniden mümkün olmayacaktır. Sınıfın tüm özellikleri için parametreleri olan bir oluşturucuvarsa, her zamanki camelCase adlandırma kuralıile gerçekten salt okunur özelliklerini `[JsonConstructor]`de kullanabilirsiniz ve oluşturucuyu . Ancak, bu seçenek daha fazla kod gerektirir.

Örneğin, bir sipariş oluşturmak için komut sınıfı büyük olasılıkla oluşturmak istediğiniz sıraya veri açısından benzer, ancak büyük olasılıkla aynı öznitelikleri gerekmez. Örneğin, `CreateOrderCommand` sipariş henüz oluşturulmadığından, sipariş kimliği yoktur.

Birçok komut sınıfı, değiştirilmesi gereken bazı durum hakkında yalnızca birkaç alan gerektiren basit olabilir. Bir siparişin durumunu aşağıdakilere benzer bir komut kullanarak "işlemde" "ücretli" veya "sevk" olarak değiştiriyorsanız durum böyle olacaktır:

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

Bazı geliştiriciler, UI istek nesnelerini komut DT'lerinden ayrı hale getirsin, ancak bu yalnızca bir tercih konusudur. Bu çok fazla katma değer ile sıkıcı bir ayrım, ve nesneleri hemen hemen aynı şekli vardır. Örneğin, eShopOnContainers, bazı komutlar doğrudan istemci tarafında gelir.

### <a name="the-command-handler-class"></a>Komut işleyicisınıfı

Her komut için belirli bir komut işleyicisi sınıfı uygulamanız gerekir. Desen bu şekilde çalışır ve komut nesnesini, etki alanı nesnelerini ve altyapı deposu nesnelerini kullanacağınız yerdir. Komut işleyicisi aslında CQRS ve DDD açısından uygulama katmanının kalbidir. Ancak, tüm etki alanı mantığı etki alanı sınıflarında-toplam kökleri (kök varlıklar), alt varlıklar veya [etki alanı hizmetleri](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)içinde içermelidir, ancak uygulama katmanından bir sınıf olan komut işleyicisi içinde değil.

Komut işleyicisınıfı, bir önceki bölümde belirtilen Tek Sorumluluk İlkesi'ni (SRP) elde etme yolunda güçlü bir basamak sunar.

Bir komut işleyicisi bir komut alır ve kullanılan toplam bir sonuç alır. Sonuç, komutun başarılı bir şekilde yürütülmesi veya bir özel durum olmalıdır. Bir özel durum söz konusu olduğunda, sistem durumu değişmemelidir.

Komut işleyicisi genellikle aşağıdaki adımları alır:

- DTO [(arabulucu](https://en.wikipedia.org/wiki/Mediator_pattern) veya diğer altyapı nesnesinden) gibi komut nesnesini alır.

- Komutun geçerli olduğunu doğrular (arabulucu tarafından doğrulanmadıysa).

- Geçerli komutun hedefi olan toplam kök örneğini anında alartır.

- Bu komutu gerekli verileri alarak, toplam kök örnek üzerinde yöntemi yürütür.

- Agreganın yeni durumunu ilgili veritabanında devam eder. Bu son işlem gerçek işlemdir.

Genellikle, bir komut işleyicisi, toplam kökü (kök varlığı) tarafından yönlendirilen tek bir toplamla ilgilenir. Tek bir komutun alınmasından birden çok agrega etkilenecekse, durumları veya eylemleri birden çok toplama arasında yaymak için etki alanı olaylarını kullanabilirsiniz.

Burada önemli olan nokta, bir komut işlenirken, tüm etki alanı mantığının etki alanı modelinin (toplamlar) içinde, tamamen kapsüllenmiş ve birim testine hazır olması gerektiğidir. Komut işleyicisi, etki alanı modelini veritabanından almanın bir yolu olarak ve son adım olarak, altyapı katmanına (depolar) model değiştirildiğinde değişiklikleri devam etmesini söylemek için hareket eder. Bu yaklaşımın avantajı, tesisat düzeyi (komut işleyicileri, Web API, uygulama veya altyapı katmanlarında kod değiştirmeden yalıtılmış, tamamen kapsüllenmiş, zengin, davranışsal etki alanı modelinde etki alanı mantığını yeniden depolar, vb.)

Komut işleyicileri karmaşık hale geldiğinde, çok fazla mantıkla, bu bir kod kokusu olabilir. Bunları gözden geçirin ve etki alanı mantığı bulursanız, etki alanı davranışını etki alanı nesnelerinin (toplam kök ve alt varlık) yöntemlerine taşımak için kodu yeniden düzenlemeyi.

Komut işleyicisi sınıfına örnek olarak, aşağıdaki `CreateOrderCommandHandler` kod bu bölümün başında gördüğünüz aynı sınıfı gösterir. Bu durumda, Tutamaç yöntemini ve etki alanı modeli nesneleri/toplamları ile işlemleri vurgulamak istiyoruz.

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

Bunlar, komut işleyicinin atması gereken ek adımlardır:

- Toplam kökün yöntemleri ve davranışlarıyla çalışmak için komutverilerini kullanın.

- Etki alanı nesneleri içinde dahili olarak, işlem yürütülürken etki alanı olaylarını yükseltmek, ancak bir komut işleyicisi bakış açısından saydamdır.

- Agreganın işlem sonucu başarılı olursa ve işlem tamamlandıktan sonra tümleştirme olaylarını yükseltin. (Bunlar, depolar gibi altyapı sınıfları tarafından da gündeme getirilebilir.)

#### <a name="additional-resources"></a>Ek kaynaklar

- **Mark Seemann. Sınırlarda, Uygulamalar Nesne Yönelimli Değildir** \
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- **Komutlar ve olaylar** \
  <https://cqrs.nu/Faq/commands-and-events>

- **Bir komut işleyicisi ne yapar?** \
  <https://cqrs.nu/Faq/command-handlers>

- **Jimmy Bogard' ı. Etki Alanı Komut Desenleri - Işleyiciler** \
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- **Jimmy Bogard' ı. Etki Alanı Komut Uyruğu Desenleri – Doğrulama** \
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Komut işlemi ardışık hattı: komut işleyicisi nasıl tetiklenir

Bir sonraki soru, komut işleyicisi nasıl çağrılmasıdır. İlgili her ASP.NET Core denetleyicisinden el ile arayabilirsiniz. Ancak, bu yaklaşım çok birleştiğinde ve ideal değildir.

Önerilen seçenekler olan diğer iki ana seçenek şunlardır:

- Hafıza içi arabulucu desen objesi aracılığıyla.

- Denetleyiciler ve işleyiciler arasında bir eşzamanlı ileti sırası ile.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Komut ardışık düzeninde Arabulucu deseni (bellekte) kullanma

Şekil 7-25'te gösterildiği gibi, CQRS yaklaşımında, alınan komut veya DTO'nun türüne göre sağ komut işleyicisine yönlendirilecek kadar akıllı olan bellek içi veri yoluna benzer akıllı bir arabulucu kullanırsınız. Bileşenler arasındaki tek siyah oklar, nesneler arasındaki bağımlılıkları (çoğu durumda, DI aracılığıyla enjekte edilen) ve ilgili etkileşimlerini temsil eder.

![İstemciden veritabanına daha ayrıntılı bir veri akışını gösteren diyagram.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

**Şekil 7-25.** Tek bir CQRS microservice sürecinde Arabulucu deseni kullanma

Yukarıdaki diyagram, resim 7-24'ten bir yakınlaştırma gösterir: ASP.NET Core denetleyicisi komutu MediatR'ın komut ardışık hattına gönderir, böylece uygun işleyiciye ulaşırlar.

Arabulucu deseni kullanmanın mantıklı olmasının nedeni, kurumsal uygulamalarda işleme isteklerinin karmaşık hale gelebiliyor olmasıdır. Oturum açma, doğrulama, denetim ve güvenlik gibi açık sayıda çapraz kesme yle ilgili açık bir sayı ekleyebilmek istiyorsunuz. Bu gibi durumlarda, bu ekstra davranışlar veya çapraz kesme endişeleri için bir araç sağlamak için bir arabulucu ardışık düzenine güvenebilirsiniz (bkz. [Arabulucu deseni).](https://en.wikipedia.org/wiki/Mediator_pattern)

Arabulucu, bu işlemin "nasıl" olduğunu kapsülleyen bir nesnedir: yürütmeyi duruma, komut işleyicisinin çağrılma şekline veya işleyiciye sağladığınız yükü temel alınabiliyor. Bir arabulucu bileşeni ile dekoratörleri (veya [MediatR 3'ten](https://www.nuget.org/packages/MediatR/3.0.0)beri [boru hattı davranışlarını)](https://github.com/jbogard/MediatR/wiki/Behaviors) uygulayarak çapraz kesme endişelerini merkezi ve şeffaf bir şekilde uygulayabilirsiniz. Daha fazla bilgi için [Dekoratör desenine](https://en.wikipedia.org/wiki/Decorator_pattern)bakın.

Dekoratörler ve davranışlar [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)benzer, sadece aracı bileşeni tarafından yönetilen belirli bir işlem boru hattı uygulanır. AOP'de çapraz kesme endişeleri uygulayan yönler, derleme zamanında enjekte edilen *boy dokumacılarına* veya nesne çağrısı engellemeye dayalı olarak uygulanır. Her iki tipik AOP yaklaşımının bazen "sihir gibi" çalıştığı söylenir, çünkü AOP'un işini nasıl yaptığını görmek kolay değildir. Ciddi sorunlar veya hatalarla uğraşırken Hata ayıklama zor olabilir. Öte yandan, bu dekoratörler / davranışlar açık ve sadece arabulucu bağlamında uygulanan, bu yüzden hata ayıklama çok daha öngörülebilir ve kolaydır.

Örneğin, mikrohizmet sipariş için eShopOnContainers' da iki örnek davranış, bir [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınırı ve [bir ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) sınırı uyguladık. Davranışların uygulanması, eShopOnContainers'ın [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [davranışlarını](https://github.com/jbogard/MediatR/wiki/Behaviors)nasıl kullandığını göstererek bir sonraki bölümde açıklanmıştır.

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Komutun ardışık durumunda ileti kuyruklarını (proc dışı) kullanma

Başka bir seçenek, Şekil 7-26'da gösterildiği gibi, aracılara veya ileti kuyruklarına dayalı eşzamanlı iletiler kullanmaktır. Bu seçenek, komut işleyicisi hemen önce aracı bileşeni ile de birleştirilebilir.

![HA ileti kuyruğunu kullanarak veri akışını gösteren diyagram.](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

**Şekil 7-26.** CQRS komutları ile ileti kuyruklarını (işlem ve süreçler arası iletişim dışında) kullanma

Komutun ardışık hattı, komutları uygun işleyiciye teslim etmek için yüksek kullanılabilirlik iletisi kuyruğu tarafından da işlenebilir. Komutları kabul etmek için ileti kuyruklarını kullanmak, büyük olasılıkla ardışık hattı dış ileti kuyruğu üzerinden bağlı iki işlemolarak bölmeniz gerektiğinden, komutunuzun ardışık hattını daha da karmaşık hale getirebilir. Yine de, asynchronous iletidayalı gelişmiş ölçeklenebilirlik ve performans olması gerekiyorsa kullanılmalıdır. Şekil 7-26 durumunda, denetleyicinin komut iletisini kuyruğa gönderdiğini ve döndürtuğugöz önünde bulundurun. Daha sonra komut işleyicileri iletileri kendi hızlarında işler. Bu, kuyrukların büyük bir yararıdır: Ileti sırası, yüksek hacimli giriş verisi olan hisse senetleri veya başka bir senaryo gibi hiper ölçeklenebilirliğin gerekli olduğu durumlarda arabellek görevi görebilir.

Ancak, ileti kuyruklarının eşzamanlı yapısı nedeniyle, komut işleminin başarısı veya başarısızlığı hakkında istemci uygulamasıyla nasıl iletişim kurabileceğinizi bulmanız gerekir. Kural olarak, asla "ateş ve unut" komutlarını kullanmamalısınız. Her iş başvurusu, bir komutun başarılı bir şekilde işlenilip işlenmeden veya en azından doğrulanıp kabul edilip edilip edilemeden bilinmesi gerekir.

Bu nedenle, eşzamanlı bir sıraya gönderilen bir komut iletisini doğruladıktan sonra istemciye yanıt verebilmek, işlemi çalıştırdıktan sonra işlemin sonucunu döndüren bir işlem içi komut işlemiyle karşılaştırıldığında sisteminize karmaşıklık katar. Kuyrukları kullanarak, sisteminizde ek bileşenler ve özel iletişim gerektirecek diğer işlem sonuç iletileri aracılığıyla komut işleminin sonucunu döndürmeniz gerekebilir.

Ayrıca, async komutları tek yönlü komutları, birçok durumda gerekli olmayabilir, bir [online konuşma](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ)Burtsev Alexey ve Greg Young arasında aşağıdaki ilginç alışverişinde açıklandığı gibi:

> \[Burtsev Alexey\] Ben insanların bunu yapmak için herhangi bir neden olmadan async komut işleme veya tek yönlü komut mesajlaşma kullanmak kod çok bulmak (onlar bazı uzun işlem yapmıyoruz, onlar harici async kodu yürütülmez, hatta mesaj veri yolu kullanarak uygulama sınırını geçmez). Neden bu gereksiz karmaşıklığı ortaya atıyorlar? Ve aslında, çoğu durumda sadece iyi çalışacak olsa, şimdiye kadar komut işleyicileri engelleme ile bir CQRS kodu örneği görmedim.
>
> \[Greg\] \[Genç ... \] bir eşzamanlı komut yoktur; Aslında başka bir olay. Eğer bana gönderdiğin şeyi kabul edip, aynı fikirde değilsem bir etkinlik büyütmem \[gerekiyorsa, artık bana bir\]şey yapmamı söylemiyorsun, bu bir emir değil. Bana bir şey yapıldığını söylüyorsun. Bu ilk başta hafif bir fark gibi görünüyor, ama birçok etkileri vardır.

Asynchronous komutları bir sistemin karmaşıklığını büyük ölçüde artırır, çünkü hataları göstermenin basit bir yolu yoktur. Bu nedenle, asenkron komutlar ölçekleme gereksinimleri gerekli olduğunda veya özel durumlarda dahili mikro hizmetleri mesajlaşma yoluyla ileterken dışında önerilmez. Bu gibi durumlarda, hatalar için ayrı bir raporlama ve kurtarma sistemi tasarlamanız gerekir.

eShopOnContainers ilk sürümünde, senkron komut işleme kullanmaya karar verdi, HTTP istekleri başladı ve Arabulucu desen tarafından tahrik. Bu, [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) uygulamasında olduğu gibi işlemin başarısını veya başarısızlığını kolayca döndürmenizi sağlar.

Her durumda, bu uygulamanızın veya microservice'in iş gereksinimlerine dayalı bir karar olmalıdır.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Arabulucu desenli komut işlemi ardışık hattını uygulayın (MediatR)

Örnek bir uygulama olarak, bu kılavuz, komut yutma ve rota komutları sürücü için Arabulucu desen dayalı süreç içi ardışık kullanarak önerir, bellekte, sağ komut işleyicileri. Kılavuz ayrıca çapraz kesme kaygılarını ayırmak için [davranışların](https://github.com/jbogard/MediatR/wiki/Behaviors) uygulanmasını da önerir.

.NET Core'da uygulama için Arabulucu deseni uygulayan birden çok açık kaynak kitaplık vardır. Bu kılavuzda kullanılan kitaplık [MediatR](https://github.com/jbogard/MediatR) açık kaynak kitaplığı (Jimmy Bogard tarafından oluşturulmuştur), ancak başka bir yaklaşım kullanabilirsiniz. MediatR, dekoratörleri veya davranışları uygularken bellek içi iletileri komut gibi işlemenizi sağlayan küçük ve basit bir kitaplıktır.

Arabulucu deseni kullanmak, bağlantıyı azaltmanıza ve istenen çalışmanın endişelerini yalıtmanıza yardımcı olurken, bu durumda işi gerçekleştiren işleyiciye otomatik olarak bağlanarak işleyicileri komut komutlarına bağlar.

Arabulucu desen kullanmak için başka bir iyi nedeni Jimmy Bogard tarafından bu kılavuzu gözden geçirerek açıklanmıştır:

> Ben burada test söz değer olabileceğini düşünüyorum - sisteminizin davranışı içine güzel bir tutarlı pencere sağlar. İstek, yanıt-out. Bu yönü sürekli davranan testler inşa oldukça değerli bulduk.

İlk olarak, aracı nesneyi gerçekten kullanacağınız örnek bir WebAPI denetleyicisine bakalım. Arabulucu nesnesini kullanmıyorsanız, bu denetleyicinin tüm bağımlılıklarını, logger nesnesi gibi şeyleri ve diğer şeyleri enjekte etmeniz gerekir. Bu nedenle, yapıcı oldukça karmaşık olacaktır. Diğer taraftan, arabulucu nesnesini kullanırsanız, denetleyicinizin oluşturucusu, aşağıdaki örnekte olduğu gibi, kesme işlemi başına bir tane varsa, birçok bağımlılık yerine yalnızca birkaç bağımlılıkla çok daha basit olabilir:

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

Arabulucunun temiz ve yalın bir Web API denetleyici oluşturucusu sağladığını görebilirsiniz. Buna ek olarak, denetleyici yöntemleri içinde, arabulucu nesnesine komut göndermek için kod neredeyse bir satırdır:

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

### <a name="implement-idempotent-commands"></a>Idempotent Komutları Uygulama

**eShopOnContainers**, yukarıdaki daha gelişmiş bir örnek Sipariş microservice bir CreateOrderCommand nesne siniyor. Ancak Sipariş iş süreci biraz daha karmaşık olduğundan ve bizim durumumuzda aslında Sepet microservice başlar, CreateOrderCommand nesne gönderme bu eylem bir önceki basit örnekte olduğu gibi istemci App çağrılan basit bir WebAPI denetleyicisi yerine [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) adlı bir entegrasyon olay işleyicisi gerçekleştirilir.

Bununla birlikte, Komut'u MediatR'a gönderme eylemi aşağıdaki kodda gösterildiği gibi oldukça benzerdir.

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

Ancak, bu durum da biraz daha gelişmiş çünkü biz de idempotent komutları uyguluyoruz. CreateOrderCommand işlemi idempotent olmalıdır, bu nedenle aynı ileti ağ üzerinden çoğaltılır gelirse, herhangi bir nedenle, yeniden denemeler gibi, aynı iş sırası sadece bir kez işlenir.

Bu, iş komutunu sarmalayarak (bu durumda CreateOrderCommand) ve idempotent olması gereken ağ üzerinden gelen her iletinin bir kimliği tarafından izlenen genel bir IdentifiedCommand içine katıştırma tarafından uygulanır.

Aşağıdaki kodda, Tanımlanan Komut'un dto ve id artı sarılmış iş komutu nesnesinden başka bir şey olmadığını görebilirsiniz.

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

Daha sonra [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) adlı Tanımlanan Komut için CommandHandler temelde iletinin bir parçası olarak gelen kimliğin bir tabloda zaten var olup olmadığını denetler. Zaten varsa, bu komut tekrar işlenmez, bu nedenle bir idempotent komut olarak görev eder. Bu altyapı kodu aşağıdaki `_requestManager.ExistAsync` yöntem çağrısı ile gerçekleştirilir.

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

IdentifiedCommand bir iş komutu zarfı gibi davranır, çünkü tekrarlanan bir Id değil iş komutu işlenmesi gerektiğinde, o zaman bu iç iş komutu alır ve arabulucu ya yeniden `_mediator.Send(message.Command)`gönderir, çalışırken yukarıda gösterilen kodun son bölümünde olduğu gibi , [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).

Bunu yaparken, aşağıdaki kodda gösterildiği gibi, sipariş veritabanına karşı işlemleri yürüten [CreateOrderCommandHandler,](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) bu durumda, iş komut işleyicisi bağlayacak ve çalıştırın.

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

MediatR'ın komut işleyici sınıflarınızı bilmesi için, ioC kapsayıcınızda arabulucu sınıflarını ve komut işleyici sınıflarını kaydetmeniz gerekir. Varsayılan olarak, MediatR IoC kapsayıcı olarak Autofac kullanır, ancak yerleşik ASP.NET Core IoC kapsayıcı veya MediatR tarafından desteklenen başka bir kapsayıcı kullanabilirsiniz.

Aşağıdaki kod, Autofac modüllerini kullanırken Arabulucu türlerinin ve komutlarının nasıl kaydedileceğini gösterir.

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

MediatR ile "büyü nün gerçekleştiği yer burası".

Her komut işleyicisi `IAsyncRequestHandler<T>` genel arabirimi uyguladığından, derlemeleri kaydederken, kod aşağıdaki `IAsyncRequestHandler` örnekte `CommandHandlers` olduğu `Commands` `CommandHandler` gibi, sınıfta belirtilen ilişki sayesinde, kendi , ile ilgili olarak işaretlenmiş tüm türleri ile `RegisteredAssemblyTypes` kaydeder:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Bu komutları komut işleyicileri ile ilişkilendiren koddur. İşleyici sadece basit bir sınıftır, ancak `RequestHandler<T>`T komut türü olduğu yerden devralır ve MediatR doğru yük (komut) ile çağrıldığından emin olur.

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>MediatR'daki Davranışlar ile komutları işlerken çapraz kesme endişeleri uygulayın

Bir şey daha var: arabulucu boru hattına çapraz kesme kaygılarını uygulayabilmek. Autofac kayıt modülü kodunun sonunda, özellikle özel bir LoggingBehavior sınıfı ve ValidatorBehavior sınıfını nasıl kaydettiğini de görebilirsiniz. Ama başka özel davranışlar da ekleyebilirsiniz.

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

[Bu LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı, komut işleyicisinin yürütüldüğü ve başarılı olup olmadığı yla ilgili bilgileri günlüğe kaydeden aşağıdaki kod olarak uygulanabilir.

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

Yalnızca bu davranış sınıfını uygulayarak ve ardışık (yukarıdaki Arabulucu Modülü'nde) kaydederek, MediatR aracılığıyla işlenen tüm komutlar yürütme hakkında bilgi günlüğe kaydeder.

mikrohizmet sipariş ibareleri, aşağıdaki kodda gösterildiği gibi, [Akıcı Geçersiz lik](https://github.com/JeremySkinner/FluentValidation) kitaplığına dayanan [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) sınıfı olan temel doğrulamalar için ikinci bir davranış da uygular:

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

Buradaki davranış, doğrulama başarısız olursa bir özel durum yükseltiyor, ancak başarılı olursa komut sonucunu veya başarısız olması durumunda doğrulama iletilerini içeren bir sonuç nesnesi de döndürebilirsiniz. Bu, doğrulama sonuçlarını kullanıcıya görüntülemeyi büyük olasılıkla kolaylaştırır.

Daha sonra, [FluentValidation](https://github.com/JeremySkinner/FluentValidation) kitaplığını temel aldığımızda, aşağıdaki kodda olduğu gibi CreateOrderCommand ile aktarılan veriler için doğrulama oluşturduk:

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

Ek doğrulamalar oluşturabilirsiniz. Bu komut doğrulamaları uygulamak için çok temiz ve zarif bir yoldur.

Benzer bir şekilde, komutları işlerken uygulamak istediğiniz ek yönler veya çapraz kesme kaygıları için diğer davranışları uygulayabilirsiniz.

#### <a name="additional-resources"></a>Ek kaynaklar

##### <a name="the-mediator-pattern"></a>Arabulucu deseni

- **Arabulucu deseni** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Dekoratör deseni

- **Dekoratör deseni** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>Arabulucu (Jimmy Bogard)

- **MediatR' ı.** GitHub deposu. \
  <https://github.com/jbogard/MediatR>

- **MediatR ve AutoMapper ile CQRS** \
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- **Kontrolörlerinizi bir diyete koyun: POSTs ve komutlar.** \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- **Arabulucu boru hattı ile çapraz kesme sorunlarıyla mücadele** \
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- **CQRS ve REST: mükemmel maç** \
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- **MediatR Boru Hattı Örnekleri** \
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- **MediatR ve ASP.NET Çekirdek için Dikey Dilim Test Armatürleri** \
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- **Microsoft Bağımlılık Enjeksiyonu Için MediatR Uzantıları Yayınlandı** \
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a>Akıcı doğrulama

- **Jeremy Skinner' ı. Akıcı Doğrulama.** GitHub deposu. \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> [Önceki](microservice-application-layer-web-api-design.md)
> [Sonraki](../implement-resilient-applications/index.md)
