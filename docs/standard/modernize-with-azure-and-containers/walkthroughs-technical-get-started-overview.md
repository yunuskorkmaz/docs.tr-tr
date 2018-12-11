---
title: İzlenecek yollar ve teknik başlangıca genel bakış
description: Azure Bulutu ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | İzlenecek yollar ve teknik başlangıca genel bakış
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: f5a9d0c7c1c45a6afca390e93384af4c8386fe09
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150596"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="714d8-103">İzlenecek yollar ve teknik başlangıca genel bakış</span><span class="sxs-lookup"><span data-stu-id="714d8-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="714d8-104">Bu e-kitabı boyutunu sınırlamak için ek teknik belgeler ve tam yönergeler bir GitHub deposunda kullanılabilir yapıldı.</span><span class="sxs-lookup"><span data-stu-id="714d8-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="714d8-105">Bu bölümde açıklanan yönergeler çevrimiçi bir dizi adım adım kurulumu Windows kapsayıcıları ve Azure'a dağıtılacak temel alan birden çok ortamın kapsar.</span><span class="sxs-lookup"><span data-stu-id="714d8-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="714d8-106">Aşağıdaki bölümlerde hangi her izlenecek yol, hedefler ve üst düzey işleme hakkında ve söz konusu olan görevler bir diyagramını sunar açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="714d8-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="714d8-107">İzlenecek alabilirsiniz, *eShopModernizing* uygulamaları GitHub deposu wiki adresindeki [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="714d8-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="714d8-108">Teknik kılavuz listesi</span><span class="sxs-lookup"><span data-stu-id="714d8-108">Technical walkthrough list</span></span>

<span data-ttu-id="714d8-109">Get-started aşağıdaki izlenecek kaldırın ve kapsayıcıları kullanarak shift ve Azure'da birden fazla dağıtım seçeneği kullanılarak ettirin örnek uygulamalar için tutarlı ve kapsamlı teknik rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="714d8-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="714d8-110">Her biri aşağıdaki izlenecek yollar github'da kullanılabilir olan yeni örnek eShopLegacy ve eShopModernizing uygulamaları kullanan [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="714d8-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="714d8-111">**Elektronik Mağaza eski uygulamaları (modernize etme temel uygulamaları) turu**</span><span class="sxs-lookup"><span data-stu-id="714d8-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="714d8-112">**Windows kapsayıcıları ile mevcut ASP.NET web uygulamalarınızı (WebForms ve MVC) kapsayıcılı hale getirme**</span><span class="sxs-lookup"><span data-stu-id="714d8-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="714d8-113">**Windows kapsayıcıları ile mevcut, WCF hizmetlerinizi (N katmanlı uygulamalar) kapsayıcılı hale getirme**</span><span class="sxs-lookup"><span data-stu-id="714d8-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="714d8-114">**Windows kapsayıcıları tabanlı uygulamanız Azure Vm'lerine dağıtma**</span><span class="sxs-lookup"><span data-stu-id="714d8-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="714d8-115">**Azure Container Service'te Kubernetes için Windows kapsayıcı tabanlı uygulamalarınızı dağıtın**</span><span class="sxs-lookup"><span data-stu-id="714d8-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="714d8-116">**Azure Service Fabric'e Windows kapsayıcıları tabanlı uygulamalarınızı dağıtın**</span><span class="sxs-lookup"><span data-stu-id="714d8-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="714d8-117">İzlenecek yol: 1: Elektronik Mağaza eski uygulamaları turu</span><span class="sxs-lookup"><span data-stu-id="714d8-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="714d8-118">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="714d8-118">Technical walkthrough availability</span></span>

<span data-ttu-id="714d8-119">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="714d8-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="714d8-120">eShopModernizing wiki izlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="714d8-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="714d8-121">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="714d8-121">Overview</span></span>

<span data-ttu-id="714d8-122">Bu kılavuzda, üç örnek eski uygulamaları ilk uygulamasını keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714d8-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="714d8-123">İlk iki örnek web uygulaması, tek parçalı mimariye sahip ve klasik ASP.NET kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="714d8-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="714d8-124">Bir uygulama üzerinde ASP.NET tabanlı 4.x MVC; İkinci uygulama ASP.NET 4.x Web formları üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="714d8-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="714d8-125">Sunucu tarafı ve istemci WinForms uygulaması ile oluşan bir 3 katmanlı uygulama üçüncü uygulamadır [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) hizmeti.</span><span class="sxs-lookup"><span data-stu-id="714d8-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="714d8-126">Bu uygulamalar kullanılabilir [eShopModernizing GitHub deposunu](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="714d8-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="714d8-127">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="714d8-127">Goals</span></span>

<span data-ttu-id="714d8-128">Bu uygulamalarla ve kod ve yapılandırma hakkında bilgi edinmek için bu kılavuzun ana hedef teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="714d8-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="714d8-129">Oluşturma ve test amacıyla SQL veritabanı kullanmadan sahte veriler kullanın. böylece, uygulamaları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714d8-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="714d8-130">Bu isteğe bağlı yapılandırma üzerinde bağımlılık ekleme, ayrılmış bir şekilde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="714d8-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="714d8-131">Senaryo 1: ASP.NET Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="714d8-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="714d8-132">Aşağıdaki şekilde, özgün eski ASP.NET web uygulamaları basit bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="714d8-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![Basit mimari senaryo özgün eski ASP.NET web uygulamaları](./media/image5-1.png)
>

<span data-ttu-id="714d8-134">Bir iş etki alanı açısından bakıldığında, her iki uygulama aynı katalog yönetimi özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="714d8-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="714d8-135">Elektronik Mağaza Kurumsal ekibi üyelerinin, uygulamayı görüntülemek ve ürün kataloğunu düzenlemek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="714d8-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="714d8-136">Sonraki şekilde, ilk uygulama ekran görüntüleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="714d8-136">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC ve ASP.NET Web Forms uygulamaları (mevcut/bilinen teknolojileri)](./media/image5-2.png)

<span data-ttu-id="714d8-138">Bağımlılıkları ASP.NET 4.x veya önceki sürümleri (ya da Web Forms veya MVC için) anlamına gelir kodu tam olarak ASP.NET Core MVC kullanarak yeniden sürece bu uygulamalar üzerinde .NET Core çalışmadığından.</span><span class="sxs-lookup"><span data-stu-id="714d8-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="714d8-139">Senaryo 2: WCF hizmeti ve WinForms istemci uygulaması (3 katmanlı uygulama)</span><span class="sxs-lookup"><span data-stu-id="714d8-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="714d8-140">Aşağıdaki şekilde, özgün 3 katmanlı eski uygulamayı basit bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="714d8-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![Bir WCF Hizmeti ile özgün eski 3 katmanlı uygulama ve bir WinForms istemci uygulamasının basit mimari senaryosu](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="714d8-142">Yararları</span><span class="sxs-lookup"><span data-stu-id="714d8-142">Benefits</span></span>

<span data-ttu-id="714d8-143">Bu izlenecek yolda avantajlarını basittir: Yalnızca ilk uygulamaları ve kod ile hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="714d8-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="714d8-144">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="714d8-144">Next steps</span></span>

<span data-ttu-id="714d8-145">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="714d8-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="714d8-146">Tur taban ASP.NET MVC ve Web Forms "eski" uygulamaları</span><span class="sxs-lookup"><span data-stu-id="714d8-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="714d8-147">Temel WCF hizmeti ve WinForms (Katman 3) "eski" uygulama turu</span><span class="sxs-lookup"><span data-stu-id="714d8-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="714d8-148">İzlenecek yol: 2: Windows kapsayıcıları ile mevcut .NET uygulamalarınızı kapsayıcılı hale getirme</span><span class="sxs-lookup"><span data-stu-id="714d8-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="714d8-149">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="714d8-149">Overview</span></span>

<span data-ttu-id="714d8-150">Windows kapsayıcıları, MVC, Web Forms veya WCF, üretim, geliştirme ve test ortamları için tabanlı olanlar gibi mevcut .NET uygulamalarının dağıtımını iyileştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="714d8-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="714d8-151">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="714d8-151">Goals</span></span>

<span data-ttu-id="714d8-152">Bu kılavuzun amacı, size var olan bir .NET Framework uygulamasını kapsayıcılı hale getirmek için birkaç seçenek göstermektir.</span><span class="sxs-lookup"><span data-stu-id="714d8-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="714d8-153">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="714d8-153">You can:</span></span>

- <span data-ttu-id="714d8-154">Kullanarak uygulamanızı kapsayıcılı hale getirme [Docker için Visual Studio 2017 Araçları](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 veya sonraki sürümler).</span><span class="sxs-lookup"><span data-stu-id="714d8-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="714d8-155">El ile ekleyerek uygulamanızı kapsayıcılı hale getirme bir [Dockerfile](https://docs.docker.com/engine/reference/builder/)ve ardından kullanarak [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="714d8-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="714d8-156">Kullanarak uygulamanızı kapsayıcılı hale getirme [Img2Docker](https://github.com/docker/communitytools-image2docker-win) Aracı (Docker açık kaynaklı aracından).</span><span class="sxs-lookup"><span data-stu-id="714d8-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="714d8-157">Bu izlenecek yol, Docker yaklaşım için Visual Studio 2017 araçları odaklanır, ancak diğer iki yaklaşım dockerfile'ları kullanarak in regard to oldukça benzerdir.</span><span class="sxs-lookup"><span data-stu-id="714d8-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="714d8-158">Senaryo 1: Kapsayıcıda barındırılan ASP.NET web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="714d8-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="714d8-159">Aşağıdaki şekilde, kapsayıcılı Elektronik Mağaza eski web apps uygulamaları için bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="714d8-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![Basitleştirilmiş bir mimari diyagramını bir geliştirme ortamında ASP.NET uygulamaları kapsayıcıya alınmış](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="714d8-161">Senaryo 2: Kapsayıcı WCF Hizmeti</span><span class="sxs-lookup"><span data-stu-id="714d8-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="714d8-162">Aşağıdaki şekilde kapsayıcı bir WCF Hizmeti ile bir 3 katmanlı uygulama için bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="714d8-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![Basitleştirilmiş bir geliştirme ortamında kapsayıcı WCF hizmeti mimarisi diyagramı](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="714d8-164">Yararları</span><span class="sxs-lookup"><span data-stu-id="714d8-164">Benefits</span></span>

<span data-ttu-id="714d8-165">Tek parça, uygulamanızın bir kapsayıcıda çalışan avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="714d8-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="714d8-166">İlk olarak, uygulama için bir görüntü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="714d8-166">First, you create an image for the application.</span></span> <span data-ttu-id="714d8-167">Bu noktadan itibaren her dağıtımda aynı ortamda çalışır.</span><span class="sxs-lookup"><span data-stu-id="714d8-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="714d8-168">Her kapsayıcı aynı işletim sistemi sürümünü kullanır, aynı sürümü yüklü bağımlılıkları, aynı .NET framework sürümünü kullanır ve aynı işlemi kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="714d8-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="714d8-169">Temel olarak, bir Docker görüntüsü kullanarak uygulamanızın bağımlılıkları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="714d8-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="714d8-170">Kapsayıcıları dağıtırken uygulama ile bağımlılıkları seyahat.</span><span class="sxs-lookup"><span data-stu-id="714d8-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="714d8-171">Ek bir avantaj, geliştiricilerin uygulama Windows kapsayıcıları tarafından sağlanan tutarlı ortamında çalıştırabilirsiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="714d8-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="714d8-172">Yalnızca belirli sürümler ile görünen sorunları hemen bir hazırlık veya üretim ortamında görünmesini yerine anlaþýlmaz.</span><span class="sxs-lookup"><span data-stu-id="714d8-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="714d8-173">Kapsayıcı uygulamaları çalıştırdığınızda, geliştirme ekibi üyeleri tarafından kullanılan geliştirme ortamlarında farkları daha az önemli.</span><span class="sxs-lookup"><span data-stu-id="714d8-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="714d8-174">Kapsayıcılı uygulamaları, ayrıca düzleştiren bir ölçek genişletme eğri vardır.</span><span class="sxs-lookup"><span data-stu-id="714d8-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="714d8-175">Kapsayıcılı uygulamaları, daha fazla uygulama ve hizmet örnekleri (kapsayıcılarında dayanarak) sahip bir VM veya fiziksel makine normal uygulama dağıtım makine sayısı ile karşılaştırıldığında sağlar.</span><span class="sxs-lookup"><span data-stu-id="714d8-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="714d8-176">Bu daha yüksek yoğunluklu ve daha az gerekli dönüşür özellikle Kubernetes veya Service Fabric gibi düzenleyicilerle kullandığınızda kaynakları.</span><span class="sxs-lookup"><span data-stu-id="714d8-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="714d8-177">İdeal durumda, kapsayıcı uygulama koduna herhangi bir değişiklik yapmadan gerektirmez (C\#).</span><span class="sxs-lookup"><span data-stu-id="714d8-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="714d8-178">Çoğu senaryoda, Docker dağıtım meta veri dosyaları (dockerfile'ları ve Docker Compose dosyaları) yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="714d8-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="714d8-179">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="714d8-179">Next steps</span></span>

<span data-ttu-id="714d8-180">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="714d8-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="714d8-181">Nasıl Windows kapsayıcıları ve Docker ile .NET Framework web uygulamaları kapsayıcıya alın</span><span class="sxs-lookup"><span data-stu-id="714d8-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="714d8-182">Bir WCF hizmeti için Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="714d8-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="714d8-183">İzlenecek yol: 3: Windows kapsayıcıları tabanlı uygulamanız Azure Vm'lerine dağıtma</span><span class="sxs-lookup"><span data-stu-id="714d8-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="714d8-184">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="714d8-184">Technical walkthrough availability</span></span>

<span data-ttu-id="714d8-185">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="714d8-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="714d8-186">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="714d8-186">Overview</span></span>

<span data-ttu-id="714d8-187">Azure'da Windows Server 2016 sanal makine (VM) üzerinde bir Docker konağı için geliştirme/test/hazırlama ortamlarını hızlıca oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="714d8-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="714d8-188">Ayrıca, test uzmanı veya iş kullanıcılarının uygulamayı doğrulamak için ortak bir yerde tanır.</span><span class="sxs-lookup"><span data-stu-id="714d8-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="714d8-189">VM'ler, bir hizmet (Iaas) üretim ortamlarında geçerli alt yapı de olabilir.</span><span class="sxs-lookup"><span data-stu-id="714d8-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="714d8-190">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="714d8-190">Goals</span></span>

<span data-ttu-id="714d8-191">Bu kılavuzun amacı, Windows Server 2016 veya sonraki sürümler göre Azure Vm'leri için Windows kapsayıcıları dağıtma sahip birden çok çok\r\nalternatif göstermektir.</span><span class="sxs-lookup"><span data-stu-id="714d8-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="714d8-192">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="714d8-192">Scenarios</span></span>

<span data-ttu-id="714d8-193">Çeşitli senaryolar bu kılavuzda ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="714d8-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="714d8-194">Senaryo A: Docker altyapısı bağlantısı üzerinden bir geliştirme bilgisayarı bir Azure VM'ye dağıtan</span><span class="sxs-lookup"><span data-stu-id="714d8-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Bir Azure sanal makinesi için bir Docker altyapısının bağlantısı üzerinden bir geliştirme bilgisayarı dağıtan](./media/image5-4.png)

> <span data-ttu-id="714d8-196">**Şekil 5-4.**</span><span class="sxs-lookup"><span data-stu-id="714d8-196">**Figure 5-4.**</span></span> <span data-ttu-id="714d8-197">Bir Azure sanal makinesi için bir Docker altyapısının bağlantısı üzerinden bir geliştirme bilgisayarı dağıtan</span><span class="sxs-lookup"><span data-stu-id="714d8-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="714d8-198">Senaryo B: Bir Docker kayıt defteri aracılığıyla Azure VM dağıtma</span><span class="sxs-lookup"><span data-stu-id="714d8-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Bir Docker kayıt defteri aracılığıyla Azure VM dağıtma](./media/image5-5.png)

> <span data-ttu-id="714d8-200">**Şekil 5-5.**</span><span class="sxs-lookup"><span data-stu-id="714d8-200">**Figure 5-5.**</span></span> <span data-ttu-id="714d8-201">Bir Docker kayıt defteri aracılığıyla Azure VM dağıtma</span><span class="sxs-lookup"><span data-stu-id="714d8-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="714d8-202">C: senaryosu Azure DevOps Hizmetleri'nde CI/CD işlem hatları bir Azure VM'ye dağıtan</span><span class="sxs-lookup"><span data-stu-id="714d8-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Hizmetleri'nde CI/CD işlem hatları bir Azure VM'ye dağıtan](./media/image5-6.png)

> <span data-ttu-id="714d8-204">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="714d8-204">**Figure 5-6.**</span></span> <span data-ttu-id="714d8-205">Azure DevOps Hizmetleri'nde CI/CD işlem hatları bir Azure VM'ye dağıtan</span><span class="sxs-lookup"><span data-stu-id="714d8-205">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="714d8-206">Windows kapsayıcıları için Azure sanal makineleri</span><span class="sxs-lookup"><span data-stu-id="714d8-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="714d8-207">Windows Server 2016, Windows 10 veya sonraki sürümler üzerinde alan VM'ler Azure Vm'leri için Windows kapsayıcıları, Docker altyapısı ile her ikisini birden ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714d8-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="714d8-208">Çoğu durumda, Azure Vm'lerinde Windows Server 2016 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="714d8-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="714d8-209">Azure, şu anda adlı bir VM sağlayan **kapsayıcılar ile Windows Server 2016**.</span><span class="sxs-lookup"><span data-stu-id="714d8-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="714d8-210">Bu VM, Windows Server Core veya Windows Nano sunucu ile yeni Windows Server kapsayıcı özelliğini denemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714d8-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="714d8-211">Kapsayıcı işletim sistemi görüntüleri yüklenir ve sonra VM ile Docker kullanıma hazırdır.</span><span class="sxs-lookup"><span data-stu-id="714d8-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="714d8-212">Yararları</span><span class="sxs-lookup"><span data-stu-id="714d8-212">Benefits</span></span>

<span data-ttu-id="714d8-213">Windows kapsayıcıları, Azure'a dağıtırken şirket içi Windows Server 2016 sanal makinelerine dağıtılabilir olsa da, daha kolay bir yolu, kullanıma hazır Windows Server kapsayıcı sanal makinelerini kullanmaya başlama alın.</span><span class="sxs-lookup"><span data-stu-id="714d8-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="714d8-214">Ayrıca test uzmanlarına ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik erişilebilir genel, çevrimiçi bir konuma sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="714d8-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="714d8-215">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="714d8-215">Next steps</span></span>

<span data-ttu-id="714d8-216">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="714d8-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="714d8-217">İzlenecek yol: 4: Windows kapsayıcı tabanlı uygulamalarınızı Azure Container Instances'a (ACI) dağıtma</span><span class="sxs-lookup"><span data-stu-id="714d8-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="714d8-218">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="714d8-218">Technical walkthrough availability</span></span>

<span data-ttu-id="714d8-219">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="714d8-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="714d8-220">[ACI (Azure Container Instances) için uygulama dağıtma](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="714d8-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="714d8-221">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="714d8-221">Overview</span></span>

<span data-ttu-id="714d8-222">[Azure Container Instances'a (ACI)](https://docs.microsoft.com/azure/container-instances/) kapsayıcılar'ın tek örneklerine dağıtabileceğiniz bir kapsayıcı geliştirme/test/hazırlama ortamına sahip olmak için en hızlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="714d8-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="714d8-223">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="714d8-223">Goals</span></span>

<span data-ttu-id="714d8-224">Bu izlenecek yol, Windows kapsayıcıları için Azure Container Instances'a (ACI) ve eShopModernizing uygulamaları ACI nasıl dağıtabileceğiniz dağıtırken ana senaryoları gösterir.</span><span class="sxs-lookup"><span data-stu-id="714d8-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="714d8-225">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="714d8-225">Scenarios</span></span>

<span data-ttu-id="714d8-226">Tek veya tüm uygulamaları (MVC uygulaması, WebForms uygulaması veya WCF Hizmeti) dağıtma gibi ACI eShopModernizing uygulamaları dağıtma hakkında daha fazla çeşitleme olabilir.</span><span class="sxs-lookup"><span data-stu-id="714d8-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="714d8-227">Aşağıda gösterilen aşağıdaki senaryoda, ASP.NET MVC uygulaması yanı sıra bunların her ikisi de dağıtılan SQL Server kapsayıcı kapsayıcıları olarak ACI (Azure Container Instances) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714d8-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Bir geliştirme ortamından ACI'ya dağıtma](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="714d8-229">Yararları</span><span class="sxs-lookup"><span data-stu-id="714d8-229">Benefits</span></span>

<span data-ttu-id="714d8-230">Azure Container Instances, oluşturmak ve sanal makine sağlamak veya daha yüksek düzeyde bir hizmeti benimsemek zorunda kalmadan azure'da Docker kapsayıcıları yönetmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="714d8-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="714d8-231">ACI ile doğrudan azure'da bir Windows kapsayıcı dağıtabilir ve (Windows kapsayıcı görüntüsünü hazır bir Docker kayıt defterinde Docker Hub veya Azure Container gibi olması koşuluyla, bir tam etki alanı adı (FQDN) ile İnternet'e birkaç saniye içinde kullanıma sunma Kayıt defteri).</span><span class="sxs-lookup"><span data-stu-id="714d8-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="714d8-232">Dikkat Edilecekler</span><span class="sxs-lookup"><span data-stu-id="714d8-232">Considerations</span></span>

<span data-ttu-id="714d8-233">Ya da tam .NET Framework ile Windows kapsayıcıları dağıtma / ASP.NET veya SQL Server ile Azure Container Instances'a (ACI) Docker görüntüsünü olması gerektiğinden (örneğin, bir Windows Server 2016 ile Windows kapsayıcıları) normal bir Docker konağı dağıtma olarak oldukça hızlı değil her seferinde (Docker kayıt defterinden çekilen) indirilir ve kendi docker Konağı (kalıcı olarak çevrimiçi tutmaktan daha ucuz ancak SQL kapsayıcı görüntüsü (15.1 GB) ve ASP.NET kapsayıcı görüntüsü (13.9 GB) boyutunu önemli ölçüde büyük Azure'da Windows kapsayıcılarını VM ile Windows Server 2016) değil, diğer taraftan, üretim dağıtımları için harika bir seçenek olan Kubernetes Azure (AKS/ACS) veya Azure Service Fabric gibi tam bir orchestrator bahsedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714d8-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="714d8-234">Ana sonuç, Azure Container Instances kullanılarak bir çok ilgi çekici CI/CD işlem hatları ve geliştirme/Test senaryoları için seçeneğidir.</span><span class="sxs-lookup"><span data-stu-id="714d8-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="714d8-235">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="714d8-235">Next steps</span></span>

<span data-ttu-id="714d8-236">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="714d8-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="714d8-237">İzlenecek yol: 5: Azure Container Service'te Kubernetes için Windows kapsayıcı tabanlı uygulamalarınızı dağıtın</span><span class="sxs-lookup"><span data-stu-id="714d8-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="714d8-238">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="714d8-238">Technical walkthrough availability</span></span>

<span data-ttu-id="714d8-239">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="714d8-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="714d8-240">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="714d8-240">Overview</span></span>

<span data-ttu-id="714d8-241">Windows kapsayıcılarında alan bir uygulamayı hızla platformlar Iaas sanal makinelerinden hemen daha da ileri taşıma, kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="714d8-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="714d8-242">Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve dağıtımları ve sürüm oluşturma için önemli bir iyileştirme otomatik.</span><span class="sxs-lookup"><span data-stu-id="714d8-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="714d8-243">Orchestrator'ı kullanarak bu hedeflere ulaşabilirsiniz [Kubernetes](https://kubernetes.io/)sunulan [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="714d8-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="714d8-244">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="714d8-244">Goals</span></span>

<span data-ttu-id="714d8-245">Kubernetes için Windows kapsayıcı tabanlı bir uygulama dağıtma hakkında bilgi edinmek için bu kılavuzun amacı olan (olarak da adlandırılan *K8s*) Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="714d8-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="714d8-246">Kubernetes için sıfırdan dağıtma iki adımlı bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="714d8-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="714d8-247">Azure Container Service'te bir Kubernetes kümesi dağıtın.</span><span class="sxs-lookup"><span data-stu-id="714d8-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="714d8-248">Uygulama ve ilgili kaynakları Kubernetes kümesine dağıtın.</span><span class="sxs-lookup"><span data-stu-id="714d8-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="714d8-249">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="714d8-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="714d8-250">Senaryo A: Bir geliştirme ortamından doğrudan bir Kubernetes kümesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="714d8-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Bir geliştirme ortamından doğrudan bir Kubernetes kümesi dağıtma](./media/image5-7.png)

> <span data-ttu-id="714d8-252">**Şekil 5-7.**</span><span class="sxs-lookup"><span data-stu-id="714d8-252">**Figure 5-7.**</span></span> <span data-ttu-id="714d8-253">Bir geliştirme ortamından doğrudan bir Kubernetes kümesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="714d8-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="714d8-254">Senaryo B: Azure DevOps Hizmetleri'nde CI/CD işlem hatları gelen bir Kubernetes kümesine dağıtın</span><span class="sxs-lookup"><span data-stu-id="714d8-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Hizmetleri'nde CI/CD işlem hatları gelen bir Kubernetes kümesine dağıtın](./media/image5-8.png)

> <span data-ttu-id="714d8-256">**Şekil 5-8.**</span><span class="sxs-lookup"><span data-stu-id="714d8-256">**Figure 5-8.**</span></span> <span data-ttu-id="714d8-257">Azure DevOps Hizmetleri'nde CI/CD işlem hatları gelen bir Kubernetes kümesine dağıtın</span><span class="sxs-lookup"><span data-stu-id="714d8-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="714d8-258">Yararları</span><span class="sxs-lookup"><span data-stu-id="714d8-258">Benefits</span></span>

<span data-ttu-id="714d8-259">Bir Kubernetes kümesine dağıtmak için birçok faydası vardır.</span><span class="sxs-lookup"><span data-stu-id="714d8-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="714d8-260">En büyük avantaj (var olan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısını düğümler ve sanal makineleri küme (temel kapsayıcı örneği sayısını göre uygulamanın içinde ölçeklendirebilirsiniz üretime hazır bir ortamın alma olduğu Genel ölçeklenebilirlik kümenin).</span><span class="sxs-lookup"><span data-stu-id="714d8-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="714d8-261">Azure Container Service, popüler açık kaynak Araçlar ve teknolojiler için özellikle Azure iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="714d8-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="714d8-262">Hem kapsayıcılarınız için hem de uygulama yapılandırmanız için taşınabilirlik sunan bir açık çözümü sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="714d8-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="714d8-263">Boyutu, konak sayısını seçin ve diğer her şey orchestrator araçları-kapsayıcı hizmeti işler.</span><span class="sxs-lookup"><span data-stu-id="714d8-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="714d8-264">Kubernetes ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmeye gelen Diğerlerinin yanında aşağıdaki özellikleri kolaylaştıran bir kapsayıcı merkezli Altyapı planlama ilerleme:</span><span class="sxs-lookup"><span data-stu-id="714d8-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="714d8-265">Birden çok kapsayıcılara göre uygulamalar</span><span class="sxs-lookup"><span data-stu-id="714d8-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="714d8-266">Container Instances ve yatay ölçeklendirme çoğaltılıyor</span><span class="sxs-lookup"><span data-stu-id="714d8-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="714d8-267">Adlandırma ve (örneğin, iç DNS) bulma</span><span class="sxs-lookup"><span data-stu-id="714d8-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="714d8-268">Yükünü dengeleme</span><span class="sxs-lookup"><span data-stu-id="714d8-268">Balancing loads</span></span>

- <span data-ttu-id="714d8-269">Güncelleştirmeleri alma</span><span class="sxs-lookup"><span data-stu-id="714d8-269">Rolling updates</span></span>

- <span data-ttu-id="714d8-270">Gizli dizileri dağıtma</span><span class="sxs-lookup"><span data-stu-id="714d8-270">Distributing secrets</span></span>

- <span data-ttu-id="714d8-271">Uygulama sistem durumu denetimleri</span><span class="sxs-lookup"><span data-stu-id="714d8-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="714d8-272">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="714d8-272">Next steps</span></span>

<span data-ttu-id="714d8-273">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="714d8-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="714d8-274">İzlenecek yol: 6: Azure Service Fabric'e Windows kapsayıcıları tabanlı uygulamalarınızı dağıtın</span><span class="sxs-lookup"><span data-stu-id="714d8-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="714d8-275">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="714d8-275">Technical walkthrough availability</span></span>

<span data-ttu-id="714d8-276">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="714d8-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="714d8-277">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="714d8-277">Overview</span></span>

<span data-ttu-id="714d8-278">Windows kapsayıcılarında kolayca tabanlı bir uygulama platformları, Iaas sanal makinelerinden hemen daha da ileri taşıma kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="714d8-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="714d8-279">Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve dağıtımları ve sürüm oluşturma için önemli bir iyileştirme otomatik.</span><span class="sxs-lookup"><span data-stu-id="714d8-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="714d8-280">Azure bulut ortamında kullanılabilir, ancak şirket içinde de kullanılabilir olan, Azure Service Fabric, orchestrator'ı kullanarak veya hatta farklı bir genel bulut bu hedeflere elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714d8-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="714d8-281">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="714d8-281">Goals</span></span>

<span data-ttu-id="714d8-282">Windows kapsayıcı tabanlı bir uygulamayı azure'da bir Service Fabric kümesine dağıtma hakkında bilgi edinmek için bu kılavuzun amacı olan.</span><span class="sxs-lookup"><span data-stu-id="714d8-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="714d8-283">Sıfırdan Service Fabric'e dağıtma iki adımlı bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="714d8-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="714d8-284">Service Fabric kümesi, Azure (veya farklı bir ortam) dağıtın.</span><span class="sxs-lookup"><span data-stu-id="714d8-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="714d8-285">Uygulama ve ilgili kaynakları, Service Fabric kümesine dağıtın.</span><span class="sxs-lookup"><span data-stu-id="714d8-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="714d8-286">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="714d8-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="714d8-287">Senaryo A: Bir geliştirme ortamından doğrudan bir Service Fabric kümesine dağıtma</span><span class="sxs-lookup"><span data-stu-id="714d8-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Bir geliştirme ortamından doğrudan bir Service Fabric kümesine dağıtma](./media/image5-9.png)

> <span data-ttu-id="714d8-289">**Şekil 5-9.**</span><span class="sxs-lookup"><span data-stu-id="714d8-289">**Figure 5-9.**</span></span> <span data-ttu-id="714d8-290">Bir geliştirme ortamından doğrudan bir Service Fabric kümesine dağıtma</span><span class="sxs-lookup"><span data-stu-id="714d8-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="714d8-291">Senaryo B: Bir Service Fabric kümesine CI/CD işlem hatları Azure DevOps Hizmetleri'nde dağıtan</span><span class="sxs-lookup"><span data-stu-id="714d8-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Bir Service Fabric kümesine CI/CD işlem hatları Azure DevOps Hizmetleri'nde dağıtan](./media/image5-10.png)

> <span data-ttu-id="714d8-293">**Şekil 5-10.**</span><span class="sxs-lookup"><span data-stu-id="714d8-293">**Figure 5-10.**</span></span> <span data-ttu-id="714d8-294">Bir Service Fabric kümesine CI/CD işlem hatları Azure DevOps Hizmetleri'nde dağıtan</span><span class="sxs-lookup"><span data-stu-id="714d8-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

## <a name="benefits"></a><span data-ttu-id="714d8-295">Yararları</span><span class="sxs-lookup"><span data-stu-id="714d8-295">Benefits</span></span>

<span data-ttu-id="714d8-296">Bir Service Fabric kümesine dağıtma avantajları, Kubernetes kullanmanın avantajları için benzerdir.</span><span class="sxs-lookup"><span data-stu-id="714d8-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="714d8-297">Tek fark, yine de olan Service Fabric Windows uygulamaları, beta aşamasında Kubernetes sürümü 1.9 Windows kapsayıcıları için Kubernetes ile karşılaştırıldığında daha olgun bir üretim ortamında olduğunu (aralık 2017).</span><span class="sxs-lookup"><span data-stu-id="714d8-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="714d8-298">Kubernetes Linux fazla olgun bir ortamdır.</span><span class="sxs-lookup"><span data-stu-id="714d8-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="714d8-299">Azure Service Fabric kullanmanın ana Avantajı (var olan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısına göre kapsayıcı örneği sayısını göre uygulamanın içinde ölçeklendirebilirsiniz üretime hazır bir ortamın alma olduğu düğümleri veya Vm'leri kümede (genel ölçeklenebilirlik kümenin).</span><span class="sxs-lookup"><span data-stu-id="714d8-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="714d8-300">Azure Service Fabric, kapsayıcılar için hem de uygulama yapılandırmanız için taşınabilirlik sunar.</span><span class="sxs-lookup"><span data-stu-id="714d8-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="714d8-301">Azure'da küme ya da şirket içindeki kendi veri merkezinizde yüklemeyi Service Fabric olabilir.</span><span class="sxs-lookup"><span data-stu-id="714d8-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="714d8-302">Hatta bir Service Fabric kümesi farklı bir buluta gibi yükleyebilirsiniz [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="714d8-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="714d8-303">Service Fabric sayesinde geliştiriciler fiziksel ve sanal makineler hakkında düşünmeye gelen Diğerlerinin yanında aşağıdaki özellikleri kolaylaştıran bir kapsayıcı merkezli Altyapı planlama ilerleme:</span><span class="sxs-lookup"><span data-stu-id="714d8-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="714d8-304">Birden çok kapsayıcılara göre uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="714d8-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="714d8-305">Container Instances ve yatay ölçeklendirme çoğaltılıyor.</span><span class="sxs-lookup"><span data-stu-id="714d8-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="714d8-306">Adlandırma ve (örneğin, iç DNS) bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="714d8-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="714d8-307">Yükü Dengeleme.</span><span class="sxs-lookup"><span data-stu-id="714d8-307">Balancing loads.</span></span>

- <span data-ttu-id="714d8-308">Güncelleştirmeleri alınıyor.</span><span class="sxs-lookup"><span data-stu-id="714d8-308">Rolling updates.</span></span>

- <span data-ttu-id="714d8-309">Gizli dizileri dağıtma.</span><span class="sxs-lookup"><span data-stu-id="714d8-309">Distributing secrets.</span></span>

- <span data-ttu-id="714d8-310">Uygulama durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="714d8-310">Application health checks.</span></span>

<span data-ttu-id="714d8-311">Aşağıdaki özellikleri (diğer düzenleyiciler için karşılaştırıldığında) Service fabric'te özel şunlardır:</span><span class="sxs-lookup"><span data-stu-id="714d8-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="714d8-312">Reliable Services uygulaması modeliyle durum bilgisi olan hizmetler yeteneği.</span><span class="sxs-lookup"><span data-stu-id="714d8-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="714d8-313">Reliable Actors uygulama modeli aracılığıyla aktörler deseni.</span><span class="sxs-lookup"><span data-stu-id="714d8-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="714d8-314">Çıplak bone süreçlerinin, Windows veya Linux kapsayıcıları dağıtın.</span><span class="sxs-lookup"><span data-stu-id="714d8-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="714d8-315">Gelişmiş sıralı güncelleştirme ve sistem durumu denetimleri.</span><span class="sxs-lookup"><span data-stu-id="714d8-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="714d8-316">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="714d8-316">Next steps</span></span>

<span data-ttu-id="714d8-317">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="714d8-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
><span data-ttu-id="714d8-318">[Önceki](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
>[İleri](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="714d8-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>