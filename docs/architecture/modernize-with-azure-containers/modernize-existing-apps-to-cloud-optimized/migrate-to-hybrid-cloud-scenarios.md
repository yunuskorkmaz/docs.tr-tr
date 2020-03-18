---
title: Karma bulut senaryolarına geçiş
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Karma bulut senaryolarına geçiş
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937372"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="f2398-103">Karma bulut senaryolarına geçiş</span><span class="sxs-lookup"><span data-stu-id="f2398-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="f2398-104">Bazı kuruluşlar ve kuruluşlar, düzenlemeler veya kendi ilkeleri nedeniyle bazı uygulamalarını Microsoft Azure veya başka bir genel bulut gibi genel bulutlara geçiremez.</span><span class="sxs-lookup"><span data-stu-id="f2398-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="f2398-105">Ancak, herhangi bir kuruluşun bazı uygulamalarının genel bulutta ve diğer uygulamalarda şirket içinde olması ndan yararlanabileceği olasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2398-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="f2398-106">Ancak karışık bir ortam, genel bulutlarda kullanılan farklı platformlar ve teknolojiler ve şirket içi ortamlar nedeniyle ortamlarda aşırı karmaşıklığa yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="f2398-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="f2398-107">Microsoft, bir Azure karma bulutta tutarlılık sağlarken, varolan varlıklarınızı şirket içinde ve genel bulutta optimize edebileceğiniz en iyi karma bulut çözümlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2398-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="f2398-108">Azure Yığını (şirket içi) ve Azure (genel bulut) sayesinde varolan becerileri en üst düzeye çıkarabilir ve bulutta veya şirket içinde çalıştırılabilen uygulamalar oluşturmak için esnek ve birleşik bir yaklaşım elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2398-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="f2398-109">Güvenlik söz konusu olduğunda, yönetim ve güvenliği karma bulutunuzda merkezileştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2398-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="f2398-110">Şirket içi ve bulut uygulamalarına tek oturum açma sağlayarak veri merkezinizden buluta kadar tüm varlıkların kontrolünü edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2398-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="f2398-111">Bunu, Active Directory'yi karma buluta genişleterek ve kimlik yönetimini kullanarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2398-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="f2398-112">Son olarak, verileri sorunsuz bir şekilde dağıtabilir ve analiz edebilir, bulut ve şirket içi varlıklar için aynı sorgu dillerini kullanabilir ve kaynağıne bakılmaksızın verilerinizi zenginleştirmek için Azure'da analitik ve derin öğrenme uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2398-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="f2398-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="f2398-113">Azure Stack</span></span>

<span data-ttu-id="f2398-114">Azure Yığını, kuruluşunuzun veri merkezinden Azure hizmetleri sunmanıza olanak tanıyan karma bir bulut platformudur.</span><span class="sxs-lookup"><span data-stu-id="f2398-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="f2398-115">Azure Yığını, kenar ve bağlantısız ortamlar veya belirli güvenlik ve uyumluluk gereksinimlerini karşılama gibi önemli senaryolarda modern uygulamalarınız için yeni seçenekleri desteklemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f2398-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="f2398-116">Şekil 4-13, Microsoft'un sunduğu gerçek karma bulut platformuna genel bir bakış gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2398-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Azure Yığını ve Azure ile Microsoft karma bulut platformu diyagramı.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="f2398-118">**Şekil 4-13.**</span><span class="sxs-lookup"><span data-stu-id="f2398-118">**Figure 4-13.**</span></span> <span data-ttu-id="f2398-119">Azure Yığını ve Azure ile Microsoft karma bulut platformu</span><span class="sxs-lookup"><span data-stu-id="f2398-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="f2398-120">Azure Yığını, gereksinimlerinizi karşılamak için iki dağıtım seçeneğinde sunulur:</span><span class="sxs-lookup"><span data-stu-id="f2398-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="f2398-121">Azure Yığını tümleşik sistemleri</span><span class="sxs-lookup"><span data-stu-id="f2398-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="f2398-122">Azure Yığını Geliştirme Kiti</span><span class="sxs-lookup"><span data-stu-id="f2398-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="f2398-123">Azure Yığını tümleşik sistemleri</span><span class="sxs-lookup"><span data-stu-id="f2398-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="f2398-124">Azure Stack tümleşik sistemleri, Microsoft ve donanım iş ortaklarının ortaklığı yla sunulur.</span><span class="sxs-lookup"><span data-stu-id="f2398-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="f2398-125">Ortaklık, yönetimde basitlikle dengelenmiş bulut tempolu bir yenilik sunan bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2398-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="f2398-126">Azure Yığını entegre bir donanım ve yazılım sistemi olarak sunulduğundan, buluttan inovasyonu benimsemeye devam ederken doğru miktarda esneklik ve denetim elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="f2398-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="f2398-127">Azure Stack tümleşik sistemlerinin boyutları 4 ile 12 arasında değişir ve donanım ortağı ve Microsoft tarafından ortaklaşa desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f2398-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="f2398-128">Üretim iş yükleriniçin yeni senaryolar uygulamak için Azure Yığını tümleşik sistemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2398-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="f2398-129">Azure Yığını Geliştirme Kiti</span><span class="sxs-lookup"><span data-stu-id="f2398-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="f2398-130">Microsoft Azure Yığını Geliştirme Kiti, Azure Yığını'nı değerlendirmek ve Azure Yığını hakkında bilgi edinmek için kullanabileceğiniz tek düğümlü bir Azure Yığını dağıtımıdır.</span><span class="sxs-lookup"><span data-stu-id="f2398-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="f2398-131">Azure Yığını Geliştirme Kiti'ni, ApI'leri ve Azure ile tutarlı araçlar kullanarak geliştirebileceğiniz bir geliştirici ortamı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2398-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="f2398-132">Azure Yığını Geliştirme Kiti'nin üretim ortamı olarak kullanılması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="f2398-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f2398-133">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f2398-133">Additional resources</span></span>

- <span data-ttu-id="f2398-134">**Azure karma bulut**</span><span class="sxs-lookup"><span data-stu-id="f2398-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="f2398-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="f2398-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="f2398-136">**Windows Kapsayıcıları için Etkin Dizin Hizmet Hesapları**</span><span class="sxs-lookup"><span data-stu-id="f2398-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="f2398-137">**Active Directory desteğine sahip bir kapsayıcı oluşturma**</span><span class="sxs-lookup"><span data-stu-id="f2398-137">**Create a container with Active Directory support**</span></span>

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- <span data-ttu-id="f2398-138">**Azure Karma Avantaj lisanslama**</span><span class="sxs-lookup"><span data-stu-id="f2398-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="f2398-139">[Önceki](life-cycle-ci-cd-pipelines-devops-tools.md)
>[Sonraki](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="f2398-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
