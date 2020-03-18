---
title: Varolan .NET uygulamalarını Azure IaaS'a (Bulut Altyapısına Hazır) kaldırın ve kaydırın
description: Azure Bulut ve Windows Kapsayıcıları ile Varolan .NET Uygulamalarını Modernize Edin.
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089629"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a><span data-ttu-id="5a584-103">Varolan .NET uygulamalarını Azure IaaS'a (Bulut Altyapısına Hazır) kaldırın ve kaydırın</span><span class="sxs-lookup"><span data-stu-id="5a584-103">Lift and shift existing .NET apps to Azure IaaS (Cloud Infrastructure-Ready)</span></span>

> <span data-ttu-id="5a584-104">Vizyon: Şirket içi yatırımınızı ve toplam donanım ve ağ bakımı maliyetinizi azaltmak için ilk adım olarak, buluttaki mevcut uygulamalarınızı yeniden barındırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="5a584-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="5a584-105">Mevcut uygulamalarınızı hizmet (IaaS) platformu olarak Azure altyapısına *geçirmeden* önce, Azure'da doğrudan IaaS'a geçiş yapmak isteme *nedenleri* nizi çözümlemeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5a584-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="5a584-106">Bu modernizasyon olgunluk düzeyindeki senaryo, mevcut şirket içi altyapınızı kullanmaya devam etmek yerine bulutta VM'ler kullanmaya başlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5a584-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="5a584-107">Analiz etmek için başka bir nokta, *azure'da* daha gelişmiş yönetilen hizmetler eklemek yerine neden saf IaaS bulutuna geçiş yapmak isteyebileceğinizdir.</span><span class="sxs-lookup"><span data-stu-id="5a584-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="5a584-108">İlk etapta hangi durumlarda IaaS gerektirebileceğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="5a584-108">Determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="5a584-109">Şekil 2-1 pozisyonları Bulut Altyapısı-Modernizasyon olgunluk düzeylerinde hazır uygulamalar:</span><span class="sxs-lookup"><span data-stu-id="5a584-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![Bulut Altyapılarını Konumlandırma-Hazır uygulamaları](./media/image2-1.png)

<span data-ttu-id="5a584-111">**Şekil 2-1.**</span><span class="sxs-lookup"><span data-stu-id="5a584-111">**Figure 2-1.**</span></span> <span data-ttu-id="5a584-112">Bulut Altyapılarını Konumlandırma-Hazır uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5a584-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="5a584-113">Neden varolan .NET web uygulamalarını Azure IaaS'a geçirin?</span><span class="sxs-lookup"><span data-stu-id="5a584-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="5a584-114">Buluta geçişin temel nedeni, ilk IaaS düzeyinde bile, maliyet indirimleri elde etmektir.</span><span class="sxs-lookup"><span data-stu-id="5a584-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="5a584-115">Kuruluşunuz daha yönetilen altyapı hizmetlerini kullanarak donanım bakımı, sunucu veya VM sağlama ve dağıtım ve altyapı yönetimine yaptığı yatırımı düşürebilir.</span><span class="sxs-lookup"><span data-stu-id="5a584-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="5a584-116">Uygulamalarınızı buluta taşıma kararı aldıktan sonra, PaaS gibi daha gelişmiş seçenekler yerine IaaS'i seçmenizin temel nedeni, IaaS ortamının daha tanıdık olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5a584-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="5a584-117">Mevcut, şirket içi ortamınıza benzer bir ortama geçmek, onu buluta giden en hızlı yol yapan daha düşük bir öğrenme eğrisi sunar.</span><span class="sxs-lookup"><span data-stu-id="5a584-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="5a584-118">Ancak, buluta giden en hızlı yolu bulmak, uygulamalarınızın bulutta çalışmasını sağlamaktan en fazla faydayı sağlayacağınız anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="5a584-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="5a584-119">Herhangi bir kuruluş, daha önce tanıtılan Bulut Optimize edilmiş ve Bulut-Yerel olgunluk düzeylerinde bulut geçişinden en önemli avantajları elde eder.</span><span class="sxs-lookup"><span data-stu-id="5a584-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud-Optimized and Cloud-Native maturity levels.</span></span>

<span data-ttu-id="5a584-120">Ayrıca, uygulamaların gelecekte iaas'ta bile bulutta çalışırken modernizasyonu ve yeniden mimarlığını daha kolay hale geldiği de ortaya çıkmıştır.</span><span class="sxs-lookup"><span data-stu-id="5a584-120">It also has become evident that applications are easier to modernize and rearchitect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="5a584-121">Uygulama veri geçişi zaten elde edildi.</span><span class="sxs-lookup"><span data-stu-id="5a584-121">Application data migration has already been achieved.</span></span> <span data-ttu-id="5a584-122">Ayrıca, kuruluşunuz bulutta çalışmak için gerekli becerileri kazanmış ve bir "bulut kültüründe" çalışmaya geçiş yapmış olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5a584-122">Also, your organization will have gained skills required for working in the cloud and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="5a584-123">PaaS yerine IaaS'ye ne zaman göç edilebisisin</span><span class="sxs-lookup"><span data-stu-id="5a584-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="5a584-124">Sonraki bölümlerde çoğunlukla PaaS platformlarını ve hizmetlerini temel alan Bulut Tarafından Optimize Edilmiş uygulamalar tartışılır.</span><span class="sxs-lookup"><span data-stu-id="5a584-124">The next sections discuss Cloud-Optimized applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="5a584-125">Bu uygulamalar, buluta geçişten en çok faydayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a584-125">These apps give you the most benefits from migrating to the cloud.</span></span>

<span data-ttu-id="5a584-126">Amacınız yalnızca varolan uygulamaları buluta taşımaksa, öncelikle Azure Uygulama Hizmeti'nde çalıştırılmak için önemli değişiklikler gerektirmeyen varolan uygulamaları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5a584-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that would not require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="5a584-127">Bu uygulamalar, Bulut Için Optimize Edilmiş ilk adaylar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a584-127">These apps should be the first candidates for Cloud-Optimized.</span></span>

<span data-ttu-id="5a584-128">Ardından, Uygulama Hizmeti gibi Windows Kapsayıcıları ve PaaS'a veya Azure Kubernetes Hizmeti gibi orkestratörlere hala taşınamayan uygulamalar için, bunları basit düz VM'lere (IaaS) geçirin.</span><span class="sxs-lookup"><span data-stu-id="5a584-128">Then, for the apps that still cannot move to Windows Containers and PaaS such as App Service or orchestrators like Azure Kubernetes Service, migrate those to simple plain VMs (IaaS).</span></span>

<span data-ttu-id="5a584-129">Ancak, VM'leri doğru şekilde yapılandırmanın, güvence altına almanın ve korumanın, Azure'daki PaaS hizmetlerini kullanmaya kıyasla çok daha fazla zaman ve BT uzmanlığı gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5a584-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="5a584-130">Azure Sanal Makineleri düşünüyorsanız, VM ortamınızı yamamak, güncellemek ve yönetmek için gereken devam eden bakım çabasını dikkate aldığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5a584-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="5a584-131">Azure Sanal Makineler IaaS'dır.</span><span class="sxs-lookup"><span data-stu-id="5a584-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="5a584-132">Varolan uygulamalarınızı analiz etmek ve Azure'a geçirmek için Azure Geçiş'i kullanın</span><span class="sxs-lookup"><span data-stu-id="5a584-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="5a584-133">Buluta göç etmek zor olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="5a584-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="5a584-134">Ancak birçok kuruluş, çevreye ve uygulamalar, iş yükleri ve veriler arasındaki sıkı karşılıklı bağımlılıkları derinlemesine görmek için başlamak için mücadele eder.</span><span class="sxs-lookup"><span data-stu-id="5a584-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="5a584-135">Bu görünürlük olmadan, ileriye doğru yol planlamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a584-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="5a584-136">Başarılı bir geçiş için nelerin gerekli olduğu hakkında ayrıntılı bilgi olmadan, kuruluşunuz içinde doğru konuşmaları yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="5a584-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="5a584-137">Olası maliyet avantajları veya iş yüklerinin sadece kaldırma ve kaydırma veya başarılı bir şekilde geçiş yapmak için önemli bir yeniden çalışma gerektirip gerekmediği hakkında yeterli şey bilmiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="5a584-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="5a584-138">Pek çok kuruluşun tereddüt etmemesine şaşmamalı.</span><span class="sxs-lookup"><span data-stu-id="5a584-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="5a584-139">[Azure Geçiş,](https://aka.ms/azuremigrate) Azure'a geçişte size yardımcı olmak için gereken yönergeleri, öngörüleri ve mekanizmaları sağlayan yeni bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="5a584-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="5a584-140">Azure Geçiş sağlar:</span><span class="sxs-lookup"><span data-stu-id="5a584-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="5a584-141">Şirket içi sanal makineler için keşif ve değerlendirme</span><span class="sxs-lookup"><span data-stu-id="5a584-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="5a584-142">Çok katmanlı uygulamaların yüksek güven keşfi için dahili bağımlılık haritalama</span><span class="sxs-lookup"><span data-stu-id="5a584-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="5a584-143">Azure sanal makinelerine akıllı sağ boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="5a584-143">Intelligent right sizing to Azure virtual machines</span></span>

- <span data-ttu-id="5a584-144">Olası sorunları giderme yönergeleriile uyumluluk raporlaması</span><span class="sxs-lookup"><span data-stu-id="5a584-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="5a584-145">Veritabanı bulma ve geçiş için Azure Veritabanı Yönetim Hizmeti ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="5a584-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="5a584-146">Azure Geçiş, iş yüklerinizin işletmeye en az etkiyle geçirebileceğine ve Azure'da beklendiği gibi çalıştırılayabildiği konusunda size güven verir.</span><span class="sxs-lookup"><span data-stu-id="5a584-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="5a584-147">Doğru araçlar ve kılavuzla, kritik performans ve güvenilirlik gereksinimlerinin karşılandığına dair güvence verirken maksimum yatırım getirisi elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a584-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="5a584-148">Şekil 2-2, Azure Geçiş tarafından gerçekleştirilen tüm sunucu ve uygulama bağlantıları için yerleşik bağımlılık eşlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a584-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![Bulut Altyapılarını Konumlandırma-Hazır uygulamaları](./media/image2-2.png)

<span data-ttu-id="5a584-150">**Şekil 2-2.**</span><span class="sxs-lookup"><span data-stu-id="5a584-150">**Figure 2-2.**</span></span> <span data-ttu-id="5a584-151">Bulut Altyapılarını Konumlandırma-Hazır uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5a584-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="5a584-152">Mevcut VM'lerinizi Azure VM'lerine geçirmek için Azure Site Kurtarma'yı kullanın</span><span class="sxs-lookup"><span data-stu-id="5a584-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="5a584-153">Uçtan uca [Azure Geçiş'in](https://aka.ms/azuremigrate)bir parçası olarak, [Azure Site Kurtarma,](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) web uygulamalarınızı Azure'daki VM'lere kolayca geçirmek için kullanabileceğiniz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="5a584-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="5a584-154">Site Kurtarma'yı şirket içi VM'leri ve fiziksel sunucuları Azure'da çoğaltmak veya bunları ikincil bir şirket içi konuma çoğaltmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a584-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="5a584-155">Desteklenen bir Azure VM'de, şirket içi *Hyper-V* VM'de, *VMware* VM'de veya Windows veya Linux fiziksel sunucusunda çalışan bir iş yükünü bile çoğaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a584-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="5a584-156">Azure’a çoğaltma seçeneği, ikincil bir veri merkezi kullanmanın maliyetini ve karmaşıklığını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5a584-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="5a584-157">Site Kurtarma, kısmen şirket içi ve kısmen Azure'da olan karma ortamlar için de özel olarak hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5a584-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="5a584-158">Site Kurtarma, bir site çökerse, VM'lerde ve şirket içi fiziksel sunucularda çalışan uygulamalarınızı kullanılabilir durumda tutarak iş sürekliliğini sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5a584-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="5a584-159">Birincil site kullanılamıyorsa ikincil bir konumda kullanılabilir kalmaları için VM'lerde ve fiziksel sunucularda çalışan iş yüklerini çoğaltıyor.</span><span class="sxs-lookup"><span data-stu-id="5a584-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="5a584-160">Birincil site yeniden çalışmaya başladığında birincil sitede iş yüklerini kurtarır.</span><span class="sxs-lookup"><span data-stu-id="5a584-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="5a584-161">Şekil 2-3, Azure Site Kurtarma'yı kullanarak birden çok VM geçişinin gerçekleştirilimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a584-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![Bulut Altyapılarını Konumlandırma-Hazır uygulamaları](./media/image2-3.png)

<span data-ttu-id="5a584-163">**Şekil 2-3.**</span><span class="sxs-lookup"><span data-stu-id="5a584-163">**Figure 2-3.**</span></span> <span data-ttu-id="5a584-164">Bulut Altyapılarını Konumlandırma-Hazır uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5a584-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5a584-165">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5a584-165">Additional resources</span></span>

- <span data-ttu-id="5a584-166">**Azure Geçir Veri Sayfası**</span><span class="sxs-lookup"><span data-stu-id="5a584-166">**Azure Migrate Datasheet**</span></span>

    <https://aka.ms/azuremigration\_datasheet>

- <span data-ttu-id="5a584-167">**Azure Geçiş**</span><span class="sxs-lookup"><span data-stu-id="5a584-167">**Azure Migrate**</span></span>

    <https://aka.ms/azuremigrate>

- <span data-ttu-id="5a584-168">**Azure geçiş merkezi**</span><span class="sxs-lookup"><span data-stu-id="5a584-168">**Azure migration center**</span></span>

    <https://azure.microsoft.com/migration/>

- <span data-ttu-id="5a584-169">**Site Recovery ile Azure’a Geçiş**</span><span class="sxs-lookup"><span data-stu-id="5a584-169">**Migrate to Azure with Site Recovery**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- <span data-ttu-id="5a584-170">**Azure Site Kurtarma hizmetine genel bakış**</span><span class="sxs-lookup"><span data-stu-id="5a584-170">**Azure Site Recovery service overview**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- <span data-ttu-id="5a584-171">**AWS'deki VM'leri Azure VM'lere geçirme**</span><span class="sxs-lookup"><span data-stu-id="5a584-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
><span data-ttu-id="5a584-172">[Önceki](index.md)
>[Sonraki](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="5a584-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span> <!-- Next Chapter -->
