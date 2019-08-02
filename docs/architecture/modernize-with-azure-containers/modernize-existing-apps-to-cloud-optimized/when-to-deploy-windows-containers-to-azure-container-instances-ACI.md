---
title: Azure Container Instances (ACI) için Windows kapsayıcıları ne zaman dağıtılır
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Azure Container Instances (ACI) için Windows kapsayıcıları ne zaman dağıtılır
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676909"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="f892b-103">Azure Container Instances (ACI) için Windows kapsayıcıları ne zaman dağıtılır</span><span class="sxs-lookup"><span data-stu-id="f892b-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="f892b-104">Ana değer teklifini Azure Container Instances, kapsayıcıyı buna doğru bir şekilde dağıtmanızı ve bu ortamın bakımını yapmanıza gerek duymamanız, temel alınan işletim sistemini veya VM 'Leri yükseltmeniz/düzeltme eki uygulamanız gerekmez, hepsi saydam ve yeni bir dağıtım yapmanız gerekmez kullanıma hazırlama ortamına kapsayıcılar.</span><span class="sxs-lookup"><span data-stu-id="f892b-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="f892b-105">Azure VM 'lerini kapsayıcılarla birlikte kullanırken ACI 'yi kullanmak isteyebileceğiniz nedenler ve senaryolar ana senaryolara benzerdir, bu nedenle temel olarak Azure Container Instances kullanmaya yönelik temel senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f892b-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="f892b-106">**Geliştirme ve test senaryoları**</span><span class="sxs-lookup"><span data-stu-id="f892b-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="f892b-107">**Görev Otomasyonu**</span><span class="sxs-lookup"><span data-stu-id="f892b-107">**Task automation**</span></span>
- <span data-ttu-id="f892b-108">**CI/CD aracıları**</span><span class="sxs-lookup"><span data-stu-id="f892b-108">**CI/CD agents**</span></span>
- <span data-ttu-id="f892b-109">**Küçük/ölçekli toplu iş işleme**</span><span class="sxs-lookup"><span data-stu-id="f892b-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="f892b-110">**Basit Web uygulamaları**</span><span class="sxs-lookup"><span data-stu-id="f892b-110">**Simple web apps**</span></span>

<span data-ttu-id="f892b-111">Basit Web Apps senaryosu, acı için bir teme senaryosudur, ancak her kapsayıcı görüntüsü için yalnızca tek bir kapsayıcı örneğiniz olduğundan, yüksek kullanılabilirliğe sahip olmayacaktır ve yalnızca sınırlı ölçeklenebilirliğe sahip kalmazsınız.</span><span class="sxs-lookup"><span data-stu-id="f892b-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="f892b-112">Ancak tek bir kapsayıcı örnekleri sağladığından, acı altyapısı olarak kabul edilse bile, Windows Server ile normal Azure VM 'lerine kıyasla büyük bir avantaj vardır.</span><span class="sxs-lookup"><span data-stu-id="f892b-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="f892b-113">ACI ile, kapsayıcıları yalnızca kendi kendine korunan bir ortama dağıtırsınız ve yalnızca bu kapsayıcılar için ödeme yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="f892b-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="f892b-114">VM 'Leri korumanız/güncelleştirmeniz gerekmez, bu nedenle kapsayıcılarla VM 'Leri kullandığınız birçok senaryo için çok daha iyi bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="f892b-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="f892b-115">ACI 'yi kullanarak, yalnızca bir kapsayıcı dağıtırsınız, yalnızca kapsayıcıları dağıttığınız bir VM ortamı oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f892b-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="f892b-116">Azure Container Instances (ACI) 'nin başlıca avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f892b-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="f892b-117">Sunucuları yönetmeksizin kapsayıcıları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f892b-117">Run containers without managing servers</span></span>
- <span data-ttu-id="f892b-118">İsteğe bağlı kapsayıcılarla çevikliği artırma</span><span class="sxs-lookup"><span data-stu-id="f892b-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="f892b-119">Tek bir komutla, kapsayıcıları, daha önce basit ve hızlı bir şekilde buluta dağıtın.</span><span class="sxs-lookup"><span data-stu-id="f892b-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="f892b-120">Hiper yönetici yalıtımına sahip uygulamaları güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="f892b-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="f892b-121">Kısaca, ACI ile, sanal makineleri yönetmeden veya yeni araçlar öğrenmeden uygulamalar geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="f892b-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="f892b-122">Yalnızca uygulamanız bulutta çalışan bir kapsayıcıda yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="f892b-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="f892b-123">[Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)İleri
> [](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="f892b-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
