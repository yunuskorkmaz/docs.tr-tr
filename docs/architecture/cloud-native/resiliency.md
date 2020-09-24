---
title: Bulutta yerel dayanıklılık
description: Azure için Cloud Native .NET uygulamaları tasarlama | Cloud Native dayanıklılık
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 5c4fb261515c151fd666cc33cbb020447716c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163563"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="e2ae5-103">Bulutta yerel dayanıklılık</span><span class="sxs-lookup"><span data-stu-id="e2ae5-103">Cloud-native resiliency</span></span>

<span data-ttu-id="e2ae5-104">Dayanıklılık, sisteminizin hataya tepki verme ve hala işlevsel olmaya devam etme yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="e2ae5-105">Hatayı önleme, ancak hatayı kabul etme ve buluta yerel hizmetlerinizi oluşturma hakkında bilgi almak için bu değildir.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-105">It's not about avoiding failure, but accepting failure and constructing your cloud-native services to respond to it.</span></span> <span data-ttu-id="e2ae5-106">Mümkün olduğunca hızlı bir şekilde çalışır duruma geri dönmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-106">You want to return to a fully functioning state quickly as possible.</span></span>

<span data-ttu-id="e2ae5-107">Her şeyin tek bir işlemde birlikte çalıştığı geleneksel tek parçalı uygulamalardan farklı olarak, bulutta yerel sistemler Şekil 6-1 ' de gösterildiği gibi dağıtılmış bir mimarinin ayracına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e2ae5-107">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace a distributed architecture as shown in Figure 6-1:</span></span>

![Dağıtılmış bulutta yerel ortam](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="e2ae5-109">**Şekil 6-1.**</span><span class="sxs-lookup"><span data-stu-id="e2ae5-109">**Figure 6-1.**</span></span> <span data-ttu-id="e2ae5-110">Dağıtılmış bulutta yerel ortam</span><span class="sxs-lookup"><span data-stu-id="e2ae5-110">Distributed cloud-native environment</span></span>

<span data-ttu-id="e2ae5-111">Önceki şekilde, her mikro hizmet ve bulut tabanlı [yedekleme hizmeti](https://12factor.net/backing-services) , ağ tabanlı çağrılar üzerinden iletişim kurarak sunucu altyapısı genelinde ayrı bir işlemde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-111">In the previous figure, each microservice and cloud-based [backing service](https://12factor.net/backing-services) execute in a separate process, across server infrastructure, communicating via network-based calls.</span></span>

<span data-ttu-id="e2ae5-112">Bu ortamda çalışırken, bir hizmet birçok farklı güçlüklere duyarlı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e2ae5-112">Operating in this environment, a service must be sensitive to many different challenges:</span></span>

- <span data-ttu-id="e2ae5-113">Beklenmeyen ağ gecikmesi-bir hizmet isteğinin alıcıya ve geri yolculuğu için geçen süre.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-113">Unexpected network latency - the time for a service request to travel to the receiver and back.</span></span>

- <span data-ttu-id="e2ae5-114">[Geçici hatalar](/azure/architecture/best-practices/transient-faults) -kısa süreli ağ bağlantısı hataları.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-114">[Transient faults](/azure/architecture/best-practices/transient-faults) - short-lived network connectivity errors.</span></span>

- <span data-ttu-id="e2ae5-115">Uzun süre çalışan bir zaman uyumlu işlem ile engelleme.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-115">Blockage by a long-running synchronous operation.</span></span>

- <span data-ttu-id="e2ae5-116">Kilitlenen ve yeniden başlatılan veya taşınan bir ana bilgisayar işlemi.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-116">A host process that has crashed and is being restarted or moved.</span></span>

- <span data-ttu-id="e2ae5-117">Kısa bir süre yanıt vermeyen aşırı yüklenmiş bir mikro hizmet.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-117">An overloaded microservice that can't respond for a short time.</span></span>

- <span data-ttu-id="e2ae5-118">Sıralı yükseltme veya bir hizmeti bir düğümden diğerine taşıma gibi uçuş için bir Orchestrator işlemi.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-118">An in-flight orchestrator operation such as a rolling upgrade or moving a service from one node to another.</span></span>

- <span data-ttu-id="e2ae5-119">Donanım sorunları.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-119">Hardware failures.</span></span>

<span data-ttu-id="e2ae5-120">Bulut platformları, bu altyapı sorunlarının çoğunu algılayabilir ve azaltır.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-120">Cloud platforms can detect and mitigate many of these infrastructure issues.</span></span> <span data-ttu-id="e2ae5-121">Hizmetinizi yeniden başlatabilir, ölçeklendirebilir ve hatta farklı bir düğüme yeniden dağıtabilir.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-121">It may restart, scale out, and even redistribute your service to a different node.</span></span>  <span data-ttu-id="e2ae5-122">Ancak, bu yerleşik korumadan tam olarak yararlanabilmek için, bu dinamik ortamda BT ve Misyonumuz 'e tepki vermek üzere hizmetlerinizi tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-122">However, to take full advantage of this built-in protection, you must design your services to react to it and thrive in this dynamic environment.</span></span>

<span data-ttu-id="e2ae5-123">Aşağıdaki bölümlerde, hizmet ve yönetilen bulut kaynaklarınızın kapalı kalma süresini ve kesintiyi en aza indirmek için yararlanabilen savunma tekniklerini keşfedeceğiz.</span><span class="sxs-lookup"><span data-stu-id="e2ae5-123">In the following sections, we'll explore defensive techniques that your service and managed cloud resources can leverage to minimize downtime and disruption.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e2ae5-124">[Önceki](elastic-search-in-azure.md) 
> [Sonraki](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="e2ae5-124">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>
