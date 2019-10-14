---
title: ASP.NET Core Hizmetleri ve Web uygulamalarını test etme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Kapsayıcılarda ASP.NET Core Hizmetleri ve Web uygulamalarını test etmek için bir mimari bulun.
ms.date: 10/02/2018
ms.openlocfilehash: 042f7a6171a88025d3d4a8e37c4deceb416e5711
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291275"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>ASP.NET Core Hizmetleri ve Web uygulamalarını test etme

Denetleyiciler, tüm ASP.NET Core API Service ve ASP.NET MVC web uygulamalarının merkezi bir parçasıdır. Bu nedenle, uygulamanız için amaçlanan gibi davrandıklarından emin olmanız gerekir. Otomatikleştirilmiş testler size bu güvenilirliği sağlayabilir ve üretime ulaşmadan önce hataları tespit edebilir.

Denetleyicinin geçerli veya geçersiz girişlere göre nasıl davranacağını ve gerçekleştirdiği iş işleminin sonucuna bağlı olarak test denetleyicisi yanıtlarını test etmeniz gerekir. Ancak, mikro hizmetlerinizde bu tür testlerin olması gerekir:

- Birim testleri. Bu, uygulamanın ayrı bileşenlerinin beklenen şekilde çalışmasını güvence altına aldığından emin olun. Onaylar bileşen API 'sini test etme.

- Tümleştirme testleri. Bu, bileşen etkileşimlerin veritabanları gibi dış yapılara karşı beklendiği gibi çalışmasını güvence altına aldığından emin olun. Onaylar, bileşen API 'sini, Kullanıcı arabirimini veya veritabanı g/ç, günlüğe kaydetme vb. gibi eylemlerin yan etkilerini test edebilir.

- Her mikro hizmet için işlevsel testler. Bu, uygulamanın kullanıcının perspektifinden beklendiği gibi çalıştığından emin olun.

- Hizmet testleri. Bu, birden çok hizmetin aynı anda test edilmesi de dahil olmak üzere uçtan uca hizmet kullanım örneklerinin test edilmesine olanak sağlar. Bu test türü için öncelikle ortamı hazırlamanız gerekir. Bu durumda, hizmetler (örneğin, Docker-Compose kullanarak) başlatılıyor demektir.

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>ASP.NET Core Web API 'Leri için birim testlerini uygulama

Birim testi, bir uygulamanın bir bölümünün altyapısından ve bağımlılıklarından yalıtımıyla test edilmesini içerir. Birim test denetleyicisi mantığınızı kullandığınızda yalnızca tek bir eylemin veya metodun içeriği test edilir, bağımlılıkları veya çerçevenin kendisi değildir. Birim testleri, tümleştirme testi amacı olan bileşenler arasındaki etkileşimle ilgili sorunları algılamaz.

Denetleyici eylemlerinizi birim testi yaparken, yalnızca davranışlarını odakladığınızdan emin olun. Denetleyici birimi testi, filtreler, yönlendirme veya model bağlama (istek verilerinin bir ViewModel veya DTO) gibi şeyleri önler. Yalnızca bir şeyi test etmeye odaklandığından, birim testlerinin genellikle yazma ve hızlı çalışma için basit olması gerekir. İyi yazılmış bir birim testleri kümesi, çok fazla yük olmadan sık çalıştırılabilir.

Birim testleri xUnit.net, MSTest, moq veya NUnit gibi test çerçeveleri temelinde uygulanır. EShopOnContainers örnek uygulaması için xUnit kullandık.

Bir Web API denetleyicisi için bir birim testi yazdığınızda, test, mümkün olduğunca hızlı çalışacak şekilde C @ no__t-0 içindeki New anahtar sözcüğünü kullanarak doğrudan denetleyici sınıfını örnekleyebilirsiniz. Aşağıdaki örnek, [xUnit](https://xunit.github.io/) 'i test çerçevesi olarak kullanırken nasıl yapılacağını gösterir.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Her mikro hizmet için tümleştirme ve işlevsel testleri uygulama

Belirtildiği gibi, tümleştirme testleri ve işlevsel testlerin farklı amaçları ve hedefleri vardır. Ancak, ASP.NET Core denetleyicileri test edilirken her ikisini de aynı şekilde uyguladığınızda, bu bölümde tümleştirme testlerine odaklanıyoruz.

Tümleştirme testi, bir uygulamanın bileşenlerinin, bir araya geldiğinde doğru şekilde çalışmasını sağlar. ASP.NET Core, birim test çerçeveleri ve ağ yükü olmadan istekleri işlemek için kullanılabilen yerleşik bir test Web ana bilgisayarı kullanılarak tümleştirme testini destekler.

Birim testinin aksine, tümleştirme sınamaları genellikle veritabanı, dosya sistemi, ağ kaynakları veya Web istekleri ve yanıtları gibi uygulama altyapısı sorunlarını kapsar. Birim testleri, bu endişeler yerine Fakes veya sahte nesneler kullanır. Ancak tümleştirme testlerinin amacı, sistemin bu sistemlerle beklendiği gibi çalıştığından emin olmak için, tümleştirme testi için Fakes veya sahte nesneler kullanmayın. Bunun yerine, diğer hizmetlerden veritabanı erişimi veya hizmet çağrısı gibi altyapıyı dahil edersiniz.

Tümleştirme sınamaları, kod segmentlerinin birim testlerine göre daha büyük kesimlebildiğinden ve tümleştirme testleri altyapı öğelerini kullandığından, birim testlerinden daha yavaş bir şekilde sıra daha yavaş bir şekilde ücretlidir. Bu nedenle, kaç tane tümleştirme testini yazıp çalıştıracağınızı kısıtlamak iyi bir fikirdir.

ASP.NET Core, ağ yükü olmadan HTTP isteklerini işlemek için kullanılabilen yerleşik bir test Web ana bilgisayarı içerir, yani bu testleri gerçek bir Web ana bilgisayarı kullanırken daha hızlı çalıştırabilirsiniz. Test Web ana bilgisayarı (TestServer), bir NuGet bileşeninde Microsoft. AspNetCore. TestHost olarak kullanılabilir. Tümleştirme test projelerine eklenebilir ve ASP.NET Core uygulamalarını barındırmak için kullanılır.

Aşağıdaki kodda görebileceğiniz gibi, ASP.NET Core denetleyicileri için tümleştirme testleri oluşturduğunuzda, denetleyicileri test ana bilgisayarı aracılığıyla örnekleyebilirsiniz. Bu bir HTTP isteğine benzer, ancak daha hızlı çalışır.

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

- **Steve Smith. Test denetleyicileri** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- **Steve Smith. Tümleştirme testi** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- **DotNet test  \ kullanarak .NET Core 'Da birim testi**
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- **xUnit.net**. Resmi site. \
    <https://xunit.github.io/>

- **Birim testi temelleri.** \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- **Moq**. GitHub deposu. \
    <https://github.com/moq/moq>

- **NUnit**. Resmi site. \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Çok kapsayıcılı bir uygulamada hizmet testlerini uygulama

Daha önce belirtildiği gibi, çok Kapsayıcılı uygulamaları test ettiğinizde, tüm mikro hizmetlerin Docker konağı veya kapsayıcı kümesi içinde çalışıyor olması gerekir. Birkaç mikro hizmeti içeren birden çok işlem içeren uçtan uca hizmet testleri, Docker-Compose ' i (veya bir Orchestrator kullanıyorsanız karşılaştırılabilir bir mekanizmayı) çalıştırarak tüm uygulamayı Docker konağında dağıtmanızı ve başlatmanız gerekir. Tüm uygulama ve tüm hizmetleri çalışır olduktan sonra, uçtan uca tümleştirmeyi ve işlevsel testleri çalıştırabilirsiniz.

Kullanabileceğiniz birkaç yaklaşım vardır. Uygulamayı çözüm düzeyinde dağıtmak için kullandığınız Docker-Compose. yıml dosyasında, [DotNet testini](../../../core/tools/dotnet-test.md)kullanmak için giriş noktasını genişletebilirsiniz. Ayrıca, hedeflediğiniz görüntüde testlerinizi çalıştıracak başka bir oluşturma dosyası da kullanabilirsiniz. Mikro hizmetlerinizi ve kapsayıcılarındaki veritabanlarını içeren tümleştirme testleri için başka bir oluşturma dosyası kullanarak, testleri çalıştırmadan önce ilgili verilerin her zaman özgün durumuna sıfırlandığını unutmayın.

Oluşturma uygulaması çalışır duruma getirildikten sonra, Visual Studio çalıştırıyorsanız kesme noktalarından ve özel durumların avantajlarından yararlanabilirsiniz. Veya Azure DevOps Services veya Docker kapsayıcılarını destekleyen herhangi bir CI/CD sisteminde bulunan CI işlem hattınızda tümleştirme testlerini otomatik olarak çalıştırabilirsiniz.

## <a name="testing-in-eshoponcontainers"></a>EShopOnContainers 'da test etme

Başvuru uygulaması (eShopOnContainers) testleri yakın zamanda yeniden yapılandırılmış ve şu anda dört kategori var:

1. **Birim** testleri, **{mikro ServiceName} içinde yer alan yalnızca düz eski normal birim testleri. UnitTests** projeleri

2. **Mikro hizmet işlevsel/tümleştirme testleri**, her bir mikro hizmetin altyapısını içeren, ancak diğerlerinden yalıtılmış ve **{mikro ServiceName} içinde yer alan test çalışmaları. FunctionalTests** projeleri.

3. Birkaç mikro hizmet sunan test çalışmaları ile mikro hizmet tümleştirmesine odaklanarak **uygulama işlev/tümleştirme testleri**. Bu testler Project **Application. FunctionalTests**içinde bulunur.

4. Her mikro hizmet için yanıt sürelerine odaklanarak **Yük testleri**. Bu sınamalar proje **LoadTest** ' de bulunur ve Visual Studio 2017 Enterprise Edition gerekir.

Mikro hizmet başına birim ve tümleştirme testi, her mikro hizmette bir test klasöründe bulunur ve uygulama, Şekil 6-25 ' de gösterildiği gibi çözüm klasöründeki test klasörü altında bir yük testi içerir.

![EShopOnContainers içindeki testlerin yapısı: her hizmetin birim ve işlev testlerini içeren bir "test" klasörü vardır. Çözüm "test" klasörünün altında, uygulama genelinde işlevsel testler ve yük testi vardır.](./media/image42.png)

**Şekil 6-25**. EShopOnContainers 'daki test klasörü yapısı

Mikro hizmet ve uygulama işlev/tümleştirme testleri, normal testler Çalıştırıcısı kullanılarak Visual Studio 'dan çalıştırılır, ancak önce çözüm sınama klasöründe yer alan bir Docker-Compose dosyaları kümesi aracılığıyla gerekli altyapı hizmetlerini başlatmanız gerekir :

**Docker-Compose-test. yıml**

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
  nosql.data:
    image: mongo
```

**Docker-Compose-test. override. yıml**

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
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
```

Bu nedenle, işlev/tümleştirme testlerini çalıştırmak için önce bu komutu çözüm test klasöründen çalıştırmanız gerekir:

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Gördüğünüz gibi, bu Docker-Compose dosyaları yalnızca Redsıs, Kbbitmq, SQL Server ve MongoDB mikro hizmetlerini başlatır.

### <a name="additional-resources"></a>Ek kaynaklar

- GitHub 'daki eShopOnContainers deposunda **README dosyasını sınar**
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- GitHub 'daki eShopOnContainers deposunda **yükleme Testlerı Benioku dosyası**
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> [Önceki](subscribe-events.md)
> [İleri](background-tasks-with-ihostedservice.md)
