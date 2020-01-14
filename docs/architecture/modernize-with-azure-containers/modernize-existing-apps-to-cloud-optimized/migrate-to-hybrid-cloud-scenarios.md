---
title: Karma bulut senaryolarına geçiş
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Karma bulut senaryolarına geçiş
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937372"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="f8c4c-103">Karma bulut senaryolarına geçiş</span><span class="sxs-lookup"><span data-stu-id="f8c4c-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="f8c4c-104">Bazı kuruluşlar ve kuruluşlar, bazı uygulamalarını, düzenlemeler veya kendi ilkeleri nedeniyle Microsoft Azure veya başka bir genel bulut gibi genel bulutlara geçiremez.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="f8c4c-105">Ancak, herhangi bir kuruluşun bazı uygulamalarını genel bulutta ve şirket içi diğer uygulamalarda sahip olma olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="f8c4c-106">Ancak, karma bir ortam, genel bulutlarda kullanılan farklı platformlar ve teknolojiler ve şirket içi ortamlardan dolayı ortamlarda aşırı karmaşıklığa yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="f8c4c-107">Microsoft, bir Azure hibrit bulutu 'nda tutarlılığın sağladığından, mevcut varlıklarınızı şirket içinde ve genel bulutta iyileştirilebilmenizi sağlayan en iyi karma bulut çözümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="f8c4c-108">Var olan becerileri en üst düzeye çıkarabilir ve bulutta veya şirket içinde çalışabilen uygulamalar oluşturmaya yönelik esnek ve birleştirilmiş bir yaklaşım edinebilirsiniz (Şirket içi) ve Azure (genel bulut) Azure Stack sayesinde.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="f8c4c-109">Güvenlik 'e geldiğinde, karma bulutunuz genelinde yönetim ve güvenliği merkezileştirme sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="f8c4c-110">Şirket içi ve bulut uygulamaları için çoklu oturum açma olanağı sunarak, veri merkezinizden buluta kadar tüm varlıklar üzerinde denetim edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="f8c4c-111">Bunu, karma buluta Active Directory genişleterek ve kimlik yönetimi 'ni kullanarak gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="f8c4c-112">Son olarak, verileri sorunsuzca dağıtabilir ve analiz edebilir, bulut ve şirket içi varlıklar için aynı sorgu dillerini kullanabilir ve Azure 'da, kaynağına bakılmaksızın verilerinizi zenginleştirmek için analiz ve derin öğrenme uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="f8c4c-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="f8c4c-113">Azure Stack</span></span>

<span data-ttu-id="f8c4c-114">Azure Stack, kuruluşunuzun veri merkezinden Azure hizmetleri sunmanıza olanak tanıyan bir karma bulut platformudur.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="f8c4c-115">Azure Stack, kenar ve bağlı olmayan ortamlar gibi önemli senaryolarda modern uygulamalarınızın yeni seçeneklerini destekleyecek şekilde tasarlanmıştır veya belirli güvenlik ve uyumluluk gereksinimlerini karşılayarak.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="f8c4c-116">Şekil 4-13, Microsoft 'un sunduğu gerçek hibrit bulut platformunun bir genel görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Azure Stack ve Azure ile Microsoft hibrit bulut platformu diyagramı.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="f8c4c-118">**Şekil 4-13.**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-118">**Figure 4-13.**</span></span> <span data-ttu-id="f8c4c-119">Azure Stack ve Azure ile Microsoft hibrit bulut platformu</span><span class="sxs-lookup"><span data-stu-id="f8c4c-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="f8c4c-120">Azure Stack, gereksinimlerinizi karşılamak için iki dağıtım seçeneği sunulur:</span><span class="sxs-lookup"><span data-stu-id="f8c4c-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="f8c4c-121">Azure Stack tümleşik sistemleri</span><span class="sxs-lookup"><span data-stu-id="f8c4c-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="f8c4c-122">Azure Stack Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="f8c4c-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="f8c4c-123">Azure Stack tümleşik sistemleri</span><span class="sxs-lookup"><span data-stu-id="f8c4c-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="f8c4c-124">Azure Stack tümleşik sistemler, Microsoft ve donanım iş ortaklarının bir ortaklığı aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="f8c4c-125">İş ortaklığı, yönetimin basitliği ile dengeli bulut adımlı yenilik sunan bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="f8c4c-126">Azure Stack, donanım ve yazılım tümleştirilmiş bir sistem olarak sunulduğundan, doğru esneklik ve denetim elde edersiniz, ancak yine de buluttan yeniliği benimsemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="f8c4c-127">4 ile 12 düğümden oluşan tümleşik sistemleri Azure Stack ve donanım ortağı ve Microsoft tarafından ortaklaşa desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="f8c4c-128">Üretim iş yükleriniz için yeni senaryolar uygulamak üzere Azure Stack tümleşik sistemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="f8c4c-129">Azure Stack Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="f8c4c-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="f8c4c-130">Microsoft Azure Stack Development Kit, Azure Stack hakkında değerlendirmek ve bilgi edinmek için kullanabileceğiniz Azure Stack tek düğümlü bir dağıtımdır.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="f8c4c-131">Azure ile tutarlı olan API 'Leri ve araçları kullanarak geliştirebileceğiniz bir geliştirici ortamı olarak Azure Stack Geliştirme Seti de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="f8c4c-132">Azure Stack Geliştirme Seti, üretim ortamı olarak kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="f8c4c-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f8c4c-133">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f8c4c-133">Additional resources</span></span>

- <span data-ttu-id="f8c4c-134">**Azure hibrit bulutu**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="f8c4c-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="f8c4c-136">**Windows kapsayıcıları için hizmet hesaplarını Active Directory**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="f8c4c-137">**Active Directory desteğiyle kapsayıcı oluşturma**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-137">**Create a container with Active Directory support**</span></span>

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- <span data-ttu-id="f8c4c-138">**Azure Hibrit Avantajı lisanslama**</span><span class="sxs-lookup"><span data-stu-id="f8c4c-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="f8c4c-139">[Önceki](life-cycle-ci-cd-pipelines-devops-tools.md)
>[İleri](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="f8c4c-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
