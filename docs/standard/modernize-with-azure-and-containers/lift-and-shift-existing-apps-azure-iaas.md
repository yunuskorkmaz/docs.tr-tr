---
title: Kaldırma ve var olan .NET uygulamalarını Azure Iaas (bulut altyapısını kullanıma hazır) için kaydırma
description: Azure Bulutu ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 0f9ff19c8e346560960a09d3b7c52976c478f2f3
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612881"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a><span data-ttu-id="3204f-103">Kaldırma ve var olan .NET uygulamalarını Azure Iaas (bulut altyapısını kullanıma hazır) için kaydırma</span><span class="sxs-lookup"><span data-stu-id="3204f-103">Lift and shift existing .NET apps to Azure IaaS (Cloud Infrastructure-Ready)</span></span>

> <span data-ttu-id="3204f-104">İşleme: Şirket içi yatırım ve donanım ve Bakım ağ toplam maliyetini azaltmak için ilk adım olarak, yalnızca mevcut uygulamalarınızı bulutta barındırma.</span><span class="sxs-lookup"><span data-stu-id="3204f-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="3204f-105">İçine alma önce *nasıl* mevcut uygulamalarınızı Azure altyapısı (ıaas) platformu olarak geçirmek için nedenlerini analiz önemlidir *neden* doğrudan Iaas'ye geçirin istiyorsunuz Azure'da.</span><span class="sxs-lookup"><span data-stu-id="3204f-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="3204f-106">Bu modernizasyonu olgunluk düzeyinde temelde Vm'leri, şirket içi altyapınızı kullanmaya devam etme niyetiniz yerine bulutta kullanmaya başlamak için bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="3204f-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="3204f-107">Analiz etmek için başka bir nokta *neden* yalnızca Azure yönetilen Hizmetleri daha gelişmiş eklemek yerine, saf Iaas bulutuna geçirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3204f-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="3204f-108">Hangi durumlarda olabilir belirlemek Iaas ilk başta gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3204f-108">Determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="3204f-109">Şekil 2-1, bulut altyapısını kullanıma hazır uygulamalar modernizasyonu olgunluk Düzeyler halinde yerleştirir:</span><span class="sxs-lookup"><span data-stu-id="3204f-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![Bulut altyapısını kullanıma hazır uygulamalar konumlandırma](./media/image2-1.png)

> <span data-ttu-id="3204f-111">**Şekil 2-1.**</span><span class="sxs-lookup"><span data-stu-id="3204f-111">**Figure 2-1.**</span></span> <span data-ttu-id="3204f-112">Bulut altyapısını kullanıma hazır uygulamalar konumlandırma</span><span class="sxs-lookup"><span data-stu-id="3204f-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="3204f-113">Neden Azure Iaas mevcut .NET web uygulamaları geçirme</span><span class="sxs-lookup"><span data-stu-id="3204f-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="3204f-114">Temel nedeni bile, ilk bir Iaas düzeyinde buluta geçirin, maliyet indirimleri elde etmektir.</span><span class="sxs-lookup"><span data-stu-id="3204f-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="3204f-115">Daha fazla yönetilen altyapı Hizmetleri'ni kullanarak, kuruluşunuzun Donanım bakımı, sunucu veya VM sağlama ve dağıtım ve altyapı yönetimi, yatırım düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3204f-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="3204f-116">Uygulamalarınızı buluta geçmeye karar yaptıktan sonra neden, Iaas, PaaS yalnızca olduğu gibi daha gelişmiş seçenekler yerine Iaas ortamı tercih edebileceğiniz temel nedeni daha tanıdık gelecektir.</span><span class="sxs-lookup"><span data-stu-id="3204f-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="3204f-117">Geçerli için benzer bir ortama taşıma, bir alt buluta giden en hızlı yol yapan öğrenme, şirket içi ortamı sunar.</span><span class="sxs-lookup"><span data-stu-id="3204f-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="3204f-118">Ancak, buluta giden en hızlı yol almak, bulutta çalışan uygulamalarınızın sahip gelen en çok faydayı elde anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="3204f-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="3204f-119">Herhangi bir kuruluştaki bir buluta geçiş zaten sunulan bulut için iyileştirilmiş hem de bulutta yerel olgunluk düzeylerinde sağladığı en önemli avantajları konusunda bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3204f-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud-Optimized and Cloud-Native maturity levels.</span></span>

<span data-ttu-id="3204f-120">Ayrıca dikkati uygulamaları modernize etme ve bulutta bile ıaas'de zaten çalışırken gelecekte yeniden oluşturma daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="3204f-120">It also has become evident that applications are easier to modernize and rearchitect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="3204f-121">Uygulama veri geçişi zaten kazanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3204f-121">Application data migration has already been achieved.</span></span> <span data-ttu-id="3204f-122">Ayrıca, kuruluşunuz bulutta çalışmak için gerekli becerileri kısalttılar ve bir "bulut kültürde." işletim için shift yapılan</span><span class="sxs-lookup"><span data-stu-id="3204f-122">Also, your organization will have gained skills required for working in the cloud and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="3204f-123">PaaS için yerine Iaas geçirmek ne zaman</span><span class="sxs-lookup"><span data-stu-id="3204f-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="3204f-124">Sonraki bölümlerde, PaaS platformları ve Hizmetleri çoğunlukla göre bulut için iyileştirilmiş uygulamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3204f-124">The next sections discuss Cloud-Optimized applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="3204f-125">Bu uygulamaları buluta geçirme gelen birçok avantaj sağlar.</span><span class="sxs-lookup"><span data-stu-id="3204f-125">These apps give you the most benefits from migrating to the cloud.</span></span> 

<span data-ttu-id="3204f-126">Amacınız yalnızca mevcut uygulamalarınızı buluta taşımak için ise, ilk olarak, Azure App Service'te çalıştırılacak değişikliği gerektirmez, mevcut uygulamaları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3204f-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that would not require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="3204f-127">Bu uygulamalar için ilk aday olmalıdır Bulutla optimize edilmiş.</span><span class="sxs-lookup"><span data-stu-id="3204f-127">These apps should be the first candidates for Cloud-Optimized.</span></span> 

<span data-ttu-id="3204f-128">App Service veya Azure Service Fabric gibi düzenleyicilerle geçirme gibi bu basit düz vm'lere (Iaas) sonra uygulamalar için yine de Windows kapsayıcıları ve PaaS taşıyamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3204f-128">Then, for the apps that still cannot move to Windows Containers and PaaS such as App Service or orchestrators like Azure Service Fabric, migrate those to simple plain VMs (IaaS).</span></span> 

<span data-ttu-id="3204f-129">Ancak, doğru şekilde yapılandırma, güvenlik altına alma ve Vm'leri koruma çok daha fazla zaman ve IT uzmanlığı Azure PaaS hizmetleri kullanmaya kıyasla gerektirdiğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="3204f-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="3204f-130">Azure sanal makineleri düşünüyorsanız, düzeltme eki uygulama, güncelleştirme ve VM ortamınızı yönetmek için gereken sürekli bir bakım çabası hesaba katması emin olun.</span><span class="sxs-lookup"><span data-stu-id="3204f-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="3204f-131">Azure sanal makineleri Iaas olur.</span><span class="sxs-lookup"><span data-stu-id="3204f-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="3204f-132">Analiz ve mevcut uygulamalarınızı azure'a geçirmek için Azure Geçişi'ı kullanın</span><span class="sxs-lookup"><span data-stu-id="3204f-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="3204f-133">Buluta geçmek zor olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="3204f-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="3204f-134">Ancak, çoğu kuruluş - ortam ve uygulamaları, iş yüklerini ve verileri birbirine sıkı derin görünürlük elde etmek için'da başlamak uğraşır.</span><span class="sxs-lookup"><span data-stu-id="3204f-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="3204f-135">Bu görünürlük ileriye doğru yolu planlamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="3204f-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="3204f-136">Ne başarılı bir geçiş için gereken ilgili ayrıntılı bilgiler, kuruluşunuzdaki doğru konuşmalar sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="3204f-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="3204f-137">Olası maliyet avantajları, hakkında yeterli bilmiyorsanız veya iş yükleri yalnızca lift-and-shift ile taşıma verebilir veya başarıyla geçirmek için önemli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3204f-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="3204f-138">Hiçbir elmas pek çok kuruluş istemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="3204f-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="3204f-139">[Azure geçişi](https://aka.ms/azuremigrate) Kılavuzu, Öngörüler ve Azure'a geçiş ile yardımcı olmak için gereken mekanizmalar sağlayan yeni bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="3204f-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="3204f-140">Azure geçişi sağlar:</span><span class="sxs-lookup"><span data-stu-id="3204f-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="3204f-141">Keşif ve değerlendirme şirket içi sanal makineler için</span><span class="sxs-lookup"><span data-stu-id="3204f-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="3204f-142">Yüksek güvenle bulma çok katmanlı uygulamaları için yerleşik bağımlılık eşlemesi</span><span class="sxs-lookup"><span data-stu-id="3204f-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="3204f-143">Azure sanal makinelerine akıllı doğru boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="3204f-143">Intelligent right sizing to Azure virtual machines</span></span>

- <span data-ttu-id="3204f-144">Uyumluluk kuralları düzelterek olası sorunlar için ile raporlama</span><span class="sxs-lookup"><span data-stu-id="3204f-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="3204f-145">Veritabanı keşfi ve geçişi için Azure veritabanı yönetim hizmeti ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="3204f-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="3204f-146">Azure geçişi, iş yüklerinizi iş olabildiğince az etkileyerek geçirme ve Azure'da beklendiği gibi çalışmazsa olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3204f-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="3204f-147">Doğru Araçlar ve rehberlik ile en fazla kritik performans işlemlerini sırasında yatırım getirisini elde edebileceğiniz ve güvenilirlik ihtiyaçlarının karşılandığından.</span><span class="sxs-lookup"><span data-stu-id="3204f-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="3204f-148">Şekil 2-2, Azure geçişi tarafından gerçekleştirilen tüm sunucu ve uygulama bağlantıları için yerleşik bağımlılık eşlemesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3204f-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![Bulut altyapısını kullanıma hazır uygulamalar konumlandırma](./media/image2-2.png)

> <span data-ttu-id="3204f-150">**Şekil 2-2.**</span><span class="sxs-lookup"><span data-stu-id="3204f-150">**Figure 2-2.**</span></span> <span data-ttu-id="3204f-151">Bulut altyapısını kullanıma hazır uygulamalar konumlandırma</span><span class="sxs-lookup"><span data-stu-id="3204f-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="3204f-152">Mevcut Vm'lerinizi Azure Vm'lerine geçirmek için Azure Site RECOVERY'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="3204f-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="3204f-153">Uçtan uca bir parçası olarak [Azure geçişi](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) kolayca web uygulamalarınızı Azure sanal makineleri geçirmek için kullanabileceğiniz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="3204f-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="3204f-154">Şirket içi Vm'leri ve fiziksel sunucuları Azure'a çoğaltmak için veya bunları bir ikincil şirket içi konuma çoğaltmak için Site RECOVERY'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3204f-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="3204f-155">Bir şirket içi desteklenen bir Azure sanal makinesinde çalıştırılan bir iş yükü bile çoğaltabilirsiniz *Hyper-V* VM, bir *VMware* VM veya bir Windows veya Linux fiziksel sunucusu üzerinde.</span><span class="sxs-lookup"><span data-stu-id="3204f-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="3204f-156">Azure'a çoğaltma, maliyet ve ikincil bir veri merkezi kullanmanın karmaşıklığını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3204f-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="3204f-157">Site kurtarma kısmen özellikle karma ortamlar için de yapılan şirket içinde ve kısmen üzerinde Azure.</span><span class="sxs-lookup"><span data-stu-id="3204f-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="3204f-158">Site Recovery Vm'lerde çalışan uygulamalarınızı tutarak iş sürekliliği sağlamaya yardımcı olur ve şirket içi fiziksel sunucuları kullanılabilir bir site dışı kalırsa.</span><span class="sxs-lookup"><span data-stu-id="3204f-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="3204f-159">Bu birincil site kullanılamıyorsa, ikincil bir konumda kullanılabilir kalmasını Vm'lerde ve fiziksel sunucularda çalışan iş yükleri çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="3204f-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="3204f-160">Bu, başladığında birincil site ile yeniden çalışan iş yüklerini kurtarır.</span><span class="sxs-lookup"><span data-stu-id="3204f-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="3204f-161">Şekil 2-3, Azure Site Recovery kullanarak birden çok sanal makine geçişi yürütülmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3204f-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![Bulut altyapısını kullanıma hazır uygulamalar konumlandırma](./media/image2-3.png)

> <span data-ttu-id="3204f-163">**Şekil 2-3.**</span><span class="sxs-lookup"><span data-stu-id="3204f-163">**Figure 2-3.**</span></span> <span data-ttu-id="3204f-164">Bulut altyapısını kullanıma hazır uygulamalar konumlandırma</span><span class="sxs-lookup"><span data-stu-id="3204f-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3204f-165">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3204f-165">Additional resources</span></span>

- <span data-ttu-id="3204f-166">**Azure veri geçişi**</span><span class="sxs-lookup"><span data-stu-id="3204f-166">**Azure Migrate Datasheet**</span></span>

    <https://aka.ms/azuremigration\_datasheet>

- <span data-ttu-id="3204f-167">**Azure geçişi**</span><span class="sxs-lookup"><span data-stu-id="3204f-167">**Azure Migrate**</span></span>

    <https://aka.ms/azuremigrate>

- <span data-ttu-id="3204f-168">**Azure geçiş Merkezi**</span><span class="sxs-lookup"><span data-stu-id="3204f-168">**Azure migration center**</span></span>

    <https://azure.microsoft.com/migration/>

- <span data-ttu-id="3204f-169">**Site Recovery ile azure'a geçirme**</span><span class="sxs-lookup"><span data-stu-id="3204f-169">**Migrate to Azure with Site Recovery**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- <span data-ttu-id="3204f-170">**Azure Site Recovery hizmetine genel bakış**</span><span class="sxs-lookup"><span data-stu-id="3204f-170">**Azure Site Recovery service overview**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- <span data-ttu-id="3204f-171">**Azure VM'ler için AWS VM geçirme**</span><span class="sxs-lookup"><span data-stu-id="3204f-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
><span data-ttu-id="3204f-172">[Önceki](index.md)
>[İleri](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="3204f-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span>
