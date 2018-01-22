---
title: "ASP.NET Core services ve web uygulamaları test etme"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | ASP.NET Core services ve web uygulamaları test etme"
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
ms.openlocfilehash: 80b7fa75344f8737baacfba6462a03b436fdf6a8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="62d7e-104">ASP.NET Core services ve web uygulamaları test etme</span><span class="sxs-lookup"><span data-stu-id="62d7e-104">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="62d7e-105">Denetleyicileri, tüm ASP.NET Core API hizmeti ve ASP.NET MVC Web uygulaması, merkezi bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="62d7e-105">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="62d7e-106">Bu nedenle, uygulamanız için tasarlandığı gibi davranırlar güven olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62d7e-106">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="62d7e-107">Otomatikleştirilmiş test üretim düşmeden önce hatalarını algılayabilir ve bu güvenle sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d7e-107">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="62d7e-108">Denetleyicinin geçerli veya geçersiz girişleri göre nasıl davranacağını test ve gerçekleştirdiği iş işlemi sonucuna denetleyicisi yanıtları test gerekir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-108">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="62d7e-109">Ancak, bu tür testler, mikro sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="62d7e-109">However, you should have these types of tests your microservices:</span></span>

-   <span data-ttu-id="62d7e-110">Birim testleri.</span><span class="sxs-lookup"><span data-stu-id="62d7e-110">Unit tests.</span></span> <span data-ttu-id="62d7e-111">Bu uygulamanın bileşenleri tek tek beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="62d7e-111">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="62d7e-112">Onaylar bileşen API sınayın.</span><span class="sxs-lookup"><span data-stu-id="62d7e-112">Assertions test the component API.</span></span>

-   <span data-ttu-id="62d7e-113">Tümleştirme sınar.</span><span class="sxs-lookup"><span data-stu-id="62d7e-113">Integration tests.</span></span> <span data-ttu-id="62d7e-114">Bu bileşen etkileşimleri veritabanları gibi dış yapıları karşı beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="62d7e-114">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="62d7e-115">Onaylar bileşen API'si, kullanıcı Arabirimi veya veritabanı g/ç gibi eylemleri günlüğe kaydetme, vb. yan etkileri test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d7e-115">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="62d7e-116">İşlevsel testleri her mikro hizmet için.</span><span class="sxs-lookup"><span data-stu-id="62d7e-116">Functional tests for each microservice.</span></span> <span data-ttu-id="62d7e-117">Bu, uygulama kullanıcının açısından beklendiği gibi çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="62d7e-117">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="62d7e-118">Hizmet sınar.</span><span class="sxs-lookup"><span data-stu-id="62d7e-118">Service tests.</span></span> <span data-ttu-id="62d7e-119">Bu, uçtan uca hizmeti kullanım örnekleri, aynı anda birden fazla hizmet testi dahil olmak üzere test edilmesini emin olun.</span><span class="sxs-lookup"><span data-stu-id="62d7e-119">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="62d7e-120">Bu tür sınama ortamı ilk hazırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-120">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="62d7e-121">Bu durumda, hizmetler başlatma anlamına gelir (örneğin, kullanarak docker-oluşturmanıza).</span><span class="sxs-lookup"><span data-stu-id="62d7e-121">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="62d7e-122">ASP.NET çekirdek Web API'leri için uygulama birim testleri</span><span class="sxs-lookup"><span data-stu-id="62d7e-122">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="62d7e-123">Birim testi haklarında altyapı ve bağımlılıklar ayrı bir uygulamanın bir bölümünü test içerir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-123">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="62d7e-124">Ne zaman, birim test denetleyicisi mantığı, yalnızca tek bir eylem içeriğini veya yöntemi test, değil davranışı bağımlılıklarından biri veya framework'ün.</span><span class="sxs-lookup"><span data-stu-id="62d7e-124">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="62d7e-125">Birim testleri algılanmayan sorunların bileşenleri arasındaki etkileşim — diğer bir deyişle tümleştirme sınaması amacı.</span><span class="sxs-lookup"><span data-stu-id="62d7e-125">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="62d7e-126">Test denetleyicisi eylemleriniz, birimi, yalnızca davranışlarını üzerinde odaklanmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="62d7e-126">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="62d7e-127">Denetleyici birim testi filtreleri, yönlendirme veya model bağlama gibi şeyleri önler.</span><span class="sxs-lookup"><span data-stu-id="62d7e-127">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="62d7e-128">Tek şey sınama odaklanmak için birim testleri yazmak basit ve hızlı çalıştırmak genellikle durumdadır.</span><span class="sxs-lookup"><span data-stu-id="62d7e-128">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="62d7e-129">Birim testleri iyi yazılmış bir dizi sık kadar ek yükü çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d7e-129">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="62d7e-130">Birim testleri test çerçevelerini xUnit.net, mstest'i, Moq veya NUnit gibi göre uygulanır.</span><span class="sxs-lookup"><span data-stu-id="62d7e-130">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="62d7e-131">XUnit eShopOnContainers örnek uygulama için kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="62d7e-131">For the eShopOnContainers sample application, we are using XUnit.</span></span>

<span data-ttu-id="62d7e-132">Birim testi için bir Web API denetleyicisi yazdığınızda, yeni anahtar sözcük C'de kullanarak doğrudan denetleyici sınıfının örneği\#, böylece test mümkün olduğunca hızlı çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="62d7e-132">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="62d7e-133">Aşağıdaki örnek kullanırken bunu gösterilmektedir [XUnit](https://xunit.github.io/) Test Çerçevesi olarak.</span><span class="sxs-lookup"><span data-stu-id="62d7e-133">The following example shows how to do this when using [XUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="62d7e-134">Uygulama tümleştirme ve her mikro hizmet için işlevsel testleri</span><span class="sxs-lookup"><span data-stu-id="62d7e-134">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="62d7e-135">Belirtildiği gibi tümleştirme testleri ve işlevsel testleri farklı amaçlar ve hedeflerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-135">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="62d7e-136">Bu bölümde biz tümleştirme testleri yoğunlaşabilirsiniz şekilde ancak her ikisi de ASP.NET Core denetleyicileri sınarken uygulamak benzer, yoludur.</span><span class="sxs-lookup"><span data-stu-id="62d7e-136">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="62d7e-137">Tümleştirme sınaması uygulamanın bileşenleri birleştirilen zaman doğru şekilde işlev sağlar.</span><span class="sxs-lookup"><span data-stu-id="62d7e-137">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="62d7e-138">ASP.NET Core destekler tümleştirme birim test çerçevelerini ve ağ yükü olmadan isteklerini işlemek için kullanılan bir yerleşik test web ana bilgisayarı kullanarak test etme.</span><span class="sxs-lookup"><span data-stu-id="62d7e-138">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="62d7e-139">Birim testi, tümleştirme testleri, bir veritabanı, dosya sistemi, ağ kaynaklarına veya web isteklerini ve yanıtlarını gibi uygulama altyapı sorunlarını sık içerir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-139">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="62d7e-140">Birim testleri veya bu sorunları yerine nesneleri mock fakes kullanın.</span><span class="sxs-lookup"><span data-stu-id="62d7e-140">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="62d7e-141">Ancak tümleştirme testleri amacı sistem bu sistemleriyle tümleştirme test etmek için fakes kullanmaz veya nesneler mock şekilde beklendiği gibi çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="62d7e-141">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="62d7e-142">Bunun yerine, diğer hizmetlerden veritabanı erişimi veya hizmet çağırma gibi altyapı içerir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-142">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="62d7e-143">Daha büyük kod parçalarını birim testleri daha tümleştirme testleri çalışma olduğundan ve tümleştirme testleri altyapı öğelerde dayandığından, bunlar büyüklük birim testleri yavaş olma eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-143">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="62d7e-144">Bu nedenle, yazma ve çalıştırma kaç tümleştirme testleri sınırlamak için bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-144">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="62d7e-145">ASP.NET Core size bu testler daha hızlı gerçek web ana bilgisayar kullanırken çalıştırabileceğiniz anlamına gelir, ağ yükü olmadan HTTP isteklerini işlemek için kullanılan bir yerleşik test web ana içerir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-145">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="62d7e-146">Test web ana bilgisayarı Microsoft.AspNetCore.TestHost NuGet bileşeninde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-146">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="62d7e-147">Tümleştirme test projeleri için eklenebilir ve konak ASP.NET Core uygulamaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62d7e-147">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="62d7e-148">Tümleştirme testleri için ASP.NET Core denetleyicileri oluşturduğunuzda aşağıdaki kodda görüldüğü gibi test ana bilgisayar üzerinden denetleyicileri örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62d7e-148">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="62d7e-149">Bu bir HTTP isteğini karşılaştırılabilir, ancak daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="62d7e-149">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="62d7e-150">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="62d7e-150">Additional resources</span></span>

-   <span data-ttu-id="62d7e-151">**Steve Smith. Test denetleyicileri** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="62d7e-151">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="62d7e-152">**Steve Smith. Tümleştirme sınaması** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span><span class="sxs-lookup"><span data-stu-id="62d7e-152">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span></span>

-   <span data-ttu-id="62d7e-153">**Birim testi .NET kullanarak dotnet test çekirdek**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span><span class="sxs-lookup"><span data-stu-id="62d7e-153">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span></span>

-   <span data-ttu-id="62d7e-154">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="62d7e-154">**xUnit.net**.</span></span> <span data-ttu-id="62d7e-155">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="62d7e-155">Official site.</span></span>
    [<span data-ttu-id="62d7e-156">*https://xunit.github.io/*</span><span class="sxs-lookup"><span data-stu-id="62d7e-156">*https://xunit.github.io/*</span></span>](https://xunit.github.io/)

-   <span data-ttu-id="62d7e-157">**Birim testi temelleri. ** 
     [ *https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="62d7e-157">**Unit Test Basics.**
[*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="62d7e-158">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="62d7e-158">**Moq**.</span></span> <span data-ttu-id="62d7e-159">GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="62d7e-159">GitHub repo.</span></span>
    [<span data-ttu-id="62d7e-160">*https://github.com/moq/moq*</span><span class="sxs-lookup"><span data-stu-id="62d7e-160">*https://github.com/moq/moq*</span></span>](https://github.com/moq/moq)

-   <span data-ttu-id="62d7e-161">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="62d7e-161">**NUnit**.</span></span> <span data-ttu-id="62d7e-162">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="62d7e-162">Official site.</span></span>
    [<span data-ttu-id="62d7e-163">*https://www.nunit.org/*</span><span class="sxs-lookup"><span data-stu-id="62d7e-163">*https://www.nunit.org/*</span></span>](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="62d7e-164">Uygulama hizmeti testleri çok kapsayıcı uygulama</span><span class="sxs-lookup"><span data-stu-id="62d7e-164">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="62d7e-165">Birden çok kapsayıcı uygulamaları test ettiğinizde daha önce belirtildiği gibi tüm mikro Docker ana bilgisayar veya kapsayıcı küme içinde çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="62d7e-165">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="62d7e-166">Birkaç mikro içeren birden çok işlemleri içeren uçtan uca hizmet testleri gerektirir dağıtma ve docker çalıştırarak Docker ana tüm uygulama başlatma-oluşturan Yukarı (veya bir orchestrator kullanıyorsanız karşılaştırılabilir bir mekanizma).</span><span class="sxs-lookup"><span data-stu-id="62d7e-166">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="62d7e-167">Tüm uygulama ve tüm hizmetlerinin çalıştığını sonra uçtan uca tümleştirme ve işlevsel testleri çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d7e-167">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="62d7e-168">Kullanabileceğiniz birkaç yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="62d7e-168">There are a few approaches you can use.</span></span> <span data-ttu-id="62d7e-169">Uygulama (veya docker compose.ci.build.yml gibi benzer olanlar) dağıtmak için kullandığınız docker-compose.yml dosyası çözüm düzeyinde kullanmak için giriş noktası genişletebilirsiniz [dotnet test](https://docs.microsoft.com/dotnet/core/tools/dotnet-test).</span><span class="sxs-lookup"><span data-stu-id="62d7e-169">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](https://docs.microsoft.com/dotnet/core/tools/dotnet-test).</span></span> <span data-ttu-id="62d7e-170">Ayrıca testleri, hedeflediğiniz görüntüde çalıştırırsınız: başka bir oluşturma dosyasını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d7e-170">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="62d7e-171">Mikro ve kapsayıcıları veritabanlarını içeren tümleştirme testleri için başka bir oluşturma dosyasını kullanarak, ilgili verileri her zaman özgün durumuna testleri çalıştırmadan önce sıfırlanacağını emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d7e-171">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="62d7e-172">Oluşturma uygulama hazır ve çalışır hale geldikten sonra Visual Studio çalıştırıyorsanız, kesme noktaları ve özel durumları yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d7e-172">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="62d7e-173">Veya tümleştirme testleri otomatik olarak CI hattınızı Visual Studio Team Services veya Docker kapsayıcıları destekleyen herhangi bir CI/CD sistemi içinde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d7e-173">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="62d7e-174">[Önceki] (abone-events.md) [sonraki] (.. /microservice-ddd-cqrs-Patterns/index.MD)</span><span class="sxs-lookup"><span data-stu-id="62d7e-174">[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
