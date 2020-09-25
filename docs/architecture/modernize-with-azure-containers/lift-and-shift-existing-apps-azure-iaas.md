---
title: Mevcut .NET uygulamalarını Azure IaaS 'ye yükseltme ve kaydırma (bulut altyapısına hazırlanın)
description: Azure bulut ve Windows kapsayıcıları Ile mevcut .NET uygulamalarını modernleştirin.
ms.date: 04/28/2018
ms.openlocfilehash: d610222aa6649c1b28e198c074794dd316f895ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172176"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a><span data-ttu-id="55ce4-103">Mevcut .NET uygulamalarını Azure IaaS 'ye yükseltme ve kaydırma (bulut altyapısına hazırlanın)</span><span class="sxs-lookup"><span data-stu-id="55ce4-103">Lift and shift existing .NET apps to Azure IaaS (Cloud Infrastructure-Ready)</span></span>

> <span data-ttu-id="55ce4-104">Vizyon: ilk adım olarak, şirket içi yatırımınızdan ve donanım ve ağ bakımının toplam maliyetinizi azaltmak için, mevcut uygulamalarınızı bulutta yeniden barındırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="55ce4-105">Mevcut uygulamalarınızı Azure *how* hizmet olarak altyapı (IaaS) platformuna geçirme işlemine geçmeden önce, Azure 'Da IaaS 'ye doğrudan geçiş *yapmak istediğiniz nedenleri analiz etmeniz önemlidir* .</span><span class="sxs-lookup"><span data-stu-id="55ce4-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="55ce4-106">Bu modernon vade düzeyindeki senaryo temelde, geçerli şirket içi altyapınızı kullanmaya devam etmek yerine buluttaki VM 'Leri kullanmaya başlamadır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="55ce4-107">Analiz etmek için başka bir *nokta de yalnızca* Azure 'da daha gelişmiş yönetilen hizmetler eklemek yerine saf IaaS bulutuna geçiş yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ce4-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="55ce4-108">İlk yerde IaaS için hangi durumların gerekli olabileceğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="55ce4-108">Determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="55ce4-109">Şekil 2-1, bulut altyapısına uygun olan uygulamaları modernleştirme vade düzeylerinde konumlandırır:</span><span class="sxs-lookup"><span data-stu-id="55ce4-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![Bulut altyapısına yönelik özellikli uygulamaları konumlandırma](./media/image2-1.png)

<span data-ttu-id="55ce4-111">**Şekil 2-1.**</span><span class="sxs-lookup"><span data-stu-id="55ce4-111">**Figure 2-1.**</span></span> <span data-ttu-id="55ce4-112">Bulut altyapısına yönelik özellikli uygulamaları konumlandırma</span><span class="sxs-lookup"><span data-stu-id="55ce4-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="55ce4-113">Mevcut .NET Web uygulamaları neden Azure IaaS 'ye geçirilir?</span><span class="sxs-lookup"><span data-stu-id="55ce4-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="55ce4-114">İlk IaaS düzeyinde bile buluta geçiş yapmanın ana nedeni, maliyet azaltmaları elde etmelidir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="55ce4-115">Kuruluşunuz, daha fazla yönetilen altyapı hizmeti kullanarak, donanım bakımı, sunucu veya VM sağlama ve dağıtım ve altyapı yönetimi için yatırımınızı düşürür.</span><span class="sxs-lookup"><span data-stu-id="55ce4-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="55ce4-116">Uygulamalarınızı buluta taşıma kararı verdikten sonra, PaaS gibi daha gelişmiş seçenekler yerine IaaS ' ı seçip IaaS ortamının daha tanıdık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="55ce4-117">Geçerli, şirket içi ortamınıza benzer bir ortama geçiş yapmak, daha düşük bir öğrenme eğrisi sunarak buluta en hızlı yol açar.</span><span class="sxs-lookup"><span data-stu-id="55ce4-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="55ce4-118">Ancak, bulut için en hızlı yolu almak, uygulamalarınızın bulutta çalışmasını sağlamak için en avantajdan yararlanabileceğinizi ifade etmez.</span><span class="sxs-lookup"><span data-stu-id="55ce4-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="55ce4-119">Herhangi bir kuruluş, bulut geçişinizden en önemli avantajlara sahip olacak, zaten buluta Iyileştirilmiş ve bulut Yerel vade seviyelerine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="55ce4-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud-Optimized and Cloud-Native maturity levels.</span></span>

<span data-ttu-id="55ce4-120">Ayrıca, uygulamaların bulutta zaten çalışmakta olduğu durumlarda (IaaS 'de bile) modernleştirin ve yeniden mimarilerde daha kolay hale geldiğini de unutmayın.</span><span class="sxs-lookup"><span data-stu-id="55ce4-120">It also has become evident that applications are easier to modernize and rearchitect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="55ce4-121">Uygulama verileri geçişi zaten elde edildi.</span><span class="sxs-lookup"><span data-stu-id="55ce4-121">Application data migration has already been achieved.</span></span> <span data-ttu-id="55ce4-122">Ayrıca, kuruluşunuz bulutta çalışmak için gereken becerileri elde etmiş ve bir "bulut kültürüne" kaydırma yapacaktır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-122">Also, your organization will have gained skills required for working in the cloud and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="55ce4-123">PaaS yerine IaaS 'e geçiş yapma</span><span class="sxs-lookup"><span data-stu-id="55ce4-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="55ce4-124">Sonraki bölümlerde, genellikle PaaS platformları ve hizmetlerine bağlı olan buluta Iyileştirilmiş uygulamalar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-124">The next sections discuss Cloud-Optimized applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="55ce4-125">Bu uygulamalar, buluta geçiş işleminden en iyi avantajları sağlar.</span><span class="sxs-lookup"><span data-stu-id="55ce4-125">These apps give you the most benefits from migrating to the cloud.</span></span>

<span data-ttu-id="55ce4-126">Amacınız var olan uygulamaları buluta taşımak için ilk olarak, Azure App Service içinde çalışması gereken önemli değişiklikleri gerektirmeyen mevcut uygulamaları belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="55ce4-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that would not require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="55ce4-127">Bu uygulamalar, buluta En Iyi duruma getirilmiş ilk aday olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-127">These apps should be the first candidates for Cloud-Optimized.</span></span>

<span data-ttu-id="55ce4-128">Daha sonra, Azure Kubernetes hizmeti gibi App Service veya düzenleyicilerle Windows kapsayıcılarına ve PaaS 'ye geçemeyen uygulamalar için, bunları basit düz VM 'lere (IaaS) geçirin.</span><span class="sxs-lookup"><span data-stu-id="55ce4-128">Then, for the apps that still cannot move to Windows Containers and PaaS such as App Service or orchestrators like Azure Kubernetes Service, migrate those to simple plain VMs (IaaS).</span></span>

<span data-ttu-id="55ce4-129">Ancak, VM 'Lerin yapılandırılması, güvenliğinin sağlanması ve sürdürülmesi, Azure 'da PaaS hizmetlerini kullanmaya kıyasla çok daha fazla zaman ve BT uzmanlığı gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="55ce4-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="55ce4-130">Azure sanal makinelerini düşünüyorsanız, VM ortamınızı düzeltme eki uygulamak, güncelleştirmek ve yönetmek için gereken devam eden bakım çabalarını göz önünde bulundurduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="55ce4-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="55ce4-131">Azure sanal makineleri IaaS 'dir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="55ce4-132">Azure geçişi 'ni kullanarak mevcut uygulamalarınızı çözümleyin ve Azure 'a geçirin</span><span class="sxs-lookup"><span data-stu-id="55ce4-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="55ce4-133">Buluta geçiş yapmak zor değildir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="55ce4-134">Ancak birçok kuruluş, ortama ve uygulamalar, iş yükleri ve veriler arasındaki sıkı bağımlılıklar hakkında ayrıntılı görünürlük almak için kullanmaya başlamıştır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="55ce4-135">Bu görünürlük olmadan yolun ileri planlanılması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="55ce4-136">Başarılı bir geçiş için nelerin gerekli olduğuna ilişkin ayrıntılı bilgiler olmadan, kuruluşunuzda doğru konuşmaları olamaz.</span><span class="sxs-lookup"><span data-stu-id="55ce4-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="55ce4-137">Olası maliyet avantajları hakkında yeterince bilginiz yok ya da iş yüklerinin yalnızca kaldırıp kaldıramayacağını veya başarıyla geçiş yapmak için önemli bir yeniden çalışma gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="55ce4-138">Çok sayıda kuruluş yoktur.</span><span class="sxs-lookup"><span data-stu-id="55ce4-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="55ce4-139">[Azure geçişi](https://aka.ms/azuremigrate) , Azure 'a geçiş yaparken size yardımcı olmak için gereken kılavuz, Öngörüler ve mekanizmaları sağlayan yeni bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="55ce4-140">Azure geçişi şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="55ce4-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="55ce4-141">Şirket içi sanal makineler için bulma ve değerlendirme</span><span class="sxs-lookup"><span data-stu-id="55ce4-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="55ce4-142">Çok katmanlı uygulamaların yüksek güvenilirlikli keşfi için yerleşik bağımlılık eşlemesi</span><span class="sxs-lookup"><span data-stu-id="55ce4-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="55ce4-143">Azure sanal makinelerine akıllı doğru boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="55ce4-143">Intelligent right sizing to Azure virtual machines</span></span>

- <span data-ttu-id="55ce4-144">Olası sorunları giderme yönergeleriyle uyumluluk raporlaması</span><span class="sxs-lookup"><span data-stu-id="55ce4-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="55ce4-145">Veritabanı bulma ve geçiş için Azure veritabanı yönetim hizmeti ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="55ce4-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="55ce4-146">Azure geçişi, iş yüklerinizin işletmeye en az etkiyle geçiş yapma ve Azure 'da beklendiği gibi çalıştırma konusunda size güvendiğinden emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="55ce4-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="55ce4-147">Doğru araçlar ve kılavuzla, kritik performans ve güvenilirlik ihtiyaçlarını karşıladıktan sonra yatırımdaki maksimum iadeyi elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ce4-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="55ce4-148">Şekil 2-2, Azure geçişi tarafından gerçekleştirilen tüm sunucu ve uygulama bağlantıları için yerleşik bağımlılık eşlemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![Bulut altyapısına yönelik özellikli uygulamaları konumlandırma](./media/image2-2.png)

<span data-ttu-id="55ce4-150">**Şekil 2-2.**</span><span class="sxs-lookup"><span data-stu-id="55ce4-150">**Figure 2-2.**</span></span> <span data-ttu-id="55ce4-151">Bulut altyapısına yönelik özellikli uygulamaları konumlandırma</span><span class="sxs-lookup"><span data-stu-id="55ce4-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="55ce4-152">Mevcut VM 'lerinizi Azure VM 'lerine geçirmek için Azure Site Recovery kullanın</span><span class="sxs-lookup"><span data-stu-id="55ce4-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="55ce4-153">Uçtan uca [Azure geçişi](https://aka.ms/azuremigrate)kapsamında, [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) Web uygulamalarınızı Azure 'daki VM 'lere kolayca geçirmek için kullanabileceğiniz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="55ce4-154">Şirket içi VM 'Leri ve fiziksel sunucuları Azure 'a çoğaltmak veya ikincil bir şirket içi konuma çoğaltmak için Site Recovery kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ce4-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="55ce4-155">Hatta, desteklenen bir Azure VM 'de çalışan bir iş yükünü şirket içi *Hyper-V* VM 'Sinde, *VMware* VM 'de veya Windows ya da Linux fiziksel sunucusunda çoğaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ce4-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="55ce4-156">Azure’a çoğaltma seçeneği, ikincil bir veri merkezi kullanmanın maliyetini ve karmaşıklığını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="55ce4-157">Site Recovery Ayrıca, kısmen şirket içinde ve kısmen Azure 'da olan karma ortamlar için de yapılır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="55ce4-158">Site Recovery, VM 'lerde çalışan uygulamalarınızı ve şirket içi fiziksel sunucuları bir site daha sonra kullanılabilir durumda tutarak iş sürekliliği sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="55ce4-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="55ce4-159">Birincil site kullanılabilir değilse ikincil bir konumda kullanılabilir kalması için VM 'lerde ve fiziksel sunucularda çalışan iş yüklerini çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="55ce4-160">Birincil site yeniden çalışmaya başladığında birincil sitede iş yüklerini kurtarır.</span><span class="sxs-lookup"><span data-stu-id="55ce4-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="55ce4-161">Şekil 2-3 Azure Site Recovery kullanarak birden çok VM geçişlerinin yürütülmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ce4-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![Bulut altyapısına yönelik özellikli uygulamaları konumlandırma](./media/image2-3.png)

<span data-ttu-id="55ce4-163">**Şekil 2-3.**</span><span class="sxs-lookup"><span data-stu-id="55ce4-163">**Figure 2-3.**</span></span> <span data-ttu-id="55ce4-164">Bulut altyapısına yönelik özellikli uygulamaları konumlandırma</span><span class="sxs-lookup"><span data-stu-id="55ce4-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="55ce4-165">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="55ce4-165">Additional resources</span></span>

- <span data-ttu-id="55ce4-166">**Azure veri sayfasını geçirme**</span><span class="sxs-lookup"><span data-stu-id="55ce4-166">**Azure Migrate Datasheet**</span></span>

    <https://aka.ms/azuremigration\_datasheet>

- <span data-ttu-id="55ce4-167">**Azure Geçişi**</span><span class="sxs-lookup"><span data-stu-id="55ce4-167">**Azure Migrate**</span></span>

    <https://aka.ms/azuremigrate>

- <span data-ttu-id="55ce4-168">**Azure'a geçiş merkezi**</span><span class="sxs-lookup"><span data-stu-id="55ce4-168">**Azure migration center**</span></span>

    <https://azure.microsoft.com/migration/>

- <span data-ttu-id="55ce4-169">**Site Recovery ile Azure’a Geçiş**</span><span class="sxs-lookup"><span data-stu-id="55ce4-169">**Migrate to Azure with Site Recovery**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- <span data-ttu-id="55ce4-170">**Azure Site Recovery hizmete genel bakış**</span><span class="sxs-lookup"><span data-stu-id="55ce4-170">**Azure Site Recovery service overview**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- <span data-ttu-id="55ce4-171">**AWS 'de VM 'Leri Azure VM 'lerine geçirme**</span><span class="sxs-lookup"><span data-stu-id="55ce4-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
><span data-ttu-id="55ce4-172">[Önceki](index.md) 
> [Sonraki](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="55ce4-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span> <!-- Next Chapter -->
