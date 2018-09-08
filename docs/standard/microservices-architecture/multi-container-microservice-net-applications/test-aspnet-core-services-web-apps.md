---
title: ASP.NET Core hizmetlerini ve web uygulamalarını test etme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | ASP.NET Core hizmetlerini ve web uygulamalarını test etme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 63576445a44df0c0bdbd22b263754bb3d2919963
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195627"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="3cb01-103">ASP.NET Core hizmetlerini ve web uygulamalarını test etme</span><span class="sxs-lookup"><span data-stu-id="3cb01-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="3cb01-104">Denetleyicileri, herhangi bir ASP.NET Core API'si hizmeti ve ASP.NET MVC Web uygulaması, merkezi bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="3cb01-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="3cb01-105">Bu nedenle, uygulamanız için tasarlandığı gibi davranırlar güven olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="3cb01-106">Otomatikleştirilmiş testleri Bu güvenle sağlayabilir ve üretime ulaşmadan önce hatalar da algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="3cb01-107">Test denetleyicisinin geçerli ya da geçersiz girişler temelinde nasıl davranacağını ve test denetleyicisi yanıtları gerçekleştirdiği iş işleminin sonucuna göre gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="3cb01-108">Ancak, bu tür testler için mikro hizmetlerin sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3cb01-108">However, you should have these types of tests for your microservices:</span></span>

-   <span data-ttu-id="3cb01-109">Birim testleri.</span><span class="sxs-lookup"><span data-stu-id="3cb01-109">Unit tests.</span></span> <span data-ttu-id="3cb01-110">Bu, tek tek bileşenler uygulamanın beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="3cb01-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="3cb01-111">Onaylamalar bileşen API'yi test etme.</span><span class="sxs-lookup"><span data-stu-id="3cb01-111">Assertions test the component API.</span></span>

-   <span data-ttu-id="3cb01-112">Tümleştirme testleri.</span><span class="sxs-lookup"><span data-stu-id="3cb01-112">Integration tests.</span></span> <span data-ttu-id="3cb01-113">Bu bileşen etkileşimleri veritabanları gibi dış yapıtları karşı beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="3cb01-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="3cb01-114">Onaylamalar bileşen API, kullanıcı Arabirimi veya yan etkilerini, günlük, vb. Eylemler gibi veritabanı g/ç test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb01-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="3cb01-115">Her mikro hizmet işlevsel sınar.</span><span class="sxs-lookup"><span data-stu-id="3cb01-115">Functional tests for each microservice.</span></span> <span data-ttu-id="3cb01-116">Bu, uygulama kullanıcının açısından beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="3cb01-116">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="3cb01-117">Hizmeti test eder.</span><span class="sxs-lookup"><span data-stu-id="3cb01-117">Service tests.</span></span> <span data-ttu-id="3cb01-118">Bu, uçtan uca hizmeti kullanım örnekleri aynı anda birden çok hizmet testi dahil olmak üzere, test emin olun.</span><span class="sxs-lookup"><span data-stu-id="3cb01-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="3cb01-119">Bu tür sınama ortamı önce hazırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="3cb01-120">Bu durumda, bu hizmetleri başlatılıyor anlamına gelir (örneğin, kullanarak docker compose up).</span><span class="sxs-lookup"><span data-stu-id="3cb01-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="3cb01-121">ASP.NET Core Web API'leri için uygulama birim testleri</span><span class="sxs-lookup"><span data-stu-id="3cb01-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="3cb01-122">Bir uygulamanın bir parçası, altyapısını ve bağımlılıklarını yalıtımdan test birim testi içerir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="3cb01-123">Ne zaman, birim test denetleyicisi mantığı, yalnızca tek bir eylem içeriği veya yöntemi test, olmayan davranış framework'ün ya da bağımlılıklarından biri.</span><span class="sxs-lookup"><span data-stu-id="3cb01-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="3cb01-124">Birim testleri algılama sorunları, bileşenler arasındaki etkileşim — diğer bir deyişle tümleştirme testi amacı.</span><span class="sxs-lookup"><span data-stu-id="3cb01-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="3cb01-125">Test denetleyicisi eylemlerinizi, birimi, yalnızca davranışına odaklanmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="3cb01-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="3cb01-126">Bir denetleyici birim testi filtreleri, yönlendirme veya model bağlama gibi şeyleri önler.</span><span class="sxs-lookup"><span data-stu-id="3cb01-126">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="3cb01-127">Bunlar tek şey test etmeye odaklanmamız olduğundan, birim testleri yazmak basit ve hızlı çalıştırmak genellikle.</span><span class="sxs-lookup"><span data-stu-id="3cb01-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="3cb01-128">Birim testleri iyi-yazılan bir dizi sık kadar ek yük çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb01-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="3cb01-129">Birim testleri, test çerçevelerini xUnit.net, MSTest, Moq ve NUnit gibi göre uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3cb01-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="3cb01-130">XUnit hizmetine örnek uygulama için kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="3cb01-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="3cb01-131">Birim testi için bir Web API denetleyicisi yazdığınızda, doğrudan C new anahtar sözcüğünü kullanarak denetleyici sınıfının örneği\#, böylece test mümkün olduğunca hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="3cb01-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="3cb01-132">Aşağıdaki örnek kullanırken, bunun nasıl yapılacağını gösterir [xUnit](https://xunit.github.io/) Test Çerçevesi olarak.</span><span class="sxs-lookup"><span data-stu-id="3cb01-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="3cb01-133">Uygulama Tümleştirmesi ve her bir mikro hizmet için işlevsel testler</span><span class="sxs-lookup"><span data-stu-id="3cb01-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="3cb01-134">Belirtildiği gibi tümleştirme testlerini ve işlevsel testleri farklı amaçlara ve hedeflere sahip.</span><span class="sxs-lookup"><span data-stu-id="3cb01-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="3cb01-135">Bu bölümde biz tümleştirme testleri üzerinde yoğunlaşmak için ancak her ikisi de ASP.NET Core denetleyicileri test ederken uygulamak benzer yoludur.</span><span class="sxs-lookup"><span data-stu-id="3cb01-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="3cb01-136">Tümleştirme testi, bir uygulamanın bileşenleri bir araya getirilen olduğunda düzgün çalışması sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cb01-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="3cb01-137">ASP.NET Core birim testi çerçevelerini ve ağ yükü olmadan isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı'nı kullanarak test tümleştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="3cb01-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="3cb01-138">Tümleştirme testleri, birim testi, bir veritabanı, dosya sistemi, ağ kaynakları veya web isteklerini ve yanıtlarını gibi uygulama altyapıyla ilgili endişelerini sık içerir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="3cb01-139">Birim testleri, fakes kullanın veya bu sorunlar yerine nesneleri Sahne.</span><span class="sxs-lookup"><span data-stu-id="3cb01-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="3cb01-140">Ancak amacı tümleştirme testleri, sistem tümleştirme test etmek için fakes kullanın ya da nesneleri Sahne şekilde bu sistemlerle, beklendiği gibi çalıştığını onaylayın.</span><span class="sxs-lookup"><span data-stu-id="3cb01-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="3cb01-141">Bunun yerine, veritabanı erişimi veya hizmet çağırma diğer hizmetlerden gibi altyapı dahil edin.</span><span class="sxs-lookup"><span data-stu-id="3cb01-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="3cb01-142">Daha büyük kod parçalarını birim testlerinden tümleştirme testleri alıştırma olduğundan ve tümleştirme testleri altyapı öğelerde gerektirdiğinden bunlar kat birim testleri yavaş olma eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="3cb01-143">Bu nedenle, yazma ve çalıştırma kaç tümleştirme testleri sınırlamak için bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="3cb01-144">ASP.NET Core, bu testlerin daha hızlı bir gerçek web ana bilgisayarı kullanırken çalıştırabileceğiniz anlamına gelir, ağ yükü olmadan HTTP isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı içerir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="3cb01-145">Test web ana bilgisayarı Microsoft.AspNetCore.TestHost bir NuGet bileşenini kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-145">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="3cb01-146">Bu tümleştirme test projesine eklenebilir ve konağa ASP.NET Core uygulamaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3cb01-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="3cb01-147">Tümleştirme testleri için ASP.NET Core denetleyicileri oluşturduğunuzda aşağıdaki kodda, gördüğünüz gibi denetleyicileri üzerinden test ana bilgisayar örneği.</span><span class="sxs-lookup"><span data-stu-id="3cb01-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="3cb01-148">Bir HTTP isteği için karşılaştırılabilir budur ancak daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="3cb01-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="3cb01-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3cb01-149">Additional resources</span></span>

-   <span data-ttu-id="3cb01-150">**Steve Smith. Test denetleyicileri** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="3cb01-150">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="3cb01-151">**Steve Smith. Tümleştirme testi** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](/aspnet/core/test/integration-tests)</span><span class="sxs-lookup"><span data-stu-id="3cb01-151">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](/aspnet/core/test/integration-tests)</span></span>

-   <span data-ttu-id="3cb01-152">**Birim testi .NET Core kullanarak dotnet testi**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span><span class="sxs-lookup"><span data-stu-id="3cb01-152">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span></span>

-   <span data-ttu-id="3cb01-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="3cb01-153">**xUnit.net**.</span></span> <span data-ttu-id="3cb01-154">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="3cb01-154">Official site.</span></span>
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   <span data-ttu-id="3cb01-155">**Birim testi temel bilgileri.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="3cb01-155">**Unit Test Basics.**
[*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="3cb01-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="3cb01-156">**Moq**.</span></span> <span data-ttu-id="3cb01-157">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="3cb01-157">GitHub repo.</span></span>
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   <span data-ttu-id="3cb01-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="3cb01-158">**NUnit**.</span></span> <span data-ttu-id="3cb01-159">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="3cb01-159">Official site.</span></span>
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="3cb01-160">Çok kapsayıcılı bir uygulama üzerinde uygulama hizmet testleri</span><span class="sxs-lookup"><span data-stu-id="3cb01-160">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="3cb01-161">Çok kapsayıcılı uygulamaları test ederken daha önce belirtildiği gibi tüm mikro Hizmetleri Docker kapsayıcı ya da konak kümede çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="3cb01-162">Birden fazla mikro hizmetler içeren birden çok işlem içeren uçtan uca hizmet testleri gerektirir dağıtma ve docker çalıştırarak Docker ana tüm uygulama başlatma-compose up (veya bir orchestrator kullanıyorsanız benzer bir mekanizma).</span><span class="sxs-lookup"><span data-stu-id="3cb01-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="3cb01-163">Tüm uygulama ve tüm hizmetlerinin çalıştığını sonra uçtan uca tümleştirme ve işlevsel testler yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="3cb01-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="3cb01-164">Kullanabileceğiniz birkaç yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="3cb01-164">There are a few approaches you can use.</span></span> <span data-ttu-id="3cb01-165">Uygulama (veya benzer olanları docker-Compose.ci.Build.yml dosyalarını gibi) dağıtmak için kullandığınız docker-compose.yml dosyası çözüm düzeyinde giriş noktasını kullanmak üzere genişletebilirsiniz [dotnet testi](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="3cb01-165">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="3cb01-166">Hedeflediğiniz görüntüde testlerinizi çalıştıracağınız başka bir compose dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb01-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="3cb01-167">Mikro hizmetler ve kapsayıcılar veritabanlarında içeren tümleştirme testleri için başka bir compose dosyası kullanarak, ilgili verileri her zaman özgün durumuna testleri çalıştırmadan önce sıfırlanacağını emin yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb01-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="3cb01-168">Compose uygulaması çalışır duruma geldikten sonra Visual Studio çalıştırıyorsanız, kesme noktaları ve özel durumlar yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb01-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="3cb01-169">Veya, tümleştirme testlerini otomatik olarak CI işlem hattınızı Visual Studio Team Services veya Docker kapsayıcılarını destekleyen herhangi bir CI/CD sisteminde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb01-169">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="3cb01-170">[Önceki](subscribe-events.md)
[İleri](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="3cb01-170">[Previous](subscribe-events.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
