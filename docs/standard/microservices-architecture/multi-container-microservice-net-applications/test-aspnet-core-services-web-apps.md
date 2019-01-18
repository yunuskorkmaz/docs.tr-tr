---
title: ASP.NET Core hizmetlerini ve web uygulamalarını test etme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Kapsayıcılarda ASP.NET Core hizmetlerini ve web uygulamalarını test etmek için bir mimari keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 0f4b9a8461b4d14cd5b468a50af1783a340392e2
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362164"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>ASP.NET Core hizmetlerini ve web uygulamalarını test etme

Denetleyicileri, herhangi bir ASP.NET Core API'si hizmeti ve ASP.NET MVC Web uygulaması, merkezi bir parçasıdır. Bu nedenle, uygulamanız için tasarlandığı gibi davranırlar güven olması gerekir. Otomatikleştirilmiş testleri Bu güvenle sağlayabilir ve üretime ulaşmadan önce hatalar da algılanabilir.

Test denetleyicisinin geçerli ya da geçersiz girişler temelinde nasıl davranacağını ve test denetleyicisi yanıtları gerçekleştirdiği iş işleminin sonucuna göre gerekir. Ancak, bu tür testler için mikro hizmetlerin sahip olmalıdır:

-   Birim testleri. Bu, tek tek bileşenler uygulamanın beklendiği gibi çalıştığından emin olun. Onaylamalar bileşen API'yi test etme.

-   Tümleştirme testleri. Bu bileşen etkileşimleri veritabanları gibi dış yapıtları karşı beklendiği gibi çalıştığından emin olun. Onaylamalar bileşen API, kullanıcı Arabirimi veya yan etkilerini, günlük, vb. Eylemler gibi veritabanı g/ç test edebilirsiniz.

-   Her mikro hizmet işlevsel sınar. Bu, uygulama kullanıcının açısından beklendiği gibi çalıştığından emin olun.

-   Hizmeti test eder. Bu, uçtan uca hizmeti kullanım örnekleri aynı anda birden çok hizmet testi dahil olmak üzere, test emin olun. Bu tür sınama ortamı önce hazırlamanız gerekir. Bu durumda, bu hizmetleri başlatılıyor anlamına gelir (örneğin, kullanarak docker compose up).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>ASP.NET Core Web API'leri için uygulama birim testleri

Bir uygulamanın bir parçası, altyapısını ve bağımlılıklarını yalıtımdan test birim testi içerir. Ne zaman, birim test denetleyicisi mantığı, yalnızca tek bir eylem içeriği veya yöntemi test, olmayan davranış framework'ün ya da bağımlılıklarından biri. Birim testleri algılama sorunları, bileşenler arasındaki etkileşim — diğer bir deyişle tümleştirme testi amacı.

Test denetleyicisi eylemlerinizi, birimi, yalnızca davranışına odaklanmak emin olun. Bir denetleyici birim testi filtreleri, yönlendirme veya model bağlama (istek verisi ViewModel veya DTO eşleme) gibi şeyleri önler. Bunlar tek şey test etmeye odaklanmamız olduğundan, birim testleri yazmak basit ve hızlı çalıştırmak genellikle. Birim testleri iyi-yazılan bir dizi sık kadar ek yük çalıştırabilirsiniz.

Birim testleri, test çerçevelerini xUnit.net, MSTest, Moq ve NUnit gibi göre uygulanır. XUnit hizmetine örnek uygulama için kullanıyoruz.

Birim testi için bir Web API denetleyicisi yazdığınızda, doğrudan C new anahtar sözcüğünü kullanarak denetleyici sınıfının örneği\#, böylece test mümkün olduğunca hızlı çalışır. Aşağıdaki örnek kullanırken, bunun nasıl yapılacağını gösterir [xUnit](https://xunit.github.io/) Test Çerçevesi olarak.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Uygulama Tümleştirmesi ve her bir mikro hizmet için işlevsel testler

Belirtildiği gibi tümleştirme testlerini ve işlevsel testleri farklı amaçlara ve hedeflere sahip. Bu bölümde biz tümleştirme testleri üzerinde yoğunlaşmak için ancak her ikisi de ASP.NET Core denetleyicileri test ederken uygulamak benzer yoludur.

Tümleştirme testi, bir uygulamanın bileşenleri bir araya getirilen olduğunda düzgün çalışması sağlar. ASP.NET Core birim testi çerçevelerini ve ağ yükü olmadan isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı'nı kullanarak test tümleştirme destekler.

Tümleştirme testleri, birim testi, bir veritabanı, dosya sistemi, ağ kaynakları veya web isteklerini ve yanıtlarını gibi uygulama altyapıyla ilgili endişelerini sık içerir. Birim testleri, fakes kullanın veya bu sorunlar yerine nesneleri Sahne. Ancak amacı tümleştirme testleri, sistem tümleştirme test etmek için fakes kullanın ya da nesneleri Sahne şekilde bu sistemlerle, beklendiği gibi çalıştığını onaylayın. Bunun yerine, veritabanı erişimi veya hizmet çağırma diğer hizmetlerden gibi altyapı dahil edin.

Daha büyük kod parçalarını birim testlerinden tümleştirme testleri alıştırma olduğundan ve tümleştirme testleri altyapı öğelerde gerektirdiğinden bunlar kat birim testleri yavaş olma eğilimindedir. Bu nedenle, yazma ve çalıştırma kaç tümleştirme testleri sınırlamak için bir fikirdir.

ASP.NET Core, bu testlerin daha hızlı bir gerçek web ana bilgisayarı kullanırken çalıştırabileceğiniz anlamına gelir, ağ yükü olmadan HTTP isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı içerir. Test web ana bilgisayarı'nı (TestServer) bir NuGet bileşenini Microsoft.AspNetCore.TestHost kullanılabilir. Bu tümleştirme test projesine eklenebilir ve konağa ASP.NET Core uygulamaları kullanılır.

Tümleştirme testleri için ASP.NET Core denetleyicileri oluşturduğunuzda aşağıdaki kodda, gördüğünüz gibi denetleyicileri üzerinden test ana bilgisayar örneği. Bir HTTP isteği için karşılaştırılabilir budur ancak daha hızlı çalışır.

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

-   **Steve Smith. Test denetleyicileri** (ASP.NET Core) <br/>
    [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Tümleştirme testi** (ASP.NET Core) <br/>
    [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](https://docs.microsoft.com/aspnet/core/test/integration-tests)

-   **Birim testi .NET Core kullanarak dotnet testi** <br/>
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](~/docs/core/testing/unit-testing-with-dotnet-test.md)

-   **xUnit.net**. Resmi sitesi. <br/>
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **Birim testi temel bilgileri.** <br/>
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)

-   **Moq**. GitHub deposu. <br/>
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Resmi sitesi. <br/>
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Çok kapsayıcılı bir uygulama üzerinde uygulama hizmet testleri 

Çok kapsayıcılı uygulamaları test ederken daha önce belirtildiği gibi tüm mikro Hizmetleri Docker kapsayıcı ya da konak kümede çalışıyor olması gerekir. Birden fazla mikro hizmetler içeren birden çok işlem içeren uçtan uca hizmet testleri gerektirir dağıtma ve docker çalıştırarak Docker ana tüm uygulama başlatma-compose up (veya bir orchestrator kullanıyorsanız benzer bir mekanizma). Tüm uygulama ve tüm hizmetlerinin çalıştığını sonra uçtan uca tümleştirme ve işlevsel testler yürütebilir.

Kullanabileceğiniz birkaç yaklaşım vardır. Çözüm düzeyinde uygulamayı dağıtmak için kullandığınız docker-compose.yml dosyası içinde giriş noktasını kullanmak üzere genişletebilirsiniz [dotnet testi](https://docs.microsoft.com/dotnet/articles/core/tools/dotnet-test). Hedeflediğiniz görüntüde testlerinizi çalıştıracağınız başka bir compose dosyası kullanabilirsiniz. Mikro hizmetler ve kapsayıcılar veritabanlarında içeren tümleştirme testleri için başka bir compose dosyası kullanarak, ilgili verileri her zaman özgün durumuna testleri çalıştırmadan önce sıfırlanacağını emin yapabilirsiniz.

Compose uygulaması çalışır duruma geldikten sonra Visual Studio çalıştırıyorsanız, kesme noktaları ve özel durumlar yararlanabilirsiniz. Veya, tümleştirme testlerini otomatik olarak CI işlem hattınızdaki Azure DevOps Hizmetleri veya Docker kapsayıcılarını destekleyen herhangi bir CI/CD sisteminde çalıştırabilirsiniz.

## <a name="testing-in-eshoponcontainers"></a>Hizmetine test etme

Başvuru uygulaması (hizmetine) testleri kısa bir süre önce yapmayın ve artık dört kategorisi vardır:

1.  **Birim** testleri, yer alan, yalnızca düz eski Normal birim testleri **{MicroserviceName}. UnitTests** projeleri

2.  **Mikro hizmet işlev/tümleştirme testleri**, altyapı için her bir mikro hizmetin diğerlerinden yalıtılmış ancak test çalışmalarıyla ilgili ve içerdiği **{MicroserviceName}. FunctionalTests** projeleri.

3.  **Uygulama işlevsel/tümleştirme testleri**, mikro hizmetler tümleştirme, test çalışmaları birden fazla mikro hizmetler sağlama odaklanan. Bu testler, projede bulunan **Application.FunctionalTests**.

4.  **Yük testleri**, her bir mikro hizmetin yanıt süreleri, odaklanan. Bu testler, projede bulunan **LoadTest** ve Visual Studio 2017 Enterprise Edition gerekiyor.

Mikro hizmet başına birim ve tümleştirme test içerdiği yük testleri Çözüm klasörü'ndeki test foldel altında bulunan her mikro hizmet ve uygulama testi klasöründe Şekil 6-25 gösterildiği gibi.

![Testleri hizmetine yapısı: Her hizmetin birim ve işlev testleri içeren "test" klasörü vardır. Çözüm "test" klasörü altında vardır uygulama genelinde işlevsel testleri ve yük testi.](./media/image42.png)

**Şekil 6-25**. Hizmetine test klasör yapısı

Mikro hizmet ve uygulama işlevsel/tümleştirme testleri Visual Studio'da normal Test Çalıştırıcı kullanarak çalıştırılır ancak öncelikle gerekir gerekli altyapı hizmetleri başlatmak için testi klasöründe çözümde yer alan docker-compose dosyaları kümesi yoluyla :

**docker compose test.yml**

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

**docker compose test.override.yml**

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

Bu nedenle, işlev/tümleştirme testleri çalıştırmak için önce bu komut çözümü test klasöründen çalıştırmanız gerekir:

``` console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Gördüğünüz gibi bu docker-dosyaları yalnızca başlangıç Redis, RabitMQ, SQL Server ve MongoDB mikro hizmetler oluşturun.

### <a name="additionl-resources"></a>Additionl kaynakları

-   **Testleri Benioku dosyası** github'da hizmetine depoda <br/>
    [*https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test*](https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test)

-   **Yük testleri Benioku dosyası** github'da hizmetine depoda <br/>
    [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/)

>[!div class="step-by-step"]
>[Önceki](subscribe-events.md)
>[İleri](background-tasks-with-ihostedservice.md)