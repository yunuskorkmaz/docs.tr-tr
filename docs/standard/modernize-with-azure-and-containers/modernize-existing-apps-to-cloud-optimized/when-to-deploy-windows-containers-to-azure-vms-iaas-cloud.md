---
title: Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Azure Vm'lere (Iaas Bulutu) Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 8bff4297f99b6549b80604860985568445bbdc0b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625654"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="7fe09-103">Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?</span><span class="sxs-lookup"><span data-stu-id="7fe09-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="7fe09-104">Ayrıca Windows kapsayıcılarını kullanıyor olsanız bile kuruluşunuz Azure Vm'leri kullanıyor, Iaas uğraşmanızı hala demektir.</span><span class="sxs-lookup"><span data-stu-id="7fe09-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="7fe09-105">Bir yük dengeli altyapısında birden çok VM dağıtmak ihtiyacınız olduğunda bu uğraşmanızı altyapı işlemleri, VM işletim sistemi düzeltme ekleri ve altyapı karmaşıklığını yüksek düzeyde ölçeklenebilir uygulamalar için anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7fe09-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="7fe09-106">Bir Azure sanal Makinesinde Windows kapsayıcılarını kullanmaya yönelik temel senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7fe09-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

- <span data-ttu-id="7fe09-107">**Geliştirme/test ortamı**: Bir VM bulut geliştirme ve test amacıyla buluta mükemmeldir.</span><span class="sxs-lookup"><span data-stu-id="7fe09-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="7fe09-108">Hızlı bir şekilde oluşturabilir veya gereksinimlerinize bağlı olarak ortamı durdurun.</span><span class="sxs-lookup"><span data-stu-id="7fe09-108">You can rapidly create or stop the environment depending on your needs.</span></span>

- <span data-ttu-id="7fe09-109">**Küçük ve orta ölçekli ölçeklenebilirlik ihtiyacı**: Düzenleyiciler gibi daha gelişmiş PaaS ortamlara taşınana kadar burada yalnızca birkaç sanal makinelerinin üretim ortamınız için ihtiyacınız olabilecek senaryolarda, uygun maliyetli az sayıda VM yönetme olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fe09-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

- <span data-ttu-id="7fe09-110">**Üretim ortamında var olan dağıtım araçlarıyla**: Bir şirket içi ortamdan sanal makineleri veya çıplak sunucuları (örneğin, Puppet veya benzer Araçlar) karmaşık dağıtımları yapmak için Araçlar, yatırım yapmış taşıma.</span><span class="sxs-lookup"><span data-stu-id="7fe09-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="7fe09-111">Üretim ortamına dağıtım yordamları için minimum değişiklikle buluta taşımak için Azure Vm'leri dağıtmak için bu araçları kullanmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="7fe09-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="7fe09-112">Ancak, Windows kapsayıcıları dağıtım deneyimini iyileştirmek üzere dağıtım birimi olarak kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7fe09-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7fe09-113">[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[İleri](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="7fe09-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>