---
title: Dayanıklı uygulamalar uygulama
description: Dayanıklılık, mikro hizmetler mimarisinde bir temel kavramlar hakkında bilgi edinin. Geçici hatalar meydana gelir çünkü düzgün bir şekilde işlemek nasıl bilmeniz gerekir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 00724509ba6e027ef73f72bfb6f85b8ec0aa9d25
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362749"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="50ecf-104">Dayanıklı uygulamalar uygulama</span><span class="sxs-lookup"><span data-stu-id="50ecf-104">Implement Resilient Applications</span></span>

<span data-ttu-id="50ecf-105">*Bulut tabanlı uygulamalar ve mikro hizmet kesinlikle sonuçta ortaya çıkan hataları kısmi benimseyin gerekir. Uygulamanız bu kısmi hatalara karşı dayanıklı olacak şekilde tasarlamanız gerekir.*</span><span class="sxs-lookup"><span data-stu-id="50ecf-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="50ecf-106">Dayanıklılık, hatalardan kurtularak çalışmaya devam yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="50ecf-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="50ecf-107">Hatalarını önleme ancak hatalar kaçınılmazdır gerçeğini kabul eden ve bunlara kapalı kalma süresi veya veri kaybı engelleyen bir şekilde yanıt ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="50ecf-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="50ecf-108">Dayanıklılığın hedefi, bir hatadan sonra uygulamayı tam çalışır duruma getirmektir.</span><span class="sxs-lookup"><span data-stu-id="50ecf-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="50ecf-109">Tasarım ve mikro hizmet tabanlı bir uygulamayı dağıtmak için yeterli güç olabilir.</span><span class="sxs-lookup"><span data-stu-id="50ecf-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="50ecf-110">Ancak uygulamanızın hata çeşit belirli olduğu bir ortamda çalışmaya devam etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="50ecf-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="50ecf-111">Bu nedenle, uygulamanızı dayanıklı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="50ecf-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="50ecf-112">Ağ kesintileri veya düğümleri veya bulutta kilitlenen VM'ler gibi kısmi hataları olan başa çıkacak şekilde tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50ecf-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="50ecf-113">Bir kümedeki farklı bir düğüme taşınmasını bile mikro hizmetler (kapsayıcılar), uygulama içinde aralıklı kısa hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="50ecf-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="50ecf-114">Uygulamanızın birçok ayrı ayrı bileşen sistem durumu izleme özellikleri de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="50ecf-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="50ecf-115">Bu bölümdeki yönergeleri izleyerek, karmaşık ve bulut tabanlı dağıtımlarda artma geçici kapalı kalma süresi sorunsuz çalışması bir uygulama veya gerçekleşen normal yürütebilme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50ecf-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="50ecf-116">[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[İleri](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="50ecf-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>