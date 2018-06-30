---
title: Docker içinde - C# barındırılan mikro
description: ASP.NET Docker kapsayıcılarında çalıştırmak Çekirdek Hizmetleri oluşturmayı öğrenin
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 1f4b38243beb1210b1374bd701fac66b2fa72cc5
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106356"
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="17b86-103">Docker içinde barındırılan mikro</span><span class="sxs-lookup"><span data-stu-id="17b86-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="17b86-104">Bu öğretici oluşturmak ve ASP.NET Core mikro Docker kapsayıcısı içinde dağıtmak gerekli görevlerin ayrıntılarını verir.</span><span class="sxs-lookup"><span data-stu-id="17b86-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="17b86-105">Bu öğreticinin sürecinde şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="17b86-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="17b86-106">Bir ASP.NET Core uygulama oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="17b86-106">How to generate an ASP.NET Core application.</span></span>
* <span data-ttu-id="17b86-107">Bir geliştirme Docker ortamının nasıl oluşturulacağı.</span><span class="sxs-lookup"><span data-stu-id="17b86-107">How to create a development Docker environment.</span></span>
* <span data-ttu-id="17b86-108">Varolan bir görüntüyü temel alarak bir Docker görüntü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="17b86-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="17b86-109">Nasıl bir Docker kapsayıcıya hizmetinizi dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="17b86-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="17b86-110">Yol boyunca bazı C# dil özellikleri görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="17b86-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="17b86-111">C# nesnelerini JSON yüklerini dönüştürmek nasıl.</span><span class="sxs-lookup"><span data-stu-id="17b86-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="17b86-112">Sabit veri aktarım nesneleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="17b86-112">How to build immutable Data Transfer Objects.</span></span>
* <span data-ttu-id="17b86-113">Gelen HTTP isteklerini işleyen ve HTTP yanıtı oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="17b86-113">How to process incoming HTTP Requests and generate the HTTP Response.</span></span>
* <span data-ttu-id="17b86-114">Boş değer atanabilen değer türleri ile çalışmaya nasıl.</span><span class="sxs-lookup"><span data-stu-id="17b86-114">How to work with nullable value types.</span></span>

<span data-ttu-id="17b86-115">Yapabilecekleriniz [görüntüleyebilir veya örnek uygulama indirebilirsiniz](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) Bu konu için.</span><span class="sxs-lookup"><span data-stu-id="17b86-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="17b86-116">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="17b86-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="why-docker"></a><span data-ttu-id="17b86-117">Neden Docker?</span><span class="sxs-lookup"><span data-stu-id="17b86-117">Why Docker?</span></span>

<span data-ttu-id="17b86-118">Docker hizmetlerinizi bir veri merkezinde barındırılacağını standart makine görüntülerini oluşturmak kolaylaştırır veya genel bulut.</span><span class="sxs-lookup"><span data-stu-id="17b86-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="17b86-119">Docker yapılandırma resmi ve yükleme, uygulamanızın ölçeklendirmek için gerektiği şekilde çoğaltmak etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="17b86-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="17b86-120">Bu öğreticideki tüm kod tüm .NET Core ortamlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="17b86-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="17b86-121">Docker yükleme için ek görevler için bir ASP.NET Core uygulama çalışır.</span><span class="sxs-lookup"><span data-stu-id="17b86-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="17b86-122">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="17b86-122">Prerequisites</span></span>

<span data-ttu-id="17b86-123">.NET Core çalışmasına, makine Kurulum gerekir.</span><span class="sxs-lookup"><span data-stu-id="17b86-123">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="17b86-124">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="17b86-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="17b86-125">Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17b86-125">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="17b86-126">Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="17b86-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="17b86-127">Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/) platform Düzenleyicisi arası bir açık kaynak olduğu.</span><span class="sxs-lookup"><span data-stu-id="17b86-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="17b86-128">Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17b86-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="17b86-129">Docker altyapısına yüklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="17b86-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="17b86-130">Bkz: [Docker yükleme sayfası](http://www.docker.com/products/docker) platformunuza ilişkin yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="17b86-130">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="17b86-131">Docker, birçok Linux dağıtımları, macOS veya Windows yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="17b86-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="17b86-132">Yukarıda başvurulan sayfa her bir kullanılabilir yüklemeler bölümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="17b86-132">The page referenced above contains sections to each of the available installations.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="17b86-133">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="17b86-133">Create the Application</span></span>

<span data-ttu-id="17b86-134">Tüm Araçlar yüklediniz, yeni bir ASP.NET Core uygulaması, sık kullanılan Kabuğu'nda aşağıdaki komutu çalıştırarak "WeatherMicroservice" adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="17b86-134">Now that you've installed all the tools, create a new ASP.NET Core application in a directory called "WeatherMicroservice" by executing the following command in your favorite shell:</span></span>

```console
dotnet new web -o WeatherMicroservice
```

<span data-ttu-id="17b86-135">`dotnet` Komutu .NET geliştirme için gerekli araçları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="17b86-135">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="17b86-136">Her fiil farklı bir komut yürütür.</span><span class="sxs-lookup"><span data-stu-id="17b86-136">Each verb executes a different command.</span></span>

<span data-ttu-id="17b86-137">`dotnet new` Komutu .net oluşturmak için kullanılan çekirdek projeleri.</span><span class="sxs-lookup"><span data-stu-id="17b86-137">The `dotnet new` command is used to create .Net Core projects.</span></span>

<span data-ttu-id="17b86-138">`-o WeatherMicroservice` Sonra seçeneği `dotnet new` komutu ASP.NET Core uygulama oluşturmak için konum vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17b86-138">The `-o WeatherMicroservice` option after the `dotnet new` command is used to give the location to create the ASP.NET Core application.</span></span>

<span data-ttu-id="17b86-139">Kısa adını belirterek "ASP.NET Core boş" şablonu kullandık şekilde bu mikro hizmet için basit ve en basit bir web uygulaması mümkün istiyoruz `web`.</span><span class="sxs-lookup"><span data-stu-id="17b86-139">For this microservice, we want the simplest, most lightweight web application possible, so we used the "ASP.NET Core Empty" template, by specifying its short name, `web`.</span></span>

<span data-ttu-id="17b86-140">Şablon dört dosyaları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="17b86-140">The template creates four files for you:</span></span>

* <span data-ttu-id="17b86-141">Haline dosya.</span><span class="sxs-lookup"><span data-stu-id="17b86-141">A Startup.cs file.</span></span> <span data-ttu-id="17b86-142">Bu uygulamanın temel içerir.</span><span class="sxs-lookup"><span data-stu-id="17b86-142">This contains the basis of the application.</span></span>
* <span data-ttu-id="17b86-143">Program.cs dosyasının.</span><span class="sxs-lookup"><span data-stu-id="17b86-143">A Program.cs file.</span></span> <span data-ttu-id="17b86-144">Bu uygulama giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="17b86-144">This contains the entry point of the application.</span></span>
* <span data-ttu-id="17b86-145">Bir WeatherMicroservice.csproj dosyası.</span><span class="sxs-lookup"><span data-stu-id="17b86-145">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="17b86-146">Bu uygulama için yapı dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="17b86-146">This is the build file for the application.</span></span>
* <span data-ttu-id="17b86-147">Bir Properties/launchSettings.json dosyası.</span><span class="sxs-lookup"><span data-stu-id="17b86-147">A Properties/launchSettings.json file.</span></span> <span data-ttu-id="17b86-148">IDE tarafından kullanılan hata ayıklama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="17b86-148">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="17b86-149">Şimdi oluşturulan şablon uygulama çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b86-149">Now you can run the template generated application:</span></span>

```console
dotnet run
```

<span data-ttu-id="17b86-150">Bu komut ilk uygulamayı oluşturmak için gerekli bağımlılıkları geri yükler ve ardından uygulamayı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="17b86-150">This command will first restore dependencies required to build the application and then it will build the application.</span></span>

<span data-ttu-id="17b86-151">Varsayılan yapılandırma dinler `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="17b86-151">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="17b86-152">Bir tarayıcıda açabilir ve bu sayfaya gidin ve bir "Hello World!" konusuna bakın</span><span class="sxs-lookup"><span data-stu-id="17b86-152">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="17b86-153">İleti.</span><span class="sxs-lookup"><span data-stu-id="17b86-153">message.</span></span>

<span data-ttu-id="17b86-154">İşiniz bittiğinde, uygulama tuşlarına basarak kapatabilirsiniz <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="17b86-154">When you're done, you can shut down the application by pressing <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="17b86-155">Bir ASP.NET Core uygulama anatomisi</span><span class="sxs-lookup"><span data-stu-id="17b86-155">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="17b86-156">Uygulama oluşturduğunuza göre bu işlev nasıl uygulandığı konumundaki bakalım.</span><span class="sxs-lookup"><span data-stu-id="17b86-156">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="17b86-157">Bu noktada özellikle ilginç oluşturulan dosyalar iki vardır: WeatherMicroservice.csproj ve haline.</span><span class="sxs-lookup"><span data-stu-id="17b86-157">There are two of the generated files that are particularly interesting at this point: WeatherMicroservice.csproj and Startup.cs.</span></span> 

<span data-ttu-id="17b86-158">.Csproj dosyası proje hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="17b86-158">The .csproj file contains information about the project.</span></span>
<span data-ttu-id="17b86-159">En ilginç iki düğümler `<TargetFramework>` ve `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="17b86-159">The two nodes that are most interesting are `<TargetFramework>` and `<PackageReference>`.</span></span>

<span data-ttu-id="17b86-160">`<TargetFramework>` Düğümü Bu, uygulamanın çalıştırılacağı .NET sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="17b86-160">The `<TargetFramework>` node specifies the version of .NET that will run this application.</span></span>

<span data-ttu-id="17b86-161">Her `<PackageReference>` düğüm, bu uygulama için gerekli bir paket belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17b86-161">Each `<PackageReference>` node is used to specify a package that is needed for this application.</span></span>

<span data-ttu-id="17b86-162">Uygulama haline içinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="17b86-162">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="17b86-163">Bu dosya başlangıç sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="17b86-163">This file contains the startup class.</span></span>

<span data-ttu-id="17b86-164">İki yöntem yapılandırmak ve uygulamayı çalıştırmak için ASP.NET Core altyapısı tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="17b86-164">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="17b86-165">`ConfigureServices` Yöntemi bu uygulama için gerekli hizmetleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b86-165">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="17b86-166">Bağımlılıkları yapılandırmak gerekli olmayan şekilde yalın mikro hizmet oluşturmakta olduğunuz.</span><span class="sxs-lookup"><span data-stu-id="17b86-166">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="17b86-167">`Configure` Yöntemi işleyiciler gelen HTTP isteklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="17b86-167">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="17b86-168">Şablon 'Hello World!' metinle herhangi bir istek için yanıt veren basit bir işleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17b86-168">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="17b86-169">Bir mikro hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="17b86-169">Build a microservice</span></span>

<span data-ttu-id="17b86-170">Giderek oluşturmak için hizmet hava raporları yerden teslim eder dünya.</span><span class="sxs-lookup"><span data-stu-id="17b86-170">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="17b86-171">Bir üretim uygulamasında hava durumu verilerini almak için bazı hizmet çağırırdı.</span><span class="sxs-lookup"><span data-stu-id="17b86-171">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="17b86-172">Bizim örnek için size rastgele hava tahmini oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="17b86-172">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="17b86-173">Rastgele hava durumu hizmetimizi uygulamak üzere gerçekleştirmeniz gereken görevler vardır:</span><span class="sxs-lookup"><span data-stu-id="17b86-173">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="17b86-174">Enlem ve boylam okumak için gelen istek ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="17b86-174">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="17b86-175">Bazı rastgele tahmin verilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17b86-175">Generate some random forecast data.</span></span>
* <span data-ttu-id="17b86-176">Bu rastgele tahmin verilerini C# nesnelerden JSON paketlere dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="17b86-176">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="17b86-177">Hizmet gönderir JSON geri belirtmek için yanıt üstbilgisi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="17b86-177">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="17b86-178">Yanıt yazma.</span><span class="sxs-lookup"><span data-stu-id="17b86-178">Write the response.</span></span>

<span data-ttu-id="17b86-179">Sonraki bölümlerde, bu adımların her biri yol.</span><span class="sxs-lookup"><span data-stu-id="17b86-179">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="17b86-180">Sorgu dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="17b86-180">Parsing the Query String</span></span>

<span data-ttu-id="17b86-181">Sorgu dizesini ayrıştırarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="17b86-181">You'll begin by parsing the query string.</span></span> <span data-ttu-id="17b86-182">Hizmeti, 'lat' ve 'uzun' bağımsız değişkeni bu formda sorgu dizesini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="17b86-182">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

<span data-ttu-id="17b86-183">Bağımsız değişken olarak tanımlanan lambda ifadesi almanız gereken tüm değişiklikleri bulunan `app.Run` başlangıç sınıfınızda.</span><span class="sxs-lookup"><span data-stu-id="17b86-183">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="17b86-184">Lambda ifadesi bağımsız değişkeni `HttpContext` istek için.</span><span class="sxs-lookup"><span data-stu-id="17b86-184">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="17b86-185">Özelliklerinden biri olan `Request` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="17b86-185">One of its properties is the `Request` object.</span></span> <span data-ttu-id="17b86-186">`Request` Nesnesi bir `Query` istek için sorgu dizesinde tüm değerlerin sözlüğü içeren özelliği.</span><span class="sxs-lookup"><span data-stu-id="17b86-186">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="17b86-187">Enlem ve boylam değerlerini bulmak için ilk ektir bakın:</span><span class="sxs-lookup"><span data-stu-id="17b86-187">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="17b86-188">`Query` Sözlük değerler `StringValue` türü.</span><span class="sxs-lookup"><span data-stu-id="17b86-188">The `Query` dictionary values are `StringValue` type.</span></span> <span data-ttu-id="17b86-189">Bu tür dizeleri koleksiyonu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="17b86-189">That type can contain a collection of strings.</span></span> <span data-ttu-id="17b86-190">Hava durumu hizmetiniz için her bir değer tek bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="17b86-190">For your weather service, each value is a single string.</span></span> <span data-ttu-id="17b86-191">İşte çağrısı yok `FirstOrDefault()` Yukarıdaki kod.</span><span class="sxs-lookup"><span data-stu-id="17b86-191">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="17b86-192">Ardından, çiftleri için dizeleri dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="17b86-192">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="17b86-193">Dize için bir çift dönüştürmek için kullanılan yöntemi `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="17b86-193">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="17b86-194">Bu yöntem C# out Parametreleri giriş dizesi bir double dönüştürülüp dönüştürülemeyeceğini belirtmek için yararlanır.</span><span class="sxs-lookup"><span data-stu-id="17b86-194">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="17b86-195">Dize çift türü için geçerli bir temsili temsil ediyorsa, yöntem true döndürür ve `result` bağımsız değişken değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="17b86-195">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="17b86-196">Dize geçerli bir çift göstermiyor varsa yöntemi false değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="17b86-196">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="17b86-197">Bu API kullanarak uyarlayabilirsiniz bir *genişletme yöntemi* döndüren bir *boş değer atanabilir çift*.</span><span class="sxs-lookup"><span data-stu-id="17b86-197">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="17b86-198">A *boş değer atanabilir değer türü* bazı değer türü temsil eden bir tür olduğundan ve ayrıca eksik tutun veya null değer.</span><span class="sxs-lookup"><span data-stu-id="17b86-198">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="17b86-199">Boş değer atanabilir bir tür ekleyerek temsil edilen `?` türü bildirimi karakter.</span><span class="sxs-lookup"><span data-stu-id="17b86-199">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="17b86-200">Genişletme yöntemleri statik yöntemler, ancak ekleyerek tanımlanan yöntemlerdir `this` o sınıfın üyeleri olsa gibi ilk parametre değiştirici çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="17b86-200">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="17b86-201">Genişletme yöntemleri yalnızca statik sınıflarda tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="17b86-201">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="17b86-202">Ayrıştırma için genişletme yöntemi içeren sınıf tanımını şöyledir:</span><span class="sxs-lookup"><span data-stu-id="17b86-202">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="17b86-203">Genişletme yöntemi çağrılmadan önce geçerli kültür için değişmez değiştirin:</span><span class="sxs-lookup"><span data-stu-id="17b86-203">Before calling the extension method, change the current culture to invariant:</span></span>

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

<span data-ttu-id="17b86-204">Bu, uygulama ayrıştırıyor numaralarının aynı varsayılan kültürü bağımsız olarak herhangi bir sunucuda sağlar.</span><span class="sxs-lookup"><span data-stu-id="17b86-204">This ensures that your application parses numbers the same on any server, regardless of its default culture.</span></span>

<span data-ttu-id="17b86-205">Şimdi sorgu dizesi bağımsız değişkenleri çift türüne dönüştürmek için genişletme yöntemi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b86-205">Now you can use the extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="17b86-206">Kolayca ayrıştırma kodu test etmek için bağımsız değişkenlerin değerlerini dahil etmek için yanıt güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="17b86-206">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="17b86-207">Bu noktada, web uygulamasını çalıştırın ve ayrıştırma kodunuzu çalışıp çalışmadığını.</span><span class="sxs-lookup"><span data-stu-id="17b86-207">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="17b86-208">Bir tarayıcıda web isteğine değerlerini ekleyin ve güncelleştirilmiş sonuçları görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="17b86-208">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="17b86-209">Rastgele bir hava durumu tahmini derleme</span><span class="sxs-lookup"><span data-stu-id="17b86-209">Build a random weather forecast</span></span>

<span data-ttu-id="17b86-210">Sonraki göreviniz rastgele hava tahmini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="17b86-210">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="17b86-211">Hava tahmini için istediğiniz değerleri içeren bir veri kapsayıcısı ile başlayalım tıklatın:</span><span class="sxs-lookup"><span data-stu-id="17b86-211">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions =
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HighTemperatureFahrenheit { get; }
    public int LowTemperatureFahrenheit { get; }
    public int AverageWindSpeedMph { get; }
    public string Condition { get; }
}
```

<span data-ttu-id="17b86-212">Ardından, bu değerleri rastgele ayarlar bir oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="17b86-212">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="17b86-213">Bu oluşturucu enlem ve boylam çekirdek için değerleri kullanan `Random` sayı oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="17b86-213">This constructor uses the values for the latitude and longitude to seed the `Random` number generator.</span></span> <span data-ttu-id="17b86-214">Aynı konuma tahmin aynı olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="17b86-214">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="17b86-215">Enlem ve boylam bağımsız değişkenleri değiştirirseniz, çünkü (farklı çekirdek ile başlar) farklı bir tahmin elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="17b86-215">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed).</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="17b86-216">Bu gibi durumlarda, 5 gün tahmin şimdi yanıt yönteminizi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b86-216">You can now generate the 5-day forecast in your response method:</span></span>

```csharp
if (latitude.HasValue && longitude.HasValue)
{
    var forecast = new List<WeatherReport>();
    for (var days = 1; days <= 5; days++)
    {
        forecast.Add(new WeatherReport(latitude.Value, longitude.Value, days));
    }
}
```

### <a name="build-the-json-response"></a><span data-ttu-id="17b86-217">JSON yanıt oluşturma</span><span class="sxs-lookup"><span data-stu-id="17b86-217">Build the JSON response</span></span>

<span data-ttu-id="17b86-218">Sunucuda son kodu görev dönüştürmektir `WeatherReport` listesine JSON belgesi ve istemciye geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="17b86-218">The final code task on the server is to convert the `WeatherReport` list into JSON document, and send that back to the client.</span></span> <span data-ttu-id="17b86-219">JSON belgesini oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="17b86-219">Let's start by creating the JSON document.</span></span> <span data-ttu-id="17b86-220">Bağımlılıklar listesine Newtonsoft JSON seri hale getirici ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="17b86-220">You'll add the Newtonsoft JSON serializer to the list of dependencies.</span></span> <span data-ttu-id="17b86-221">Aşağıdaki kullanan yapabileceğiniz `dotnet` komutu:</span><span class="sxs-lookup"><span data-stu-id="17b86-221">You can do that using the following `dotnet` command:</span></span>

```console
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="17b86-222">Ardından, kullanabileceğiniz `JsonConvert` dizeye nesne yazmak için sınıf:</span><span class="sxs-lookup"><span data-stu-id="17b86-222">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="17b86-223">Yukarıdaki kod tahmin nesne dönüştürür (listesini `WeatherForecast` nesneler) bir JSON belgesine.</span><span class="sxs-lookup"><span data-stu-id="17b86-223">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON document.</span></span> <span data-ttu-id="17b86-224">Yanıt belgesi oluşturduktan sonra içerik türü ayarlayın `application/json`ve dize yazma.</span><span class="sxs-lookup"><span data-stu-id="17b86-224">After you've constructed the response document, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="17b86-225">Uygulamayı şimdi çalıştırır ve rastgele tahminlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="17b86-225">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="17b86-226">Docker yansıması oluştur</span><span class="sxs-lookup"><span data-stu-id="17b86-226">Build a Docker image</span></span>

<span data-ttu-id="17b86-227">Bizim son Docker içinde uygulamayı çalıştırmak için bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="17b86-227">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="17b86-228">Uygulamamız temsil eden bir Docker görüntü çalışan bir Docker kapsayıcısı oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="17b86-228">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="17b86-229">A ***Docker görüntü*** uygulamayı çalıştırmak için ortam tanımlayan bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="17b86-229">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="17b86-230">A ***Docker kapsayıcısı*** Docker görüntü çalışan bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17b86-230">A ***Docker Container*** represents a running instance of a Docker Image.</span></span>

<span data-ttu-id="17b86-231">Benzerleme tarafından düşünebilirsiniz *Docker görüntü* olarak bir *sınıfı*ve *Docker kapsayıcısı* bir nesne ya da bu sınıfının bir örneği olarak.</span><span class="sxs-lookup"><span data-stu-id="17b86-231">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="17b86-232">Aşağıdaki Dockerfile bizim amacıyla hizmet verecektir:</span><span class="sxs-lookup"><span data-stu-id="17b86-232">The following Dockerfile will serve for our purposes:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="17b86-233">Şimdi içeriğinin gidin.</span><span class="sxs-lookup"><span data-stu-id="17b86-233">Let's go over its contents.</span></span>

<span data-ttu-id="17b86-234">İlk satırı uygulama oluşturmak için kullanılan kaynak görüntüsü belirtir:</span><span class="sxs-lookup"><span data-stu-id="17b86-234">The first line specifies the source image used for building the application:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
```

<span data-ttu-id="17b86-235">Docker kaynak şablonunu temel alan bir makine görüntüsünün yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="17b86-235">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="17b86-236">Başlattığınızda tüm makine parametreler sağlamanız gerekmez anlamına yalnızca herhangi bir değişiklik sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="17b86-236">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="17b86-237">Değişiklikler burada uygulamamız eklenecek.</span><span class="sxs-lookup"><span data-stu-id="17b86-237">The changes here will be to include our application.</span></span>

<span data-ttu-id="17b86-238">Bu örnekte, kullanacağız `2.1-sdk` sürümü `dotnet` görüntü.</span><span class="sxs-lookup"><span data-stu-id="17b86-238">In this sample, we'll use the `2.1-sdk` version of the `dotnet` image.</span></span> <span data-ttu-id="17b86-239">Bu, çalışan bir Docker ortamı oluşturmak için en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="17b86-239">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="17b86-240">Bu görüntü, .NET çekirdeği çalışma zamanı ve .NET Core SDK'sı içerir.</span><span class="sxs-lookup"><span data-stu-id="17b86-240">This image includes the .NET Core runtime, and the .NET Core SDK.</span></span>
<span data-ttu-id="17b86-241">Kolaylaştırır başlamak ve yapı, ancak bu görüntü uygulama ve farklı bir görüntüsü oluşturmak için çalıştırmak için kullanacağız şekilde daha büyük bir görüntü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="17b86-241">That makes it easier to get started and build, but does create a larger image, so we'll use this image for building the application and a different image to run it.</span></span>

<span data-ttu-id="17b86-242">Sonraki satırların Kurulum ve uygulamanızı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="17b86-242">The next lines setup and build your application:</span></span>

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="17b86-243">Bu proje dosyası Docker VM geçerli dizinden kopyalayın ve tüm paketler geri yükleme.</span><span class="sxs-lookup"><span data-stu-id="17b86-243">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="17b86-244">Dotnet CLI kullanarak Docker görüntünün .NET Core SDK içermelidir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="17b86-244">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="17b86-245">Bundan sonra uygulamanızın rest kopyalanan ve `dotnet
publish` komut oluşturur ve uygulamanızı paketler.</span><span class="sxs-lookup"><span data-stu-id="17b86-245">After that, the rest of your application gets copied, and the `dotnet
publish` command builds and packages your application.</span></span>

<span data-ttu-id="17b86-246">Son olarak, uygulamayı çalıştıran ikinci bir Docker görüntü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="17b86-246">Finally, we create a second Docker image that runs the application:</span></span>

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="17b86-247">Bu görüntüyü kullanan `2.1-aspnetcore-runtime` sürümü `dotnet` ASP.NET Core uygulamaları çalıştırmak için gereken her şeyi içerir, ancak .NET Core SDK içermez görüntü.</span><span class="sxs-lookup"><span data-stu-id="17b86-247">This image uses the `2.1-aspnetcore-runtime` version of the `dotnet` image, which contains everything necessary to run ASP.NET Core applications, but does not include the .NET Core SDK.</span></span> <span data-ttu-id="17b86-248">Bu, .NET Core uygulamaları oluşturmak için bu görüntü kullanılamıyor, ancak Ayrıca son görüntünün küçük kılar anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="17b86-248">This means this image can't be used to build .NET Core applications, but it also makes the final image smaller.</span></span>

<span data-ttu-id="17b86-249">Bunun çalışmasını sağlamak için biz oluşturulmuş bir uygulamayı ilk görüntüden ikinci birine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="17b86-249">To make this work, we copy the built application from the first image to the second one.</span></span>

<span data-ttu-id="17b86-250">`ENTRYPOINT` Komut bildirir Docker hangi komutu hizmetini başlatır.</span><span class="sxs-lookup"><span data-stu-id="17b86-250">The `ENTRYPOINT` command informs Docker what command starts the service.</span></span>

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="17b86-251">Oluşturma ve görüntüyü bir kapsayıcıda çalıştırma</span><span class="sxs-lookup"><span data-stu-id="17b86-251">Building and running the image in a container</span></span>

<span data-ttu-id="17b86-252">Şimdi bir görüntü oluşturun ve Docker kapsayıcısı içinde hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="17b86-252">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="17b86-253">Yerel dizininizdeki görüntüsüne kopyalanan tüm dosyaları istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="17b86-253">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="17b86-254">Bunun yerine, kapsayıcı uygulamada yapı.</span><span class="sxs-lookup"><span data-stu-id="17b86-254">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="17b86-255">Oluşturacağınız bir `.dockerignore` dosya görüntüsüne kopyalanmaz dizinleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="17b86-255">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="17b86-256">Kopyalanan yapı varlıklar istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="17b86-256">You don't want any of the build assets copied.</span></span> <span data-ttu-id="17b86-257">Yapı belirtin ve dizinlerde yayımlayın `.dockerignore` dosyası:</span><span class="sxs-lookup"><span data-stu-id="17b86-257">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="17b86-258">Görüntü kullanarak yapı `docker build` komutu.</span><span class="sxs-lookup"><span data-stu-id="17b86-258">You build the image using the `docker build` command.</span></span> <span data-ttu-id="17b86-259">Kodunuzu içeren dizininden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="17b86-259">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="17b86-260">Bu komut, Dockerfile içindeki tüm bilgileri temel kapsayıcı görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17b86-260">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="17b86-261">`-t` Bağımsız değişkeni bir etiket veya bu kapsayıcı görüntü adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="17b86-261">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="17b86-262">Yukarıdaki komut satırında, Docker kapsayıcısı için kullanılan etiketi olan `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="17b86-262">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="17b86-263">Bu komut tamamlandığında, yeni hizmetinizi çalıştırılmaya hazır bir kapsayıcıya sahip.</span><span class="sxs-lookup"><span data-stu-id="17b86-263">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="17b86-264">Kapsayıcı başlatmak ve hizmetinizi başlatmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="17b86-264">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

<span data-ttu-id="17b86-265">`-d` Geçerli terminal durumundan ayrılmış kapsayıcı çalıştırmak seçenek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="17b86-265">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="17b86-266">Terminalinizde komut çıktısı görmezsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="17b86-266">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="17b86-267">`-p` Seçeneği, hizmet ve ana bilgisayar arasında bağlantı noktası eşleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="17b86-267">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="17b86-268">Burada herhangi bir gelen istek bağlantı noktası 80 üzerinde kapsayıcısı üzerinde 80 numaralı bağlantı noktasına iletilmesi gereken yazacaktır.</span><span class="sxs-lookup"><span data-stu-id="17b86-268">Here it says that any incoming request on port 80 should be forwarded to port 80 on the container.</span></span> <span data-ttu-id="17b86-269">80 kullanarak üretim uygulamaları için varsayılan bağlantı noktası olan hizmetinizi dinlediği bağlantı noktasını eşleşir.</span><span class="sxs-lookup"><span data-stu-id="17b86-269">Using 80 matches the port your service is listening on, which is the default port for production applications.</span></span> <span data-ttu-id="17b86-270">`--name` Bağımsız değişken adları, çalışan kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="17b86-270">The `--name` argument names your running container.</span></span> <span data-ttu-id="17b86-271">Bu kapsayıcı ile çalışmak için kullanabileceğiniz bir kolay adıdır.</span><span class="sxs-lookup"><span data-stu-id="17b86-271">It's a convenient name you can use to work with that container.</span></span>

<span data-ttu-id="17b86-272">Görüntü komutu denetleyerek çalışıp çalışmadığını görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b86-272">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="17b86-273">Kapsayıcı çalışıyorsa, çalışan işlemler listeleyen bir satırı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="17b86-273">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="17b86-274">(Yalnızca biri olabilir.)</span><span class="sxs-lookup"><span data-stu-id="17b86-274">(It may be the only one.)</span></span>

<span data-ttu-id="17b86-275">Bir tarayıcıda açmak ve localhost için gezinme ve enlem ve boylam belirterek hizmetinizi test edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b86-275">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="17b86-276">Çalışan bir kapsayıcı ekleme</span><span class="sxs-lookup"><span data-stu-id="17b86-276">Attaching to a running container</span></span>

<span data-ttu-id="17b86-277">Bir komut penceresinde hizmetinizi çalıştırdığınızda, her istek için yazdırılan tanılama bilgileri görebilir.</span><span class="sxs-lookup"><span data-stu-id="17b86-277">When you ran your service in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="17b86-278">Kapsayıcı ayrılmış modda çalışırken bu bilgileri görmüyorum.</span><span class="sxs-lookup"><span data-stu-id="17b86-278">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="17b86-279">Docker komut ekleme, günlük bilgilerini görebilmeniz için çalışan bir kapsayıcıya eklenecek sağlar.</span><span class="sxs-lookup"><span data-stu-id="17b86-279">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="17b86-280">Bir komut penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="17b86-280">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="17b86-281">`--sig-proxy=false` Bağımsız değişkeni anlamına <kbd>Ctrl</kbd>+<kbd>C</kbd> komutları kapsayıcı işleme gönderilen değil, ancak yerine Durdur `docker attach` komutu.</span><span class="sxs-lookup"><span data-stu-id="17b86-281">The `--sig-proxy=false` argument means that <kbd>Ctrl</kbd>+<kbd>C</kbd> commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="17b86-282">Son bağımsız değişkeni kapsayıcısında verilen addır `docker run` komutu.</span><span class="sxs-lookup"><span data-stu-id="17b86-282">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="17b86-283">Kapsayıcı kimliği atanan Docker, herhangi bir kapsayıcıya başvurmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17b86-283">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="17b86-284">Kapsayıcı için bir ad belirtirseniz kaydetmedi `docker run` kapsayıcı kimliğini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17b86-284">If you didn't specify a name for your container in `docker run` you must use the container ID.</span></span>

<span data-ttu-id="17b86-285">Bir tarayıcı açın ve hizmetinize gidin.</span><span class="sxs-lookup"><span data-stu-id="17b86-285">Open a browser and navigate to your service.</span></span> <span data-ttu-id="17b86-286">Tanılama iletileri ekli çalışan kapsayıcısından komutu Windows görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="17b86-286">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="17b86-287">Tuşuna <kbd>Ctrl</kbd>+<kbd>C</kbd> ekleme işlemi durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="17b86-287">Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the attach process.</span></span>

<span data-ttu-id="17b86-288">İşiniz bittiğinde, kapsayıcı ile çalışma, durdurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b86-288">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="17b86-289">Kapsayıcı ve görüntü yeniden başlatmak için hala mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="17b86-289">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="17b86-290">Kapsayıcı makinenizden kaldırmak istiyorsanız, bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="17b86-290">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="17b86-291">Kullanılmayan görüntüleri makinenizden kaldırmak istiyorsanız, bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="17b86-291">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="17b86-292">Sonuç</span><span class="sxs-lookup"><span data-stu-id="17b86-292">Conclusion</span></span> 

<span data-ttu-id="17b86-293">Bu öğreticide ASP.NET Core mikro hizmet yerleşik ve birkaç basit özellikler eklenir.</span><span class="sxs-lookup"><span data-stu-id="17b86-293">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="17b86-294">Bir Docker kapsayıcısı görüntü hizmetin yerleşik ve bu kapsayıcı, makinenizde çalıştı.</span><span class="sxs-lookup"><span data-stu-id="17b86-294">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="17b86-295">Bir terminal penceresi hizmete bağlı ve tanılama iletileri hizmetinizden gördünüz.</span><span class="sxs-lookup"><span data-stu-id="17b86-295">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="17b86-296">Yol boyunca eylem C# dilinin çeşitli özellikler gördünüz.</span><span class="sxs-lookup"><span data-stu-id="17b86-296">Along the way, you saw several features of the C# language in action.</span></span>
