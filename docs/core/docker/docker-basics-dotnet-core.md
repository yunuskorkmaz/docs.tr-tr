---
title: .NET Core ile Docker temellerini öğrenme
description: Docker ve .NET Core temel Öğreticisi
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 02b6b3fc9e149f5d1d5d78e310c7df257be983c1
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961553"
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="b9351-103">.NET Core ile Docker temellerini öğrenme</span><span class="sxs-lookup"><span data-stu-id="b9351-103">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="b9351-104">Bu öğreticide, Docker kapsayıcı derleme ve dağıtım görevleri bir .NET Core uygulaması için size öğretir.</span><span class="sxs-lookup"><span data-stu-id="b9351-104">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="b9351-105">Bu öğreticinin Kurs sırasında şunları öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b9351-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="b9351-106">Bir Dockerfile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9351-106">How to create a Dockerfile</span></span>
> * <span data-ttu-id="b9351-107">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9351-107">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="b9351-108">Uygulamanızı bir Docker kapsayıcısına dağıtma</span><span class="sxs-lookup"><span data-stu-id="b9351-108">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="b9351-109">[Docker platformu](https://docs.docker.com/engine/docker-overview/#the-docker-platform) kullanan [Docker altyapısı](https://docs.docker.com/engine/docker-overview/#docker-engine) oluşturmayı ve uygulamaları olarak paketini [Docker görüntülerini](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="b9351-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="b9351-110">Bu görüntüleri yazılan [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) dağıtılabilir ve çalışacak biçimde bir [kapsayıcı katmanlı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="b9351-110">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="b9351-111">.NET core: başlamanın en kolay yolu</span><span class="sxs-lookup"><span data-stu-id="b9351-111">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="b9351-112">Docker görüntüsünü oluşturmadan önce bir uygulamayı kapsayıcılı hale getirme için gerekir.</span><span class="sxs-lookup"><span data-stu-id="b9351-112">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="b9351-113">Linux, MacOS veya Windows üzerinde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9351-113">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="b9351-114">Bunu yapmanın hızlı ve en kolay yolu, .NET Core kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b9351-114">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="b9351-115">.NET Core CLI araç takımıyla bilmiyorsanız, okuma [.NET Core SDK'sı genel bakış](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="b9351-115">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="b9351-116">İle hem Windows hem de Linux kapsayıcıları oluşturabilirsiniz [çok arch tabanlı etiketleri](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="b9351-116">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="b9351-117">İlk .NET Core Docker uygulamanızı</span><span class="sxs-lookup"><span data-stu-id="b9351-117">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b9351-118">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b9351-118">Prerequisites</span></span>

<span data-ttu-id="b9351-119">Bu öğreticiyi tamamlamak için:</span><span class="sxs-lookup"><span data-stu-id="b9351-119">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="b9351-120">.NET core 2.0 SDK'sı</span><span class="sxs-lookup"><span data-stu-id="b9351-120">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="b9351-121">Yükleme [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="b9351-121">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="b9351-122">Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.</span><span class="sxs-lookup"><span data-stu-id="b9351-122">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="b9351-123">Henüz yapmadıysanız, sık kullandığınız kod düzenleyicinize yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b9351-123">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="b9351-124">Bir kod Düzenleyicisi'ni yüklemeniz gerekir?</span><span class="sxs-lookup"><span data-stu-id="b9351-124">Need to install a code editor?</span></span> <span data-ttu-id="b9351-125">Deneyin [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="b9351-125">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="b9351-126">Docker istemcisi yükleme</span><span class="sxs-lookup"><span data-stu-id="b9351-126">Installing Docker Client</span></span>

<span data-ttu-id="b9351-127">Yükleme [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="b9351-127">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="b9351-128">Docker istemcisi yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="b9351-128">The Docker client can be installed in:</span></span>

* <span data-ttu-id="b9351-129">Linux dağıtımları</span><span class="sxs-lookup"><span data-stu-id="b9351-129">Linux distributions</span></span>

   * [<span data-ttu-id="b9351-130">CentOS</span><span class="sxs-lookup"><span data-stu-id="b9351-130">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="b9351-131">Debian</span><span class="sxs-lookup"><span data-stu-id="b9351-131">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="b9351-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="b9351-132">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="b9351-133">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="b9351-133">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="b9351-134">macOS</span><span class="sxs-lookup"><span data-stu-id="b9351-134">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="b9351-135">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="b9351-135">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="b9351-136">Dockerization için bir .NET Core 2.0 konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9351-136">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="b9351-137">Bir komut istemi açın ve adlı bir klasör oluşturun *Hello*.</span><span class="sxs-lookup"><span data-stu-id="b9351-137">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="b9351-138">Oluşturduğunuz klasöre gidin ve aşağıdaki komutları yazın:</span><span class="sxs-lookup"><span data-stu-id="b9351-138">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="b9351-139">Hızlı bir kılavuz inceleyelim:</span><span class="sxs-lookup"><span data-stu-id="b9351-139">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="b9351-140">[`dotnet new`](../tools/dotnet-new.md) güncel bir oluşturur `Hello.csproj` bir konsol uygulaması oluşturmak gerekli bağımlılıkları olan proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="b9351-140">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="b9351-141">Ayrıca oluşturur bir `Program.cs`, uygulamanın giriş noktasını içeren temel bir dosya.</span><span class="sxs-lookup"><span data-stu-id="b9351-141">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="b9351-142">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="b9351-142">`Hello.csproj`:</span></span>

   <span data-ttu-id="b9351-143">Proje dosyası geri yükleme bağımlılıkları ve program oluşturmak için gerekli olan her şeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9351-143">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="b9351-144">`OutputType` Etiketini belirtir bir yürütülebilir dosya, başka bir deyişle bir konsol uygulaması oluşturuyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b9351-144">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="b9351-145">`TargetFramework` Hedefleyen hangi .NET uygulaması etiketini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9351-145">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="b9351-146">Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtin ve tek bir işlemde belirtilen çerçeveleri için oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b9351-146">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="b9351-147">Bu öğreticide, .NET Core 2.0 için ekleriz.</span><span class="sxs-lookup"><span data-stu-id="b9351-147">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="b9351-148">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="b9351-148">`Program.cs`:</span></span>

   <span data-ttu-id="b9351-149">Tarafından program başlar `using System`.</span><span class="sxs-lookup"><span data-stu-id="b9351-149">The program starts by `using System`.</span></span> <span data-ttu-id="b9351-150">Bu ifade anlamına gelir, "her şey Getir `System` ad alanına bu dosyası için kapsama girer."</span><span class="sxs-lookup"><span data-stu-id="b9351-150">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="b9351-151">`System` Ad alanı içeren temel yapılarından gibi `string`, ya da sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="b9351-151">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="b9351-152">Ad alanı ardından tanımlarız `Hello`.</span><span class="sxs-lookup"><span data-stu-id="b9351-152">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="b9351-153">Ad alanı için istediğiniz değişikliği yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9351-153">You can change namespace to anything you want.</span></span> <span data-ttu-id="b9351-154">Adlı bir sınıf `Program` ile bu ad alanı içinde tanımlanan bir `Main` dizisini kendi bağımsız değişkeni olarak alan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b9351-154">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="b9351-155">Bu dizi, derlenmiş programın çağrılırken geçirilen bağımsız değişken listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b9351-155">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="b9351-156">Bizim örneğimizde programı yalnızca "Hello World!" yazar.</span><span class="sxs-lookup"><span data-stu-id="b9351-156">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="b9351-157">konsola.</span><span class="sxs-lookup"><span data-stu-id="b9351-157">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="b9351-158">.NET core'da 2.x **yeni dotnet** çalıştıran [ `dotnet restore` ](../tools/dotnet-restore.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="b9351-158">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="b9351-159">**DotNet restore** bağımlılıklarla ağacının yükler bir [NuGet](https://www.nuget.org/)(.NET Paket Yöneticisi) çağrısı.</span><span class="sxs-lookup"><span data-stu-id="b9351-159">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="b9351-160">NuGet, aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="b9351-160">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="b9351-161">çözümler *Hello.csproj* dosyası</span><span class="sxs-lookup"><span data-stu-id="b9351-161">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="b9351-162">dosya yüklemeleri bağımlılıkları (veya Dallarınızla makine önbelleğinizden)</span><span class="sxs-lookup"><span data-stu-id="b9351-162">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="b9351-163">Yazar *obj/project.assets.json* dosyası</span><span class="sxs-lookup"><span data-stu-id="b9351-163">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="b9351-164">*Project.assets.json* eksiksiz bir NuGet bağımlılıklarını grafiği, bağlama çözümler ve diğer uygulama meta veri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="b9351-164">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="b9351-165">Bu dosya kullanılan diğer araçlarla gibi gerekli [ `dotnet build` ](../tools/dotnet-build.md) ve [ `dotnet run` ](../tools/dotnet-run.md), kaynak kodunu doğru şekilde işlemek için.</span><span class="sxs-lookup"><span data-stu-id="b9351-165">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="b9351-166">[`dotnet run`](../tools/dotnet-run.md) çağrıları [ `dotnet build` ](../tools/dotnet-build.md) başarılı bir derleme ve çağrılarını doğrulamak için `dotnet <assembly.dll>` uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b9351-166">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="b9351-167">Gelişmiş senaryolar için bkz: [.NET Core uygulaması dağıtımını](../deploying/index.md) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="b9351-167">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="b9351-168">.NET Core uygulamasını docker kapsayıcılarında çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b9351-168">Dockerize the .NET Core application</span></span>

<span data-ttu-id="b9351-169">Hello .NET Core konsol uygulamasının başarıyla yerel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="b9351-169">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="b9351-170">Şimdi github'dan bir adım ileri taşımak ve derleme ve uygulamayı Docker'da çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="b9351-170">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="b9351-171">İlk Dockerfile</span><span class="sxs-lookup"><span data-stu-id="b9351-171">Your first Dockerfile</span></span>

<span data-ttu-id="b9351-172">Metin Düzenleyicisi'ni açın ve başlayalım!</span><span class="sxs-lookup"><span data-stu-id="b9351-172">Open your text editor and let's get started!</span></span> <span data-ttu-id="b9351-173">Yine de uygulamayı oluşturduk Hello dizininden çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="b9351-173">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="b9351-174">Ya da Linux aşağıdaki Docker yönergelerini ekleyin veya [Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) yeni bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="b9351-174">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="b9351-175">İşiniz bittiğinde Hello dizininizin kökünde Kaydet **Dockerfile**, uzantı yoktur (dosya türünüze kümesine gerekebilir `All types (*.*)` veya benzer bir şey).</span><span class="sxs-lookup"><span data-stu-id="b9351-175">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

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

<span data-ttu-id="b9351-176">Dockerfile, sıralı olarak çalışan Docker derleme yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b9351-176">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="b9351-177">İlk yönerge olmalıdır [ **FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="b9351-177">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="b9351-178">Bu yönerge, yeni bir derleme aşaması başlatır ve yönergeleri için temel görüntüyü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b9351-178">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="b9351-179">Çok yay etiketleri Windows veya Linux kapsayıcıları için Docker Windows bağlı olarak çekme [kapsayıcı modu](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span><span class="sxs-lookup"><span data-stu-id="b9351-179">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="b9351-180">Bizim Örneğimiz için temel görüntüyü microsoft/dotnet deposundan 2.0 SDK'sını görüntüdür,</span><span class="sxs-lookup"><span data-stu-id="b9351-180">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="b9351-181">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) yönergesi ayarlar çalışma dizini herhangi kalan çalışma, CMD, ENTRYPOINT, kopyalama ve Ekle Dockerfile için yönergeler.</span><span class="sxs-lookup"><span data-stu-id="b9351-181">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="b9351-182">Dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b9351-182">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="b9351-183">Bu durumda, dockerfile'da kendisinden sonra gelen uygulama dizinine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b9351-183">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="b9351-184">[ **Kopyalama** ](https://docs.docker.com/engine/reference/builder/#copy) yönergesi kaynak yolundan yeni dosyaları veya dizinleri kopyalar ve onları hedef kapsayıcı dosya sisteminde ekler.</span><span class="sxs-lookup"><span data-stu-id="b9351-184">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="b9351-185">Bu yönerge ile size C# proje dosyası kapsayıcıya kopyalarsınız.</span><span class="sxs-lookup"><span data-stu-id="b9351-185">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="b9351-186">[ **ÇALIŞTIRMA** ](https://docs.docker.com/engine/reference/builder/#run) yönerge tüm komutları geçerli görüntünün üzerindeki yeni bir katmanda yürütür ve sonuçları işleyin.</span><span class="sxs-lookup"><span data-stu-id="b9351-186">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="b9351-187">Sonuçta elde edilen işlenmiş görüntü, Dockerfile'da bir sonraki adım için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b9351-187">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="b9351-188">Çalıştırılmakta olan **dotnet restore** C# proje dosyası gerekli bağımlılıkları almak için.</span><span class="sxs-lookup"><span data-stu-id="b9351-188">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="b9351-189">Bu **kopyalama** yönerge kopyalar dosyaların geri kalanı bizim kapsayıcıya içine yeni [katmanları](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="b9351-189">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="b9351-190">Biz bu uygulamayı yayımladığınız **ÇALIŞTIRMA** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="b9351-190">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="b9351-191">[ **Dotnet yayımlama** ](../tools/dotnet-publish.md) komut uygulamayı derler, bağımlılıkları proje dosyasında belirtilen aracılığıyla okur ve bir dizine dosya sonuç kümesini yayımlar.</span><span class="sxs-lookup"><span data-stu-id="b9351-191">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="b9351-192">Uygulamamızı ile yayımlanan bir **yayın** yapılandırma ve çıkış için varsayılan dizin.</span><span class="sxs-lookup"><span data-stu-id="b9351-192">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="b9351-193">[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) yönerge bir yürütülebilir dosyayı çalıştırmak kapsayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9351-193">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="b9351-194">Artık bir Dockerfile:</span><span class="sxs-lookup"><span data-stu-id="b9351-194">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="b9351-195">Uygulamanızı bir resme kopyalar.</span><span class="sxs-lookup"><span data-stu-id="b9351-195">copies your app to the image</span></span>
* <span data-ttu-id="b9351-196">Uygulamanızın bağımlılıklarına görüntüye</span><span class="sxs-lookup"><span data-stu-id="b9351-196">your app's dependencies to the image</span></span>
* <span data-ttu-id="b9351-197">yürütülebilir dosya olarak çalıştırmak için bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b9351-197">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="b9351-198">Hello .NET Core 2.0 uygulaması derleyebilir ve çalıştırabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="b9351-198">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="b9351-199">Temel Docker komutları</span><span class="sxs-lookup"><span data-stu-id="b9351-199">Essential Docker commands</span></span>

<span data-ttu-id="b9351-200">Bu Docker komutları büyük/küçük harf önemlidir:</span><span class="sxs-lookup"><span data-stu-id="b9351-200">These Docker commands are essential:</span></span>

* [<span data-ttu-id="b9351-201">docker derleme</span><span class="sxs-lookup"><span data-stu-id="b9351-201">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="b9351-202">docker Run</span><span class="sxs-lookup"><span data-stu-id="b9351-202">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="b9351-203">docker ps</span><span class="sxs-lookup"><span data-stu-id="b9351-203">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="b9351-204">docker durdurma</span><span class="sxs-lookup"><span data-stu-id="b9351-204">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="b9351-205">docker rm</span><span class="sxs-lookup"><span data-stu-id="b9351-205">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="b9351-206">docker RMI</span><span class="sxs-lookup"><span data-stu-id="b9351-206">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="b9351-207">docker görüntüsü</span><span class="sxs-lookup"><span data-stu-id="b9351-207">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="b9351-208">Derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b9351-208">Build and run</span></span>

<span data-ttu-id="b9351-209">Dockerfile yazdığınız; Şimdi Docker uygulamanızı oluşturur ve kapsayıcı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b9351-209">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="b9351-210">Çıkışı `docker build` komutu aşağıdaki konsol çıktısına benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b9351-210">The output from the `docker build` command should be similar to the following console output:</span></span>

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

<span data-ttu-id="b9351-211">Docker altyapısı Dockerfile çıktısı görebileceğiniz gibi bizim kapsayıcı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b9351-211">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="b9351-212">Çıkışı `docker run` komutu aşağıdaki konsol çıktısına benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b9351-212">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="b9351-213">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="b9351-213">Congratulations!</span></span> <span data-ttu-id="b9351-214">yalnızca gerekir:</span><span class="sxs-lookup"><span data-stu-id="b9351-214">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b9351-215">Yerel .NET Core uygulaması oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="b9351-215">Created a local .NET Core app</span></span>
> * <span data-ttu-id="b9351-216">Oluşturulan bir Dockerfile ilk kapsayıcınızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="b9351-216">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="b9351-217">Yerleşik ve Dockerized uygulamanızı çalıştı</span><span class="sxs-lookup"><span data-stu-id="b9351-217">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="b9351-218">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b9351-218">Next Steps</span></span>

<span data-ttu-id="b9351-219">Gerçekleştirebileceğiniz bazı sonraki adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b9351-219">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="b9351-220">.NET Docker görüntüleri Video giriş</span><span class="sxs-lookup"><span data-stu-id="b9351-220">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="b9351-221">Visual Studio, Docker ve Azure Container Instances, birlikte daha iyi!</span><span class="sxs-lookup"><span data-stu-id="b9351-221">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="b9351-222">Azure Hızlı Başlangıç için docker</span><span class="sxs-lookup"><span data-stu-id="b9351-222">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="b9351-223">Uygulamanızı Azure için Docker</span><span class="sxs-lookup"><span data-stu-id="b9351-223">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="b9351-224">Azure aboneliğiniz yoksa [hemen kaydolun](https://azure.microsoft.com/free/?b=16.48) 30 günlük ücretsiz hesabı ve get 200 ABD Doları değerinde Azure kredisi, out Azure Hizmetleri, herhangi bir birleşimini denemek için.</span><span class="sxs-lookup"><span data-stu-id="b9351-224">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="b9351-225">Bu örnekte kullanılan docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="b9351-225">Docker Images used in this sample</span></span>

<span data-ttu-id="b9351-226">Bu örnekte kullanılan aşağıdaki Docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="b9351-226">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="b9351-227">İlgili Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b9351-227">Related Resources</span></span>

* [<span data-ttu-id="b9351-228">.NET core Docker örnekleri</span><span class="sxs-lookup"><span data-stu-id="b9351-228">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="b9351-229">Dockerfile Windows kapsayıcıları hakkında</span><span class="sxs-lookup"><span data-stu-id="b9351-229">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="b9351-230">.NET framework Docker örnekleri</span><span class="sxs-lookup"><span data-stu-id="b9351-230">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="b9351-231">DockerHub üzerinde ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b9351-231">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="b9351-232">.NET Core uygulaması - Docker öğretici docker kapsayıcılarında çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b9351-232">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="b9351-233">Visual Studio Docker araçları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="b9351-233">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="b9351-234">Docker görüntülerini Azure Container registry'den Azure Container ınstances'a dağıtma</span><span class="sxs-lookup"><span data-stu-id="b9351-234">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)