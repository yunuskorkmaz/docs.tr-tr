---
title: ASP.NET Core hizmetlerini ve web uygulamalarını test etme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Kapsayıcılarda ASP.NET Core hizmetlerini ve web uygulamalarını test etmek için bir mimari keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 99f17f713a1193e82ad64036a4b3f5e0caa20fd7
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845979"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="d224b-103">ASP.NET Core hizmetlerini ve web uygulamalarını test etme</span><span class="sxs-lookup"><span data-stu-id="d224b-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="d224b-104">Denetleyicileri, herhangi bir ASP.NET Core API'si hizmeti ve ASP.NET MVC Web uygulaması, merkezi bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="d224b-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="d224b-105">Bu nedenle, uygulamanız için tasarlandığı gibi davranırlar güven olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d224b-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="d224b-106">Otomatikleştirilmiş testleri Bu güvenle sağlayabilir ve üretime ulaşmadan önce hatalar da algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="d224b-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="d224b-107">Test denetleyicisinin geçerli ya da geçersiz girişler temelinde nasıl davranacağını ve test denetleyicisi yanıtları gerçekleştirdiği iş işleminin sonucuna göre gerekir.</span><span class="sxs-lookup"><span data-stu-id="d224b-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="d224b-108">Ancak, bu tür testler için mikro hizmetlerin sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="d224b-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="d224b-109">Birim testleri.</span><span class="sxs-lookup"><span data-stu-id="d224b-109">Unit tests.</span></span> <span data-ttu-id="d224b-110">Bu, tek tek bileşenler uygulamanın beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="d224b-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="d224b-111">Onaylamalar bileşen API'yi test etme.</span><span class="sxs-lookup"><span data-stu-id="d224b-111">Assertions test the component API.</span></span>

- <span data-ttu-id="d224b-112">Tümleştirme testleri.</span><span class="sxs-lookup"><span data-stu-id="d224b-112">Integration tests.</span></span> <span data-ttu-id="d224b-113">Bu bileşen etkileşimleri veritabanları gibi dış yapıtları karşı beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="d224b-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="d224b-114">Onaylamalar bileşen API, kullanıcı Arabirimi veya yan etkilerini, günlük, vb. Eylemler gibi veritabanı g/ç test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d224b-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="d224b-115">Her mikro hizmet işlevsel sınar.</span><span class="sxs-lookup"><span data-stu-id="d224b-115">Functional tests for each microservice.</span></span> <span data-ttu-id="d224b-116">Bu, uygulama kullanıcının açısından beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="d224b-116">These ensure that the application works as expected from the user’s perspective.</span></span>

- <span data-ttu-id="d224b-117">Hizmeti test eder.</span><span class="sxs-lookup"><span data-stu-id="d224b-117">Service tests.</span></span> <span data-ttu-id="d224b-118">Bu, uçtan uca hizmeti kullanım örnekleri aynı anda birden çok hizmet testi dahil olmak üzere, test emin olun.</span><span class="sxs-lookup"><span data-stu-id="d224b-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="d224b-119">Bu tür sınama ortamı önce hazırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d224b-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="d224b-120">Bu durumda, bu hizmetleri başlatılıyor anlamına gelir (örneğin, kullanarak docker compose up).</span><span class="sxs-lookup"><span data-stu-id="d224b-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="d224b-121">ASP.NET Core Web API'leri için uygulama birim testleri</span><span class="sxs-lookup"><span data-stu-id="d224b-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="d224b-122">Bir uygulamanın bir parçası, altyapısını ve bağımlılıklarını yalıtımdan test birim testi içerir.</span><span class="sxs-lookup"><span data-stu-id="d224b-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="d224b-123">Ne zaman, birim test denetleyicisi mantığı, yalnızca tek bir eylem içeriği veya yöntemi test, olmayan davranış framework'ün ya da bağımlılıklarından biri.</span><span class="sxs-lookup"><span data-stu-id="d224b-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="d224b-124">Birim testleri algılama sorunları, bileşenler arasındaki etkileşim — diğer bir deyişle tümleştirme testi amacı.</span><span class="sxs-lookup"><span data-stu-id="d224b-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="d224b-125">Test denetleyicisi eylemlerinizi, birimi, yalnızca davranışına odaklanmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="d224b-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="d224b-126">Bir denetleyici birim testi filtreleri, yönlendirme veya model bağlama (istek verisi ViewModel veya DTO eşleme) gibi şeyleri önler.</span><span class="sxs-lookup"><span data-stu-id="d224b-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="d224b-127">Bunlar tek şey test etmeye odaklanmamız olduğundan, birim testleri yazmak basit ve hızlı çalıştırmak genellikle.</span><span class="sxs-lookup"><span data-stu-id="d224b-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="d224b-128">Birim testleri iyi-yazılan bir dizi sık kadar ek yük çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d224b-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="d224b-129">Birim testleri, test çerçevelerini xUnit.net, MSTest, Moq ve NUnit gibi göre uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d224b-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="d224b-130">XUnit hizmetine örnek uygulama için kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="d224b-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="d224b-131">Birim testi için bir Web API denetleyicisi yazdığınızda, doğrudan C new anahtar sözcüğünü kullanarak denetleyici sınıfının örneği\#, böylece test mümkün olduğunca hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="d224b-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="d224b-132">Aşağıdaki örnek kullanırken, bunun nasıl yapılacağını gösterir [xUnit](https://xunit.github.io/) Test Çerçevesi olarak.</span><span class="sxs-lookup"><span data-stu-id="d224b-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="d224b-133">Uygulama Tümleştirmesi ve her bir mikro hizmet için işlevsel testler</span><span class="sxs-lookup"><span data-stu-id="d224b-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="d224b-134">Belirtildiği gibi tümleştirme testlerini ve işlevsel testleri farklı amaçlara ve hedeflere sahip.</span><span class="sxs-lookup"><span data-stu-id="d224b-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="d224b-135">Bu bölümde biz tümleştirme testleri üzerinde yoğunlaşmak için ancak her ikisi de ASP.NET Core denetleyicileri test ederken uygulamak benzer yoludur.</span><span class="sxs-lookup"><span data-stu-id="d224b-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="d224b-136">Tümleştirme testi, bir uygulamanın bileşenleri bir araya getirilen olduğunda düzgün çalışması sağlar.</span><span class="sxs-lookup"><span data-stu-id="d224b-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="d224b-137">ASP.NET Core birim testi çerçevelerini ve ağ yükü olmadan isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı'nı kullanarak test tümleştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="d224b-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="d224b-138">Tümleştirme testleri, birim testi, bir veritabanı, dosya sistemi, ağ kaynakları veya web isteklerini ve yanıtlarını gibi uygulama altyapıyla ilgili endişelerini sık içerir.</span><span class="sxs-lookup"><span data-stu-id="d224b-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="d224b-139">Birim testleri, fakes kullanın veya bu sorunlar yerine nesneleri Sahne.</span><span class="sxs-lookup"><span data-stu-id="d224b-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="d224b-140">Ancak amacı tümleştirme testleri, sistem tümleştirme test etmek için fakes kullanın ya da nesneleri Sahne şekilde bu sistemlerle, beklendiği gibi çalıştığını onaylayın.</span><span class="sxs-lookup"><span data-stu-id="d224b-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="d224b-141">Bunun yerine, veritabanı erişimi veya hizmet çağırma diğer hizmetlerden gibi altyapı dahil edin.</span><span class="sxs-lookup"><span data-stu-id="d224b-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="d224b-142">Daha büyük kod parçalarını birim testlerinden tümleştirme testleri alıştırma olduğundan ve tümleştirme testleri altyapı öğelerde gerektirdiğinden bunlar kat birim testleri yavaş olma eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="d224b-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="d224b-143">Bu nedenle, yazma ve çalıştırma kaç tümleştirme testleri sınırlamak için bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="d224b-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="d224b-144">ASP.NET Core, bu testlerin daha hızlı bir gerçek web ana bilgisayarı kullanırken çalıştırabileceğiniz anlamına gelir, ağ yükü olmadan HTTP isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı içerir.</span><span class="sxs-lookup"><span data-stu-id="d224b-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="d224b-145">Test web ana bilgisayarı'nı (TestServer) bir NuGet bileşenini Microsoft.AspNetCore.TestHost kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d224b-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="d224b-146">Bu tümleştirme test projesine eklenebilir ve konağa ASP.NET Core uygulamaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d224b-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="d224b-147">Tümleştirme testleri için ASP.NET Core denetleyicileri oluşturduğunuzda aşağıdaki kodda, gördüğünüz gibi denetleyicileri üzerinden test ana bilgisayar örneği.</span><span class="sxs-lookup"><span data-stu-id="d224b-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="d224b-148">Bir HTTP isteği için karşılaştırılabilir budur ancak daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="d224b-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="d224b-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d224b-149">Additional resources</span></span>

- <span data-ttu-id="d224b-150">**Steve Smith. Test denetleyicileri** (ASP.NET Core)</span><span class="sxs-lookup"><span data-stu-id="d224b-150">**Steve Smith. Testing controllers** (ASP.NET Core)</span></span> <br/>
    [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="d224b-151">**Steve Smith. Tümleştirme testi** (ASP.NET Core)</span><span class="sxs-lookup"><span data-stu-id="d224b-151">**Steve Smith. Integration testing** (ASP.NET Core)</span></span> <br/>
    [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](https://docs.microsoft.com/aspnet/core/test/integration-tests)

- <span data-ttu-id="d224b-152">**Birim testi .NET Core kullanarak dotnet testi**</span><span class="sxs-lookup"><span data-stu-id="d224b-152">**Unit testing in .NET Core using dotnet test**</span></span> <br/>
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="d224b-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="d224b-153">**xUnit.net**.</span></span> <span data-ttu-id="d224b-154">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="d224b-154">Official site.</span></span> <br/>
    [*https://xunit.github.io/*](https://xunit.github.io/)

- <span data-ttu-id="d224b-155">**Birim testi temel bilgileri.**</span><span class="sxs-lookup"><span data-stu-id="d224b-155">**Unit Test Basics.**</span></span> <br/>
    [*https://docs.microsoft.com/visualstudio/test/unit-test-basics*](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="d224b-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="d224b-156">**Moq**.</span></span> <span data-ttu-id="d224b-157">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="d224b-157">GitHub repo.</span></span> <br/>
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

- <span data-ttu-id="d224b-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="d224b-158">**NUnit**.</span></span> <span data-ttu-id="d224b-159">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="d224b-159">Official site.</span></span> <br/>
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="d224b-160">Çok kapsayıcılı bir uygulama üzerinde uygulama hizmet testleri</span><span class="sxs-lookup"><span data-stu-id="d224b-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="d224b-161">Çok kapsayıcılı uygulamaları test ederken daha önce belirtildiği gibi tüm mikro Hizmetleri Docker kapsayıcı ya da konak kümede çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d224b-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="d224b-162">Birden fazla mikro hizmetler içeren birden çok işlem içeren uçtan uca hizmet testleri gerektirir dağıtma ve docker çalıştırarak Docker ana tüm uygulama başlatma-compose up (veya bir orchestrator kullanıyorsanız benzer bir mekanizma).</span><span class="sxs-lookup"><span data-stu-id="d224b-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="d224b-163">Tüm uygulama ve tüm hizmetlerinin çalıştığını sonra uçtan uca tümleştirme ve işlevsel testler yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="d224b-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="d224b-164">Kullanabileceğiniz birkaç yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="d224b-164">There are a few approaches you can use.</span></span> <span data-ttu-id="d224b-165">Çözüm düzeyinde uygulamayı dağıtmak için kullandığınız docker-compose.yml dosyası içinde giriş noktasını kullanmak üzere genişletebilirsiniz [dotnet testi](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="d224b-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="d224b-166">Hedeflediğiniz görüntüde testlerinizi çalıştıracağınız başka bir compose dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d224b-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="d224b-167">Mikro hizmetler ve kapsayıcılar veritabanlarında içeren tümleştirme testleri için başka bir compose dosyası kullanarak, ilgili verileri her zaman özgün durumuna testleri çalıştırmadan önce sıfırlanacağını emin yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d224b-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="d224b-168">Compose uygulaması çalışır duruma geldikten sonra Visual Studio çalıştırıyorsanız, kesme noktaları ve özel durumlar yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d224b-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="d224b-169">Veya, tümleştirme testlerini otomatik olarak CI işlem hattınızdaki Azure DevOps Hizmetleri veya Docker kapsayıcılarını destekleyen herhangi bir CI/CD sisteminde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d224b-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="d224b-170">Hizmetine test etme</span><span class="sxs-lookup"><span data-stu-id="d224b-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="d224b-171">Başvuru uygulaması (hizmetine) testleri kısa bir süre önce yapmayın ve artık dört kategorisi vardır:</span><span class="sxs-lookup"><span data-stu-id="d224b-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="d224b-172">**Birim** testleri, yer alan, yalnızca düz eski Normal birim testleri **{MicroserviceName}. UnitTests** projeleri</span><span class="sxs-lookup"><span data-stu-id="d224b-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="d224b-173">**Mikro hizmet işlev/tümleştirme testleri**, her bir mikro hizmetin diğerlerinden yalıtılmış ancak altyapısı test çalışmalarıyla ilgili ve içerdiği **{MicroserviceName}. FunctionalTests** projeleri.</span><span class="sxs-lookup"><span data-stu-id="d224b-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="d224b-174">**Uygulama işlevsel/tümleştirme testleri**, mikro hizmetler tümleştirme, test çalışmaları birden fazla mikro hizmetler sağlama odaklanan.</span><span class="sxs-lookup"><span data-stu-id="d224b-174">**Application functional/integration tests**, that focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="d224b-175">Bu testler, projede bulunan **Application.FunctionalTests**.</span><span class="sxs-lookup"><span data-stu-id="d224b-175">These tests are located in project **Application.FunctionalTests**.</span></span>

4. <span data-ttu-id="d224b-176">**Yük testleri**, her bir mikro hizmetin yanıt süreleri, odaklanan.</span><span class="sxs-lookup"><span data-stu-id="d224b-176">**Load tests**, that focus on response times for each microservice.</span></span> <span data-ttu-id="d224b-177">Bu testler, projede bulunan **LoadTest** ve Visual Studio 2017 Enterprise Edition gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="d224b-177">These tests are located in project **LoadTest** and need Visual Studio 2017 Enterprise Edition.</span></span>

<span data-ttu-id="d224b-178">Mikro hizmet başına birim ve tümleştirme test içerdiği yük testleri Çözüm klasörü'ndeki test klasörü altında bulunan her mikro hizmet ve uygulama testi klasöründe Şekil 6-25 gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d224b-178">Unit and integration test per microservice are contained in a test folder in each microservice and Application a Load tests are contained under the test folder in the solution folder, as shown in Figure 6-25.</span></span>

![Testleri hizmetine yapısı: Her hizmetin birim ve işlev testleri içeren "test" klasörü vardır.](./media/image42.png)

<span data-ttu-id="d224b-181">**Şekil 6-25**.</span><span class="sxs-lookup"><span data-stu-id="d224b-181">**Figure 6-25**.</span></span> <span data-ttu-id="d224b-182">Hizmetine test klasör yapısı</span><span class="sxs-lookup"><span data-stu-id="d224b-182">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="d224b-183">Mikro hizmet ve uygulama işlevsel/tümleştirme testleri Visual Studio'da normal Test Çalıştırıcı kullanarak çalıştırılır ancak öncelikle gerekir gerekli altyapı hizmetleri başlatmak için testi klasöründe çözümde yer alan docker-compose dosyaları kümesi yoluyla :</span><span class="sxs-lookup"><span data-stu-id="d224b-183">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, by means of a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="d224b-184">**docker compose test.yml**</span><span class="sxs-lookup"><span data-stu-id="d224b-184">**docker-compose-test.yml**</span></span>

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

<span data-ttu-id="d224b-185">**docker compose test.override.yml**</span><span class="sxs-lookup"><span data-stu-id="d224b-185">**docker-compose-test.override.yml**</span></span>

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

<span data-ttu-id="d224b-186">Bu nedenle, işlev/tümleştirme testleri çalıştırmak için önce bu komut çözümü test klasöründen çalıştırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="d224b-186">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

``` console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="d224b-187">Gördüğünüz gibi bu docker-dosyaları yalnızca başlangıç Redis, RabbitMQ, SQL Server ve MongoDB mikro hizmetler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d224b-187">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d224b-188">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d224b-188">Additional resources</span></span>

- <span data-ttu-id="d224b-189">**Testleri Benioku dosyası** github'da hizmetine depoda</span><span class="sxs-lookup"><span data-stu-id="d224b-189">**Tests README file** on the eShopOnContainers repo on GitHub</span></span> <br/>
    [*https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test*](https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test)

- <span data-ttu-id="d224b-190">**Yük testleri Benioku dosyası** github'da hizmetine depoda</span><span class="sxs-lookup"><span data-stu-id="d224b-190">**Load tests README file** on the eShopOnContainers repo on GitHub</span></span> <br/>
    [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/)

> [!div class="step-by-step"]
> <span data-ttu-id="d224b-191">[Önceki](subscribe-events.md)
> [İleri](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="d224b-191">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>