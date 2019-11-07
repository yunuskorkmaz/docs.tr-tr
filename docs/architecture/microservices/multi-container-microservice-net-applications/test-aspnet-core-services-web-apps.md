---
title: ASP.NET Core hizmetlerini ve web uygulamalarını test etme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Kapsayıcılarda ASP.NET Core Hizmetleri ve Web uygulamalarını test etmek için bir mimari bulun.
ms.date: 10/02/2018
ms.openlocfilehash: 324b71d830bca43be71e8847fe2dd1b8b1593556
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739483"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="91a78-103">ASP.NET Core hizmetlerini ve web uygulamalarını test etme</span><span class="sxs-lookup"><span data-stu-id="91a78-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="91a78-104">Denetleyiciler, tüm ASP.NET Core API Service ve ASP.NET MVC web uygulamalarının merkezi bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="91a78-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="91a78-105">Bu nedenle, uygulamanız için amaçlanan gibi davrandıklarından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a78-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="91a78-106">Otomatikleştirilmiş testler size bu güvenilirliği sağlayabilir ve üretime ulaşmadan önce hataları tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="91a78-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="91a78-107">Denetleyicinin geçerli veya geçersiz girişlere göre nasıl davranacağını ve gerçekleştirdiği iş işleminin sonucuna bağlı olarak test denetleyicisi yanıtlarını test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a78-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="91a78-108">Ancak, mikro hizmetlerinizde bu tür testlerin olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="91a78-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="91a78-109">Birim testleri.</span><span class="sxs-lookup"><span data-stu-id="91a78-109">Unit tests.</span></span> <span data-ttu-id="91a78-110">Bu, uygulamanın ayrı bileşenlerinin beklenen şekilde çalışmasını güvence altına aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="91a78-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="91a78-111">Onaylar bileşen API 'sini test etme.</span><span class="sxs-lookup"><span data-stu-id="91a78-111">Assertions test the component API.</span></span>

- <span data-ttu-id="91a78-112">Tümleştirme testleri.</span><span class="sxs-lookup"><span data-stu-id="91a78-112">Integration tests.</span></span> <span data-ttu-id="91a78-113">Bu, bileşen etkileşimlerin veritabanları gibi dış yapılara karşı beklendiği gibi çalışmasını güvence altına aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="91a78-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="91a78-114">Onaylar, bileşen API 'sini, Kullanıcı arabirimini veya veritabanı g/ç, günlüğe kaydetme vb. gibi eylemlerin yan etkilerini test edebilir.</span><span class="sxs-lookup"><span data-stu-id="91a78-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="91a78-115">Her mikro hizmet için işlevsel testler.</span><span class="sxs-lookup"><span data-stu-id="91a78-115">Functional tests for each microservice.</span></span> <span data-ttu-id="91a78-116">Bu, uygulamanın kullanıcının perspektifinden beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="91a78-116">These ensure that the application works as expected from the user’s perspective.</span></span>

- <span data-ttu-id="91a78-117">Hizmet testleri.</span><span class="sxs-lookup"><span data-stu-id="91a78-117">Service tests.</span></span> <span data-ttu-id="91a78-118">Bu, birden çok hizmetin aynı anda test edilmesi de dahil olmak üzere uçtan uca hizmet kullanım örneklerinin test edilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="91a78-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="91a78-119">Bu test türü için öncelikle ortamı hazırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a78-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="91a78-120">Bu durumda, hizmetler (örneğin, Docker-Compose kullanarak) başlatılıyor demektir.</span><span class="sxs-lookup"><span data-stu-id="91a78-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="91a78-121">ASP.NET Core Web API 'Leri için birim testlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="91a78-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="91a78-122">Birim testi, bir uygulamanın bir bölümünün altyapısından ve bağımlılıklarından yalıtımıyla test edilmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="91a78-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="91a78-123">Birim test denetleyicisi mantığınızı kullandığınızda yalnızca tek bir eylemin veya metodun içeriği test edilir, bağımlılıkları veya çerçevenin kendisi değildir.</span><span class="sxs-lookup"><span data-stu-id="91a78-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="91a78-124">Birim testleri, tümleştirme testi amacı olan bileşenler arasındaki etkileşimle ilgili sorunları algılamaz.</span><span class="sxs-lookup"><span data-stu-id="91a78-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="91a78-125">Denetleyici eylemlerinizi birim testi yaparken, yalnızca davranışlarını odakladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="91a78-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="91a78-126">Denetleyici birimi testi, filtreler, yönlendirme veya model bağlama (istek verilerinin bir ViewModel veya DTO) gibi şeyleri önler.</span><span class="sxs-lookup"><span data-stu-id="91a78-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="91a78-127">Yalnızca bir şeyi test etmeye odaklandığından, birim testlerinin genellikle yazma ve hızlı çalışma için basit olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a78-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="91a78-128">İyi yazılmış bir birim testleri kümesi, çok fazla yük olmadan sık çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="91a78-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="91a78-129">Birim testleri xUnit.net, MSTest, moq veya NUnit gibi test çerçeveleri temelinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="91a78-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="91a78-130">EShopOnContainers örnek uygulaması için xUnit kullandık.</span><span class="sxs-lookup"><span data-stu-id="91a78-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="91a78-131">Bir Web API denetleyicisi için bir birim testi yazdığınızda, test, mümkün olduğunca hızlı çalışacak şekilde, C \# içindeki New anahtar sözcüğünü kullanarak doğrudan denetleyici sınıfını örnekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a78-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="91a78-132">Aşağıdaki örnek, [xUnit](https://xunit.github.io/) 'i test çerçevesi olarak kullanırken nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="91a78-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="91a78-133">Her mikro hizmet için tümleştirme ve işlevsel testleri uygulama</span><span class="sxs-lookup"><span data-stu-id="91a78-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="91a78-134">Belirtildiği gibi, tümleştirme testleri ve işlevsel testlerin farklı amaçları ve hedefleri vardır.</span><span class="sxs-lookup"><span data-stu-id="91a78-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="91a78-135">Ancak, ASP.NET Core denetleyicileri test edilirken her ikisini de aynı şekilde uyguladığınızda, bu bölümde tümleştirme testlerine odaklanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="91a78-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="91a78-136">Tümleştirme testi, bir uygulamanın bileşenlerinin, bir araya geldiğinde doğru şekilde çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="91a78-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="91a78-137">ASP.NET Core, birim test çerçeveleri ve ağ yükü olmadan istekleri işlemek için kullanılabilen yerleşik bir test Web ana bilgisayarı kullanılarak tümleştirme testini destekler.</span><span class="sxs-lookup"><span data-stu-id="91a78-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="91a78-138">Birim testinin aksine, tümleştirme sınamaları genellikle veritabanı, dosya sistemi, ağ kaynakları veya Web istekleri ve yanıtları gibi uygulama altyapısı sorunlarını kapsar.</span><span class="sxs-lookup"><span data-stu-id="91a78-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="91a78-139">Birim testleri, bu endişeler yerine Fakes veya sahte nesneler kullanır.</span><span class="sxs-lookup"><span data-stu-id="91a78-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="91a78-140">Ancak tümleştirme testlerinin amacı, sistemin bu sistemlerle beklendiği gibi çalıştığından emin olmak için, tümleştirme testi için Fakes veya sahte nesneler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="91a78-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="91a78-141">Bunun yerine, diğer hizmetlerden veritabanı erişimi veya hizmet çağrısı gibi altyapıyı dahil edersiniz.</span><span class="sxs-lookup"><span data-stu-id="91a78-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="91a78-142">Tümleştirme sınamaları, kod segmentlerinin birim testlerine göre daha büyük kesimlebildiğinden ve tümleştirme testleri altyapı öğelerini kullandığından, birim testlerinden daha yavaş bir şekilde sıra daha yavaş bir şekilde ücretlidir.</span><span class="sxs-lookup"><span data-stu-id="91a78-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="91a78-143">Bu nedenle, kaç tane tümleştirme testini yazıp çalıştıracağınızı kısıtlamak iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="91a78-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="91a78-144">ASP.NET Core, ağ yükü olmadan HTTP isteklerini işlemek için kullanılabilen yerleşik bir test Web ana bilgisayarı içerir, yani bu testleri gerçek bir Web ana bilgisayarı kullanırken daha hızlı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a78-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="91a78-145">Test Web ana bilgisayarı (TestServer), bir NuGet bileşeninde Microsoft. AspNetCore. TestHost olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91a78-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="91a78-146">Tümleştirme test projelerine eklenebilir ve ASP.NET Core uygulamalarını barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91a78-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="91a78-147">Aşağıdaki kodda görebileceğiniz gibi, ASP.NET Core denetleyicileri için tümleştirme testleri oluşturduğunuzda, denetleyicileri test ana bilgisayarı aracılığıyla örnekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a78-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="91a78-148">Bu bir HTTP isteğine benzer, ancak daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="91a78-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="91a78-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="91a78-149">Additional resources</span></span>

- <span data-ttu-id="91a78-150">**Steve Smith. Test denetleyicileri** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="91a78-150">**Steve Smith. Testing controllers** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="91a78-151">**Steve Smith. Tümleştirme testi** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="91a78-151">**Steve Smith. Integration testing** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="91a78-152">**DotNet test  \ kullanarak .NET Core 'Da birim testi**</span><span class="sxs-lookup"><span data-stu-id="91a78-152">**Unit testing in .NET Core using dotnet test** \</span></span>
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="91a78-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="91a78-153">**xUnit.net**.</span></span> <span data-ttu-id="91a78-154">Resmi site.</span><span class="sxs-lookup"><span data-stu-id="91a78-154">Official site.</span></span> \
    <https://xunit.github.io/>

- <span data-ttu-id="91a78-155">**Birim testi temelleri.**</span><span class="sxs-lookup"><span data-stu-id="91a78-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="91a78-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="91a78-156">**Moq**.</span></span> <span data-ttu-id="91a78-157">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="91a78-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="91a78-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="91a78-158">**NUnit**.</span></span> <span data-ttu-id="91a78-159">Resmi site.</span><span class="sxs-lookup"><span data-stu-id="91a78-159">Official site.</span></span> \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="91a78-160">Çok kapsayıcılı bir uygulamada hizmet testlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="91a78-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="91a78-161">Daha önce belirtildiği gibi, çok Kapsayıcılı uygulamaları test ettiğinizde, tüm mikro hizmetlerin Docker konağı veya kapsayıcı kümesi içinde çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a78-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="91a78-162">Birkaç mikro hizmeti içeren birden çok işlem içeren uçtan uca hizmet testleri, Docker-Compose ' i (veya bir Orchestrator kullanıyorsanız karşılaştırılabilir bir mekanizmayı) çalıştırarak tüm uygulamayı Docker konağında dağıtmanızı ve başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a78-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="91a78-163">Tüm uygulama ve tüm hizmetleri çalışır olduktan sonra, uçtan uca tümleştirmeyi ve işlevsel testleri çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a78-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="91a78-164">Kullanabileceğiniz birkaç yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="91a78-164">There are a few approaches you can use.</span></span> <span data-ttu-id="91a78-165">Uygulamayı çözüm düzeyinde dağıtmak için kullandığınız Docker-Compose. yıml dosyasında, [DotNet testini](../../../core/tools/dotnet-test.md)kullanmak için giriş noktasını genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a78-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="91a78-166">Ayrıca, hedeflediğiniz görüntüde testlerinizi çalıştıracak başka bir oluşturma dosyası da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a78-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="91a78-167">Mikro hizmetlerinizi ve kapsayıcılarındaki veritabanlarını içeren tümleştirme testleri için başka bir oluşturma dosyası kullanarak, testleri çalıştırmadan önce ilgili verilerin her zaman özgün durumuna sıfırlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="91a78-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="91a78-168">Oluşturma uygulaması çalışır duruma getirildikten sonra, Visual Studio çalıştırıyorsanız kesme noktalarından ve özel durumların avantajlarından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a78-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="91a78-169">Veya Azure DevOps Services veya Docker kapsayıcılarını destekleyen herhangi bir CI/CD sisteminde bulunan CI işlem hattınızda tümleştirme testlerini otomatik olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a78-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="91a78-170">EShopOnContainers 'da test etme</span><span class="sxs-lookup"><span data-stu-id="91a78-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="91a78-171">Başvuru uygulaması (eShopOnContainers) testleri yakın zamanda yeniden yapılandırılmış ve şu anda dört kategori var:</span><span class="sxs-lookup"><span data-stu-id="91a78-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="91a78-172">**Birim** testleri, **{mikro ServiceName} içinde yer alan yalnızca düz eski normal birim testleri. UnitTests** projeleri</span><span class="sxs-lookup"><span data-stu-id="91a78-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="91a78-173">**Mikro hizmet işlevsel/tümleştirme testleri**, her bir mikro hizmetin altyapısını içeren, ancak diğerlerinden yalıtılmış ve **{mikro ServiceName} içinde yer alan test çalışmaları. FunctionalTests** projeleri.</span><span class="sxs-lookup"><span data-stu-id="91a78-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="91a78-174">Birkaç mikro hizmet sunan test çalışmaları ile mikro hizmet tümleştirmesine odaklanarak **uygulama işlevsel/tümleştirme sınamaları**.</span><span class="sxs-lookup"><span data-stu-id="91a78-174">**Application functional/integration tests**, which focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="91a78-175">Bu testler Project **Application. FunctionalTests**içinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="91a78-175">These tests are located in project **Application.FunctionalTests**.</span></span>

4. <span data-ttu-id="91a78-176">Her mikro hizmet için yanıt sürelerine odaklanarak **Yük testleri**.</span><span class="sxs-lookup"><span data-stu-id="91a78-176">**Load tests**, which focus on response times for each microservice.</span></span> <span data-ttu-id="91a78-177">Bu sınamalar proje **LoadTest** ' de bulunur ve Visual Studio 2017 Enterprise Edition gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a78-177">These tests are located in project **LoadTest** and need Visual Studio 2017 Enterprise Edition.</span></span>

<span data-ttu-id="91a78-178">Mikro hizmet başına birim ve tümleştirme testi, her mikro hizmette bir test klasöründe bulunur ve uygulama, Şekil 6-25 ' de gösterildiği gibi çözüm klasöründeki test klasörü altında bir yük testi içerir.</span><span class="sxs-lookup"><span data-stu-id="91a78-178">Unit and integration test per microservice are contained in a test folder in each microservice and Application a Load tests are contained under the test folder in the solution folder, as shown in Figure 6-25.</span></span>

![Çözümdeki test projelerinin bazılarını gösteren ekran görüntüsü.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

<span data-ttu-id="91a78-180">**Şekil 6-25**.</span><span class="sxs-lookup"><span data-stu-id="91a78-180">**Figure 6-25**.</span></span> <span data-ttu-id="91a78-181">EShopOnContainers 'daki test klasörü yapısı</span><span class="sxs-lookup"><span data-stu-id="91a78-181">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="91a78-182">Mikro hizmet ve uygulama işlev/tümleştirme testleri, normal testler Çalıştırıcısı kullanılarak Visual Studio 'dan çalıştırılır, ancak önce çözüm sınama klasöründe yer alan bir Docker-Compose dosyaları kümesi aracılığıyla gerekli altyapı hizmetlerini başlatmanız gerekir :</span><span class="sxs-lookup"><span data-stu-id="91a78-182">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, by means of a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="91a78-183">**Docker-Compose-test. yıml**</span><span class="sxs-lookup"><span data-stu-id="91a78-183">**docker-compose-test.yml**</span></span>

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

<span data-ttu-id="91a78-184">**Docker-Compose-test. override. yıml**</span><span class="sxs-lookup"><span data-stu-id="91a78-184">**docker-compose-test.override.yml**</span></span>

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

<span data-ttu-id="91a78-185">Bu nedenle, işlev/tümleştirme testlerini çalıştırmak için önce bu komutu çözüm test klasöründen çalıştırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="91a78-185">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="91a78-186">Gördüğünüz gibi, bu Docker-Compose dosyaları yalnızca Redsıs, Kbbitmq, SQL Server ve MongoDB mikro hizmetlerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="91a78-186">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="91a78-187">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="91a78-187">Additional resources</span></span>

- <span data-ttu-id="91a78-188">GitHub 'daki eShopOnContainers deposunda **README dosyasını sınar**</span><span class="sxs-lookup"><span data-stu-id="91a78-188">**Tests README file** on the eShopOnContainers repo on GitHub \</span></span>
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- <span data-ttu-id="91a78-189">GitHub 'daki eShopOnContainers deposunda **yükleme Testlerı Benioku dosyası**</span><span class="sxs-lookup"><span data-stu-id="91a78-189">**Load tests README file** on the eShopOnContainers repo on GitHub \</span></span>
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> <span data-ttu-id="91a78-190">[Önceki](subscribe-events.md)
> [İleri](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="91a78-190">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
