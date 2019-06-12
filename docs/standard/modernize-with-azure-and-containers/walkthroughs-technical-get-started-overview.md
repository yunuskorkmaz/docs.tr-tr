---
title: İzlenecek yollar ve teknik başlangıca genel bakış
description: Azure Bulutu ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | İzlenecek yollar ve teknik başlangıca genel bakış
ms.date: 04/28/2018
ms.openlocfilehash: 1ae6f3c1e739184356b97fa96e74bab402bf1d2a
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832968"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="ea2ce-103">İzlenecek yollar ve teknik başlangıca genel bakış</span><span class="sxs-lookup"><span data-stu-id="ea2ce-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="ea2ce-104">Bu e-kitabı boyutunu sınırlamak için ek teknik belgeler ve tam yönergeler bir GitHub deposunda kullanılabilir yapıldı.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="ea2ce-105">Bu bölümde açıklanan yönergeler çevrimiçi bir dizi adım adım kurulumu Windows kapsayıcıları ve Azure'a dağıtılacak temel alan birden çok ortamın kapsar.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="ea2ce-106">Aşağıdaki bölümlerde hangi her izlenecek yol, hedefler ve üst düzey işleme hakkında ve söz konusu olan görevler bir diyagramını sunar açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="ea2ce-107">İzlenecek alabilirsiniz, *eShopModernizing* uygulamaları GitHub deposu wiki adresindeki <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="ea2ce-108">Teknik kılavuz listesi</span><span class="sxs-lookup"><span data-stu-id="ea2ce-108">Technical walkthrough list</span></span>

<span data-ttu-id="ea2ce-109">Get-started aşağıdaki izlenecek kaldırın ve kapsayıcıları kullanarak shift ve Azure'da birden fazla dağıtım seçeneği kullanılarak ettirin örnek uygulamalar için tutarlı ve kapsamlı teknik rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="ea2ce-110">Her biri aşağıdaki izlenecek yollar github'da kullanılabilir olan yeni örnek eShopLegacy ve eShopModernizing uygulamaları kullanan <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="ea2ce-111">**Elektronik Mağaza eski uygulamaları (modernize etme temel uygulamaları) turu**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="ea2ce-112">**Windows kapsayıcıları ile mevcut ASP.NET web uygulamalarınızı (WebForms ve MVC) kapsayıcılı hale getirme**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="ea2ce-113">**Windows kapsayıcıları ile mevcut, WCF hizmetlerinizi (N katmanlı uygulamalar) kapsayıcılı hale getirme**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="ea2ce-114">**Windows kapsayıcıları tabanlı uygulamanız Azure Vm'lerine dağıtma**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="ea2ce-115">**Azure Container Service'te Kubernetes için Windows kapsayıcı tabanlı uygulamalarınızı dağıtın**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="ea2ce-116">İzlenecek yol: 1: Elektronik Mağaza eski uygulamaları turu</span><span class="sxs-lookup"><span data-stu-id="ea2ce-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ea2ce-117">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="ea2ce-117">Technical walkthrough availability</span></span>

<span data-ttu-id="ea2ce-118">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="ea2ce-119">eShopModernizing wiki izlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="ea2ce-120">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea2ce-120">Overview</span></span>

<span data-ttu-id="ea2ce-121">Bu kılavuzda, üç örnek eski uygulamaları ilk uygulamasını keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="ea2ce-122">İlk iki örnek web uygulaması, tek parçalı mimariye sahip ve klasik ASP.NET kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="ea2ce-123">Bir uygulama üzerinde ASP.NET tabanlı 4.x MVC; İkinci uygulama ASP.NET 4.x Web formları üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="ea2ce-124">Sunucu tarafı ve istemci WinForms uygulaması ile oluşan bir 3 katmanlı uygulama üçüncü uygulamadır [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) hizmeti.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="ea2ce-125">Bu uygulamalar kullanılabilir [eShopModernizing GitHub deposunu](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="ea2ce-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="ea2ce-126">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="ea2ce-126">Goals</span></span>

<span data-ttu-id="ea2ce-127">Bu uygulamalarla ve kod ve yapılandırma hakkında bilgi edinmek için bu kılavuzun ana hedef teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="ea2ce-128">Oluşturma ve test amacıyla SQL veritabanı kullanmadan sahte veriler kullanın. böylece, uygulamaları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="ea2ce-129">Bu isteğe bağlı yapılandırma üzerinde bağımlılık ekleme, ayrılmış bir şekilde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="ea2ce-130">Senaryo 1: ASP.NET Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="ea2ce-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="ea2ce-131">Aşağıdaki şekilde, özgün eski ASP.NET web uygulamaları basit bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Basit mimari senaryo özgün eski ASP.NET web uygulamaları](./media/image5-1.png)

<span data-ttu-id="ea2ce-133">Bir iş etki alanı açısından bakıldığında, her iki uygulama aynı katalog yönetimi özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="ea2ce-134">Elektronik Mağaza Kurumsal ekibi üyelerinin, uygulamayı görüntülemek ve ürün kataloğunu düzenlemek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="ea2ce-135">Sonraki şekilde, ilk uygulama ekran görüntüleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC ve ASP.NET Web Forms uygulamaları (mevcut/bilinen teknolojileri)](./media/image5-2.png)

<span data-ttu-id="ea2ce-137">Bağımlılıkları ASP.NET 4.x veya önceki sürümleri (ya da Web Forms veya MVC için) anlamına gelir kodu tam olarak ASP.NET Core MVC kullanarak yeniden sürece bu uygulamalar üzerinde .NET Core çalışmadığından.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="ea2ce-138">Senaryo 2: WCF hizmeti ve WinForms istemci uygulaması (3 katmanlı uygulama)</span><span class="sxs-lookup"><span data-stu-id="ea2ce-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="ea2ce-139">Aşağıdaki şekilde, özgün 3 katmanlı eski uygulamayı basit bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Bir WCF Hizmeti ile özgün eski 3 katmanlı uygulama ve bir WinForms istemci uygulamasının basit mimari senaryosu](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="ea2ce-141">Yararları</span><span class="sxs-lookup"><span data-stu-id="ea2ce-141">Benefits</span></span>

<span data-ttu-id="ea2ce-142">Bu izlenecek yolda avantajlarını basittir: Yalnızca ilk uygulamaları ve kod ile hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ea2ce-143">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-143">Next steps</span></span>

<span data-ttu-id="ea2ce-144">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="ea2ce-145">Tur taban ASP.NET MVC ve Web Forms "eski" uygulamaları</span><span class="sxs-lookup"><span data-stu-id="ea2ce-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="ea2ce-146">Temel WCF hizmeti ve WinForms (Katman 3) "eski" uygulama turu</span><span class="sxs-lookup"><span data-stu-id="ea2ce-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="ea2ce-147">İzlenecek yol: 2: Windows kapsayıcıları ile mevcut .NET uygulamalarınızı kapsayıcılı hale getirme</span><span class="sxs-lookup"><span data-stu-id="ea2ce-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="ea2ce-148">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea2ce-148">Overview</span></span>

<span data-ttu-id="ea2ce-149">Windows kapsayıcıları, MVC, Web Forms veya WCF, üretim, geliştirme ve test ortamları için tabanlı olanlar gibi mevcut .NET uygulamalarının dağıtımını iyileştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ea2ce-150">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="ea2ce-150">Goals</span></span>

<span data-ttu-id="ea2ce-151">Bu kılavuzun amacı, size var olan bir .NET Framework uygulamasını kapsayıcılı hale getirmek için birkaç seçenek göstermektir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="ea2ce-152">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-152">You can:</span></span>

- <span data-ttu-id="ea2ce-153">Kullanarak uygulamanızı kapsayıcılı hale getirme [Docker için Visual Studio 2017 Araçları](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 veya sonraki sürümler).</span><span class="sxs-lookup"><span data-stu-id="ea2ce-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="ea2ce-154">El ile ekleyerek uygulamanızı kapsayıcılı hale getirme bir [Dockerfile](https://docs.docker.com/engine/reference/builder/)ve ardından kullanarak [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="ea2ce-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="ea2ce-155">Kullanarak uygulamanızı kapsayıcılı hale getirme [Img2Docker](https://github.com/docker/communitytools-image2docker-win) Aracı (Docker açık kaynaklı aracından).</span><span class="sxs-lookup"><span data-stu-id="ea2ce-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="ea2ce-156">Bu izlenecek yol, Docker yaklaşım için Visual Studio 2017 araçları odaklanır, ancak diğer iki yaklaşım dockerfile'ları kullanarak in regard to oldukça benzerdir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="ea2ce-157">Senaryo 1: Kapsayıcıda barındırılan ASP.NET web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="ea2ce-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="ea2ce-158">Aşağıdaki şekilde, kapsayıcılı Elektronik Mağaza eski web apps uygulamaları için bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Basitleştirilmiş bir mimari diyagramını bir geliştirme ortamında ASP.NET uygulamaları kapsayıcıya alınmış](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="ea2ce-160">Senaryo 2: Kapsayıcı WCF Hizmeti</span><span class="sxs-lookup"><span data-stu-id="ea2ce-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="ea2ce-161">Aşağıdaki şekilde kapsayıcı bir WCF Hizmeti ile bir 3 katmanlı uygulama için bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Basitleştirilmiş bir geliştirme ortamında kapsayıcı WCF hizmeti mimarisi diyagramı](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="ea2ce-163">Yararları</span><span class="sxs-lookup"><span data-stu-id="ea2ce-163">Benefits</span></span>

<span data-ttu-id="ea2ce-164">Tek parça, uygulamanızın bir kapsayıcıda çalışan avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="ea2ce-165">İlk olarak, uygulama için bir görüntü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-165">First, you create an image for the application.</span></span> <span data-ttu-id="ea2ce-166">Bu noktadan itibaren her dağıtımda aynı ortamda çalışır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="ea2ce-167">Her kapsayıcı aynı işletim sistemi sürümünü kullanır, aynı sürümü yüklü bağımlılıkları, aynı .NET framework sürümünü kullanır ve aynı işlemi kullanılarak oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="ea2ce-168">Temel olarak, bir Docker görüntüsü kullanarak uygulamanızın bağımlılıkları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="ea2ce-169">Kapsayıcıları dağıtırken uygulama ile bağımlılıkları seyahat.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="ea2ce-170">Ek bir avantaj, geliştiricilerin uygulama Windows kapsayıcıları tarafından sağlanan tutarlı ortamında çalıştırabilirsiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="ea2ce-171">Yalnızca belirli sürümler ile görünen sorunları hemen bir hazırlık veya üretim ortamında görünmesini yerine anlaþýlmaz.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="ea2ce-172">Kapsayıcı uygulamaları çalıştırdığınızda, geliştirme ekibi üyeleri tarafından kullanılan geliştirme ortamlarında farkları daha az önemli.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="ea2ce-173">Kapsayıcılı uygulamaları, ayrıca düzleştiren bir ölçek genişletme eğri vardır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="ea2ce-174">Kapsayıcılı uygulamaları, daha fazla uygulama ve hizmet örnekleri (kapsayıcılarında dayanarak) sahip bir VM veya fiziksel makine normal uygulama dağıtım makine sayısı ile karşılaştırıldığında sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="ea2ce-175">Bu daha yüksek yoğunluklu ve daha az gerekli dönüşür özellikle Kubernetes gibi düzenleyicilerle kullandığınızda kaynakları.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="ea2ce-176">İdeal durumda, kapsayıcı uygulama koduna herhangi bir değişiklik yapmadan gerektirmez (C\#).</span><span class="sxs-lookup"><span data-stu-id="ea2ce-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="ea2ce-177">Çoğu senaryoda, Docker dağıtım meta veri dosyaları (dockerfile'ları ve Docker Compose dosyaları) yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="ea2ce-178">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-178">Next steps</span></span>

<span data-ttu-id="ea2ce-179">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="ea2ce-180">Nasıl Windows kapsayıcıları ve Docker ile .NET Framework web uygulamaları kapsayıcıya alın</span><span class="sxs-lookup"><span data-stu-id="ea2ce-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="ea2ce-181">Bir WCF hizmeti için Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="ea2ce-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="ea2ce-182">İzlenecek yol: 3: Windows kapsayıcıları tabanlı uygulamanız Azure Vm'lerine dağıtma</span><span class="sxs-lookup"><span data-stu-id="ea2ce-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ea2ce-183">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="ea2ce-183">Technical walkthrough availability</span></span>

<span data-ttu-id="ea2ce-184">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="ea2ce-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="ea2ce-185">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea2ce-185">Overview</span></span>

<span data-ttu-id="ea2ce-186">Azure'da Windows Server 2016 sanal makine (VM) üzerinde bir Docker konağı için geliştirme/test/hazırlama ortamlarını hızlıca oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="ea2ce-187">Ayrıca, test uzmanı veya iş kullanıcılarının uygulamayı doğrulamak için ortak bir yerde tanır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="ea2ce-188">VM'ler, geçerli altyapı bir hizmet (Iaas) üretim ortamları da olabilir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ea2ce-189">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="ea2ce-189">Goals</span></span>

<span data-ttu-id="ea2ce-190">Bu kılavuzun amacı, Windows Server 2016 veya sonraki sürümler göre Azure Vm'leri için Windows kapsayıcıları dağıtma sahip birden çok çok\r\nalternatif göstermektir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ea2ce-191">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-191">Scenarios</span></span>

<span data-ttu-id="ea2ce-192">Çeşitli senaryolar bu kılavuzda ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="ea2ce-193">Senaryo A: Docker altyapısı bağlantısı üzerinden bir geliştirme bilgisayarı bir Azure VM'ye dağıtan</span><span class="sxs-lookup"><span data-stu-id="ea2ce-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Bir Azure sanal makinesi için bir Docker altyapısının bağlantısı üzerinden bir geliştirme bilgisayarı dağıtan](./media/image5-4.png)

<span data-ttu-id="ea2ce-195">**Şekil 5-4.**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-195">**Figure 5-4.**</span></span> <span data-ttu-id="ea2ce-196">Bir Azure sanal makinesi için bir Docker altyapısının bağlantısı üzerinden bir geliştirme bilgisayarı dağıtan</span><span class="sxs-lookup"><span data-stu-id="ea2ce-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="ea2ce-197">Senaryo B: Bir Docker kayıt defteri aracılığıyla Azure VM dağıtma</span><span class="sxs-lookup"><span data-stu-id="ea2ce-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Bir Docker kayıt defteri aracılığıyla Azure VM dağıtma](./media/image5-5.png)

<span data-ttu-id="ea2ce-199">**Şekil 5-5.**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-199">**Figure 5-5.**</span></span> <span data-ttu-id="ea2ce-200">Bir Docker kayıt defteri aracılığıyla Azure VM dağıtma</span><span class="sxs-lookup"><span data-stu-id="ea2ce-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ea2ce-201">C: senaryosu Azure DevOps Hizmetleri'nde CI/CD işlem hatları bir Azure VM'ye dağıtan</span><span class="sxs-lookup"><span data-stu-id="ea2ce-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Hizmetleri'nde CI/CD işlem hatları bir Azure VM'ye dağıtan](./media/image5-6.png)

<span data-ttu-id="ea2ce-203">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-203">**Figure 5-6.**</span></span> <span data-ttu-id="ea2ce-204">Azure DevOps Hizmetleri'nde CI/CD işlem hatları bir Azure VM'ye dağıtan</span><span class="sxs-lookup"><span data-stu-id="ea2ce-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="ea2ce-205">Windows kapsayıcıları için Azure sanal makineleri</span><span class="sxs-lookup"><span data-stu-id="ea2ce-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="ea2ce-206">Windows Server 2016, Windows 10 veya sonraki sürümler üzerinde alan VM'ler Azure Vm'leri için Windows kapsayıcıları, Docker altyapısı ile her ikisini birden ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="ea2ce-207">Çoğu durumda, Azure Vm'lerinde Windows Server 2016 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="ea2ce-208">Azure, şu anda adlı bir VM sağlayan **kapsayıcılar ile Windows Server 2016**.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="ea2ce-209">Bu VM, Windows Server Core veya Windows Nano sunucu ile yeni Windows Server kapsayıcı özelliğini denemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="ea2ce-210">Kapsayıcı işletim sistemi görüntüleri yüklenir ve sonra VM ile Docker kullanıma hazırdır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="ea2ce-211">Yararları</span><span class="sxs-lookup"><span data-stu-id="ea2ce-211">Benefits</span></span>

<span data-ttu-id="ea2ce-212">Windows kapsayıcıları, Azure'a dağıtırken şirket içi Windows Server 2016 sanal makinelerine dağıtılabilir olsa da, daha kolay bir yolu, kullanıma hazır Windows Server kapsayıcı sanal makinelerini kullanmaya başlama alın.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="ea2ce-213">Ayrıca test uzmanlarına ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik erişilebilir genel, çevrimiçi bir konuma sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ea2ce-214">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-214">Next steps</span></span>

<span data-ttu-id="ea2ce-215">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="ea2ce-216">İzlenecek yol: 4: Windows kapsayıcı tabanlı uygulamalarınızı Azure Container Instances'a (ACI) dağıtma</span><span class="sxs-lookup"><span data-stu-id="ea2ce-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ea2ce-217">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="ea2ce-217">Technical walkthrough availability</span></span>

<span data-ttu-id="ea2ce-218">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="ea2ce-219">[ACI (Azure Container Instances) için uygulama dağıtma](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="ea2ce-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="ea2ce-220">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea2ce-220">Overview</span></span>

<span data-ttu-id="ea2ce-221">[Azure Container Instances'a (ACI)](https://docs.microsoft.com/azure/container-instances/) kapsayıcılar'ın tek örneklerine dağıtabileceğiniz bir kapsayıcı geliştirme/test/hazırlama ortamına sahip olmak için en hızlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="ea2ce-222">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="ea2ce-222">Goals</span></span>

<span data-ttu-id="ea2ce-223">Bu izlenecek yol, Windows kapsayıcıları için Azure Container Instances'a (ACI) ve eShopModernizing uygulamaları ACI nasıl dağıtabileceğiniz dağıtırken ana senaryoları gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ea2ce-224">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-224">Scenarios</span></span>

<span data-ttu-id="ea2ce-225">Tek veya tüm uygulamaları (MVC uygulaması, WebForms uygulaması veya WCF Hizmeti) dağıtma gibi ACI eShopModernizing uygulamaları dağıtma hakkında daha fazla çeşitleme olabilir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="ea2ce-226">Aşağıda gösterilen aşağıdaki senaryoda, ASP.NET MVC uygulaması yanı sıra bunların her ikisi de dağıtılan SQL Server kapsayıcı kapsayıcıları olarak ACI (Azure Container Instances) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Bir geliştirme ortamından ACI'ya dağıtma](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="ea2ce-228">Yararları</span><span class="sxs-lookup"><span data-stu-id="ea2ce-228">Benefits</span></span>

<span data-ttu-id="ea2ce-229">Azure Container Instances, oluşturmak ve sanal makine sağlamak veya daha yüksek düzeyde bir hizmeti benimsemek zorunda kalmadan azure'da Docker kapsayıcıları yönetmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="ea2ce-230">ACI ile doğrudan azure'da bir Windows kapsayıcı dağıtabilir ve (Windows kapsayıcı görüntüsünü hazır bir Docker kayıt defterinde Docker Hub veya Azure Container gibi olması koşuluyla, bir tam etki alanı adı (FQDN) ile İnternet'e birkaç saniye içinde kullanıma sunma Kayıt defteri).</span><span class="sxs-lookup"><span data-stu-id="ea2ce-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="ea2ce-231">Dikkat Edilecekler</span><span class="sxs-lookup"><span data-stu-id="ea2ce-231">Considerations</span></span>

<span data-ttu-id="ea2ce-232">Ya da tam .NET Framework ile Windows kapsayıcıları dağıtma / ASP.NET veya SQL Server ile Azure Container Instances'a (ACI) Docker görüntüsünü olması gerektiğinden (örneğin, bir Windows Server 2016 ile Windows kapsayıcıları) normal bir Docker konağı dağıtma olarak oldukça hızlı değil her seferinde (Docker kayıt defterinden çekilen) indirilir ve kendi docker Konağı (kalıcı olarak çevrimiçi tutmaktan daha ucuz ancak SQL kapsayıcı görüntüsü (15.1 GB) ve ASP.NET kapsayıcı görüntüsü (13.9 GB) boyutunu önemli ölçüde büyük Azure'da Windows kapsayıcılarını VM ile Windows Server 2016) Kubernetes Azure (Öte yandan, üretim dağıtımları için harika bir seçim olan AKS) gibi tam bir orchestrator bahsedebilirsiniz değil.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="ea2ce-233">Ana sonuç, Azure Container Instances kullanılarak bir çok ilgi çekici CI/CD işlem hatları ve geliştirme/Test senaryoları için seçeneğidir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea2ce-234">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-234">Next steps</span></span>

<span data-ttu-id="ea2ce-235">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="ea2ce-236">İzlenecek yol: 5: Azure Container Service'te Kubernetes için Windows kapsayıcı tabanlı uygulamalarınızı dağıtın</span><span class="sxs-lookup"><span data-stu-id="ea2ce-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ea2ce-237">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="ea2ce-237">Technical walkthrough availability</span></span>

<span data-ttu-id="ea2ce-238">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="ea2ce-239">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea2ce-239">Overview</span></span>

<span data-ttu-id="ea2ce-240">Windows kapsayıcılarında alan bir uygulamayı hızla platformlar Iaas sanal makinelerinden hemen daha da ileri taşıma, kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="ea2ce-241">Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve dağıtımları ve sürüm oluşturma için önemli bir iyileştirme otomatik.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="ea2ce-242">Orchestrator'ı kullanarak bu hedeflere ulaşabilirsiniz [Kubernetes](https://kubernetes.io/)sunulan [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="ea2ce-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="ea2ce-243">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="ea2ce-243">Goals</span></span>

<span data-ttu-id="ea2ce-244">Kubernetes için Windows kapsayıcı tabanlı bir uygulama dağıtma hakkında bilgi edinmek için bu kılavuzun amacı olan (olarak da adlandırılan *K8s*) Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="ea2ce-245">Kubernetes için sıfırdan dağıtma iki adımlı bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="ea2ce-246">Azure Container Service'te bir Kubernetes kümesi dağıtın.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="ea2ce-247">Uygulama ve ilgili kaynakları Kubernetes kümesine dağıtın.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ea2ce-248">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="ea2ce-249">Senaryo A: Bir geliştirme ortamından doğrudan bir Kubernetes kümesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="ea2ce-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Bir geliştirme ortamından doğrudan bir Kubernetes kümesi dağıtma](./media/image5-7.png)

<span data-ttu-id="ea2ce-251">**Şekil 5-7.**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-251">**Figure 5-7.**</span></span> <span data-ttu-id="ea2ce-252">Bir geliştirme ortamından doğrudan bir Kubernetes kümesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="ea2ce-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ea2ce-253">Senaryo B: Azure DevOps Hizmetleri'nde CI/CD işlem hatları gelen bir Kubernetes kümesine dağıtın</span><span class="sxs-lookup"><span data-stu-id="ea2ce-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Hizmetleri'nde CI/CD işlem hatları gelen bir Kubernetes kümesine dağıtın](./media/image5-8.png)

<span data-ttu-id="ea2ce-255">**Şekil 5-8.**</span><span class="sxs-lookup"><span data-stu-id="ea2ce-255">**Figure 5-8.**</span></span> <span data-ttu-id="ea2ce-256">Azure DevOps Hizmetleri'nde CI/CD işlem hatları gelen bir Kubernetes kümesine dağıtın</span><span class="sxs-lookup"><span data-stu-id="ea2ce-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="ea2ce-257">Yararları</span><span class="sxs-lookup"><span data-stu-id="ea2ce-257">Benefits</span></span>

<span data-ttu-id="ea2ce-258">Bir Kubernetes kümesine dağıtmak için birçok faydası vardır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="ea2ce-259">En büyük avantaj (var olan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısını düğümler ve sanal makineleri küme (temel kapsayıcı örneği sayısını göre uygulamanın içinde ölçeklendirebilirsiniz üretime hazır bir ortamın alma olduğu Genel ölçeklenebilirlik kümenin).</span><span class="sxs-lookup"><span data-stu-id="ea2ce-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="ea2ce-260">Azure Container Service, popüler açık kaynak Araçlar ve teknolojiler için özellikle Azure iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="ea2ce-261">Hem kapsayıcılarınız için hem de uygulama yapılandırmanız için taşınabilirlik sunan bir açık çözümü sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="ea2ce-262">Boyutu, konak sayısını seçin ve diğer her şey orchestrator araçları-kapsayıcı hizmeti işler.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="ea2ce-263">Kubernetes ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmeye gelen Diğerlerinin yanında aşağıdaki özellikleri kolaylaştıran bir kapsayıcı merkezli Altyapı planlama ilerleme:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="ea2ce-264">Birden çok kapsayıcılara göre uygulamalar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="ea2ce-265">Container Instances ve yatay ölçeklendirme çoğaltılıyor</span><span class="sxs-lookup"><span data-stu-id="ea2ce-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="ea2ce-266">Adlandırma ve (örneğin, iç DNS) bulma</span><span class="sxs-lookup"><span data-stu-id="ea2ce-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="ea2ce-267">Yükünü dengeleme</span><span class="sxs-lookup"><span data-stu-id="ea2ce-267">Balancing loads</span></span>

- <span data-ttu-id="ea2ce-268">Güncelleştirmeleri alma</span><span class="sxs-lookup"><span data-stu-id="ea2ce-268">Rolling updates</span></span>

- <span data-ttu-id="ea2ce-269">Gizli dizileri dağıtma</span><span class="sxs-lookup"><span data-stu-id="ea2ce-269">Distributing secrets</span></span>

- <span data-ttu-id="ea2ce-270">Uygulama sistem durumu denetimleri</span><span class="sxs-lookup"><span data-stu-id="ea2ce-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea2ce-271">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-271">Next steps</span></span>

<span data-ttu-id="ea2ce-272">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="ea2ce-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="ea2ce-273">İzlenecek yol: 6: Kapsayıcılar için Azure App Service'e Windows kapsayıcıları tabanlı uygulamalarınızı dağıtın</span><span class="sxs-lookup"><span data-stu-id="ea2ce-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ea2ce-274">Teknik kılavuz kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="ea2ce-274">Technical walkthrough availability</span></span>

<span data-ttu-id="ea2ce-275">Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ea2ce-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="ea2ce-276">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea2ce-276">Overview</span></span>

<span data-ttu-id="ea2ce-277">Windows kapsayıcıları kullanarak basit kapsayıcılı bir uygulama, kapsayıcılar için Azure App Service'e kolayca dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="ea2ce-278">Bu, çoğu Windows kapsayıcı tabanlı uygulamalar için önerilen yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="ea2ce-279">Hedefleri</span><span class="sxs-lookup"><span data-stu-id="ea2ce-279">Goals</span></span>

<span data-ttu-id="ea2ce-280">Bu kılavuzun amacı, bir Windows kapsayıcı tabanlı uygulama kapsayıcılar için Azure App Service'e bir kayıt defterinden (Docker Hub veya Azure Container Registry) dağıtmayı öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="ea2ce-281">Senaryo</span><span class="sxs-lookup"><span data-stu-id="ea2ce-281">Scenario</span></span>

![Windows uygulama kapsayıcı tabanlı kapsayıcılar için Azure App Service'e dağıtma](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="ea2ce-283">Yararları</span><span class="sxs-lookup"><span data-stu-id="ea2ce-283">Benefits</span></span>

<span data-ttu-id="ea2ce-284">Kapsayıcılar için Azure App Service'e dağıtma, Azure App Service PaaS avantajları ile eşleştirilmiş kapsayıcılarının avantajları sunar.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="ea2ce-285">App service dikey ve yatay kolayca ölçeklendirilebilir ve otomatik ölçeklendirme için değişen taleplerini karşılamak üzere yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="ea2ce-286">Hiç kesinti yaşanmadan güncelleştirmeleri gerçekleştirilebilir ve sürekli dağıtım bir kayıt defteri yapılandırmasını kolayca de yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ea2ce-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea2ce-287">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ea2ce-287">Next steps</span></span>

<span data-ttu-id="ea2ce-288">Bu içerik daha derinlemesine GitHub Wiki'de keşfedin: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="ea2ce-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="ea2ce-289">[Önceki](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
> [İleri](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="ea2ce-289">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
