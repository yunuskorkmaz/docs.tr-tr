---
title: ASP.NET Core hizmetlerini ve web uygulamalarını test etme
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | ASP.NET Core hizmetlerini ve web uygulamalarını kapsayıcılarda test etmek için bir mimari keşfedin.
ms.date: 01/30/2020
ms.openlocfilehash: f66d6184d913405c9372904f8072dda1dbfbe6ac
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988238"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="b4d51-103">ASP.NET Core hizmetlerini ve web uygulamalarını test etme</span><span class="sxs-lookup"><span data-stu-id="b4d51-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="b4d51-104">Denetleyiciler, herhangi bir ASP.NET Core API hizmetinin ve MVC Web uygulaması ASP.NETnın merkezi bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b4d51-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="b4d51-105">Bu nedenle, uygulamanız için amaçlandığı gibi çalıştıklarına güvenmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="b4d51-106">Otomatik testler size bu güveni sağlayabilir ve üretime ulaşmadan önce hataları algılayabilir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="b4d51-107">Denetleyicinin geçerli veya geçersiz girişlere göre nasıl hareket edeceğini sınamak ve gerçekleştirdiği iş işleminin sonucuna göre denetleyici yanıtlarını test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="b4d51-108">Ancak, mikro hizmetleriniz için bu tür testler olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b4d51-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="b4d51-109">Birim testleri.</span><span class="sxs-lookup"><span data-stu-id="b4d51-109">Unit tests.</span></span> <span data-ttu-id="b4d51-110">Bunlar, uygulamanın tek tek bileşenlerinin beklendiği gibi çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d51-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="b4d51-111">İddialar bileşen API sına.</span><span class="sxs-lookup"><span data-stu-id="b4d51-111">Assertions test the component API.</span></span>

- <span data-ttu-id="b4d51-112">Entegrasyon testleri.</span><span class="sxs-lookup"><span data-stu-id="b4d51-112">Integration tests.</span></span> <span data-ttu-id="b4d51-113">Bunlar, bileşen etkileşimlerinin veritabanları gibi dış yapılara karşı beklendiği gibi çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d51-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="b4d51-114">İddialar bileşen API,UI veya veritabanı G/Ç, günlük, vb. gibi eylemlerin yan etkilerini test edebilir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="b4d51-115">Her mikro hizmet için fonksiyonel testler.</span><span class="sxs-lookup"><span data-stu-id="b4d51-115">Functional tests for each microservice.</span></span> <span data-ttu-id="b4d51-116">Bunlar, uygulamanın kullanıcının bakış açısından beklendiği gibi çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d51-116">These ensure that the application works as expected from the user's perspective.</span></span>

- <span data-ttu-id="b4d51-117">Servis testleri.</span><span class="sxs-lookup"><span data-stu-id="b4d51-117">Service tests.</span></span> <span data-ttu-id="b4d51-118">Bunlar, aynı anda birden çok hizmeti test etmek de dahil olmak üzere uçlardan uca hizmet kullanım örneklerinin sınanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d51-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="b4d51-119">Bu tür bir test için önce ortamı hazırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="b4d51-120">Bu durumda, hizmetleri başlatmak anlamına gelir (örneğin, docker-comto up kullanarak).</span><span class="sxs-lookup"><span data-stu-id="b4d51-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="b4d51-121">ASP.NET Çekirdek Web API'leri için birim testleri uygulama</span><span class="sxs-lookup"><span data-stu-id="b4d51-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="b4d51-122">Birim testi, bir uygulamanın bir bölümünü altyapısından ve bağımlılıklarından izole olarak test etmektir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="b4d51-123">Test denetleyicisi mantığını birim lediğinizde, yalnızca tek bir eylemin veya yöntemin içeriği sınanır, bağımlılıklarının veya çerçevenin kendisinin davranışı değil.</span><span class="sxs-lookup"><span data-stu-id="b4d51-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="b4d51-124">Birim testleri, bileşenler arasındaki etkileşimdeki sorunları algılamaz, bu da tümleştirme testinin amacıdır.</span><span class="sxs-lookup"><span data-stu-id="b4d51-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="b4d51-125">Denetleyici eylemlerinizi bir araya getirerken, yalnızca davranışlarına odaklandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b4d51-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="b4d51-126">Denetleyici birim testi filtreler, yönlendirme veya model bağlama (istek verilerinin ViewModel veya DTO ile eşleştirilmesi) gibi şeyleri önler.</span><span class="sxs-lookup"><span data-stu-id="b4d51-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="b4d51-127">Onlar sadece bir şey test odaklanmak çünkü, birim testleri genellikle yazmak ve çalıştırmak için hızlı basittir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="b4d51-128">İyi yazılmış birim testleri kümesi çok fazla yükü olmadan sık sık çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="b4d51-129">Birim testleri xUnit.net, MSTest, Moq veya NUnit gibi test çerçevelerine göre uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b4d51-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="b4d51-130">eShopOnContainers örnek uygulaması için xUnit kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="b4d51-131">Bir Web API denetleyicisi için bir birim testi yazdığınızda, testin mümkün olduğunca\#hızlı çalışması için C'deki yeni anahtar sözcüğü kullanarak denetleyici sınıfını doğrudan anında alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="b4d51-132">Aşağıdaki örnek, test çerçevesi olarak [xUnit](https://xunit.github.io/) kullanırken bunu nasıl yapacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="b4d51-133">Her mikro hizmet için entegrasyon ve işlevsel testlerin uygulanması</span><span class="sxs-lookup"><span data-stu-id="b4d51-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="b4d51-134">Belirtildiği gibi, entegrasyon testleri ve fonksiyonel testler farklı amaç ve hedefleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b4d51-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="b4d51-135">Ancak, Core denetleyicileri ASP.NET test ederken her ikisini de uygulama şekliniz benzerdir, bu nedenle bu bölümde tümleştirme testlerine odaklanırız.</span><span class="sxs-lookup"><span data-stu-id="b4d51-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="b4d51-136">Tümleştirme sınama, bir uygulamanın bileşenlerinin monte edildiğinde düzgün çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d51-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="b4d51-137">ASP.NET Core, birim test çerçevelerini ve ağ yükü olmadan istekleri işlemek için kullanılabilecek yerleşik bir test web ana bilgisayarlarını kullanarak tümleştirme testini destekler.</span><span class="sxs-lookup"><span data-stu-id="b4d51-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="b4d51-138">Birim sınamanın aksine, tümleştirme testleri genellikle veritabanı, dosya sistemi, ağ kaynakları veya web istekleri ve yanıtları gibi uygulama altyapısı yla ilgili endişeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="b4d51-139">Birim testleri bu endişeler yerine sahte veya sahte nesneler kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4d51-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="b4d51-140">Ancak tümleştirme testlerinin amacı, sistemin beklendiği gibi çalıştığını doğrulamaktır, bu nedenle tümleştirme testi için sahte veya sahte nesneler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b4d51-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="b4d51-141">Bunun yerine, veritabanı erişimi veya diğer hizmetlerden hizmet çağırma gibi altyapıyı eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="b4d51-142">Tümleştirme testleri birim testlerinden daha büyük kod bölümlerini uyguladığından ve tümleştirme testleri altyapı öğelerine dayandığından, birim testlerinden daha yavaş büyüklük emirleri olma eğilimindedirler.</span><span class="sxs-lookup"><span data-stu-id="b4d51-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="b4d51-143">Bu nedenle, kaç tümleştirme testi yazıp çalıştırdığınızı sınırlamak iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="b4d51-144">ASP.NET Core, ağ yükü olmadan HTTP isteklerini işlemek için kullanılabilecek yerleşik bir test web ana bilgisayar içerir, yani bu testleri gerçek bir web ana bilgisayar kullanırken daha hızlı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster than when using a real web host.</span></span> <span data-ttu-id="b4d51-145">Test web ana bilgisayarı (TestServer), Microsoft.AspNetCore.TestHost olarak NuGet bileşeninde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="b4d51-146">Tümleştirme test projelerine eklenebilir ve ASP.NET Çekirdek uygulamalarını barındırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="b4d51-147">Aşağıdaki kodda görebileceğiniz gibi, ASP.NET Çekirdek denetleyicileri için tümleştirme testleri oluşturduğunuzda, denetleyicileri test ana bilgisayarı üzerinden anında alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="b4d51-148">Bu, bir HTTP isteğiyle karşılaştırılabilir, ancak daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="b4d51-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="b4d51-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b4d51-149">Additional resources</span></span>

- <span data-ttu-id="b4d51-150">**Steve Smith' i. Test denetleyicileri** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="b4d51-150">**Steve Smith. Testing controllers** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="b4d51-151">**Steve Smith' i. Entegrasyon testi** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="b4d51-151">**Steve Smith. Integration testing** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="b4d51-152">**Dotnet testi kullanarak .NET Core'da birim testi** </span><span class="sxs-lookup"><span data-stu-id="b4d51-152">**Unit testing in .NET Core using dotnet test** </span></span>\
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="b4d51-153">**xUnit.net.**</span><span class="sxs-lookup"><span data-stu-id="b4d51-153">**xUnit.net**.</span></span> <span data-ttu-id="b4d51-154">Resmi site.</span><span class="sxs-lookup"><span data-stu-id="b4d51-154">Official site.</span></span> \
    <https://xunit.github.io/>

- <span data-ttu-id="b4d51-155">**Ünite Test Temelleri.**</span><span class="sxs-lookup"><span data-stu-id="b4d51-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="b4d51-156">**Güve**.</span><span class="sxs-lookup"><span data-stu-id="b4d51-156">**Moq**.</span></span> <span data-ttu-id="b4d51-157">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="b4d51-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="b4d51-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="b4d51-158">**NUnit**.</span></span> <span data-ttu-id="b4d51-159">Resmi site.</span><span class="sxs-lookup"><span data-stu-id="b4d51-159">Official site.</span></span> \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="b4d51-160">Çoklu kapsayıcı uygulamasında servis testleri uygulama</span><span class="sxs-lookup"><span data-stu-id="b4d51-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="b4d51-161">Daha önce de belirtildiği gibi, çoklu kapsayıcı uygulamalarını test ettiğinizde, tüm mikro hizmetlerin Docker ana bilgisayar veya konteyner kümesi içinde çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="b4d51-162">Birden fazla mikro hizmeti içeren birden fazla işlemi içeren uçtan uca hizmet testleri, docker-comto'yu çalıştırarak (veya bir orkestratör kullanıyorsanız karşılaştırılabilir bir mekanizma) çalıştırarak docker ana bilgisayarda tüm uygulamayı dağıtmanızı ve başlatmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b4d51-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="b4d51-163">Tüm uygulama ve tüm hizmetleri çalıştırdıktan sonra uçuça tümleştirme ve işlevsel testler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="b4d51-164">Kullanabileceğiniz birkaç yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="b4d51-164">There are a few approaches you can use.</span></span> <span data-ttu-id="b4d51-165">Çözümüz düzeyinde uygulamayı dağıtmak için kullandığınız docker-compose.yml dosyasında [dotnet testini](../../../core/tools/dotnet-test.md)kullanmak için giriş noktasını genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="b4d51-166">Ayrıca, testlerinizi hedeflediğiniz resimde çalıştıracak başka bir oluşturma dosyası da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="b4d51-167">Kapsayıcılar üzerinde mikrohizmetler ve veritabanları içeren tümleştirme testleri için başka bir oluşturma dosyası kullanarak, ilgili verilerin testleri çalıştırmadan önce her zaman özgün durumuna sıfırlanır emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="b4d51-168">Oluşturma uygulaması çalışmaya başladığında, Visual Studio'yu çalıştırıyorsanız kesme noktalarından ve özel durumlardan yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="b4d51-169">Veya azure DevOps Hizmetlerinde veya Docker kapsayıcılarını destekleyen diğer CI/CD sisteminde, tümleştirme testlerini CI ardışık ardışık sisteminizde otomatik olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d51-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="b4d51-170">eShopOnContainers test</span><span class="sxs-lookup"><span data-stu-id="b4d51-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="b4d51-171">Referans uygulama (eShopOnContainers) testleri yakın zamanda yeniden yapılandırıldı ve şimdi dört kategori vardır:</span><span class="sxs-lookup"><span data-stu-id="b4d51-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="b4d51-172">**Birim** testleri, {MicroserviceName} içinde yer alan sadece düz eski normal birim **testleri. UnitTests** projeleri</span><span class="sxs-lookup"><span data-stu-id="b4d51-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="b4d51-173">**Microservice fonksiyonel/tümleştirme testleri,** her bir microservice için altyapı içeren ancak diğerlerinden izole ve **{MicroserviceName} bulunan test durumlarda. FunctionalTests** projeleri.</span><span class="sxs-lookup"><span data-stu-id="b4d51-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="b4d51-174">Mikro hizmet entegrasyonuna odaklanan **uygulama işlevsel/tümleştirme testleri,** çeşitli mikro hizmetler uygulayan test çalışmaları ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="b4d51-174">**Application functional/integration tests**, which focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="b4d51-175">Bu testler project **Application.FunctionalTests**bulunur.</span><span class="sxs-lookup"><span data-stu-id="b4d51-175">These tests are located in project **Application.FunctionalTests**.</span></span>

<span data-ttu-id="b4d51-176">Mikrohizmet başına birim ve entegrasyon testi her microservice bir test klasöründe yer almaktadır ve Uygulama bir Yük testleri Şekil 6-25'te gösterildiği gibi çözüm klasöründeki test klasörü altında yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="b4d51-176">Unit and integration test per microservice are contained in a test folder in each microservice and Application a Load tests are contained under the test folder in the solution folder, as shown in Figure 6-25.</span></span>

![VS'nin çözümdeki bazı test projelerini işaret eden ekran görüntüsü.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

<span data-ttu-id="b4d51-178">**Şekil 6-25**.</span><span class="sxs-lookup"><span data-stu-id="b4d51-178">**Figure 6-25**.</span></span> <span data-ttu-id="b4d51-179">eShopOnContainers test klasörü yapısı</span><span class="sxs-lookup"><span data-stu-id="b4d51-179">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="b4d51-180">Microservice ve Uygulama fonksiyonel/tümleştirme testleri Visual Studio'dan düzenli test koşucusu kullanılarak çalıştırılır, ancak öncelikle çözüm test klasöründe yer alan bir dizi docker-compose dosyası ile gerekli altyapı hizmetlerini başlatmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b4d51-180">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, by means of a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="b4d51-181">**docker-beste-test.yml**</span><span class="sxs-lookup"><span data-stu-id="b4d51-181">**docker-compose-test.yml**</span></span>

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

<span data-ttu-id="b4d51-182">**docker-compose-test.override.yml**</span><span class="sxs-lookup"><span data-stu-id="b4d51-182">**docker-compose-test.override.yml**</span></span>

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

<span data-ttu-id="b4d51-183">Bu nedenle, işlevsel/tümleştirme testlerini çalıştırmak için öncelikle çözüm test klasöründen bu komutu çalıştırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b4d51-183">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="b4d51-184">Gördüğünüz gibi, bu docker-beste dosyaları sadece Redis, RabbitMQ, SQL Server ve MongoDB microservices başlatın.</span><span class="sxs-lookup"><span data-stu-id="b4d51-184">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b4d51-185">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b4d51-185">Additional resources</span></span>

- <span data-ttu-id="b4d51-186">GitHub üzerinde eShopOnContainers repo testleri **README dosyası** </span><span class="sxs-lookup"><span data-stu-id="b4d51-186">**Tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- <span data-ttu-id="b4d51-187">**GitHub** üzerinde eShopOnContainers repo üzerinde Yük testleri README dosyası </span><span class="sxs-lookup"><span data-stu-id="b4d51-187">**Load tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> <span data-ttu-id="b4d51-188">[Önceki](subscribe-events.md)
> [Sonraki](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="b4d51-188">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
