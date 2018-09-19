---
title: ASP.NET Core hizmetlerini ve web uygulamalarını test etme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | ASP.NET Core hizmetlerini ve web uygulamalarını test etme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 2702a273ade0e58ba93d556cfd1ecc5531027f93
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006397"
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

Test denetleyicisi eylemlerinizi, birimi, yalnızca davranışına odaklanmak emin olun. Bir denetleyici birim testi filtreleri, yönlendirme veya model bağlama gibi şeyleri önler. Bunlar tek şey test etmeye odaklanmamız olduğundan, birim testleri yazmak basit ve hızlı çalıştırmak genellikle. Birim testleri iyi-yazılan bir dizi sık kadar ek yük çalıştırabilirsiniz.

Birim testleri, test çerçevelerini xUnit.net, MSTest, Moq ve NUnit gibi göre uygulanır. XUnit hizmetine örnek uygulama için kullanıyoruz.

Birim testi için bir Web API denetleyicisi yazdığınızda, doğrudan C new anahtar sözcüğünü kullanarak denetleyici sınıfının örneği\#, böylece test mümkün olduğunca hızlı çalışır. Aşağıdaki örnek kullanırken, bunun nasıl yapılacağını gösterir [xUnit](https://xunit.github.io/) Test Çerçevesi olarak.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Uygulama Tümleştirmesi ve her bir mikro hizmet için işlevsel testler

Belirtildiği gibi tümleştirme testlerini ve işlevsel testleri farklı amaçlara ve hedeflere sahip. Bu bölümde biz tümleştirme testleri üzerinde yoğunlaşmak için ancak her ikisi de ASP.NET Core denetleyicileri test ederken uygulamak benzer yoludur.

Tümleştirme testi, bir uygulamanın bileşenleri bir araya getirilen olduğunda düzgün çalışması sağlar. ASP.NET Core birim testi çerçevelerini ve ağ yükü olmadan isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı'nı kullanarak test tümleştirme destekler.

Tümleştirme testleri, birim testi, bir veritabanı, dosya sistemi, ağ kaynakları veya web isteklerini ve yanıtlarını gibi uygulama altyapıyla ilgili endişelerini sık içerir. Birim testleri, fakes kullanın veya bu sorunlar yerine nesneleri Sahne. Ancak amacı tümleştirme testleri, sistem tümleştirme test etmek için fakes kullanın ya da nesneleri Sahne şekilde bu sistemlerle, beklendiği gibi çalıştığını onaylayın. Bunun yerine, veritabanı erişimi veya hizmet çağırma diğer hizmetlerden gibi altyapı dahil edin.

Daha büyük kod parçalarını birim testlerinden tümleştirme testleri alıştırma olduğundan ve tümleştirme testleri altyapı öğelerde gerektirdiğinden bunlar kat birim testleri yavaş olma eğilimindedir. Bu nedenle, yazma ve çalıştırma kaç tümleştirme testleri sınırlamak için bir fikirdir.

ASP.NET Core, bu testlerin daha hızlı bir gerçek web ana bilgisayarı kullanırken çalıştırabileceğiniz anlamına gelir, ağ yükü olmadan HTTP isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı içerir. Test web ana bilgisayarı Microsoft.AspNetCore.TestHost bir NuGet bileşenini kullanılabilir. Bu tümleştirme test projesine eklenebilir ve konağa ASP.NET Core uygulamaları kullanılır.

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

-   **Steve Smith. Test denetleyicileri** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Tümleştirme testi** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](/aspnet/core/test/integration-tests)

-   **Birim testi .NET Core kullanarak dotnet testi**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)

-   **xUnit.net**. Resmi sitesi.
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **Birim testi temel bilgileri.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)

-   **Moq**. GitHub deposu.
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Resmi sitesi.
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Çok kapsayıcılı bir uygulama üzerinde uygulama hizmet testleri 

Çok kapsayıcılı uygulamaları test ederken daha önce belirtildiği gibi tüm mikro Hizmetleri Docker kapsayıcı ya da konak kümede çalışıyor olması gerekir. Birden fazla mikro hizmetler içeren birden çok işlem içeren uçtan uca hizmet testleri gerektirir dağıtma ve docker çalıştırarak Docker ana tüm uygulama başlatma-compose up (veya bir orchestrator kullanıyorsanız benzer bir mekanizma). Tüm uygulama ve tüm hizmetlerinin çalıştığını sonra uçtan uca tümleştirme ve işlevsel testler yürütebilir.

Kullanabileceğiniz birkaç yaklaşım vardır. Uygulama (veya benzer olanları docker-Compose.ci.Build.yml dosyalarını gibi) dağıtmak için kullandığınız docker-compose.yml dosyası çözüm düzeyinde giriş noktasını kullanmak üzere genişletebilirsiniz [dotnet testi](../../../core/tools/dotnet-test.md). Hedeflediğiniz görüntüde testlerinizi çalıştıracağınız başka bir compose dosyası kullanabilirsiniz. Mikro hizmetler ve kapsayıcılar veritabanlarında içeren tümleştirme testleri için başka bir compose dosyası kullanarak, ilgili verileri her zaman özgün durumuna testleri çalıştırmadan önce sıfırlanacağını emin yapabilirsiniz.

Compose uygulaması çalışır duruma geldikten sonra Visual Studio çalıştırıyorsanız, kesme noktaları ve özel durumlar yararlanabilirsiniz. Veya, tümleştirme testlerini otomatik olarak CI işlem hattınızdaki Azure DevOps Hizmetleri veya Docker kapsayıcılarını destekleyen herhangi bir CI/CD sisteminde çalıştırabilirsiniz.

>[!div class="step-by-step"]
[Önceki](subscribe-events.md)
[İleri](../microservice-ddd-cqrs-patterns/index.md)
