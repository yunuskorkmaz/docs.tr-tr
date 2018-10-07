---
title: .NET Core, Docker görüntüleri oluşturma
description: Docker görüntülerini ve .NET Core anlama
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 675b6821588f8d0dd9495346a13665a32986f060
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841170"
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="30d6b-103">.NET Core uygulamaları için Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="30d6b-103">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="30d6b-104">Bu öğreticide, .NET Core üzerinde Docker nasıl odaklanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="30d6b-104">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="30d6b-105">İlk olarak sunulur ve Microsoft ve kullanım örnekleri tarafından tutulan farklı bir Docker görüntüleri keşfedin.</span><span class="sxs-lookup"><span data-stu-id="30d6b-105">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="30d6b-106">Biz, daha sonra nasıl oluşturacağınızı ve ASP.NET Core uygulaması docker kapsayıcılarında çalıştırın öğrenin.</span><span class="sxs-lookup"><span data-stu-id="30d6b-106">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="30d6b-107">Bu öğreticinin Kurs sırasında şunları öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30d6b-107">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="30d6b-108">Microsoft .NET Core Docker görüntüleri hakkında bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="30d6b-108">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="30d6b-109">Bir ASP.NET Core Dockerize örnek uygulaması alma</span><span class="sxs-lookup"><span data-stu-id="30d6b-109">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="30d6b-110">ASP.NET örnek uygulamayı yerel olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="30d6b-110">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="30d6b-111">Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="30d6b-111">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="30d6b-112">Derleme ve örnek için Docker Windows kapsayıcıları ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="30d6b-112">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="30d6b-113">Docker görüntüsünü en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="30d6b-113">Docker Image Optimizations</span></span>

<span data-ttu-id="30d6b-114">Geliştiriciler için Docker görüntülerini oluştururken, biz üç ana senaryo üzerinde odaklanır:</span><span class="sxs-lookup"><span data-stu-id="30d6b-114">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="30d6b-115">.NET Core uygulamaları geliştirmek için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="30d6b-115">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="30d6b-116">.NET Core uygulamaları oluşturmak için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="30d6b-116">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="30d6b-117">.NET Core uygulamaları çalıştırmak için kullanılan görüntü</span><span class="sxs-lookup"><span data-stu-id="30d6b-117">Images used to run .NET Core apps</span></span>

<span data-ttu-id="30d6b-118">Neden üç görüntüleri?</span><span class="sxs-lookup"><span data-stu-id="30d6b-118">Why three images?</span></span>
<span data-ttu-id="30d6b-119">Geliştirme, derleme ve kapsayıcılı uygulamalar çalıştırmak, farklı önceliklere sahibiz.</span><span class="sxs-lookup"><span data-stu-id="30d6b-119">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="30d6b-120">**Geliştirme:** öncelik odaklanır değişiklikleri ve değişiklikleri hata ayıklama özelliği hızla yineleyin.</span><span class="sxs-lookup"><span data-stu-id="30d6b-120">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="30d6b-121">Resmin boyutu önemli değildir, bunun yerine, değişiklikler kodunuza yapabilir ve bunları hızlıca görmek?</span><span class="sxs-lookup"><span data-stu-id="30d6b-121">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="30d6b-122">**Derleme:** bu görüntü derleyici ve ikili dosyaları iyileştirmek için diğer herhangi bir bağımlılığın içeren uygulamanızı derlemek için gereken her şeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-122">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="30d6b-123">Derleme görüntüyü bir üretim görüntüsüne yerleştirdiğiniz varlıkları oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="30d6b-123">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="30d6b-124">Derleme görüntüsünü veya bir yapı ortamı sürekli tümleştirme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-124">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="30d6b-125">Bu yaklaşım, derlemek ve bir yapı görüntü örneği (tüm gerekli bağımlılıkları olan) uygulamasında oluşturmak bir yapı aracısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="30d6b-125">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="30d6b-126">Yapı aracınız, yalnızca bu Docker görüntüsünü çalıştırma bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-126">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="30d6b-127">**Üretim:** dağıtma ve görüntü Başlat ne kadar hızlı?</span><span class="sxs-lookup"><span data-stu-id="30d6b-127">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="30d6b-128">Bu görüntü, Docker kayıt defterinizin Docker konaklarınız için ağ performansı en iyi duruma getirilmiş şekilde küçüktür.</span><span class="sxs-lookup"><span data-stu-id="30d6b-128">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="30d6b-129">İçeriği, Docker run sonuçları işlemek için hızlı süreye etkinleştirme çalıştırmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="30d6b-129">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="30d6b-130">Dinamik kod derlemesi, Docker modelde gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="30d6b-130">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="30d6b-131">Bu görüntüde yerleştirdiğiniz içeriği ikili dosyaları ve uygulamayı çalıştırmak için gerekli içeriklere sınırlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-131">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="30d6b-132">Örneğin, `dotnet publish` çıktı içerir:</span><span class="sxs-lookup"><span data-stu-id="30d6b-132">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="30d6b-133">derlenmiş ikili dosyaları</span><span class="sxs-lookup"><span data-stu-id="30d6b-133">the compiled binaries</span></span>
    * <span data-ttu-id="30d6b-134">.js ve .css dosyaları</span><span class="sxs-lookup"><span data-stu-id="30d6b-134">.js and .css files</span></span>


<span data-ttu-id="30d6b-135">Eklenecek nedeni `dotnet publish` üretim görüntünüzü komut çıktısında boyutuna dürüst etmektir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-135">The reason to include the `dotnet publish` command output in your production image is to keep its size to a minimum.</span></span>

<span data-ttu-id="30d6b-136">Bazı .NET Core görüntüleri Katmanlar oldukça basit bir işlem en son etiket indiriliyor, bu nedenle farklı etiketler arasında paylaşın.</span><span class="sxs-lookup"><span data-stu-id="30d6b-136">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="30d6b-137">Makinenizde zaten daha eski bir sürümü varsa, bu mimaride gerekli disk alanını azaltır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-137">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="30d6b-138">Birden çok uygulama aynı makinede genel görüntülerden kullandığınızda, bellek ortak görüntülerin arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-138">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="30d6b-139">Görüntüleri paylaşılması için aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-139">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="30d6b-140">Docker görüntüsü farklılıkları</span><span class="sxs-lookup"><span data-stu-id="30d6b-140">Docker image variations</span></span>

<span data-ttu-id="30d6b-141">Görüntü çeşitleri altında sağladığımız yukarıdaki hedeflere ulaşmak için [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="30d6b-141">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="30d6b-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Bu görüntü .NET Core ve komut satırı araçları'nı (CLI) içerir .NET Core SDK'sı içerir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="30d6b-143">Bu görüntü eşlendiği **geliştirme senaryosu**.</span><span class="sxs-lookup"><span data-stu-id="30d6b-143">This image maps to the **development scenario**.</span></span> <span data-ttu-id="30d6b-144">Bu görüntü, yerel geliştirme, hata ayıklama ve birim testi için kullanın.</span><span class="sxs-lookup"><span data-stu-id="30d6b-144">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="30d6b-145">Bu görüntü için de kullanılabilir, **derleme** senaryoları.</span><span class="sxs-lookup"><span data-stu-id="30d6b-145">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="30d6b-146">Kullanarak `microsoft/dotnet:sdk` , en son sürümü her zaman verir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-146">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="30d6b-147">Gereksinimlerinizi hakkında konusunda emin değilseniz, kullanmak istediğiniz `microsoft/dotnet:<version>-sdk` görüntü.</span><span class="sxs-lookup"><span data-stu-id="30d6b-147">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="30d6b-148">"Pratikte" görüntü olarak throw kullanılmak üzere tasarlanmıştır koyma kapsayıcı (kaynak kodunuzu bağlayın ve uygulamanızı başlatmak için bir kapsayıcı başlatma) ve diğer görüntüleri oluşturmak için temel görüntü olarak.</span><span class="sxs-lookup"><span data-stu-id="30d6b-148">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="30d6b-149">`microsoft/dotnet:<version>-runtime`: Bu görüntü, .NET Core (çalışma zamanı ve kitaplıklarda) içerir ve .NET Core uygulamaları çalıştırma için optimize edilmiştir **üretim**.</span><span class="sxs-lookup"><span data-stu-id="30d6b-149">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="30d6b-150">Alternatif resimleri</span><span class="sxs-lookup"><span data-stu-id="30d6b-150">Alternative images</span></span>

<span data-ttu-id="30d6b-151">Geliştirme, derleme ve üretim en iyi duruma getirilmiş senaryoların yanı sıra ek görüntüleri sağlıyoruz:</span><span class="sxs-lookup"><span data-stu-id="30d6b-151">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="30d6b-152">`microsoft/dotnet:<version>-runtime-deps`**Çalışma zamanı deps** görüntü, tüm yerel .NET Core tarafından gerekli bağımlılıkları ile işletim sistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-152">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="30d6b-153">Bu görüntü içindir [kendi içindeki uygulamaları](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="30d6b-153">This image is for [self-contained applications](../deploying/index.md).</span></span>

<span data-ttu-id="30d6b-154">Her değişken en son sürümleri:</span><span class="sxs-lookup"><span data-stu-id="30d6b-154">Latest versions of each variant:</span></span>

* <span data-ttu-id="30d6b-155">`microsoft/dotnet` veya `microsoft/dotnet:latest` (diğer ad SDK görüntü için)</span><span class="sxs-lookup"><span data-stu-id="30d6b-155">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="30d6b-156">Araştırılacak örnekleri</span><span class="sxs-lookup"><span data-stu-id="30d6b-156">Samples to explore</span></span>

* <span data-ttu-id="30d6b-157">[Bu ASP.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) Docker görüntüleri için ASP.NET Core için üretim uygulamaları oluşturmaya yönelik en iyi uygulama desenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-157">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="30d6b-158">Örnek, hem Linux hem de Windows kapsayıcıları ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-158">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="30d6b-159">Bu .NET Core Docker örnek bir en iyi uygulama desenini gösterir [üretim için .NET Core uygulamaları için Docker görüntülerinizi oluşturmak.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span><span class="sxs-lookup"><span data-stu-id="30d6b-159">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span></span>

## <a name="forward-the-request-scheme-and-original-ip-address"></a><span data-ttu-id="30d6b-160">İstek düzeni ve özgün IP iletme</span><span class="sxs-lookup"><span data-stu-id="30d6b-160">Forward the request scheme and original IP address</span></span>

<span data-ttu-id="30d6b-161">Proxy sunucuları, yük Dengeleyiciler ve diğer ağ Gereçleri, bir istek hakkındaki bilgiler genellikle kapsayıcılı uygulama ulaşmadan önce gizlememeniz:</span><span class="sxs-lookup"><span data-stu-id="30d6b-161">Proxy servers, load balancers, and other network appliances often obscure information about a request before it reaches the containerized app:</span></span>

* <span data-ttu-id="30d6b-162">HTTPS isteklerini HTTP üzerinden taşınır, özgün şeması (HTTPS) kaybolur ve bir üst bilgisinde iletilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-162">When HTTPS requests are proxied over HTTP, the original scheme (HTTPS) is lost and must be forwarded in a header.</span></span>
* <span data-ttu-id="30d6b-163">Uygulama proxy'si ve doğru kaynağına değil Internet veya kurumsal ağ üzerindeki bir istek aldığından, özgün istemci IP adresi de üst bilgisinde gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-163">Because an app receives a request from the proxy and not its true source on the Internet or corporate network, the original client IP address must also be forwarded in a header.</span></span>

<span data-ttu-id="30d6b-164">Bu bilgiler, örneğin yeniden yönlendirmeleri, kimlik doğrulaması, bağlama oluşturmayı, ilke değerlendirmesi ve istemci coğrafi konum isteği işleme önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-164">This information may be important in request processing, for example in redirects, authentication, link generation, policy evaluation, and client geolocation.</span></span>

<span data-ttu-id="30d6b-165">Şema ve kapsayıcılı bir ASP.NET Core uygulaması orijinal IP adresine iletmek için iletilen üstbilgileri ara yazılımı kullanın.</span><span class="sxs-lookup"><span data-stu-id="30d6b-165">To forward the scheme and original IP address to a containerized ASP.NET Core app, use Forwarded Headers Middleware.</span></span> <span data-ttu-id="30d6b-166">Daha fazla bilgi için [proxy sunucuları ile çalışma ve yük Dengeleyiciler için ASP.NET Core yapılandırma](/aspnet/core/host-and-deploy/proxy-load-balancer).</span><span class="sxs-lookup"><span data-stu-id="30d6b-166">For more information, see [Configure ASP.NET Core to work with proxy servers and load balancers](/aspnet/core/host-and-deploy/proxy-load-balancer).</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="30d6b-167">İlk ASP.NET Core Docker uygulamanızı</span><span class="sxs-lookup"><span data-stu-id="30d6b-167">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="30d6b-168">Bu öğretici için docker kapsayıcılarında çalıştırın istiyoruz uygulama için bir ASP.NET Core Docker örnek uygulama kullanma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-168">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="30d6b-169">Bu ASP.NET Core Docker örnek uygulama, Docker görüntüleri için ASP.NET Core için üretim uygulamaları oluşturmaya yönelik en iyi bir uygulama desenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-169">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="30d6b-170">Örnek, hem Linux hem de Windows kapsayıcıları ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-170">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="30d6b-171">Örnek Dockerfile, ASP.NET Core çalışma zamanı Docker temel görüntüsünde alanlarını temel alan bir ASP.NET Core uygulamasını Docker görüntü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30d6b-171">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="30d6b-172">Kullandığı [Docker çok aşamalı yapı özelliği](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) için:</span><span class="sxs-lookup"><span data-stu-id="30d6b-172">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="30d6b-173">temel bir kapsayıcıda örneği oluşturmak **büyük** ASP.NET Core derleme Docker temel görüntüsünde</span><span class="sxs-lookup"><span data-stu-id="30d6b-173">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="30d6b-174">temel bir Docker görüntüsü son yapı sonucu kopyalar **daha küçük** ASP.NET Core Docker çalışma zamanı temel görüntü</span><span class="sxs-lookup"><span data-stu-id="30d6b-174">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="30d6b-175">Derleme görüntü, çalışma zamanı yansıma çalışmazken uygulamaları geliştirmek için gerekli araçları içerir.</span><span class="sxs-lookup"><span data-stu-id="30d6b-175">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="30d6b-176">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="30d6b-176">Prerequisites</span></span>

<span data-ttu-id="30d6b-177">Derlemek ve çalıştırmak için aşağıdakileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="30d6b-177">To build and run, install the following items:</span></span>

#### <a name="net-core-21-sdk"></a><span data-ttu-id="30d6b-178">.NET core 2.1 SDK'sı</span><span class="sxs-lookup"><span data-stu-id="30d6b-178">.NET Core 2.1 SDK</span></span>

* <span data-ttu-id="30d6b-179">Yükleme [.NET Core SDK'sını 2.1](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="30d6b-179">Install [.NET Core SDK 2.1](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="30d6b-180">Henüz yapmadıysanız, sık kullandığınız kod düzenleyicinize yükleyin.</span><span class="sxs-lookup"><span data-stu-id="30d6b-180">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="30d6b-181">Bir kod Düzenleyicisi'ni yüklemeniz gerekir?</span><span class="sxs-lookup"><span data-stu-id="30d6b-181">Need to install a code editor?</span></span> <span data-ttu-id="30d6b-182">Deneyin [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="30d6b-182">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="30d6b-183">Docker istemcisi yükleme</span><span class="sxs-lookup"><span data-stu-id="30d6b-183">Installing Docker Client</span></span>

<span data-ttu-id="30d6b-184">Yükleme [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="30d6b-184">Install [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="30d6b-185">Docker istemcisi yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="30d6b-185">The Docker client can be installed in:</span></span>

* <span data-ttu-id="30d6b-186">Linux dağıtımları</span><span class="sxs-lookup"><span data-stu-id="30d6b-186">Linux distributions</span></span>

   * [<span data-ttu-id="30d6b-187">CentOS</span><span class="sxs-lookup"><span data-stu-id="30d6b-187">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [<span data-ttu-id="30d6b-188">Debian</span><span class="sxs-lookup"><span data-stu-id="30d6b-188">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [<span data-ttu-id="30d6b-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="30d6b-189">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [<span data-ttu-id="30d6b-190">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="30d6b-190">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="30d6b-191">macOS</span><span class="sxs-lookup"><span data-stu-id="30d6b-191">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="30d6b-192">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="30d6b-192">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="30d6b-193">Örnek deposu için Git yükleme</span><span class="sxs-lookup"><span data-stu-id="30d6b-193">Installing Git for sample repository</span></span>

* <span data-ttu-id="30d6b-194">Yükleme [git](https://git-scm.com/download) depoyu kopyalamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="30d6b-194">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="30d6b-195">Örnek uygulamayı alma</span><span class="sxs-lookup"><span data-stu-id="30d6b-195">Getting the sample application</span></span>

<span data-ttu-id="30d6b-196">Kopyalayarak örnek almak için en kolay yolu olan [.NET Core Docker deposunda](https://github.com/dotnet/dotnet-docker) git ile aşağıdaki yönergeleri kullanarak:</span><span class="sxs-lookup"><span data-stu-id="30d6b-196">The easiest way to get the sample is by cloning the [.NET Core Docker repository](https://github.com/dotnet/dotnet-docker) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker
```

<span data-ttu-id="30d6b-197">(Küçük) depo, .NET Core Docker depodan bir zip olarak da indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30d6b-197">You can also download the repository (it is small) as a zip from the .NET Core Docker repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="30d6b-198">ASP.NET uygulamasını yerel olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="30d6b-198">Run the ASP.NET app locally</span></span>

<span data-ttu-id="30d6b-199">Biz uygulamayı kapsayıcılı hale getirme önce bir başvuru noktası için öncelikle uygulamayı yerel olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="30d6b-199">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="30d6b-200">Derleme ve uygulamayı yerel olarak .NET Core 2.1 (depo kökünde yönergeleri olduğunu varsayın) aşağıdaki komutları kullanarak SDK ile çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="30d6b-200">You can build and run the application locally with the .NET Core 2.1 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

<span data-ttu-id="30d6b-201">Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.</span><span class="sxs-lookup"><span data-stu-id="30d6b-201">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="30d6b-202">Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="30d6b-202">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="30d6b-203">Derleme ve Docker (depo kökünde yönergeleri olduğunu varsayın) aşağıdaki komutları kullanarak Linux kapsayıcıları kullanarak örneği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="30d6b-203">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="30d6b-204">`docker run` '-P' bağımsız değişkeni haritalar 5000 kapsayıcının 80 numaralı bağlantı noktasına yerel makinenizde bağlantı noktası (bağlantı noktası eşleme formu `host:container`).</span><span class="sxs-lookup"><span data-stu-id="30d6b-204">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="30d6b-205">Daha fazla bilgi için [docker run](https://docs.docker.com/engine/reference/commandline/exec/) başvuru komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="30d6b-205">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="30d6b-206">Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.</span><span class="sxs-lookup"><span data-stu-id="30d6b-206">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="30d6b-207">Derleme ve örnek için Docker Windows kapsayıcıları ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="30d6b-207">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="30d6b-208">Derleme ve Docker (depo kökünde yönergeleri olduğunu varsayın) aşağıdaki komutları kullanarak Windows kapsayıcıları kullanarak örneği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="30d6b-208">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="30d6b-209">İçin gezinmesi gereken **kapsayıcı IP adresi** (başlangıcı yerine sonundan `http://localhost`) doğrudan tarayıcınızda Windows kapsayıcıları kullanırken.</span><span class="sxs-lookup"><span data-stu-id="30d6b-209">You must navigate to the **container IP address** (as opposed to `http://localhost`) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="30d6b-210">Aşağıdaki adımlarla kapsayıcınızı IP adresini alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30d6b-210">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="30d6b-211">Başka bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="30d6b-211">Open up another command prompt.</span></span>
* <span data-ttu-id="30d6b-212">Çalıştırma `docker ps` , çalışan kapsayıcıları görmek için.</span><span class="sxs-lookup"><span data-stu-id="30d6b-212">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="30d6b-213">"Aspnetcore_sample" kapsayıcı olması.</span><span class="sxs-lookup"><span data-stu-id="30d6b-213">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="30d6b-214">Çalıştırma `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="30d6b-214">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="30d6b-215">Kapsayıcı IP adresini kopyalayıp tarayıcınıza (örneğin, 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="30d6b-215">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="30d6b-216">Docker exec adı ya da karma değeri ile tanımlama kapsayıcıları destekler.</span><span class="sxs-lookup"><span data-stu-id="30d6b-216">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="30d6b-217">Bizim örneğimizde (aspnetcore_sample) adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-217">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="30d6b-218">Çalışan bir Windows kapsayıcısına IP adresini alma, aşağıdaki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="30d6b-218">See the following example of how to get the IP address of a running Windows container.</span></span>

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
> <span data-ttu-id="30d6b-219">Docker exec çalışan bir kapsayıcıda yeni bir komut çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-219">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="30d6b-220">Daha fazla bilgi için [docker exec başvuru](https://docs.docker.com/engine/reference/commandline/exec/) komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="30d6b-220">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="30d6b-221">Yerel olarak kullanarak üretime dağıtmaya hazır bir uygulama oluşturabilir [dotnet yayımlama](../tools/dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="30d6b-221">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> <span data-ttu-id="30d6b-222">- C sürüm bağımsız uygulamayı (hata ayıklama modu varsayılandır) yayın modunda oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30d6b-222">The -c Release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="30d6b-223">Daha fazla bilgi için [dotnet çalıştırma başvuru](../tools/dotnet-run.md) komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="30d6b-223">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="30d6b-224">Uygulamayı çalıştırmak **Windows** aşağıdaki komutu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="30d6b-224">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="30d6b-225">Uygulamayı çalıştırmak **Linux** veya **macOS** aşağıdaki komutu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="30d6b-225">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="30d6b-226">Bu örnekte kullanılan docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="30d6b-226">Docker Images used in this sample</span></span>

<span data-ttu-id="30d6b-227">Bu örnek 's dockerfile içinde aşağıdaki Docker görüntüleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30d6b-227">The following Docker images are used in this sample's dockerfile.</span></span>

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

<span data-ttu-id="30d6b-228">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="30d6b-228">Congratulations!</span></span> <span data-ttu-id="30d6b-229">yalnızca gerekir:</span><span class="sxs-lookup"><span data-stu-id="30d6b-229">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="30d6b-230">Microsoft .NET Core Docker görüntüleri hakkında bilgi edindiniz</span><span class="sxs-lookup"><span data-stu-id="30d6b-230">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="30d6b-231">Bir ASP.NET Core Dockerize örnek uygulaması alındı</span><span class="sxs-lookup"><span data-stu-id="30d6b-231">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="30d6b-232">Örnek ASP.NET uygulamasını yerel olarak çalıştı</span><span class="sxs-lookup"><span data-stu-id="30d6b-232">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="30d6b-233">Yerleşik ve örnek Linux kapsayıcıları için Docker ile çalıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="30d6b-233">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="30d6b-234">Yerleşik ve örnek için Docker Windows kapsayıcıları ile çalıştırıldı</span><span class="sxs-lookup"><span data-stu-id="30d6b-234">Built and ran the sample with Docker for Windows containers</span></span>

<span data-ttu-id="30d6b-235">**Sonraki adımlar**</span><span class="sxs-lookup"><span data-stu-id="30d6b-235">**Next Steps**</span></span>

<span data-ttu-id="30d6b-236">Gerçekleştirebileceğiniz bazı sonraki adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="30d6b-236">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="30d6b-237">Visual Studio Docker araçları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="30d6b-237">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="30d6b-238">Docker görüntülerini Azure Container registry'den Azure Container ınstances'a dağıtma</span><span class="sxs-lookup"><span data-stu-id="30d6b-238">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="30d6b-239">Visual Studio kodu ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="30d6b-239">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="30d6b-240">Bire bir Visual Studio ile Mac, kapsayıcılar ve sunucusuz kod için bulutta hakkında edinme</span><span class="sxs-lookup"><span data-stu-id="30d6b-240">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="30d6b-241">Mac Laboratuvar için Docker ve Visual Studio ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="30d6b-241">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> <span data-ttu-id="30d6b-242">Azure aboneliğiniz yoksa [hemen kaydolun](https://azure.microsoft.com/free/?b=16.48) 30 günlük ücretsiz hesabı ve get 200 ABD Doları değerinde Azure kredisi, out Azure Hizmetleri, herhangi bir birleşimini denemek için.</span><span class="sxs-lookup"><span data-stu-id="30d6b-242">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
