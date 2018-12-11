---
title: Azure Container Instances'a (ACI) Windows kapsayıcıları dağıtma zamanı
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Azure Container Instances'a (ACI) Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 297461f1403ab2d6ca6fd63a05d5ded7f210483e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128105"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="35f15-103">Azure Container Instances'a (ACI) Windows kapsayıcıları dağıtma zamanı</span><span class="sxs-lookup"><span data-stu-id="35f15-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="35f15-104">Ana değer önerisi hemen kapsayıcılar için uygulamayı dağıtmak ve bu ortamı sürdürmeniz gerekmez olan Azure Container Instances, yükseltmek/yama uygulamak underlaying işletim sistemi ya da tüm saydam olan VM'ler ihtiyacınız yoksa ve yalnızca dağıtma kullanıma hazır bir ortam kapsayıcılarına.</span><span class="sxs-lookup"><span data-stu-id="35f15-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlaying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="35f15-105">ACI kullanmak istediğiniz zaman senaryoları ve nedeni, Azure Vm'leri kapsayıcılar ile aslında kullandığınızda yönelik temel senaryolar için benzer, Azure Container Instances kullanılarak için ana senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="35f15-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

-   <span data-ttu-id="35f15-106">**Geliştirme/Test senaryoları**</span><span class="sxs-lookup"><span data-stu-id="35f15-106">**Dev/Test scenarios**</span></span>
-   <span data-ttu-id="35f15-107">**Görev Otomasyonu**</span><span class="sxs-lookup"><span data-stu-id="35f15-107">**Task automation**</span></span>
-   <span data-ttu-id="35f15-108">**CI/CD aracıları**</span><span class="sxs-lookup"><span data-stu-id="35f15-108">**CI/CD agents**</span></span>
-   <span data-ttu-id="35f15-109">**Küçük/ölçek toplu işleme**</span><span class="sxs-lookup"><span data-stu-id="35f15-109">**Small/scale batch processing**</span></span>
-   <span data-ttu-id="35f15-110">**Basit web uygulamaları**</span><span class="sxs-lookup"><span data-stu-id="35f15-110">**Simple web apps**</span></span>

<span data-ttu-id="35f15-111">Basit web apps senaryosu için ACI adil bir senaryodur ancak ACI kapsayıcı görüntüsü başına tek bir kapsayıcı örneği yalnızca olabileceği için yüksek oranda kullanılabilir olmaz ve yalnızca ölçeklenebilirlik sınırlı olduğunu dikkate alın.</span><span class="sxs-lookup"><span data-stu-id="35f15-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="35f15-112">Ancak, yalnızca tek bir container Instances sağladığından ACI altyapı bile edildiği durumlarda, Windows Server normal Azure Vm'lerle karşılaştırıldığında çok büyük bir avantajı yoktur.</span><span class="sxs-lookup"><span data-stu-id="35f15-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="35f15-113">ACI, şirket içinde tutulan bir ortama yalnızca kapsayıcıları dağıtın ve yalnızca bu kapsayıcılar için ücret ödersiniz.</span><span class="sxs-lookup"><span data-stu-id="35f15-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="35f15-114">Burada, sanal makineleri ile kapsayıcıları kullanıyor olabilecek çoğu senaryo için bir çok daha iyi platformu, bu nedenle korumak/güncelleştirme/düzeltme eki için Vm'leri, gerekmez.</span><span class="sxs-lookup"><span data-stu-id="35f15-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="35f15-115">ACI kullanarak oldukça kolaydır, yalnızca bir kapsayıcı dağıtma, kapsayıcıları dağıttığınız yalnızca bir sanal makine ortamınızı oluşturmaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="35f15-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="35f15-116">Azure Container Instances'a (ACI) başlıca avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="35f15-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

-   <span data-ttu-id="35f15-117">Kapsayıcıları, sunucu yönetmeye gerek kalmadan çalıştırın</span><span class="sxs-lookup"><span data-stu-id="35f15-117">Run containers without managing servers</span></span>
-   <span data-ttu-id="35f15-118">İsteğe bağlı kapsayıcılarla çevikliği artırın</span><span class="sxs-lookup"><span data-stu-id="35f15-118">Increase agility with containers on demand</span></span>
-   <span data-ttu-id="35f15-119">Bulutta hiç olmadığı kadar kolay ve hızlı kapsayıcılar dağıtma — tek bir komutla.</span><span class="sxs-lookup"><span data-stu-id="35f15-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span> 
-   <span data-ttu-id="35f15-120">Hiper yönetici yalıtımı ile uygulamaları güvenli hale getirin</span><span class="sxs-lookup"><span data-stu-id="35f15-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="35f15-121">Kısacası, ACI ile uygulamaları hızlı sanal makineler yönetmeden veya yeni araçlar öğrenmek zorunda kalmadan geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35f15-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="35f15-122">Yalnızca uygulamanızda, bir kapsayıcı içinde bulutta olduğu.</span><span class="sxs-lookup"><span data-stu-id="35f15-122">It's just your application, in a container, running in the cloud.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="35f15-123">[Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
>[İleri](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="35f15-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>