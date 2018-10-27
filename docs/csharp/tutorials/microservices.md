---
title: Docker içinde barındırılan mikro Hizmetleri-C#
description: ASP.NET Docker kapsayıcılarında çalıştıracak bir Çekirdek Hizmetleri oluşturmayı öğrenin
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b1f7159a222ab4d68715844e9997ca922676bc80
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454492"
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="995fb-103">Docker içinde barındırılan mikro hizmetler</span><span class="sxs-lookup"><span data-stu-id="995fb-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="995fb-104">Bu öğreticide oluşturun ve bir Docker kapsayıcısında bir ASP.NET Core mikro hizmet dağıtmak için gereken görevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="995fb-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="995fb-105">Bu öğreticide Kurs sırasında şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="995fb-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="995fb-106">Bir ASP.NET Core uygulaması oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="995fb-106">How to generate an ASP.NET Core application.</span></span>
* <span data-ttu-id="995fb-107">Docker geliştirme ortamı oluşturma</span><span class="sxs-lookup"><span data-stu-id="995fb-107">How to create a development Docker environment.</span></span>
* <span data-ttu-id="995fb-108">Mevcut bir görüntüyle bir Docker görüntüsünü oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="995fb-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="995fb-109">Hizmetiniz bir Docker kapsayıcısına dağıtma</span><span class="sxs-lookup"><span data-stu-id="995fb-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="995fb-110">Bu doğrultuda, ayrıca bazı görürsünüz C# dil özellikleri:</span><span class="sxs-lookup"><span data-stu-id="995fb-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="995fb-111">Dönüştürme C# JSON yükü nesneleri.</span><span class="sxs-lookup"><span data-stu-id="995fb-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="995fb-112">Sabit veri aktarımı nesneleri oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="995fb-112">How to build immutable Data Transfer Objects.</span></span>
* <span data-ttu-id="995fb-113">HTTP yanıtı oluşturur ve gelen HTTP isteklerini işlemek nasıl.</span><span class="sxs-lookup"><span data-stu-id="995fb-113">How to process incoming HTTP Requests and generate the HTTP Response.</span></span>
* <span data-ttu-id="995fb-114">Boş değer atanabilen değer türleri ile çalışmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="995fb-114">How to work with nullable value types.</span></span>

<span data-ttu-id="995fb-115">Yapabilecekleriniz [görüntülemek veya örnek uygulamasını indirin](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) için bu konuda.</span><span class="sxs-lookup"><span data-stu-id="995fb-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="995fb-116">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="995fb-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="why-docker"></a><span data-ttu-id="995fb-117">Neden Docker?</span><span class="sxs-lookup"><span data-stu-id="995fb-117">Why Docker?</span></span>

<span data-ttu-id="995fb-118">Docker hizmetlerinizi bir veri merkezinde barındırılacağını standart makine görüntülerini oluşturmak kolaylaştırır ve genel bulut.</span><span class="sxs-lookup"><span data-stu-id="995fb-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="995fb-119">Docker görüntüsü yapılandırmak ve uygulamanın yüklenmesi ölçeklendirmek için gerektiği şekilde çoğaltmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="995fb-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="995fb-120">Bu öğreticideki tüm kod herhangi bir .NET Core ortamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="995fb-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="995fb-121">Docker yükleme için ek görevler, bir ASP.NET Core uygulaması için çalışır.</span><span class="sxs-lookup"><span data-stu-id="995fb-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="995fb-122">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="995fb-122">Prerequisites</span></span>

<span data-ttu-id="995fb-123">.NET Core çalıştırmak için makinenizi ayarlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="995fb-123">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="995fb-124">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="995fb-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="995fb-125">Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="995fb-125">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="995fb-126">Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="995fb-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="995fb-127">Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/) açık kaynaklı, çapraz platform Düzenleyicisi olduğu.</span><span class="sxs-lookup"><span data-stu-id="995fb-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="995fb-128">Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="995fb-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="995fb-129">Docker Altyapısı'nı gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="995fb-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="995fb-130">Bkz: [Docker yükleme sayfası](https://docs.docker.com/install/overview/) platformunuza yönelik yönergeler.</span><span class="sxs-lookup"><span data-stu-id="995fb-130">See the [Docker Installation page](https://docs.docker.com/install/overview/) for instructions for your platform.</span></span>
<span data-ttu-id="995fb-131">Docker, çok sayıda Linux dağıtımlarına, macOS veya Windows yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="995fb-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="995fb-132">Yukarıda anılan sayfa her kullanılabilir yüklemeler bölümler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="995fb-132">The page referenced above contains sections to each of the available installations.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="995fb-133">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="995fb-133">Create the Application</span></span>

<span data-ttu-id="995fb-134">Tüm Araçlar yüklediğinize göre sık kullanılan shell'de aşağıdaki komutu yürüterek "WeatherMicroservice" adlı bir dizinde yeni bir ASP.NET Core uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="995fb-134">Now that you've installed all the tools, create a new ASP.NET Core application in a directory called "WeatherMicroservice" by executing the following command in your favorite shell:</span></span>

```console
dotnet new web -o WeatherMicroservice
```

<span data-ttu-id="995fb-135">`dotnet` .NET geliştirme için gerekli araçları komutu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="995fb-135">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="995fb-136">Her bir fiil, farklı bir komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="995fb-136">Each verb executes a different command.</span></span>

<span data-ttu-id="995fb-137">`dotnet new` .Net Core oluşturmak için kullanılan komut projeleri.</span><span class="sxs-lookup"><span data-stu-id="995fb-137">The `dotnet new` command is used to create .Net Core projects.</span></span>

<span data-ttu-id="995fb-138">`-o WeatherMicroservice` Sonra seçeneği `dotnet new` komutu, ASP.NET Core uygulaması oluşturmak için konum vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="995fb-138">The `-o WeatherMicroservice` option after the `dotnet new` command is used to give the location to create the ASP.NET Core application.</span></span>

<span data-ttu-id="995fb-139">"ASP.NET Core boş" şablonu kısa adını belirterek kullandığımız için bu mikro hizmet için basit ve en basit bir web uygulaması mümkün istiyoruz `web`.</span><span class="sxs-lookup"><span data-stu-id="995fb-139">For this microservice, we want the simplest, most lightweight web application possible, so we used the "ASP.NET Core Empty" template, by specifying its short name, `web`.</span></span>

<span data-ttu-id="995fb-140">Şablon dört dosyaları sizin için oluşturur:</span><span class="sxs-lookup"><span data-stu-id="995fb-140">The template creates four files for you:</span></span>

* <span data-ttu-id="995fb-141">Startup.cs dosya.</span><span class="sxs-lookup"><span data-stu-id="995fb-141">A Startup.cs file.</span></span> <span data-ttu-id="995fb-142">Bu, uygulamanın temel içerir.</span><span class="sxs-lookup"><span data-stu-id="995fb-142">This contains the basis of the application.</span></span>
* <span data-ttu-id="995fb-143">Program.cs dosyasının bir.</span><span class="sxs-lookup"><span data-stu-id="995fb-143">A Program.cs file.</span></span> <span data-ttu-id="995fb-144">Bu, uygulamanın giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="995fb-144">This contains the entry point of the application.</span></span>
* <span data-ttu-id="995fb-145">WeatherMicroservice.csproj dosya.</span><span class="sxs-lookup"><span data-stu-id="995fb-145">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="995fb-146">Bu uygulama için derleme dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="995fb-146">This is the build file for the application.</span></span>
* <span data-ttu-id="995fb-147">Properties/launchSettings.json dosya.</span><span class="sxs-lookup"><span data-stu-id="995fb-147">A Properties/launchSettings.json file.</span></span> <span data-ttu-id="995fb-148">Bu, IDE'ler tarafından kullanılan hata ayıklama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="995fb-148">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="995fb-149">Artık şablon oluşturulan uygulamayı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="995fb-149">Now you can run the template generated application:</span></span>

```console
dotnet run
```

<span data-ttu-id="995fb-150">Bu komut, ilk uygulamayı oluşturmak için gerekli bağımlılıkları geri yükler ve ardından uygulamayı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="995fb-150">This command will first restore dependencies required to build the application and then it will build the application.</span></span>

<span data-ttu-id="995fb-151">Varsayılan yapılandırma dinleyen `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="995fb-151">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="995fb-152">Bir tarayıcıda açabilir ve söz konusu sayfaya gidin ve bir "Hello World!" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="995fb-152">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="995fb-153">İleti.</span><span class="sxs-lookup"><span data-stu-id="995fb-153">message.</span></span>

<span data-ttu-id="995fb-154">İşiniz bittiğinde tuşlarına basarak uygulamayı kapatabilirsiniz <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="995fb-154">When you're done, you can shut down the application by pressing <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="995fb-155">Bir ASP.NET Core uygulaması anatomisi</span><span class="sxs-lookup"><span data-stu-id="995fb-155">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="995fb-156">Uygulamayı oluşturduğunuza göre bu işlevselliği nasıl uygulandığını konumunda göz atalım.</span><span class="sxs-lookup"><span data-stu-id="995fb-156">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="995fb-157">Bu noktada özellikle ilgi çekici oluşturulan dosyaların iki: WeatherMicroservice.csproj ve Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="995fb-157">There are two of the generated files that are particularly interesting at this point: WeatherMicroservice.csproj and Startup.cs.</span></span> 

<span data-ttu-id="995fb-158">.Csproj dosyasını proje hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="995fb-158">The .csproj file contains information about the project.</span></span>
<span data-ttu-id="995fb-159">En ilginç iki düğümler `<TargetFramework>` ve `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="995fb-159">The two nodes that are most interesting are `<TargetFramework>` and `<PackageReference>`.</span></span>

<span data-ttu-id="995fb-160">`<TargetFramework>` Düğümü Bu, uygulamanın çalıştırılacağı .NET sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="995fb-160">The `<TargetFramework>` node specifies the version of .NET that will run this application.</span></span>

<span data-ttu-id="995fb-161">Her `<PackageReference>` düğüm, bu uygulama için gerekli olan bir paketi belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="995fb-161">Each `<PackageReference>` node is used to specify a package that is needed for this application.</span></span>

<span data-ttu-id="995fb-162">Uygulama, Startup.cs içinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="995fb-162">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="995fb-163">Bu dosya, başlangıç sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="995fb-163">This file contains the startup class.</span></span>

<span data-ttu-id="995fb-164">İki yöntem yapılandırmak ve uygulamayı çalıştırmak için ASP.NET Core altyapısı tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="995fb-164">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="995fb-165">`ConfigureServices` Yöntemi, bu uygulama için gerekli olan hizmetlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="995fb-165">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="995fb-166">Herhangi bir bağımlılığın yapılandırmak gerekli olmayan şekilde yalın bir mikro hizmet oluşturuyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="995fb-166">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="995fb-167">`Configure` Yöntemi için gelen HTTP isteklerini işleyicileri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="995fb-167">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="995fb-168">Şablon 'Hello World!' metin herhangi bir istekle yanıt veren basit bir işleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="995fb-168">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="995fb-169">Bir mikro hizmet oluşturun</span><span class="sxs-lookup"><span data-stu-id="995fb-169">Build a microservice</span></span>

<span data-ttu-id="995fb-170">İlerlememesi ileride oluşturmak için hizmet hava durumu raporları yerden verecektir dünya.</span><span class="sxs-lookup"><span data-stu-id="995fb-170">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="995fb-171">Bir üretim uygulamasında, hava durumu verilerini almak için bazı hizmet çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="995fb-171">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="995fb-172">Bizim Örneğimiz için rastgele bir hava durumu tahminini başlığında oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="995fb-172">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="995fb-173">Birkaç rastgele hava durumu hizmetimiz uygulamak için gerçekleştirmeniz gereken görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="995fb-173">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="995fb-174">Enlem ve boylamını okumak için gelen istek ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="995fb-174">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="995fb-175">Bazı rastgele tahmin veriler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="995fb-175">Generate some random forecast data.</span></span>
* <span data-ttu-id="995fb-176">Bu rastgele tahmin verilerden dönüştürme C# JSON paketleri nesneleri.</span><span class="sxs-lookup"><span data-stu-id="995fb-176">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="995fb-177">Yanıt üst bilgisi, hizmet gönderir JSON geri belirtmek üzere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="995fb-177">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="995fb-178">Yanıt yazın.</span><span class="sxs-lookup"><span data-stu-id="995fb-178">Write the response.</span></span>

<span data-ttu-id="995fb-179">Sonraki bölümlerde, bu adımların her biri yol.</span><span class="sxs-lookup"><span data-stu-id="995fb-179">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="995fb-180">Sorgu dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="995fb-180">Parsing the Query String</span></span>

<span data-ttu-id="995fb-181">Sorgu dizesini ayrıştırarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="995fb-181">You'll begin by parsing the query string.</span></span> <span data-ttu-id="995fb-182">Hizmet, 'lat' ve 'uzun' bağımsız değişkenleri bu formda sorgu dizesini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="995fb-182">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

<span data-ttu-id="995fb-183">Lambda ifadesi bağımsız değişkeni olarak tanımlanan almanız gereken tüm değişiklikleri bulunan `app.Run` başlangıç sınıfınızdaki.</span><span class="sxs-lookup"><span data-stu-id="995fb-183">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="995fb-184">Lambda ifadesi bağımsız değişkeni `HttpContext` istek için.</span><span class="sxs-lookup"><span data-stu-id="995fb-184">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="995fb-185">Kendi özelliklerinden biri `Request` nesne.</span><span class="sxs-lookup"><span data-stu-id="995fb-185">One of its properties is the `Request` object.</span></span> <span data-ttu-id="995fb-186">`Request` Nesnesinin bir `Query` özelliği içeren bir istek için sorgu dizesini tüm değerlerin sözlüğü.</span><span class="sxs-lookup"><span data-stu-id="995fb-186">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="995fb-187">Enlem ve boylam değerleri bulmak için ilk toplama şöyledir:</span><span class="sxs-lookup"><span data-stu-id="995fb-187">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="995fb-188">`Query` Sözlük değerler `StringValue` türü.</span><span class="sxs-lookup"><span data-stu-id="995fb-188">The `Query` dictionary values are `StringValue` type.</span></span> <span data-ttu-id="995fb-189">Bu tür, dizelerden oluşan bir koleksiyonu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="995fb-189">That type can contain a collection of strings.</span></span> <span data-ttu-id="995fb-190">Hava durumu hizmetiniz için her değeri tek bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="995fb-190">For your weather service, each value is a single string.</span></span> <span data-ttu-id="995fb-191">İşte bu çağrı yoktur `FirstOrDefault()` Yukarıdaki kod.</span><span class="sxs-lookup"><span data-stu-id="995fb-191">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="995fb-192">Ardından, Double için dizeleri dönüştürmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="995fb-192">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="995fb-193">Double'a dize dönüştürmek için kullanacağınız yöntemdir `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="995fb-193">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="995fb-194">Bu yöntem yararlanır C# out parametreleri için bir double dönüştürülebilir giriş dizesini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="995fb-194">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="995fb-195">Dize geçerli bir çift temsili temsil ediyorsa true, döner ve `result` bağımsız değişken değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="995fb-195">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="995fb-196">Yöntemi, dize geçerli bir çift göstermiyor değilse false döndürür.</span><span class="sxs-lookup"><span data-stu-id="995fb-196">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="995fb-197">Bu API kullanımı ile uyum sağlayabilen bir *genişletme yöntemi* döndüren bir *boş değer atanabilir çift*.</span><span class="sxs-lookup"><span data-stu-id="995fb-197">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="995fb-198">A *null değer türü* bazı değer türünü temsil eden bir türdür ve ayrıca bir eksik tutun veya null değeri.</span><span class="sxs-lookup"><span data-stu-id="995fb-198">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="995fb-199">Boş değer atanabilir bir tür eklenerek temsil edilen `?` türü bildirimi için karakter.</span><span class="sxs-lookup"><span data-stu-id="995fb-199">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="995fb-200">Genişletme yöntemleri statik yöntemler, ancak ekleyerek tanımladığınız yöntemlerdir `this` ilk parametre değiştiricisi, sınıf üyesi olduğu gibi sorgulamanıza çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="995fb-200">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="995fb-201">Uzantı yöntemleri yalnızca statik sınıf içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="995fb-201">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="995fb-202">Ayrıştırma için genişletme yöntemi içeren sınıf tanımı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="995fb-202">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="995fb-203">Genişletme yöntemi çağrılmadan önce geçerli kültürü için sabit değiştirin:</span><span class="sxs-lookup"><span data-stu-id="995fb-203">Before calling the extension method, change the current culture to invariant:</span></span>

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

<span data-ttu-id="995fb-204">Bu, uygulama ayrıştırıyor numaralarının aynı varsayılan kültürünü bağımsız olarak herhangi bir sunucuda sağlar.</span><span class="sxs-lookup"><span data-stu-id="995fb-204">This ensures that your application parses numbers the same on any server, regardless of its default culture.</span></span>

<span data-ttu-id="995fb-205">Artık sorgu dizesi bağımsız değişkenleri çift türüne dönüştürmeye genişletme yöntemini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="995fb-205">Now you can use the extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="995fb-206">Kolayca ayrıştırma kodunu test etmek için bağımsız değişkenlerin değerlerini dahil etmek için yanıt güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="995fb-206">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="995fb-207">Bu noktada, web uygulamasını çalıştırmak ve ayrıştırma kodunuzu çalışıp çalışmadığını.</span><span class="sxs-lookup"><span data-stu-id="995fb-207">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="995fb-208">Bir tarayıcıda web isteği değerlerini ekleyin ve güncelleştirilmiş sonuçları görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="995fb-208">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="995fb-209">Rastgele bir hava durumu tahminini oluşturun</span><span class="sxs-lookup"><span data-stu-id="995fb-209">Build a random weather forecast</span></span>

<span data-ttu-id="995fb-210">Sonraki göreviniz, rastgele bir hava durumu tahminini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="995fb-210">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="995fb-211">Bir hava durumu tahminini istediğiniz değerleri içeren bir veri depolayıcı başlayalım:</span><span class="sxs-lookup"><span data-stu-id="995fb-211">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

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

<span data-ttu-id="995fb-212">Ardından, bu değerleri rastgele ayarlayan bir oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="995fb-212">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="995fb-213">Bu oluşturucu, enlem ve boylam çekirdek için değerleri kullanır. `Random` sayı üreteci.</span><span class="sxs-lookup"><span data-stu-id="995fb-213">This constructor uses the values for the latitude and longitude to seed the `Random` number generator.</span></span> <span data-ttu-id="995fb-214">Bu tahmin aynı konumu için aynı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="995fb-214">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="995fb-215">Enlem ve boylamını bağımsız değişkenleri değiştirirseniz (farklı bir çekirdek ile başlatma için) farklı bir tahmin alırsınız.</span><span class="sxs-lookup"><span data-stu-id="995fb-215">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed).</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="995fb-216">Bu gibi durumlarda, 5 günlük hava durumu tahminini artık yanıt yönteminizi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="995fb-216">You can now generate the 5-day forecast in your response method:</span></span>

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

### <a name="build-the-json-response"></a><span data-ttu-id="995fb-217">JSON yanıtı oluşturun</span><span class="sxs-lookup"><span data-stu-id="995fb-217">Build the JSON response</span></span>

<span data-ttu-id="995fb-218">Sunucuda son kod görev dönüştürülür `WeatherReport` listesine JSON belgesini ve istemciye gönderme.</span><span class="sxs-lookup"><span data-stu-id="995fb-218">The final code task on the server is to convert the `WeatherReport` list into JSON document, and send that back to the client.</span></span> <span data-ttu-id="995fb-219">JSON belgesini oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="995fb-219">Let's start by creating the JSON document.</span></span> <span data-ttu-id="995fb-220">Bağımlılıklar listesine Newtonsoft JSON serileştirici ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="995fb-220">You'll add the Newtonsoft JSON serializer to the list of dependencies.</span></span> <span data-ttu-id="995fb-221">Aşağıdakileri kullanarak bunu yapabilirsiniz `dotnet` komutu:</span><span class="sxs-lookup"><span data-stu-id="995fb-221">You can do that using the following `dotnet` command:</span></span>

```console
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="995fb-222">Daha sonra kullanabileceğiniz `JsonConvert` sınıfı nesne için bir dize yazmak için:</span><span class="sxs-lookup"><span data-stu-id="995fb-222">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="995fb-223">Yukarıdaki kod tahmin nesne dönüştürür (listesini `WeatherForecast` nesneleri) JSON belgesine.</span><span class="sxs-lookup"><span data-stu-id="995fb-223">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON document.</span></span> <span data-ttu-id="995fb-224">Yanıt belge oluşturduktan sonra içerik türü ayarlayın `application/json`ve dizeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="995fb-224">After you've constructed the response document, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="995fb-225">Uygulama artık çalışır ve rastgele tahminlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="995fb-225">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="995fb-226">Bir Docker görüntüsü oluşturun</span><span class="sxs-lookup"><span data-stu-id="995fb-226">Build a Docker image</span></span>

<span data-ttu-id="995fb-227">Bizim son Docker uygulamayı çalıştırmak için bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="995fb-227">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="995fb-228">Uygulamamızı temsil eden bir Docker görüntüsü çalıştıran bir Docker kapsayıcı oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="995fb-228">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="995fb-229">A ***Docker görüntüsü*** uygulamayı çalıştırmak için ortamı tanımlayan bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="995fb-229">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="995fb-230">A ***Docker kapsayıcısı*** bir Docker görüntüsü çalışan bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="995fb-230">A ***Docker Container*** represents a running instance of a Docker Image.</span></span>

<span data-ttu-id="995fb-231">Benzerleme tarafından kadar aklınıza gelebilecek *Docker görüntüsü* olarak bir *sınıfı*ve *Docker kapsayıcısı* bir nesne veya söz konusu sınıfın bir örneği.</span><span class="sxs-lookup"><span data-stu-id="995fb-231">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="995fb-232">Aşağıdaki Dockerfile, amaçlarımız doğrultusunda kullanılacak:</span><span class="sxs-lookup"><span data-stu-id="995fb-232">The following Dockerfile will serve for our purposes:</span></span>

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

<span data-ttu-id="995fb-233">Şimdi içeriğini geçelim.</span><span class="sxs-lookup"><span data-stu-id="995fb-233">Let's go over its contents.</span></span>

<span data-ttu-id="995fb-234">İlk satırı, uygulama oluşturmak için kullanılan kaynak görüntüyü belirtir:</span><span class="sxs-lookup"><span data-stu-id="995fb-234">The first line specifies the source image used for building the application:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
```

<span data-ttu-id="995fb-235">Docker, kaynak şablonu temel alan bir makine görüntüsü yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="995fb-235">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="995fb-236">Başlattığınızda, tüm makine parametreleri sağlamak zorunda olmadığınız anlamına yalnızca herhangi bir değişiklik sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="995fb-236">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="995fb-237">Uygulamamızı dahil etmek için değişiklikleri buraya olacaktır.</span><span class="sxs-lookup"><span data-stu-id="995fb-237">The changes here will be to include our application.</span></span>

<span data-ttu-id="995fb-238">Bu örnekte, kullanacağız `2.1-sdk` sürümünü `dotnet` görüntü.</span><span class="sxs-lookup"><span data-stu-id="995fb-238">In this sample, we'll use the `2.1-sdk` version of the `dotnet` image.</span></span> <span data-ttu-id="995fb-239">Bu, çalışan bir Docker ortamında oluşturmak için en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="995fb-239">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="995fb-240">Bu görüntü, .NET Core çalışma zamanı ve .NET Core SDK'sını içerir.</span><span class="sxs-lookup"><span data-stu-id="995fb-240">This image includes the .NET Core runtime, and the .NET Core SDK.</span></span>
<span data-ttu-id="995fb-241">Sayede başlamak ve derleme, ancak bu görüntü uygulama ve farklı bir görüntü oluşturmak için bunu kullanacağız için daha büyük bir görüntü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="995fb-241">That makes it easier to get started and build, but does create a larger image, so we'll use this image for building the application and a different image to run it.</span></span>

<span data-ttu-id="995fb-242">Sonraki satırı Kur ve uygulamanızı:</span><span class="sxs-lookup"><span data-stu-id="995fb-242">The next lines setup and build your application:</span></span>

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="995fb-243">Bu proje dosyası için Docker VM geçerli dizinden kopyalayın ve tüm paketleri geri yükle.</span><span class="sxs-lookup"><span data-stu-id="995fb-243">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="995fb-244">Dotnet CLI kullanılarak Docker görüntüsünü .NET Core SDK'sını içermelidir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="995fb-244">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="995fb-245">Bundan sonra uygulamanızın rest kopyalanır ve `dotnet
publish` komut oluşturur ve uygulama paketleri.</span><span class="sxs-lookup"><span data-stu-id="995fb-245">After that, the rest of your application gets copied, and the `dotnet
publish` command builds and packages your application.</span></span>

<span data-ttu-id="995fb-246">Son olarak, uygulamayı çalıştıran ikinci bir Docker görüntüsü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="995fb-246">Finally, we create a second Docker image that runs the application:</span></span>

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="995fb-247">Bu görüntüyü kullanan `2.1-aspnetcore-runtime` sürümünü `dotnet` ASP.NET Core uygulamaları çalıştırmak için gereken her şeyi içerir, ancak .NET Core SDK'sını içermeyen bir görüntü.</span><span class="sxs-lookup"><span data-stu-id="995fb-247">This image uses the `2.1-aspnetcore-runtime` version of the `dotnet` image, which contains everything necessary to run ASP.NET Core applications, but does not include the .NET Core SDK.</span></span> <span data-ttu-id="995fb-248">Başka bir deyişle, bu görüntü, .NET Core uygulamaları oluşturmak için kullanılamaz, ancak Ayrıca son görüntü daha küçük olur.</span><span class="sxs-lookup"><span data-stu-id="995fb-248">This means this image can't be used to build .NET Core applications, but it also makes the final image smaller.</span></span>

<span data-ttu-id="995fb-249">Bunun çalışmasını sağlamak için biz oluşturulan uygulamayı ilk görüntüden ikinci birine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="995fb-249">To make this work, we copy the built application from the first image to the second one.</span></span>

<span data-ttu-id="995fb-250">`ENTRYPOINT` Komut Docker hizmeti hangi komut başlatır bildirir.</span><span class="sxs-lookup"><span data-stu-id="995fb-250">The `ENTRYPOINT` command informs Docker what command starts the service.</span></span>

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="995fb-251">Oluşturma ve bir kapsayıcıda görüntünün çalıştırma</span><span class="sxs-lookup"><span data-stu-id="995fb-251">Building and running the image in a container</span></span>

<span data-ttu-id="995fb-252">Şimdi bir görüntü oluşturun ve bir Docker kapsayıcısı içinde hizmet.</span><span class="sxs-lookup"><span data-stu-id="995fb-252">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="995fb-253">Görüntüye kopyalanan yerel dizininizden tüm dosyaları istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="995fb-253">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="995fb-254">Bunun yerine, uygulama kapsayıcısında oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="995fb-254">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="995fb-255">Oluşturacağınız bir `.dockerignore` görüntüye kopyalanmaz dizinleri belirlemek için dosya.</span><span class="sxs-lookup"><span data-stu-id="995fb-255">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="995fb-256">Kopyalanan derleme varlıkları istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="995fb-256">You don't want any of the build assets copied.</span></span> <span data-ttu-id="995fb-257">Bir derleme belirleyin ve dizinlerde yayımlama `.dockerignore` dosyası:</span><span class="sxs-lookup"><span data-stu-id="995fb-257">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="995fb-258">Kullanarak yapı `docker build` komutu.</span><span class="sxs-lookup"><span data-stu-id="995fb-258">You build the image using the `docker build` command.</span></span> <span data-ttu-id="995fb-259">Kodunuzu içeren dizininden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="995fb-259">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="995fb-260">Bu komut Dockerfile içindeki tüm bilgileri temel alan bir kapsayıcı görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="995fb-260">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="995fb-261">`-t` Bağımsız değişkeni, bir etiket ya da bu kapsayıcı görüntüsü için bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="995fb-261">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="995fb-262">Yukarıdaki komut satırında Docker kapsayıcısı için kullanılan etikettir `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="995fb-262">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="995fb-263">Bu komut tamamlandığında, hizmetinizin yeni çalıştırmaya hazır bir kapsayıcı vardır.</span><span class="sxs-lookup"><span data-stu-id="995fb-263">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="995fb-264">Kapsayıcı başlatın ve hizmetinizi başlatmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="995fb-264">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

<span data-ttu-id="995fb-265">`-d` Geçerli terminalden ayrılmış kapsayıcıyı çalıştırmak seçenek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="995fb-265">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="995fb-266">Komut çıktısı terminalinizde görmezsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="995fb-266">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="995fb-267">`-p` Seçeneği, hizmet ile konak arasındaki bağlantı noktası eşlemesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="995fb-267">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="995fb-268">Burada 80 numaralı bağlantı noktasına gelen tüm istekler kapsayıcı üzerindeki 80 numaralı bağlantı noktasına iletilen olduğunu söylüyor.</span><span class="sxs-lookup"><span data-stu-id="995fb-268">Here it says that any incoming request on port 80 should be forwarded to port 80 on the container.</span></span> <span data-ttu-id="995fb-269">Eşleşen hizmetinizi dinlediği bağlantı üretim uygulamaları için varsayılan bağlantı noktası 80'i kullanarak.</span><span class="sxs-lookup"><span data-stu-id="995fb-269">Using 80 matches the port your service is listening on, which is the default port for production applications.</span></span> <span data-ttu-id="995fb-270">`--name` Çalışan kapsayıcınıza bağımsız değişken adları.</span><span class="sxs-lookup"><span data-stu-id="995fb-270">The `--name` argument names your running container.</span></span> <span data-ttu-id="995fb-271">Bu, bu kapsayıcı ile çalışmak için kullanabileceğiniz, kullanışlı bir addır.</span><span class="sxs-lookup"><span data-stu-id="995fb-271">It's a convenient name you can use to work with that container.</span></span>

<span data-ttu-id="995fb-272">Görüntü komutu denetleyerek çalışıp çalışmadığını görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="995fb-272">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="995fb-273">Kapsayıcınızı çalışıyorsa, bu çalışan işlemler listeleyen bir satır görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="995fb-273">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="995fb-274">(Yalnızca biri olabilir.)</span><span class="sxs-lookup"><span data-stu-id="995fb-274">(It may be the only one.)</span></span>

<span data-ttu-id="995fb-275">Bir tarayıcı açmak ve localhost için gezinme ve bir enlem ve boylamını belirten hizmetinizi test edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="995fb-275">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="995fb-276">Bir çalışan kapsayıcıya ekleme</span><span class="sxs-lookup"><span data-stu-id="995fb-276">Attaching to a running container</span></span>

<span data-ttu-id="995fb-277">Hizmetiniz bir komut penceresinde çalıştırdığınızda, her istek için yazdırılan tanı bilgilerini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="995fb-277">When you ran your service in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="995fb-278">Kapsayıcınızı ayrılmış modda çalışırken bu bilgileri görmüyorum.</span><span class="sxs-lookup"><span data-stu-id="995fb-278">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="995fb-279">Docker komut ekleme, günlük bilgilerini görebilmeniz için çalışan bir kapsayıcıya bağlayabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="995fb-279">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="995fb-280">Komut penceresinden şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="995fb-280">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="995fb-281">`--sig-proxy=false` Bağımsız değişken anlamına <kbd>Ctrl</kbd>+<kbd>C</kbd> komutları kapsayıcı işlemine gönderilen değil, ancak bunun yerine Durdur `docker attach` komutu.</span><span class="sxs-lookup"><span data-stu-id="995fb-281">The `--sig-proxy=false` argument means that <kbd>Ctrl</kbd>+<kbd>C</kbd> commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="995fb-282">Kapsayıcıda verilen ad son bağımsız değişken olan `docker run` komutu.</span><span class="sxs-lookup"><span data-stu-id="995fb-282">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="995fb-283">Docker kapsayıcı kimliği atanır, herhangi bir kapsayıcıya başvuran için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="995fb-283">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="995fb-284">Kapsayıcınızda için bir ad belirtirseniz yaramadı `docker run` kapsayıcı kimliği kullanmalıdır</span><span class="sxs-lookup"><span data-stu-id="995fb-284">If you didn't specify a name for your container in `docker run` you must use the container ID.</span></span>

<span data-ttu-id="995fb-285">Bir tarayıcı açın ve hizmetinize gidin.</span><span class="sxs-lookup"><span data-stu-id="995fb-285">Open a browser and navigate to your service.</span></span> <span data-ttu-id="995fb-286">Ekli çalışmakta olan kapsayıcıyı komutu windows tanılama iletisini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="995fb-286">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="995fb-287">Tuşuna <kbd>Ctrl</kbd>+<kbd>C</kbd> ekleme işlemi durdurulamadı.</span><span class="sxs-lookup"><span data-stu-id="995fb-287">Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the attach process.</span></span>

<span data-ttu-id="995fb-288">İşiniz bittiğinde kapsayıcı ile çalışma, durdurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="995fb-288">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="995fb-289">Kapsayıcı ve görüntü yeniden başlatmak için hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="995fb-289">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="995fb-290">Kapsayıcı makinenizden kaldırmak istiyorsanız, bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="995fb-290">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="995fb-291">Kullanılmayan görüntüleri makinenizden kaldırmak istiyorsanız, bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="995fb-291">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="995fb-292">Sonuç</span><span class="sxs-lookup"><span data-stu-id="995fb-292">Conclusion</span></span> 

<span data-ttu-id="995fb-293">Bu öğreticide bir ASP.NET Core mikro hizmet yerleşik ve birkaç basit özelliği eklendi.</span><span class="sxs-lookup"><span data-stu-id="995fb-293">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="995fb-294">Bir Docker kapsayıcı görüntüsü bu hizmet için oluşturulmuş ve bu kapsayıcı makinenizde çalıştı.</span><span class="sxs-lookup"><span data-stu-id="995fb-294">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="995fb-295">Bir terminal penceresi servise bağlı ve tanılama iletileri hizmetinizden gördünüz.</span><span class="sxs-lookup"><span data-stu-id="995fb-295">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="995fb-296">Süreç boyunca birkaç özelliklerinin gördüğünüz C# eylem dili.</span><span class="sxs-lookup"><span data-stu-id="995fb-296">Along the way, you saw several features of the C# language in action.</span></span>
