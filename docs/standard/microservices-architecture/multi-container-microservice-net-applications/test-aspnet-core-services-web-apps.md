---
title: ASP.NET Core services ve web uygulamaları test etme
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | ASP.NET Core services ve web uygulamaları test etme
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 596f588aae8c0814e5b40d29c4bf5723f944c5ac
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>ASP.NET Core services ve web uygulamaları test etme

Denetleyicileri, tüm ASP.NET Core API hizmeti ve ASP.NET MVC Web uygulaması, merkezi bir parçasıdır. Bu nedenle, uygulamanız için tasarlandığı gibi davranırlar güven olmalıdır. Otomatikleştirilmiş test üretim düşmeden önce hatalarını algılayabilir ve bu güvenle sağlayabilirsiniz.

Denetleyicinin geçerli veya geçersiz girişleri göre nasıl davranacağını test ve gerçekleştirdiği iş işlemi sonucuna denetleyicisi yanıtları test gerekir. Ancak, bu tür testler, mikro sahip olmalıdır:

-   Birim testleri. Bu uygulamanın bileşenleri tek tek beklendiği gibi çalıştığından emin olun. Onaylar bileşen API sınayın.

-   Tümleştirme sınar. Bu bileşen etkileşimleri veritabanları gibi dış yapıları karşı beklendiği gibi çalıştığından emin olun. Onaylar bileşen API'si, kullanıcı Arabirimi veya veritabanı g/ç gibi eylemleri günlüğe kaydetme, vb. yan etkileri test edebilirsiniz.

-   İşlevsel testleri her mikro hizmet için. Bu, uygulama kullanıcının açısından beklendiği gibi çalıştığından emin olun.

-   Hizmet sınar. Bu, uçtan uca hizmeti kullanım örnekleri, aynı anda birden fazla hizmet testi dahil olmak üzere test edilmesini emin olun. Bu tür sınama ortamı ilk hazırlamanız gerekir. Bu durumda, hizmetler başlatma anlamına gelir (örneğin, kullanarak docker-oluşturmanıza).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>ASP.NET çekirdek Web API'leri için uygulama birim testleri

Birim testi haklarında altyapı ve bağımlılıklar ayrı bir uygulamanın bir bölümünü test içerir. Ne zaman, birim test denetleyicisi mantığı, yalnızca tek bir eylem içeriğini veya yöntemi test, değil davranışı bağımlılıklarından biri veya framework'ün. Birim testleri algılanmayan sorunların bileşenleri arasındaki etkileşim — diğer bir deyişle tümleştirme sınaması amacı.

Test denetleyicisi eylemleriniz, birimi, yalnızca davranışlarını üzerinde odaklanmak emin olun. Denetleyici birim testi filtreleri, yönlendirme veya model bağlama gibi şeyleri önler. Tek şey sınama odaklanmak için birim testleri yazmak basit ve hızlı çalıştırmak genellikle durumdadır. Birim testleri iyi yazılmış bir dizi sık kadar ek yükü çalıştırabilirsiniz.

Birim testleri test çerçevelerini xUnit.net, mstest'i, Moq veya NUnit gibi göre uygulanır. XUnit eShopOnContainers örnek uygulama için kullanıyoruz.

Birim testi için bir Web API denetleyicisi yazdığınızda, yeni anahtar sözcük C'de kullanarak doğrudan denetleyici sınıfının örneği\#, böylece test mümkün olduğunca hızlı çalışacaktır. Aşağıdaki örnek kullanırken bunu gösterilmektedir [XUnit](https://xunit.github.io/) Test Çerçevesi olarak.

```csharp
[Fact]
public void Add_new_Order_raises_new_event()
{
    // Arrange
    var street = " FakeStreet ";
    var city = "FakeCity";
    // Other variables omitted for brevity ...
    // Act
    var fakeOrder = new Order(new Address(street, city, state, country, zipcode),
        cardTypeId, cardNumber,
        cardSecurityNumber, cardHolderName,
        cardExpiration);
    // Assert
    Assert.Equal(fakeOrder.DomainEvents.Count, expectedResult);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Uygulama tümleştirme ve her mikro hizmet için işlevsel testleri

Belirtildiği gibi tümleştirme testleri ve işlevsel testleri farklı amaçlar ve hedeflerine sahiptir. Bu bölümde biz tümleştirme testleri yoğunlaşabilirsiniz şekilde ancak her ikisi de ASP.NET Core denetleyicileri sınarken uygulamak benzer, yoludur.

Tümleştirme sınaması uygulamanın bileşenleri birleştirilen zaman doğru şekilde işlev sağlar. ASP.NET Core destekler tümleştirme birim test çerçevelerini ve ağ yükü olmadan isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı kullanarak test etme.

Birim testi, tümleştirme testleri, bir veritabanı, dosya sistemi, ağ kaynaklarına veya web isteklerini ve yanıtlarını gibi uygulama altyapı sorunlarını sık içerir. Birim testleri veya bu sorunları yerine nesneleri mock fakes kullanın. Ancak tümleştirme testleri amacı sistem bu sistemleriyle tümleştirme test etmek için fakes kullanmaz veya nesneler mock şekilde beklendiği gibi çalıştığını doğrulayın. Bunun yerine, diğer hizmetlerden veritabanı erişimi veya hizmet çağırma gibi altyapı içerir.

Daha büyük kod parçalarını birim testleri daha tümleştirme testleri çalışma olduğundan ve tümleştirme testleri altyapı öğelerde dayandığından, bunlar büyüklük birim testleri yavaş olma eğilimindedir. Bu nedenle, yazma ve çalıştırma kaç tümleştirme testleri sınırlamak için bir fikirdir.

ASP.NET Core size bu testler daha hızlı gerçek web ana bilgisayar kullanırken çalıştırabileceğiniz anlamına gelir, ağ yükü olmadan HTTP isteklerini işlemek için kullanılan bir yerleşik test web ana içerir. Test web ana bilgisayarı Microsoft.AspNetCore.TestHost NuGet bileşeninde kullanılabilir. Tümleştirme test projeleri için eklenebilir ve konak ASP.NET Core uygulamaları kullanılır.

Tümleştirme testleri için ASP.NET Core denetleyicileri oluşturduğunuzda aşağıdaki kodda görüldüğü gibi test ana bilgisayar üzerinden denetleyicileri örneği oluşturur. Bu bir HTTP isteğini karşılaştırılabilir, ancak daha hızlı çalışır.

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

-   **Steve Smith. Test denetleyicileri** (ASP.NET çekirdek) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Tümleştirme sınaması** (ASP.NET çekirdek) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](/aspnet/core/testing/integration-testing)

-   **Birim testi .NET kullanarak dotnet test çekirdek**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)

-   **xUnit.net**. Resmi sitesi.
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **Birim testi temelleri.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)

-   **Moq**. GitHub depo.
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Resmi sitesi.
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Uygulama hizmeti testleri çok kapsayıcı uygulama 

Birden çok kapsayıcı uygulamaları test ettiğinizde daha önce belirtildiği gibi tüm mikro Docker ana bilgisayar veya kapsayıcı küme içinde çalışıyor olması gerekir. Birkaç mikro içeren birden çok işlemleri içeren uçtan uca hizmet testleri gerektirir dağıtma ve docker çalıştırarak Docker ana tüm uygulama başlatma-oluşturan Yukarı (veya bir orchestrator kullanıyorsanız karşılaştırılabilir bir mekanizma). Tüm uygulama ve tüm hizmetlerinin çalıştığını sonra uçtan uca tümleştirme ve işlevsel testleri çalıştırabilirsiniz.

Kullanabileceğiniz birkaç yaklaşım vardır. Uygulama (veya docker compose.ci.build.yml gibi benzer olanlar) dağıtmak için kullandığınız docker-compose.yml dosyası çözüm düzeyinde kullanmak için giriş noktası genişletebilirsiniz [dotnet test](../../../core/tools/dotnet-test.md). Ayrıca testleri, hedeflediğiniz görüntüde çalıştırırsınız: başka bir oluşturma dosyasını da kullanabilirsiniz. Mikro ve kapsayıcıları veritabanlarını içeren tümleştirme testleri için başka bir oluşturma dosyasını kullanarak, ilgili verileri her zaman özgün durumuna testleri çalıştırmadan önce sıfırlanacağını emin olabilirsiniz.

Oluşturma uygulama hazır ve çalışır hale geldikten sonra Visual Studio çalıştırıyorsanız, kesme noktaları ve özel durumları yararlanabilirsiniz. Veya tümleştirme testleri otomatik olarak CI hattınızı Visual Studio Team Services veya Docker kapsayıcıları destekleyen herhangi bir CI/CD sistemi içinde çalıştırabilirsiniz.

>[!div class="step-by-step"]
[Önceki] (abone-events.md) [sonraki] (.. /microservice-ddd-cqrs-Patterns/index.MD)
