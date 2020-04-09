---
title: Windows Kapsayıcıları Azure Kapsayıcı Örneklerine (ACI) ne zaman dağıtılır?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Windows Kapsayıcıları Azure Kapsayıcı Örneklerine (ACI) ne zaman dağıtılır?
ms.date: 04/29/2018
ms.openlocfilehash: 6c889db6f0475f24a196144c7fb62faec4c173ed
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989161"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="b00e9-103">Windows Kapsayıcıları Azure Kapsayıcı Örneklerine (ACI) ne zaman dağıtılır?</span><span class="sxs-lookup"><span data-stu-id="b00e9-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="b00e9-104">Azure Kapsayıcı Örnekleri ana değer teklifi, kapsayıcıları hemen ona dağıtabilmeniz ve bu ortamı korumanız gerekmemektedir, temel işletim sistemini veya VM'leri yükseltmeniz/düzeltmeniz gerekmez, tüm bunlar saydamdır ve kapsayıcıları kullanıma hazır bir ortama dağıtırsınız.</span><span class="sxs-lookup"><span data-stu-id="b00e9-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don't need to maintain that environment, you don't need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="b00e9-105">ACI kullanmak istediğiniz nedenler ve senaryolar, kapsayıcılarla Azure VM'leri kullandığınızda ana senaryolara benzer, bu nedenle temel olarak Azure Kapsayıcı Örnekleri'ni kullanmak için temel senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b00e9-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="b00e9-106">**Dev/Test senaryoları**</span><span class="sxs-lookup"><span data-stu-id="b00e9-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="b00e9-107">**Görev otomasyonu**</span><span class="sxs-lookup"><span data-stu-id="b00e9-107">**Task automation**</span></span>
- <span data-ttu-id="b00e9-108">**CI/CD aracıları**</span><span class="sxs-lookup"><span data-stu-id="b00e9-108">**CI/CD agents**</span></span>
- <span data-ttu-id="b00e9-109">**Küçük/ölçekli toplu işleme**</span><span class="sxs-lookup"><span data-stu-id="b00e9-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="b00e9-110">**Basit web uygulamaları**</span><span class="sxs-lookup"><span data-stu-id="b00e9-110">**Simple web apps**</span></span>

<span data-ttu-id="b00e9-111">Basit web uygulamaları senaryosu ACI için adil bir senaryodur, ancak ACI'da konteyner görüntüsü başına yalnızca tek bir kapsayıcı örneğine sahip olabileceğiniz için yüksek kullanılabilirliğe sahip olmanızı ve yalnızca ölçeklenebilirliğe sahip olduğunuzu göz önünde bulundurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b00e9-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won't have high availability and only have limited scalability.</span></span>

<span data-ttu-id="b00e9-112">Ancak, Yalnızca tek kapsayıcı örnekleri sağladığı için ACI altyapı olarak kabul edilse bile, Windows Server'a sahip normal Azure VM'lere kıyasla büyük bir avantaj sağlar.</span><span class="sxs-lookup"><span data-stu-id="b00e9-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="b00e9-113">ACI ile, sadece kendi kendine bakımlı bir ortama konteyner dağıtmak ve sadece bu konteynerler için ödeme.</span><span class="sxs-lookup"><span data-stu-id="b00e9-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="b00e9-114">VM'leri korumanız/güncellemeniz/yamanız gerekmez, bu nedenle kapsayıcılı VM'ler kullandığınız çoğu senaryo için çok daha iyi bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="b00e9-114">You don't need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="b00e9-115">ACI kullanarak düz, sadece bir kapsayıcı dağıtmak, sadece kapsayıcıdağıtmak bir VM ortamı oluşturmak için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="b00e9-115">Using ACI is straight forward, you just deploy a container, there's no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="b00e9-116">Azure Kapsayıcı Örnekleri'nin (ACI) başlıca avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b00e9-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="b00e9-117">Sunucuları yönetmeden kapsayıcıları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b00e9-117">Run containers without managing servers</span></span>
- <span data-ttu-id="b00e9-118">Talep üzerine konteynerler ile çevikliği artırın</span><span class="sxs-lookup"><span data-stu-id="b00e9-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="b00e9-119">Tek bir komutla, daha önce görülmemiş basitlik ve hızile kapsayıcıları buluta dağıtın.</span><span class="sxs-lookup"><span data-stu-id="b00e9-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="b00e9-120">Hipervizör izolasyonlu güvenli uygulamalar</span><span class="sxs-lookup"><span data-stu-id="b00e9-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="b00e9-121">Kısacası, ACI ile sanal makineleri yönetmeden veya yeni araçlar öğrenmek zorunda kalmadan uygulamaları hızlı bir şekilde geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b00e9-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="b00e9-122">Sadece uygulamanız, bir kapta, bulutta çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="b00e9-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="b00e9-123">[Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Sonraki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="b00e9-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
