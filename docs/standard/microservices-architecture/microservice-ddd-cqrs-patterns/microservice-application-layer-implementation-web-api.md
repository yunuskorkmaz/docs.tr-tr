---
title: "Mikro hizmet uygulama katmanı Web API kullanarak uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet uygulama katmanı Web API kullanarak uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a>Mikro hizmet uygulama katmanı Web API kullanarak uygulama

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Uygulama katmana altyapı nesnelerinden eklemesine bağımlılık ekleme kullanılarak

Daha önce belirtildiği gibi uygulama katmanı oluşturduğunuz, örneğin bir Web API projesi veya bir MVC web uygulaması projesi olarak içinde yapının parçası olarak uygulanabilir. ASP.NET Core ile yerleşik bir mikro hizmet söz konusu olduğunda, uygulama katmanı Web API kitaplığınızın genellikle olacaktır. ASP.NET Core (alt yapısına artı denetleyicilerinizi) özel uygulama katman kodunuzdan yakında ayırmak istiyorsanız, uygulama katmanı ayrı Sınıf Kitaplığı'nda koyabilir, ancak isteğe bağlıdır.

Örneğin, uygulama katmanı kodunu sıralama mikro hizmet parçası olarak doğrudan uygulanır **Ordering.API** proje (bir ASP.NET çekirdek Web API projesi) olarak gösterildiği Şekil 9-19.

![](./media/image20.png)

**Şekil 9-19**. Uygulama katmanı Ordering.API ASP.NET çekirdek Web API projesi '

ASP.NET Core içeren basit bir [yerleşik IOC kapsayıcı](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (IServiceProvider arabirimi tarafından temsil edilen) Oluşturucu ekleme varsayılan destekleyen ve ASP.NET belirli hizmetleri dı aracılığıyla kullanılabilir yapar. ASP.NET Core kullanan terimi *hizmet* dı eklenecek kaydettiğiniz türlerinden herhangi birini için. Yerleşik kapsayıcının Hizmetleri, uygulamanızın başlangıç sınıfı ConfigureServices yönteminde yapılandırın. Bağımlılıklarınız türü gerektiren hizmetlere uygulanır.

Tipik olarak, altyapı nesnelerinden uygulama bağımlılıkları ekleme istersiniz. Eklemesine oldukça tipik bir bağımlılık bir depodur. Ancak, yaptığınız herhangi bir altyapı Bağımlılığı Ekle. DBContext altyapı Kalıcılık nesnelerinizi uyarlamasını de olduğundan daha basit uygulamalar için doğrudan iş birimi düzeni nesnenizin (EF DbContext nesnesi) ekleyebilir.

Aşağıdaki örnekte, .NET Core Oluşturucusu gerekli depo nesnelerde nasıl injecting görebilirsiniz. Sonraki bölümde ele alınacaktır bir komut işleyici sınıftır.

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

İşlem yürütme ve durum değişiklikleri kalıcı hale getirmek için eklenen depoları sınıfını kullanır. Bu sınıf bir komut işleyici, bir ASP.NET çekirdek Web API denetleyicisi yöntemi olup olmadığını veya önemli değildir [DDD uygulama hizmeti](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Sonuç olarak, bir komut işleyici benzer bir şekilde depoları, etki alanı varlıkları ve diğer uygulama koordinasyon kullanan basit bir sınıf değil. Tüm sözü edilen sınıflar dı kullanarak örnekte olduğu gibi aynı şekilde Oluşturucu tabanlı bağımlılık ekleme çalışır.

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Bağımlılık uygulama türleri ve arabirimleri veya soyutlamalar kaydetme

Oluşturucular eklenen nesneleri kullanmadan önce arabirimleri ve uygulama sınıflarınızı dı aracılığıyla içine eklenen nesneleri üretmek sınıfları kaydedileceği yeri bilmeniz gerekir. (Dı gibi temel oluşturucu, daha önce gösterildiği gibi.)

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a>ASP.NET Core tarafından sağlanan yerleşik IOC kapsayıcı kullanma

ASP.NET Core tarafından sağlanan yerleşik IOC kapsayıcı kullandığınızda, aşağıdaki kod olduğu gibi haline dosyasındaki ConfigureServices yöntemi Ekle istediğiniz türlerini kaydedin:

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

En yaygın düzeni IOC kapsayıcısında türlerini kaydetme türleri çifti kaydetmek için olduğunda — bir arabirim ve onun ilişkili uygulama sınıfı. Ardından herhangi Oluşturucusu aracılığıyla IOC kapsayıcısından bir nesne istediğinde, belirli bir arabirim türünde bir nesne isteyin. Örneği için oluşturucular herhangi bir bağımlılık IMyCustomRepository (arabirimi veya soyutlama) varsa, IOC kapsayıcı MyCustomSQLServerRepository uygulama örneğini ekleme, önceki örnekte, son satır durumları sınıf.

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a>Otomatik türleri kaydı için Scrutor kitaplığı kullanma

DI .NET Core kullanırken, bir derlemeyi tarayın ve türlerinden kurala göre otomatik olarak kaydetmek isteyebilirsiniz. ASP.NET Core bu özellik şu anda kullanılamıyor. Ancak, kullanabileceğiniz [Scrutor](https://github.com/khellang/Scrutor) kitaplığı konusu. IOC kapsayıcısında kayıtlı olması gereken türleri düzinelerce olduğunda bu kullanışlı bir yaklaşımdır.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Matthew Kol. Hizmetleri ile Scrutor kaydediliyor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)

<!-- -->

-   **Kristian Hellang. Scrutor.** GitHub depo.
    [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a>Autofac IOC kapsayıcı olarak kullanma

Ayrıca ek IOC kapsayıcılar kullanma ve sıralama mikro hizmet kullanan eShopOnContainers içinde olduğu gibi ASP.NET Core kanalının takın [Autofac](https://autofac.org/). Autofac kullanırken, genellikle kayıt türleri arasında birden fazla sınıf kitaplıkları dağıtılmış uygulama türleri sahip olduğunuz, türlerinizi nerede olduğunuza bağlı olarak birden çok dosya arasında bölmek izin modülleri aracılığıyla türleri kaydedin.

Örneğin, aşağıdaki gibidir [Autofac uygulama modülü](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) için [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) eklemesine istediğiniz türleriyle projesi.

```csharp
public class ApplicationModule
    :Autofac.Module
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

Kavramları ve kayıt işlemine çok benzer şekilde, yerleşik ASP.NET Core iOS kapsayıcıyla türleri kaydedebilirsiniz, ancak Autofac kullanırken sözdizimi biraz farklıdır.

Örnek kodda IOrderRepository soyutlama uygulama sınıfı OrderRepository birlikte kaydedilir. Bu, bağımlılık IOrderRepository soyutlama veya arabirimi aracılığıyla bir kurucusu bildirme her IOC kapsayıcı OrderRepository sınıfının bir örneğini ekleme anlamına gelir.

Bir örneği aynı hizmet veya bağımlılık istekler arasında nasıl paylaşılacağını örneği kapsam türü belirler. Bir istek için bağımlılık yapıldığında IOC kapsayıcı aşağıdaki döndürebilirsiniz:

-   Ömür kapsam başına tek bir örnek (ASP.NET Core IOC kapsayıcı olarak başvurulan *kapsamlı*).

-   Yeni bir örneğini bağımlılık başına (ASP.NET Core IOC kapsayıcı olarak başvurulan *geçici*).

-   IOC kapsayıcı kullanan tüm nesneler arasında paylaşılan tek bir örnek (ASP.NET Core IOC kapsayıcı olarak başvurulan *singleton*).

#### <a name="additional-resources"></a>Ek kaynaklar

-   **ASP.NET Core bağımlılık ekleme giriş**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

-   **Autofac.** Resmi belge.
    [*http://docs.autofac.org/en/Latest/*](http://docs.autofac.org/en/latest/)

-   **Cesar de la Torre. ASP.NET Core IOC kapsayıcı hizmeti ömürleri Autofac IOC kapsayıcı örneği kapsamlarla karşılaştırma**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ comparing-ASP-NET-Core-ioc-Service-Life-Times-and-autofac-ioc-instance-Scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implementing-the-command-and-command-handler-patterns"></a>Komut ve komut işleyici desenleri uygulama

Önceki bölümde gösterilen Oluşturucusu aracılığıyla dı örnekte IOC kapsayıcı bir sınıf oluşturucuda aracılığıyla depoları injecting oluştu. Ancak, tam olarak burada bunlar eklenmiş? Bir basit Web API'si (örneğin, katalog mikro hizmet eShopOnContainers içinde), siz bunları MVC denetleyicileri düzeyinde bir denetleyici Oluşturucu yerleştirir. Bu bölümde, ancak ilk kodda ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) eShopOnContainers Ordering.API hizmetinde sınıfından), bağımlılıklar ekleme belirli bir komut oluşturucu kullanılarak yapılır işleyici. Bize açıklayan bir komut işleyici ne olduğunu ve neden bunu kullanmak isteyebilirsiniz.

Komut düzeni, bu kılavuzun önceki bölümlerinde sunulan CQRS düzeni doğası gereği ilgilidir. CQRS iki kenara sahiptir. Basitleştirilmiş sorgularıyla kullanarak sorguları, ilk alanıdır [Dapper](https://github.com/StackExchange/dapper-dot-net) daha önce açıklanan mikro ORM. İşlemler için başlangıç noktası ve giriş kanaldan hizmetin dışında olan komutları ikinci bir alandır.

Şekil 9-20'de gösterildiği gibi düzeni istemci tarafında, komutları kabul dayalıdır etki alanı modeli kurallara göre işlemeden ve son olarak durumları işlemleri ile kalıcı yapma.

![](./media/image21.png)

**Şekil 9-20**. Komutları veya CQRS desende "işlem yan" üst düzey görünümü

### <a name="the-command-class"></a>Komut sınıfı

Sistem durumunu değiştiren bir eylem gerçekleştirmek üzere sistem için bir istek komuttur. Komutlar, kesinlik temelli ve yalnızca bir kez işlenmesi.

Komutları imperatives olduğundan, bunlar genellikle bir fiil kesinlik temelli ruh (örneğin, "oluşturma" veya "güncelleştir") olarak adlandırılır ve CreateOrderCommand gibi toplama türü içerebilir. Bir olay, bir komut bir olgu Geçmişten değil; yalnızca bir istek ve böylece reddetti.

İşlem Yöneticisi'ni bir eylemi gerçekleştirmek için bir toplama yönlendirerek, komutları bir isteği başlatan kullanıcı sonucunda UI veya bir işlem yöneticisi kaynaklanan.

Bir önemli bir komutu tek bir alıcı tarafından yalnızca bir kez işlenmesi gerektiğini özelliğidir. Bir komut tek eylem veya uygulamada gerçekleştirmek istediğiniz işlem olmasıdır. Örneğin, aynı sırası oluşturma komutunu birden çok kez işlenmesi gerektiğini değil. Komutlar ve olayları arasında önemli bir fark budur. Birçok sistemleri veya mikro olayda ilgileniyor çünkü olayları birden çok kez işlenebilir.

Ayrıca, komut ıdempotent kullanılamaz durumda olduğunda bir komutu yalnızca bir kez işlenmesi önemlidir. Birden çok kez sonucu komut yapısını nedeniyle veya sistem komut işleme biçimi nedeniyle değiştirmeden yürütülmek üzere ise bir komut ıdempotent olur.

Komutlarınızı yapmak için iyi bir uygulamadır ve etki alanınızın iş kuralları ve invariants altında mantıklıdır ıdempotent güncelleştirir. Örneğin, herhangi bir nedenle (yeniden deneme mantığı, korsan, vb.), sisteminizi birden çok kez aynı CreateOrder komutu ulaşırsa aynı örneği kullanmak için tanımlamak ve birden çok sipariş oluşturmayın sağlamak mümkün olması gerekir. Bunu yapmak için bir tür kimlik işlemlerinin ekleme ve komut veya güncelleştirme işlenmiş olup olmadığını belirlemeniz gerekir.

Tek bir alıcı bir komut Gönder; bir komut yayımlamayın. Yayımlama olan bir olgu durum tümleştirme olaylarını — bir şey gerçekleştirilmedi ve olabilir Olay alıcıları için ilginç. Olayları söz konusu olduğunda, publisher hakkında olay veya bunların yerine getirebileceği alıcıları almak hiçbir sorunları vardır. Ancak zaten önceki bölümlerinde sunulan farklı bir öykü tümleştirme olaylardır.

Bir komut, veri alanları veya koleksiyonları bu komutu yürütmek için gerekli tüm bilgileri içeren bir sınıf ile uygulanır. Özel bir tür, veri aktarım nesnesini (DTO), özellikle istek değişiklikleri veya işlemleri için kullanılan bir komuttur. Komutu tam olarak komut ve hiçbir şey daha fazla işlemek için gerekli bilgileri temel alır.

Aşağıdaki örnek, Basitleştirilmiş CreateOrderCommand sınıfı gösterir. Bu sipariş mikro hizmet eShopOnContainers içinde kullanılan sabit bir komuttur.

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
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

Temel olarak, komut sınıfı etki alanı model nesneleri kullanarak bir iş işlemi gerçekleştirmek için gereken tüm verileri içerir. Bu nedenle, yalnızca salt okunur veri ve davranışı yok içeren veri yapılarını komutlardır. Komut adını amacını gösterir. C gibi birden çok dilde\#, komutları sınıfları olarak temsil, ancak bunlar gerçek nesne yönelimli algılama true sınıflarda değildir.

Beklenen kullanım doğrudan etki alanı modeli tarafından işlenen olduğundan ek bir özellik komutları, sabittir. Kendi tahmini ömrü boyunca değiştirmek gerekmez. Bir c\# sınıfı, girişi elde edilebilir herhangi ayarlayıcılar veya iç durum değişikliği diğer yöntemleri zorunluluğunu ortadan kaldırarak.

Örneğin, bir sıra oluşturmak için komut sınıfı oluşturmak istediğiniz sipariş veri açısından büyük olasılıkla benzer, ancak aynı öznitelikleri muhtemelen gerekmez. Örneği için CreateOrderCommand sırasını henüz oluşturulmadı çünkü bir sıra kimliği yok.

Birçok komut sınıfları basit, yalnızca birkaç alanları değiştirilmesi gereken bazı durumu hakkında gerektiren olabilir. Bu durumda, "işlem" için bir sıra durumunu yalnızca değiştiriyorsanız "Ücretli" veya "aşağıdakine benzer bir komut kullanarak sevk edilen" olacaktır:

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

Bazı geliştiriciler kendi kullanıcı Arabirimi isteği nesneleri kendi komut DTOs ayrı yapın, ancak sağlasa da, yalnızca tercih olmasıdır. Can sıkıcı ayrımı konuya eklenen değerine sahip olan ve neredeyse tam olarak aynı şekilde nesneleridir. Örneğin, eShopOnContainers komutları doğrudan istemci tarafındaki gelir.

### <a name="the-command-handler-class"></a>Komut işleyici sınıfı

Her komut için bir özel bir komut işleyici sınıfı uygulamanız gerekir. Düzeni nasıl çalıştığını ve burada komut nesnesi, etki alanı nesnelerini ve altyapı depo nesneleri kullanacağı adrestir. Komut gerçekte CQRS ve DDD açısından uygulama katmanı Kalp işleyicidir. Ancak, tüm etki alanı mantığı içinde yer alan etki alanı sınıfları yer almalıdır — toplama kökleri (kök varlıklar) içinde alt varlıkları veya [etki alanı Hizmetleri](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ancak komut işleyici değil içinde olduğu uygulamadan sınıfı katmanı.

Bir komut işleyici komutu alır ve bir sonuç kullanılan toplam değer alır. Sonuç, komutun başarılı yürütme ya da bir özel durum olmalıdır. Bir özel durum söz konusu olduğunda sistem durumu değiştirilmeden olmalıdır.

Komut işleyici genellikle aşağıdaki adımları gerçekleştirir:

-   Komut nesnesi bir DTO gibi alır (gelen [Dünyası](https://en.wikipedia.org/wiki/Mediator_pattern) veya başka bir altyapı nesne).

-   Bu komutu (Dünyası tarafından doğrulanmamış varsa) geçerli olduğunu doğrular.

-   Geçerli komut hedefi olan birleşik kök örneği başlatır.

-   Komuttan gerekli verileri alma toplama kök örneğinde yöntemini yürütür.

-   Bu toplama, ilgili veritabanı için yeni durumu devam ettirir. Bu son işlem gerçek bir işlemdir.

Genellikle, bir komut işleyici toplama kökü (kök varlık) tarafından yönetilen tek bir toplama ile ilgilidir. Birden çok toplamalar tek bir komut alma tarafından etkilenir, durumları veya eylemler arasında birden çok toplamalar yaymak için etki alanı olayları kullanabilirsiniz

Burada önemli olan nokta, bir komut işlenirken, tüm etki alanı mantığı etki alanı model içinde (toplamalar) tam olarak kapsüllenmiş ve birim testi için hazır olması gerektiğini ' dir. Komut işleyici yalnızca etki alanı modeli veritabanından almanın bir yolu olarak ve model değiştirildiğinde değişiklikleri kalıcı hale getirmek için altyapı katman (depoları) bildirmek için son adımı olarak davranır. Bu yaklaşımın avantajı uygulama veya tesisat düzeyi (komut işleyicileri, Web API altyapı Katmanlar kodunu değiştirmeden bir yalıtılmış, tam olarak kapsüllenmiş, zengin, davranış etki alanı modelinde etki alanı mantığı yeniden emin olan depoları, vb.).

Komut işleyicileri çok fazla mantığı ile karmaşık aldığınızda, kod kokusu olabilir. Bunları gözden geçirin ve etki alanı mantığı bulursanız, o etki alanı davranışı etki alanı nesnelerini (Birleşik kök ve alt varlık) yöntemlerinin taşımak için kodu yeniden düzenleyin.

Bir komut işleyici sınıfın örnek olarak, aşağıdaki kod bu bölümün başında gördüğünüz aynı CreateOrderCommandHandler sınıfı gösterir. Bu durumda biz tanıtıcı yöntem ve etki alanı model nesneleri/toplamalar işlemleriyle vurguladığınız.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

Bir komut işleyici gerçekleştirmeniz ek adımlar şunlardır:

-   Komutunun veri toplama kökün yöntemleri ve davranış ile çalışması için kullanın.

-   Dahili olarak etki alanı nesnelerinde işlem yürütülür, ancak bir komut işleyici açısından saydam olan etki alanı olayları yükseltin.

-   Toplama 's işlem sonucu başarılı olursa ve işlem tamamlandıktan sonra tümleştirme olayları komut işleyici yükseltin. (Bu da depoları gibi altyapı sınıflar tarafından oluşturulması.)

#### <a name="additional-resources"></a>Ek kaynaklar

-   **İşareti Seemann. Değil nesne odaklı uygulamalar sınırlarında**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, ApplicationsareNotObject odaklı /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

-   **Komutlar ve olayları**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

-   **Bir komut işleyici ne yapar? ** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

-   **Jimmy Bogard. Etki alanı komutu desenleri – işleyicileri**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

-   **Jimmy Bogard. Etki alanı komutu desenleri – doğrulama**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Komut işlemi ardışık: bir komut işleyici tetikleme

Sonraki Soru bir komut işleyici çağırma şeklidir. El ile ilgili her ASP.NET Core denetleyicisinden çağırabilirsiniz. Ancak, bir yaklaşım çok olacaktır eşleşmiş ve ideal değil.

Önerilen seçenek olan diğer iki ana seçenekleri şunlardır:

-   Bellek içi Dünyası düzeni yapı.

-   Bir zaman uyumsuz ileti sırası ile denetleyicileri ve işleyicileri Between.

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Komut ardışık düzeninde Dünyası deseni (bellek içi) kullanma

Şekil 9-21'de gösterildiği gibi bir CQRS yaklaşım, komutun veya alınma DTO türüne göre sağ komut işleyici yeniden yönlendirmek akıllı bir bellek içi veri yoluna benzer akıllı bir Dünyası kullanın. Bileşenler arasındaki tek siyah oklar (dı eklenen çoğu durumda,) nesneler arasındaki bağımlılıkları ile ilgili kendi etkileşimleri temsil eder.

![](./media/image22.png)

**Şekil 9-21**. Tek bir CQRS mikro hizmet işleminde Dünyası desen kullanma

Kullanmakta Dünyası düzeni mantıklı Kurumsal uygulamalarda istekleri işlemek karmaşık alabilirsiniz nedenidir. Çapraz kesme sorunları günlüğe kaydetme, doğrulama, Denetim ve güvenlik gibi açık bir sayısı eklemek kullanabilmek ister. Bu durumlarda, bir Dünyası ardışık kullanır (bkz [Dünyası düzeni](https://en.wikipedia.org/wiki/Mediator_pattern)) bu ek davranışları veya çapraz kesme sorunları için bir yol sağlamak için.

"Nasıl" Bu işlemi yalıtan bir nesne bir Dünyası olduğu: durumuna bağlı yürütme koordinatları, bir komut işleyici yolu çağrılır ya da yük işleyicisine sağlayın. Dünyası bileşeniyle arası kesme sorunları merkezi ve saydam bir şekilde dekoratörler uygulayarak uygulayabilirsiniz (veya [kanal davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) Dünyası v3 itibaren). (Daha fazla bilgi için bkz: [oluşturma öğesi düzeni](https://en.wikipedia.org/wiki/Decorator_pattern).)

Dekoratörler ve davranışları benzer [en boy odaklı programlama (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)Dünyası bileşen tarafından yönetilen bir özel işlem ardışık düzene uygulanan yalnızca. Çapraz kesme sorunları uygulayan AOP yönlerine göre uygulanır *en boy weavers* nesne araması yakalanması temelinde ya da derleme zamanında eklenmiş. Nasıl AOP çalıştığını görmek kolay değildir çünkü her iki tipik AOP yaklaşım bazen "Sihirli gibi" iş söylenir. Önemli sorunları veya hatalar ile ilgilenirken, AOP hata ayıklaması zor olabilir. Öte yandan, hata ayıklama çok daha tahmin edilebilir ve kolay şekilde bu dekoratörler/davranışları açık ve yalnızca Dünyası bağlamında uygulandı.

Örneğin, mikro hizmet sıralama eShopOnContainers şu iki örnek dekoratörler uygulanan bir [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) sınıfı ve bir [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) sınıfı. Oluşturma öğesi'nin uygulama bir sonraki bölümde açıklanmıştır. İçin sonraki bir sürümde eShopOnContainers geçiş yapacağınız Not [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) ve gitme [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) dekoratörler kullanmak yerine.

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a>İleti kuyrukları (giden işlem dışı) komutunun ardışık düzeninde kullanma

Aracıların veya ileti kuyrukları, Şekil 9-22'de gösterildiği gibi göre zaman uyumsuz iletileri kullanan başka bir seçenektir. Bu seçenek ayrıca komut işleyici önceki Dünyası bileşeni ile birleştirilir.

![](./media/image23.png)

**Şekil 9-22**. İleti kuyrukları (dışında işlem ve işlemler arası iletişim) CQRS komutları ile kullanma

Ardışık düzen iki süreçleriyle bölme gerekecek çünkü komutları daha kabul edecek şekilde sıralar, komutunun ardışık düzen, karmaşık hale iletiyi kullanarak dış ileti sırası yoluyla bağlı. Yine de, ölçeklenebilirlik ve performans zaman uyumsuz Mesajlaşma göre iyileştirilmiştir ihtiyacınız varsa kullanılmalıdır. Şekil 9-22 durumunda göz önünde bulundurun, denetleyici yalnızca sıraya komutu ileti gönderir ve döndürür. Ardından komut işleyicileri kendi hızlarında iletileri işleyin. Diğer bir deyişle harika bir avantajı sıraların — hyper ölçeklenebilirlik gerekli, istediğiniz hisse veya herhangi bir giriş veri hacmi yüksek senaryoyla gibi olduğunda ileti sırası durumlarda bir arabellek olarak çalışabilir.

Ancak, zaman uyumsuz ileti kuyrukları yapısı nedeniyle, başarı veya başarısızlık komutunun işleminin hakkında istemci uygulamasıyla iletişim kurmak nasıl ekleneceğini gerekir. Bir kural olarak, hiçbir zaman "yangın ve unut" komutları kullanmanız gerekir. Her iş uygulamasının bir komutu başarıyla, işlenen veya en az doğrulandı ve kabul durumunda bilmesi gerekir.

Bu nedenle, bir zaman uyumsuz kuyruğa gönderilen bir komut iletisi doğrulandıktan sonra istemciye yanıt yapamamasına karmaşıklık işlem çalıştırdıktan sonra işlemin sonucunu döndürür bir işlemdeki komutu işlemi ile karşılaştırıldığında, sisteminizi ekler. Kuyrukları kullanma, ek bileşenleri ve özel iletişim sisteminizde gerektirecektir diğer işlem sonucu iletileri komutu sürecinde sonuç gerekebilir.

Ayrıca, zaman uyumsuz, çoğu durumda, aşağıdaki ilginç exchange Burtsev Alexey Greg Young arasındaki açıklandığı şekilde gerekebilecek değil tek yönlü komutları komutlardır bir [çevrimiçi konuşma](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

\[Burtsev Alexey\] burada kişiler zaman uyumsuz komut işleme veya bunu yapmak için herhangi bir nedenle Mesajlaşma tek yönlü komutunu kullanın kodu çok sayıda bulabilirim (bazı uzun işlemi yaptıklarını değil, dış zaman uyumsuz kod yürütme değil, bile uygulama geçmez ileti veri yolu kullanılmasını sınır). Neden bu gereksiz karmaşıklığı tanıtmak? Ve gerçekte, çoğu durumda düzgün çalışır ancak ı komut işleyicileri o ana kadarki engelleme ile CQRS kod örneği görmediyseniz.

\[Greg Young\] \[... \] zaman uyumsuz bir komutu yok; gerçekten başka bir olaydır. I ne bana gönderdiğiniz kabul ediyor ve kabul etmiyorum bir olay oluştur gerekir artık, bana bir şeyler belirten değildir. Bana bir şey bitti söyleyen olduğunu. Bu bir hafif fark ilk gibi görünüyor, ancak birçok etkilere sahiptir.

Hataları göstermek için basit bir yolu olduğundan zaman uyumsuz komutları bir sistem karmaşıklığını önemli ölçüde artırır. Bu nedenle, zaman uyumsuz komutları dışındaki ölçekleme gereksinimleri gerektiğinde veya özel durumlarda Mesajlaşma aracılığıyla iç mikro iletişim kurarken önerilmez. Bu durumda, hatalar için ayrı bir raporlama ve kurtarma sistemi tasarlamanız gerekir.

EShopOnContainers ilk sürümünde, biz alınan HTTP isteklerini başlatıldı ve Dünyası düzeni tarafından yönlendirilen zaman uyumlu komut işleme kullanmaya karar vermiştir. Kolayca sağlayan başarı veya başarısızlık işlemin olarak döndürmek [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) uygulaması.

Herhangi bir durumda, bu uygulamanın veya mikro'nın iş gereksinimlerine göre kararı olmalıdır.

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Komut işlemi ardışık düzen Dünyası deseniyle (MediatR) uygulama

Örnek uygulama, bu kılavuz kullanılarak Dünyası düzeni sürücü komutu alımı için temel alır ve bunları doğru komut işleyicileri için bellekte yönlendirme işlemdeki ardışık düzeni önerir. Kılavuz, ayrıca dekoratörler uygulama önerir veya [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) arası kesme sorunları ayırmak için.

.NET Core uygulama için Dünyası deseni uygulayan birden fazla açık kaynak kitaplıkları kullanılabilir vardır. Bu kılavuzda kullanılan kitaplık [MediatR](https://github.com/jbogard/MediatR) açık kaynak kitaplığı (Jimmy Bogard tarafından oluşturulan), ancak başka bir yaklaşım kullanır. MediatR dekoratörler veya davranışları uygulanırken bir komutu gibi bellek içi iletileri işlemek izin veren küçük ve basit bir kitaplıktır.

Dünyası desenini kullanarak ve yardımcı olur bağ azaltmak için otomatik olarak o çalışma gerçekleştirir işleyici bağlanma sırasında istenen iş sorunları yalıtmak için — bu durumda, komut işleyicileri için.

Bu kılavuzu gözden geçirirken Dünyası deseni kullanılacak başka bir iyi neden Jimmy Bogard tarafından açıklandığı:

Düşünüyorum burada sınama tümleştirilmediği olabilir – sisteminizi davranışını iyi tutarlı penceresi sağlar. İstek içinde yanıt genişletme. Biz bu en boy tutarlı bir şekilde testleri davranmakta binada oldukça değerli buldunuz.

İlk olarak, bize denetleyicisi kod burada gerçekten Dünyası nesne kullanırsınız göz. Dünyası nesne kullanmadıysanız, tüm bağımlılıkları Bu denetleyici için bir Günlükçü nesnesi ve diğerleri gibi eklemesine gerekir. Bu nedenle, Oluşturucusu oldukça karmaşık olabilir. Diğer taraftan, Dünyası nesne kullanırsanız, denetleyicinizin Oluşturucusu çok daha basit, aşağıdaki örnekte olduğu gibi çapraz kesme işlemi her olsaydı, olurdu pek çok bağımlılık yerine yalnızca birkaç bağımlılıkları olabilir:

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

Dünyası temiz ve yalın bir Web API denetleyicisi yapıcı sağlar görebilirsiniz. Ayrıca, denetleyici yöntemlerinde Dünyası nesnesine bir komut göndermek için kodu neredeyse tek bir çizgi bulunur:

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

Komut işleyici sınıfları unutmayın MediatR Dünyası sınıfları ve komut işleyici sınıfları IOC kapsayıcısında kaydetmek gerekir. Varsayılan olarak, MediatR IOC kapsayıcı olarak Autofac kullanır, ancak yerleşik ASP.NET Core IOC kapsayıcı veya MediatR tarafından desteklenen herhangi bir kapsayıcısına de kullanabilirsiniz.

Aşağıdaki kod Dünyası'nın türleri ve komutları Autofac modülleri kullanırken nasıl gösterir.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

Her komut işleyici generic IAsyncRequestHandler arabirimiyle uyguladığından&lt;T&gt; ve RegisteredAssemblyTypes inceler nesne işleyicidir her komutun kendi komut işleyici ile ilişkili mümkün olduğundan, İlişki CommandHandler sınıfında, aşağıdaki örnekte olduğu gibi belirtilir:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Bu komutları ile komut işleyicileri karşılık gelen koddur. Yalnızca basit bir sınıf işleyicisidir ancak RequestHandler devralan&lt;T&gt;, ve MediatR doğru yükü ile çağrılması emin yapar.

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a>Çapraz kesme sorunları dünyası ve oluşturma öğesi desenlerle komutları işlenirken uygulama

Daha fazla bir şey yok: arası kesme sorunlarının Dünyası ardışık düzene geçerli durum. Bir oluşturma öğesi nasıl kaydetme Autofac kayıt modülü kod sonunda görebilirsiniz, özellikle, özel bir LogDecorator sınıf yazın.

Yeniden eShopOnContainers gelecek bir sürümünde bu şekilde geçiş yapacağınız olduğunu unutmayın [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) ve gitme [davranışları](https://github.com/jbogard/MediatR/wiki/Behaviors) dekoratörler kullanmak yerine.

Olduğunu [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) sınıfı, yürütülmekte olan komut işleyici ve olup olmadığını başarılı olup hakkındaki bilgileri kaydeder aşağıdaki kodu olarak uygulanabilir.

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

Bu oluşturma öğesi sınıf uygulama tarafından ve onunla ardışık dekorasyon tarafından MediatR işlenen tüm komutları yürütme hakkında bilgi kaydetme.

Mikro hizmet ikinci bir oluşturma öğesi temel doğrulama için de geçerlidir sıralama eShopOnContainers [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) dayanan sınıfı [FluentValidation](https://github.com/JeremySkinner/FluentValidation) gösterildiği gibi kitaplığı Aşağıdaki kod:

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

Ardından, temel [FluentValidation](https://github.com/JeremySkinner/FluentValidation) kitaplığı oluşturduğumuz doğrulama CreateOrderCommand ile olduğu gibi aşağıdaki kodu geçirilen verileri için:

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
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
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

Ek doğrulama oluşturabilirsiniz. Komut doğrulamaları uygulamak için çok temiz ve zarif bir yolu budur.

Benzer şekilde, diğer dekoratörler ek unsurları veya bunları işlerken komutları uygulamak istediğiniz arası kesme sorunları için uygulamanız.

#### <a name="additional-resources"></a>Ek kaynaklar

##### <a name="the-mediator-pattern"></a>Dünyası düzeni

-   **Dünyası düzeni**
    [*https://en.wikipedia.org/wiki/Mediator\_düzeni*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Oluşturma öğesi düzeni

-   **Oluşturma öğesi düzeni**
    [*https://en.wikipedia.org/wiki/Decorator\_düzeni*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

-   **MediatR.** GitHub depo.
    [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

-   **MediatR ve AutoMapper CQRS**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

-   **Üzerinde bir Diyet denetleyicilerinizi put: gönderileri ve komutları. ** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

-   **Çapraz kesme sorunları Dünyası ardışık düzen ile tackling**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

-   **CQRS ve REST: mükemmel**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

-   **MediatR ardışık örnekler**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

-   **Dikey dilim Test armatürleri MediatR ve ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*

-   **İçin yayımlanan Microsoft bağımlılık ekleme MediatR uzantıları**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a>Fluent doğrulama

-   **Jeremy Skinner. FluentValidation.** GitHub depo.
    [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
[Önceki] (microservice-application-layer-web-api-design.md) [sonraki] (.. /implement-resilient-Applications/index.MD)
