---
title: Docker öğreticisiyle bir uygulamayı kapsayıcılı hale getirme
description: Bu öğreticide bir Docker ile .NET Core uygulamasını kapsayıcılı hale getirme öğreneceksiniz.
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 81dbcd5e0fd15048a0fc59bfeeef64bedbfeb769
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481138"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="3b52e-103">Öğretici: Kapsayıcılı bir .NET Core uygulaması</span><span class="sxs-lookup"><span data-stu-id="3b52e-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="3b52e-104">Bu öğreticide, .NET Core uygulamanızı içeren bir Docker görüntüsü oluşturmayı öğretiyor.</span><span class="sxs-lookup"><span data-stu-id="3b52e-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="3b52e-105">Görüntü, kapsayıcılar, yerel geliştirme ortamı, özel Bulut veya genel bulut oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b52e-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="3b52e-106">Bu öğreticide şunları öğreneceksiniz nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="3b52e-106">In this tutorial you will learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3b52e-107">Bir Dockerfile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b52e-107">Create a Dockerfile</span></span>
> * <span data-ttu-id="3b52e-108">Microsoft .NET Core Docker temel görüntüsünde çekme</span><span class="sxs-lookup"><span data-stu-id="3b52e-108">Pull a Microsoft .NET Core Docker base image</span></span>
> * <span data-ttu-id="3b52e-109">Görüntüyü uygulamanızı dağıtma ve özelleştirme</span><span class="sxs-lookup"><span data-stu-id="3b52e-109">Customize and deploy your app to the image</span></span>
> * <span data-ttu-id="3b52e-110">Oluşturma ve kapsayıcı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3b52e-110">Create and run a container</span></span>
> * <span data-ttu-id="3b52e-111">Azure’a dağıtma</span><span class="sxs-lookup"><span data-stu-id="3b52e-111">Deploy to Azure</span></span>

<span data-ttu-id="3b52e-112">Bu öğreticide, Docker kapsayıcı derleme ve dağıtım görevleri bir .NET Core uygulaması için size öğretir.</span><span class="sxs-lookup"><span data-stu-id="3b52e-112">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="3b52e-113">[Docker platformu](https://docs.docker.com/engine/docker-overview/#the-docker-platform) kullanan [Docker altyapısı](https://docs.docker.com/engine/docker-overview/#docker-engine) oluşturmayı ve uygulamaları olarak paketini [Docker görüntülerini](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="3b52e-113">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="3b52e-114">Bu görüntüleri yazılan [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) dağıtılabilir ve çalışacak biçimde bir [kapsayıcı katmanlı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="3b52e-114">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="3b52e-115">.NET core: Başlamanın en kolay yolu</span><span class="sxs-lookup"><span data-stu-id="3b52e-115">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="3b52e-116">Docker görüntüsünü oluşturmadan önce bir uygulamayı kapsayıcılı hale getirme için gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b52e-116">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="3b52e-117">Linux, MacOS veya Windows üzerinde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b52e-117">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="3b52e-118">Bunu yapmanın hızlı ve en kolay yolu, .NET Core kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3b52e-118">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="3b52e-119">.NET Core CLI araç takımıyla bilmiyorsanız, okuma [.NET Core SDK'sı genel bakış](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b52e-119">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="3b52e-120">İle hem Windows hem de Linux kapsayıcıları oluşturabilirsiniz [çok arch tabanlı etiketleri](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="3b52e-120">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="3b52e-121">İlk .NET Core Docker uygulamanızı</span><span class="sxs-lookup"><span data-stu-id="3b52e-121">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3b52e-122">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3b52e-122">Prerequisites</span></span>

<span data-ttu-id="3b52e-123">Bu öğreticiyi tamamlamak için:</span><span class="sxs-lookup"><span data-stu-id="3b52e-123">To complete this tutorial:</span></span>

#### <a name="net-core-sdk"></a><span data-ttu-id="3b52e-124">.NET core SDK'sı</span><span class="sxs-lookup"><span data-stu-id="3b52e-124">.NET Core SDK</span></span>

* <span data-ttu-id="3b52e-125">Yükleme [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="3b52e-125">Install [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later.</span></span>

<span data-ttu-id="3b52e-126">Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında işletim sistemlerinin tam listesi, .NET Core 2.1 desteklenen.</span><span class="sxs-lookup"><span data-stu-id="3b52e-126">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="3b52e-127">Henüz yapmadıysanız, sık kullandığınız kod düzenleyicinize yükleyin.</span><span class="sxs-lookup"><span data-stu-id="3b52e-127">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="3b52e-128">Bir kod Düzenleyicisi'ni yüklemeniz gerekir?</span><span class="sxs-lookup"><span data-stu-id="3b52e-128">Need to install a code editor?</span></span> <span data-ttu-id="3b52e-129">Deneyin [Visual Studio Code'u](https://code.visualstudio.com/download)!</span><span class="sxs-lookup"><span data-stu-id="3b52e-129">Try [Visual Studio Code](https://code.visualstudio.com/download)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="3b52e-130">Docker istemcisi yükleme</span><span class="sxs-lookup"><span data-stu-id="3b52e-130">Installing Docker Client</span></span>

<span data-ttu-id="3b52e-131">Yükleme [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="3b52e-131">Install [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="3b52e-132">Docker istemcisi yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="3b52e-132">The Docker client can be installed in:</span></span>

* <span data-ttu-id="3b52e-133">Linux dağıtımları</span><span class="sxs-lookup"><span data-stu-id="3b52e-133">Linux distributions</span></span>

  * [<span data-ttu-id="3b52e-134">CentOS</span><span class="sxs-lookup"><span data-stu-id="3b52e-134">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

  * [<span data-ttu-id="3b52e-135">Debian</span><span class="sxs-lookup"><span data-stu-id="3b52e-135">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

  * [<span data-ttu-id="3b52e-136">Fedora</span><span class="sxs-lookup"><span data-stu-id="3b52e-136">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

  * [<span data-ttu-id="3b52e-137">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3b52e-137">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="3b52e-138">macOS</span><span class="sxs-lookup"><span data-stu-id="3b52e-138">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="3b52e-139">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="3b52e-139">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

### <a name="create-a-net-core-21-console-app-for-dockerization"></a><span data-ttu-id="3b52e-140">Dockerization için bir .NET Core 2.1 konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b52e-140">Create a .NET Core 2.1 console app for Dockerization</span></span>

<span data-ttu-id="3b52e-141">Bir komut istemi açın ve adlı bir klasör oluşturun *Hello*.</span><span class="sxs-lookup"><span data-stu-id="3b52e-141">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="3b52e-142">Oluşturduğunuz klasöre gidin ve aşağıdaki komutları yazın:</span><span class="sxs-lookup"><span data-stu-id="3b52e-142">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="3b52e-143">Hızlı bir kılavuz inceleyelim:</span><span class="sxs-lookup"><span data-stu-id="3b52e-143">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="3b52e-144">[`dotnet new`](../tools/dotnet-new.md) güncel bir oluşturur `Hello.csproj` bir konsol uygulaması oluşturmak gerekli bağımlılıkları olan proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="3b52e-144">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="3b52e-145">Ayrıca oluşturur bir `Program.cs`, uygulamanın giriş noktasını içeren temel bir dosya.</span><span class="sxs-lookup"><span data-stu-id="3b52e-145">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   `Hello.csproj`<span data-ttu-id="3b52e-146">:</span><span class="sxs-lookup"><span data-stu-id="3b52e-146">:</span></span>

   <span data-ttu-id="3b52e-147">Proje dosyası geri yükleme bağımlılıkları ve program oluşturmak için gerekli olan her şeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b52e-147">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="3b52e-148">`OutputType` Etiketini belirtir bir yürütülebilir dosya, başka bir deyişle bir konsol uygulaması oluşturuyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="3b52e-148">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="3b52e-149">`TargetFramework` Hedefleyen hangi .NET uygulaması etiketini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b52e-149">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="3b52e-150">Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtin ve tek bir işlemde belirtilen çerçeveleri için oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3b52e-150">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="3b52e-151">Bu öğreticide, .NET Core 2.1 için ekleriz.</span><span class="sxs-lookup"><span data-stu-id="3b52e-151">In this tutorial, we build for .NET Core 2.1.</span></span>

   `Program.cs`<span data-ttu-id="3b52e-152">:</span><span class="sxs-lookup"><span data-stu-id="3b52e-152">:</span></span>

   <span data-ttu-id="3b52e-153">Tarafından program başlar `using System`.</span><span class="sxs-lookup"><span data-stu-id="3b52e-153">The program starts by `using System`.</span></span> <span data-ttu-id="3b52e-154">Bu ifade anlamına gelir, "her şey Getir `System` ad alanına bu dosyası için kapsama girer."</span><span class="sxs-lookup"><span data-stu-id="3b52e-154">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="3b52e-155">`System` Ad alanı içeren temel yapılarından gibi `string`, ya da sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="3b52e-155">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="3b52e-156">Ad alanı ardından tanımlarız `Hello`.</span><span class="sxs-lookup"><span data-stu-id="3b52e-156">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="3b52e-157">Ad alanı için istediğiniz değişikliği yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b52e-157">You can change namespace to anything you want.</span></span> <span data-ttu-id="3b52e-158">Adlı bir sınıf `Program` ile bu ad alanı içinde tanımlanan bir `Main` dizisini kendi bağımsız değişkeni olarak alan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3b52e-158">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="3b52e-159">Bu dizi, derlenmiş programın çağrılırken geçirilen bağımsız değişken listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3b52e-159">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="3b52e-160">Bizim örneğimizde programı yalnızca "Hello World!" yazar.</span><span class="sxs-lookup"><span data-stu-id="3b52e-160">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="3b52e-161">konsola.</span><span class="sxs-lookup"><span data-stu-id="3b52e-161">to the console.</span></span>

   <span data-ttu-id="3b52e-162">**Yeni dotnet** çalıştıran [ `dotnet restore` ](../tools/dotnet-restore.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="3b52e-162">**dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="3b52e-163">**DotNet restore** bağımlılıklarla ağacının yükler bir [NuGet](https://www.nuget.org/)(.NET Paket Yöneticisi) çağrısı.</span><span class="sxs-lookup"><span data-stu-id="3b52e-163">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="3b52e-164">NuGet, aşağıdaki görevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="3b52e-164">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="3b52e-165">çözümler *Hello.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="3b52e-165">analyzes the *Hello.csproj* file.</span></span>
   * <span data-ttu-id="3b52e-166">dosya yüklemeleri bağımlılıkları (veya Dallarınızla makine önbelleğinizden).</span><span class="sxs-lookup"><span data-stu-id="3b52e-166">downloads the file dependencies (or grabs from your machine cache).</span></span>
   * <span data-ttu-id="3b52e-167">Yazar *obj/project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="3b52e-167">writes the *obj/project.assets.json* file.</span></span>

   <span data-ttu-id="3b52e-168">*Project.assets.json* eksiksiz bir NuGet bağımlılıklarını grafiği, bağlama çözümler ve diğer uygulama meta veri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="3b52e-168">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="3b52e-169">Bu dosya kullanılan diğer araçlarla gibi gerekli [ `dotnet build` ](../tools/dotnet-build.md) ve [ `dotnet run` ](../tools/dotnet-run.md), kaynak kodunu doğru şekilde işlemek için.</span><span class="sxs-lookup"><span data-stu-id="3b52e-169">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>

2. `$ dotnet run`

   <span data-ttu-id="3b52e-170">[`dotnet run`](../tools/dotnet-run.md) çağrıları [ `dotnet build` ](../tools/dotnet-build.md) başarılı bir derleme ve çağrılarını doğrulamak için `dotnet <assembly.dll>` uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3b52e-170">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>

    ```console
    $ dotnet run

    Hello World!
    ```

    <span data-ttu-id="3b52e-171">Gelişmiş senaryolar için bkz: [.NET Core uygulaması dağıtımını](../deploying/index.md) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="3b52e-171">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="3b52e-172">.NET Core uygulamasını docker kapsayıcılarında çalıştırın</span><span class="sxs-lookup"><span data-stu-id="3b52e-172">Dockerize the .NET Core application</span></span>

<span data-ttu-id="3b52e-173">Hello .NET Core konsol uygulamasının başarıyla yerel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="3b52e-173">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="3b52e-174">Şimdi github'dan bir adım ileri taşımak ve derleme ve uygulamayı Docker'da çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="3b52e-174">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="3b52e-175">İlk Dockerfile</span><span class="sxs-lookup"><span data-stu-id="3b52e-175">Your first Dockerfile</span></span>

<span data-ttu-id="3b52e-176">Metin Düzenleyicisi'ni açın ve başlayalım!</span><span class="sxs-lookup"><span data-stu-id="3b52e-176">Open your text editor and let's get started!</span></span> <span data-ttu-id="3b52e-177">Yine de uygulamayı oluşturduk Hello dizininden çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="3b52e-177">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="3b52e-178">Ya da Linux aşağıdaki Docker yönergelerini ekleyin veya [Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) yeni bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="3b52e-178">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="3b52e-179">İşiniz bittiğinde Hello dizininizin kökünde Kaydet **Dockerfile**, uzantı yoktur (dosya türünüze kümesine gerekebilir `All types (*.*)` veya benzer bir şey).</span><span class="sxs-lookup"><span data-stu-id="3b52e-179">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="3b52e-180">Dockerfile, sıralı olarak çalışan Docker derleme yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3b52e-180">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="3b52e-181">İlk yönerge olmalıdır [ **FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="3b52e-181">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="3b52e-182">Bu yönerge, yeni bir derleme aşaması başlatır ve yönergeleri için temel görüntüyü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3b52e-182">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="3b52e-183">Çok yay etiketleri Windows veya Linux kapsayıcıları için Docker Windows bağlı olarak çekme [kapsayıcı modu](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span><span class="sxs-lookup"><span data-stu-id="3b52e-183">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="3b52e-184">Bizim Örneğimiz için temel görüntüyü microsoft/dotnet deposundan sdk 2.1 görüntüdür,</span><span class="sxs-lookup"><span data-stu-id="3b52e-184">The Base Image for our sample is the 2.1-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
```

<span data-ttu-id="3b52e-185">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) yönergesi ayarlar çalışma dizini herhangi kalan çalışma, CMD, ENTRYPOINT, kopyalama ve Ekle Dockerfile için yönergeler.</span><span class="sxs-lookup"><span data-stu-id="3b52e-185">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="3b52e-186">Dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b52e-186">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="3b52e-187">Bu durumda, dockerfile'da kendisinden sonra gelen uygulama dizinine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3b52e-187">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="3b52e-188">[ **Kopyalama** ](https://docs.docker.com/engine/reference/builder/#copy) yönergesi kaynak yolundan yeni dosyaları veya dizinleri kopyalar ve onları hedef kapsayıcı dosya sisteminde ekler.</span><span class="sxs-lookup"><span data-stu-id="3b52e-188">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="3b52e-189">Bu yönerge ile size C# proje dosyası kapsayıcıya kopyalarsınız.</span><span class="sxs-lookup"><span data-stu-id="3b52e-189">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="3b52e-190">[ **ÇALIŞTIRMA** ](https://docs.docker.com/engine/reference/builder/#run) yönerge tüm komutları geçerli görüntünün üzerindeki yeni bir katmanda yürütür ve sonuçları işleyin.</span><span class="sxs-lookup"><span data-stu-id="3b52e-190">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="3b52e-191">Sonuçta elde edilen işlenmiş görüntü, Dockerfile'da bir sonraki adım için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b52e-191">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="3b52e-192">Çalıştırılmakta olan **dotnet restore** C# proje dosyası gerekli bağımlılıkları almak için.</span><span class="sxs-lookup"><span data-stu-id="3b52e-192">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="3b52e-193">Bu **kopyalama** yönerge kopyalar dosyaların geri kalanı bizim kapsayıcıya içine yeni [katmanları](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="3b52e-193">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="3b52e-194">Biz bu uygulamayı yayımladığınız **ÇALIŞTIRMA** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="3b52e-194">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="3b52e-195">[ **Dotnet yayımlama** ](../tools/dotnet-publish.md) komut uygulamayı derler, bağımlılıkları proje dosyasında belirtilen aracılığıyla okur ve bir dizine dosya sonuç kümesini yayımlar.</span><span class="sxs-lookup"><span data-stu-id="3b52e-195">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="3b52e-196">Uygulamamızı ile yayımlanan bir **yayın** yapılandırma ve çıkış için varsayılan dizin.</span><span class="sxs-lookup"><span data-stu-id="3b52e-196">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="3b52e-197">[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) yönerge bir yürütülebilir dosyayı çalıştırmak kapsayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b52e-197">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="3b52e-198">Artık bir Dockerfile:</span><span class="sxs-lookup"><span data-stu-id="3b52e-198">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="3b52e-199">Uygulamanızı bir resme kopyalar.</span><span class="sxs-lookup"><span data-stu-id="3b52e-199">copies your app to the image</span></span>
* <span data-ttu-id="3b52e-200">Uygulamanızın bağımlılıklarına görüntüye</span><span class="sxs-lookup"><span data-stu-id="3b52e-200">your app's dependencies to the image</span></span>
* <span data-ttu-id="3b52e-201">yürütülebilir dosya olarak çalıştırmak için bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b52e-201">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-app"></a><span data-ttu-id="3b52e-202">Hello .NET Core uygulaması derleyebilir ve çalıştırabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="3b52e-202">Build and run the Hello .NET Core app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="3b52e-203">Temel Docker komutları</span><span class="sxs-lookup"><span data-stu-id="3b52e-203">Essential Docker commands</span></span>

<span data-ttu-id="3b52e-204">Bu Docker komutları büyük/küçük harf önemlidir:</span><span class="sxs-lookup"><span data-stu-id="3b52e-204">These Docker commands are essential:</span></span>

* [<span data-ttu-id="3b52e-205">docker derleme</span><span class="sxs-lookup"><span data-stu-id="3b52e-205">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="3b52e-206">docker Run</span><span class="sxs-lookup"><span data-stu-id="3b52e-206">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="3b52e-207">docker ps</span><span class="sxs-lookup"><span data-stu-id="3b52e-207">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="3b52e-208">docker durdurma</span><span class="sxs-lookup"><span data-stu-id="3b52e-208">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="3b52e-209">docker rm</span><span class="sxs-lookup"><span data-stu-id="3b52e-209">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="3b52e-210">docker RMI</span><span class="sxs-lookup"><span data-stu-id="3b52e-210">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="3b52e-211">docker görüntüsü</span><span class="sxs-lookup"><span data-stu-id="3b52e-211">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="3b52e-212">Derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3b52e-212">Build and run</span></span>

<span data-ttu-id="3b52e-213">Dockerfile yazdığınız; Şimdi Docker uygulamanızı oluşturur ve kapsayıcı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3b52e-213">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="3b52e-214">Çıkışı `docker build` komutu aşağıdaki konsol çıktısına benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3b52e-214">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   173.1kB
Step 1/7 : FROM microsoft/dotnet:2.1-sdk
 ---> 288f8c45f7c2
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
Successfully built 46db075bd98d
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="3b52e-215">Docker altyapısı Dockerfile çıktısı görebileceğiniz gibi bizim kapsayıcı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b52e-215">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="3b52e-216">Çıkışı `docker run` komutu aşağıdaki konsol çıktısına benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3b52e-216">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="3b52e-217">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="3b52e-217">Congratulations!</span></span> <span data-ttu-id="3b52e-218">yalnızca gerekir:</span><span class="sxs-lookup"><span data-stu-id="3b52e-218">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3b52e-219">Yerel .NET Core uygulaması oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="3b52e-219">Created a local .NET Core app</span></span>
> * <span data-ttu-id="3b52e-220">Oluşturulan bir Dockerfile ilk kapsayıcınızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="3b52e-220">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="3b52e-221">Yerleşik ve Dockerized uygulamanızı çalıştı</span><span class="sxs-lookup"><span data-stu-id="3b52e-221">Built and ran your Dockerized app</span></span>

## <a name="next-steps"></a><span data-ttu-id="3b52e-222">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3b52e-222">Next steps</span></span>

<span data-ttu-id="3b52e-223">Gerçekleştirebileceğiniz bazı sonraki adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b52e-223">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="3b52e-224">.NET Docker görüntüleri Video giriş</span><span class="sxs-lookup"><span data-stu-id="3b52e-224">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="3b52e-225">Visual Studio, Docker ve Azure Container Instances, birlikte daha iyi!</span><span class="sxs-lookup"><span data-stu-id="3b52e-225">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://medium.com/@AliMazaheri/visual-studio-docker-azure-container-instances-better-together-bf8c2f0419ae)
* [<span data-ttu-id="3b52e-226">Azure Hızlı Başlangıç için docker</span><span class="sxs-lookup"><span data-stu-id="3b52e-226">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="3b52e-227">Uygulamanızı Azure için Docker</span><span class="sxs-lookup"><span data-stu-id="3b52e-227">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!NOTE]
> <span data-ttu-id="3b52e-228">Azure aboneliğiniz yoksa [hemen kaydolun](https://azure.microsoft.com/free/?b=16.48) 30 günlük ücretsiz hesabı ve get 200 ABD Doları değerinde Azure kredisi, out Azure Hizmetleri, herhangi bir birleşimini denemek için.</span><span class="sxs-lookup"><span data-stu-id="3b52e-228">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="3b52e-229">Bu örnekte kullanılan docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="3b52e-229">Docker Images used in this sample</span></span>

<span data-ttu-id="3b52e-230">Bu örnekte kullanılan aşağıdaki Docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="3b52e-230">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.1-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="3b52e-231">İlgili kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3b52e-231">Related resources</span></span>

* [<span data-ttu-id="3b52e-232">.NET core Docker örnekleri</span><span class="sxs-lookup"><span data-stu-id="3b52e-232">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [<span data-ttu-id="3b52e-233">Dockerfile Windows kapsayıcıları hakkında</span><span class="sxs-lookup"><span data-stu-id="3b52e-233">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="3b52e-234">.NET framework Docker örnekleri</span><span class="sxs-lookup"><span data-stu-id="3b52e-234">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="3b52e-235">DockerHub üzerinde ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3b52e-235">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="3b52e-236">.NET Core uygulaması - Docker öğretici docker kapsayıcılarında çalıştırın</span><span class="sxs-lookup"><span data-stu-id="3b52e-236">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="3b52e-237">Visual Studio Docker araçları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="3b52e-237">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="3b52e-238">Docker görüntülerini Azure Container registry'den Azure Container ınstances'a dağıtma</span><span class="sxs-lookup"><span data-stu-id="3b52e-238">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
