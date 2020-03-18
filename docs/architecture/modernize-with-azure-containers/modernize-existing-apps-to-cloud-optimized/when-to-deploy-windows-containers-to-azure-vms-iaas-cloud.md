---
title: Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Windows Kapsayıcılarını Azure VM'lere (IaaS bulutu) ne zaman dağıtılır?
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676900"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="74a9a-103">Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?</span><span class="sxs-lookup"><span data-stu-id="74a9a-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="74a9a-104">Kuruluşunuz Azure VM kullanıyorsa, Windows Kapsayıcıları kullanıyor sanız bile, Hala IaaS ile uğraşıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="74a9a-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="74a9a-105">Bu, yük dengeli bir altyapıda birden fazla VM'ye dağıtmanız gerektiğinde, altyapı işlemleri, VM OS yamaları ve yüksek ölçeklenebilir uygulamalar için altyapı karmaşıklığı yla başa çıkmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="74a9a-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="74a9a-106">Windows Kapsayıcılarını Azure VM'de kullanmak için temel senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="74a9a-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

- <span data-ttu-id="74a9a-107">**Geliştirme/test ortamı**: Buluttaki Bir VM, bulutta geliştirme ve test için idealdir.</span><span class="sxs-lookup"><span data-stu-id="74a9a-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="74a9a-108">İhtiyaçlarınıza bağlı olarak ortamı hızla oluşturabilir veya durdurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74a9a-108">You can rapidly create or stop the environment depending on your needs.</span></span>

- <span data-ttu-id="74a9a-109">**Küçük ve orta ölçeklenebilirlik gereksinimleri**: Üretim ortamınız için sadece birkaç VM'ye ihtiyaç duyabileceğiniz senaryolarda, orkestratörler gibi daha gelişmiş PaaS ortamlarına taşınana kadar az sayıda VM'yi yönetmek uygun fiyatlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="74a9a-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

- <span data-ttu-id="74a9a-110">**Varolan dağıtım araçlarıyla üretim ortamı**: VM'lere veya çıplak metal sunuculara (Puppet veya benzeri araçlar gibi) karmaşık dağıtımlar yapmak için araçlara yatırım yaptığınız şirket içi bir ortamdan hareket ediyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74a9a-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="74a9a-111">Üretim ortamı dağıtım yordamlarında en az değişiklikle buluta geçmek için, bu araçları Azure VM'lerine dağıtmak için kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74a9a-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="74a9a-112">Ancak, dağıtım deneyimini geliştirmek için dağıtım birimi olarak Windows Kapsayıcıları kullanmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="74a9a-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="74a9a-113">[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[Sonraki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="74a9a-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>
