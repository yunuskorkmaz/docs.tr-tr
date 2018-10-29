---
title: Ortak kapsayıcı tasarım ilkeleri
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3af174279e8b6f56a10413817b05ef68cfcabea5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202184"
---
# <a name="common-container-design-principles"></a><span data-ttu-id="8f48a-103">Ortak kapsayıcı tasarım ilkeleri</span><span class="sxs-lookup"><span data-stu-id="8f48a-103">Common container design principles</span></span>

<span data-ttu-id="8f48a-104">Önceden geliştirme işlemine başlama kapsayıcıları kullanma ile ilgili bahseden değer birkaç temel kavram vardır.</span><span class="sxs-lookup"><span data-stu-id="8f48a-104">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="8f48a-105">Kapsayıcı işlemi eşittir</span><span class="sxs-lookup"><span data-stu-id="8f48a-105">Container equals a process</span></span>

<span data-ttu-id="8f48a-106">Kapsayıcı modelinde, tek bir işlem bir kapsayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f48a-106">In the container model, a container represents a single process.</span></span> <span data-ttu-id="8f48a-107">Kapsayıcı işlemi sınır olarak tanımlayarak, Ölçek veya toplu kapalı, işlemleri için kullanılan ilkel oluşturmaya başlamadan.</span><span class="sxs-lookup"><span data-stu-id="8f48a-107">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="8f48a-108">Bir Docker kapsayıcısı çalıştırdığınızda, gördüğünüz bir [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) tanımı.</span><span class="sxs-lookup"><span data-stu-id="8f48a-108">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definition.</span></span> <span data-ttu-id="8f48a-109">Bu işlem ve kapsayıcı ömrünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8f48a-109">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="8f48a-110">İşlem tamamlandığında, kapsayıcı yaşam döngüsü sona erer.</span><span class="sxs-lookup"><span data-stu-id="8f48a-110">When the process completes, the container life cycle ends.</span></span> <span data-ttu-id="8f48a-111">Web sunucuları ve Microsoft Azure uygulanmış toplu işler gibi kısa süreli işlemler gibi uzun süre çalışan işlem [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/).</span><span class="sxs-lookup"><span data-stu-id="8f48a-111">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="8f48a-112">İşlem başarısız olursa, kapsayıcı sona erer ve orchestrator sürüyorsa.</span><span class="sxs-lookup"><span data-stu-id="8f48a-112">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="8f48a-113">Orchestrator çalışan beş örneklerinin tutmak istendi ve biri başarısız olursa, orchestrator başarısız işlemi değiştirmek için başka bir kapsayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f48a-113">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="8f48a-114">Bir batch işinde parametrelerle işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="8f48a-114">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="8f48a-115">İşlem tamamlandığında, iş tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="8f48a-115">When the process completes, the work is complete.</span></span>

<span data-ttu-id="8f48a-116">Birden çok işlem tek bir kapsayıcıda çalıştırmak istediğiniz bir senaryo bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f48a-116">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="8f48a-117">Herhangi bir mimari belgesinde yoktur hiçbir zaman bir "," ya da her zaman olduğu bir "her zaman."</span><span class="sxs-lookup"><span data-stu-id="8f48a-117">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="8f48a-118">Birden çok işlem gerektiren senaryolar için yaygın bir düzen kullanmaktır [gözetmen](http://supervisord.org/).</span><span class="sxs-lookup"><span data-stu-id="8f48a-118">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8f48a-119">[Önceki](design-docker-applications.md)
[İleri](monolithic-applications.md)</span><span class="sxs-lookup"><span data-stu-id="8f48a-119">[Previous](design-docker-applications.md)
[Next](monolithic-applications.md)</span></span>
