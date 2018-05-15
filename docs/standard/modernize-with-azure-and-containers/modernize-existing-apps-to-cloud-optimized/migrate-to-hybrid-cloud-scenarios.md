---
title: Karma bulut senaryolarında geçirme
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Karma bulut senaryolarında geçirme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 8885ee8fce4f8c11c14ee8936f3ee0ffd89ece04
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="13a49-103">Karma bulut senaryolarında geçirme</span><span class="sxs-lookup"><span data-stu-id="13a49-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="13a49-104">Bazı kuruluşlar ve işletmeler uygulamalarını Microsoft Azure gibi genel Bulutlar için bazıları veya diğer genel bulut düzenlemeler veya kendi ilkeleri nedeniyle geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="13a49-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="13a49-105">Ancak, herhangi bir kuruluştaki bazı genel Bulut ve diğer uygulamalar şirket uygulamalarında kalmaktan yararlanabilir olasıdır.</span><span class="sxs-lookup"><span data-stu-id="13a49-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="13a49-106">Ancak, karma bir ortamı farklı platformları ve şirket içi ortamları ve genel Bulutlar kullanılan teknolojiler nedeniyle ortamlarda aşırı karmaşıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="13a49-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="13a49-107">Microsoft, en iyi karma bulut çözümü sağlar, biri içinde en iyi duruma getirebilir varolan varlıklarınızı şirket içi ve buluttaki bir Azure karma bulutta tutarlılığı sırada ortak,.</span><span class="sxs-lookup"><span data-stu-id="13a49-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="13a49-108">Var olan becerileri en üst düzeye çıkarmak ve bulutta veya şirket içi, Azure yığını (şirket içi) ve Azure (genel bulut) sayesinde çalıştırabilirsiniz uygulamaları oluşturmak için esnek, birleştirilmiş bir yaklaşım alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13a49-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="13a49-109">Güvenlik geldiğinde, yönetim ve güvenlik, karma bulut merkezileştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13a49-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="13a49-110">Çoklu oturum açma şirket içi sağlayarak tüm varlıklar üzerinde denetim merkeziniz buluta almak ve bulut uygulamalarında.</span><span class="sxs-lookup"><span data-stu-id="13a49-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="13a49-111">Bunu Active Directory karma bir buluta genişletme ve kimlik yönetimi kullanarak gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13a49-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="13a49-112">Son olarak, dağıtmak ve sorunsuz bir şekilde verileri çözümlemek, Bulut ve şirket içi varlıklar için sorgu dillerini kullanın ve analizi ve kaynağına bakılmaksızın, verilerinizi zenginleştirmek için azure'da öğrenme derin uygulanır.</span><span class="sxs-lookup"><span data-stu-id="13a49-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="13a49-113">Azure yığını</span><span class="sxs-lookup"><span data-stu-id="13a49-113">Azure Stack</span></span>

<span data-ttu-id="13a49-114">Azure yığın kuruluşunuzun veri merkezinden Azure Hizmetleri sunmanıza olanak sağlayan bir karma bulut platformudur.</span><span class="sxs-lookup"><span data-stu-id="13a49-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="13a49-115">Azure yığın kenar ve bağlantısız ortamlarda veya toplantı belirli güvenlik ve uyumluluk gereksinimleri gibi anahtar senaryolarda modern, uygulamalarınız için yeni seçenekler destekleyecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="13a49-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="13a49-116">Şekil 4-13 Microsoft sunar doğru karma bulut platformu özetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="13a49-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Microsoft Azure yığın ve Azure ile karma bulut platformu](./media/image13.jpg)

> <span data-ttu-id="13a49-118">**Şekil 4-13.**</span><span class="sxs-lookup"><span data-stu-id="13a49-118">**Figure 4-13.**</span></span> <span data-ttu-id="13a49-119">Microsoft Azure yığın ve Azure ile karma bulut platformu</span><span class="sxs-lookup"><span data-stu-id="13a49-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="13a49-120">Azure yığın gereksinimlerinizi karşılamak için iki dağıtım seçeneği, sunulur:</span><span class="sxs-lookup"><span data-stu-id="13a49-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

-   <span data-ttu-id="13a49-121">Azure tümleşik yığını sistemleri</span><span class="sxs-lookup"><span data-stu-id="13a49-121">Azure Stack integrated systems</span></span>

-   <span data-ttu-id="13a49-122">Azure yığın Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="13a49-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="13a49-123">Azure tümleşik yığını sistemleri</span><span class="sxs-lookup"><span data-stu-id="13a49-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="13a49-124">Azure tümleşik yığını sistemleri, bir Microsoft ve donanım iş ortakları ortaklık sunulur.</span><span class="sxs-lookup"><span data-stu-id="13a49-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="13a49-125">Ortaklık Yönetimi'nde Basitlik denkleştirilir bulut hızını belirleyebileceği yenilik sunan bir çözümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13a49-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="13a49-126">Azure yığın donanım ve yazılım tümleşik bir sistem olarak sunulan olduğundan hala bulutta yenilik benimsenmesi sırasında esneklik ve Denetim doğru miktarda alın.</span><span class="sxs-lookup"><span data-stu-id="13a49-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="13a49-127">Azure tümleşik yığını sistemleri 4 boyutu 12 düğümlere aralığı ve ortaklaşa donanım iş ortakları ve Microsoft tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="13a49-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="13a49-128">Üretim iş yükleri için yeni senaryolar uygulamak için Azure tümleşik yığını sistemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="13a49-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="13a49-129">Azure yığın Geliştirme Seti</span><span class="sxs-lookup"><span data-stu-id="13a49-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="13a49-130">Microsoft Azure yığın Geliştirme Seti değerlendirmek ve Azure yığın hakkında bilgi almak için kullanabileceğiniz Azure yığınının tek düğümlü dağıtımıdır.</span><span class="sxs-lookup"><span data-stu-id="13a49-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="13a49-131">Burada API'lerini kullanarak geliştirebilirsiniz ve, tooling Azure ile tutarlı bir geliştirici ortamı olarak Azure yığın Geliştirme Seti de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13a49-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="13a49-132">Azure yığın Geliştirme Seti, bir üretim ortamına olarak kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="13a49-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="13a49-133">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="13a49-133">Additional resources</span></span>

-   <span data-ttu-id="13a49-134">**Azure karma bulut**</span><span class="sxs-lookup"><span data-stu-id="13a49-134">**Azure hybrid cloud**</span></span>

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   <span data-ttu-id="13a49-135">**Azure yığını**</span><span class="sxs-lookup"><span data-stu-id="13a49-135">**Azure Stack**</span></span>

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   <span data-ttu-id="13a49-136">**Windows kapsayıcıları için Active Directory hizmet hesapları**</span><span class="sxs-lookup"><span data-stu-id="13a49-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   <span data-ttu-id="13a49-137">**Active Directory desteği olan bir kapsayıcı oluşturma**</span><span class="sxs-lookup"><span data-stu-id="13a49-137">**Create a container with Active Directory support**</span></span>

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   <span data-ttu-id="13a49-138">**Azure karma avantajı lisanslama**</span><span class="sxs-lookup"><span data-stu-id="13a49-138">**Azure Hybrid Benefit licensing**</span></span>

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
<span data-ttu-id="13a49-139">[Önceki](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[sonraki](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="13a49-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
