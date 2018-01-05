---
title: ".NET Core ile Docker temellerini öğrenin"
description: "Docker ve .NET Core temel Öğreticisi"
keywords: ".NET, .NET core, Docker, öğretici"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.workload: dotnetcore
ms.openlocfilehash: 79ded2ce5de5100c18301127a2654f8791b8ed76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="67265-104">.NET Core ile Docker temellerini öğrenin</span><span class="sxs-lookup"><span data-stu-id="67265-104">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="67265-105">Bu öğretici, Docker kapsayıcısı derleme ve görevler için bir .NET Core uygulaması dağıtma öğretir.</span><span class="sxs-lookup"><span data-stu-id="67265-105">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="67265-106">Bu öğreticinin sürecinde size bilgi edinin:</span><span class="sxs-lookup"><span data-stu-id="67265-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="67265-107">Bir Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="67265-107">How to create a Dockerfile</span></span>
> * <span data-ttu-id="67265-108">Bir .NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="67265-108">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="67265-109">Docker kapsayıcıya uygulamanızı dağıtmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="67265-109">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="67265-110">[Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) kullanan [Docker altyapısına](https://docs.docker.com/engine/docker-overview/#docker-engine) hızlı bir şekilde oluşturmak ve uygulamaları olarak paketlemek için [Docker görüntüleri](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="67265-110">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="67265-111">Bu görüntüleri yazılmış [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) dağıtılması ve çalıştırmak için biçimde bir [kapsayıcı katmanlı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="67265-111">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="67265-112">.NET core: başlamak için en kolay yolu</span><span class="sxs-lookup"><span data-stu-id="67265-112">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="67265-113">Docker görüntü oluşturmadan önce uygulamanın containerize gerekir.</span><span class="sxs-lookup"><span data-stu-id="67265-113">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="67265-114">Linux, MacOS veya Windows oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67265-114">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="67265-115">Bunu yapmak için hızlı ve en kolay yolu, .NET Core kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="67265-115">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="67265-116">.NET Core CLI araç takımı değilseniz, okuma [.NET Core SDK Genel Bakış](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="67265-116">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="67265-117">Hem Windows hem de Linux kapsayıcılarıyla yapı [çok arch dayalı etiketleri](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="67265-117">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="67265-118">İlk .NET Core Docker uygulamanızı</span><span class="sxs-lookup"><span data-stu-id="67265-118">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="67265-119">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="67265-119">Prerequisites</span></span>

<span data-ttu-id="67265-120">Bu öğreticiyi tamamlamak için:</span><span class="sxs-lookup"><span data-stu-id="67265-120">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="67265-121">.NET core 2.0 SDK'sı</span><span class="sxs-lookup"><span data-stu-id="67265-121">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="67265-122">Yükleme [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="67265-122">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="67265-123">Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="67265-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="67265-124">Henüz yapmadıysanız, sık kullanılan kod düzenleyicisinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="67265-124">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="67265-125">Kod Düzenleyicisi yüklemeniz gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="67265-125">Need to install a code editor?</span></span> <span data-ttu-id="67265-126">Deneyin [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="67265-126">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="67265-127">Docker istemcisi yükleme</span><span class="sxs-lookup"><span data-stu-id="67265-127">Installing Docker Client</span></span>

<span data-ttu-id="67265-128">Yükleme [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki.</span><span class="sxs-lookup"><span data-stu-id="67265-128">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="67265-129">Docker istemci yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="67265-129">The Docker client can be installed in:</span></span>

* <span data-ttu-id="67265-130">Linux dağıtımları</span><span class="sxs-lookup"><span data-stu-id="67265-130">Linux distributions</span></span>

   * [<span data-ttu-id="67265-131">CentOS</span><span class="sxs-lookup"><span data-stu-id="67265-131">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="67265-132">Debian</span><span class="sxs-lookup"><span data-stu-id="67265-132">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="67265-133">Fedora</span><span class="sxs-lookup"><span data-stu-id="67265-133">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="67265-134">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="67265-134">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="67265-135">macOS</span><span class="sxs-lookup"><span data-stu-id="67265-135">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="67265-136">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="67265-136">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="67265-137">Dockerization için bir .NET Core 2.0 konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="67265-137">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="67265-138">Bir komut istemi açın ve adlı bir klasör oluşturun *Hello*.</span><span class="sxs-lookup"><span data-stu-id="67265-138">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="67265-139">Oluşturduğunuz klasöre gidin ve aşağıdaki komutları yazın:</span><span class="sxs-lookup"><span data-stu-id="67265-139">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="67265-140">Şimdi hızlı bir kılavuz yapın:</span><span class="sxs-lookup"><span data-stu-id="67265-140">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="67265-141">[`dotnet new`](../tools/dotnet-new.md)güncel bir oluşturur `Hello.csproj` bir konsol uygulaması oluşturmak için gereken bağımlılıkları olan proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="67265-141">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="67265-142">Ayrıca oluşturur bir `Program.cs`, uygulama için giriş noktası içeren temel bir dosya.</span><span class="sxs-lookup"><span data-stu-id="67265-142">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="67265-143">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="67265-143">`Hello.csproj`:</span></span>

   <span data-ttu-id="67265-144">Proje dosyası bağımlılıkları geri yükleyin ve programı oluşturmak için gerekli olan her şeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="67265-144">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="67265-145">`OutputType` Etiketi bir yürütülebilir dosya, diğer bir deyişle bir konsol uygulaması oluşturduğunuz belirtir.</span><span class="sxs-lookup"><span data-stu-id="67265-145">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="67265-146">`TargetFramework` Etiketi hedefleme hangi .NET uygulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="67265-146">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="67265-147">Gelişmiş bir senaryo da birden çok hedef çerçeveyi belirtin ve tek bir işlem içinde belirtilen çerçeve için oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67265-147">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="67265-148">Bu öğreticide, .NET Core 2.0 için oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67265-148">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="67265-149">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="67265-149">`Program.cs`:</span></span>

   <span data-ttu-id="67265-150">Tarafından programı başlatan `using System`.</span><span class="sxs-lookup"><span data-stu-id="67265-150">The program starts by `using System`.</span></span> <span data-ttu-id="67265-151">Bu bildirimi anlamına gelir, "her şeyi Getir `System` ad alanı bu dosya için kapsam içine."</span><span class="sxs-lookup"><span data-stu-id="67265-151">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="67265-152">`System` Ad alanı içeren temel yapıları gibi `string`, veya sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="67265-152">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="67265-153">Ardından adlı bir ad alanı tanımlarız `Hello`.</span><span class="sxs-lookup"><span data-stu-id="67265-153">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="67265-154">Ad alanı için istediğiniz değişikliği yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67265-154">You can change namespace to anything you want.</span></span> <span data-ttu-id="67265-155">Adlı bir sınıf `Program` ad alanında, ile tanımlanmış bir `Main` yönteminin dizisini kendi bağımsız değişken olarak alan.</span><span class="sxs-lookup"><span data-stu-id="67265-155">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="67265-156">Bu dizi derlenmiş program çağrıldığında geçirilen bağımsız değişkenlerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="67265-156">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="67265-157">Bizim örneğimizde, programın yalnızca "Hello World!" yazar.</span><span class="sxs-lookup"><span data-stu-id="67265-157">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="67265-158">konsola.</span><span class="sxs-lookup"><span data-stu-id="67265-158">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="67265-159">.NET Core içinde 2.x **dotnet yeni** çalıştıran [ `dotnet restore` ](../tools/dotnet-restore.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="67265-159">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="67265-160">**DotNet geri yükleme** bağımlılıkları ile ağacının yükler bir [NuGet](https://www.nuget.org/)(.NET Paket Yöneticisi) çağrısı.</span><span class="sxs-lookup"><span data-stu-id="67265-160">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="67265-161">NuGet aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="67265-161">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="67265-162">çözümler *Hello.csproj* dosyası</span><span class="sxs-lookup"><span data-stu-id="67265-162">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="67265-163">dosya yüklemeleri bağımlılıkları (veya alan, makine önbelleğinden)</span><span class="sxs-lookup"><span data-stu-id="67265-163">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="67265-164">Yazar *obj/project.assets.json* dosyası</span><span class="sxs-lookup"><span data-stu-id="67265-164">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="67265-165">*Project.assets.json* NuGet bağımlılıkları grafiği, bağlama çözümleri ve diğer uygulama meta verileri eksiksiz bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="67265-165">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="67265-166">Bu dosya kullanılır diğer araçları tarafından gibi gerekli [ `dotnet build` ](../tools/dotnet-build.md) ve [ `dotnet run` ](../tools/dotnet-run.md), kaynak kodu doğru şekilde işleyemedi.</span><span class="sxs-lookup"><span data-stu-id="67265-166">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="67265-167">[`dotnet run`](../tools/dotnet-run.md)çağrıları [ `dotnet build` ](../tools/dotnet-build.md) başarılı bir yapı ve çağrılarını doğrulamak için `dotnet <assembly.dll>` uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="67265-167">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="67265-168">Gelişmiş senaryolar için bkz: [.NET Core uygulama dağıtımı](../deploying/index.md) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="67265-168">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="67265-169">.NET Core uygulama dockerize</span><span class="sxs-lookup"><span data-stu-id="67265-169">Dockerize the .NET Core application</span></span>

<span data-ttu-id="67265-170">Merhaba .NET Core konsol uygulaması başarıyla yerel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="67265-170">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="67265-171">Şimdi şirketinizdeki başka bir adım yapmanıza ve derleme ve Docker içinde uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="67265-171">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="67265-172">İlk Dockerfile</span><span class="sxs-lookup"><span data-stu-id="67265-172">Your first Dockerfile</span></span>

<span data-ttu-id="67265-173">Metin Düzenleyicisi'ni açın ve başlayalım!</span><span class="sxs-lookup"><span data-stu-id="67265-173">Open your text editor and let's get started!</span></span> <span data-ttu-id="67265-174">Hala uygulama oluşturduğumuz Hello dizininden çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="67265-174">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="67265-175">Ya da Linux aşağıdaki Docker yönergelerini ekleyin veya [Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) yeni bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="67265-175">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="67265-176">Tamamlandığında, kök Hello dizininizin kaydedin **Dockerfile**, uzantısı olmayan (dosya türü kümesine gerekebilir `All types (*.*)` veya benzeri).</span><span class="sxs-lookup"><span data-stu-id="67265-176">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="67265-177">Dockerfile sırayla çalışır Docker derleme yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="67265-177">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="67265-178">İlk yönergenin olmalıdır [ **FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="67265-178">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="67265-179">Bu yönerge, yeni bir derleme aşama başlatır ve temel görüntü yönergeleri için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="67265-179">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="67265-180">Birden çok yay etiketleri Windows veya Linux kapsayıcıları için Docker Windows bağlı olarak çekme [kapsayıcı modu](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span><span class="sxs-lookup"><span data-stu-id="67265-180">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="67265-181">2.0 sdk görüntünün microsoft/dotnet depodan bizim örnek için temel görüntüdür,</span><span class="sxs-lookup"><span data-stu-id="67265-181">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="67265-182">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) yönerge ayarlar çalışma dizini herhangi kalan çalışma, CMD, ENTRYPOINT, kopyalama ve Ekle Dockerfile için yönergeler.</span><span class="sxs-lookup"><span data-stu-id="67265-182">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="67265-183">Dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="67265-183">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="67265-184">Bu durumda, WORKDIR uygulama dizinine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="67265-184">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="67265-185">[ **Kopya** ](https://docs.docker.com/engine/reference/builder/#copy) yönerge yeni dosya veya dizinlerin kaynak yolundan kopyalar ve hedef kapsayıcı dosya sisteminde ekler.</span><span class="sxs-lookup"><span data-stu-id="67265-185">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="67265-186">Bu yönerge ile biz kapsayıcıya C# proje dosyası konumuna kopyalarsınız.</span><span class="sxs-lookup"><span data-stu-id="67265-186">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="67265-187">[ **Çalıştırmak** ](https://docs.docker.com/engine/reference/builder/#run) yönergesi geçerli görüntü üzerinde yeni bir katman içinde herhangi bir komut çalıştırır ve sonuçları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="67265-187">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="67265-188">Sonuçta elde edilen taahhüt edilen görüntü Dockerfile sonraki adımda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67265-188">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="67265-189">Çalıştırılmakta olan **dotnet geri yükleme** C# proje dosyası gerekli bağımlılıkları alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="67265-189">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="67265-190">Bu **kopya** yönerge kopyalar dosyaların geri kalanını bizim kapsayıcıya içine yeni [katmanları](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="67265-190">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="67265-191">Biz bu uygulamayla yayımlama **çalıştırmak** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="67265-191">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="67265-192">[ **Dotnet yayımlama** ](../tools/dotnet-publish.md) komutu uygulama derler, proje dosyasında belirtilen bağımlılıklarını aracılığıyla okur ve bir dizine dosyaları sonuç kümesini yayımlar.</span><span class="sxs-lookup"><span data-stu-id="67265-192">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="67265-193">Bizim uygulama ile yayımlanan bir **sürüm** yapılandırması ve varsayılan dizinine çıktı.</span><span class="sxs-lookup"><span data-stu-id="67265-193">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="67265-194">[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) yönerge bir yürütülebilir dosyayı çalıştırmak için kapsayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="67265-194">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="67265-195">Bir Dockerfile var. Bu:</span><span class="sxs-lookup"><span data-stu-id="67265-195">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="67265-196">Uygulamanızı görüntüye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="67265-196">copies your app to the image</span></span>
* <span data-ttu-id="67265-197">görüntüye uygulamanızın bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="67265-197">your app's dependencies to the image</span></span>
* <span data-ttu-id="67265-198">bir yürütülebilir dosya çalıştırmak için uygulamayı derlemeler</span><span class="sxs-lookup"><span data-stu-id="67265-198">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="67265-199">Derleme ve Hello .NET Core 2.0 uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="67265-199">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="67265-200">Temel Docker komutları</span><span class="sxs-lookup"><span data-stu-id="67265-200">Essential Docker commands</span></span>

<span data-ttu-id="67265-201">Bu Docker komutları gereklidir:</span><span class="sxs-lookup"><span data-stu-id="67265-201">These Docker commands are essential:</span></span>

* [<span data-ttu-id="67265-202">docker derleme</span><span class="sxs-lookup"><span data-stu-id="67265-202">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="67265-203">docker Çalıştır</span><span class="sxs-lookup"><span data-stu-id="67265-203">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="67265-204">docker ps</span><span class="sxs-lookup"><span data-stu-id="67265-204">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="67265-205">docker Durdur</span><span class="sxs-lookup"><span data-stu-id="67265-205">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="67265-206">docker rm</span><span class="sxs-lookup"><span data-stu-id="67265-206">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="67265-207">docker RMI</span><span class="sxs-lookup"><span data-stu-id="67265-207">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="67265-208">docker görüntüsü</span><span class="sxs-lookup"><span data-stu-id="67265-208">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="67265-209">Derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="67265-209">Build and run</span></span>

<span data-ttu-id="67265-210">Dockerfile yazdı; Şimdi Docker uygulamanızı oluşturur ve ardından kapsayıcı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="67265-210">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="67265-211">Çıktısını `docker build` komutu aşağıdaki konsol çıktısı benzer:</span><span class="sxs-lookup"><span data-stu-id="67265-211">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="67265-212">Çıktısını gördüğünüz gibi Docker altyapısına Dockerfile bizim kapsayıcı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67265-212">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="67265-213">Çıktısını `docker run` komutu aşağıdaki konsol çıktısı benzer:</span><span class="sxs-lookup"><span data-stu-id="67265-213">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="67265-214">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="67265-214">Congratulations!</span></span> <span data-ttu-id="67265-215">yalnızca gerekir:</span><span class="sxs-lookup"><span data-stu-id="67265-215">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="67265-216">Yerel bir .NET Core uygulaması oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="67265-216">Created a local .NET Core app</span></span>
> * <span data-ttu-id="67265-217">İlk kapsayıcı oluşturmak için bir Dockerfile oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="67265-217">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="67265-218">Yerleşik ve Dockerized uygulamanızı çalıştı</span><span class="sxs-lookup"><span data-stu-id="67265-218">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="67265-219">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="67265-219">Next Steps</span></span>

<span data-ttu-id="67265-220">Uygulayabileceğiniz bazı sonraki adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="67265-220">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="67265-221">.NET Docker görüntüleri Video giriş</span><span class="sxs-lookup"><span data-stu-id="67265-221">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="67265-222">Visual Studio, Docker & Azure kapsayıcı örnekleri birlikte daha iyi!</span><span class="sxs-lookup"><span data-stu-id="67265-222">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="67265-223">Azure Quickstarts için docker</span><span class="sxs-lookup"><span data-stu-id="67265-223">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="67265-224">Uygulamanızı Azure için Docker üzerinde dağıtma</span><span class="sxs-lookup"><span data-stu-id="67265-224">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="67265-225">Bir Azure aboneliğiniz yoksa [bugün kaydolun](https://azure.microsoft.com/free/?b=16.48) Ücretsiz 30 günlük hesabı ve Azure Hizmetleri herhangi bir bileşimini denemek için Azure KREDİLERİ 200 ABD Doları alın.</span><span class="sxs-lookup"><span data-stu-id="67265-225">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="67265-226">Bu örnekte kullanılan docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="67265-226">Docker Images used in this sample</span></span>

<span data-ttu-id="67265-227">Bu örnekte kullanılan aşağıdaki Docker yansımaları</span><span class="sxs-lookup"><span data-stu-id="67265-227">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="67265-228">İlgili Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="67265-228">Related Resources</span></span>

* [<span data-ttu-id="67265-229">.NET core Docker örnekleri</span><span class="sxs-lookup"><span data-stu-id="67265-229">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="67265-230">Windows kapsayıcılarında Dockerfile</span><span class="sxs-lookup"><span data-stu-id="67265-230">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="67265-231">.NET framework Docker örnekleri</span><span class="sxs-lookup"><span data-stu-id="67265-231">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="67265-232">ASP.NET Core DockerHub üzerinde</span><span class="sxs-lookup"><span data-stu-id="67265-232">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="67265-233">.NET Core uygulama - Docker öğretici dockerize</span><span class="sxs-lookup"><span data-stu-id="67265-233">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="67265-234">Visual Studio Docker araçları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="67265-234">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="67265-235">Azure kapsayıcı örneklerine Azure kapsayıcı kayıt defterinden Docker görüntüleri dağıtma</span><span class="sxs-lookup"><span data-stu-id="67265-235">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)