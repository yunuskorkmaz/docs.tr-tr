---
title: Karma bulut senaryolarına geçiş
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Karma bulut senaryolarına geçiş
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b04c6edecf5b63f191cb2e0f808fb1d0f801d0a3
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612582"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="c9fb3-103">Karma bulut senaryolarına geçiş</span><span class="sxs-lookup"><span data-stu-id="c9fb3-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="c9fb3-104">Bazı kuruluşlar ve işletmeler, bazı Microsoft Azure gibi genel Bulutlar, uygulamalarına veya diğer genel bulut düzenlemeler veya kendi ilkeleri nedeniyle geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="c9fb3-105">Ancak, bazı müşterilerin uygulamalarını genel bulutta ve diğer şirket içi uygulamaları sahip her kuruluş yararlanabilecek olasıdır.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="c9fb3-106">Ancak, karma bir ortamda ortamlarda farklı platformları ve şirket içi ortamlara ve genel bulutlarda kullanılan teknolojiler nedeniyle aşırı karmaşıklıktan yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="c9fb3-107">Microsoft sağladığı en iyi hibrit bulut çözümü, size en iyi duruma getirebilir mevcut varlıklarınızı bir şirket içi ve Azure hibrit bulut tutarlılığı sırada genel bulutta.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="c9fb3-108">Mevcut becerilerinizi en üst düzeye çıkarmak ve bulutta veya şirket içi, Azure Stack (şirket) ve Azure (genel bulut) sayesinde çalışabilen uygulamalar oluşturmak için esnek ve birleşik bir yaklaşım elde edin.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="c9fb3-109">Güvenlik geldiğinde, yönetim ve güvenlik arasında karma bulutunuzu merkezileştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="c9fb3-110">Şirket içi çoklu oturum açma sağlayarak tüm varlıklar üzerinde denetim veri merkezinizi buluta alın ve bulut uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="c9fb3-111">Bu Active Directory karma buluta genişleterek ve kimlik yönetimi kullanarak gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="c9fb3-112">Son olarak, dağıtın ve verileri sorunsuz bir şekilde analiz, Bulut ve şirket içi varlıkları için aynı sorgu dilini kullanın ve analiz ve derin öğrenme azure'da verilerinizi kaynağından bağımsız olarak zenginleştirin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="c9fb3-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="c9fb3-113">Azure Stack</span></span>

<span data-ttu-id="c9fb3-114">Azure Stack, kuruluşunuzun veri merkezinden Azure Hizmetleri elde etmenizi sağlayan bir karma bulut platformudur.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="c9fb3-115">Azure Stack, edge ve bağlantısız ortamlarda veya toplantı belirli güvenlik ve uyumluluk gereksinimlerini gibi anahtar senaryolar, modern uygulamalar için yeni seçenekler desteklemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="c9fb3-116">Şekil 4-13, Microsoft'un sunduğu gerçek hibrit bulut platformu özetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Azure Stack ve Azure ile Microsoft hibrit bulut platformu](./media/image13.jpg)

> <span data-ttu-id="c9fb3-118">**Şekil 4-13.**</span><span class="sxs-lookup"><span data-stu-id="c9fb3-118">**Figure 4-13.**</span></span> <span data-ttu-id="c9fb3-119">Azure Stack ve Azure ile Microsoft hibrit bulut platformu</span><span class="sxs-lookup"><span data-stu-id="c9fb3-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="c9fb3-120">Azure Stack, gereksinimlerinizi karşılamak üzere iki dağıtım seçenekleri sunulur:</span><span class="sxs-lookup"><span data-stu-id="c9fb3-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

-   <span data-ttu-id="c9fb3-121">Azure Stack tümleşik sistemleri</span><span class="sxs-lookup"><span data-stu-id="c9fb3-121">Azure Stack integrated systems</span></span>

-   <span data-ttu-id="c9fb3-122">Azure Stack Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="c9fb3-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="c9fb3-123">Azure Stack tümleşik sistemleri</span><span class="sxs-lookup"><span data-stu-id="c9fb3-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="c9fb3-124">Azure Stack tümleşik sistemleri, Microsoft ve donanım iş ortaklarından oluşan bir iş ortaklığı sunulur.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="c9fb3-125">İş ortaklığı, basitçe yönetim olanağı sunan bulut hızını sizin belirlediğiniz yenilik sunan bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="c9fb3-126">Azure Stack, donanım ve yazılım tümleşik bir sistem halinde sunulur çünkü hala buluttan yenilik benimseme sırasında esneklik ve denetim, doğru miktarda alın.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="c9fb3-127">Azure Stack tümleşik sistemleri 12 düğümlere boyutu 4'ten aralık ve tüm dünyada donanım iş ortağı ve Microsoft tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="c9fb3-128">Üretim iş yükleriniz için yeni senaryolar uygulamak için Azure Stack tümleşik sistemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="c9fb3-129">Azure Stack Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="c9fb3-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="c9fb3-130">Microsoft Azure Stack geliştirme Seti'ni değerlendirmek ve Azure Stack hakkında bilgi edinmek için kullanabileceğiniz Azure Stack, tek düğümlü dağıtımıdır.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="c9fb3-131">Burada API'lerini kullanarak geliştirebilirsiniz ve Araçlar Azure ile tutarlı bir geliştirme ortamı olarak Azure Stack Geliştirme Seti de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="c9fb3-132">Azure Stack Geliştirme Seti, bir üretim ortamı olarak kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c9fb3-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c9fb3-133">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c9fb3-133">Additional resources</span></span>

-   <span data-ttu-id="c9fb3-134">**Azure hibrit bulut**</span><span class="sxs-lookup"><span data-stu-id="c9fb3-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

-   <span data-ttu-id="c9fb3-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="c9fb3-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

-   <span data-ttu-id="c9fb3-136">**Windows kapsayıcıları için Active Directory hizmet hesapları**</span><span class="sxs-lookup"><span data-stu-id="c9fb3-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

-   <span data-ttu-id="c9fb3-137">**Active Directory desteği ile bir kapsayıcı oluşturma**</span><span class="sxs-lookup"><span data-stu-id="c9fb3-137">**Create a container with Active Directory support**</span></span>

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

-   <span data-ttu-id="c9fb3-138">**Azure hibrit avantajı lisanslama**</span><span class="sxs-lookup"><span data-stu-id="c9fb3-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="c9fb3-139">[Önceki](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[İleri](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="c9fb3-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
