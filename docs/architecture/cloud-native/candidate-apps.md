---
title: Bulut yerel için aday uygulamalar
description: Bulut ayarı olan bir yaklaşımdan hangi tür uygulamaların yararlandığını öğrenin
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805616"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="26ae7-103">Bulut yerel için aday uygulamalar</span><span class="sxs-lookup"><span data-stu-id="26ae7-103">Candidate apps for cloud native</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="26ae7-104">Portföyünüzdeki uygulamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="26ae7-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="26ae7-105">Kaç tanesi bulut-yerel mimari için uygun?</span><span class="sxs-lookup"><span data-stu-id="26ae7-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="26ae7-106">Bunların tümü?</span><span class="sxs-lookup"><span data-stu-id="26ae7-106">All of them?</span></span> <span data-ttu-id="26ae7-107">Belki biraz?</span><span class="sxs-lookup"><span data-stu-id="26ae7-107">Perhaps some?</span></span>

<span data-ttu-id="26ae7-108">Maliyet/fayda çözümlemesi uygulayarak, çoğu bulut yerel olması için gerekli ağır fiyat etiketini desteklemez iyi bir şans var.</span><span class="sxs-lookup"><span data-stu-id="26ae7-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="26ae7-109">Bulut yerel olmanın maliyeti, uygulamanın iş değerini çok aşar.</span><span class="sxs-lookup"><span data-stu-id="26ae7-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="26ae7-110">Bulut yerel için ne tür bir uygulama adayı olabilir?</span><span class="sxs-lookup"><span data-stu-id="26ae7-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="26ae7-111">Sürekli iş yetenekleri / özellikleri geliştirmek için gereken büyük, stratejik kurumsal sistem</span><span class="sxs-lookup"><span data-stu-id="26ae7-111">A large, strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="26ae7-112">Yüksek serbest bırakma hızı gerektiren bir uygulama - yüksek güven ile</span><span class="sxs-lookup"><span data-stu-id="26ae7-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="26ae7-113">Tüm sistemin tam olarak yeniden dağıtılması *olmadan* tek tek özelliklerin serbest bırakılması gereken bir sistem</span><span class="sxs-lookup"><span data-stu-id="26ae7-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="26ae7-114">Farklı teknoloji yığınlarında uzman ekipler tarafından geliştirilen bir uygulama</span><span class="sxs-lookup"><span data-stu-id="26ae7-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="26ae7-115">Bağımsız ölçeklendirmesi gereken bileşenlere sahip bir uygulama</span><span class="sxs-lookup"><span data-stu-id="26ae7-115">An application with components that must scale independently</span></span>

<span data-ttu-id="26ae7-116">Bir de eski sistemler var.</span><span class="sxs-lookup"><span data-stu-id="26ae7-116">Then there are legacy systems.</span></span> <span data-ttu-id="26ae7-117">Hepimiz yeni uygulamalar oluşturmak isterken, genellikle işletme için kritik öneme sahip eski iş yüklerini modernize etmekle yükümlüyuz.</span><span class="sxs-lookup"><span data-stu-id="26ae7-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="26ae7-118">Zaman içinde, eski bir uygulama mikro hizmetlere ayrıştırılabilir, konteynerlenebilir ve sonuçta bulut-yerel mimariye "yeniden platformlaştırılabilir".</span><span class="sxs-lookup"><span data-stu-id="26ae7-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="26ae7-119">Eski uygulamaları modernize etme</span><span class="sxs-lookup"><span data-stu-id="26ae7-119">Modernizing legacy apps</span></span>

<span data-ttu-id="26ae7-120">Ücretsiz Microsoft e-kitap [Azure bulutu ve Windows Kapsayıcıları ile mevcut .NET uygulamalarını](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) modernleştirin, şirket içi iş yüklerini buluta geçirmek için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="26ae7-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="26ae7-121">Şekil 1-10, eski uygulamaları modernize etmek için tek, tek boyutlu bir strateji olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="26ae7-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![Eski iş yüklerini geçirme stratejileri](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="26ae7-123">**Şekil 1-10**.</span><span class="sxs-lookup"><span data-stu-id="26ae7-123">**Figure 1-10**.</span></span> <span data-ttu-id="26ae7-124">Eski iş yüklerini geçirme stratejileri</span><span class="sxs-lookup"><span data-stu-id="26ae7-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="26ae7-125">Kritik olmayan monolitik uygulamalar büyük ölçüde hızlı kaldırma ve kaydırma[(Bulut Altyapısına Hazır)](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)geçişinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="26ae7-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="26ae7-126">Burada, şirket içi iş yükü, herhangi bir değişiklik olmaksızın bulut tabanlı bir VM'ye yeniden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="26ae7-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="26ae7-127">Bu yaklaşım, [IaaS (Hizmet Olarak Altyapı) modelini](https://azure.microsoft.com/overview/what-is-iaas/)kullanır.</span><span class="sxs-lookup"><span data-stu-id="26ae7-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="26ae7-128">Azure, böyle bir hareketi kolaylaştırmak için [Azure Geçiş,](https://azure.microsoft.com/services/azure-migrate/) [Azure Site Kurtarma](https://azure.microsoft.com/services/site-recovery/)ve Azure Veritabanı Geçiş [Hizmeti](https://azure.microsoft.com/campaigns/database-migration/) gibi çeşitli araçları içerir.</span><span class="sxs-lookup"><span data-stu-id="26ae7-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="26ae7-129">Bu strateji bazı maliyet tasarrufları sağlayabilir ken, bu tür uygulamalar genellikle bulut bilgi işlemin avantajlarının kilidini açmak ve bunlardan yararlanmak için tasarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="26ae7-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="26ae7-130">İşletme için kritik öneme sahip monolitik uygulamalar, gelişmiş kaldırma ve kaydırma *(Bulut Optimize Edilmiş)* geçişinden çoğu zaman yararlanır.</span><span class="sxs-lookup"><span data-stu-id="26ae7-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="26ae7-131">Bu yaklaşım, uygulamanın temel mimarisini değiştirmeden anahtar bulut hizmetlerini etkinleştiren dağıtım optimizasyonlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="26ae7-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="26ae7-132">Örneğin, uygulamayı [kapsayıcı hale](https://docs.microsoft.com/virtualization/windowscontainers/about/) getirebilir ve bu kitapta daha sonra tartışılan [Azure Kubernetes Hizmetleri](https://azure.microsoft.com/services/kubernetes-service/)gibi bir kapsayıcı orkestratöre dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26ae7-132">For example, you might [containerize](https://docs.microsoft.com/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="26ae7-133">Buluta girdikten sonra, uygulama veritabanları, ileti kuyrukları, izleme ve dağıtılmış önbelleğe alma gibi diğer bulut hizmetlerini tüketebilir.</span><span class="sxs-lookup"><span data-stu-id="26ae7-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="26ae7-134">Son olarak, stratejik kurumsal işlevleri gerçekleştiren yekpare uygulamalar, bu kitabın konusu olan *Bulut-Yerel* yaklaşımından en iyi şekilde yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="26ae7-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="26ae7-135">Bu yaklaşım çeviklik ve hız sağlar.</span><span class="sxs-lookup"><span data-stu-id="26ae7-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="26ae7-136">Ancak, yeniden platformlama, yeniden architectyon ve kod yeniden yazma bir maliyetle gelir.</span><span class="sxs-lookup"><span data-stu-id="26ae7-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="26ae7-137">Siz ve ekibiniz bulut ait bir yaklaşımın uygun olduğuna inanıyorsanız, kararı kuruluşunuzla birlikte mantıklı hale getirmek size yakıştırılır.</span><span class="sxs-lookup"><span data-stu-id="26ae7-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="26ae7-138">Bulut-yerel bir yaklaşımın çözeceği iş sorunu tam olarak nedir?</span><span class="sxs-lookup"><span data-stu-id="26ae7-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="26ae7-139">İş ihtiyaçlarıyla nasıl uyumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="26ae7-139">How would it align with business needs?</span></span>

- <span data-ttu-id="26ae7-140">Artan güven ile özellikleri hızlı bültenleri?</span><span class="sxs-lookup"><span data-stu-id="26ae7-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="26ae7-141">İnce taneli ölçeklenebilirlik - kaynakların daha verimli kullanımı?</span><span class="sxs-lookup"><span data-stu-id="26ae7-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="26ae7-142">Geliştirilmiş sistem esnekliği?</span><span class="sxs-lookup"><span data-stu-id="26ae7-142">Improved system resiliency?</span></span>

- <span data-ttu-id="26ae7-143">Geliştirilmiş sistem performansı?</span><span class="sxs-lookup"><span data-stu-id="26ae7-143">Improved system performance?</span></span>

- <span data-ttu-id="26ae7-144">Operasyonlarda daha fazla görünürlük mü?</span><span class="sxs-lookup"><span data-stu-id="26ae7-144">More visibility into operations?</span></span>

- <span data-ttu-id="26ae7-145">İş için en iyi araca ulaşmak için geliştirme platformlarını ve veri depolarını harmanlamak mı?</span><span class="sxs-lookup"><span data-stu-id="26ae7-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="26ae7-146">Geleceğe dönük uygulama yatırımı mı?</span><span class="sxs-lookup"><span data-stu-id="26ae7-146">Future-proof application investment?</span></span>

<span data-ttu-id="26ae7-147">Doğru geçiş stratejisi, kuruluş önceliklerine ve hedeflediğiniz sistemlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="26ae7-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="26ae7-148">Birçokları için, yekpare bir uygulamayı buluta optimize etmek veya bir N-Tier uygulamasına kaba taneli hizmetler eklemek daha uygun maliyetli olabilir.</span><span class="sxs-lookup"><span data-stu-id="26ae7-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="26ae7-149">Bu gibi durumlarda, Azure Uygulama Hizmeti tarafından sunulanlar gibi bulut PaaS özelliklerinden tam olarak yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26ae7-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="26ae7-150">Özet</span><span class="sxs-lookup"><span data-stu-id="26ae7-150">Summary</span></span>

<span data-ttu-id="26ae7-151">Bu bölümde, bulut-yerli bilgi işlem tanıttı.</span><span class="sxs-lookup"><span data-stu-id="26ae7-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="26ae7-152">Bulut ayarı yapan bir uygulamayı yönlendiren temel özelliklerle birlikte bir tanım sağladık.</span><span class="sxs-lookup"><span data-stu-id="26ae7-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="26ae7-153">Bu yatırımı ve çabayı haklı çıkaracak uygulama türlerine baktık.</span><span class="sxs-lookup"><span data-stu-id="26ae7-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="26ae7-154">Arkadaki girişle birlikte, şimdi bulut anına çok daha ayrıntılı bir bakış atıyoruz.</span><span class="sxs-lookup"><span data-stu-id="26ae7-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="26ae7-155">Başvurular</span><span class="sxs-lookup"><span data-stu-id="26ae7-155">References</span></span>

- [<span data-ttu-id="26ae7-156">Cloud Native Computing Foundation</span><span class="sxs-lookup"><span data-stu-id="26ae7-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="26ae7-157">.NET Microservices: Containerized .NET uygulamaları için mimari</span><span class="sxs-lookup"><span data-stu-id="26ae7-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="26ae7-158">Azure bulutu ve Windows Kapsayıcıları ile mevcut .NET uygulamalarını modernize edin</span><span class="sxs-lookup"><span data-stu-id="26ae7-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="26ae7-159">Cornelia Davis tarafından Cloud Yerli Desenler</span><span class="sxs-lookup"><span data-stu-id="26ae7-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="26ae7-160">On iki Faktörlü Uygulamanın Ötesinde</span><span class="sxs-lookup"><span data-stu-id="26ae7-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="26ae7-161">Kod Olarak Altyapı Nedir</span><span class="sxs-lookup"><span data-stu-id="26ae7-161">What is Infrastructure as Code</span></span>](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="26ae7-162">Uber Engineering's Micro Deploy: Günlük Güvenle Dağıtım</span><span class="sxs-lookup"><span data-stu-id="26ae7-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="26ae7-163">Netflix Kodu Nasıl Dağır</span><span class="sxs-lookup"><span data-stu-id="26ae7-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="26ae7-164">WeChat Microservices Ölçekleme için Aşırı Yük Kontrolü</span><span class="sxs-lookup"><span data-stu-id="26ae7-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="26ae7-165">[Önceki](definition.md)
>[Sonraki](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="26ae7-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
