---
title: İzlenecek yollar ve teknik başlatılan özeti
description: Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize | izlenecek yollar ve teknik başlatılan özeti
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0bad7e3afbdf3e55c447319b3756f2235b9e0a19
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="14453-103">İzlenecek yollar ve teknik başlatılan özeti</span><span class="sxs-lookup"><span data-stu-id="14453-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="14453-104">Bu e-kitap boyutunu sınırlamak için ek teknik belgeler ve tam izlenecek yollar GitHub deposunda kullanılabilir yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="14453-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="14453-105">Bu bölümde açıklanan izlenecek yollar çevrimiçi bir dizi adım adım kurulum Windows kapsayıcıları ve Azure dağıtımına dayalı birden çok ortamlarının kapsar.</span><span class="sxs-lookup"><span data-stu-id="14453-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="14453-106">Aşağıdaki bölümlerde ne her gözden geçirme, hedefler ve üst düzey görme hakkında ve ilgili olan görevleri diyagramı sağlar açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="14453-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="14453-107">İzlenecek yollar kendilerini alabilirsiniz içinde *eShopModernizing* uygulamaları GitHub deposuna wiki adresindeki [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="14453-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="14453-108">Teknik kılavuz listesi</span><span class="sxs-lookup"><span data-stu-id="14453-108">Technical walkthrough list</span></span>

<span data-ttu-id="14453-109">Aşağıdaki get-started izlenecek kaldırın ve kapsayıcılar kullanarak kaydırma ve Azure içinde birden çok dağıtım seçenekleri kullanarak Taşı örnek uygulamaları için tutarlı ve kapsamlı teknik Kılavuzu sağlamak.</span><span class="sxs-lookup"><span data-stu-id="14453-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="14453-110">Her biri aşağıdaki izlenecek github'da kullanılabilir olan yeni örnek eShopLegacy ve eShopModernizing uygulamaları kullanır [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="14453-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="14453-111">**Elektronik Mağaza eski uygulamaları turu**</span><span class="sxs-lookup"><span data-stu-id="14453-111">**Tour of eShop legacy apps**</span></span>

- <span data-ttu-id="14453-112">**Var olan .NET uygulamalarınız Windows kapsayıcılarla containerize**</span><span class="sxs-lookup"><span data-stu-id="14453-112">**Containerize your existing .NET applications with Windows Containers**</span></span>

- <span data-ttu-id="14453-113">**Azure VM'ler kapsayıcıları tabanlı Windows uygulamanızı dağıtma**</span><span class="sxs-lookup"><span data-stu-id="14453-113">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="14453-114">**Azure kapsayıcı Hizmeti'nde Kubernetes Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma**</span><span class="sxs-lookup"><span data-stu-id="14453-114">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="14453-115">**Azure Service Fabric Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma**</span><span class="sxs-lookup"><span data-stu-id="14453-115">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="14453-116">Gözden geçirme 1: Elektronik Mağaza eski uygulamaları turu</span><span class="sxs-lookup"><span data-stu-id="14453-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14453-117">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="14453-117">Technical walkthrough availability</span></span>

<span data-ttu-id="14453-118">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="14453-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a><span data-ttu-id="14453-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="14453-119">Overview</span></span>

<span data-ttu-id="14453-120">Bu kılavuzda, iki örnek eski uygulamalar ilk uyarlamasını keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14453-120">In this walkthrough, you can explore the initial implementation of two sample legacy applications.</span></span> <span data-ttu-id="14453-121">Her iki örnek uygulamaları tek yapılı bir mimariye sahip ve klasik ASP.NET kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="14453-121">Both sample apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="14453-122">ASP.NET ile tabanlı bir uygulamayı 4.x MVC; İkinci uygulama ASP.NET 4.x Web Forms üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="14453-122">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="14453-123">Her iki uygulamada bulunan [eShopModernizing GitHub deposuna](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="14453-123">Both applications are in the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

<span data-ttu-id="14453-124">Her iki örnek uygulamaları containerize, benzer şekilde, Klasik containerize [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) bir masaüstü uygulaması olarak kullanılması (WCF) uygulama.</span><span class="sxs-lookup"><span data-stu-id="14453-124">You can containerize both sample apps, similar to the way you can containerize a classic [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) (WCF) application to be consumed as a desktop application.</span></span> <span data-ttu-id="14453-125">Bir örnek için bkz: [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span><span class="sxs-lookup"><span data-stu-id="14453-125">For an example, see [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span></span>

### <a name="goals"></a><span data-ttu-id="14453-126">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="14453-126">Goals</span></span>

<span data-ttu-id="14453-127">Asıl amacı, bu kılavuzda yalnızca bu uygulamalarla ve kendi kod ve yapılandırma hakkında bilgi edinmek için ' dir.</span><span class="sxs-lookup"><span data-stu-id="14453-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="14453-128">Böylece oluşturmak ve test amacıyla SQL veritabanı kullanmadan sahte veriler kullanmak uygulamaları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14453-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="14453-129">Bu isteğe bağlı yapılandırma bağımlılık ekleme, ayrılmış bir biçimde temel alır.</span><span class="sxs-lookup"><span data-stu-id="14453-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario"></a><span data-ttu-id="14453-130">Senaryo</span><span class="sxs-lookup"><span data-stu-id="14453-130">Scenario</span></span>

<span data-ttu-id="14453-131">Şekil 5-1 özgün eski uygulamaları basit bir senaryo gösterir.</span><span class="sxs-lookup"><span data-stu-id="14453-131">Figure 5-1 shows the simple scenario of the original legacy applications.</span></span>

> ![Basit mimarisi senaryo özgün eski uygulamalar](./media/image5-1.png)
>
> <span data-ttu-id="14453-133">**Şekil 5-1.**</span><span class="sxs-lookup"><span data-stu-id="14453-133">**Figure 5-1.**</span></span> <span data-ttu-id="14453-134">Basit mimarisi senaryo özgün eski uygulamalar</span><span class="sxs-lookup"><span data-stu-id="14453-134">Simple architecture scenario of the original legacy applications</span></span>

<span data-ttu-id="14453-135">Bir iş etki alanı açısından bakıldığında, hem uygulamalar aynı katalog yönetimi özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="14453-135">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="14453-136">Elektronik Mağaza Kurumsal ekibi üyelerinin uygulamayı görüntülemek ve ürün kataloğu düzenlemek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="14453-136">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> <span data-ttu-id="14453-137">Şekil 5-2 ilk uygulama ekran görüntüleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="14453-137">Figure 5-2 shows the initial app screenshots.</span></span>

![ASP.NET MVC ve ASP.NET Web Forms uygulamaları (varolan eski teknolojileri)](./media/image5-2.png)

> <span data-ttu-id="14453-139">**Şekil 5-2.**</span><span class="sxs-lookup"><span data-stu-id="14453-139">**Figure 5-2.**</span></span> <span data-ttu-id="14453-140">ASP.NET MVC ve ASP.NET Web Forms uygulamaları (varolan eski teknolojileri)</span><span class="sxs-lookup"><span data-stu-id="14453-140">ASP.NET MVC and ASP.NET Web Forms applications (existing/legacy technologies)</span></span>

<span data-ttu-id="14453-141">Gözat ve Katalog girişleri değiştirmek için kullanılan web uygulamaları şunlardır.</span><span class="sxs-lookup"><span data-stu-id="14453-141">These are web applications that are used to browse and modify catalog entries.</span></span> <span data-ttu-id="14453-142">Her iki uygulamalar aynı iş/işlevsel özellikleri sunmak olgu yalnızca karşılaştırma amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14453-142">The fact that both apps deliver the same business/functional features is simply for comparison purposes.</span></span> <span data-ttu-id="14453-143">ASP.NET MVC ve ASP.NET Web Forms çerçeveler kullanılarak oluşturulmuş olan uygulamalar için benzer bir modernization işlem görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14453-143">You can see a similar modernization process for apps that were created by using the ASP.NET MVC and ASP.NET Web Forms frameworks.</span></span>

<span data-ttu-id="14453-144">Bağımlılıklar ASP.NET 4.x veya önceki sürümleri (veya MVC için Web formları için) anlamına gelir kodu tam olarak ASP.NET Core MVC kullanarak yeniden yazılmıştır sürece bu uygulamaları .NET Core üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="14453-144">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> <span data-ttu-id="14453-145">Bu yeniden düzenlenmesine veya kodu yeniden istemediğiniz yaparsanız, mevcut uygulamaları containerize ve hala aynı .NET teknolojileri ve aynı kodu kullan olduğunu noktası gösterir.</span><span class="sxs-lookup"><span data-stu-id="14453-145">This demonstrates the point that if you don't want to re-architect or rewrite code, you can containerize existing applications, and still use the same .NET technologies and the same code.</span></span> <span data-ttu-id="14453-146">Bu eski kod için herhangi bir değişiklik yapılmadan kapsayıcılarında gibi uygulamaları nasıl çalıştırabileceğiniz görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14453-146">You can see how you can run applications like these in containers, without any changes to legacy code.</span></span>

### <a name="benefits"></a><span data-ttu-id="14453-147">Yararları</span><span class="sxs-lookup"><span data-stu-id="14453-147">Benefits</span></span>

<span data-ttu-id="14453-148">Bu kılavuzda yararları basit: yalnızca bağımlılık ekleme temel kod ve uygulama yapılandırma hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="14453-148">The benefits of this walkthrough are simple: Just get familiar with the code and application configuration, based on dependency injection.</span></span> <span data-ttu-id="14453-149">Ardından, containerize ve birden çok ortamlar için gelecekte dağıtırken Bu yaklaşımda deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14453-149">Then, you can experiment with this approach when you containerize and deploy to multiple environments in the future.</span></span>

### <a name="next-steps"></a><span data-ttu-id="14453-150">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="14453-150">Next steps</span></span>

<span data-ttu-id="14453-151">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="14453-151">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="14453-152">İzlenecek yol: 2: var olan .NET uygulamalarınız Windows kapsayıcılarla Containerize</span><span class="sxs-lookup"><span data-stu-id="14453-152">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14453-153">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="14453-153">Technical walkthrough availability</span></span>

<span data-ttu-id="14453-154">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="14453-154">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a><span data-ttu-id="14453-155">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="14453-155">Overview</span></span>

<span data-ttu-id="14453-156">MVC, Web Forms veya WCF, üretim, geliştirme ve test ortamları için temel gelenler varolan .NET uygulamalarının dağıtımını iyileştirmek için Windows kapsayıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="14453-156">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="14453-157">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="14453-157">Goals</span></span>

<span data-ttu-id="14453-158">Bu kılavuzun amacı, var olan bir .NET Framework uygulamasını containerizing için çeşitli seçenekler göstermektir.</span><span class="sxs-lookup"><span data-stu-id="14453-158">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="14453-159">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="14453-159">You can:</span></span>

- <span data-ttu-id="14453-160">Uygulamanızı kullanarak containerize [Docker için Visual Studio 2017 Araçları](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 veya sonraki sürümler).</span><span class="sxs-lookup"><span data-stu-id="14453-160">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="14453-161">El ile ekleyerek uygulamanızı containerize bir [Dockerfile](https://docs.docker.com/engine/reference/builder/)ve ardından kullanarak [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="14453-161">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="14453-162">Uygulamanızı kullanarak containerize [Img2Docker](https://github.com/docker/communitytools-image2docker-win) Aracı (Docker açık kaynak aracından).</span><span class="sxs-lookup"><span data-stu-id="14453-162">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="14453-163">Bu kılavuz Docker yaklaşım için Visual Studio 2017 araçları odaklanır, ancak diğer iki yaklaşım Dockerfiles kullanarak in regard to oldukça benzer.</span><span class="sxs-lookup"><span data-stu-id="14453-163">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario"></a><span data-ttu-id="14453-164">Senaryo</span><span class="sxs-lookup"><span data-stu-id="14453-164">Scenario</span></span>

<span data-ttu-id="14453-165">Şekil 5-3 kapsayıcılı Elektronik Mağaza eski uygulamaları senaryosu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="14453-165">Figure 5-3 shows the scenario for containerized eShop legacy applications.</span></span>

> ![Bir geliştirme ortamı kapsayıcılı uygulamalarda Basitleştirilmiş mimarisi diyagramı](./media/image5-3.png)
>
> <span data-ttu-id="14453-167">**Şekil 5-3.**</span><span class="sxs-lookup"><span data-stu-id="14453-167">**Figure 5-3.**</span></span> <span data-ttu-id="14453-168">Bir geliştirme ortamı kapsayıcılı uygulamalarda Basitleştirilmiş mimarisi diyagramı</span><span class="sxs-lookup"><span data-stu-id="14453-168">Simplified architecture diagram of containerized applications in a development environment</span></span>

### <a name="benefits"></a><span data-ttu-id="14453-169">Yararları</span><span class="sxs-lookup"><span data-stu-id="14453-169">Benefits</span></span>

<span data-ttu-id="14453-170">Bir kapsayıcıda tek yapılı uygulamanızı çalıştırmanın avantajı vardır.</span><span class="sxs-lookup"><span data-stu-id="14453-170">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="14453-171">İlk olarak, uygulama için bir görüntü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14453-171">First, you create an image for the application.</span></span> <span data-ttu-id="14453-172">Bu noktadan itibaren her dağıtım aynı ortamda çalışır.</span><span class="sxs-lookup"><span data-stu-id="14453-172">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="14453-173">Her kapsayıcı aynı işletim sistemi sürümünü kullanır, yüklü bağımlılıkları aynı sürümü, aynı .NET framework sürümünü kullanır ve aynı işlemi kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="14453-173">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="14453-174">Temel olarak, uygulamanızın bağımlılıkları Docker görüntüsünü kullanarak denetler.</span><span class="sxs-lookup"><span data-stu-id="14453-174">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="14453-175">Kapsayıcılar dağıttığınızda bağımlılıkları uygulamayla ilerler.</span><span class="sxs-lookup"><span data-stu-id="14453-175">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="14453-176">Ek bir faydası, geliştiricilerin uygulama Windows kapsayıcıları tarafından sağlanan tutarlı ortamında çalıştırabilirsiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="14453-176">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="14453-177">Yalnızca belirli sürümler ile görünür sorunları bir hazırlık veya üretim ortamında görünmesini yerine hemen anlaþýlmaz.</span><span class="sxs-lookup"><span data-stu-id="14453-177">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="14453-178">Kapsayıcı uygulamaları çalıştırdığınızda, geliştirme ortamları ve geliştirme ekibi üyeleri tarafından kullanılan farklılıkları daha az önemli.</span><span class="sxs-lookup"><span data-stu-id="14453-178">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="14453-179">Kapsayıcılı uygulamaları daha düz genişleme eğri de vardır.</span><span class="sxs-lookup"><span data-stu-id="14453-179">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="14453-180">Kapsayıcılı uygulamaları, daha fazla uygulama ve hizmet örnekleri (kapsayıcılarında dayanarak) sahip bir VM veya fiziksel makine makine başına normal uygulama dağıtımı ile karşılaştırıldığında olanak verir.</span><span class="sxs-lookup"><span data-stu-id="14453-180">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="14453-181">Bu daha yüksek yoğunluk ve daha az gerekli dönüşür özellikle orchestrators Kubernetes veya Service Fabric gibi kullandığınızda kaynakları.</span><span class="sxs-lookup"><span data-stu-id="14453-181">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="14453-182">İdeal durumlarda verilerin kapsayıcıyla taşınmasını uygulama kodu herhangi bir değişiklik yapmadan gerektirmez (C\#).</span><span class="sxs-lookup"><span data-stu-id="14453-182">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="14453-183">Çoğu senaryoda, Docker dağıtım meta veri dosyaları (Dockerfiles ve Docker Compose) yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="14453-183">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="14453-184">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="14453-184">Next steps</span></span>

<span data-ttu-id="14453-185">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span><span class="sxs-lookup"><span data-stu-id="14453-185">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span></span>

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="14453-186">İzlenecek yol: 3: kapsayıcıları tabanlı Windows uygulamanızı Azure VM'ler için dağıtma</span><span class="sxs-lookup"><span data-stu-id="14453-186">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14453-187">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="14453-187">Technical walkthrough availability</span></span>

<span data-ttu-id="14453-188">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="14453-188">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="14453-189">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="14453-189">Overview</span></span>

<span data-ttu-id="14453-190">Docker ana bilgisayar üzerinde bir Windows Server 2016 sanal makine (VM) azure'a dağıtma hızlı geliştirme/test/hazırlama ortamlarını ayarlama ayarlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="14453-190">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="14453-191">Bu ayrıca sınayıcılar veya iş kullanıcıları uygulama doğrulamak ortak bir yer sağlar.</span><span class="sxs-lookup"><span data-stu-id="14453-191">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="14453-192">VM'ler, bir hizmet (Iaas) üretim ortamlarında geçerli alt yapı de olabilir.</span><span class="sxs-lookup"><span data-stu-id="14453-192">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="14453-193">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="14453-193">Goals</span></span>

<span data-ttu-id="14453-194">Bu kılavuz, Windows Server 2016 veya sonraki sürümler göre Azure vm'lerine Windows kapsayıcıları dağıtırken sahip birden çok alternatifleri göstermek için hedefidir.</span><span class="sxs-lookup"><span data-stu-id="14453-194">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="14453-195">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="14453-195">Scenarios</span></span>

<span data-ttu-id="14453-196">Bazı senaryolarda bu kılavuzda ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="14453-196">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="14453-197">Senaryo A: bir Azure VM geliştirme PC Docker altyapısına bağlantısı üzerinden gelen Dağıt</span><span class="sxs-lookup"><span data-stu-id="14453-197">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Docker altyapısına bağlantısı üzerinden geliştirme bilgisayarınıza bir Azure VM Dağıtım](./media/image5-4.png)

> <span data-ttu-id="14453-199">**Şekil 5-4.**</span><span class="sxs-lookup"><span data-stu-id="14453-199">**Figure 5-4.**</span></span> <span data-ttu-id="14453-200">Docker altyapısına bağlantısı üzerinden geliştirme bilgisayarınıza bir Azure VM Dağıtım</span><span class="sxs-lookup"><span data-stu-id="14453-200">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="14453-201">Senaryo B: Docker kayıt defteri aracılığıyla bir Azure VM dağıtma</span><span class="sxs-lookup"><span data-stu-id="14453-201">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Bir Azure VM Docker kayıt defteri aracılığıyla dağıtma](./media/image5-5.png)

> <span data-ttu-id="14453-203">**Şekil 5-5.**</span><span class="sxs-lookup"><span data-stu-id="14453-203">**Figure 5-5.**</span></span> <span data-ttu-id="14453-204">Bir Azure VM Docker kayıt defteri aracılığıyla dağıtma</span><span class="sxs-lookup"><span data-stu-id="14453-204">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="14453-205">Visual Studio Team Services içinde senaryo C: dağıtımı için bir Azure VM CI/CD'sinden ardışık düzenleri</span><span class="sxs-lookup"><span data-stu-id="14453-205">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Visual Studio Team Services CI/CD ardışık düzen bir Azure VM Dağıtım](./media/image5-6.png)

> <span data-ttu-id="14453-207">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="14453-207">**Figure 5-6.**</span></span> <span data-ttu-id="14453-208">Visual Studio Team Services CI/CD ardışık düzen bir Azure VM Dağıtım</span><span class="sxs-lookup"><span data-stu-id="14453-208">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="14453-209">Azure VM'ler Windows kapsayıcıları için</span><span class="sxs-lookup"><span data-stu-id="14453-209">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="14453-210">Azure VM'ler için Windows Windows Server 2016, Windows 10 veya sonraki sürümler göre VM'ler kapsayıcılardır, Docker altyapısına her ikisi de ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="14453-210">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="14453-211">Çoğu durumda, Windows Server 2016 Azure Vm'lerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14453-211">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="14453-212">Azure şu anda sağlar adlı bir VM'den **Windows Server 2016 kapsayıcılarla**.</span><span class="sxs-lookup"><span data-stu-id="14453-212">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="14453-213">Bu VM, Windows Server Core veya Windows Nano Server ile yeni Windows Server kapsayıcı özelliği denemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14453-213">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="14453-214">Kapsayıcı işletim sistemi görüntüleri yüklenir ve ardından VM ile Docker kullanıma hazırdır.</span><span class="sxs-lookup"><span data-stu-id="14453-214">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="14453-215">Yararları</span><span class="sxs-lookup"><span data-stu-id="14453-215">Benefits</span></span>

<span data-ttu-id="14453-216">Azure'a dağıtırken, şirket içi Windows Server 2016 VM'ler için Windows kapsayıcıları dağıtılabilir rağmen kullanıma hazır Windows Server kapsayıcı VM'ler ile çalışmaya başlamak için daha kolay bir yolu alın.</span><span class="sxs-lookup"><span data-stu-id="14453-216">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="14453-217">Ayrıca Sınayıcılar ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik erişebileceği ortak bir çevrimiçi konumu elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="14453-217">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="14453-218">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="14453-218">Next steps</span></span>

<span data-ttu-id="14453-219">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="14453-219">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="14453-220">İzlenecek yol: 4: Azure kapsayıcı Hizmeti'nde Kubernetes Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma</span><span class="sxs-lookup"><span data-stu-id="14453-220">Walkthrough 4: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14453-221">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="14453-221">Technical walkthrough availability</span></span>

<span data-ttu-id="14453-222">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="14453-222">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="14453-223">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="14453-223">Overview</span></span>

<span data-ttu-id="14453-224">Windows kapsayıcılarında tabanlı bir uygulama hızlı bir şekilde daha uzakta Iaas Vm'lerden taşıma platformlarda kullanmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="14453-224">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="14453-225">Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve önemli bir iyileştirme için dağıtımları ve sürüm oluşturma otomatik.</span><span class="sxs-lookup"><span data-stu-id="14453-225">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="14453-226">Orchestrator'ı kullanarak bu hedefleri elde edebilirsiniz [Kubernetes](https://kubernetes.io/), kullanılabilir [Azure kapsayıcı hizmetlerini](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="14453-226">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="14453-227">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="14453-227">Goals</span></span>

<span data-ttu-id="14453-228">Kubernetes Windows kapsayıcı tabanlı bir uygulamaya dağıtma hakkında bilgi edinmek için bu kılavuzu belirtilir (olarak da bilinir *K8s*) Azure kapsayıcı Hizmeti'nde.</span><span class="sxs-lookup"><span data-stu-id="14453-228">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="14453-229">Kubernetes için baştan dağıtma iki adımlı bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="14453-229">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="14453-230">Kubernetes küme Azure kapsayıcı hizmeti dağıtın.</span><span class="sxs-lookup"><span data-stu-id="14453-230">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="14453-231">İlgili kaynaklar ve uygulama Kubernetes kümeye dağıtın.</span><span class="sxs-lookup"><span data-stu-id="14453-231">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="14453-232">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="14453-232">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="14453-233">Senaryo A: bir geliştirme ortamı'ndan doğrudan Kubernetes kümeye dağıtma</span><span class="sxs-lookup"><span data-stu-id="14453-233">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Geliştirme ortamından doğrudan Kubernetes kümeye dağıtma](./media/image5-7.png)

> <span data-ttu-id="14453-235">**Şekil 5-7.**</span><span class="sxs-lookup"><span data-stu-id="14453-235">**Figure 5-7.**</span></span> <span data-ttu-id="14453-236">Geliştirme ortamından doğrudan Kubernetes kümeye dağıtma</span><span class="sxs-lookup"><span data-stu-id="14453-236">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="14453-237">Senaryo B: dağıtmak Kubernetes kümeye CI/CD'sinden Team Services içinde ardışık düzenleri</span><span class="sxs-lookup"><span data-stu-id="14453-237">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![CI/CD ardışık düzen Team Services Kubernetes kümeye dağıtım](./media/image5-8.png)

> <span data-ttu-id="14453-239">**Şekil 5-8.**</span><span class="sxs-lookup"><span data-stu-id="14453-239">**Figure 5-8.**</span></span> <span data-ttu-id="14453-240">CI/CD ardışık düzen Team Services Kubernetes kümeye dağıtım</span><span class="sxs-lookup"><span data-stu-id="14453-240">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="14453-241">Yararları</span><span class="sxs-lookup"><span data-stu-id="14453-241">Benefits</span></span>

<span data-ttu-id="14453-242">Kubernetes bir kümede dağıtılması için birçok avantaj vardır.</span><span class="sxs-lookup"><span data-stu-id="14453-242">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="14453-243">En büyük (varolan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısını düğümlerinin veya sanal makineleri küme (temel kapsayıcı örnek sayısına göre uygulamanın içinde ölçeklenebilen bir üretime hazır ortamı alma avantajdır Genel ölçeklenebilirlik kümenin).</span><span class="sxs-lookup"><span data-stu-id="14453-243">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="14453-244">Azure kapsayıcı hizmeti popüler açık kaynak Araçlar ve teknolojiler özellikle Azure için en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="14453-244">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="14453-245">Taşınabilirlik, kapsayıcılarınızı hem uygulama yapılandırmanızı sağlayan açık olan çözüm alın.</span><span class="sxs-lookup"><span data-stu-id="14453-245">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="14453-246">Boyutu, ana bilgisayar sayısını seçin ve orchestrator araçları-kapsayıcı hizmeti şey işler.</span><span class="sxs-lookup"><span data-stu-id="14453-246">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="14453-247">Kubernetes ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten aşağıdaki özellikleri, diğerlerinin yanı sıra kolaylaştıran kapsayıcı merkezli bir altyapı planlama için ilerleme:</span><span class="sxs-lookup"><span data-stu-id="14453-247">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="14453-248">Birden çok kapsayıcılara göre uygulamaları</span><span class="sxs-lookup"><span data-stu-id="14453-248">Applications based on multiple containers</span></span>

- <span data-ttu-id="14453-249">Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltma</span><span class="sxs-lookup"><span data-stu-id="14453-249">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="14453-250">Adlandırma ve (örneğin, iç DNS) bulma</span><span class="sxs-lookup"><span data-stu-id="14453-250">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="14453-251">Yükünü dengeleme</span><span class="sxs-lookup"><span data-stu-id="14453-251">Balancing loads</span></span>

- <span data-ttu-id="14453-252">Güncelleştirmeleri alınıyor</span><span class="sxs-lookup"><span data-stu-id="14453-252">Rolling updates</span></span>

- <span data-ttu-id="14453-253">Gizli dağıtma</span><span class="sxs-lookup"><span data-stu-id="14453-253">Distributing secrets</span></span>

- <span data-ttu-id="14453-254">Uygulama durumu denetimleri</span><span class="sxs-lookup"><span data-stu-id="14453-254">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="14453-255">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="14453-255">Next steps</span></span>

<span data-ttu-id="14453-256">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="14453-256">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="14453-257">İzlenecek yol: 5: Azure Service Fabric Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma</span><span class="sxs-lookup"><span data-stu-id="14453-257">Walkthrough 5: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14453-258">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="14453-258">Technical walkthrough availability</span></span>

<span data-ttu-id="14453-259">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="14453-259">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="14453-260">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="14453-260">Overview</span></span>

<span data-ttu-id="14453-261">Windows kapsayıcılarında hızla tabanlı bir uygulama daha uzakta Iaas Vm'lerden taşıma platformları kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="14453-261">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="14453-262">Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve önemli bir iyileştirme için dağıtımları ve sürüm oluşturma otomatik.</span><span class="sxs-lookup"><span data-stu-id="14453-262">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="14453-263">Azure bulutta kullanılabilir, ancak şirket içi kullanmak de kullanılabilir olan, Azure Service Fabric orchestrator kullanarak veya farklı bir genel bulut bile, bu hedefleri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14453-263">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="14453-264">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="14453-264">Goals</span></span>

<span data-ttu-id="14453-265">Bu kılavuzda Windows kapsayıcı tabanlı bir uygulama için Azure Service Fabric kümesi dağıtma hakkında bilgi edinmek için hedefidir.</span><span class="sxs-lookup"><span data-stu-id="14453-265">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="14453-266">Service Fabric sıfırdan dağıtma iki adımlı bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="14453-266">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="14453-267">Service Fabric kümesi Azure (veya farklı bir ortam) dağıtın.</span><span class="sxs-lookup"><span data-stu-id="14453-267">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="14453-268">İlgili kaynaklar ve uygulama için Service Fabric kümesi dağıtın.</span><span class="sxs-lookup"><span data-stu-id="14453-268">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="14453-269">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="14453-269">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="14453-270">Senaryo A: Dağıt doğrudan bir Service Fabric kümesi bir geliştirme ortamı'ndan</span><span class="sxs-lookup"><span data-stu-id="14453-270">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Geliştirme ortamından doğrudan bir Service Fabric kümesi dağıtma](./media/image5-9.png)

> <span data-ttu-id="14453-272">**Şekil 5-9.**</span><span class="sxs-lookup"><span data-stu-id="14453-272">**Figure 5-9.**</span></span> <span data-ttu-id="14453-273">Geliştirme ortamından doğrudan bir Service Fabric kümesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="14453-273">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="14453-274">Senaryo B: dağıtmak için Service Fabric kümesi CI/CD'sinden Team Services içinde ardışık düzenleri</span><span class="sxs-lookup"><span data-stu-id="14453-274">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Service Fabric kümesi için Visual Studio Team Services CI/CD ardışık düzen dağıtım](./media/image5-10.png)

> <span data-ttu-id="14453-276">**Şekil 5-10.**</span><span class="sxs-lookup"><span data-stu-id="14453-276">**Figure 5-10.**</span></span> <span data-ttu-id="14453-277">Service Fabric kümesi için Visual Studio Team Services CI/CD ardışık düzen dağıtım</span><span class="sxs-lookup"><span data-stu-id="14453-277">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="14453-278">Yararları</span><span class="sxs-lookup"><span data-stu-id="14453-278">Benefits</span></span>

<span data-ttu-id="14453-279">Service Fabric, kümeye dağıtma avantajlarını Kubernetes kullanmanın avantajları için benzerdir.</span><span class="sxs-lookup"><span data-stu-id="14453-279">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="14453-280">Tek fark, yine de olan Service Fabric Kubernetes sürüm 1.9 Windows kapsayıcı için bir beta aşamasında olan Kubernetes karşılaştırıldığında Windows uygulamaları için daha da olgun bir üretim ortamında olduğunu (aralık 2017).</span><span class="sxs-lookup"><span data-stu-id="14453-280">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="14453-281">Kubernetes Linux daha da olgun bir ortamdır.</span><span class="sxs-lookup"><span data-stu-id="14453-281">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="14453-282">Azure Service Fabric kullanmanın ana Avantajı (varolan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısına göre kapsayıcı örnek sayısına göre uygulamanın içinde ölçeklenebilen bir üretime hazır ortamı alma olduğu düğümler ve (genel ölçeklenebilirlik kümenin) kümedeki sanal makineleri.</span><span class="sxs-lookup"><span data-stu-id="14453-282">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="14453-283">Azure Service Fabric taşınabilirlik kapsayıcılarınızı hem uygulama yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="14453-283">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="14453-284">Azure'da küme ya da şirket içi, kendi veri merkezinizde yüklemeyi Service Fabric olabilir.</span><span class="sxs-lookup"><span data-stu-id="14453-284">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="14453-285">Bile bir Service Fabric kümesi farklı bir buluta gibi yükleyebilirsiniz [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="14453-285">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="14453-286">Service Fabric ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten aşağıdaki özellikleri, diğerlerinin yanı sıra kolaylaştıran kapsayıcı merkezli bir altyapı planlama için ilerleme:</span><span class="sxs-lookup"><span data-stu-id="14453-286">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="14453-287">Birden çok kapsayıcılara göre uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="14453-287">Applications based on multiple containers.</span></span>

- <span data-ttu-id="14453-288">Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltılıyor.</span><span class="sxs-lookup"><span data-stu-id="14453-288">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="14453-289">Adlandırma ve (örneğin, iç DNS) bulma.</span><span class="sxs-lookup"><span data-stu-id="14453-289">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="14453-290">Yükü Dengeleme.</span><span class="sxs-lookup"><span data-stu-id="14453-290">Balancing loads.</span></span>

- <span data-ttu-id="14453-291">Güncelleştirmeleri alınıyor.</span><span class="sxs-lookup"><span data-stu-id="14453-291">Rolling updates.</span></span>

- <span data-ttu-id="14453-292">Gizli dağıtma.</span><span class="sxs-lookup"><span data-stu-id="14453-292">Distributing secrets.</span></span>

- <span data-ttu-id="14453-293">Uygulama durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="14453-293">Application health checks.</span></span>

<span data-ttu-id="14453-294">Aşağıdaki özellikleri Service Fabric (diğer orchestrators karşılaştırıldığında) de özeldir:</span><span class="sxs-lookup"><span data-stu-id="14453-294">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="14453-295">Güvenilir hizmetler uygulama modeli üzerinden durum bilgisi olan hizmetler yeteneği.</span><span class="sxs-lookup"><span data-stu-id="14453-295">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="14453-296">Reliable Actors uygulama modeli üzerinden aktörler deseni.</span><span class="sxs-lookup"><span data-stu-id="14453-296">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="14453-297">Windows veya Linux kapsayıcıları yanı sıra tam kemik işlemleri dağıtın.</span><span class="sxs-lookup"><span data-stu-id="14453-297">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="14453-298">Gelişmiş çalışırken güncelleştirmeleri ve sistem durumu denetimleri.</span><span class="sxs-lookup"><span data-stu-id="14453-298">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="14453-299">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="14453-299">Next steps</span></span>

<span data-ttu-id="14453-300">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="14453-300">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="14453-301">[Önceki](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[sonraki](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="14453-301">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
