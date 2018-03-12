---
title: "İzlenecek yollar ve teknik başlatılan özeti"
description: "Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize | izlenecek yollar ve teknik başlatılan özeti"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6a2abda3949c1fffc4d731b01e35e58e7c56dac0
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="0ba4f-103">İzlenecek yollar ve teknik başlatılan özeti</span><span class="sxs-lookup"><span data-stu-id="0ba4f-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="0ba4f-104">Bu e-kitap boyutunu sınırlamak için ek teknik belgeler ve tam izlenecek yollar GitHub deposunda kullanılabilir yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="0ba4f-105">Bu bölümde açıklanan izlenecek yollar çevrimiçi bir dizi adım adım kurulum Windows kapsayıcıları ve Azure dağıtımına dayalı birden çok ortamlarının kapsar.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="0ba4f-106">Aşağıdaki bölümlerde ne her gözden geçirme, hedefler ve üst düzey görme hakkında ve ilgili olan görevleri diyagramı sağlar açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="0ba4f-107">İzlenecek yollar kendilerini alabilirsiniz içinde *eShopModernizing* uygulamaları GitHub deposuna wiki adresindeki [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="0ba4f-108">Teknik kılavuz listesi</span><span class="sxs-lookup"><span data-stu-id="0ba4f-108">Technical walkthrough list</span></span>

<span data-ttu-id="0ba4f-109">Aşağıdaki get-started izlenecek kaldırın ve kapsayıcılar kullanarak kaydırma ve Azure içinde birden çok dağıtım seçenekleri kullanarak Taşı örnek uygulamaları için tutarlı ve kapsamlı teknik Kılavuzu sağlamak.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="0ba4f-110">Her biri aşağıdaki izlenecek github'da kullanılabilir olan yeni örnek eShopLegacy ve eShopModernizing uygulamaları kullanır [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="0ba4f-111">**Elektronik Mağaza eski uygulamaları turu**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-111">**Tour of eShop legacy apps**</span></span>

- <span data-ttu-id="0ba4f-112">**Var olan .NET uygulamalarınız Windows kapsayıcılarla containerize**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-112">**Containerize your existing .NET applications with Windows Containers**</span></span>

- <span data-ttu-id="0ba4f-113">**Azure VM'ler kapsayıcıları tabanlı Windows uygulamanızı dağıtma**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-113">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="0ba4f-114">**Azure kapsayıcı Hizmeti'nde Kubernetes Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-114">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="0ba4f-115">**Azure Service Fabric Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-115">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="0ba4f-116">Gözden geçirme 1: Elektronik Mağaza eski uygulamaları turu</span><span class="sxs-lookup"><span data-stu-id="0ba4f-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="0ba4f-117">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="0ba4f-117">Technical walkthrough availability</span></span>

<span data-ttu-id="0ba4f-118">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="0ba4f-119">https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code</span><span class="sxs-lookup"><span data-stu-id="0ba4f-119">https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a><span data-ttu-id="0ba4f-120">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ba4f-120">Overview</span></span>

<span data-ttu-id="0ba4f-121">Bu kılavuzda, iki örnek eski uygulamalar ilk uyarlamasını keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-121">In this walkthrough, you can explore the initial implementation of two sample legacy applications.</span></span> <span data-ttu-id="0ba4f-122">Her iki örnek uygulamaları tek yapılı bir mimariye sahip ve klasik ASP.NET kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-122">Both sample apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="0ba4f-123">ASP.NET ile tabanlı bir uygulamayı 4.x MVC; İkinci uygulama ASP.NET 4.x Web Forms üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="0ba4f-124">Her iki uygulamada bulunan [eShopModernizing GitHub deposuna](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-124">Both applications are in the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

<span data-ttu-id="0ba4f-125">Her iki örnek uygulamaları containerize, benzer şekilde, Klasik containerize [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) bir masaüstü uygulaması olarak kullanılması (WCF) uygulama.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-125">You can containerize both sample apps, similar to the way you can containerize a classic [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) (WCF) application to be consumed as a desktop application.</span></span> <span data-ttu-id="0ba4f-126">Bir örnek için bkz: [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-126">For an example, see [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span></span>

### <a name="goals"></a><span data-ttu-id="0ba4f-127">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="0ba4f-127">Goals</span></span>

<span data-ttu-id="0ba4f-128">Asıl amacı, bu kılavuzda yalnızca bu uygulamalarla ve kendi kod ve yapılandırma hakkında bilgi edinmek için ' dir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="0ba4f-129">Böylece oluşturmak ve test amacıyla SQL veritabanı kullanmadan sahte veriler kullanmak uygulamaları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="0ba4f-130">Bu isteğe bağlı yapılandırma bağımlılık ekleme, ayrılmış bir biçimde temel alır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario"></a><span data-ttu-id="0ba4f-131">Senaryo</span><span class="sxs-lookup"><span data-stu-id="0ba4f-131">Scenario</span></span>

<span data-ttu-id="0ba4f-132">Şekil 5-1 özgün eski uygulamaları basit bir senaryo gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-132">Figure 5-1 shows the simple scenario of the original legacy applications.</span></span>

> ![Basit mimarisi senaryo özgün eski uygulamalar](./media/image5-1.png)
>
> <span data-ttu-id="0ba4f-134">**Şekil 5-1.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-134">**Figure 5-1.**</span></span> <span data-ttu-id="0ba4f-135">Basit mimarisi senaryo özgün eski uygulamalar</span><span class="sxs-lookup"><span data-stu-id="0ba4f-135">Simple architecture scenario of the original legacy applications</span></span>

<span data-ttu-id="0ba4f-136">Bir iş etki alanı açısından bakıldığında, hem uygulamalar aynı katalog yönetimi özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-136">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="0ba4f-137">Elektronik Mağaza Kurumsal ekibi üyelerinin uygulamayı görüntülemek ve ürün kataloğu düzenlemek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-137">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> <span data-ttu-id="0ba4f-138">Şekil 5-2 ilk uygulama ekran görüntüleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-138">Figure 5-2 shows the initial app screenshots.</span></span>

![ASP.NET MVC ve ASP.NET Web Forms uygulamaları (varolan eski teknolojileri)](./media/image5-2.png)

> <span data-ttu-id="0ba4f-140">**Şekil 5-2.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-140">**Figure 5-2.**</span></span> <span data-ttu-id="0ba4f-141">ASP.NET MVC ve ASP.NET Web Forms uygulamaları (varolan eski teknolojileri)</span><span class="sxs-lookup"><span data-stu-id="0ba4f-141">ASP.NET MVC and ASP.NET Web Forms applications (existing/legacy technologies)</span></span>

<span data-ttu-id="0ba4f-142">Gözat ve Katalog girişleri değiştirmek için kullanılan web uygulamaları şunlardır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-142">These are web applications that are used to browse and modify catalog entries.</span></span> <span data-ttu-id="0ba4f-143">Her iki uygulamalar aynı iş/işlevsel özellikleri sunmak olgu yalnızca karşılaştırma amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-143">The fact that both apps deliver the same business/functional features is simply for comparison purposes.</span></span> <span data-ttu-id="0ba4f-144">ASP.NET MVC ve ASP.NET Web Forms çerçeveler kullanılarak oluşturulmuş olan uygulamalar için benzer bir modernization işlem görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-144">You can see a similar modernization process for apps that were created by using the ASP.NET MVC and ASP.NET Web Forms frameworks.</span></span>

<span data-ttu-id="0ba4f-145">Bağımlılıklar ASP.NET 4.x veya önceki sürümleri (veya MVC için Web formları için) anlamına gelir kodu tam olarak ASP.NET Core MVC kullanarak yeniden yazılmıştır sürece bu uygulamaları .NET Core üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-145">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> <span data-ttu-id="0ba4f-146">Bu yeniden düzenlenmesine veya kodu yeniden istemediğiniz yaparsanız, mevcut uygulamaları containerize ve hala aynı .NET teknolojileri ve aynı kodu kullan olduğunu noktası gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-146">This demonstrates the point that if you don't want to re-architect or rewrite code, you can containerize existing applications, and still use the same .NET technologies and the same code.</span></span> <span data-ttu-id="0ba4f-147">Bu eski kod için herhangi bir değişiklik yapılmadan kapsayıcılarında gibi uygulamaları nasıl çalıştırabileceğiniz görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-147">You can see how you can run applications like these in containers, without any changes to legacy code.</span></span>

### <a name="benefits"></a><span data-ttu-id="0ba4f-148">Yararları</span><span class="sxs-lookup"><span data-stu-id="0ba4f-148">Benefits</span></span>

<span data-ttu-id="0ba4f-149">Bu kılavuzda yararları basit: yalnızca bağımlılık ekleme temel kod ve uygulama yapılandırma hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-149">The benefits of this walkthrough are simple: Just get familiar with the code and application configuration, based on dependency injection.</span></span> <span data-ttu-id="0ba4f-150">Ardından, containerize ve birden çok ortamlar için gelecekte dağıtırken Bu yaklaşımda deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-150">Then, you can experiment with this approach when you containerize and deploy to multiple environments in the future.</span></span>

### <a name="next-steps"></a><span data-ttu-id="0ba4f-151">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0ba4f-151">Next steps</span></span>

<span data-ttu-id="0ba4f-152">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-152">Explore this content more in-depth on the GitHub wiki:</span></span>

[<span data-ttu-id="0ba4f-153">https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code</span><span class="sxs-lookup"><span data-stu-id="0ba4f-153">https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="0ba4f-154">İzlenecek yol: 2: var olan .NET uygulamalarınız Windows kapsayıcılarla Containerize</span><span class="sxs-lookup"><span data-stu-id="0ba4f-154">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="0ba4f-155">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="0ba4f-155">Technical walkthrough availability</span></span>

<span data-ttu-id="0ba4f-156">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-156">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="0ba4f-157">https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker</span><span class="sxs-lookup"><span data-stu-id="0ba4f-157">https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a><span data-ttu-id="0ba4f-158">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ba4f-158">Overview</span></span>

<span data-ttu-id="0ba4f-159">MVC, Web Forms veya WCF, üretim, geliştirme ve test ortamları için temel gelenler varolan .NET uygulamalarının dağıtımını iyileştirmek için Windows kapsayıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-159">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="0ba4f-160">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="0ba4f-160">Goals</span></span>

<span data-ttu-id="0ba4f-161">Bu kılavuzun amacı, var olan bir .NET Framework uygulamasını containerizing için çeşitli seçenekler göstermektir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-161">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="0ba4f-162">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-162">You can:</span></span>

- <span data-ttu-id="0ba4f-163">Uygulamanızı kullanarak containerize [Docker için Visual Studio 2017 Araçları](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 veya sonraki sürümler).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-163">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="0ba4f-164">El ile ekleyerek uygulamanızı containerize bir [Dockerfile](https://docs.docker.com/engine/reference/builder/)ve ardından kullanarak [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-164">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="0ba4f-165">Uygulamanızı kullanarak containerize [Img2Docker](https://github.com/docker/communitytools-image2docker-win) Aracı (Docker açık kaynak aracından).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-165">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="0ba4f-166">Bu kılavuz Docker yaklaşım için Visual Studio 2017 araçları odaklanır, ancak diğer iki yaklaşım Dockerfiles kullanarak in regard to oldukça benzer.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-166">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario"></a><span data-ttu-id="0ba4f-167">Senaryo</span><span class="sxs-lookup"><span data-stu-id="0ba4f-167">Scenario</span></span>

<span data-ttu-id="0ba4f-168">Şekil 5-3 kapsayıcılı Elektronik Mağaza eski uygulamaları senaryosu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-168">Figure 5-3 shows the scenario for containerized eShop legacy applications.</span></span>

> ![Bir geliştirme ortamı kapsayıcılı uygulamalarda Basitleştirilmiş mimarisi diyagramı](./media/image5-3.png)
>
> <span data-ttu-id="0ba4f-170">**Şekil 5-3.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-170">**Figure 5-3.**</span></span> <span data-ttu-id="0ba4f-171">Bir geliştirme ortamı kapsayıcılı uygulamalarda Basitleştirilmiş mimarisi diyagramı</span><span class="sxs-lookup"><span data-stu-id="0ba4f-171">Simplified architecture diagram of containerized applications in a development environment</span></span>

### <a name="benefits"></a><span data-ttu-id="0ba4f-172">Yararları</span><span class="sxs-lookup"><span data-stu-id="0ba4f-172">Benefits</span></span>

<span data-ttu-id="0ba4f-173">Bir kapsayıcıda tek yapılı uygulamanızı çalıştırmanın avantajı vardır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-173">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="0ba4f-174">İlk olarak, uygulama için bir görüntü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-174">First, you create an image for the application.</span></span> <span data-ttu-id="0ba4f-175">Bu noktadan itibaren her dağıtım aynı ortamda çalışır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-175">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="0ba4f-176">Her kapsayıcı aynı işletim sistemi sürümünü kullanır, yüklü bağımlılıkları aynı sürümü, aynı .NET framework sürümünü kullanır ve aynı işlemi kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-176">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="0ba4f-177">Temel olarak, uygulamanızın bağımlılıkları Docker görüntüsünü kullanarak denetler.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-177">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="0ba4f-178">Kapsayıcılar dağıttığınızda bağımlılıkları uygulamayla ilerler.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-178">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="0ba4f-179">Ek bir faydası, geliştiricilerin uygulama Windows kapsayıcıları tarafından sağlanan tutarlı ortamında çalıştırabilirsiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-179">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="0ba4f-180">Yalnızca belirli sürümler ile görünür sorunları bir hazırlık veya üretim ortamında görünmesini yerine hemen anlaþýlmaz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-180">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="0ba4f-181">Kapsayıcı uygulamaları çalıştırdığınızda, geliştirme ortamları ve geliştirme ekibi üyeleri tarafından kullanılan farklılıkları daha az önemli.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-181">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="0ba4f-182">Kapsayıcılı uygulamaları daha düz genişleme eğri de vardır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-182">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="0ba4f-183">Kapsayıcılı uygulamaları, daha fazla uygulama ve hizmet örnekleri (kapsayıcılarında dayanarak) sahip bir VM veya fiziksel makine makine başına normal uygulama dağıtımı ile karşılaştırıldığında olanak verir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-183">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="0ba4f-184">Bu daha yüksek yoğunluk ve daha az gerekli dönüşür özellikle orchestrators Kubernetes veya Service Fabric gibi kullandığınızda kaynakları.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-184">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="0ba4f-185">İdeal durumlarda verilerin kapsayıcıyla taşınmasını uygulama kodu herhangi bir değişiklik yapmadan gerektirmez (C\#).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-185">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="0ba4f-186">Çoğu senaryoda, Docker dağıtım meta veri dosyaları (Dockerfiles ve Docker Compose) yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-186">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="0ba4f-187">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0ba4f-187">Next steps</span></span>

<span data-ttu-id="0ba4f-188">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span><span class="sxs-lookup"><span data-stu-id="0ba4f-188">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span></span>

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="0ba4f-189">İzlenecek yol: 3: kapsayıcıları tabanlı Windows uygulamanızı Azure VM'ler için dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-189">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="0ba4f-190">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="0ba4f-190">Technical walkthrough availability</span></span>

<span data-ttu-id="0ba4f-191">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-191">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="0ba4f-192">[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="0ba4f-192">[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="0ba4f-193">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ba4f-193">Overview</span></span>

<span data-ttu-id="0ba4f-194">Docker ana bilgisayar üzerinde bir Windows Server 2016 sanal makine (VM) azure'a dağıtma hızlı geliştirme/test/hazırlama ortamlarını ayarlama ayarlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-194">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="0ba4f-195">Bu ayrıca sınayıcılar veya iş kullanıcıları uygulama doğrulamak ortak bir yer sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-195">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="0ba4f-196">VM'ler, bir hizmet (Iaas) üretim ortamlarında geçerli alt yapı de olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-196">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="0ba4f-197">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="0ba4f-197">Goals</span></span>

<span data-ttu-id="0ba4f-198">Bu kılavuz, Windows Server 2016 veya sonraki sürümler göre Azure vm'lerine Windows kapsayıcıları dağıtırken sahip birden çok alternatifleri göstermek için hedefidir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-198">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="0ba4f-199">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="0ba4f-199">Scenarios</span></span>

<span data-ttu-id="0ba4f-200">Bazı senaryolarda bu kılavuzda ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-200">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="0ba4f-201">Senaryo A: bir Azure VM geliştirme PC Docker altyapısına bağlantısı üzerinden gelen Dağıt</span><span class="sxs-lookup"><span data-stu-id="0ba4f-201">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Docker altyapısına bağlantısı üzerinden geliştirme bilgisayarınıza bir Azure VM Dağıtım](./media/image5-4.png)

> <span data-ttu-id="0ba4f-203">**Şekil 5-4.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-203">**Figure 5-4.**</span></span> <span data-ttu-id="0ba4f-204">Docker altyapısına bağlantısı üzerinden geliştirme bilgisayarınıza bir Azure VM Dağıtım</span><span class="sxs-lookup"><span data-stu-id="0ba4f-204">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="0ba4f-205">Senaryo B: Docker kayıt defteri aracılığıyla bir Azure VM dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-205">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Bir Azure VM Docker kayıt defteri aracılığıyla dağıtma](./media/image5-5.png)

> <span data-ttu-id="0ba4f-207">**Şekil 5-5.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-207">**Figure 5-5.**</span></span> <span data-ttu-id="0ba4f-208">Bir Azure VM Docker kayıt defteri aracılığıyla dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-208">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="0ba4f-209">Visual Studio Team Services içinde senaryo C: dağıtımı için bir Azure VM CI/CD'sinden ardışık düzenleri</span><span class="sxs-lookup"><span data-stu-id="0ba4f-209">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Visual Studio Team Services CI/CD ardışık düzen bir Azure VM Dağıtım](./media/image5-6.png)

> <span data-ttu-id="0ba4f-211">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-211">**Figure 5-6.**</span></span> <span data-ttu-id="0ba4f-212">Visual Studio Team Services CI/CD ardışık düzen bir Azure VM Dağıtım</span><span class="sxs-lookup"><span data-stu-id="0ba4f-212">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="0ba4f-213">Azure VM'ler Windows kapsayıcıları için</span><span class="sxs-lookup"><span data-stu-id="0ba4f-213">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="0ba4f-214">Azure VM'ler için Windows Windows Server 2016, Windows 10 veya sonraki sürümler göre VM'ler kapsayıcılardır, Docker altyapısına her ikisi de ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-214">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="0ba4f-215">Çoğu durumda, Windows Server 2016 Azure Vm'lerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-215">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="0ba4f-216">Azure şu anda sağlar adlı bir VM'den **Windows Server 2016 kapsayıcılarla**.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-216">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="0ba4f-217">Bu VM, Windows Server Core veya Windows Nano Server ile yeni Windows Server kapsayıcı özelliği denemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-217">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="0ba4f-218">Kapsayıcı işletim sistemi görüntüleri yüklenir ve ardından VM ile Docker kullanıma hazırdır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-218">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="0ba4f-219">Yararları</span><span class="sxs-lookup"><span data-stu-id="0ba4f-219">Benefits</span></span>

<span data-ttu-id="0ba4f-220">Azure'a dağıtırken, şirket içi Windows Server 2016 VM'ler için Windows kapsayıcıları dağıtılabilir rağmen kullanıma hazır Windows Server kapsayıcı VM'ler ile çalışmaya başlamak için daha kolay bir yolu alın.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-220">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="0ba4f-221">Ayrıca Sınayıcılar ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik erişebileceği ortak bir çevrimiçi konumu elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-221">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="0ba4f-222">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0ba4f-222">Next steps</span></span>

<span data-ttu-id="0ba4f-223">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-223">Explore this content more in-depth on the GitHub wiki:</span></span>

<span data-ttu-id="0ba4f-224">[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="0ba4f-224">[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="0ba4f-225">İzlenecek yol: 4: Azure kapsayıcı Hizmeti'nde Kubernetes Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-225">Walkthrough 4: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="0ba4f-226">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="0ba4f-226">Technical walkthrough availability</span></span>

<span data-ttu-id="0ba4f-227">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-227">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="0ba4f-228">[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="0ba4f-228">[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="0ba4f-229">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ba4f-229">Overview</span></span>

<span data-ttu-id="0ba4f-230">Windows kapsayıcılarında tabanlı bir uygulama hızlı bir şekilde daha uzakta Iaas Vm'lerden taşıma platformlarda kullanmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-230">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="0ba4f-231">Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve önemli bir iyileştirme için dağıtımları ve sürüm oluşturma otomatik.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-231">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="0ba4f-232">Orchestrator'ı kullanarak bu hedefleri elde edebilirsiniz [Kubernetes](https://kubernetes.io/), kullanılabilir [Azure kapsayıcı hizmetlerini](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-232">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="0ba4f-233">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="0ba4f-233">Goals</span></span>

<span data-ttu-id="0ba4f-234">Kubernetes Windows kapsayıcı tabanlı bir uygulamaya dağıtma hakkında bilgi edinmek için bu kılavuzu belirtilir (olarak da bilinir *K8s*) Azure kapsayıcı Hizmeti'nde.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-234">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="0ba4f-235">Kubernetes için baştan dağıtma iki adımlı bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-235">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="0ba4f-236">Kubernetes küme Azure kapsayıcı hizmeti dağıtın.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-236">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="0ba4f-237">İlgili kaynaklar ve uygulama Kubernetes kümeye dağıtın.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-237">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="0ba4f-238">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="0ba4f-238">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="0ba4f-239">Senaryo A: bir geliştirme ortamı'ndan doğrudan Kubernetes kümeye dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-239">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Geliştirme ortamından doğrudan Kubernetes kümeye dağıtma](./media/image5-7.png)

> <span data-ttu-id="0ba4f-241">**Şekil 5-7.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-241">**Figure 5-7.**</span></span> <span data-ttu-id="0ba4f-242">Geliştirme ortamından doğrudan Kubernetes kümeye dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-242">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="0ba4f-243">Senaryo B: dağıtmak Kubernetes kümeye CI/CD'sinden Team Services içinde ardışık düzenleri</span><span class="sxs-lookup"><span data-stu-id="0ba4f-243">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![CI/CD ardışık düzen Team Services Kubernetes kümeye dağıtım](./media/image5-8.png)

> <span data-ttu-id="0ba4f-245">**Şekil 5-8.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-245">**Figure 5-8.**</span></span> <span data-ttu-id="0ba4f-246">CI/CD ardışık düzen Team Services Kubernetes kümeye dağıtım</span><span class="sxs-lookup"><span data-stu-id="0ba4f-246">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="0ba4f-247">Yararları</span><span class="sxs-lookup"><span data-stu-id="0ba4f-247">Benefits</span></span>

<span data-ttu-id="0ba4f-248">Kubernetes bir kümede dağıtılması için birçok avantaj vardır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-248">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="0ba4f-249">En büyük (varolan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısını düğümlerinin veya sanal makineleri küme (temel kapsayıcı örnek sayısına göre uygulamanın içinde ölçeklenebilen bir üretime hazır ortamı alma avantajdır Genel ölçeklenebilirlik kümenin).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-249">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="0ba4f-250">Azure kapsayıcı hizmeti popüler açık kaynak Araçlar ve teknolojiler özellikle Azure için en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-250">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="0ba4f-251">Taşınabilirlik, kapsayıcılarınızı hem uygulama yapılandırmanızı sağlayan açık olan çözüm alın.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-251">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="0ba4f-252">Boyutu, ana bilgisayar sayısını seçin ve orchestrator araçları-kapsayıcı hizmeti şey işler.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-252">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="0ba4f-253">Kubernetes ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten aşağıdaki özellikleri, diğerlerinin yanı sıra kolaylaştıran kapsayıcı merkezli bir altyapı planlama için ilerleme:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-253">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="0ba4f-254">Birden çok kapsayıcılara göre uygulamaları</span><span class="sxs-lookup"><span data-stu-id="0ba4f-254">Applications based on multiple containers</span></span>

- <span data-ttu-id="0ba4f-255">Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-255">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="0ba4f-256">Adlandırma ve (örneğin, iç DNS) bulma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-256">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="0ba4f-257">Yükünü dengeleme</span><span class="sxs-lookup"><span data-stu-id="0ba4f-257">Balancing loads</span></span>

- <span data-ttu-id="0ba4f-258">Güncelleştirmeleri alınıyor</span><span class="sxs-lookup"><span data-stu-id="0ba4f-258">Rolling updates</span></span>

- <span data-ttu-id="0ba4f-259">Gizli dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-259">Distributing secrets</span></span>

- <span data-ttu-id="0ba4f-260">Uygulama durumu denetimleri</span><span class="sxs-lookup"><span data-stu-id="0ba4f-260">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="0ba4f-261">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0ba4f-261">Next steps</span></span>

<span data-ttu-id="0ba4f-262">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-() Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="0ba4f-262">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="0ba4f-263">İzlenecek yol: 5: Azure Service Fabric Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-263">Walkthrough 5: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="0ba4f-264">Teknik kılavuz kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="0ba4f-264">Technical walkthrough availability</span></span>

<span data-ttu-id="0ba4f-265">Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-265">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="0ba4f-266">[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="0ba4f-266">[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="0ba4f-267">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ba4f-267">Overview</span></span>

<span data-ttu-id="0ba4f-268">Windows kapsayıcılarında hızla tabanlı bir uygulama daha uzakta Iaas Vm'lerden taşıma platformları kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-268">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="0ba4f-269">Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve önemli bir iyileştirme için dağıtımları ve sürüm oluşturma otomatik.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-269">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="0ba4f-270">Azure bulutta kullanılabilir, ancak şirket içi kullanmak de kullanılabilir olan, Azure Service Fabric orchestrator kullanarak veya farklı bir genel bulut bile, bu hedefleri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-270">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="0ba4f-271">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="0ba4f-271">Goals</span></span>

<span data-ttu-id="0ba4f-272">Bu kılavuzda Windows kapsayıcı tabanlı bir uygulama için Azure Service Fabric kümesi dağıtma hakkında bilgi edinmek için hedefidir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-272">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="0ba4f-273">Service Fabric sıfırdan dağıtma iki adımlı bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-273">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="0ba4f-274">Service Fabric kümesi Azure (veya farklı bir ortam) dağıtın.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-274">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="0ba4f-275">İlgili kaynaklar ve uygulama için Service Fabric kümesi dağıtın.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-275">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="0ba4f-276">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="0ba4f-276">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="0ba4f-277">Senaryo A: Dağıt doğrudan bir Service Fabric kümesi bir geliştirme ortamı'ndan</span><span class="sxs-lookup"><span data-stu-id="0ba4f-277">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Geliştirme ortamından doğrudan bir Service Fabric kümesi dağıtma](./media/image5-9.png)

> <span data-ttu-id="0ba4f-279">**Şekil 5-9.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-279">**Figure 5-9.**</span></span> <span data-ttu-id="0ba4f-280">Geliştirme ortamından doğrudan bir Service Fabric kümesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="0ba4f-280">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="0ba4f-281">Senaryo B: dağıtmak için Service Fabric kümesi CI/CD'sinden Team Services içinde ardışık düzenleri</span><span class="sxs-lookup"><span data-stu-id="0ba4f-281">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Service Fabric kümesi için Visual Studio Team Services CI/CD ardışık düzen dağıtım](./media/image5-10.png)

> <span data-ttu-id="0ba4f-283">**Şekil 5-10.**</span><span class="sxs-lookup"><span data-stu-id="0ba4f-283">**Figure 5-10.**</span></span> <span data-ttu-id="0ba4f-284">Service Fabric kümesi için Visual Studio Team Services CI/CD ardışık düzen dağıtım</span><span class="sxs-lookup"><span data-stu-id="0ba4f-284">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="0ba4f-285">Yararları</span><span class="sxs-lookup"><span data-stu-id="0ba4f-285">Benefits</span></span>

<span data-ttu-id="0ba4f-286">Service Fabric, kümeye dağıtma avantajlarını Kubernetes kullanmanın avantajları için benzerdir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-286">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="0ba4f-287">Tek fark, yine de olan Service Fabric Kubernetes sürüm 1.9 Windows kapsayıcı için bir beta aşamasında olan Kubernetes karşılaştırıldığında Windows uygulamaları için daha da olgun bir üretim ortamında olduğunu (aralık 2017).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-287">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="0ba4f-288">Kubernetes Linux daha da olgun bir ortamdır.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-288">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="0ba4f-289">Azure Service Fabric kullanmanın ana Avantajı (varolan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısına göre kapsayıcı örnek sayısına göre uygulamanın içinde ölçeklenebilen bir üretime hazır ortamı alma olduğu düğümler ve (genel ölçeklenebilirlik kümenin) kümedeki sanal makineleri.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-289">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="0ba4f-290">Azure Service Fabric taşınabilirlik kapsayıcılarınızı hem uygulama yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-290">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="0ba4f-291">Azure'da küme ya da şirket içi, kendi veri merkezinizde yüklemeyi Service Fabric olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-291">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="0ba4f-292">Bile bir Service Fabric kümesi farklı bir buluta gibi yükleyebilirsiniz [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="0ba4f-292">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="0ba4f-293">Service Fabric ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten aşağıdaki özellikleri, diğerlerinin yanı sıra kolaylaştıran kapsayıcı merkezli bir altyapı planlama için ilerleme:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-293">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="0ba4f-294">Birden çok kapsayıcılara göre uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-294">Applications based on multiple containers.</span></span>

- <span data-ttu-id="0ba4f-295">Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltılıyor.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-295">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="0ba4f-296">Adlandırma ve (örneğin, iç DNS) bulma.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-296">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="0ba4f-297">Yükü Dengeleme.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-297">Balancing loads.</span></span>

- <span data-ttu-id="0ba4f-298">Güncelleştirmeleri alınıyor.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-298">Rolling updates.</span></span>

- <span data-ttu-id="0ba4f-299">Gizli dağıtma.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-299">Distributing secrets.</span></span>

- <span data-ttu-id="0ba4f-300">Uygulama durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-300">Application health checks.</span></span>

<span data-ttu-id="0ba4f-301">Aşağıdaki özellikleri Service Fabric (diğer orchestrators karşılaştırıldığında) de özeldir:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-301">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="0ba4f-302">Güvenilir hizmetler uygulama modeli üzerinden durum bilgisi olan hizmetler yeteneği.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-302">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="0ba4f-303">Reliable Actors uygulama modeli üzerinden aktörler deseni.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-303">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="0ba4f-304">Windows veya Linux kapsayıcıları yanı sıra tam kemik işlemleri dağıtın.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-304">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="0ba4f-305">Gelişmiş çalışırken güncelleştirmeleri ve sistem durumu denetimleri.</span><span class="sxs-lookup"><span data-stu-id="0ba4f-305">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="0ba4f-306">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0ba4f-306">Next steps</span></span>

<span data-ttu-id="0ba4f-307">Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="0ba4f-307">Explore this content more in-depth on the GitHub wiki:</span></span>

<span data-ttu-id="0ba4f-308">[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="0ba4f-308">[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="0ba4f-309">[Önceki](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[sonraki](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="0ba4f-309">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
