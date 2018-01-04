---
title: ".NET Core Docker görüntülerinizi oluşturmak"
description: "Docker görüntüler ve .NET Core anlama"
keywords: .NET, .NET core, Docker
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
ms.openlocfilehash: cb438957a6519cf503e5bcaf85f2bc82fa18a047
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="53823-104">.NET Core uygulamaları için Docker görüntülerinizi oluşturmak</span><span class="sxs-lookup"><span data-stu-id="53823-104">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="53823-105">Bu öğreticide, biz .NET Core üzerinde Docker kullanma odaklanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53823-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="53823-106">İlk olarak sunulan ve Microsoft ve kullanım örnekleri tarafından tutulan farklı Docker görüntüleri keşfedin.</span><span class="sxs-lookup"><span data-stu-id="53823-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="53823-107">Biz sonra yapı ve ASP.NET Core uygulama dockerize hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="53823-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="53823-108">Bu öğreticinin sürecinde size bilgi edinin:</span><span class="sxs-lookup"><span data-stu-id="53823-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="53823-109">Microsoft .NET Core Docker görüntüler hakkında bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="53823-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="53823-110">Bir ASP.NET Core Dockerize için örnek uygulamayı Al</span><span class="sxs-lookup"><span data-stu-id="53823-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="53823-111">ASP.NET örnek uygulamayı yerel olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="53823-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="53823-112">Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="53823-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="53823-113">Derleme ve örnek ile Windows için Docker kapsayıcıları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="53823-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="53823-114">Docker resmi en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="53823-114">Docker Image Optimizations</span></span>

<span data-ttu-id="53823-115">Geliştiriciler için Docker görüntülerinizi oluşturmak, biz üzerinde üç ana senaryo odaklanır:</span><span class="sxs-lookup"><span data-stu-id="53823-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="53823-116">.NET Core uygulamaları geliştirmek için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="53823-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="53823-117">.NET Core uygulamaları oluşturmak için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="53823-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="53823-118">.NET Core uygulamaları çalıştırmak için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="53823-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="53823-119">Neden üç görüntüleri?</span><span class="sxs-lookup"><span data-stu-id="53823-119">Why three images?</span></span>
<span data-ttu-id="53823-120">Geliştirme, derleme ve kapsayıcılı uygulamaları çalıştıran farklı önceliklere sahip olduğumuz.</span><span class="sxs-lookup"><span data-stu-id="53823-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="53823-121">**Geliştirme:** değişiklikleri ve değişiklikleri hata ayıklama özelliği öncelik odaklanır hızla yineleme.</span><span class="sxs-lookup"><span data-stu-id="53823-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="53823-122">Görüntünün boyutuna kadar önemli değilse, bunun yerine, değişiklik kodunuzu yapabilir ve hızlıca görmek?</span><span class="sxs-lookup"><span data-stu-id="53823-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="53823-123">**Derleme:** bu görüntü derleyici ve ikili dosyaları iyileştirmek için başka bir bağımlılık içerir, uygulamanızın derlemek için gereken her şeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="53823-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="53823-124">Yapı görüntünün bir üretim görüntüsüne yerleştirin varlıklar oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="53823-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="53823-125">Yapı görüntü sürekli tümleştirme için veya bir yapı ortamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53823-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="53823-126">Bu yaklaşım derlemek ve uygulamada (tüm gerekli bağımlılıkları olan) bir yapı görüntü örneği oluşturmak derleme aracısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="53823-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="53823-127">Derleme aracınızı, yalnızca bu Docker görüntü çalıştırma bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="53823-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="53823-128">**Üretim:** ne kadar hızlı dağıtma ve görüntü başlatma?</span><span class="sxs-lookup"><span data-stu-id="53823-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="53823-129">Bu görüntü, Docker ana bilgisayarlarınız için Docker kayıt defterinden ağ performansı en iyi duruma getirilmiş şekilde küçüktür.</span><span class="sxs-lookup"><span data-stu-id="53823-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="53823-130">İçeriği Docker sonuçları işleme için Çalıştır'dan en iyi süreye etkinleştirme çalıştırmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="53823-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="53823-131">Dinamik kod derleme Docker modelinde gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="53823-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="53823-132">Bu görüntüde yerleştirin içeriği ikili dosyaları ve uygulamayı çalıştırmak için gereken içerik için sınırlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="53823-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="53823-133">Örneğin, `dotnet publish` çıktı içerir:</span><span class="sxs-lookup"><span data-stu-id="53823-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="53823-134">derlenmiş ikili dosyalar</span><span class="sxs-lookup"><span data-stu-id="53823-134">the compiled binaries</span></span>
    * <span data-ttu-id="53823-135">.js ve .css dosyaları</span><span class="sxs-lookup"><span data-stu-id="53823-135">.js and .css files</span></span>


<span data-ttu-id="53823-136">Eklenecek neden `dotnet publish` üretim görüntünüzü komut çıktısında olduğu tutmak için ' minimum boyut.</span><span class="sxs-lookup"><span data-stu-id="53823-136">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="53823-137">Bazı .NET Core görüntüleri katmanları son etiket indirme oldukça basit bir işlemdir şekilde farklı etiketler arasında paylaşın.</span><span class="sxs-lookup"><span data-stu-id="53823-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="53823-138">Makinenizde zaten daha eski bir sürümü varsa, bu mimarinin gerekli disk alanı azaltır.</span><span class="sxs-lookup"><span data-stu-id="53823-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="53823-139">Birden çok uygulama aynı makinede ortak görüntüleri kullandığınızda, bellek ortak görüntülerin arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="53823-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="53823-140">Görüntüleri paylaşılması için aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="53823-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="53823-141">Docker görüntü farklılıkları</span><span class="sxs-lookup"><span data-stu-id="53823-141">Docker image variations</span></span>

<span data-ttu-id="53823-142">Görüntü çeşitleri altında sağladığımız yukarıdaki hedeflerinize ulaşmak için [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="53823-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="53823-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Bu görüntü .NET Core ve komut satırı araçları (CLI) içeren .NET Core SDK'sı içerir.</span><span class="sxs-lookup"><span data-stu-id="53823-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="53823-144">Bu görüntü eşlendiği **geliştirme senaryosu**.</span><span class="sxs-lookup"><span data-stu-id="53823-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="53823-145">Bu görüntü, yerel geliştirme, hata ayıklama ve birim testi için kullanın.</span><span class="sxs-lookup"><span data-stu-id="53823-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="53823-146">Bu görüntü için de kullanılabilir, **yapı** senaryoları.</span><span class="sxs-lookup"><span data-stu-id="53823-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="53823-147">Kullanarak `microsoft/dotnet:sdk` her zaman en son sürümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="53823-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="53823-148">Kullanmak istediğiniz, gereksinimleriniz hakkında konusunda emin değilseniz `microsoft/dotnet:<version>-sdk` görüntü.</span><span class="sxs-lookup"><span data-stu-id="53823-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="53823-149">"Gerçek" görüntüsü olarak throw kullanılmak üzere tasarlanmıştır koyma kapsayıcı (kaynak kodu bağlayın ve kapsayıcı uygulamanızı başlatmak için Başlat) ve diğer görüntüleri oluşturmak için temel görüntü olarak.</span><span class="sxs-lookup"><span data-stu-id="53823-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="53823-150">`microsoft/dotnet:<version>-runtime`: Bu görüntü .NET Core (çalışma zamanı ve kitaplıklar) içerir ve .NET Core uygulamaları çalıştırmak için optimize edilmiştir **üretim**.</span><span class="sxs-lookup"><span data-stu-id="53823-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="53823-151">Alternatif görüntüleri</span><span class="sxs-lookup"><span data-stu-id="53823-151">Alternative images</span></span>

<span data-ttu-id="53823-152">Geliştirme, derleme ve üretim en iyi duruma getirilmiş senaryolara ek olarak, ek görüntüleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="53823-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="53823-153">`microsoft/dotnet:<version>-runtime-deps`**Çalışma zamanı deps** görüntü tüm .NET Core tarafından gerekli yerel bağımlılıklarını ile işletim sistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="53823-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="53823-154">Bu görüntü içindir [kendi içinde bulunan uygulamalar](https://docs.microsoft.com/dotnet/core/deploying/index).</span><span class="sxs-lookup"><span data-stu-id="53823-154">This image is for [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index).</span></span>

<span data-ttu-id="53823-155">Her değişken en son sürümleri:</span><span class="sxs-lookup"><span data-stu-id="53823-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="53823-156">`microsoft/dotnet`veya `microsoft/dotnet:latest` (diğer ad SDK görüntüsü için)</span><span class="sxs-lookup"><span data-stu-id="53823-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="53823-157">Keşfetmek için örnekleri</span><span class="sxs-lookup"><span data-stu-id="53823-157">Samples to explore</span></span>

* <span data-ttu-id="53823-158">[Bu ASP.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) Docker görüntülerinizi ASP.NET Core için üretim için uygulamalar oluşturmak için en iyi yöntem desen gösterir.</span><span class="sxs-lookup"><span data-stu-id="53823-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="53823-159">Örnek, Linux ve Windows kapsayıcılarını ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="53823-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="53823-160">Bu .NET Core Docker örneği için en iyi yöntem deseni gösterir [üretim için .NET Core uygulamaları için Docker görüntülerinizi oluşturmak.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="53823-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="53823-161">İlk ASP.NET Core Docker uygulamanızı</span><span class="sxs-lookup"><span data-stu-id="53823-161">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="53823-162">Bu öğretici için dockerize istiyoruz uygulama için bir ASP.NET Core Docker örnek uygulama kullanarak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="53823-162">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="53823-163">Bu ASP.NET Core Docker örnek uygulama Docker görüntülerinizi ASP.NET Core için üretim için uygulamalar oluşturmak için en iyi yöntem desen gösterir.</span><span class="sxs-lookup"><span data-stu-id="53823-163">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="53823-164">Örnek, Linux ve Windows kapsayıcılarını ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="53823-164">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="53823-165">Dockerfile örnek dışına ASP.NET çekirdeği çalışma zamanı Docker temel görüntü tabanlı bir ASP.NET Core uygulama Docker görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53823-165">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="53823-166">Kullandığı [Docker çok aşama yapı özelliği](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) için:</span><span class="sxs-lookup"><span data-stu-id="53823-166">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="53823-167">bağlı bir kapsayıcıdaki örneği oluşturmak **büyük** ASP.NET Core yapı Docker temel görüntüsü</span><span class="sxs-lookup"><span data-stu-id="53823-167">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="53823-168">temel bir Docker görüntüye son derleme sonucu kopyalar **küçük** ASP.NET çekirdeği Docker çalışma zamanı temel görüntüsü</span><span class="sxs-lookup"><span data-stu-id="53823-168">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!Note]
> <span data-ttu-id="53823-169">Yapı görüntüsü çalışma zamanı görüntü çalışmazken uygulamaları geliştirmek için gerekli araçları içerir.</span><span class="sxs-lookup"><span data-stu-id="53823-169">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="53823-170">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="53823-170">Prerequisites</span></span>

<span data-ttu-id="53823-171">Derlemek ve çalıştırmak için aşağıdaki öğeleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="53823-171">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="53823-172">.NET core 2.0 SDK'sı</span><span class="sxs-lookup"><span data-stu-id="53823-172">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="53823-173">Yükleme [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="53823-173">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="53823-174">Henüz yapmadıysanız, sık kullanılan kod düzenleyicisinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="53823-174">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="53823-175">Kod Düzenleyicisi yüklemeniz gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="53823-175">Need to install a code editor?</span></span> <span data-ttu-id="53823-176">Deneyin [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="53823-176">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="53823-177">Docker istemcisi yükleme</span><span class="sxs-lookup"><span data-stu-id="53823-177">Installing Docker Client</span></span>

<span data-ttu-id="53823-178">Yükleme [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki.</span><span class="sxs-lookup"><span data-stu-id="53823-178">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="53823-179">Docker istemci yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="53823-179">The Docker client can be installed in:</span></span>

* <span data-ttu-id="53823-180">Linux dağıtımları</span><span class="sxs-lookup"><span data-stu-id="53823-180">Linux distributions</span></span>

   * [<span data-ttu-id="53823-181">CentOS</span><span class="sxs-lookup"><span data-stu-id="53823-181">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="53823-182">Debian</span><span class="sxs-lookup"><span data-stu-id="53823-182">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="53823-183">Fedora</span><span class="sxs-lookup"><span data-stu-id="53823-183">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="53823-184">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="53823-184">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="53823-185">macOS</span><span class="sxs-lookup"><span data-stu-id="53823-185">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="53823-186">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="53823-186">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="53823-187">Örnek depo için Git yükleme</span><span class="sxs-lookup"><span data-stu-id="53823-187">Installing Git for sample repository</span></span>

* <span data-ttu-id="53823-188">Yükleme [git](https://git-scm.com/download) depoyu kopyalayın istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="53823-188">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="53823-189">Örnek uygulama alma</span><span class="sxs-lookup"><span data-stu-id="53823-189">Getting the sample application</span></span>

<span data-ttu-id="53823-190">Kopyalama işlemi tarafından örnek almak için en kolay yolu olan [örnekleri depo](https://github.com/dotnet/dotnet-docker-samples) git ile aşağıdaki yönergeleri kullanarak:</span><span class="sxs-lookup"><span data-stu-id="53823-190">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="53823-191">.NET Core Docker örnekleri depodan bir zip olarak (küçük) deposu de indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53823-191">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="53823-192">ASP.NET uygulama yerel olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="53823-192">Run the ASP.NET app locally</span></span>

<span data-ttu-id="53823-193">Biz uygulama containerize önce bir başvuru noktası için ilk uygulama yerel olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="53823-193">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="53823-194">Derleme ve uygulamayı .NET Core 2.0 (yönergeleri depo kök varsayılmıştır) aşağıdaki komutları kullanarak SDK ile yerel olarak çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="53823-194">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="53823-195">Uygulama başlatıldıktan sonra ziyaret **http://localhost: 5000** web tarayıcınızda.</span><span class="sxs-lookup"><span data-stu-id="53823-195">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="53823-196">Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="53823-196">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="53823-197">Derleme ve örnek (yönergeleri depo kök varsayılmıştır) aşağıdaki komutları kullanarak Linux kapsayıcıları kullanma Docker içinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="53823-197">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] <span data-ttu-id="53823-198">`docker run` '-P' bağımsız değişkeni eşlemeleri bağlantı noktası 5000 kapsayıcının 80 numaralı bağlantı noktasına yerel makinenizde (bağlantı noktası eşleme form `host:container`).</span><span class="sxs-lookup"><span data-stu-id="53823-198">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="53823-199">Daha fazla bilgi için bkz: [çalıştırmak docker](https://docs.docker.com/engine/reference/commandline/exec/) komut satırı parametreleri başvuru.</span><span class="sxs-lookup"><span data-stu-id="53823-199">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="53823-200">Uygulama başlatıldıktan sonra ziyaret **http://localhost: 5000** web tarayıcınızda.</span><span class="sxs-lookup"><span data-stu-id="53823-200">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="53823-201">Derleme ve örnek ile Windows için Docker kapsayıcıları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="53823-201">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="53823-202">Derleme ve örnek (yönergeleri depo kök varsayılmıştır) aşağıdaki komutları kullanarak Windows kapsayıcıları kullanma Docker içinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="53823-202">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="53823-203">İçin gezinmesi gereken **kapsayıcı IP adresi** (aksine http://localhost) doğrudan tarayıcınızda Windows kapsayıcıları kullanırken.</span><span class="sxs-lookup"><span data-stu-id="53823-203">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="53823-204">Aşağıdaki adımlarla, kapsayıcı IP adresini elde edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="53823-204">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="53823-205">Başka bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="53823-205">Open up another command prompt.</span></span>
* <span data-ttu-id="53823-206">Çalıştırma `docker ps` çalışan kapsayıcıları görmek için.</span><span class="sxs-lookup"><span data-stu-id="53823-206">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="53823-207">"Aspnetcore_sample" kapsayıcı olması.</span><span class="sxs-lookup"><span data-stu-id="53823-207">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="53823-208">Çalıştırma `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="53823-208">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="53823-209">Kapsayıcı IP adresi kopyalayıp tarayıcınıza (örneğin, 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="53823-209">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!Note]
> <span data-ttu-id="53823-210">Docker exec adı ya da karma ile tanımlayıcı kapsayıcıları destekler.</span><span class="sxs-lookup"><span data-stu-id="53823-210">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="53823-211">Bizim örneğimizde (aspnetcore_sample) adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53823-211">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="53823-212">Çalışan bir Windows kapsayıcısının IP adresini almak nasıl aşağıdaki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="53823-212">See the following example of how to get the IP address of a running Windows container.</span></span>

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!Note]
> <span data-ttu-id="53823-213">Docker exec çalışan bir kapsayıcıda yeni bir komut çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="53823-213">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="53823-214">Daha fazla bilgi için bkz: [docker exec başvuru](https://docs.docker.com/engine/reference/commandline/exec/) komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="53823-214">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="53823-215">Kullanarak yerel olarak üretime dağıtmaya hazır bir uygulama oluşturmak üzere [dotnet yayımlama](../tools/dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="53823-215">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c release -o published
```

> [!Note]
> <span data-ttu-id="53823-216">-C yayın bağımsız değişkeni uygulama yayın modunda (hata ayıklama modu varsayılandır) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53823-216">The -c release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="53823-217">Daha fazla bilgi için bkz: [dotnet çalıştırmak başvuru](../tools/dotnet-run.md) komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="53823-217">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="53823-218">Uygulamayı çalıştırmak **Windows** aşağıdaki komutu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="53823-218">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="53823-219">Uygulamayı çalıştırmak **Linux** veya **macOS** aşağıdaki komutu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="53823-219">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="53823-220">Bu örnekte kullanılan docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="53823-220">Docker Images used in this sample</span></span>

<span data-ttu-id="53823-221">Bu örnekte kullanılan aşağıdaki Docker yansımaları</span><span class="sxs-lookup"><span data-stu-id="53823-221">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="53823-222">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="53823-222">Congratulations!</span></span> <span data-ttu-id="53823-223">yalnızca gerekir:</span><span class="sxs-lookup"><span data-stu-id="53823-223">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="53823-224">Microsoft .NET Core Docker görüntüler hakkında öğrendiniz</span><span class="sxs-lookup"><span data-stu-id="53823-224">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="53823-225">Bir ASP.NET Core Dockerize için örnek uygulama var</span><span class="sxs-lookup"><span data-stu-id="53823-225">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="53823-226">ASP.NET örnek uygulamayı yerel olarak çalışan</span><span class="sxs-lookup"><span data-stu-id="53823-226">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="53823-227">Yerleşik ve örnek Docker ile Linux kapsayıcıları için çalıştı.</span><span class="sxs-lookup"><span data-stu-id="53823-227">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="53823-228">Yerleşik ve örnek ile Windows için Docker kapsayıcıları çalıştı</span><span class="sxs-lookup"><span data-stu-id="53823-228">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="53823-229">**Sonraki adımlar**</span><span class="sxs-lookup"><span data-stu-id="53823-229">**Next Steps**</span></span>

<span data-ttu-id="53823-230">Uygulayabileceğiniz bazı sonraki adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="53823-230">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="53823-231">Visual Studio Docker araçları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="53823-231">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="53823-232">Azure kapsayıcı örneklerine Azure kapsayıcı kayıt defterinden Docker görüntüleri dağıtma</span><span class="sxs-lookup"><span data-stu-id="53823-232">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="53823-233">Visual Studio Code ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="53823-233">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="53823-234">Ellere Visual Studio ile Mac, kapsayıcıları ve sunucusuz kodu bulutta hakkında alma</span><span class="sxs-lookup"><span data-stu-id="53823-234">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="53823-235">Mac Laboratuvar için Docker ve Visual Studio ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="53823-235">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> <span data-ttu-id="53823-236">Bir Azure aboneliğiniz yoksa [bugün kaydolun](https://azure.microsoft.com/free/?b=16.48) Ücretsiz 30 günlük hesabı ve Azure Hizmetleri herhangi bir bileşimini denemek için Azure KREDİLERİ 200 ABD Doları alın.</span><span class="sxs-lookup"><span data-stu-id="53823-236">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
