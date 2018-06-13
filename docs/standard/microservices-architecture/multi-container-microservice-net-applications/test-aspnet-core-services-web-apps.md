---
title: ASP.NET Core services ve web uygulamaları test etme
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | ASP.NET Core services ve web uygulamaları test etme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: b3aa0d50ba3ab64440ef51201d611177fea78ce4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582681"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="f3079-103">ASP.NET Core services ve web uygulamaları test etme</span><span class="sxs-lookup"><span data-stu-id="f3079-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="f3079-104">Denetleyicileri, tüm ASP.NET Core API hizmeti ve ASP.NET MVC Web uygulaması, merkezi bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="f3079-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="f3079-105">Bu nedenle, uygulamanız için tasarlandığı gibi davranırlar güven olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3079-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="f3079-106">Otomatikleştirilmiş test üretim düşmeden önce hatalarını algılayabilir ve bu güvenle sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3079-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="f3079-107">Denetleyicinin geçerli veya geçersiz girişleri göre nasıl davranacağını test ve gerçekleştirdiği iş işlemi sonucuna denetleyicisi yanıtları test gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3079-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="f3079-108">Ancak, bu tür testler, mikro sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="f3079-108">However, you should have these types of tests your microservices:</span></span>

-   <span data-ttu-id="f3079-109">Birim testleri.</span><span class="sxs-lookup"><span data-stu-id="f3079-109">Unit tests.</span></span> <span data-ttu-id="f3079-110">Bu uygulamanın bileşenleri tek tek beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f3079-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="f3079-111">Onaylar bileşen API sınayın.</span><span class="sxs-lookup"><span data-stu-id="f3079-111">Assertions test the component API.</span></span>

-   <span data-ttu-id="f3079-112">Tümleştirme sınar.</span><span class="sxs-lookup"><span data-stu-id="f3079-112">Integration tests.</span></span> <span data-ttu-id="f3079-113">Bu bileşen etkileşimleri veritabanları gibi dış yapıları karşı beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f3079-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="f3079-114">Onaylar bileşen API'si, kullanıcı Arabirimi veya veritabanı g/ç gibi eylemleri günlüğe kaydetme, vb. yan etkileri test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3079-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="f3079-115">İşlevsel testleri her mikro hizmet için.</span><span class="sxs-lookup"><span data-stu-id="f3079-115">Functional tests for each microservice.</span></span> <span data-ttu-id="f3079-116">Bu, uygulama kullanıcının açısından beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f3079-116">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="f3079-117">Hizmet sınar.</span><span class="sxs-lookup"><span data-stu-id="f3079-117">Service tests.</span></span> <span data-ttu-id="f3079-118">Bu, uçtan uca hizmeti kullanım örnekleri, aynı anda birden fazla hizmet testi dahil olmak üzere test edilmesini emin olun.</span><span class="sxs-lookup"><span data-stu-id="f3079-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="f3079-119">Bu tür sınama ortamı ilk hazırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3079-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="f3079-120">Bu durumda, hizmetler başlatma anlamına gelir (örneğin, kullanarak docker-oluşturmanıza).</span><span class="sxs-lookup"><span data-stu-id="f3079-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="f3079-121">ASP.NET çekirdek Web API'leri için uygulama birim testleri</span><span class="sxs-lookup"><span data-stu-id="f3079-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="f3079-122">Birim testi haklarında altyapı ve bağımlılıklar ayrı bir uygulamanın bir bölümünü test içerir.</span><span class="sxs-lookup"><span data-stu-id="f3079-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="f3079-123">Ne zaman, birim test denetleyicisi mantığı, yalnızca tek bir eylem içeriğini veya yöntemi test, değil davranışı bağımlılıklarından biri veya framework'ün.</span><span class="sxs-lookup"><span data-stu-id="f3079-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="f3079-124">Birim testleri algılanmayan sorunların bileşenleri arasındaki etkileşim — diğer bir deyişle tümleştirme sınaması amacı.</span><span class="sxs-lookup"><span data-stu-id="f3079-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="f3079-125">Test denetleyicisi eylemleriniz, birimi, yalnızca davranışlarını üzerinde odaklanmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="f3079-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="f3079-126">Denetleyici birim testi filtreleri, yönlendirme veya model bağlama gibi şeyleri önler.</span><span class="sxs-lookup"><span data-stu-id="f3079-126">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="f3079-127">Tek şey sınama odaklanmak için birim testleri yazmak basit ve hızlı çalıştırmak genellikle durumdadır.</span><span class="sxs-lookup"><span data-stu-id="f3079-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="f3079-128">Birim testleri iyi yazılmış bir dizi sık kadar ek yükü çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3079-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="f3079-129">Birim testleri test çerçevelerini xUnit.net, mstest'i, Moq veya NUnit gibi göre uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f3079-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="f3079-130">XUnit eShopOnContainers örnek uygulama için kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="f3079-130">For the eShopOnContainers sample application, we are using XUnit.</span></span>

<span data-ttu-id="f3079-131">Birim testi için bir Web API denetleyicisi yazdığınızda, yeni anahtar sözcük C'de kullanarak doğrudan denetleyici sınıfının örneği\#, böylece test mümkün olduğunca hızlı çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="f3079-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="f3079-132">Aşağıdaki örnek kullanırken bunu gösterilmektedir [XUnit](https://xunit.github.io/) Test Çerçevesi olarak.</span><span class="sxs-lookup"><span data-stu-id="f3079-132">The following example shows how to do this when using [XUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="f3079-133">Uygulama tümleştirme ve her mikro hizmet için işlevsel testleri</span><span class="sxs-lookup"><span data-stu-id="f3079-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="f3079-134">Belirtildiği gibi tümleştirme testleri ve işlevsel testleri farklı amaçlar ve hedeflerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f3079-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="f3079-135">Bu bölümde biz tümleştirme testleri yoğunlaşabilirsiniz şekilde ancak her ikisi de ASP.NET Core denetleyicileri sınarken uygulamak benzer, yoludur.</span><span class="sxs-lookup"><span data-stu-id="f3079-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="f3079-136">Tümleştirme sınaması uygulamanın bileşenleri birleştirilen zaman doğru şekilde işlev sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3079-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="f3079-137">ASP.NET Core destekler tümleştirme birim test çerçevelerini ve ağ yükü olmadan isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı kullanarak test etme.</span><span class="sxs-lookup"><span data-stu-id="f3079-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="f3079-138">Birim testi, tümleştirme testleri, bir veritabanı, dosya sistemi, ağ kaynaklarına veya web isteklerini ve yanıtlarını gibi uygulama altyapı sorunlarını sık içerir.</span><span class="sxs-lookup"><span data-stu-id="f3079-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="f3079-139">Birim testleri veya bu sorunları yerine nesneleri mock fakes kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3079-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="f3079-140">Ancak tümleştirme testleri amacı sistem bu sistemleriyle tümleştirme test etmek için fakes kullanmaz veya nesneler mock şekilde beklendiği gibi çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f3079-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="f3079-141">Bunun yerine, diğer hizmetlerden veritabanı erişimi veya hizmet çağırma gibi altyapı içerir.</span><span class="sxs-lookup"><span data-stu-id="f3079-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="f3079-142">Daha büyük kod parçalarını birim testleri daha tümleştirme testleri çalışma olduğundan ve tümleştirme testleri altyapı öğelerde dayandığından, bunlar büyüklük birim testleri yavaş olma eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="f3079-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="f3079-143">Bu nedenle, yazma ve çalıştırma kaç tümleştirme testleri sınırlamak için bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="f3079-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="f3079-144">ASP.NET Core size bu testler daha hızlı gerçek web ana bilgisayar kullanırken çalıştırabileceğiniz anlamına gelir, ağ yükü olmadan HTTP isteklerini işlemek için kullanılan bir yerleşik test web ana içerir.</span><span class="sxs-lookup"><span data-stu-id="f3079-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="f3079-145">Test web ana bilgisayarı Microsoft.AspNetCore.TestHost NuGet bileşeninde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3079-145">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="f3079-146">Tümleştirme test projeleri için eklenebilir ve konak ASP.NET Core uygulamaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3079-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="f3079-147">Tümleştirme testleri için ASP.NET Core denetleyicileri oluşturduğunuzda aşağıdaki kodda görüldüğü gibi test ana bilgisayar üzerinden denetleyicileri örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3079-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="f3079-148">Bu bir HTTP isteğini karşılaştırılabilir, ancak daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="f3079-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="f3079-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f3079-149">Additional resources</span></span>

-   <span data-ttu-id="f3079-150">**Steve Smith. Test denetleyicileri** (ASP.NET çekirdek) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="f3079-150">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="f3079-151">**Steve Smith. Tümleştirme sınaması** (ASP.NET çekirdek) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](/aspnet/core/testing/integration-testing)</span><span class="sxs-lookup"><span data-stu-id="f3079-151">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](/aspnet/core/testing/integration-testing)</span></span>

-   <span data-ttu-id="f3079-152">**Birim testi .NET kullanarak dotnet test çekirdek**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span><span class="sxs-lookup"><span data-stu-id="f3079-152">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span></span>

-   <span data-ttu-id="f3079-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="f3079-153">**xUnit.net**.</span></span> <span data-ttu-id="f3079-154">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="f3079-154">Official site.</span></span>
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   <span data-ttu-id="f3079-155">**Birim testi temelleri.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="f3079-155">**Unit Test Basics.**
[*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="f3079-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="f3079-156">**Moq**.</span></span> <span data-ttu-id="f3079-157">GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="f3079-157">GitHub repo.</span></span>
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   <span data-ttu-id="f3079-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="f3079-158">**NUnit**.</span></span> <span data-ttu-id="f3079-159">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="f3079-159">Official site.</span></span>
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="f3079-160">Uygulama hizmeti testleri çok kapsayıcı uygulama</span><span class="sxs-lookup"><span data-stu-id="f3079-160">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="f3079-161">Birden çok kapsayıcı uygulamaları test ettiğinizde daha önce belirtildiği gibi tüm mikro Docker ana bilgisayar veya kapsayıcı küme içinde çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3079-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="f3079-162">Birkaç mikro içeren birden çok işlemleri içeren uçtan uca hizmet testleri gerektirir dağıtma ve docker çalıştırarak Docker ana tüm uygulama başlatma-oluşturan Yukarı (veya bir orchestrator kullanıyorsanız karşılaştırılabilir bir mekanizma).</span><span class="sxs-lookup"><span data-stu-id="f3079-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="f3079-163">Tüm uygulama ve tüm hizmetlerinin çalıştığını sonra uçtan uca tümleştirme ve işlevsel testleri çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3079-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="f3079-164">Kullanabileceğiniz birkaç yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="f3079-164">There are a few approaches you can use.</span></span> <span data-ttu-id="f3079-165">Uygulama (veya docker compose.ci.build.yml gibi benzer olanlar) dağıtmak için kullandığınız docker-compose.yml dosyası çözüm düzeyinde kullanmak için giriş noktası genişletebilirsiniz [dotnet test](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="f3079-165">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="f3079-166">Ayrıca testleri, hedeflediğiniz görüntüde çalıştırırsınız: başka bir oluşturma dosyasını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3079-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="f3079-167">Mikro ve kapsayıcıları veritabanlarını içeren tümleştirme testleri için başka bir oluşturma dosyasını kullanarak, ilgili verileri her zaman özgün durumuna testleri çalıştırmadan önce sıfırlanacağını emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3079-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="f3079-168">Oluşturma uygulama hazır ve çalışır hale geldikten sonra Visual Studio çalıştırıyorsanız, kesme noktaları ve özel durumları yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3079-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="f3079-169">Veya tümleştirme testleri otomatik olarak CI hattınızı Visual Studio Team Services veya Docker kapsayıcıları destekleyen herhangi bir CI/CD sistemi içinde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3079-169">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f3079-170">[Önceki] (abone-events.md) [sonraki] (.. /microservice-ddd-cqrs-Patterns/index.MD)</span><span class="sxs-lookup"><span data-stu-id="f3079-170">[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
