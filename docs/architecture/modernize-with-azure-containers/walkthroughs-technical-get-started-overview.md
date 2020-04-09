---
title: İzlenecek yollar ve teknik başlangıca genel bakış
description: Azure Bulutu ve Windows Kapsayıcıları ile Mevcut .NET Uygulamalarını Modernize Edin | Walkthroughs ve teknik genel bakış başlar
ms.date: 04/28/2018
ms.openlocfilehash: cff418d9b6e931a3082d8a2f8b818e7275139578
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987875"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="a6fec-103">İzlenecek yollar ve teknik başlangıca genel bakış</span><span class="sxs-lookup"><span data-stu-id="a6fec-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="a6fec-104">Bu e-kitabın boyutunu sınırlamak için, ek teknik belgeler ve tam izlikler GitHub deposunda kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="a6fec-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="a6fec-105">Bu bölümde açıklanan çevrimiçi gözden geçirme ler serisi, Windows Kapsayıcılarını temel alan birden çok ortamın adım adım kurulumünü ve Azure'a dağıtımını kapsar.</span><span class="sxs-lookup"><span data-stu-id="a6fec-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="a6fec-106">Aşağıdaki bölümler, her gözden geçirmenin ne yle ilgili olduğunu, hedeflerini ve üst düzey vizyonunu açıklar ve ilgili görevlerin diyagramını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6fec-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="a6fec-107">*EShopModernizing* uygulamaları GitHub repo wiki de <https://github.com/dotnet-architecture/eShopModernizing/wiki>izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="a6fec-108">Teknik gözden geçirme listesi</span><span class="sxs-lookup"><span data-stu-id="a6fec-108">Technical walkthrough list</span></span>

<span data-ttu-id="a6fec-109">Aşağıdaki başlangıç walkthroughs kapsayıcıları kullanarak kaldırabilir ve kaydırabilirsiniz örnek uygulamalar için tutarlı ve kapsamlı teknik yönergeler sağlar ve ardından Azure'da birden fazla dağıtım seçeneği kullanarak hareket ettirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="a6fec-110">Aşağıdaki izbinlerin her biri, GitHub'da <https://github.com/dotnet-architecture/eShopModernizing>bulunan yeni örnek eShopLegacy ve eShopModernizing uygulamalarını kullanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="a6fec-111">**eShop eski uygulamaları turu (modernize etmek için temel uygulamalar)**</span><span class="sxs-lookup"><span data-stu-id="a6fec-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="a6fec-112">**Mevcut ASP.NET web uygulamalarınızı (WebForm'lar & MVC) Windows Kapsayıcıları ile kaplayın**</span><span class="sxs-lookup"><span data-stu-id="a6fec-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="a6fec-113">**Mevcut WCF hizmetlerinizi (N Katmanlı uygulamalar) Windows Kapsayıcıları ile konteynerleştirin**</span><span class="sxs-lookup"><span data-stu-id="a6fec-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="a6fec-114">**Windows Kapsayıcılar tabanlı uygulamanızı Azure VM'lerine dağıtma**</span><span class="sxs-lookup"><span data-stu-id="a6fec-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="a6fec-115">**Azure Kapsayıcı Hizmeti'nde Windows Kapsayıcı tabanlı uygulamalarınızı Kubernetes'e dağıtın**</span><span class="sxs-lookup"><span data-stu-id="a6fec-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="a6fec-116">Walkthrough 1: eShop eski uygulamaları turu</span><span class="sxs-lookup"><span data-stu-id="a6fec-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="a6fec-117">Teknik yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="a6fec-117">Technical walkthrough availability</span></span>

<span data-ttu-id="a6fec-118">Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="a6fec-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="a6fec-119">eShopModernizing wiki walkthroughs</span><span class="sxs-lookup"><span data-stu-id="a6fec-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="a6fec-120">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6fec-120">Overview</span></span>

<span data-ttu-id="a6fec-121">Bu izne, üç örnek eski uygulamanın ilk uygulamasını keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="a6fec-122">İlk iki örnek web uygulaması yekpare bir mimariye sahiptir ve klasik ASP.NET kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="a6fec-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="a6fec-123">Bir uygulama ASP.NET 4.x MVC dayanmaktadır; ikinci uygulama ASP.NET 4.x Web Formları dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="a6fec-124">Üçüncü uygulama, istemci WinForms uygulaması ve sunucu tarafı [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) hizmeti tarafından oluşturulan 3 Katmanlı bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="a6fec-125">Tüm bu uygulamalar [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing)mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a6fec-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="a6fec-126">Hedefler</span><span class="sxs-lookup"><span data-stu-id="a6fec-126">Goals</span></span>

<span data-ttu-id="a6fec-127">Bu gözden geçirmenin temel amacı, bu uygulamalara ve onların kod ve yapılandırmasına aşina olmaktır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="a6fec-128">Uygulamaları, SQL veritabanını kullanmadan, test amacıyla sahte veri oluşturacak ve kullanacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="a6fec-129">Bu isteğe bağlı config bağımlılık enjeksiyonu dayanmaktadır, bir decoupled şekilde.</span><span class="sxs-lookup"><span data-stu-id="a6fec-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="a6fec-130">Senaryo 1: ASP.NET Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="a6fec-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="a6fec-131">Aşağıdaki şekil, web uygulamaları ASP.NET orijinal eski basit senaryo gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Web uygulamaları ASP.NET orijinal mirasın basit mimari senaryosu](./media/image5-1.png)

<span data-ttu-id="a6fec-133">İş alanı açısından bakıldığında, her iki uygulama da aynı katalog yönetimi özelliklerini sunar.</span><span class="sxs-lookup"><span data-stu-id="a6fec-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="a6fec-134">eShop kurumsal ekibinin üyeleri, ürün kataloğunu görüntülemek ve bunları görüntülemek için uygulamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="a6fec-135">Bir sonraki şekil, ilk uygulama ekran görüntülerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC ve ASP.NET Web Formları uygulamaları (mevcut/eski teknolojiler)](./media/image5-2.png)

<span data-ttu-id="a6fec-137">ASP.NET 4.x veya önceki sürümlerde (MVC veya Web Formları için) bağımlılıklar, kod ASP.NET Core MVC kullanılarak tamamen yeniden yazılmadıkça bu uygulamaların .NET Core'da çalışmayamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="a6fec-138">Senaryo 2: WCF hizmeti ve WinForms istemci uygulaması (3 Katmanlı uygulama)</span><span class="sxs-lookup"><span data-stu-id="a6fec-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="a6fec-139">Aşağıdaki şekil, orijinal 3 Katmanlı eski uygulamanın basit senaryosunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![WCF hizmeti ve WinForms istemci uygulaması ile orijinal eski 3 Katmanlı uygulamanın basit mimari senaryosu](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="a6fec-141">Yararları</span><span class="sxs-lookup"><span data-stu-id="a6fec-141">Benefits</span></span>

<span data-ttu-id="a6fec-142">Bu gözden geçirmenin avantajları basittir: Kodu ve ilk uygulamaları tanımanın yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="a6fec-143">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a6fec-143">Next steps</span></span>

<span data-ttu-id="a6fec-144">Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:</span><span class="sxs-lookup"><span data-stu-id="a6fec-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="a6fec-145">MVC ve Web Formları "eski" uygulamalar ASP.NET temel üzerinde Tur</span><span class="sxs-lookup"><span data-stu-id="a6fec-145">Tour on the baseline ASP.NET MVC and Web Forms "legacy" apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="a6fec-146">Temel WCF hizmeti nde tur ve WinForms (3 Katmanlı) "eski" uygulaması</span><span class="sxs-lookup"><span data-stu-id="a6fec-146">Tour on the baseline WCF service and WinForms (3-Tier) "legacy" app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="a6fec-147">Walkthrough 2: Mevcut .NET uygulamalarınızı Windows Kapsayıcıları ile konteynerleştirin</span><span class="sxs-lookup"><span data-stu-id="a6fec-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="a6fec-148">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6fec-148">Overview</span></span>

<span data-ttu-id="a6fec-149">MVC, Web Formları veya WCF'ye dayalı uygulamalar gibi varolan .NET uygulamalarının üretim, geliştirme ve test ortamlarına dağıtımını iyileştirmek için Windows Kapsayıcıları'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a6fec-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="a6fec-150">Hedefler</span><span class="sxs-lookup"><span data-stu-id="a6fec-150">Goals</span></span>

<span data-ttu-id="a6fec-151">Bu gözden geçirmenin amacı, varolan bir .NET Framework uygulamasını kapsayıcı hale getirmek için çeşitli seçenekler göstermektir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="a6fec-152">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a6fec-152">You can:</span></span>

- <span data-ttu-id="a6fec-153">[Visual Studio 2017 Docker Araçları](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 veya sonraki sürümleri) kullanarak başvurunuzu konteynerize edin.</span><span class="sxs-lookup"><span data-stu-id="a6fec-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="a6fec-154">Bir [Dockerfile'ı](https://docs.docker.com/engine/reference/builder/)el ile ekleyerek ve docker [CLI'yi](https://docs.docker.com/engine/reference/commandline/cli/)kullanarak uygulamanızı konteynerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a6fec-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="a6fec-155">[Img2Docker](https://github.com/docker/communitytools-image2docker-win) aracını (Docker'dan gelen açık kaynak bir araç) kullanarak uygulamanızı konteynerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a6fec-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="a6fec-156">Bu izim, Visual Studio 2017 Docker için Araçlar yaklaşımına odaklanır, ancak diğer iki yaklaşım Dockerfiles'ı kullanma konusunda oldukça benzerdir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="a6fec-157">Senaryo 1: Web uygulamaları ASP.NET kaplanmış</span><span class="sxs-lookup"><span data-stu-id="a6fec-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="a6fec-158">Aşağıdaki şekil konteynere eShop eski web uygulamaları uygulamaları için senaryo gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Geliştirme ortamında kapsayıcı ASP.NET uygulamalarının basitleştirilmiş mimari diyagramı](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="a6fec-160">Senaryo 2: Konteynerleştirilmiş WCF hizmeti</span><span class="sxs-lookup"><span data-stu-id="a6fec-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="a6fec-161">Aşağıdaki şekil, konteynerleştirilmiş bir WCF hizmetine sahip 3 Katmanlı bir uygulama senaryosunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Geliştirme ortamında kapsayıcı WCF hizmetinin basitleştirilmiş mimari diyagramı](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="a6fec-163">Yararları</span><span class="sxs-lookup"><span data-stu-id="a6fec-163">Benefits</span></span>

<span data-ttu-id="a6fec-164">Yekpare uygulamanızı bir kapta çalıştırmanın avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="a6fec-165">İlk olarak, uygulama için bir görüntü oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-165">First, you create an image for the application.</span></span> <span data-ttu-id="a6fec-166">Bu noktadan itibaren, her dağıtım aynı ortamda çalışır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="a6fec-167">Her kapsayıcı aynı işletim sistemi sürümünü kullanır, bağımlılıkların aynı sürümü yüklü, aynı .NET çerçeve sürümünü kullanır ve aynı işlem kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a6fec-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="a6fec-168">Temel olarak, docker görüntüsü kullanarak uygulamanızın bağımlılıklarını kontrol eleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="a6fec-169">Kapsayıcıları dağıttığınızda bağımlılıklar uygulamayla birlikte hareket emredilir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="a6fec-170">Ek bir yararı geliştiriciler Windows Kapsayıcılar tarafından sağlanan tutarlı ortamda uygulama çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="a6fec-171">Yalnızca belirli sürümlerle görünen sorunlar, bir evreleme veya üretim ortamında yüzeye çıkmak yerine hemen tespit edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="a6fec-172">Uygulamalar kapsayıcılarda çalıştırıldığında geliştirme ekibi üyeleri tarafından kullanılan geliştirme ortamlarında farklılıklar daha az önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="a6fec-173">Konteyner uygulamaları da düz bir ölçek-out eğrisi var.</span><span class="sxs-lookup"><span data-stu-id="a6fec-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="a6fec-174">Kapsayıcı uygulamalar, bir VM veya fiziksel makinede makine başına normal uygulama dağıtımlarına kıyasla daha fazla uygulama ve servis örneğine (kapsayıcılara göre) sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="a6fec-175">Bu, özellikle Kubernetes gibi orkestratörleri kullandığınızda, daha yüksek yoğunluk ve daha az gerekli kaynak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="a6fec-176">Konteynerleştirme, ideal durumlarda, uygulama kodu (C)\#herhangi bir değişiklik yapılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="a6fec-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="a6fec-177">Çoğu senaryoda, docker dağıtım meta veri dosyaları (Dockerfiles ve Docker Compose dosyaları) gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="a6fec-178">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a6fec-178">Next steps</span></span>

<span data-ttu-id="a6fec-179">Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:</span><span class="sxs-lookup"><span data-stu-id="a6fec-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="a6fec-180">Windows Kapsayıcıları ve Docker ile .NET Framework web uygulamalarını nasıl kaplarlar?</span><span class="sxs-lookup"><span data-stu-id="a6fec-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="a6fec-181">Bir WCF hizmetine Docker Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="a6fec-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="a6fec-182">Walkthrough 3: Windows Kapsayıcıları tabanlı uygulamanızı Azure VM'lerine dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="a6fec-183">Teknik yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="a6fec-183">Technical walkthrough availability</span></span>

<span data-ttu-id="a6fec-184">Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="a6fec-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="a6fec-185">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6fec-185">Overview</span></span>

<span data-ttu-id="a6fec-186">Azure'daki Windows Server 2016 Sanal Makine'de (VM) Docker ana bilgisayara dağıtmak, geliştirme/test/evreleme ortamlarını hızla ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6fec-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="a6fec-187">Ayrıca, test edenlerin veya iş kullanıcılarının uygulamayı doğrulamaları için ortak bir yer sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6fec-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="a6fec-188">VM'ler, Hizmet Olarak Altyapı (IaaS) üretim ortamları da geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="a6fec-189">Hedefler</span><span class="sxs-lookup"><span data-stu-id="a6fec-189">Goals</span></span>

<span data-ttu-id="a6fec-190">Bu izbin amacı, Windows Kapsayıcılarını Windows Server 2016 veya sonraki sürümlerine dayalı Azure VM'lere dağıtırken sahip olduğunuz birden çok alternatifi size göstermektir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="a6fec-191">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="a6fec-191">Scenarios</span></span>

<span data-ttu-id="a6fec-192">Bu gözden geçirme de çeşitli senaryolar ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="a6fec-193">Senaryo A: Docker Engine bağlantısı aracılığıyla dev bir bilgisayardan Azure VM'ye dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Docker Engine bağlantısı aracılığıyla dev bir bilgisayardan Azure VM'ye dağıtma](./media/image5-4.png)

<span data-ttu-id="a6fec-195">**Şekil 5-4.**</span><span class="sxs-lookup"><span data-stu-id="a6fec-195">**Figure 5-4.**</span></span> <span data-ttu-id="a6fec-196">Docker Engine bağlantısı aracılığıyla dev bir bilgisayardan Azure VM'ye dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="a6fec-197">Senaryo B: Docker Kayıt Defteri aracılığıyla Azure VM'ye dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Docker Kayıt Defteri aracılığıyla Azure VM'ye dağıtma](./media/image5-5.png)

<span data-ttu-id="a6fec-199">**Şekil 5-5.**</span><span class="sxs-lookup"><span data-stu-id="a6fec-199">**Figure 5-5.**</span></span> <span data-ttu-id="a6fec-200">Docker Kayıt Defteri aracılığıyla Azure VM'ye dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="a6fec-201">Senaryo C: Azure DevOps Hizmetlerinde CI/CD ardışık hatlarından bir Azure VM'sine dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Hizmetleri'ndeki CI/CD ardışık işlerinden Azure VM'ye dağıtma](./media/image5-6.png)

<span data-ttu-id="a6fec-203">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="a6fec-203">**Figure 5-6.**</span></span> <span data-ttu-id="a6fec-204">Azure DevOps Hizmetleri'ndeki CI/CD ardışık işlerinden Azure VM'ye dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="a6fec-205">Windows Kapsayıcıları için Azure VM'ler</span><span class="sxs-lookup"><span data-stu-id="a6fec-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="a6fec-206">Windows Kapsayıcıları için Azure VM'ler, Docker Engine'in ayarlanmasıyla windows server 2016, Windows 10 veya sonraki sürümlere dayalı VM'lerdir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="a6fec-207">Çoğu durumda, Windows Server 2016 Azure VM'lerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="a6fec-208">Azure şu anda **Kapsayıcılarla Windows Server 2016**adında bir VM sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6fec-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="a6fec-209">Bu VM'yi, Windows Server Core veya Windows Nano Server ile yeni Windows Server Kapsayıcı özelliğini denemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="a6fec-210">Konteyner işletim sistemi görüntüleri yüklenir ve ardından VM Docker ile kullanıma hazırdır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="a6fec-211">Yararları</span><span class="sxs-lookup"><span data-stu-id="a6fec-211">Benefits</span></span>

<span data-ttu-id="a6fec-212">Windows Kapsayıcıları şirket içi Windows Server 2016 VM'lerine dağıtılabilse de, Azure'a dağıttığınızda kullanıma hazır Windows Server Container VM'lerle başlamak için daha kolay bir yol elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="a6fec-213">Ayrıca, test edenler tarafından erişilebilen ortak bir çevrimiçi konum ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik de elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-213">You also get a common online location that's accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="a6fec-214">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a6fec-214">Next steps</span></span>

<span data-ttu-id="a6fec-215">Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:</span><span class="sxs-lookup"><span data-stu-id="a6fec-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="a6fec-216">Walkthrough 4: Windows Kapsayıcıtabanlı uygulamalarınızı Azure Kapsayıcı Örneklerine (ACI) dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="a6fec-217">Teknik yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="a6fec-217">Technical walkthrough availability</span></span>

<span data-ttu-id="a6fec-218">Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="a6fec-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="a6fec-219">[Uygulamaları ACI'ye Dağıtma (Azure Kapsayıcı Örnekleri)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="a6fec-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="a6fec-220">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6fec-220">Overview</span></span>

<span data-ttu-id="a6fec-221">[Azure Kapsayıcı Örnekleri (ACI),](https://docs.microsoft.com/azure/container-instances/) tek kapsayıcı örneklerini dağıtabileceğiniz kapsayıcı geliştirme/test/hazırlama ortamına sahip olmak için en hızlı yoldur.</span><span class="sxs-lookup"><span data-stu-id="a6fec-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="a6fec-222">Hedefler</span><span class="sxs-lookup"><span data-stu-id="a6fec-222">Goals</span></span>

<span data-ttu-id="a6fec-223">Bu izim, Windows Kapsayıcılarını Azure Kapsayıcı Örneklerine (ACI) dağıtırken ana senaryoları ve eShopModernizing Apps'ı ACI'ye nasıl dağıtabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="a6fec-224">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="a6fec-224">Scenarios</span></span>

<span data-ttu-id="a6fec-225">eShopModernizing uygulamalarını ACI'ye dağıtma konusunda, uygulamaların yalnızca birini veya tamamını dağıtma (MVC uygulaması, WebForms uygulaması veya WCF hizmeti) gibi varyasyonlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="a6fec-226">Aşağıda gösterilen aşağıdaki senaryoda ASP.NET MVC uygulamasını ve SQL Server kapsayıcısını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Geliştirme ortamından ACI'ye dağıtın](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="a6fec-228">Yararları</span><span class="sxs-lookup"><span data-stu-id="a6fec-228">Benefits</span></span>

<span data-ttu-id="a6fec-229">Azure Container Instances, sanal makine sağlamak veya daha yüksek düzey bir hizmet benimsemek zorunda kalmadan Azure’da Docker kapsayıcıları oluşturmayı ve yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="a6fec-230">ACI ile, Azure'da doğrudan bir Windows kapsayıcısı dağıtabilir ve birkaç saniye içinde tam nitelikli bir alan adı (FQDN) ile internete maruz kalabilirsiniz (Windows Konteyner görüntüsünü Docker Hub veya Azure Kapsayıcı Kayıt Defteri gibi docker kayıt defterinde hazır olması koşuluyla).</span><span class="sxs-lookup"><span data-stu-id="a6fec-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="a6fec-231">Dikkat edilmesi gerekenler</span><span class="sxs-lookup"><span data-stu-id="a6fec-231">Considerations</span></span>

<span data-ttu-id="a6fec-232">Windows Kapsayıcılarını Azure Kapsayıcı Örneklerine (ACI) tam .NET Framework / ASP.NET veya SQL Server ile dağıtmak, normal bir Docker Hosts'a (Windows Containers ile windows server 2016 gibi) dağıtmak kadar hızlı değildir, çünkü Docker görüntüsünün her seferinde indirilmesi (Docker kayıt defterinden çekilmesi) ve SQL kapsayıcı görüntüsünün (15,1 GB) boyutları ASP.NET (13,9 GB) önemli ölçüde büyüktür, ancak kendi docker ana bilgisayarını (Windows Containers VM ile Azure'da kalıcı olarak çevrimiçi Windows Server 2016) korumaktan çok daha ucuzdur, diğer taraftan, üretim dağıtımları için harika bir seçim olan Azure'daki Kubernetes (AKS) gibi bir orkestratörden bahsetmiyorum bile.</span><span class="sxs-lookup"><span data-stu-id="a6fec-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="a6fec-233">Ana sonuç olarak, Azure Kapsayıcı Örnekleri'ni kullanmak, Geliştirme/Test senaryoları ve CI/CD ardışık hatları için çok cazip bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a6fec-234">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a6fec-234">Next steps</span></span>

<span data-ttu-id="a6fec-235">Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:</span><span class="sxs-lookup"><span data-stu-id="a6fec-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="a6fec-236">Walkthrough 5: Windows Kapsayıcı tabanlı uygulamalarınızı Azure Kapsayıcı Hizmeti'nde Kubernetes'e dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="a6fec-237">Teknik yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="a6fec-237">Technical walkthrough availability</span></span>

<span data-ttu-id="a6fec-238">Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="a6fec-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="a6fec-239">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6fec-239">Overview</span></span>

<span data-ttu-id="a6fec-240">Windows Kapsayıcıları'nı temel alan bir uygulamanın, IaaS VM'lerden daha da uzağa hareket eden platformları hızlı bir şekilde kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="a6fec-241">Bu, yüksek ölçeklenebilirlik ve daha iyi otomatik ölçeklenebilirlik elde etmek ve otomatik dağıtımlar ve sürümlerde önemli bir iyileşme sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="a6fec-242">[Azure Konteyner Hizmetleri'nde](https://azure.microsoft.com/services/container-service/)bulunan orkestratör [Kubernetes'i](https://kubernetes.io/)kullanarak bu hedeflere ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="a6fec-243">Hedefler</span><span class="sxs-lookup"><span data-stu-id="a6fec-243">Goals</span></span>

<span data-ttu-id="a6fec-244">Bu gözden geçirmenin amacı, Azure Kapsayıcı Hizmeti'nde Windows Kapsayıcı tabanlı bir uygulamayı Kubernetes'e *(K8*olarak da adlandırılır) nasıl dağıtılamayı öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="a6fec-245">Kubernetes'e sıfırdan dağıtmak iki aşamalı bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="a6fec-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="a6fec-246">Azure Kapsayıcı Hizmetine bir Kubernetes kümesi dağıtın.</span><span class="sxs-lookup"><span data-stu-id="a6fec-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="a6fec-247">Uygulamayı ve ilgili kaynakları Kubernetes kümesine dağıtın.</span><span class="sxs-lookup"><span data-stu-id="a6fec-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="a6fec-248">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="a6fec-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="a6fec-249">Senaryo A: Bir dev ortamdan doğrudan bir Kubernetes kümesine dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Geliştirme ortamından doğrudan bir Kubernetes kümesine dağıtın](./media/image5-7.png)

<span data-ttu-id="a6fec-251">**Şekil 5-7.**</span><span class="sxs-lookup"><span data-stu-id="a6fec-251">**Figure 5-7.**</span></span> <span data-ttu-id="a6fec-252">Geliştirme ortamından doğrudan bir Kubernetes kümesine dağıtın</span><span class="sxs-lookup"><span data-stu-id="a6fec-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="a6fec-253">Senaryo B: Azure DevOps Hizmetlerinde CI/CD ardışık hatlarından bir Kubernetes kümesine dağıtın</span><span class="sxs-lookup"><span data-stu-id="a6fec-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Hizmetleri'ndeki CI/CD ardışık hatlarından Bir Kubernetes kümesine dağıtın](./media/image5-8.png)

<span data-ttu-id="a6fec-255">**Şekil 5-8.**</span><span class="sxs-lookup"><span data-stu-id="a6fec-255">**Figure 5-8.**</span></span> <span data-ttu-id="a6fec-256">Azure DevOps Hizmetleri'ndeki CI/CD ardışık hatlarından Bir Kubernetes kümesine dağıtın</span><span class="sxs-lookup"><span data-stu-id="a6fec-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="a6fec-257">Yararları</span><span class="sxs-lookup"><span data-stu-id="a6fec-257">Benefits</span></span>

<span data-ttu-id="a6fec-258">Kubernetes'teki bir kümeye dağıtımın birçok faydası vardır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="a6fec-259">En büyük yararı, kullanmak istediğiniz kapsayıcı örneklerinin sayısına (varolan düğümlerde iç ölçeklenebilirlik) ve kümedeki düğüm veya VM sayısına (kümenin küresel ölçeklenebilirliği) göre uygulamayı ölçeklendirebileceğiniz üretime hazır bir ortam elde edeyim.</span><span class="sxs-lookup"><span data-stu-id="a6fec-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="a6fec-260">Azure Kapsayıcı Hizmeti, azure için özel olarak popüler açık kaynak araçlarını ve teknolojilerini optimize eder.</span><span class="sxs-lookup"><span data-stu-id="a6fec-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="a6fec-261">Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan açık bir çözüm elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6fec-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="a6fec-262">Boyutu, ana bilgisayar sayısını ve orkestratör araçları-Konteyner Hizmeti diğer her şeyi işler seçin.</span><span class="sxs-lookup"><span data-stu-id="a6fec-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="a6fec-263">Kubernetes ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten, aşağıdaki yetenekleri kolaylaştıran konteyner merkezli bir altyapı planlamaya kadar ilerleyebilirler:</span><span class="sxs-lookup"><span data-stu-id="a6fec-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="a6fec-264">Birden fazla kapsayıcıya dayalı uygulamalar</span><span class="sxs-lookup"><span data-stu-id="a6fec-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="a6fec-265">Kapsayıcı örneklerini çoğaltma ve yatay otomatik ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="a6fec-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="a6fec-266">Adlandırma ve keşfetme (örneğin, dahili DNS)</span><span class="sxs-lookup"><span data-stu-id="a6fec-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="a6fec-267">Dengeleme yükleri</span><span class="sxs-lookup"><span data-stu-id="a6fec-267">Balancing loads</span></span>

- <span data-ttu-id="a6fec-268">Güncele kaydetme</span><span class="sxs-lookup"><span data-stu-id="a6fec-268">Rolling updates</span></span>

- <span data-ttu-id="a6fec-269">Sırları dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-269">Distributing secrets</span></span>

- <span data-ttu-id="a6fec-270">Uygulama sağlık kontrolleri</span><span class="sxs-lookup"><span data-stu-id="a6fec-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="a6fec-271">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a6fec-271">Next steps</span></span>

<span data-ttu-id="a6fec-272">Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="a6fec-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="a6fec-273">Walkthrough 6: Windows Kapsayıcılar tabanlı uygulamalarınızı Kapsayıcılar için Azure Uygulama Hizmetine dağıtma</span><span class="sxs-lookup"><span data-stu-id="a6fec-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="a6fec-274">Teknik yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="a6fec-274">Technical walkthrough availability</span></span>

<span data-ttu-id="a6fec-275">Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="a6fec-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="a6fec-276">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6fec-276">Overview</span></span>

<span data-ttu-id="a6fec-277">Windows Kapsayıcıları'nı kullanan basit bir kapsayıcı uygulaması, Kapsayıcılar için Azure Uygulama Hizmeti'ne kolayca dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="a6fec-278">Bu, çoğu Windows Kapsayıcı tabanlı uygulamalar için önerilen yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="a6fec-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="a6fec-279">Hedefler</span><span class="sxs-lookup"><span data-stu-id="a6fec-279">Goals</span></span>

<span data-ttu-id="a6fec-280">Bu gözden geçirmenin amacı, bir kayıt defterinden (Docker Hub veya Azure Kapsayıcı Kayıt Defteri) Kapsayıcılar için Azure Uygulama Hizmetine Windows Kapsayıcı tabanlı bir uygulamayı nasıl dağıtılamayı öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="a6fec-281">Senaryo</span><span class="sxs-lookup"><span data-stu-id="a6fec-281">Scenario</span></span>

![Kapsayıcılar için Azure Uygulama Hizmetine Windows Kapsayıcı tabanlı uygulamayı dağıtma](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="a6fec-283">Yararları</span><span class="sxs-lookup"><span data-stu-id="a6fec-283">Benefits</span></span>

<span data-ttu-id="a6fec-284">Kapsayıcılar için Azure Uygulama Hizmetine dağıtmak, Azure Uygulama Hizmeti'nin PaaS avantajlarıyla eşleştirilmiş kapsayıcıların avantajlarını sunar.</span><span class="sxs-lookup"><span data-stu-id="a6fec-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="a6fec-285">Uygulama hizmeti hem dikey hem de yatay olarak kolayca ölçeklenebilir ve değişen talepleri karşılamak üzere otomatik ölçeklendirilecek şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="a6fec-286">Güncelleştirmeler sıfır kapalı kalma süresi yle gerçekleştirilebilir ve bir kayıt defterinden sürekli dağıtım yapılandırması da kolayca yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6fec-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a6fec-287">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a6fec-287">Next steps</span></span>

<span data-ttu-id="a6fec-288">Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="a6fec-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="a6fec-289">[Önceki](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [Sonraki](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="a6fec-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
