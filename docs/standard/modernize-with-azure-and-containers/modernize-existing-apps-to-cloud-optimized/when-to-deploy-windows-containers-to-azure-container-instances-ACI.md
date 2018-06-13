---
title: Azure kapsayıcı örnekleri (ACI) Windows kapsayıcıları dağıtma zamanı
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Azure kapsayıcı örnekleri (ACI) Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958226"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="4149d-103">Azure kapsayıcı örnekleri (ACI) Windows kapsayıcıları dağıtma zamanı</span><span class="sxs-lookup"><span data-stu-id="4149d-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="4149d-104">Ana değer teklifinde hemen kapsayıcıları için dağıtabilirsiniz ve o ortamınızı sürdürmek gerekmeyen olan Azure kapsayıcı örnekleri, yükseltme / underlaying işletim sistemi veya tüm saydamdır VM'ler, düzeltme eki gerekmez ve yalnızca dağıtma kapsayıcıları bir kullanıma hazır ortamına.</span><span class="sxs-lookup"><span data-stu-id="4149d-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlaying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="4149d-105">Azure VM'ler ile kapsayıcıları, bu nedenle temelde kullandığınızda nedenleri ve ACI kullanmak istediğiniz zaman senaryoları ana senaryoları ile benzerdir, Azure kapsayıcı örneği kullanmak için ana senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4149d-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

-   <span data-ttu-id="4149d-106">**Geliştirme ve Test senaryoları**</span><span class="sxs-lookup"><span data-stu-id="4149d-106">**Dev/Test scenarios**</span></span>
-   <span data-ttu-id="4149d-107">**Görev Otomasyonu**</span><span class="sxs-lookup"><span data-stu-id="4149d-107">**Task automation**</span></span>
-   <span data-ttu-id="4149d-108">**CI/CD aracıları**</span><span class="sxs-lookup"><span data-stu-id="4149d-108">**CI/CD agents**</span></span>
-   <span data-ttu-id="4149d-109">**Küçük/ölçek toplu işleme**</span><span class="sxs-lookup"><span data-stu-id="4149d-109">**Small/scale batch processing**</span></span>
-   <span data-ttu-id="4149d-110">**Basit web uygulamaları**</span><span class="sxs-lookup"><span data-stu-id="4149d-110">**Simple web apps**</span></span>

<span data-ttu-id="4149d-111">Orta senaryo ACI için basit web apps senaryodur ancak ACI içinde yalnızca tek kapsayıcı örnek kapsayıcı görüntü başına olabileceği için yüksek oranda kullanılabilir olmaz ve yalnızca sınırlı ölçeklenebilirlik olduğunu dikkate alın.</span><span class="sxs-lookup"><span data-stu-id="4149d-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="4149d-112">Ancak, yalnızca tek kapsayıcı örnekleri sağladığından bile ACI altyapı olarak kabul edildiğinde, Windows Server ile normal Azure vm'lerine karşılaştırıldığında büyük bir yararı yoktur.</span><span class="sxs-lookup"><span data-stu-id="4149d-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="4149d-113">ACI, kendi kendine tutulan ortamına yalnızca kapsayıcıları dağıtın ve yalnızca bu kapsayıcı için ödeme yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="4149d-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="4149d-114">Burada, VM'ler ile kapsayıcıları kullanabilecek Çoğu senaryoda daha iyi kadar platformu olacak şekilde korumak/güncelleştirme/düzeltme eki VM gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4149d-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="4149d-115">ACI kullanarak doğrudan İleri, yalnızca bir kapsayıcıyı dağıtmak, yalnızca kapsayıcıları dağıtın VM ortamı oluşturmak için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="4149d-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="4149d-116">Azure kapsayıcı örnekleri (ACI) ana avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4149d-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

-   <span data-ttu-id="4149d-117">Sunucuları yönetmek zorunda kalmadan kapsayıcıları çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4149d-117">Run containers without managing servers</span></span>
-   <span data-ttu-id="4149d-118">İsteğe bağlı kapsayıcılarla çeviklik artırın</span><span class="sxs-lookup"><span data-stu-id="4149d-118">Increase agility with containers on demand</span></span>
-   <span data-ttu-id="4149d-119">Eşi görülmemiş Basitlik ve hız ile bulut kapsayıcıları dağıtın — tek bir komutla.</span><span class="sxs-lookup"><span data-stu-id="4149d-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span> 
-   <span data-ttu-id="4149d-120">Hiper yönetici yalıtımlı güvenli uygulamalar</span><span class="sxs-lookup"><span data-stu-id="4149d-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="4149d-121">Kısacası, ACI ile uygulamaları hızlı sanal makineleri yönetme veya yeni araçları öğrenmek zorunda kalmadan geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4149d-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="4149d-122">Yalnızca uygulamanız, bulutta çalışan bir kapsayıcıda değil.</span><span class="sxs-lookup"><span data-stu-id="4149d-122">It's just your application, in a container, running in the cloud.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="4149d-123">[Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[sonraki](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="4149d-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
