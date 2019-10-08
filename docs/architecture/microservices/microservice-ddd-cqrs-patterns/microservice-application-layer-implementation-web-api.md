---
title: Web API’si kullanarak mikro hizmet uygulama katmanını uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Bağımlılık ekleme ve ortalama düzenlerini ve bunların uygulama ayrıntılarını Web API 'SI uygulama katmanında anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: d462f692366575fd01842f41252fc96658fdcac5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002341"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Web API 'sini kullanarak mikro hizmet uygulama katmanını uygulama

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Uygulama katmanınıza altyapı nesneleri eklemek için bağımlılık ekleme 'yi kullanma

Daha önce belirtildiği gibi, uygulama katmanı, oluşturduğunuz yapıtın (derleme) bir parçası olarak (örneğin, bir Web API projesi veya bir MVC web uygulaması projesi) uygulanabilir. ASP.NET Core ile oluşturulmuş bir mikro hizmet söz konusu olduğunda, uygulama katmanı genellikle Web API kitaplığınız olacaktır. Özel uygulama katmanı kodunuzda ASP.NET Core (altyapı ve Denetleyicilerinizden) nelerin geldiğini ayırmak istiyorsanız, uygulama katmanınızı ayrı bir sınıf kitaplığına yerleştirebilirsiniz, ancak bu isteğe bağlıdır.

Örneğin, sıralama mikro hizmetinin uygulama katmanı kodu, Şekil 7-23 ' de gösterildiği gibi doğrudan **sıralama. API** projesinin (bir ASP.NET Core Web API Projesi) bir parçası olarak uygulanır.

![Sıralama. API mikro hizmeti 'nin, uygulama klasörü altındaki alt klasörleri gösteren Çözüm Gezgini görünümü: davranışlar, komutlar, DomainEventHandlers, ıntegrationevents, modeller, sorgular ve doğrulamalar.](./media/image20.png)

**Şekil 7-23**. Sıralama. API ASP.NET Core Web API projesindeki uygulama katmanı

ASP.NET Core, varsayılan olarak Oluşturucu ekleme işlemini destekleyen basit bir [yerleşik IOC kapsayıcısı](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (IServiceProvider arabirimi tarafından temsil edilir) içerir ve ASP.net, belırlı Hizmetleri dı üzerinden kullanılabilir hale getirir. ASP.NET Core, YAZMAÇ aracılığıyla eklenecek olan herhangi bir türden herhangi biri için *hizmet* koşulları 'nı kullanır. Yerleşik kapsayıcının hizmetlerini uygulamanızın başlangıç sınıfındaki ConfigureServices yönteminde yapılandırırsınız. Bağımlılıklarınız, bir tür için gereken ve IOC kapsayıcısına kaydolmanızı sağlayan hizmetlerde uygulanır.

Genellikle, altyapı nesneleri uygulayan bağımlılıklar eklemek istersiniz. Ekleme için çok tipik bir bağımlılık, bir depodur. Ancak sahip olduğunuz herhangi bir altyapı bağımlılığı ekleyebilirsiniz. Daha basit uygulamalar için, DBContext aynı zamanda altyapı Kalıcılık nesnelerinizin uygulanması olduğundan, çalışma birimi nesnesi (EF DbContext nesnesi) birimini doğrudan ekleyebiliriniz.

Aşağıdaki örnekte, .NET Core 'un Oluşturucu aracılığıyla gerekli depo nesnelerini nasıl ekleme görürsünüz. Sınıfı, sonraki bölümde ele alacak bir komut işleyicisidir.

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

Sınıfı, işlemi yürütmek ve durum değişikliklerini kalıcı hale getirmek için eklenen depoları kullanır. Bu sınıfın bir komut işleyicisi, ASP.NET Core Web API denetleyicisi yöntemi veya [ddd uygulama hizmeti](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)olup olmadığı konusunda bir önemi yoktur. Sonuç olarak, bir komut işleyicisine benzer şekilde depoları, etki alanı varlıklarını ve diğer uygulama koordinasyonunu kullanan basit bir sınıftır. Bağımlılık ekleme, kurucuya göre dı kullanan örnekte olduğu gibi, belirtilen tüm sınıflar için aynı şekilde çalışmaktadır.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Bağımlılık uygulama türlerini ve arabirimlerini veya soyutlamaları kaydetme

Oluşturucular aracılığıyla eklenen nesneleri kullanmadan önce, uygulama sınıflarınıza eklenen nesneleri oluşturan arabirimlerin ve sınıfların, DI aracılığıyla ne şekilde kaydedeceğinizi bilmeniz gerekir. (Daha önce gösterildiği gibi, oluşturucuyu temel alan dı gibi.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>ASP.NET Core tarafından sunulan yerleşik IOC kapsayıcısını kullanın

ASP.NET Core tarafından sağlanmış yerleşik IOC kapsayıcısını kullandığınızda, Startup.cs dosyasındaki ConfigureServices yöntemine eklemek istediğiniz türleri aşağıdaki kodda olduğu gibi kaydedersiniz:

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

Bir IOC kapsayıcısına türlerin kaydedilmesinde en sık kullanılan desenler, bir arabirim ve ilgili uygulama sınıfı olan bir çift türü kaydetmesidir. Ardından, herhangi bir Oluşturucu aracılığıyla IOC kapsayıcısından bir nesne istediğinizde, belirli bir arabirim türünün bir nesnesini istemeniz gerekir. Örneğin, önceki örnekte, kurucularınızın herhangi birinin ımıcustomrepository (arabirim veya soyutlama) üzerinde bir bağımlılığı olduğunda, IOC kapsayıcısı MyCustomSQLServerRepository uygulamasının bir örneğini ekleyecektir sınıfı.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Otomatik türler kaydı için Itilen kitaplığı kullanın

.NET Core 'da dı kullanırken, bir derlemeyi tarayabilmesi ve türlerini kurala göre otomatik olarak kaydetmenizi isteyebilirsiniz. Bu özellik şu anda ASP.NET Core ' de kullanılamaz. Ancak, bunun için [itilen](https://github.com/khellang/Scrutor) kitaplığı kullanabilirsiniz. Bu yaklaşım, IOC kapsayıcısına kaydedilmesi gereken düzinelerce türlerinizin olması durumunda kullanışlıdır.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Matthew King. Hizmetleri Itilen @no__t kaydetme**-1
  <https://www.mking.net/blog/registering-services-with-scrutor>

- **Bir Hellang. İtilen.** GitHub deposu. \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a>IoC kapsayıcısı olarak Autofac kullanma

Ayrıca, ek IOC kapsayıcıları kullanabilir ve bunları, [Autofac](https://autofac.org/)kullanan eShopOnContainers 'daki sıralama mikro hizmetinde olduğu gibi ASP.NET Core işlem hattına ekleyebilirsiniz. Autofac kullanırken, genellikle türleri modüller aracılığıyla kaydedersiniz; bu sayede, birden çok sınıf kitaplığı genelinde dağıtılmış uygulama türlerine sahip olduğu gibi, kayıt türlerini türlerinizin bulunduğu yere bağlı olarak birden çok Dosya arasında bölmeniz sağlanır.

Örneğin, aşağıda [sıralama. API Web API 'si](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projesi için eklemek istediğiniz türleri içeren [Autofac uygulama modülü](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) verilmiştir.

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

Autofac Ayrıca [derlemeleri tarama ve türleri ad kurallarına göre kaydetme](https://autofac.readthedocs.io/en/latest/register/scanning.html)özelliği de vardır.

Kayıt işlemi ve kavramlar, yerleşik ASP.NET Core IOC kapsayıcısına sahip türleri kaydetme yöntemine çok benzer, ancak Autofac kullanırken sözdizimi biraz farklıdır.

Örnek kodda, soyutlama ıorderrepository, OrderRepository uygulama sınıfı ile birlikte kaydedilir. Bu, bir oluşturucunun ıorderrepository soyutlama veya arabirimi aracılığıyla bağımlılık bildirdiğinde, IOC kapsayıcısının OrderRepository sınıfının bir örneğini ekleymesidir.

Örnek kapsamı türü, bir örneğin aynı hizmet veya bağımlılık istekleri arasında nasıl paylaşılacağını belirler. Bağımlılık için bir istek yapıldığında, IOC kapsayıcısı aşağıdakileri döndürebilir:

- Yaşam süresi kapsamı başına tek örnekli (ASP.NET Core IOC kapsayıcısında *kapsam*olarak adlandırılır).

- Bağımlılık başına yeni bir örnek (ASP.NET Core IOC kapsayıcısında *geçici*olarak adlandırılır).

- IFC kapsayıcısını kullanan tüm nesneler genelinde paylaşılan tek bir örnek (ASP.NET Core IOC kapsayıcısında *Singleton*olarak adlandırılır).

#### <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core @no__t bağımlılık eklenmesine giriş**-1
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** Resmi belgeler. \
  <https://docs.autofac.org/en/latest/>

- **Autofac IoC kapsayıcı örneği kapsamları ile ASP.NET Core IOC kapsayıcı hizmeti yaşam sürelerini karşılaştırma-Cesar de La Torre.** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a>Komut ve komut Işleyici desenlerini uygulama

Önceki bölümde gösterilen dı---Oluşturucu örneğinde, IOC kapsayıcısı bir sınıftaki Oluşturucu aracılığıyla ekleme depolandı. Ancak tam olarak nereye eklenen? Basit bir Web API 'sinde (örneğin, eShopOnContainers 'daki Katalog mikro hizmeti), ASP.NET Core istek ardışık düzeninin bir parçası olarak, bunları bir denetleyici oluşturucusunda MVC denetleyicileri ' düzeyinde eklersiniz. Ancak, bu bölümün ilk kodunda (eShopOnContainers 'daki sıralama. API hizmetinden [Createordercommandhandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) sınıfı), bağımlılık ekleme işlemi, belirli bir komut işleyicisinin Oluşturucusu aracılığıyla yapılır. Bir komut işleyicisinin ne olduğunu ve neden kullanmak istediğinizi açıklamıza izin verin.

Komut deseninin, bu kılavuzda daha önce sunulan CQRS düzeniyle ilgili doğası gereği vardır. CQRS 'nin iki yüzü vardır. İlk alan, daha önce açıklanan [paber](https://github.com/StackExchange/dapper-dot-net) mikro ORM ile basitleştirilmiş sorguları kullanarak sorgular. İkinci alan, işlemler için başlangıç noktası ve hizmet dışından giriş kanalı olan komutlardır.

Şekil 7-24 ' de gösterildiği gibi, model, istemci tarafındaki komutları kabul etmeyi, etki alanı modeli kurallarına göre işlemeyi ve son olarak işlemler ile durumları kalıcı hale getirmeyi temel alır.

![CQRS: UI uygulamasındaki yazma tarafı üst düzey görünümü, etki alanı modeline ve veritabanını güncelleştirme altyapısına bağlı olan bir CommandHandler 'e yönelik API aracılığıyla bir komut gönderir.](./media/image21.png)

**Şekil 7-24**. Bir CQRS deseninin içindeki komutların veya "işlem tarafındaki" üst düzey görünümü

### <a name="the-command-class"></a>Komut sınıfı

Komut, sistemin sistem durumunu değiştiren bir eylem gerçekleştirmesi için bir isteğidir. Komutları zorunludur ve yalnızca bir kez işlenmelidir.

Komutlar imperatives olduğundan, genellikle kesinlik (örneğin, "Oluştur" veya "Güncelleştir") bir fiil ile adlandırılır ve CreateOrderCommand gibi toplam türü içerebilir. Bir olaydan farklı olarak, bir komut geçmişte bir olgu değildir; yalnızca bir istekte bulunur ve bu nedenle bu durum reddedilebilir.

Komutlar, bir kullanıcının isteği başlatan bir sonucu olarak veya işlem yöneticisi bir eylemi gerçekleştirmek için bir toplama işlemi yaparken bir işlem yöneticisi 'nden kaynaklı olabilir.

Bir komutun önemli bir özelliği tek bir alıcı tarafından yalnızca bir kez işlenmelidir. Bunun nedeni, bir komutun uygulamada gerçekleştirmek istediğiniz tek bir eylem veya işlemdir. Örneğin, aynı sıra oluşturma komutu birden çok kez işlenmemelidir. Bu, komutlar ve olaylar arasındaki önemli bir farktır. Olaylar birden çok kez işlenebilir, çünkü birçok sistem veya mikro hizmet olayla ilgileniyor olabilir.

Ayrıca, komutun ıdempotent olmadığı durumlarda bir komutun yalnızca bir kez işlenmesi önemlidir. Komutun doğası veya sistemin komutu işleme biçimi nedeniyle, sonucu değiştirmeden birden çok kez yürütülebileceğini bir komut ıdempotent olur.

Bu, kullanıcılarınızın iş kuralları ve ınvaryanslarınızın altındayken komutlarınızın ve güncelleştirmelerin ıdempotent hale gelmesini iyi bir uygulamadır. Örneğin, her nedenden dolayı aynı örneği kullanmak için (yeniden deneme mantığı, hacimme vb.), aynı CreateOrder komutu sisteminize birden çok kez ulaşırsa, bunu tanımlayabilir ve birden çok sipariş oluşturmayın. Bunu yapmak için, işlemlere bir tür kimlik eklemeniz ve komutun veya güncelleştirmenin zaten işlenip işlenmediğini belirlemeniz gerekir.

Tek bir alıcıya komut gönderirsiniz; bir komut yayımlamayın. Yayımlama, bir şeyin meydana geldiğini ve Olay alıcıları için ilginç olabileceğini gösteren olaylar içindir. Olaylar söz konusu olduğunda, yayımcı hangi alıcıların olay veya ne yaptığını öğrenmek için bir kaygıya sahip değildir. Ancak, etki alanı veya tümleştirme olayları önceki bölümlerde zaten tanıtılan farklı bir hikayeye sahiptir.

Bir komut, bu komutu yürütmek için gereken tüm bilgileri içeren veri alanları veya Koleksiyonlar içeren bir sınıf ile uygulanır. Bir komut, özellikle değişiklik veya işlem istemek için kullanılan özel bir Veri Aktarımı nesne türüdür (DTO). Komutun kendisi, komutu işlemek için gereken bilgileri ve başka hiçbir şeyi temel alır.

Aşağıdaki örnek basitleştirilmiş `CreateOrderCommand` sınıfını gösterir. Bu, eShopOnContainers 'daki sıralama mikro hizmetinde kullanılan sabit bir komuttur.

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

Temel olarak, komut sınıfı, etki alanı model nesnelerini kullanarak bir iş işlemi gerçekleştirmek için gereken tüm verileri içerir. Bu nedenle, komutlar yalnızca salt okunurdur verileri içeren veri yapılarıdır ve hiçbir davranış yoktur. Komutun adı, amacını gösterir. Gibi C#birçok dilde komutlar sınıflar olarak temsil edilir ancak gerçek nesne yönelimli anlamda doğru sınıflar değildir.

Ek bir özellik olarak, beklenen kullanım doğrudan etki alanı modeli tarafından işlendiklerinden, komutlar sabittir. Bunların öngörülen yaşam süresi boyunca değiştirmeleri gerekmez. Bir sınıfta C# , bir ayarlayıcıya ya da iç durumu değiştiren başka yöntemler yoksa, dengeshlik kullanılabilirliği elde edilebilir.

Komutları bir serileştirme/seri durumdan çıkarma işlemi boyunca işlem yapmak veya beklemek istiyorsanız, özelliklerin özel ayarlayıcı ve `[DataMember]` (ya da `[JsonProperty]`) özniteliği olması gerektiğini unutmayın, aksi takdirde seri hale getirici nesneyi şu konumda yeniden yapılandıramazlar: gerekli değerlere sahip hedef.

Örneğin, sipariş oluşturmak için komut sınıfı büyük olasılıkla veri bakımından oluşturmak istediğiniz sıraya benzer, ancak büyük olasılıkla aynı özniteliklere gerek kalmaz. Örneğin, sipariş henüz oluşturulmadığından `CreateOrderCommand` ' ın bir sıra KIMLIĞI yoktur.

Birçok komut sınıfı basit olabilir ve değiştirilmesi gereken bazı durumları hakkında yalnızca birkaç alan gerektirir. Bu durum, aşağıdakine benzer bir komut kullanarak bir siparişin durumunu "işlem sürüyor" iken "ücretli" veya "sevk edildi" olarak değiştirmeniz durumunda olur:

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

Bazı geliştiriciler, Kullanıcı arabirimi istek nesnelerini kendi komut DTOs dışında, ancak bu yalnızca tercihlerden ayrı hale getirir. Bu, çok fazla eklenen değer olmadan sıkıcı bir ayırdır ve nesneler neredeyse tam olarak aynı şekildir. Örneğin, eShopOnContainers 'da, bazı komutlar doğrudan istemci tarafından gelir.

### <a name="the-command-handler-class"></a>Komut Işleyici sınıfı

Her komut için belirli bir komut işleyici sınıfı uygulamalısınız. Bu, modelin nasıl çalıştığı ve komut nesnesini, etki alanı nesnelerini ve altyapı deposu nesnelerini kullanacağınız yerdir. Komut işleyici, CQRS ve DDD bakımından uygulama katmanının temelini bulgidir. Ancak, tüm etki alanı mantığının, toplama kökleri (kök varlıklar), alt varlıklar veya [etki alanı Hizmetleri](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)içindeki etki alanı sınıfları içinde olması gerekir, ancak uygulama katmanından bir sınıf olan komut işleyicisinde yer almalıdır.

Komut işleyici sınıfı, önceki bölümde bahsedilen tek sorumluluk Ilkesine (SRP) ulaşmak için bir güçlü atlama pulu sunar.

Komut işleyici bir komut alır ve kullanılan toplamanın bir sonucunu alır. Sonuç, komutun başarılı bir şekilde yürütülmesi ya da bir özel durum olmalıdır. Özel durum söz konusu olduğunda sistem durumu değişmeden olmalıdır.

Komut işleyici genellikle aşağıdaki adımları gerçekleştirir:

- Bir DTO ( [Mediator](https://en.wikipedia.org/wiki/Mediator_pattern) veya diğer altyapı nesnesinden) gibi komut nesnesini alır.

- Komutun geçerli olduğunu doğrular (Mediator tarafından doğrulanmamıştır).

- Geçerli komutun hedefi olan toplam kök örneğini başlatır.

- Komutu, komut dosyasından gerekli verileri alarak, toplu kök örneğinde yöntemini yürütür.

- Bu, toplamanın yeni durumunu ilgili veritabanına devam ettirir. Bu son işlem, gerçek işlemdir.

Genellikle, bir komut işleyicisi toplam köküne (kök varlık) göre tek bir toplama ile ilgilidir. Birden çok toplamalar tek bir komutun alınması tarafından etkileniyorsa, birden fazla toplama arasında durumları veya eylemleri yaymak için etki alanı olaylarını kullanabilirsiniz.

Buradaki önemli nokta, bir komut işlendiğinde, tüm etki alanı mantığının etki alanı modelinde (toplamalar), tam olarak kapsüllenmiş ve birim testi için hazır olması gerekir. Komut işleyici, model değiştirildiğinde altyapı katmanının (depolar) değişiklikleri kalıcı hale getirebileceği konusunda bilgi almak için, yalnızca veritabanından etki alanı modelini almanın ve son adımın bir yolu olarak davranır. Bu yaklaşımın avantajı, etki alanı mantığını bir yalıtılmış, tamamen Kapsüllenen, zengin, davranış etki alanı modelinde, uygulama veya altyapı katmanlarındaki kodu değiştirmeden, tesisat seviyesi (komut işleyicileri, Web API, depolar vb.).

Komut işleyicileri karmaşıktır, çok fazla Logic ile, bu bir kod kokusu olabilir. Bunları gözden geçirin ve etki alanı mantığını bulursanız, bu etki alanı davranışını etki alanı nesnelerinin yöntemlerine (Toplam kök ve alt varlık) taşımak için kodu yeniden düzenleyin.

Bir komut işleyici sınıfına örnek olarak aşağıdaki kod, bu bölümün başlangıcında gördüğünüz `CreateOrderCommandHandler` sınıfını gösterir. Bu durumda, tanıtıcı yöntemini ve etki alanı modeli nesneleri/toplamaları ile işlemleri vurgulamak istiyoruz.

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

Bunlar bir komut işleyicisinin gerçekleşmesi gereken ek adımlardır:

- Komut verilerini kullanarak toplam kökünün Yöntem ve davranışıyla birlikte işlem yapın.

- Etki alanı nesneleri içinde dahili olarak, işlem yürütüldüğü sırada etki alanı olaylarını yükseltir, ancak bu, bir komut işleyici noktasından saydamdır.

- Toplamanın işlem sonucu başarılı olursa ve işlem tamamlandıktan sonra, tümleştirme olaylarını yükseltin. (Bunlar ayrıca depolar gibi altyapı sınıfları tarafından da oluşturulabilir.)

#### <a name="additional-resources"></a>Ek kaynaklar

- **Seemann ' i işaretleyin. Sınırlar üzerinde uygulamalar nesne odaklı** \ değildir
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- @No__t **komutları ve olayları**-1
  <http://cqrs.nu/Faq/commands-and-events>

- **Komut işleyici ne yapar?** \
  <http://cqrs.nu/Faq/command-handlers>

- **Jimmy Bogard. Etki alanı komut desenleri – Işleyiciler** \
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- **Jimmy Bogard. Etki alanı komut desenleri – doğrulama** \
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Komut işlemi ardışık düzeni: komut işleyicisini tetikleme

Sonraki soru, bir komut işleyicisini çağırma. Her ilgili ASP.NET Core denetleyicisinden el ile çağırabilirsiniz. Ancak, bu yaklaşım çok fazla bağlanmış ve ideal değildir.

Önerilen Seçenekler olan diğer iki ana seçenek şunlardır:

- Bellek içi bir Mediator model yapıtı.

- , Denetleyiciler ve işleyiciler arasında zaman uyumsuz bir ileti kuyruğu ile.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Komut ardışık düzeninde Mediator düzenini (bellek içi) kullanın

Şekil 7-25 ' de gösterildiği gibi, bir CQRS yaklaşımında, bir bellek içi veri yoluna benzer şekilde akıllı bir Mediator kullanın. Bu, bir veya daha fazla alma işlemi için doğru komut işleyicisine yönlendirilmeye yetecek kadar akıllıdır. Bileşenler arasındaki tek siyah oklar, ilgili etkileşimlerine sahip nesneler arasındaki bağımlılıkları temsil eder (yani, dı üzerinden eklenen).

![Önceki görüntüden yakınlaştırma: ASP.NET Core denetleyicisi komutu MediatR 'nin komut işlem hattına gönderir, bu nedenle uygun işleyiciye alırlar.](./media/image22.png)

**Şekil 7-25**. Tek bir CQRS mikro hizmetindeki işlemdeki Mediator modelini kullanma

Mediator deseninin kullanılması, kurumsal uygulamalarda işleme isteklerinin karmaşık hale gelmesini sağlar. Günlüğe kaydetme, doğrulama, denetim ve güvenlik gibi çeşitli çapraz kesme sorunları ekleyebilmek istiyorsunuz. Bu durumlarda, bu ek davranışlar veya çapraz kesme sorunları için bir yol sağlamak üzere bir Mediator işlem hattına (bkz. [Mediator düzeni](https://en.wikipedia.org/wiki/Mediator_pattern)) güvenebilirsiniz.

Bir Mediator, bu işlemin "nasıl" olduğunu kapsülleyen bir nesnedir: durumu, bir komut işleyicisinin çağrılması ya da işleyiciye sağladığınız yük olarak, yürütme şeklini temel alarak düzenler. Bir Mediator bileşeni ile, dekoratörler (veya [mediaTR 3](https://www.nuget.org/packages/MediatR/3.0.0)' den beri işlem [hattı davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) ) uygulayarak merkezi ve saydam bir şekilde çapraz kesme sorunları uygulayabilirsiniz. Daha fazla bilgi için bkz. [dekoratör deseninin](https://en.wikipedia.org/wiki/Decorator_pattern).

Dekoratörler ve davranışlar, yalnızca Mediator bileşeni tarafından yönetilen belirli bir işlem ardışık düzenine uygulanan, [en boy Yönelimli Programlamaya (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)benzerdir. Çapraz kesme sorunları uygulayan AOP 'nin yönleri, derleme zamanında eklenen veya nesne çağrı yakalaşmaya bağlı olan *en büyük hava* alanları temelinde uygulanır. Tipik AOP yaklaşımları bazen "Magic" gibi çalışarak, ne kadar AOP 'nin çalıştığını görmek çok kolay. Ciddi sorunlar veya hatalarla ilgilenirken, AOP 'nin hata ayıklaması zor olabilir. Öte yandan, bu dekoratörler/davranışlar açık ve yalnızca ortalama bağlamında uygulandı, bu nedenle hata ayıklama çok daha öngörülebilir ve kolaydır.

Örneğin, eShopOnContainers sıralama mikro hizmetinde, iki örnek davranış, bir [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı ve [validatorbehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) sınıfı uyguladık. Davranışların uygulanması, eShopOnContainers 'ın [mediaTR 3](https://www.nuget.org/packages/MediatR/3.0.0) [davranışlarını](https://github.com/jbogard/MediatR/wiki/Behaviors)nasıl kullandığını gösteren bir sonraki bölümde açıklanmaktadır.

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Komutun ardışık düzeninde ileti kuyruklarını (proc dışı) kullanın

Şekil 7-26 ' de gösterildiği gibi, aracılar veya ileti kuyrukları temelinde zaman uyumsuz iletileri kullanmak başka bir seçenektir. Bu seçenek, komut işleyicisinden önce Mediator bileşeniyle de birleştirilebilir.

![Komutun işlem hattı, komutları uygun işleyiciye teslim etmek için yüksek oranda kullanılabilir bir ileti kuyruğu tarafından da işlenebilir.](./media/image23.png)

**Şekil 7-26**. CQRS komutlarıyla ileti kuyruklarını (işlem dışı ve işlem arası iletişim) kullanma

Komutları kabul etmek için ileti sıralarının kullanılması, büyük olasılıkla bir işlem hattını dış ileti kuyruğu aracılığıyla bağlı iki işleme bölmeniz gerekeceğinden, komutunuzun işlem hattını daha karmaşıklaştırır. Hala, zaman uyumsuz mesajlaşma temelinde geliştirilmiş ölçeklenebilirlik ve performansa sahip olmanız gerekiyorsa kullanılmalıdır. Şekil 7-26 olması durumunda denetleyicinin yalnızca komut iletisini sıraya gönderse ve döndürdüğü göz önünde bulundurun. Ardından komut işleyicileri iletileri kendi hızlarında işler. Kuyrukların harika bir avantajı vardır: ileti kuyruğu, Örneğin hisse senetleri veya yüksek hacimme verileri içeren başka senaryolar gibi, Hyper ölçeklenebilirlik gerektiğinde bir arabellek görevi görebilir.

Ancak, ileti sıralarının zaman uyumsuz doğası nedeniyle, komut işleminin başarısı veya başarısızlığı hakkında istemci uygulamayla nasıl iletişim kuracağınızı belirlemeniz gerekir. Kural olarak, "yangın ve unut" komutlarını asla kullanmamalısınız. Her iş uygulamasının, bir komutun başarıyla işlenip işlenmediğini veya en azından doğrulanıp kabul edildiğini bilmeleri gerekir.

Bu nedenle, zaman uyumsuz bir kuyruğa gönderilen bir komut iletisi doğrulandıktan sonra istemciye yanıt vermek, işlemi çalıştırdıktan sonra işlemin sonucunu döndüren işlem içi bir komut işlemiyle karşılaştırıldığında sisteminize karmaşıklık ekler. Kuyrukları kullanarak, sisteminizde ek bileşenler ve özel iletişim gerektiren diğer işlem sonuç iletileri aracılığıyla komut işleminin sonucunu döndürmeyebilirsiniz.

Ayrıca, zaman uyumsuz komutlar tek yönlü bir komutlardır. Bu, bir [çevrimiçi konuşmada](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ)Burtsev Alexey ve Greg başak arasında aşağıdaki ilginç alışverişte açıklandığı gibi, birçok durumda gerekli olmayabilir:

> \[Burtsev Alexey @ no__t-1 çok sayıda kod buldum. bu nedenle, kişilerin zaman uyumsuz komut işleme veya tek yönlü komut iletileri kullanması gerekir (bunlar uzun bir işlem yapılmazlar, bunlar dışarıdan zaman uyumsuz kod yürütülerek, bu uygulamalar bile çapraz uygulama değildir ileti veri yolu kullanımı sınırı). Bu gereksiz karmaşıklığa neden tanıtılsın? Aslında, şu ana kadar çok sayıda durumda çalışacak şekilde komut işleyicilerini engelleyen bir CQRS kod örneği görmedim.
>
> \[Greg başak @ no__t-1 \[... \] zaman uyumsuz bir komut yok; Bu aslında başka bir olaydır. Bana gönderdiklerinizi kabul etmem ve bir olayı nasıl yapacağımı kabul eterdiğimde, artık @no__t bir şey yapmamızı söyledim. Bu, @ no__t-1 komutu değildir. Bir şey yapıldığını söylemiş olursunuz. Bu, ilk başta küçük bir farklılık gibi görünüyor, ancak birçok etkileri vardır.

Zaman uyumsuz komutlar, hataların belirtmenin basit bir yolu olmadığından, sistemin karmaşıklığını büyük ölçüde artırır. Bu nedenle, zaman uyumsuz komutlar, ölçekleme gereksinimlerinin gerekli olduğu durumlar dışında veya iç mikro hizmetleri mesajlaşma yoluyla iletişim kurarken özel durumlarda önerilmez. Bu durumlarda, hatalara yönelik ayrı bir raporlama ve kurtarma sistemi tasarlamanız gerekir.

EShopOnContainers 'un ilk sürümünde, HTTP isteklerinden başlatılan ve Mediator deseninin yönettiği zaman uyumlu komut işlemeyi kullanmaya karar verdik. Bu, [Createordercommandhandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) uygulamasında olduğu gibi işlemin başarısını veya başarısızlığını kolayca döndürbırakmanıza olanak tanır.

Herhangi bir durumda bu, uygulamanızın veya mikro hizmetin iş gereksinimlerine bağlı olarak bir karar olmalıdır.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Komut işlem ardışık düzenini bir Mediator düzeniyle (MediatR) uygulama

Örnek bir uygulama olarak, bu kılavuz, komut alımı ve yönlendirme komutlarının, doğru komut işleyicileriyle bir şekilde kullanılması için Mediator düzenine göre işlem içi ardışık düzeni kullanmayı önerir. Kılavuz, ayrıca çapraz kesme sorunlarını ayırmak için [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) uygulamayı önerir.

.NET Core 'da uygulama için, ortalama modelini uygulayan birden çok açık kaynak kitaplığı mevcuttur. Bu kılavuzda kullanılan kitaplık, [Ortaatr](https://github.com/jbogard/MediatR) açık kaynak kitaplığıdır (cemy Bogard tarafından oluşturulmuştur), ancak başka bir yaklaşım kullanabilirsiniz. MediatR, dekoratörler veya davranışlar uygulanırken, bir komut gibi bellek içi iletileri işlemenize olanak tanıyan küçük ve basit bir kitaplıktır.

Mediator deseninin kullanılması, bağlantıyı azaltmanıza ve istenen çalışmanın kaygılarını yalıtmanıza yardımcı olur ve bu durumda, bu çalışmayı gerçekleştiren işleyiciye otomatik olarak (Bu örnekte, komut işleyicilerine) bağlantı kurar.

Mediator deseninin kullanılması için başka bir neden, bu kılavuzu gözden geçirirken cemy Bogard tarafından açıklanmıştı:

> Burada test etmeyi düşünüyordum. sisteminizin davranışına yönelik iyi bir tutarlı pencere sağlar. İstek, yanıt verme. Bu en boy, düzenli olarak davranmakta olan testlerin oluşturulmasına oldukça değerlidir.

İlk olarak, yalnızca Mediator nesnesini kullanacağınız örnek bir WebAPI denetleyicisine göz atalım. Mediator nesnesini kullanmıyorsanız, bu denetleyiciye yönelik tüm bağımlılıkları, bir günlükçü nesnesi ve diğerleri gibi öğeleri eklemeniz gerekir. Bu nedenle, Oluşturucu oldukça karmaşıktır. Diğer taraftan, Mediator nesnesini kullanırsanız, aşağıdaki örnekte olduğu gibi, her bir çapraz kesme işlemi için bir tane olmak üzere yalnızca birkaç bağımlılıkda olmak üzere denetleyicinizin Oluşturucusu çok daha basit olabilir.

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

Mediator 'ın temiz ve yalın bir Web API denetleyici Oluşturucusu sağladığını görebilirsiniz. Ayrıca, denetleyici yöntemleri içinde Mediator nesnesine bir komut göndermek için kod neredeyse bir satırdır:

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

### <a name="implement-idempotent-commands"></a>Idempotent komutlarını Uygula

**Eshoponcontainers**'da, yukarıdaki sayıdan daha gelişmiş bir örnek, sıralama mikro hizmetinden CreateOrderCommand nesnesi gönderiliyor. Ancak, sipariş iş süreci biraz daha karmaşıktır ve bizim örneğimizde, aslında sepet mikro hizmetinde başlatılır, CreateOrderCommand nesnesini gönderme eylemi, adlı [bir tümleştirme olay işleyiciden gerçekleştirilir. ](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs)Önceki daha basit örnekte olduğu gibi, istemci uygulamasından çağrılan basit bir WebAPI denetleyicisi yerine Usercheckoutacceptedıntegrationevent.

Bununla birlikte, aşağıdaki kodda gösterildiği gibi, komutunu MediatR 'ye gönderme eylemi oldukça benzerdir.

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

Bununla birlikte, Ayrıca, ıdempotent komutlarını da uygulamamız gerektiğinden, bu durum biraz daha gelişmiş bir bittir. CreateOrderCommand işleminin ıdempotent olması gerekir, bu nedenle aynı ileti ağ üzerinden yinelenirse, yeniden denemeler gibi her nedenden dolayı aynı iş siparişi yalnızca bir kez işlenecektir.

Bu, iş komutu sarmalanarak (Bu durumda CreateOrderCommand) ve ıdempotent olması gereken ağ üzerinden gelen her iletinin KIMLIĞI tarafından izlenen genel bir IdentifiedCommand gömülerek uygulanır.

Aşağıdaki kodda, IdentifiedCommand ile bir DTO 'ın ve KIMLIĞI artı sarmalanmış iş komut nesnesinden daha fazla şey olmadığını görebilirsiniz.

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

Daha sonra, [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) adlı IdentifiedCommand Için CommandHandler, iletinin bir parçası olarak gelen kimliğin bir tabloda zaten mevcut olup olmadığını denetler. Zaten varsa, bu komut yeniden işlenmeyecek, bu nedenle bir ıdempotent komutu olarak davranır. Bu altyapı kodu, aşağıdaki `_requestManager.ExistAsync` Yöntem çağrısı tarafından gerçekleştirilir.

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

IdentifiedCommand, bir iş komutunun zarfı gibi davrandığı için, tekrarlanmış bir kimlik olmadığından iş komutunun işlenmesi gerektiğinde, bu iç iş komutunu alır ve yukarıda gösterilen kodun en son bölümünde olduğu gibi bu iç iş komutunu yeniden gönderir. `_mediator.Send(message.Command)`, [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs)üzerinden çalıştırılıyor.

Bunu yaparken, aşağıdaki kodda gösterildiği gibi, işlem veritabanına karşı işlemleri çalıştıran [Createordercommandhandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) olan bu örnekte iş komut işleyicisini bağlar ve çalıştırır.

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

MediatR 'nin komut işleyici sınıflarınızın farkında olması için, IBC sınıflarını ve komut işleyici sınıflarını IOC kapsayıcısına kaydetmeniz gerekir. Varsayılan olarak, MediatR, IOC kapsayıcısı olarak Autofac kullanır, ancak yerleşik ASP.NET Core IOC kapsayıcısını veya MediatR tarafından desteklenen başka bir kapsayıcıyı de kullanabilirsiniz.

Aşağıdaki kod, Autofac modülleri kullanılırken Mediator 'ın türlerin ve komutlarının nasıl kaydedileceği gösterilmektedir.

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

Bu, MediatR ile "sihirli olur" dır.

Her komut işleyicisi genel `IAsyncRequestHandler<T>` arabirimini uyguladığı için, derlemeleri kaydederken, kod, `CommandHandlers` ' i `Commands` ile ilişkilendirerek `IAsyncRequestHandler` olarak işaretlenen tüm türler `RegisteredAssemblyTypes` ile kaydedilir, `CommandHandler` sınıfı, aşağıdaki örnekte olduğu gibi:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Komutları komut işleyicileriyle ilişkilendiren koddur. İşleyici sadece basit bir sınıftır, ancak T `RequestHandler<T>` ' dan devralır, burada T, komut türüdür ve MediatR, doğru yük (komut) ile çağrıldığından emin olur.

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>MediatR 'deki davranışlar ile komutları işlerken çapraz kesme sorunları uygulayın

Bir şey daha vardır: ortalama işlem hattına çapraz kesme sorunları uygulayabiliyor. Ayrıca, Autofac kayıt modülü kodunun sonunda, özel bir LoggingBehavior sınıfı ve bir ValidatorBehavior sınıfı olarak bir davranış türü nasıl kaydedeceğini de görebilirsiniz. Ancak başka özel davranışlar da ekleyebilirsiniz.

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

Bu [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) sınıfı, yürütülen komut işleyicisiyle ilgili bilgileri ve başarılı olup olmadığını günlüğe kaydeden aşağıdaki kod olarak uygulanabilir.

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

Yalnızca bu davranış sınıfını uygulayarak ve bunu işlem hattına kaydederek (yukarıdaki MediatorModule), MediatR aracılığıyla işlenen tüm komutlar yürütme hakkında bilgi günlüğe alınacaktır.

EShopOnContainers sıralama mikro hizmeti Ayrıca, aşağıdaki kodda gösterildiği gibi, [akıcı bir doğrulama](https://github.com/JeremySkinner/FluentValidation) kitaplığına dayanan [validatorbehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) sınıfı temel doğrulamalar için ikinci bir davranış uygular:

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

Buradaki davranış, doğrulama başarısız olursa bir özel durum ortaya koyar, ancak başarılı olursa komut sonucunu içeren bir sonuç nesnesi de döndürebilir. Bu, büyük olasılıkla kullanıcıya doğrulama sonuçlarının görüntülenmesini kolaylaştırır.

Daha sonra, akıcı bir [doğrulama](https://github.com/JeremySkinner/FluentValidation) kitaplığına bağlı olarak, aşağıdaki kodda olduğu gibi CreateOrderCommand ile geçirilen veriler için doğrulama oluşturduk:

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

Ek doğrulamalar oluşturabilirsiniz. Bu, komut doğrulamalarınızı uygulamak için çok temiz ve zarif bir yoldur.

Benzer bir şekilde, bunları işlerken komutlara uygulamak istediğiniz ek yönleri veya çapraz kesme sorunları için diğer davranışları uygulayabilirsiniz.

#### <a name="additional-resources"></a>Ek kaynaklar

##### <a name="the-mediator-pattern"></a>Mediator deseninin

- **Mediator deseninin** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Dekoratör deseninin

- **Dekoratör deseninin** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

- **MediatR.** GitHub deposu. \
  <https://github.com/jbogard/MediatR>

- **MediatR ve Automaber  \ Ile CQRS**
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- **Denetleyicilerinizi bir diet: gönderi ve komutlara yerleştirin.** \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- **Bir Mediator işlem hattı Ile çıkış çapraz kesme sorunları**-1 @no__t
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- **CQRS ve Rest: kusursuz eşleşme** \
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- **MediaTR Işlem hattı örnekleri** \
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- **MediatR ve ASP.NET Core @no__t Için dikey dilim test armatürleri**-1
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- **Microsoft bağımlılık ekleme Için mediaTR uzantıları @no__t yayınlandı**-1
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a>Akıcı doğrulama

- **Jeremy SKINNER. Floentvalidation.** GitHub deposu. \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> [Önceki](microservice-application-layer-web-api-design.md)
> [İleri](../implement-resilient-applications/index.md)
