---
title: "Docker içinde - C# barındırılan mikro"
description: "ASP.NET Docker kapsayıcılarında çalıştırmak Çekirdek Hizmetleri oluşturmayı öğrenin"
keywords: .NET, .NET core, Docker, C#, ASP.NET, mikro hizmet
author: BillWagner
ms.author: wiwagn
ms.date: 02/03/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: csharp
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: d399cdce81350356b71e21d879a4f5b5079f98d8
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="30992-104">Docker içinde barındırılan mikro</span><span class="sxs-lookup"><span data-stu-id="30992-104">Microservices hosted in Docker</span></span>

<span data-ttu-id="30992-105">Bu öğretici oluşturmak ve ASP.NET Core mikro Docker kapsayıcısı içinde dağıtmak gerekli görevlerin ayrıntılarını verir.</span><span class="sxs-lookup"><span data-stu-id="30992-105">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="30992-106">Bu öğreticinin sürecinde şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="30992-106">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="30992-107">Yeoman kullanarak bir ASP.NET Core uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="30992-107">How to generate an ASP.NET Core application using Yeoman</span></span>
* <span data-ttu-id="30992-108">Bir geliştirme Docker ortamı oluşturma</span><span class="sxs-lookup"><span data-stu-id="30992-108">How to create a development Docker environment</span></span>
* <span data-ttu-id="30992-109">Varolan bir görüntüyü temel alarak bir Docker görüntü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="30992-109">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="30992-110">Nasıl bir Docker kapsayıcıya hizmetinizi dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="30992-110">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="30992-111">Yol boyunca bazı C# dil özellikleri görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="30992-111">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="30992-112">C# nesnelerini JSON yüklerini dönüştürmek nasıl.</span><span class="sxs-lookup"><span data-stu-id="30992-112">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="30992-113">Sabit veri aktarım nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="30992-113">How to build immutable Data Transfer Objects</span></span>
* <span data-ttu-id="30992-114">Gelen HTTP isteklerini işleyen ve HTTP yanıtı oluşturmak nasıl</span><span class="sxs-lookup"><span data-stu-id="30992-114">How to process incoming HTTP Requests and generate the HTTP Response</span></span>
* <span data-ttu-id="30992-115">Boş değer atanabilen değer türleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="30992-115">How to work with nullable value types</span></span>

<span data-ttu-id="30992-116">Yapabilecekleriniz [görüntüleyebilir veya örnek uygulama indirebilirsiniz](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) Bu konu için.</span><span class="sxs-lookup"><span data-stu-id="30992-116">You can [view or download the sample app](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="30992-117">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="30992-117">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="why-docker"></a><span data-ttu-id="30992-118">Neden Docker?</span><span class="sxs-lookup"><span data-stu-id="30992-118">Why Docker?</span></span>

<span data-ttu-id="30992-119">Docker hizmetlerinizi bir veri merkezinde barındırılacağını standart makine görüntülerini oluşturmak kolaylaştırır veya genel bulut.</span><span class="sxs-lookup"><span data-stu-id="30992-119">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="30992-120">Docker yapılandırma resmi ve yükleme, uygulamanızın ölçeklendirmek için gerektiği şekilde çoğaltmak etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="30992-120">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="30992-121">Bu öğreticideki tüm kod tüm .NET Core ortamlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="30992-121">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="30992-122">Docker yükleme için ek görevler için bir ASP.NET Core uygulama çalışır.</span><span class="sxs-lookup"><span data-stu-id="30992-122">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="30992-123">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="30992-123">Prerequisites</span></span>
<span data-ttu-id="30992-124">.NET core çalışmasına, makine Kurulum gerekir.</span><span class="sxs-lookup"><span data-stu-id="30992-124">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="30992-125">Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="30992-125">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="30992-126">Bu uygulama, Windows, Ubuntu Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30992-126">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="30992-127">Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="30992-127">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="30992-128">Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/) platform Düzenleyicisi arası bir açık kaynak olduğu.</span><span class="sxs-lookup"><span data-stu-id="30992-128">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="30992-129">Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30992-129">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="30992-130">Docker altyapısına yüklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="30992-130">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="30992-131">Bkz: [Docker yükleme sayfası](http://www.docker.com/products/docker) platformunuza ilişkin yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="30992-131">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="30992-132">Docker, birçok Linux dağıtımları, macOS veya Windows yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="30992-132">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="30992-133">Yukarıda başvurulan sayfa her bir kullanılabilir yüklemeler bölümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-133">The page referenced above contains sections to each of the available installations.</span></span>

<span data-ttu-id="30992-134">Çoğu bileşenin yüklü olmasını bir paket yöneticisi tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="30992-134">Most components to be installed are done by a package manager.</span></span> <span data-ttu-id="30992-135">Node.js'ın Paket Yöneticisi varsa `npm` yüklü bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30992-135">If you have node.js's package manager `npm` installed you can skip this step.</span></span> <span data-ttu-id="30992-136">Aksi takdirde son NodeJs gelen yükleyin [nodejs.org](https://nodejs.org) npm Paket Yöneticisi'ni yükler.</span><span class="sxs-lookup"><span data-stu-id="30992-136">Otherwise install the latest NodeJs from [nodejs.org](https://nodejs.org) which will install the npm package manager.</span></span> 

<span data-ttu-id="30992-137">Bu noktada bir dizi ASP.NET core geliştirme desteği komut satırı araçları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="30992-137">At this point you will need to install a number of command line tools that support ASP.NET core development.</span></span> <span data-ttu-id="30992-138">Komut satırı şablonlarını Yeoman, Bower, Grunt ve Gulp kullanın.</span><span class="sxs-lookup"><span data-stu-id="30992-138">The command line templates use Yeoman, Bower, Grunt, and Gulp.</span></span> <span data-ttu-id="30992-139">Aksi takdirde bunları yüklü iyi olan varsa, sık kullanılan kabuğundan aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="30992-139">If you have them installed that is good, otherwise type the following into your favorite shell:</span></span>

`npm install -g yo bower grunt-cli gulp`

<span data-ttu-id="30992-140">`-g` Seçeneği gösteren bir genel yükleme olduğunu ve bu araçlar kullanılabilir sistem genelinde.</span><span class="sxs-lookup"><span data-stu-id="30992-140">The `-g` option indicates that it is a global install, and those tools are available system wide.</span></span> <span data-ttu-id="30992-141">(Yerel bir yükleme paketi tek bir proje kapsamları).</span><span class="sxs-lookup"><span data-stu-id="30992-141">(A local install scopes the package to a single project).</span></span> <span data-ttu-id="30992-142">Bu çekirdek araçları yükledikten sonra yeoman ASP.NET şablon oluşturucuları yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="30992-142">Once you've installed those core tools, you need to install the yeoman ASP.NET template generators:</span></span>

`npm install -g generator-aspnet`

## <a name="create-the-application"></a><span data-ttu-id="30992-143">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="30992-143">Create the Application</span></span>

<span data-ttu-id="30992-144">Tüm Araçlar yüklediniz, yeni bir ASP.NET Core uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="30992-144">Now that you've installed all the tools, create a new ASP.NET Core application.</span></span> <span data-ttu-id="30992-145">Komut satırı Oluşturucu kullanmak için sık kullanılan Kabuğu'nda aşağıdaki yeoman komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="30992-145">To use the command line generator, execute the following yeoman command in your favorite shell:</span></span>

`yo aspnet`

<span data-ttu-id="30992-146">Bu komutun ne tür bir uygulama oluşturmak istediğiniz seçmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="30992-146">This command prompts you to select what Type of application you want to create.</span></span> <span data-ttu-id="30992-147">Bu mikro hizmet için basit ve en basit bir web uygulaması olası istediğiniz, bu nedenle 'Boş Web uygulaması' seçin.</span><span class="sxs-lookup"><span data-stu-id="30992-147">For this microservice, you want the simplest, most lightweight web application possible, so select 'Empty Web Application'.</span></span> <span data-ttu-id="30992-148">Şablon için bir ad ister.</span><span class="sxs-lookup"><span data-stu-id="30992-148">The template will prompt you for a name.</span></span> <span data-ttu-id="30992-149">'WeatherMicroservice' seçin.</span><span class="sxs-lookup"><span data-stu-id="30992-149">Select 'WeatherMicroservice'.</span></span> 

<span data-ttu-id="30992-150">Şablon sekiz dosyaları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="30992-150">The template creates eight files for you:</span></span>

* <span data-ttu-id="30992-151">ASP.NET Core uygulamaları için özelleştirilmiş bir .gitignore.</span><span class="sxs-lookup"><span data-stu-id="30992-151">A .gitignore, customized for ASP.NET Core applications.</span></span>
* <span data-ttu-id="30992-152">Haline dosya.</span><span class="sxs-lookup"><span data-stu-id="30992-152">A Startup.cs file.</span></span> <span data-ttu-id="30992-153">Bu uygulamanın temel içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-153">This contains the basis of the application.</span></span>
* <span data-ttu-id="30992-154">Program.cs dosyasının.</span><span class="sxs-lookup"><span data-stu-id="30992-154">A Program.cs file.</span></span> <span data-ttu-id="30992-155">Bu uygulama giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-155">This contains the entry point of the application.</span></span>
* <span data-ttu-id="30992-156">Bir WeatherMicroservice.csproj dosyası.</span><span class="sxs-lookup"><span data-stu-id="30992-156">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="30992-157">Bu uygulama için yapı dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="30992-157">This is the build file for the application.</span></span>
* <span data-ttu-id="30992-158">Bir Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="30992-158">A Dockerfile.</span></span> <span data-ttu-id="30992-159">Bu komut, uygulama için bir Docker görüntü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30992-159">This script creates a Docker image for the application.</span></span>
* <span data-ttu-id="30992-160">Bir README.md.</span><span class="sxs-lookup"><span data-stu-id="30992-160">A README.md.</span></span> <span data-ttu-id="30992-161">Bu, diğer ASP.NET Core kaynaklarına bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-161">This contains links to other ASP.NET Core resources.</span></span>
* <span data-ttu-id="30992-162">Bir web.config dosyası.</span><span class="sxs-lookup"><span data-stu-id="30992-162">A web.config file.</span></span> <span data-ttu-id="30992-163">Bu, temel yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-163">This contains basic configuration information.</span></span>
* <span data-ttu-id="30992-164">Bir runtimeconfig.template.json dosyası.</span><span class="sxs-lookup"><span data-stu-id="30992-164">A runtimeconfig.template.json file.</span></span> <span data-ttu-id="30992-165">IDE tarafından kullanılan hata ayıklama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-165">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="30992-166">Şimdi oluşturulan şablon uygulamayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30992-166">Now you can run the template generated application.</span></span> <span data-ttu-id="30992-167">Bir dizi komut satırından araçları kullanarak yapmıştır.</span><span class="sxs-lookup"><span data-stu-id="30992-167">That's done using a series of tools from the command line.</span></span> <span data-ttu-id="30992-168">`dotnet` Komutu .NET geliştirme için gerekli araçları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="30992-168">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="30992-169">Farklı bir komut her fiil çalıştırır</span><span class="sxs-lookup"><span data-stu-id="30992-169">Each verb executes a different command</span></span>

<span data-ttu-id="30992-170">Tüm bağımlılıkları geri yüklemek için ilk adımdır bakın:</span><span class="sxs-lookup"><span data-stu-id="30992-170">The first step is to restore all the dependencies:</span></span>

```console
dotnet restore
```

<span data-ttu-id="30992-171">DotNet geri yükleme NuGet Paket Yöneticisi uygulama dizine tüm gerekli paketleri yüklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="30992-171">Dotnet restore uses the NuGet package manager to install all the necessary packages into the application directory.</span></span> <span data-ttu-id="30992-172">Ayrıca, bir project.json.lock dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30992-172">It also generates a project.json.lock file.</span></span> <span data-ttu-id="30992-173">Bu dosya, başvurulan her paketi hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-173">This file contains information about each package that is referenced.</span></span> <span data-ttu-id="30992-174">Tüm bağımlılıkları geri yüklendikten sonra uygulamayı derlediğinizde:</span><span class="sxs-lookup"><span data-stu-id="30992-174">After restoring all the dependencies, you build the application:</span></span>

```console
dotnet build
```
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="30992-175">Ve uygulama yapı sonra komut satırından çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="30992-175">And once you build the application, you run it from the command line:</span></span>

```console
dotnet run
```

<span data-ttu-id="30992-176">Varsayılan yapılandırma http://localhost: 5000 için dinler.</span><span class="sxs-lookup"><span data-stu-id="30992-176">The default configuration listens to http://localhost:5000.</span></span> <span data-ttu-id="30992-177">Bir tarayıcıda açabilir ve bu sayfaya gidin ve bir "Hello World!" konusuna bakın</span><span class="sxs-lookup"><span data-stu-id="30992-177">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="30992-178">İleti.</span><span class="sxs-lookup"><span data-stu-id="30992-178">message.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="30992-179">Bir ASP.NET Core uygulama anatomisi</span><span class="sxs-lookup"><span data-stu-id="30992-179">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="30992-180">Uygulama oluşturduğunuza göre bu işlev nasıl uygulandığı konumundaki bakalım.</span><span class="sxs-lookup"><span data-stu-id="30992-180">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="30992-181">Bu noktada özellikle ilginç oluşturulan dosyalar iki vardır: project.json ve haline.</span><span class="sxs-lookup"><span data-stu-id="30992-181">There are two of the generated files that are particularly interesting at this point: project.json and Startup.cs.</span></span> 

<span data-ttu-id="30992-182">Project.JSON, proje hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-182">Project.json contains information about the project.</span></span> <span data-ttu-id="30992-183">Genellikle ile karşılaşmayacağınızı iki düğüm 'bağımlılıkları' ve 'çerçeveleri' dir.</span><span class="sxs-lookup"><span data-stu-id="30992-183">The two nodes you'll often work with are 'dependencies' and 'frameworks'.</span></span> <span data-ttu-id="30992-184">Bağımlılıklar düğümü bu uygulama için gerekli olan tüm paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="30992-184">The dependencies node lists all the packages that are needed for this application.</span></span>
<span data-ttu-id="30992-185">Şu anda bu web sunucusu çalıştıran paketleri ihtiyaç duyan, küçük bir düğümü olduğu.</span><span class="sxs-lookup"><span data-stu-id="30992-185">At the moment, this is a small node, needing only the packages that run the web server.</span></span>

<span data-ttu-id="30992-186">'Çerçeveler' düğümü sürümleri ve bu, uygulamanın çalıştırılacağı .NET framework'ün yapılandırmaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="30992-186">The 'frameworks' node specifies the versions and configurations of the .NET framework that will run this application.</span></span>

<span data-ttu-id="30992-187">Uygulama haline içinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="30992-187">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="30992-188">Bu dosya başlangıç sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-188">This file contains the startup class.</span></span>

<span data-ttu-id="30992-189">İki yöntem yapılandırmak ve uygulamayı çalıştırmak için ASP.NET Core altyapısı tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="30992-189">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="30992-190">`ConfigureServices` Yöntemi bu uygulama için gerekli hizmetleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="30992-190">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="30992-191">Bağımlılıkları yapılandırmak gerekli olmayan şekilde yalın mikro hizmet oluşturmakta olduğunuz.</span><span class="sxs-lookup"><span data-stu-id="30992-191">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="30992-192">`Configure` Yöntemi işleyiciler gelen HTTP isteklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="30992-192">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="30992-193">Şablon 'Hello World!' metinle herhangi bir istek için yanıt veren basit bir işleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30992-193">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="30992-194">Bir mikro hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="30992-194">Build a microservice</span></span>

<span data-ttu-id="30992-195">Giderek oluşturmak için hizmet hava raporları yerden teslim eder dünya.</span><span class="sxs-lookup"><span data-stu-id="30992-195">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="30992-196">Bir üretim uygulamasında hava durumu verilerini almak için bazı hizmet çağırırdı.</span><span class="sxs-lookup"><span data-stu-id="30992-196">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="30992-197">Bizim örnek için size rastgele hava tahmini oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="30992-197">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="30992-198">Rastgele hava durumu hizmetimizi uygulamak üzere gerçekleştirmeniz gereken görevler vardır:</span><span class="sxs-lookup"><span data-stu-id="30992-198">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="30992-199">Enlem ve boylam okumak için gelen istek ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="30992-199">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="30992-200">Bazı rastgele tahmin verilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30992-200">Generate some random forecast data.</span></span>
* <span data-ttu-id="30992-201">Bu rastgele tahmin verilerini C# nesnelerden JSON paketlere dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="30992-201">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="30992-202">Hizmet gönderir JSON geri belirtmek için yanıt üstbilgisi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="30992-202">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="30992-203">Yanıt yazma.</span><span class="sxs-lookup"><span data-stu-id="30992-203">Write the response.</span></span>

<span data-ttu-id="30992-204">Sonraki bölümlerde, bu adımların her biri yol.</span><span class="sxs-lookup"><span data-stu-id="30992-204">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="30992-205">Sorgu dizesini ayrıştırma.</span><span class="sxs-lookup"><span data-stu-id="30992-205">Parsing the Query String.</span></span>

<span data-ttu-id="30992-206">Sorgu dizesini ayrıştırarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="30992-206">You'll begin by parsing the query string.</span></span> <span data-ttu-id="30992-207">Hizmeti, 'lat' ve 'uzun' bağımsız değişkeni bu formda sorgu dizesini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="30992-207">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

`http://localhost:5000/?lat=-35.55&long=-12.35`  

<span data-ttu-id="30992-208">Bağımsız değişken olarak tanımlanan lambda ifadesi almanız gereken tüm değişiklikleri bulunan `app.Run` başlangıç sınıfınızda.</span><span class="sxs-lookup"><span data-stu-id="30992-208">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="30992-209">Lambda ifadesi bağımsız değişkeni `HttpContext` istek için.</span><span class="sxs-lookup"><span data-stu-id="30992-209">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="30992-210">Özelliklerinden biri olan `Request` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="30992-210">One of its properties is the `Request` object.</span></span> <span data-ttu-id="30992-211">`Request` Nesnesi bir `Query` istek için sorgu dizesinde tüm değerlerin sözlüğü içeren özelliği.</span><span class="sxs-lookup"><span data-stu-id="30992-211">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="30992-212">Enlem ve boylam değerlerini bulmak için ilk ektir bakın:</span><span class="sxs-lookup"><span data-stu-id="30992-212">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="30992-213">Sorgu sözlük değerler `StringValue` türü.</span><span class="sxs-lookup"><span data-stu-id="30992-213">The Query dictionary values are `StringValue` type.</span></span> <span data-ttu-id="30992-214">Bu tür dizeleri koleksiyonu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="30992-214">That type can contain a collection of strings.</span></span> <span data-ttu-id="30992-215">Hava durumu hizmetiniz için her bir değer tek bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="30992-215">For your weather service, each value is a single string.</span></span> <span data-ttu-id="30992-216">İşte çağrısı yok `FirstOrDefault()` Yukarıdaki kod.</span><span class="sxs-lookup"><span data-stu-id="30992-216">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="30992-217">Ardından, çiftleri için dizeleri dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="30992-217">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="30992-218">Dize için bir çift dönüştürmek için kullanılan yöntemi `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="30992-218">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="30992-219">Bu yöntem C# out Parametreleri giriş dizesi bir double dönüştürülüp dönüştürülemeyeceğini belirtmek için yararlanır.</span><span class="sxs-lookup"><span data-stu-id="30992-219">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="30992-220">Dize çift türü için geçerli bir temsili temsil ediyorsa, yöntem true döndürür ve `result` bağımsız değişken değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="30992-220">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="30992-221">Dize geçerli bir çift göstermiyor varsa yöntemi false değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="30992-221">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="30992-222">Bu API kullanarak uyarlayabilirsiniz bir *genişletme yöntemi* döndüren bir *boş değer atanabilir çift*.</span><span class="sxs-lookup"><span data-stu-id="30992-222">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="30992-223">A *boş değer atanabilir değer türü* bazı değer türü temsil eden bir tür olduğundan ve ayrıca eksik tutun veya null değer.</span><span class="sxs-lookup"><span data-stu-id="30992-223">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="30992-224">Boş değer atanabilir bir tür ekleyerek temsil edilen `?` türü bildirimi karakter.</span><span class="sxs-lookup"><span data-stu-id="30992-224">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="30992-225">Genişletme yöntemleri statik yöntemler, ancak ekleyerek tanımlanan yöntemlerdir `this` o sınıfın üyeleri olsa gibi ilk parametre değiştirici çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="30992-225">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="30992-226">Genişletme yöntemleri yalnızca statik sınıflarda tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="30992-226">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="30992-227">Ayrıştırma için genişletme yöntemi içeren sınıf tanımını şöyledir:</span><span class="sxs-lookup"><span data-stu-id="30992-227">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="30992-228">`default(double?)` İfade için varsayılan değeri döndürür `double?` türü.</span><span class="sxs-lookup"><span data-stu-id="30992-228">The `default(double?)` expression returns the default value for the `double?` type.</span></span> <span data-ttu-id="30992-229">Değeri null (ya da eksik) bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="30992-229">That default value is the null (or missing) value.</span></span>

<span data-ttu-id="30992-230">Sorgu dizesi bağımsız değişkenleri çift türüne dönüştürmek için bu genişletme yöntemi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30992-230">You can use this extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="30992-231">Kolayca ayrıştırma kodu test etmek için bağımsız değişkenlerin değerlerini dahil etmek için yanıt güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="30992-231">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="30992-232">Bu noktada, web uygulamasını çalıştırın ve ayrıştırma kodunuzu çalışıp çalışmadığını.</span><span class="sxs-lookup"><span data-stu-id="30992-232">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="30992-233">Bir tarayıcıda web isteğine değerlerini ekleyin ve güncelleştirilmiş sonuçları görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="30992-233">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="30992-234">Rastgele bir hava durumu tahmini derleme</span><span class="sxs-lookup"><span data-stu-id="30992-234">Build a random weather forecast</span></span>

<span data-ttu-id="30992-235">Sonraki göreviniz rastgele hava tahmini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="30992-235">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="30992-236">Hava tahmini için istediğiniz değerleri içeren bir veri kapsayıcısı ile başlayalım tıklatın:</span><span class="sxs-lookup"><span data-stu-id="30992-236">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

<span data-ttu-id="30992-237">Ardından, bu değerleri rastgele ayarlar bir oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="30992-237">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="30992-238">Bu oluşturucu, rastgele sayı üreticisinin oluşturmak için enlem ve boylam değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="30992-238">This constructor uses the values for the latitude and longitude to seed the Random number generator.</span></span> <span data-ttu-id="30992-239">Aynı konuma tahmin aynı olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="30992-239">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="30992-240">Enlem ve boylam bağımsız değişkenleri değiştirirseniz, (farklı çekirdek ile başlatmak için.), farklı bir tahmin elde edersiniz</span><span class="sxs-lookup"><span data-stu-id="30992-240">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed.)</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="30992-241">Bu gibi durumlarda, 5 gün tahmin şimdi yanıt yönteminizi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30992-241">You can now generate the 5-day forecast in your response method:</span></span>

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]

### <a name="build-the-json-response"></a><span data-ttu-id="30992-242">JSON yanıt oluşturun.</span><span class="sxs-lookup"><span data-stu-id="30992-242">Build the JSON response.</span></span>

<span data-ttu-id="30992-243">Son kodu sunucuda WeatherReport dizi JSON pakete dönüştürmek ve bu istemciye göndermek için bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="30992-243">The final code task on the server is to convert the WeatherReport array into a JSON packet, and send that back to the client.</span></span> <span data-ttu-id="30992-244">JSON paket oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="30992-244">Let's start by creating the JSON packet.</span></span> <span data-ttu-id="30992-245">Bağımlılıklar listesine NewtonSoft JSON seri hale getirici ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="30992-245">You'll add the NewtonSoft JSON Serializer to the list of dependencies.</span></span> <span data-ttu-id="30992-246">Bu kullanarak yapabilirsiniz `dotnet` CLI:</span><span class="sxs-lookup"><span data-stu-id="30992-246">You can do that using the `dotnet` CLI:</span></span>

```
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="30992-247">Ardından, kullanabileceğiniz `JsonConvert` dizeye nesne yazmak için sınıf:</span><span class="sxs-lookup"><span data-stu-id="30992-247">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="30992-248">Yukarıdaki kod tahmin nesne dönüştürür (listesini `WeatherForecast` nesneler) JSON paket.</span><span class="sxs-lookup"><span data-stu-id="30992-248">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON packet.</span></span> <span data-ttu-id="30992-249">Yanıt paketi oluşturduktan sonra içerik türü ayarlayın `application/json`ve dize yazma.</span><span class="sxs-lookup"><span data-stu-id="30992-249">After you've constructed the response packet, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="30992-250">Uygulamayı şimdi çalıştırır ve rastgele tahminlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="30992-250">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="30992-251">Docker yansıması oluştur</span><span class="sxs-lookup"><span data-stu-id="30992-251">Build a Docker image</span></span>

<span data-ttu-id="30992-252">Bizim son Docker içinde uygulamayı çalıştırmak için bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="30992-252">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="30992-253">Uygulamamız temsil eden bir Docker görüntü çalışan bir Docker kapsayıcısı oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="30992-253">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="30992-254">A ***Docker görüntü*** uygulamayı çalıştırmak için ortam tanımlayan bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="30992-254">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="30992-255">A ***Docker kapsayıcısı*** Docker görüntü çalışan bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30992-255">A ***Docker Container*** represents a running instance of a Docker image.</span></span>

<span data-ttu-id="30992-256">Benzerleme tarafından düşünebilirsiniz *Docker görüntü* olarak bir *sınıfı*ve *Docker kapsayıcısı* bir nesne ya da bu sınıfının bir örneği olarak.</span><span class="sxs-lookup"><span data-stu-id="30992-256">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="30992-257">ASP.NET şablonu tarafından oluşturulan Dockerfile bizim amacıyla hizmet verecektir.</span><span class="sxs-lookup"><span data-stu-id="30992-257">The Dockerfile created by the ASP.NET template will serve for our purposes.</span></span> <span data-ttu-id="30992-258">Şimdi içeriğinin gidin.</span><span class="sxs-lookup"><span data-stu-id="30992-258">Let's go over its contents.</span></span>

<span data-ttu-id="30992-259">İlk satırı kaynak görüntü belirtir:</span><span class="sxs-lookup"><span data-stu-id="30992-259">The first line specifies the source image:</span></span>

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

<span data-ttu-id="30992-260">Docker kaynak şablonunu temel alan bir makine görüntüsünün yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="30992-260">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="30992-261">Başlattığınızda tüm makine parametreler sağlamanız gerekmez anlamına yalnızca herhangi bir değişiklik sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="30992-261">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="30992-262">Değişiklikler burada uygulamamız eklenecek.</span><span class="sxs-lookup"><span data-stu-id="30992-262">The changes here will be to include our application.</span></span>

<span data-ttu-id="30992-263">Bu ilk örnekte kullanacağız `1.1-sdk-msbuild` dotnet görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="30992-263">In this first sample, we'll use the `1.1-sdk-msbuild` version of the dotnet image.</span></span> <span data-ttu-id="30992-264">Bu, çalışan bir Docker ortamı oluşturmak için en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="30992-264">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="30992-265">Bu görüntü dotnet çekirdeği çalışma zamanı ve SDK dotnet kapsar.</span><span class="sxs-lookup"><span data-stu-id="30992-265">This image include the dotnet core runtime, and the dotnet SDK.</span></span> <span data-ttu-id="30992-266">Kolaylaştırır başlamak ve yapı, ancak daha büyük bir görüntü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="30992-266">That makes it easier to get started and build, but does create a larger image.</span></span>

<span data-ttu-id="30992-267">Sonraki beş satır Kurulum ve uygulamanızı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="30992-267">The next five lines setup and build your application:</span></span>

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore 

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="30992-268">Bu proje dosyası Docker VM geçerli dizinden kopyalayın ve tüm paketler geri yükleme.</span><span class="sxs-lookup"><span data-stu-id="30992-268">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="30992-269">Dotnet CLI kullanarak Docker görüntünün .NET Core SDK içermelidir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="30992-269">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="30992-270">Bundan sonra uygulamanızın rest kopyalanan ve dotnet komutu yapılar ve paketleri uygulamanızı yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="30992-270">After that, the rest of your application gets copied, and the dotnet publish command builds and packages your application.</span></span>

<span data-ttu-id="30992-271">Dosyanın son satırının uygulama çalışır:</span><span class="sxs-lookup"><span data-stu-id="30992-271">The final line of the file runs the application:</span></span>

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

<span data-ttu-id="30992-272">Bu yapılandırılan bağlantı noktası başvuru `--server.urls` bağımsız değişkeni `dotnet` Dockerfile son satırında.</span><span class="sxs-lookup"><span data-stu-id="30992-272">This configured port is referenced in the `--server.urls` argument to `dotnet` on the last  line of the Dockerfile.</span></span> <span data-ttu-id="30992-273">`ENTRYPOINT` Komut hangi komut ve komut satırı seçenekleri hizmeti başlatmak Docker bildirir.</span><span class="sxs-lookup"><span data-stu-id="30992-273">The `ENTRYPOINT` command informs Docker what command and command-line options start the service.</span></span> 

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="30992-274">Oluşturma ve görüntüyü bir kapsayıcıda çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="30992-274">Building and running the image in a container.</span></span>

<span data-ttu-id="30992-275">Şimdi bir görüntü oluşturun ve Docker kapsayıcısı içinde hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="30992-275">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="30992-276">Yerel dizininizdeki görüntüsüne kopyalanan tüm dosyaları istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="30992-276">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="30992-277">Bunun yerine, kapsayıcı uygulamada yapı.</span><span class="sxs-lookup"><span data-stu-id="30992-277">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="30992-278">Oluşturacağınız bir `.dockerignore` dosya görüntüsüne kopyalanmaz dizinleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="30992-278">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="30992-279">Kopyalanan yapı varlıklar istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="30992-279">You don't want any of the build assets copied.</span></span> <span data-ttu-id="30992-280">Yapı belirtin ve dizinlerde yayımlayın `.dockerignore` dosyası:</span><span class="sxs-lookup"><span data-stu-id="30992-280">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="30992-281">Görüntü kullanarak yapı `docker build` komutu.</span><span class="sxs-lookup"><span data-stu-id="30992-281">You build the image using the `docker build` command.</span></span> <span data-ttu-id="30992-282">Kodunuzu içeren dizininden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="30992-282">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="30992-283">Bu komut, Dockerfile içindeki tüm bilgileri temel kapsayıcı görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30992-283">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="30992-284">`-t` Bağımsız değişkeni bir etiket veya bu kapsayıcı görüntü adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="30992-284">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="30992-285">Yukarıdaki komut satırında, Docker kapsayıcısı için kullanılan etiketi olan `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="30992-285">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="30992-286">Bu komut tamamlandığında, yeni hizmetinizi çalıştırılmaya hazır bir kapsayıcıya sahip.</span><span class="sxs-lookup"><span data-stu-id="30992-286">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="30992-287">Kapsayıcı başlatmak ve hizmetinizi başlatmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="30992-287">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

<span data-ttu-id="30992-288">`-d` Geçerli terminal durumundan ayrılmış kapsayıcı çalıştırmak seçenek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="30992-288">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="30992-289">Terminalinizde komut çıktısı görmezsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="30992-289">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="30992-290">`-p` Seçeneği, hizmet ve ana bilgisayar arasında bağlantı noktası eşleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="30992-290">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="30992-291">Burada herhangi bir gelen istek bağlantı noktası 80 üzerinde bağlantı noktası 5000 kapsayıcısı üzerinde iletilmesi gereken yazacaktır.</span><span class="sxs-lookup"><span data-stu-id="30992-291">Here it says that any incoming request on port 80 should be forwarded to port 5000 on the container.</span></span> <span data-ttu-id="30992-292">5000 kullanarak yukarıdaki Dockerfile belirtilen komut satırı bağımsız değişkenleri gelen üzerinde hizmetinizi dinleme bağlantı noktası ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="30992-292">Using 5000 matches the port your service is listening on from the command line arguments specified in the Dockerfile above.</span></span> <span data-ttu-id="30992-293">`--name` Bağımsız değişken adları, çalışan kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="30992-293">The `--name` argument names your running container.</span></span> <span data-ttu-id="30992-294">Bu kapsayıcı ile çalışmak için kullanabileceğiniz bir kolay adıdır.</span><span class="sxs-lookup"><span data-stu-id="30992-294">It's a convenient name you can use to work with that container.</span></span> 

<span data-ttu-id="30992-295">Görüntü komutu denetleyerek çalışıp çalışmadığını görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30992-295">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="30992-296">Kapsayıcı çalışıyorsa, çalışan işlemler listeleyen bir satırı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="30992-296">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="30992-297">(Yalnızca biri olabilir).</span><span class="sxs-lookup"><span data-stu-id="30992-297">(It may be the only one).</span></span>

<span data-ttu-id="30992-298">Bir tarayıcıda açmak ve localhost için gezinme ve enlem ve boylam belirterek hizmetinizi test edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30992-298">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="30992-299">Çalışan bir kapsayıcı ekleme</span><span class="sxs-lookup"><span data-stu-id="30992-299">Attaching to a running container</span></span>

<span data-ttu-id="30992-300">Bir komut penceresinde, hizmeti çalıştırdığınızda, her istek için yazdırılan tanılama bilgileri görebilir.</span><span class="sxs-lookup"><span data-stu-id="30992-300">When you ran your sevice in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="30992-301">Kapsayıcı ayrılmış modda çalışırken bu bilgileri görmüyorum.</span><span class="sxs-lookup"><span data-stu-id="30992-301">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="30992-302">Docker komut ekleme, günlük bilgilerini görebilmeniz için çalışan bir kapsayıcıya eklenecek sağlar.</span><span class="sxs-lookup"><span data-stu-id="30992-302">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="30992-303">Bir komut penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="30992-303">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="30992-304">`--sig-proxy=false` Bağımsız değişkeni anlamına `Ctrl-C` komutları kapsayıcı işleme gönderilen değil, ancak yerine Durdur `docker attach` komutu.</span><span class="sxs-lookup"><span data-stu-id="30992-304">The `--sig-proxy=false` argument means that `Ctrl-C` commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="30992-305">Son bağımsız değişkeni kapsayıcısında verilen addır `docker run` komutu.</span><span class="sxs-lookup"><span data-stu-id="30992-305">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="30992-306">Kapsayıcı kimliği atanan Docker, herhangi bir kapsayıcıya başvurmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30992-306">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="30992-307">Kapsayıcı için bir ad belirtirseniz kaydetmedi `docker run` kapsayıcı kimliği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="30992-307">If you didn't specify a name for your container in `docker run` you must use the container id.</span></span>

<span data-ttu-id="30992-308">Bir tarayıcı açın ve hizmetinize gidin.</span><span class="sxs-lookup"><span data-stu-id="30992-308">Open a browser and navigate to your service.</span></span> <span data-ttu-id="30992-309">Tanılama iletileri ekli çalışan kapsayıcısından komutu Windows görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="30992-309">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="30992-310">Tuşuna `Ctrl-C` ekleme işlemi durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="30992-310">Press `Ctrl-C` to stop the attach process.</span></span>

<span data-ttu-id="30992-311">İşiniz bittiğinde, kapsayıcı ile çalışma, durdurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30992-311">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="30992-312">Kapsayıcı ve görüntü yeniden başlatmak için hala mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="30992-312">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="30992-313">Kapsayıcı makinenizden kaldırmak istiyorsanız, bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="30992-313">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="30992-314">Kullanılmayan görüntüleri makinenizden kaldırmak istiyorsanız, bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="30992-314">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="30992-315">Sonuç</span><span class="sxs-lookup"><span data-stu-id="30992-315">Conclusion</span></span> 

<span data-ttu-id="30992-316">Bu öğreticide ASP.NET Core mikro hizmet yerleşik ve birkaç basit özellikler eklenir.</span><span class="sxs-lookup"><span data-stu-id="30992-316">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="30992-317">Bir Docker kapsayıcısı görüntü hizmetin yerleşik ve bu kapsayıcı, makinenizde çalıştı.</span><span class="sxs-lookup"><span data-stu-id="30992-317">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="30992-318">Bir terminal penceresi hizmete bağlı ve tanılama iletileri hizmetinizden gördünüz.</span><span class="sxs-lookup"><span data-stu-id="30992-318">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="30992-319">Yol boyunca eylem C# dilinin çeşitli özellikler gördünüz.</span><span class="sxs-lookup"><span data-stu-id="30992-319">Along the way, you saw several features of the C# language in action.</span></span>
