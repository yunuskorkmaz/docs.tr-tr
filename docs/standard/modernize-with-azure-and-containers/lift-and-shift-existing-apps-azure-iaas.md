---
title: Kaldırın ve mevcut uygulamalar Azure Iaas kaydırma
description: Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7922ad3a3cd5346f81008e1841a55b5e3663832
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="lift-and-shift-existing-apps-azure-iaas"></a><span data-ttu-id="9f04f-103">Kaldırın ve mevcut uygulamalar Azure Iaas kaydırma</span><span class="sxs-lookup"><span data-stu-id="9f04f-103">Lift and shift existing apps Azure IaaS</span></span>

> <span data-ttu-id="9f04f-104">Görme: şirket içi yatırım ve toplam maliyeti donanım azaltın ve yeniden barındırma bakım, ağ yalnızca mevcut uygulamalarınızı bulutta bir ilk adım.</span><span class="sxs-lookup"><span data-stu-id="9f04f-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="9f04f-105">İçine alma önce *nasıl* mevcut uygulamalarınızı Azure altyapı (ıaas) platformu olarak geçirmek için nedenleri çözümlemek önemli olduğunu *neden* doğrudan Iaas geçirmek istediğiniz Azure'da.</span><span class="sxs-lookup"><span data-stu-id="9f04f-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="9f04f-106">Bu modernization olgunluk düzeyde aslında geçerli, şirket içi altyapınızı kullanmaya devam edebilirsiniz yerine bulutta VM'ler kullanmaya başlamak için senaryodur.</span><span class="sxs-lookup"><span data-stu-id="9f04f-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="9f04f-107">Analiz etmek için başka bir nokta *neden* saf Iaas bulutuna daha gelişmiş yönetilen Azure hizmetlerinde yalnızca eklemek yerine geçirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f04f-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="9f04f-108">Hangi durumlarda olabilir belirlemek gereken Iaas ilk başta gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-108">You need to determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="9f04f-109">Şekil 2-1'de modernization olgunluk düzeyleri bulut altyapısı çapında kullanılmaya hazır uygulamalar yerleştirir:</span><span class="sxs-lookup"><span data-stu-id="9f04f-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma](./media/image2-1.png)

> <span data-ttu-id="9f04f-111">**Şekil 2-1.**</span><span class="sxs-lookup"><span data-stu-id="9f04f-111">**Figure 2-1.**</span></span> <span data-ttu-id="9f04f-112">Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma</span><span class="sxs-lookup"><span data-stu-id="9f04f-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="9f04f-113">Neden Azure Iaas varolan .NET web uygulamalarını geçirme</span><span class="sxs-lookup"><span data-stu-id="9f04f-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="9f04f-114">Maliyet azaltması elde etmek için bile, ilk bir Iaas düzeyinde buluta geçirmek için ana nedeni olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9f04f-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="9f04f-115">Daha fazla yönetilen altyapı hizmetleri kullanarak, kuruluşunuz kendi donanım bakım, sunucu veya VM sağlama ve dağıtım ve altyapı Yönetimi yatırım düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f04f-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="9f04f-116">Buluta uygulamalarınızı geçmeye karar yaptıktan sonra neden, Iaas yerine PaaS basitçe, olduğu gibi daha gelişmiş seçenekler Iaas ortam tercih edebileceğiniz ana nedeni daha tanıdık gelecektir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="9f04f-117">Geçerli için benzer bir ortama taşıma, bir alt öğrenme olmasını sağlayan en hızlı yolu buluta eğrisi, şirket içi ortamı sunar.</span><span class="sxs-lookup"><span data-stu-id="9f04f-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="9f04f-118">Ancak, en hızlı yolu buluta alma, uygulamalarınızı bulutta çalışan sahip gelen çoğu avantajı elde anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="9f04f-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="9f04f-119">Herhangi bir kuruluştaki zaten sunulan bulut DevOps hazır ve PaaS (bulut Hızlandırılmış) olgunluk düzeyleri bulut taşınan en önemli avantajlarını elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="9f04f-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud DevOps-Ready and PaaS (Cloud-Optimized) maturity levels.</span></span>

<span data-ttu-id="9f04f-120">Ayrıca korumalı uygulamaları modernize ve gelecekte zaten bulutta bile Iaas üzerinde çalışırken yeniden düzenlenmesine daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="9f04f-120">It also has become evident that applications are easier to modernize and re-architect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="9f04f-121">Uygulama veri geçişi zaten elde kısmen doğru olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9f04f-121">This is true in part because application data migration has already been achieved.</span></span> <span data-ttu-id="9f04f-122">Ayrıca, kuruluşunuz bulutta çalışmak için gerekli niteliklere kazanılan ve bir "bulut kültürün." işletim için shift yapılan</span><span class="sxs-lookup"><span data-stu-id="9f04f-122">Also, your organization will have gained skills required for working in the cloud, and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="9f04f-123">Ne zaman yerine bir Iaas PaaS için geçirmek için</span><span class="sxs-lookup"><span data-stu-id="9f04f-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="9f04f-124">Sonraki bölümlerde PaaS platformları ve Hizmetleri çoğunlukla göre bulut DevOps çapında kullanılmaya hazır uygulamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f04f-124">The next sections discuss Cloud DevOps-Ready applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="9f04f-125">Bu uygulamaları buluta geçiş çoğu avantajları verin.</span><span class="sxs-lookup"><span data-stu-id="9f04f-125">These apps give you the most benefits from migrating to the cloud.</span></span>

<span data-ttu-id="9f04f-126">Amacınız yalnızca uygulamalarınız buluta taşımak için ilk olarak, Azure App Service'te çalıştırmak için önemli değişiklik gerektiren uygulamalarınız belirlemek.</span><span class="sxs-lookup"><span data-stu-id="9f04f-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that will require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="9f04f-127">Bu uygulamaları ilk adayları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f04f-127">These apps should be the first candidates.</span></span>

<span data-ttu-id="9f04f-128">İstemiyorsanız veya hala Windows kapsayıcıları ve/veya Azure Service Fabric veya Kubernetes gibi orchestrators taşıyamazsınız, düz VM'ler (Iaas) kullanırsınız sonra henüz, ardından durumdur.</span><span class="sxs-lookup"><span data-stu-id="9f04f-128">Then, if you don't want or still cannot move to Windows Containers and or orchestrators like Azure Service Fabric or Kubernetes, yet, then is when you would use plain VMs (IaaS).</span></span>

<span data-ttu-id="9f04f-129">Ancak, doğru yapılandırma, güvenliği ve VM'ler koruyarak daha fazla zaman ve Azure'da PaaS hizmetleri kullanmaya kıyasla BT uzmanlık gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9f04f-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="9f04f-130">Azure sanal makineleri düşünüyorsanız, düzeltme eki, güncelleştirme ve VM ortamınızı yönetmek için gerekli devam eden bakım çaba dikkate almanız emin olun.</span><span class="sxs-lookup"><span data-stu-id="9f04f-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="9f04f-131">Azure sanal makinelerin Iaas şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="9f04f-132">Azure geçirmek çözümlemek ve mevcut uygulamalarınızı azure'a geçirmek için kullanın</span><span class="sxs-lookup"><span data-stu-id="9f04f-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="9f04f-133">Buluta geçiş zor sahip değil.</span><span class="sxs-lookup"><span data-stu-id="9f04f-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="9f04f-134">Ancak, çoğu kuruluş - ortam ve uygulamaların, iş yükleri ve verileri arasında sıkı bağımlılıklarını derin bir görünürlük aktarıp kullanmaya başlama güçlük.</span><span class="sxs-lookup"><span data-stu-id="9f04f-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="9f04f-135">Bu görünürlük yolun İleri plana zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="9f04f-136">Başarılı bir geçiş için gerekli ilgili ayrıntılı bilgi, kuruluşunuz içinde sağ görüşmeleri sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="9f04f-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="9f04f-137">Yeterli olası faydaları, maliyet hakkında tanımadığınız veya iş yükleri yalnızca yükseltme-ve-shift verebilir veya başarıyla geçirmek için önemli yeniden çalışma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="9f04f-138">Wonder birçok kuruluş istemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="9f04f-139">[Azure geçirme](https://aka.ms/azuremigrate) , Kılavuzu, Öngörüler ve Azure'a geçirme yardımcı olmak için gereken mekanizmaları sağlayan yeni bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="9f04f-140">Azure geçirme sağlar:</span><span class="sxs-lookup"><span data-stu-id="9f04f-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="9f04f-141">Bulma ve şirket içi sanal makineler için değerlendirme</span><span class="sxs-lookup"><span data-stu-id="9f04f-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="9f04f-142">Çok katmanlı uygulamaları Yüksek Güvenilirlikli bulma için yerleşik bağımlılık eşleme</span><span class="sxs-lookup"><span data-stu-id="9f04f-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="9f04f-143">Azure sanal makineler için akıllı sağa boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="9f04f-143">Intelligent rightsizing to Azure virtual machines</span></span>

- <span data-ttu-id="9f04f-144">Uyumluluk kuralları düzelterek olası sorunlar için raporlama</span><span class="sxs-lookup"><span data-stu-id="9f04f-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="9f04f-145">Veritabanı bulma ve geçiş için Azure veritabanı yönetim hizmeti ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="9f04f-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="9f04f-146">Azure geçirme iş yüklerinizi iş için en az etkiyle geçirmek ve Azure'da beklendiği gibi çalışmazsa güven verir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="9f04f-147">Doğru Araçlar ve Kılavuzu, en çok önemli performans modemlerin sırasında yatırım getirisi elde edebilirsiniz ve güvenilirlik gereksinimlerini karşılıyor.</span><span class="sxs-lookup"><span data-stu-id="9f04f-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="9f04f-148">Şekil 2-2 Azure geçirmek tarafından gerçekleştirilen tüm sunucu ve uygulama bağlantıları için yerleşik bağımlılık eşleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma](./media/image2-2.png)

> <span data-ttu-id="9f04f-150">**Şekil 2-2.**</span><span class="sxs-lookup"><span data-stu-id="9f04f-150">**Figure 2-2.**</span></span> <span data-ttu-id="9f04f-151">Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma</span><span class="sxs-lookup"><span data-stu-id="9f04f-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="9f04f-152">Azure VM'ler için var olan sanal makineleri geçirmek için Azure Site Recovery kullanın</span><span class="sxs-lookup"><span data-stu-id="9f04f-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="9f04f-153">Uçtan uca bir parçası olarak [Azure geçirmek](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) kolayca web uygulamalarınızı Azure sanal makineleri geçirmek için kullanabileceğiniz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="9f04f-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="9f04f-154">Site Recovery, şirket içi sanal makineleri ve fiziksel sunucuları azure'a veya ikincil şirket içi konumuna çoğaltmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f04f-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="9f04f-155">Bile bir şirket içi üzerinde desteklenen bir Azure VM üzerinde çalışan bir iş yükünü çoğaltabilir *Hyper-V* VM üzerindeki bir *VMware* VM veya Windows veya Linux fiziksel sunucuda.</span><span class="sxs-lookup"><span data-stu-id="9f04f-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="9f04f-156">Azure'a çoğaltma için ikincil veri merkezine sürdürme karmaşıklığı ve maliyeti ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9f04f-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="9f04f-157">Kısmen özellikle karma ortamlar için Site Recovery yapılan ayrıca şirket içi ve kısmen üzerinde Azure.</span><span class="sxs-lookup"><span data-stu-id="9f04f-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="9f04f-158">Site Recovery iş sürekliliği VM'ler üzerinde çalıştırılan uygulamalarınızı tutarak sağlamaya yardımcı olur ve fiziksel sunucular kullanılabilir bir site kullanılamaz hale gelirse şirket.</span><span class="sxs-lookup"><span data-stu-id="9f04f-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="9f04f-159">Böylece birincil site kullanılamıyorsa, ikincil bir konumda kullanılabilir kalır, sanal makineleri ve fiziksel sunucularda çalışan iş yükleri çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="9f04f-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="9f04f-160">Bu olduğunda, birincil site ve yeniden çalıştırmayı iş yükleri kurtarır.</span><span class="sxs-lookup"><span data-stu-id="9f04f-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="9f04f-161">Şekil 2-3, Azure Site Recovery kullanarak birden çok VM geçiş yürütülmesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f04f-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma](./media/image2-3.png)

> <span data-ttu-id="9f04f-163">**Şekil 2-3.**</span><span class="sxs-lookup"><span data-stu-id="9f04f-163">**Figure 2-3.**</span></span> <span data-ttu-id="9f04f-164">Bulut altyapısı çapında kullanılmaya hazır uygulamalar konumlandırma</span><span class="sxs-lookup"><span data-stu-id="9f04f-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9f04f-165">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9f04f-165">Additional resources</span></span>

- <span data-ttu-id="9f04f-166">**Azure veri geçirme**</span><span class="sxs-lookup"><span data-stu-id="9f04f-166">**Azure Migrate Datasheet**</span></span>

    [<span data-ttu-id="9f04f-167">https://aka.ms/azuremigration\_Veri sayfası</span><span class="sxs-lookup"><span data-stu-id="9f04f-167">https://aka.ms/azuremigration\_datasheet</span></span>](https://aka.ms/azuremigration\_datasheet)

- <span data-ttu-id="9f04f-168">**Azure geçirme**</span><span class="sxs-lookup"><span data-stu-id="9f04f-168">**Azure Migrate**</span></span>

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

- <span data-ttu-id="9f04f-169">**Site Recovery ile azure'a geçirme**</span><span class="sxs-lookup"><span data-stu-id="9f04f-169">**Migrate to Azure with Site Recovery**</span></span>

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- <span data-ttu-id="9f04f-170">**Azure Site Recovery hizmetine genel bakış**</span><span class="sxs-lookup"><span data-stu-id="9f04f-170">**Azure Site Recovery service overview**</span></span>

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- <span data-ttu-id="9f04f-171">**Azure VM'ler için aws'deki geçirme VM'ler**</span><span class="sxs-lookup"><span data-stu-id="9f04f-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
<span data-ttu-id="9f04f-172">[Önceki](index.md)
[sonraki](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="9f04f-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span>
