---
title: ASP.NET Core hizmetlerini ve web uygulamalarını test etme
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | ASP.NET Core hizmetlerini ve web uygulamalarını kapsayıcılarda test etmek için bir mimari keşfedin.
ms.date: 01/30/2020
ms.openlocfilehash: ab3ae6276ea4e4c741731f050913d956046271ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501983"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>ASP.NET Core hizmetlerini ve web uygulamalarını test etme

Denetleyiciler, herhangi bir ASP.NET Core API hizmetinin ve MVC Web uygulaması ASP.NETnın merkezi bir parçasıdır. Bu nedenle, uygulamanız için amaçlandığı gibi çalıştıklarına güvenmelisiniz. Otomatik testler size bu güveni sağlayabilir ve üretime ulaşmadan önce hataları algılayabilir.

Denetleyicinin geçerli veya geçersiz girişlere göre nasıl hareket edeceğini sınamak ve gerçekleştirdiği iş işleminin sonucuna göre denetleyici yanıtlarını test etmeniz gerekir. Ancak, mikro hizmetleriniz için bu tür testler olmalıdır:

- Birim testleri. Bunlar, uygulamanın tek tek bileşenlerinin beklendiği gibi çalışmasını sağlar. İddialar bileşen API sına.

- Entegrasyon testleri. Bunlar, bileşen etkileşimlerinin veritabanları gibi dış yapılara karşı beklendiği gibi çalışmasını sağlar. İddialar bileşen API,UI veya veritabanı G/Ç, günlük, vb. gibi eylemlerin yan etkilerini test edebilir.

- Her mikro hizmet için fonksiyonel testler. Bunlar, uygulamanın kullanıcının bakış açısından beklendiği gibi çalışmasını sağlar.

- Servis testleri. Bunlar, aynı anda birden çok hizmeti test etmek de dahil olmak üzere uçlardan uca hizmet kullanım örneklerinin sınanmasını sağlar. Bu tür bir test için önce ortamı hazırlamanız gerekir. Bu durumda, hizmetleri başlatmak anlamına gelir (örneğin, docker-comto up kullanarak).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>ASP.NET Çekirdek Web API'leri için birim testleri uygulama

Birim testi, bir uygulamanın bir bölümünü altyapısından ve bağımlılıklarından izole olarak test etmektir. Test denetleyicisi mantığını birim lediğinizde, yalnızca tek bir eylemin veya yöntemin içeriği sınanır, bağımlılıklarının veya çerçevenin kendisinin davranışı değil. Birim testleri, bileşenler arasındaki etkileşimdeki sorunları algılamaz, bu da tümleştirme testinin amacıdır.

Denetleyici eylemlerinizi bir araya getirerken, yalnızca davranışlarına odaklandığınızdan emin olun. Denetleyici birim testi filtreler, yönlendirme veya model bağlama (istek verilerinin ViewModel veya DTO ile eşleştirilmesi) gibi şeyleri önler. Onlar sadece bir şey test odaklanmak çünkü, birim testleri genellikle yazmak ve çalıştırmak için hızlı basittir. İyi yazılmış birim testleri kümesi çok fazla yükü olmadan sık sık çalıştırılabilir.

Birim testleri xUnit.net, MSTest, Moq veya NUnit gibi test çerçevelerine göre uygulanır. eShopOnContainers örnek uygulaması için xUnit kullanıyoruz.

Bir Web API denetleyicisi için bir birim testi yazdığınızda, testin mümkün olduğunca\#hızlı çalışması için C'deki yeni anahtar sözcüğü kullanarak denetleyici sınıfını doğrudan anında alabilirsiniz. Aşağıdaki örnek, test çerçevesi olarak [xUnit](https://xunit.github.io/) kullanırken bunu nasıl yapacağını gösterir.

```csharp
[Fact]
public async Task Get_order_detail_success()
{
    //Arrange
    var fakeOrderId = "12";
    var fakeOrder = GetFakeOrder();

    //...

    //Act
    var orderController = new OrderController(
        _orderServiceMock.Object,
        _basketServiceMock.Object,
        _identityParserMock.Object);

    orderController.ControllerContext.HttpContext = _contextMock.Object;
    var actionResult = await orderController.Detail(fakeOrderId);

    //Assert
    var viewResult = Assert.IsType<ViewResult>(actionResult);
    Assert.IsAssignableFrom<Order>(viewResult.ViewData.Model);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Her mikro hizmet için entegrasyon ve işlevsel testlerin uygulanması

Belirtildiği gibi, entegrasyon testleri ve fonksiyonel testler farklı amaç ve hedefleri vardır. Ancak, Core denetleyicileri ASP.NET test ederken her ikisini de uygulama şekliniz benzerdir, bu nedenle bu bölümde tümleştirme testlerine odaklanırız.

Tümleştirme sınama, bir uygulamanın bileşenlerinin monte edildiğinde düzgün çalışmasını sağlar. ASP.NET Core, birim test çerçevelerini ve ağ yükü olmadan istekleri işlemek için kullanılabilecek yerleşik bir test web ana bilgisayarlarını kullanarak tümleştirme testini destekler.

Birim sınamanın aksine, tümleştirme testleri genellikle veritabanı, dosya sistemi, ağ kaynakları veya web istekleri ve yanıtları gibi uygulama altyapısı yla ilgili endişeleri içerir. Birim testleri bu endişeler yerine sahte veya sahte nesneler kullanır. Ancak tümleştirme testlerinin amacı, sistemin beklendiği gibi çalıştığını doğrulamaktır, bu nedenle tümleştirme testi için sahte veya sahte nesneler kullanmayın. Bunun yerine, veritabanı erişimi veya diğer hizmetlerden hizmet çağırma gibi altyapıyı eklersiniz.

Tümleştirme testleri birim testlerinden daha büyük kod bölümlerini uyguladığından ve tümleştirme testleri altyapı öğelerine dayandığından, birim testlerinden daha yavaş büyüklük emirleri olma eğilimindedirler. Bu nedenle, kaç tümleştirme testi yazıp çalıştırdığınızı sınırlamak iyi bir fikirdir.

ASP.NET Core, ağ yükü olmadan HTTP isteklerini işlemek için kullanılabilecek yerleşik bir test web ana bilgisayar içerir, yani bu testleri gerçek bir web ana bilgisayar kullanırken daha hızlı çalıştırabilirsiniz. Test web ana bilgisayarı (TestServer), Microsoft.AspNetCore.TestHost olarak NuGet bileşeninde kullanılabilir. Tümleştirme test projelerine eklenebilir ve ASP.NET Çekirdek uygulamalarını barındırmak için kullanılabilir.

Aşağıdaki kodda görebileceğiniz gibi, ASP.NET Çekirdek denetleyicileri için tümleştirme testleri oluşturduğunuzda, denetleyicileri test ana bilgisayarı üzerinden anında alabilirsiniz. Bu, bir HTTP isteğiyle karşılaştırılabilir, ancak daha hızlı çalışır.

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a>Ek kaynaklar

- **Steve Smith' i. Test denetleyicileri** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- **Steve Smith' i. Entegrasyon testi** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- **Dotnet testi kullanarak .NET Core'da birim testi** \
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- **xUnit.net.** Resmi site. \
    <https://xunit.github.io/>

- **Ünite Test Temelleri.** \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- **Güve**. GitHub deposu. \
    <https://github.com/moq/moq>

- **NUnit**. Resmi site. \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Çoklu kapsayıcı uygulamasında servis testleri uygulama

Daha önce de belirtildiği gibi, çoklu kapsayıcı uygulamalarını test ettiğinizde, tüm mikro hizmetlerin Docker ana bilgisayar veya konteyner kümesi içinde çalışıyor olması gerekir. Birden fazla mikro hizmeti içeren birden fazla işlemi içeren uçtan uca hizmet testleri, docker-comto'yu çalıştırarak (veya bir orkestratör kullanıyorsanız karşılaştırılabilir bir mekanizma) çalıştırarak docker ana bilgisayarda tüm uygulamayı dağıtmanızı ve başlatmanızı gerektirir. Tüm uygulama ve tüm hizmetleri çalıştırdıktan sonra uçuça tümleştirme ve işlevsel testler gerçekleştirebilirsiniz.

Kullanabileceğiniz birkaç yaklaşım vardır. Çözümüz düzeyinde uygulamayı dağıtmak için kullandığınız docker-compose.yml dosyasında [dotnet testini](../../../core/tools/dotnet-test.md)kullanmak için giriş noktasını genişletebilirsiniz. Ayrıca, testlerinizi hedeflediğiniz resimde çalıştıracak başka bir oluşturma dosyası da kullanabilirsiniz. Kapsayıcılar üzerinde mikrohizmetler ve veritabanları içeren tümleştirme testleri için başka bir oluşturma dosyası kullanarak, ilgili verilerin testleri çalıştırmadan önce her zaman özgün durumuna sıfırlanır emin olabilirsiniz.

Oluşturma uygulaması çalışmaya başladığında, Visual Studio'yu çalıştırıyorsanız kesme noktalarından ve özel durumlardan yararlanabilirsiniz. Veya azure DevOps Hizmetlerinde veya Docker kapsayıcılarını destekleyen diğer CI/CD sisteminde, tümleştirme testlerini CI ardışık ardışık sisteminizde otomatik olarak çalıştırabilirsiniz.

## <a name="testing-in-eshoponcontainers"></a>eShopOnContainers test

Referans uygulama (eShopOnContainers) testleri yakın zamanda yeniden yapılandırıldı ve şimdi dört kategori vardır:

1. **Birim** testleri, {MicroserviceName} içinde yer alan sadece düz eski normal birim **testleri. UnitTests** projeleri

2. **Microservice fonksiyonel/tümleştirme testleri,** her bir microservice için altyapı içeren ancak diğerlerinden izole ve **{MicroserviceName} bulunan test durumlarda. FunctionalTests** projeleri.

3. Mikro hizmet entegrasyonuna odaklanan **uygulama işlevsel/tümleştirme testleri,** çeşitli mikro hizmetler uygulayan test çalışmaları ile birlikte. Bu testler project **Application.FunctionalTests**bulunur.

Mikrohizmet başına birim ve entegrasyon testi her microservice bir test klasöründe yer almaktadır ve Uygulama bir Yük testleri Şekil 6-25'te gösterildiği gibi çözüm klasöründeki test klasörü altında yer almaktadır.

![VS'nin çözümdeki bazı test projelerini işaret eden ekran görüntüsü.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

**Şekil 6-25**. eShopOnContainers test klasörü yapısı

Microservice ve Uygulama fonksiyonel/tümleştirme testleri Visual Studio'dan düzenli test koşucusu kullanılarak çalıştırılır, ancak öncelikle çözüm test klasöründe yer alan bir dizi docker-compose dosyası ile gerekli altyapı hizmetlerini başlatmanız gerekir:

**docker-beste-test.yml**

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
  nosqldata:
    image: mongo
```

**docker-compose-test.override.yml**

```yml
version: '3.4'

services:
  redis.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
```

Bu nedenle, işlevsel/tümleştirme testlerini çalıştırmak için öncelikle çözüm test klasöründen bu komutu çalıştırmanız gerekir:

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Gördüğünüz gibi, bu docker-beste dosyaları sadece Redis, RabbitMQ, SQL Server ve MongoDB microservices başlatın.

### <a name="additional-resources"></a>Ek kaynaklar

- GitHub üzerinde eShopOnContainers repo testleri **README dosyası** \
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- **GitHub** üzerinde eShopOnContainers repo üzerinde Yük testleri README dosyası \
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> [Önceki](subscribe-events.md)
> [Sonraki](background-tasks-with-ihostedservice.md)
