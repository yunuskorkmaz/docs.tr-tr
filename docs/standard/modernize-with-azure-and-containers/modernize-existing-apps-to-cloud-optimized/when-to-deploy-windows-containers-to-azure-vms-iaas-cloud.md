---
title: Azure sanal makinelerini (Iaas bulut) Windows kapsayıcıları dağıtma zamanı
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Azure sanal makinelerini (Iaas bulut) Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 7472745577f414062b460fd71ab45bae85d7a62e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="22ff6-103">Azure sanal makinelerini (Iaas bulut) Windows kapsayıcıları dağıtma zamanı</span><span class="sxs-lookup"><span data-stu-id="22ff6-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="22ff6-104">Ayrıca Windows kapsayıcıları bile kullanıyorsanız, kuruluşunuzun Azure VM'ler, kullanarak, Iaas postalarla hala demektir.</span><span class="sxs-lookup"><span data-stu-id="22ff6-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="22ff6-105">Yük dengeli altyapısındaki birden çok VM dağıtmak gerektiğinde, yüksek düzeyde ölçeklenebilir uygulamalar için altyapı işlemler, VM OS düzeltme ekleri ve altyapı karmaşıklığı o postalarla anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="22ff6-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="22ff6-106">Bir Azure VM Windows kapsayıcıları kullanma için ana senaryoları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="22ff6-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="22ff6-107">**Geliştirme ve test ortamı**: A VM bulut geliştirme ve bulutta sınama için mükemmeldir.</span><span class="sxs-lookup"><span data-stu-id="22ff6-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="22ff6-108">Hızlı bir şekilde oluşturmak veya ortamı gereksinimlerinize bağlı olarak durdur.</span><span class="sxs-lookup"><span data-stu-id="22ff6-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="22ff6-109">**Küçük ve orta ölçekli ölçeklenebilirlik gereken**: orchestrators gibi daha gelişmiş PaaS ortamlara taşıyabilirsiniz kadar burada ihtiyacınız olabilecek yalnızca VM'ler birkaç üretim ortamınıza senaryolarda, az sayıda sanal makineleri yönetme uygun maliyetli olabilir.</span><span class="sxs-lookup"><span data-stu-id="22ff6-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="22ff6-110">**Üretim ortamında var olan dağıtım araçlarıyla**: içinde yatırım VM'ler veya tam sunucuları (Puppet veya benzer araçları gibi) karmaşık dağıtımlar yapmak için Araçları'nda bir şirket içi ortamından taşıma.</span><span class="sxs-lookup"><span data-stu-id="22ff6-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="22ff6-111">Üretim ortamında dağıtım yordamları için minimum değişiklikle buluta taşımak için Azure sanal makinelerini dağıtmak için bu araçları kullanın devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="22ff6-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="22ff6-112">Ancak, dağıtım deneyimini geliştirmek için dağıtım birimi olarak Windows kapsayıcılar kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="22ff6-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="22ff6-113">[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[sonraki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="22ff6-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>
