---
title: Dayanıklı uygulamalar uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Dayanıklı uygulamalar uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: dc0db8f0cdfa77bcca467c3c632b3d93de8851d8
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875132"
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="36d6f-103">Dayanıklı uygulamalar uygulama</span><span class="sxs-lookup"><span data-stu-id="36d6f-103">Implementing Resilient Applications</span></span>

<span data-ttu-id="36d6f-104">*Bulut tabanlı uygulamalar ve mikro hizmet kesinlikle sonuçta ortaya çıkan hataları kısmi benimseyin gerekir. Bu kısmi hatalara karşı dayanıklı olacak şekilde uygulamanızı tasarlamak gerekir.*</span><span class="sxs-lookup"><span data-stu-id="36d6f-104">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="36d6f-105">Dayanıklılık, hatalardan kurtularak çalışmaya devam yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="36d6f-105">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="36d6f-106">Bu hataları önleme ancak hatalar kaçınılmazdır gerçeğini kabul eden ve bunlara kapalı kalma süresi veya veri kaybı engelleyen bir şekilde yanıt ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="36d6f-106">It is not about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="36d6f-107">Dayanıklılığın hedefi, bir hatadan sonra uygulamayı tam çalışır duruma getirmektir.</span><span class="sxs-lookup"><span data-stu-id="36d6f-107">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="36d6f-108">Tasarım ve mikro hizmet tabanlı bir uygulamayı dağıtmak için yeterli güç olabilir.</span><span class="sxs-lookup"><span data-stu-id="36d6f-108">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="36d6f-109">Ancak uygulamanızın hata çeşit belirli olduğu bir ortamda çalışmaya devam etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="36d6f-109">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="36d6f-110">Bu nedenle, uygulamanızı dayanıklı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36d6f-110">Therefore, your application should be resilient.</span></span> <span data-ttu-id="36d6f-111">Ağ kesintileri veya düğümleri veya bulutta kilitlenen VM'ler gibi kısmi hataları olan başa çıkacak şekilde tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36d6f-111">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="36d6f-112">Bir kümedeki farklı bir düğüme taşınmasını bile mikro hizmetler (kapsayıcılar), uygulama içinde aralıklı kısa hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="36d6f-112">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="36d6f-113">Uygulamanızın birçok ayrı ayrı bileşen sistem durumu izleme özellikleri de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36d6f-113">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="36d6f-114">Bu bölümdeki yönergeleri izleyerek, karmaşık ve bulut tabanlı dağıtımlarda artma geçici kapalı kalma süresi sorunsuz çalışması bir uygulama veya gerçekleşen normal yürütebilme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36d6f-114">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="36d6f-115">[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[İleri](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="36d6f-115">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
