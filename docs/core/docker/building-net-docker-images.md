---
title: Docker görüntülerini genel bakış
description: Docker kayıt defterinden yayımlanan .NET Core Docker görüntüleri kullanmayı öğrenin. Ayrıca, görüntüleri çekmek ve kendi görüntülerinizi oluşturmayı öğreneceksiniz.
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: dbe509269c1dc5868c44b12b025bbdd9faaa3508
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169345"
---
# <a name="learn-about-docker-images-for-net-core"></a><span data-ttu-id="dbe5f-104">.NET Core için Docker görüntüleri hakkında bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="dbe5f-104">Learn about Docker images for .NET Core</span></span>

<span data-ttu-id="dbe5f-105">Bu öğreticide, .NET Core üzerinde Docker nasıl odaklanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="dbe5f-106">İlk olarak sunulur ve Microsoft ve kullanım örnekleri tarafından tutulan farklı bir Docker görüntüleri keşfedin.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="dbe5f-107">Biz, daha sonra nasıl oluşturacağınızı ve ASP.NET Core uygulaması docker kapsayıcılarında çalıştırın öğrenin.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="dbe5f-108">Bu öğreticinin Kurs sırasında şunları öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="dbe5f-109">Microsoft .NET Core Docker görüntüleri hakkında bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="dbe5f-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="dbe5f-110">Bir ASP.NET Core Dockerize örnek uygulaması alma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="dbe5f-111">ASP.NET örnek uygulamayı yerel olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="dbe5f-112">Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="dbe5f-113">Derleme ve örnek için Docker Windows kapsayıcıları ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="dbe5f-114">Docker görüntüsünü en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="dbe5f-114">Docker Image Optimizations</span></span>

<span data-ttu-id="dbe5f-115">Geliştiriciler için Docker görüntülerini oluştururken, biz üç ana senaryo üzerinde odaklanır:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="dbe5f-116">.NET Core uygulamaları geliştirmek için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="dbe5f-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="dbe5f-117">.NET Core uygulamaları oluşturmak için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="dbe5f-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="dbe5f-118">.NET Core uygulamaları çalıştırmak için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="dbe5f-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="dbe5f-119">Neden üç görüntüleri?</span><span class="sxs-lookup"><span data-stu-id="dbe5f-119">Why three images?</span></span>
<span data-ttu-id="dbe5f-120">Geliştirme, derleme ve kapsayıcılı uygulamalar çalıştırmak, farklı önceliklere sahibiz.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="dbe5f-121">**Geliştirme:**  Öncelik odaklanır, değişiklikler ve değişiklikleri hata ayıklama özelliği hızla yineleyin.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="dbe5f-122">Resmin boyutu önemli değildir, bunun yerine, değişiklikler kodunuza yapabilir ve bunları hızlıca görmek?</span><span class="sxs-lookup"><span data-stu-id="dbe5f-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="dbe5f-123">**Derleme:** Bu görüntü derleyici ve ikili dosyaları iyileştirmek için diğer herhangi bir bağımlılığın içeren uygulamanızı derlemek için gereken her şeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="dbe5f-124">Derleme görüntüyü bir üretim görüntüsüne yerleştirdiğiniz varlıkları oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="dbe5f-125">Derleme görüntüsünü veya bir yapı ortamı sürekli tümleştirme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="dbe5f-126">Bu yaklaşım, derlemek ve bir yapı görüntü örneği (tüm gerekli bağımlılıkları olan) uygulamasında oluşturmak bir yapı aracısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="dbe5f-127">Yapı aracınız, yalnızca bu Docker görüntüsünü çalıştırma bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="dbe5f-128">**Üretim:** Ne kadar hızlı dağıtma ve başlatma, resmi?</span><span class="sxs-lookup"><span data-stu-id="dbe5f-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="dbe5f-129">Bu görüntü, Docker kayıt defterinizin Docker konaklarınız için ağ performansı en iyi duruma getirilmiş şekilde küçüktür.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="dbe5f-130">İçeriği, Docker run sonuçları işlemek için hızlı süreye etkinleştirme çalıştırmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="dbe5f-131">Dinamik kod derlemesi, Docker modelde gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="dbe5f-132">Bu görüntüde yerleştirdiğiniz içeriği ikili dosyaları ve uygulamayı çalıştırmak için gerekli içeriklere sınırlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="dbe5f-133">Örneğin, `dotnet publish` çıktı içerir:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="dbe5f-134">derlenmiş ikili dosyaları</span><span class="sxs-lookup"><span data-stu-id="dbe5f-134">the compiled binaries</span></span>
    * <span data-ttu-id="dbe5f-135">.js ve .css dosyaları</span><span class="sxs-lookup"><span data-stu-id="dbe5f-135">.js and .css files</span></span>


<span data-ttu-id="dbe5f-136">Eklenecek nedeni `dotnet publish` üretim görüntünüzü komut çıktısında boyutuna dürüst etmektir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-136">The reason to include the `dotnet publish` command output in your production image is to keep its size to a minimum.</span></span>

<span data-ttu-id="dbe5f-137">Bazı .NET Core görüntüleri Katmanlar oldukça basit bir işlem en son etiket indiriliyor, bu nedenle farklı etiketler arasında paylaşın.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="dbe5f-138">Makinenizde zaten daha eski bir sürümü varsa, bu mimaride gerekli disk alanını azaltır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="dbe5f-139">Birden çok uygulama aynı makinede genel görüntülerden kullandığınızda, bellek ortak görüntülerin arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="dbe5f-140">Görüntüleri paylaşılması için aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="dbe5f-141">Docker görüntüsü farklılıkları</span><span class="sxs-lookup"><span data-stu-id="dbe5f-141">Docker image variations</span></span>

<span data-ttu-id="dbe5f-142">Görüntü çeşitleri altında sağladığımız yukarıdaki hedeflere ulaşmak için [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="dbe5f-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="dbe5f-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Bu görüntü .NET Core ve komut satırı araçları'nı (CLI) içerir .NET Core SDK'sı içerir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="dbe5f-144">Bu görüntü eşlendiği **geliştirme senaryosu**.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="dbe5f-145">Bu görüntü, yerel geliştirme, hata ayıklama ve birim testi için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="dbe5f-146">Bu görüntü için de kullanılabilir, **derleme** senaryoları.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="dbe5f-147">Kullanarak `microsoft/dotnet:sdk` , en son sürümü her zaman verir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="dbe5f-148">Gereksinimlerinizi hakkında konusunda emin değilseniz, kullanmak istediğiniz `microsoft/dotnet:<version>-sdk` görüntü.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="dbe5f-149">"Pratikte" görüntü olarak throw kullanılmak üzere tasarlanmıştır koyma kapsayıcı (kaynak kodunuzu bağlayın ve uygulamanızı başlatmak için bir kapsayıcı başlatma) ve diğer görüntüleri oluşturmak için temel görüntü olarak.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="dbe5f-150">`microsoft/dotnet:<version>-runtime`: Bu görüntü, .NET Core (çalışma zamanı ve kitaplıklarda) içerir ve .NET Core uygulamaları çalıştırma için optimize edilmiştir **üretim**.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="dbe5f-151">Alternatif resimleri</span><span class="sxs-lookup"><span data-stu-id="dbe5f-151">Alternative images</span></span>

<span data-ttu-id="dbe5f-152">Geliştirme, derleme ve üretim en iyi duruma getirilmiş senaryoların yanı sıra ek görüntüleri sağlıyoruz:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="dbe5f-153">`microsoft/dotnet:<version>-runtime-deps`: **Çalışma zamanı deps** görüntü, tüm yerel .NET Core tarafından gerekli bağımlılıkları ile işletim sistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="dbe5f-154">Bu görüntü içindir [kendi içindeki uygulamaları](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="dbe5f-154">This image is for [self-contained applications](../deploying/index.md).</span></span>

<span data-ttu-id="dbe5f-155">Her değişken en son sürümleri:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="dbe5f-156">`microsoft/dotnet` veya `microsoft/dotnet:latest` (diğer ad SDK görüntü için)</span><span class="sxs-lookup"><span data-stu-id="dbe5f-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="dbe5f-157">Araştırılacak örnekleri</span><span class="sxs-lookup"><span data-stu-id="dbe5f-157">Samples to explore</span></span>

* <span data-ttu-id="dbe5f-158">[Bu ASP.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) Docker görüntüleri için ASP.NET Core için üretim uygulamaları oluşturmaya yönelik en iyi uygulama desenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="dbe5f-159">Örnek, hem Linux hem de Windows kapsayıcıları ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="dbe5f-160">Bu .NET Core Docker örnek bir en iyi uygulama desenini gösterir [üretim için .NET Core uygulamaları için Docker görüntülerinizi oluşturmak.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span><span class="sxs-lookup"><span data-stu-id="dbe5f-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span></span>

## <a name="forward-the-request-scheme-and-original-ip-address"></a><span data-ttu-id="dbe5f-161">İstek düzeni ve özgün IP iletme</span><span class="sxs-lookup"><span data-stu-id="dbe5f-161">Forward the request scheme and original IP address</span></span>

<span data-ttu-id="dbe5f-162">Proxy sunucuları, yük Dengeleyiciler ve diğer ağ Gereçleri, bir istek hakkındaki bilgiler genellikle kapsayıcılı uygulama ulaşmadan önce gizlememeniz:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-162">Proxy servers, load balancers, and other network appliances often obscure information about a request before it reaches the containerized app:</span></span>

* <span data-ttu-id="dbe5f-163">HTTPS isteklerini HTTP üzerinden taşınır, özgün şeması (HTTPS) kaybolur ve bir üst bilgisinde iletilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-163">When HTTPS requests are proxied over HTTP, the original scheme (HTTPS) is lost and must be forwarded in a header.</span></span>
* <span data-ttu-id="dbe5f-164">Uygulama proxy'si ve doğru kaynağına değil Internet veya kurumsal ağ üzerindeki bir istek aldığından, özgün istemci IP adresi de üst bilgisinde gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-164">Because an app receives a request from the proxy and not its true source on the Internet or corporate network, the original client IP address must also be forwarded in a header.</span></span>

<span data-ttu-id="dbe5f-165">Bu bilgiler, örneğin yeniden yönlendirmeleri, kimlik doğrulaması, bağlama oluşturmayı, ilke değerlendirmesi ve istemci coğrafi konum isteği işleme önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-165">This information may be important in request processing, for example in redirects, authentication, link generation, policy evaluation, and client geolocation.</span></span>

<span data-ttu-id="dbe5f-166">Şema ve kapsayıcılı bir ASP.NET Core uygulaması orijinal IP adresine iletmek için iletilen üstbilgileri ara yazılımı kullanın.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-166">To forward the scheme and original IP address to a containerized ASP.NET Core app, use Forwarded Headers Middleware.</span></span> <span data-ttu-id="dbe5f-167">Daha fazla bilgi için [proxy sunucuları ile çalışma ve yük Dengeleyiciler için ASP.NET Core yapılandırma](/aspnet/core/host-and-deploy/proxy-load-balancer).</span><span class="sxs-lookup"><span data-stu-id="dbe5f-167">For more information, see [Configure ASP.NET Core to work with proxy servers and load balancers](/aspnet/core/host-and-deploy/proxy-load-balancer).</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="dbe5f-168">İlk ASP.NET Core Docker uygulamanızı</span><span class="sxs-lookup"><span data-stu-id="dbe5f-168">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="dbe5f-169">Bu öğretici için docker kapsayıcılarında çalıştırın istiyoruz uygulama için bir ASP.NET Core Docker örnek uygulama kullanma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-169">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="dbe5f-170">Bu ASP.NET Core Docker örnek uygulama, Docker görüntüleri için ASP.NET Core için üretim uygulamaları oluşturmaya yönelik en iyi bir uygulama desenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-170">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="dbe5f-171">Örnek, hem Linux hem de Windows kapsayıcıları ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-171">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="dbe5f-172">Örnek Dockerfile, ASP.NET Core çalışma zamanı Docker temel görüntüsünde alanlarını temel alan bir ASP.NET Core uygulamasını Docker görüntü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-172">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="dbe5f-173">Kullandığı [Docker çok aşamalı yapı özelliği](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) için:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-173">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="dbe5f-174">temel bir kapsayıcıda örneği oluşturmak **büyük** ASP.NET Core derleme Docker temel görüntüsünde</span><span class="sxs-lookup"><span data-stu-id="dbe5f-174">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="dbe5f-175">temel bir Docker görüntüsü son yapı sonucu kopyalar **daha küçük** ASP.NET Core Docker çalışma zamanı temel görüntü</span><span class="sxs-lookup"><span data-stu-id="dbe5f-175">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="dbe5f-176">Derleme görüntü, çalışma zamanı yansıma çalışmazken uygulamaları geliştirmek için gerekli araçları içerir.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-176">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="dbe5f-177">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="dbe5f-177">Prerequisites</span></span>

<span data-ttu-id="dbe5f-178">Derlemek ve çalıştırmak için aşağıdakileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-178">To build and run, install the following items:</span></span>

#### <a name="net-core-21-sdk"></a><span data-ttu-id="dbe5f-179">.NET core 2.1 SDK'sı</span><span class="sxs-lookup"><span data-stu-id="dbe5f-179">.NET Core 2.1 SDK</span></span>

* <span data-ttu-id="dbe5f-180">Yükleme [.NET Core SDK'sını 2.1](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="dbe5f-180">Install [.NET Core 2.1 SDK](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="dbe5f-181">Henüz yapmadıysanız, sık kullandığınız kod düzenleyicinize yükleyin.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-181">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="dbe5f-182">Bir kod Düzenleyicisi'ni yüklemeniz gerekir?</span><span class="sxs-lookup"><span data-stu-id="dbe5f-182">Need to install a code editor?</span></span> <span data-ttu-id="dbe5f-183">Deneyin [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="dbe5f-183">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="dbe5f-184">Docker istemcisi yükleme</span><span class="sxs-lookup"><span data-stu-id="dbe5f-184">Installing Docker Client</span></span>

<span data-ttu-id="dbe5f-185">Yükleme [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-185">Install [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="dbe5f-186">Docker istemcisi yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-186">The Docker client can be installed in:</span></span>

* <span data-ttu-id="dbe5f-187">Linux dağıtımları</span><span class="sxs-lookup"><span data-stu-id="dbe5f-187">Linux distributions</span></span>

   * [<span data-ttu-id="dbe5f-188">CentOS</span><span class="sxs-lookup"><span data-stu-id="dbe5f-188">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [<span data-ttu-id="dbe5f-189">Debian</span><span class="sxs-lookup"><span data-stu-id="dbe5f-189">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [<span data-ttu-id="dbe5f-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="dbe5f-190">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [<span data-ttu-id="dbe5f-191">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dbe5f-191">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="dbe5f-192">macOS</span><span class="sxs-lookup"><span data-stu-id="dbe5f-192">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="dbe5f-193">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="dbe5f-193">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="dbe5f-194">Örnek deposu için Git yükleme</span><span class="sxs-lookup"><span data-stu-id="dbe5f-194">Installing Git for sample repository</span></span>

* <span data-ttu-id="dbe5f-195">Yükleme [git](https://git-scm.com/download) depoyu kopyalamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-195">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="dbe5f-196">Örnek uygulamayı alma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-196">Getting the sample application</span></span>

<span data-ttu-id="dbe5f-197">Kopyalayarak örnek almak için en kolay yolu olan [.NET Core Docker deposunda](https://github.com/dotnet/dotnet-docker) git ile aşağıdaki yönergeleri kullanarak:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-197">The easiest way to get the sample is by cloning the [.NET Core Docker repository](https://github.com/dotnet/dotnet-docker) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker
```

<span data-ttu-id="dbe5f-198">(Küçük) depo, .NET Core Docker depodan bir zip olarak da indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-198">You can also download the repository (it is small) as a zip from the .NET Core Docker repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="dbe5f-199">ASP.NET uygulamasını yerel olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-199">Run the ASP.NET app locally</span></span>

<span data-ttu-id="dbe5f-200">Biz uygulamayı kapsayıcılı hale getirme önce bir başvuru noktası için öncelikle uygulamayı yerel olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-200">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="dbe5f-201">Derleme ve uygulamayı yerel olarak .NET Core 2.1 (depo kökünde yönergeleri olduğunu varsayın) aşağıdaki komutları kullanarak SDK ile çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-201">You can build and run the application locally with the .NET Core 2.1 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

<span data-ttu-id="dbe5f-202">Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-202">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="dbe5f-203">Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-203">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="dbe5f-204">Derleme ve Docker (depo kökünde yönergeleri olduğunu varsayın) aşağıdaki komutları kullanarak Linux kapsayıcıları kullanarak örneği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-204">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="dbe5f-205">`docker run` '-P' bağımsız değişkeni haritalar 5000 kapsayıcının 80 numaralı bağlantı noktasına yerel makinenizde bağlantı noktası (bağlantı noktası eşleme formu `host:container`).</span><span class="sxs-lookup"><span data-stu-id="dbe5f-205">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="dbe5f-206">Daha fazla bilgi için [docker run](https://docs.docker.com/engine/reference/commandline/exec/) başvuru komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-206">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="dbe5f-207">Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-207">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="dbe5f-208">Derleme ve örnek için Docker Windows kapsayıcıları ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-208">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="dbe5f-209">Derleme ve Docker (depo kökünde yönergeleri olduğunu varsayın) aşağıdaki komutları kullanarak Windows kapsayıcıları kullanarak örneği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-209">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="dbe5f-210">İçin gezinmesi gereken **kapsayıcı IP adresi** (başlangıcı yerine sonundan `http://localhost`) doğrudan tarayıcınızda Windows kapsayıcıları kullanırken.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-210">You must navigate to the **container IP address** (as opposed to `http://localhost`) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="dbe5f-211">Aşağıdaki adımlarla kapsayıcınızı IP adresini alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-211">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="dbe5f-212">Başka bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-212">Open up another command prompt.</span></span>
* <span data-ttu-id="dbe5f-213">Çalıştırma `docker ps` , çalışan kapsayıcıları görmek için.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-213">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="dbe5f-214">"Aspnetcore_sample" kapsayıcı olması.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-214">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="dbe5f-215">`docker exec aspnetcore_sample ipconfig`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-215">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="dbe5f-216">Kapsayıcı IP adresini kopyalayıp tarayıcınıza (örneğin, 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="dbe5f-216">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="dbe5f-217">Docker exec adı ya da karma değeri ile tanımlama kapsayıcıları destekler.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-217">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="dbe5f-218">Bizim örneğimizde (aspnetcore_sample) adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-218">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="dbe5f-219">Çalışan bir Windows kapsayıcısına IP adresini alma, aşağıdaki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-219">See the following example of how to get the IP address of a running Windows container.</span></span>

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
> <span data-ttu-id="dbe5f-220">Docker exec çalışan bir kapsayıcıda yeni bir komut çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-220">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="dbe5f-221">Daha fazla bilgi için [docker exec başvuru](https://docs.docker.com/engine/reference/commandline/exec/) komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-221">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="dbe5f-222">Yerel olarak kullanarak üretime dağıtmaya hazır bir uygulama oluşturabilir [dotnet yayımlama](../tools/dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-222">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> <span data-ttu-id="dbe5f-223">- C sürüm bağımsız uygulamayı (hata ayıklama modu varsayılandır) yayın modunda oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-223">The -c Release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="dbe5f-224">Daha fazla bilgi için [dotnet çalıştırma başvuru](../tools/dotnet-run.md) komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-224">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="dbe5f-225">Uygulamayı çalıştırmak **Windows** aşağıdaki komutu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-225">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="dbe5f-226">Uygulamayı çalıştırmak **Linux** veya **macOS** aşağıdaki komutu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-226">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="dbe5f-227">Bu örnekte kullanılan docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="dbe5f-227">Docker Images used in this sample</span></span>

<span data-ttu-id="dbe5f-228">Bu örnek 's dockerfile içinde aşağıdaki Docker görüntüleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-228">The following Docker images are used in this sample's dockerfile.</span></span>

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

<span data-ttu-id="dbe5f-229">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="dbe5f-229">Congratulations!</span></span> <span data-ttu-id="dbe5f-230">yalnızca gerekir:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-230">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="dbe5f-231">Microsoft .NET Core Docker görüntüleri hakkında bilgi edindiniz</span><span class="sxs-lookup"><span data-stu-id="dbe5f-231">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="dbe5f-232">Bir ASP.NET Core Dockerize örnek uygulaması alındı</span><span class="sxs-lookup"><span data-stu-id="dbe5f-232">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="dbe5f-233">Örnek ASP.NET uygulamasını yerel olarak çalıştı</span><span class="sxs-lookup"><span data-stu-id="dbe5f-233">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="dbe5f-234">Yerleşik ve örnek Linux kapsayıcıları için Docker ile çalıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-234">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="dbe5f-235">Yerleşik ve örnek için Docker Windows kapsayıcıları ile çalıştırıldı</span><span class="sxs-lookup"><span data-stu-id="dbe5f-235">Built and ran the sample with Docker for Windows containers</span></span>

<span data-ttu-id="dbe5f-236">**Sonraki adımlar**</span><span class="sxs-lookup"><span data-stu-id="dbe5f-236">**Next Steps**</span></span>

<span data-ttu-id="dbe5f-237">Gerçekleştirebileceğiniz bazı sonraki adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-237">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="dbe5f-238">Visual Studio Docker araçları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-238">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="dbe5f-239">Docker görüntülerini Azure Container registry'den Azure Container ınstances'a dağıtma</span><span class="sxs-lookup"><span data-stu-id="dbe5f-239">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="dbe5f-240">Visual Studio kodu ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="dbe5f-240">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="dbe5f-241">Bire bir Visual Studio ile Mac, kapsayıcılar ve sunucusuz kod için bulutta hakkında edinme</span><span class="sxs-lookup"><span data-stu-id="dbe5f-241">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="dbe5f-242">Mac Laboratuvar için Docker ve Visual Studio ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="dbe5f-242">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> <span data-ttu-id="dbe5f-243">Azure aboneliğiniz yoksa [hemen kaydolun](https://azure.microsoft.com/free/?b=16.48) 30 günlük ücretsiz hesabı ve get 200 ABD Doları değerinde Azure kredisi, out Azure Hizmetleri, herhangi bir birleşimini denemek için.</span><span class="sxs-lookup"><span data-stu-id="dbe5f-243">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
