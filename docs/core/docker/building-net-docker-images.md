---
title: .NET Core Docker görüntülerinizi oluşturmak
description: Docker görüntüler ve .NET Core anlama
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: dotnet-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.custom: mvc
manager: wpickett
ms.workload:
- dotnetcore
ms.openlocfilehash: c1983be59b4a961cabd94915852e0cab7811682c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="7924c-103">.NET Core uygulamaları için Docker görüntülerinizi oluşturmak</span><span class="sxs-lookup"><span data-stu-id="7924c-103">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="7924c-104">Bu öğreticide, biz .NET Core üzerinde Docker kullanma odaklanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7924c-104">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="7924c-105">İlk olarak sunulan ve Microsoft ve kullanım örnekleri tarafından tutulan farklı Docker görüntüleri keşfedin.</span><span class="sxs-lookup"><span data-stu-id="7924c-105">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="7924c-106">Biz sonra yapı ve ASP.NET Core uygulama dockerize hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="7924c-106">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="7924c-107">Bu öğreticinin sürecinde size bilgi edinin:</span><span class="sxs-lookup"><span data-stu-id="7924c-107">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7924c-108">Microsoft .NET Core Docker görüntüler hakkında bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="7924c-108">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="7924c-109">Bir ASP.NET Core Dockerize için örnek uygulamayı Al</span><span class="sxs-lookup"><span data-stu-id="7924c-109">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="7924c-110">ASP.NET örnek uygulamayı yerel olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7924c-110">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="7924c-111">Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7924c-111">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="7924c-112">Derleme ve örnek ile Windows için Docker kapsayıcıları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7924c-112">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="7924c-113">Docker resmi en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="7924c-113">Docker Image Optimizations</span></span>

<span data-ttu-id="7924c-114">Geliştiriciler için Docker görüntülerinizi oluşturmak, biz üzerinde üç ana senaryo odaklanır:</span><span class="sxs-lookup"><span data-stu-id="7924c-114">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="7924c-115">.NET Core uygulamaları geliştirmek için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="7924c-115">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="7924c-116">.NET Core uygulamaları oluşturmak için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="7924c-116">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="7924c-117">.NET Core uygulamaları çalıştırmak için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="7924c-117">Images used to run .NET Core apps</span></span>

<span data-ttu-id="7924c-118">Neden üç görüntüleri?</span><span class="sxs-lookup"><span data-stu-id="7924c-118">Why three images?</span></span>
<span data-ttu-id="7924c-119">Geliştirme, derleme ve kapsayıcılı uygulamaları çalıştıran farklı önceliklere sahip olduğumuz.</span><span class="sxs-lookup"><span data-stu-id="7924c-119">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="7924c-120">**Geliştirme:** değişiklikleri ve değişiklikleri hata ayıklama özelliği öncelik odaklanır hızla yineleme.</span><span class="sxs-lookup"><span data-stu-id="7924c-120">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="7924c-121">Görüntünün boyutuna kadar önemli değilse, bunun yerine, değişiklik kodunuzu yapabilir ve hızlıca görmek?</span><span class="sxs-lookup"><span data-stu-id="7924c-121">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="7924c-122">**Derleme:** bu görüntü derleyici ve ikili dosyaları iyileştirmek için başka bir bağımlılık içerir, uygulamanızın derlemek için gereken her şeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="7924c-122">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="7924c-123">Yapı görüntünün bir üretim görüntüsüne yerleştirin varlıklar oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7924c-123">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="7924c-124">Yapı görüntü sürekli tümleştirme için veya bir yapı ortamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7924c-124">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="7924c-125">Bu yaklaşım derlemek ve uygulamada (tüm gerekli bağımlılıkları olan) bir yapı görüntü örneği oluşturmak derleme aracısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7924c-125">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="7924c-126">Derleme aracınızı, yalnızca bu Docker görüntü çalıştırma bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7924c-126">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="7924c-127">**Üretim:** ne kadar hızlı dağıtma ve görüntü başlatma?</span><span class="sxs-lookup"><span data-stu-id="7924c-127">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="7924c-128">Bu görüntü, Docker ana bilgisayarlarınız için Docker kayıt defterinden ağ performansı en iyi duruma getirilmiş şekilde küçüktür.</span><span class="sxs-lookup"><span data-stu-id="7924c-128">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="7924c-129">İçeriği Docker sonuçları işleme için Çalıştır'dan en iyi süreye etkinleştirme çalıştırmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="7924c-129">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="7924c-130">Dinamik kod derleme Docker modelinde gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7924c-130">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="7924c-131">Bu görüntüde yerleştirin içeriği ikili dosyaları ve uygulamayı çalıştırmak için gereken içerik için sınırlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7924c-131">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="7924c-132">Örneğin, `dotnet publish` çıktı içerir:</span><span class="sxs-lookup"><span data-stu-id="7924c-132">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="7924c-133">derlenmiş ikili dosyalar</span><span class="sxs-lookup"><span data-stu-id="7924c-133">the compiled binaries</span></span>
    * <span data-ttu-id="7924c-134">.js ve .css dosyaları</span><span class="sxs-lookup"><span data-stu-id="7924c-134">.js and .css files</span></span>


<span data-ttu-id="7924c-135">Eklenecek neden `dotnet publish` üretim görüntünüzü komut çıktısında olduğu tutmak için ' minimum boyut.</span><span class="sxs-lookup"><span data-stu-id="7924c-135">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="7924c-136">Bazı .NET Core görüntüleri katmanları son etiket indirme oldukça basit bir işlemdir şekilde farklı etiketler arasında paylaşın.</span><span class="sxs-lookup"><span data-stu-id="7924c-136">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="7924c-137">Makinenizde zaten daha eski bir sürümü varsa, bu mimarinin gerekli disk alanı azaltır.</span><span class="sxs-lookup"><span data-stu-id="7924c-137">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="7924c-138">Birden çok uygulama aynı makinede ortak görüntüleri kullandığınızda, bellek ortak görüntülerin arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="7924c-138">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="7924c-139">Görüntüleri paylaşılması için aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7924c-139">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="7924c-140">Docker görüntü farklılıkları</span><span class="sxs-lookup"><span data-stu-id="7924c-140">Docker image variations</span></span>

<span data-ttu-id="7924c-141">Görüntü çeşitleri altında sağladığımız yukarıdaki hedeflerinize ulaşmak için [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="7924c-141">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="7924c-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Bu görüntü .NET Core ve komut satırı araçları (CLI) içeren .NET Core SDK'sı içerir.</span><span class="sxs-lookup"><span data-stu-id="7924c-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="7924c-143">Bu görüntü eşlendiği **geliştirme senaryosu**.</span><span class="sxs-lookup"><span data-stu-id="7924c-143">This image maps to the **development scenario**.</span></span> <span data-ttu-id="7924c-144">Bu görüntü, yerel geliştirme, hata ayıklama ve birim testi için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7924c-144">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="7924c-145">Bu görüntü için de kullanılabilir, **yapı** senaryoları.</span><span class="sxs-lookup"><span data-stu-id="7924c-145">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="7924c-146">Kullanarak `microsoft/dotnet:sdk` her zaman en son sürümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="7924c-146">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="7924c-147">Kullanmak istediğiniz, gereksinimleriniz hakkında konusunda emin değilseniz `microsoft/dotnet:<version>-sdk` görüntü.</span><span class="sxs-lookup"><span data-stu-id="7924c-147">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="7924c-148">"Gerçek" görüntüsü olarak throw kullanılmak üzere tasarlanmıştır koyma kapsayıcı (kaynak kodu bağlayın ve kapsayıcı uygulamanızı başlatmak için Başlat) ve diğer görüntüleri oluşturmak için temel görüntü olarak.</span><span class="sxs-lookup"><span data-stu-id="7924c-148">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="7924c-149">`microsoft/dotnet:<version>-runtime`: Bu görüntü .NET Core (çalışma zamanı ve kitaplıklar) içerir ve .NET Core uygulamaları çalıştırmak için optimize edilmiştir **üretim**.</span><span class="sxs-lookup"><span data-stu-id="7924c-149">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="7924c-150">Alternatif görüntüleri</span><span class="sxs-lookup"><span data-stu-id="7924c-150">Alternative images</span></span>

<span data-ttu-id="7924c-151">Geliştirme, derleme ve üretim en iyi duruma getirilmiş senaryolara ek olarak, ek görüntüleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="7924c-151">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="7924c-152">`microsoft/dotnet:<version>-runtime-deps`**Çalışma zamanı deps** görüntü tüm .NET Core tarafından gerekli yerel bağımlılıklarını ile işletim sistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="7924c-152">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="7924c-153">Bu görüntü içindir [kendi içinde bulunan uygulamalar](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="7924c-153">This image is for [self-contained applications](../deploying/index.md).</span></span>

<span data-ttu-id="7924c-154">Her değişken en son sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7924c-154">Latest versions of each variant:</span></span>

* <span data-ttu-id="7924c-155">`microsoft/dotnet` veya `microsoft/dotnet:latest` (diğer ad SDK görüntüsü için)</span><span class="sxs-lookup"><span data-stu-id="7924c-155">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="7924c-156">Keşfetmek için örnekleri</span><span class="sxs-lookup"><span data-stu-id="7924c-156">Samples to explore</span></span>

* <span data-ttu-id="7924c-157">[Bu ASP.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) Docker görüntülerinizi ASP.NET Core için üretim için uygulamalar oluşturmak için en iyi yöntem desen gösterir.</span><span class="sxs-lookup"><span data-stu-id="7924c-157">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="7924c-158">Örnek, Linux ve Windows kapsayıcılarını ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="7924c-158">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="7924c-159">Bu .NET Core Docker örneği için en iyi yöntem deseni gösterir [üretim için .NET Core uygulamaları için Docker görüntülerinizi oluşturmak.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="7924c-159">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="7924c-160">İlk ASP.NET Core Docker uygulamanızı</span><span class="sxs-lookup"><span data-stu-id="7924c-160">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="7924c-161">Bu öğretici için dockerize istiyoruz uygulama için bir ASP.NET Core Docker örnek uygulama kullanarak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7924c-161">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="7924c-162">Bu ASP.NET Core Docker örnek uygulama Docker görüntülerinizi ASP.NET Core için üretim için uygulamalar oluşturmak için en iyi yöntem desen gösterir.</span><span class="sxs-lookup"><span data-stu-id="7924c-162">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="7924c-163">Örnek, Linux ve Windows kapsayıcılarını ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="7924c-163">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="7924c-164">Dockerfile örnek dışına ASP.NET çekirdeği çalışma zamanı Docker temel görüntü tabanlı bir ASP.NET Core uygulama Docker görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7924c-164">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="7924c-165">Kullandığı [Docker çok aşama yapı özelliği](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) için:</span><span class="sxs-lookup"><span data-stu-id="7924c-165">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="7924c-166">bağlı bir kapsayıcıdaki örneği oluşturmak **büyük** ASP.NET Core yapı Docker temel görüntüsü</span><span class="sxs-lookup"><span data-stu-id="7924c-166">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="7924c-167">temel bir Docker görüntüye son derleme sonucu kopyalar **küçük** ASP.NET çekirdeği Docker çalışma zamanı temel görüntüsü</span><span class="sxs-lookup"><span data-stu-id="7924c-167">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="7924c-168">Yapı görüntüsü çalışma zamanı görüntü çalışmazken uygulamaları geliştirmek için gerekli araçları içerir.</span><span class="sxs-lookup"><span data-stu-id="7924c-168">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7924c-169">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7924c-169">Prerequisites</span></span>

<span data-ttu-id="7924c-170">Derlemek ve çalıştırmak için aşağıdaki öğeleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="7924c-170">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="7924c-171">.NET core 2.0 SDK'sı</span><span class="sxs-lookup"><span data-stu-id="7924c-171">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="7924c-172">Yükleme [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="7924c-172">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="7924c-173">Henüz yapmadıysanız, sık kullanılan kod düzenleyicisinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7924c-173">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="7924c-174">Kod Düzenleyicisi yüklemeniz gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="7924c-174">Need to install a code editor?</span></span> <span data-ttu-id="7924c-175">Deneyin [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="7924c-175">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="7924c-176">Docker istemcisi yükleme</span><span class="sxs-lookup"><span data-stu-id="7924c-176">Installing Docker Client</span></span>

<span data-ttu-id="7924c-177">Yükleme [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki.</span><span class="sxs-lookup"><span data-stu-id="7924c-177">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="7924c-178">Docker istemci yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="7924c-178">The Docker client can be installed in:</span></span>

* <span data-ttu-id="7924c-179">Linux dağıtımları</span><span class="sxs-lookup"><span data-stu-id="7924c-179">Linux distributions</span></span>

   * [<span data-ttu-id="7924c-180">CentOS</span><span class="sxs-lookup"><span data-stu-id="7924c-180">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="7924c-181">Debian</span><span class="sxs-lookup"><span data-stu-id="7924c-181">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="7924c-182">Fedora</span><span class="sxs-lookup"><span data-stu-id="7924c-182">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="7924c-183">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7924c-183">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="7924c-184">macOS</span><span class="sxs-lookup"><span data-stu-id="7924c-184">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="7924c-185">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="7924c-185">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="7924c-186">Örnek depo için Git yükleme</span><span class="sxs-lookup"><span data-stu-id="7924c-186">Installing Git for sample repository</span></span>

* <span data-ttu-id="7924c-187">Yükleme [git](https://git-scm.com/download) depoyu kopyalayın istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="7924c-187">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="7924c-188">Örnek uygulama alma</span><span class="sxs-lookup"><span data-stu-id="7924c-188">Getting the sample application</span></span>

<span data-ttu-id="7924c-189">Kopyalama işlemi tarafından örnek almak için en kolay yolu olan [örnekleri depo](https://github.com/dotnet/dotnet-docker-samples) git ile aşağıdaki yönergeleri kullanarak:</span><span class="sxs-lookup"><span data-stu-id="7924c-189">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="7924c-190">.NET Core Docker örnekleri depodan bir zip olarak (küçük) deposu de indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7924c-190">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="7924c-191">ASP.NET uygulama yerel olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7924c-191">Run the ASP.NET app locally</span></span>

<span data-ttu-id="7924c-192">Biz uygulama containerize önce bir başvuru noktası için ilk uygulama yerel olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7924c-192">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="7924c-193">Derleme ve uygulamayı .NET Core 2.0 (yönergeleri depo kök varsayılmıştır) aşağıdaki komutları kullanarak SDK ile yerel olarak çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7924c-193">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="7924c-194">Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.</span><span class="sxs-lookup"><span data-stu-id="7924c-194">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="7924c-195">Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7924c-195">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="7924c-196">Derleme ve örnek (yönergeleri depo kök varsayılmıştır) aşağıdaki komutları kullanarak Linux kapsayıcıları kullanma Docker içinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7924c-196">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="7924c-197">`docker run` '-P' bağımsız değişkeni eşlemeleri bağlantı noktası 5000 kapsayıcının 80 numaralı bağlantı noktasına yerel makinenizde (bağlantı noktası eşleme form `host:container`).</span><span class="sxs-lookup"><span data-stu-id="7924c-197">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="7924c-198">Daha fazla bilgi için bkz: [çalıştırmak docker](https://docs.docker.com/engine/reference/commandline/exec/) komut satırı parametreleri başvuru.</span><span class="sxs-lookup"><span data-stu-id="7924c-198">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="7924c-199">Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.</span><span class="sxs-lookup"><span data-stu-id="7924c-199">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="7924c-200">Derleme ve örnek ile Windows için Docker kapsayıcıları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7924c-200">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="7924c-201">Derleme ve örnek (yönergeleri depo kök varsayılmıştır) aşağıdaki komutları kullanarak Windows kapsayıcıları kullanma Docker içinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7924c-201">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="7924c-202">İçin gezinmesi gereken **kapsayıcı IP adresi** (tersine http://localhost) doğrudan tarayıcınızda Windows kapsayıcıları kullanırken.</span><span class="sxs-lookup"><span data-stu-id="7924c-202">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="7924c-203">Aşağıdaki adımlarla, kapsayıcı IP adresini elde edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7924c-203">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="7924c-204">Başka bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="7924c-204">Open up another command prompt.</span></span>
* <span data-ttu-id="7924c-205">Çalıştırma `docker ps` çalışan kapsayıcıları görmek için.</span><span class="sxs-lookup"><span data-stu-id="7924c-205">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="7924c-206">"Aspnetcore_sample" kapsayıcı olması.</span><span class="sxs-lookup"><span data-stu-id="7924c-206">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="7924c-207">Çalıştırma `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="7924c-207">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="7924c-208">Kapsayıcı IP adresi kopyalayıp tarayıcınıza (örneğin, 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="7924c-208">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="7924c-209">Docker exec adı ya da karma ile tanımlayıcı kapsayıcıları destekler.</span><span class="sxs-lookup"><span data-stu-id="7924c-209">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="7924c-210">Bizim örneğimizde (aspnetcore_sample) adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7924c-210">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="7924c-211">Çalışan bir Windows kapsayıcısının IP adresini almak nasıl aşağıdaki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="7924c-211">See the following example of how to get the IP address of a running Windows container.</span></span>

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

> [!NOTE]
> <span data-ttu-id="7924c-212">Docker exec çalışan bir kapsayıcıda yeni bir komut çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7924c-212">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="7924c-213">Daha fazla bilgi için bkz: [docker exec başvuru](https://docs.docker.com/engine/reference/commandline/exec/) komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7924c-213">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="7924c-214">Kullanarak yerel olarak üretime dağıtmaya hazır bir uygulama oluşturmak üzere [dotnet yayımlama](../tools/dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="7924c-214">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c release -o published
```

> [!NOTE]
> <span data-ttu-id="7924c-215">-C yayın bağımsız değişkeni uygulama yayın modunda (hata ayıklama modu varsayılandır) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7924c-215">The -c release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="7924c-216">Daha fazla bilgi için bkz: [dotnet çalıştırmak başvuru](../tools/dotnet-run.md) komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7924c-216">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="7924c-217">Uygulamayı çalıştırmak **Windows** aşağıdaki komutu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7924c-217">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="7924c-218">Uygulamayı çalıştırmak **Linux** veya **macOS** aşağıdaki komutu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7924c-218">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="7924c-219">Bu örnekte kullanılan docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="7924c-219">Docker Images used in this sample</span></span>

<span data-ttu-id="7924c-220">Bu örnekte kullanılan aşağıdaki Docker yansımaları</span><span class="sxs-lookup"><span data-stu-id="7924c-220">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="7924c-221">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="7924c-221">Congratulations!</span></span> <span data-ttu-id="7924c-222">yalnızca gerekir:</span><span class="sxs-lookup"><span data-stu-id="7924c-222">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7924c-223">Microsoft .NET Core Docker görüntüler hakkında öğrendiniz</span><span class="sxs-lookup"><span data-stu-id="7924c-223">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="7924c-224">Bir ASP.NET Core Dockerize için örnek uygulama var</span><span class="sxs-lookup"><span data-stu-id="7924c-224">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="7924c-225">ASP.NET örnek uygulamayı yerel olarak çalışan</span><span class="sxs-lookup"><span data-stu-id="7924c-225">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="7924c-226">Yerleşik ve örnek Docker ile Linux kapsayıcıları için çalıştı.</span><span class="sxs-lookup"><span data-stu-id="7924c-226">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="7924c-227">Yerleşik ve örnek ile Windows için Docker kapsayıcıları çalıştı</span><span class="sxs-lookup"><span data-stu-id="7924c-227">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="7924c-228">**Sonraki adımlar**</span><span class="sxs-lookup"><span data-stu-id="7924c-228">**Next Steps**</span></span>

<span data-ttu-id="7924c-229">Uygulayabileceğiniz bazı sonraki adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7924c-229">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="7924c-230">Visual Studio Docker araçları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="7924c-230">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="7924c-231">Azure kapsayıcı örneklerine Azure kapsayıcı kayıt defterinden Docker görüntüleri dağıtma</span><span class="sxs-lookup"><span data-stu-id="7924c-231">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="7924c-232">Visual Studio Code ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="7924c-232">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="7924c-233">Ellere Visual Studio ile Mac, kapsayıcıları ve sunucusuz kodu bulutta hakkında alma</span><span class="sxs-lookup"><span data-stu-id="7924c-233">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="7924c-234">Mac Laboratuvar için Docker ve Visual Studio ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="7924c-234">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> <span data-ttu-id="7924c-235">Bir Azure aboneliğiniz yoksa [bugün kaydolun](https://azure.microsoft.com/free/?b=16.48) Ücretsiz 30 günlük hesabı ve Azure Hizmetleri herhangi bir bileşimini denemek için Azure KREDİLERİ 200 ABD Doları alın.</span><span class="sxs-lookup"><span data-stu-id="7924c-235">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
