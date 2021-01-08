---
title: Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Azure VM 'lerine (IaaS bulutu) Windows kapsayıcıları ne zaman dağıtılır
ms.date: 12/21/2020
ms.openlocfilehash: 64ba53fa56227266ee0e61a128d18373a2dbbc93
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025100"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="47a45-103">Azure VM’lere (IaaS bulutu) Windows Kapsayıcıları ne zaman dağıtılmalıdır?</span><span class="sxs-lookup"><span data-stu-id="47a45-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="47a45-104">Kuruluşunuz Azure VM 'Leri kullanıyorsa, aynı zamanda Windows kapsayıcıları kullanıyor olsanız bile IaaS ile ilgilenmeye devam edersiniz.</span><span class="sxs-lookup"><span data-stu-id="47a45-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="47a45-105">Yani, yük dengeli bir altyapıda birden çok VM 'ye dağıtmanız gerektiğinde, yüksek düzeyde ölçeklenebilir uygulamalar için altyapı işlemleri, VM OS yamaları ve altyapı karmaşıklığı ile ilgilenme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="47a45-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load-balanced infrastructure.</span></span> <span data-ttu-id="47a45-106">Azure VM 'de Windows kapsayıcıları kullanmaya yönelik temel senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="47a45-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

- <span data-ttu-id="47a45-107">Geliştirme ve **test ortamı**: BULUTTAKI bir VM, bulutta geliştirme ve test için mükemmeldir.</span><span class="sxs-lookup"><span data-stu-id="47a45-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="47a45-108">İhtiyaçlarınıza bağlı olarak ortamı hızlı bir şekilde oluşturabilir veya durdurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47a45-108">You can rapidly create or stop the environment depending on your needs.</span></span>

- <span data-ttu-id="47a45-109">**Küçük ve orta ölçeklenebilirlik ihtiyaçları**: üretim ortamınız için yalnızca birkaç VM 'niz olması gerekebileceği senaryolarda, daha gelişmiş PaaS ortamlarına geçiş yapana kadar birkaç sanal makineyi yönetmek uygun maliyetli olabilir.</span><span class="sxs-lookup"><span data-stu-id="47a45-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a few VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

- <span data-ttu-id="47a45-110">**Mevcut dağıtım araçlarıyla üretim ortamı**: VM 'lere veya çıplak sunuculara (Pupevcil hayvan veya benzer araçlar gibi) karmaşık dağıtımlar oluşturmak için, araçlara yatırım yaptığınız şirket içi bir ortamdan geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47a45-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="47a45-111">Üretim ortamı dağıtım yordamlarına en az değişiklikle buluta geçmek için bu araçları Azure VM 'lerine dağıtmak üzere kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47a45-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="47a45-112">Ancak, dağıtım deneyimini geliştirmek için dağıtım birimi olarak Windows kapsayıcıları kullanmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="47a45-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="47a45-113">[Önceki](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md) 
> [Sonraki](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="47a45-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>
