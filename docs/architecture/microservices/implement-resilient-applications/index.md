---
title: Dayanıklı Uygulamalar Uygulama
description: Mikro hizmet mimarisinde çekirdek kavram olan esnekliği hakkında bilgi edinin. Geçici hataların, gerçekleştikleri için düzgün bir şekilde nasıl işleneceğini bilmeniz gerekir.
ms.date: 10/16/2018
ms.openlocfilehash: 766349e72389f848b0a741b020707cc7acf3410d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296062"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="56275-104">Esnek uygulamalar uygulama</span><span class="sxs-lookup"><span data-stu-id="56275-104">Implement Resilient Applications</span></span>

<span data-ttu-id="56275-105">*Mikro hizmetiniz ve bulut tabanlı uygulamalarınız, sonunda tamamen gerçekleşmeyecek olan kısmi hataların ayracına sahip olmalıdır. Uygulamanızı bu kısmi hatalara dayanıklı olacak şekilde tasarlamanız gerekir.*</span><span class="sxs-lookup"><span data-stu-id="56275-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="56275-106">Dayanıklılık, hatalardan kurtulmakta ve çalışmaya devam edebilmesidir.</span><span class="sxs-lookup"><span data-stu-id="56275-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="56275-107">Arızaların oluşması ve bu durum, kapalı kalma süresi veya veri kaybını önleyen bir şekilde hatalara neden olacağı gerçeğini kabul etmeyle ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="56275-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="56275-108">Dayanıklılık amacı, bir hatadan sonra uygulamayı tam çalışır duruma döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="56275-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="56275-109">Mikro hizmet tabanlı bir uygulama tasarlamak ve dağıtmak yeterince zor.</span><span class="sxs-lookup"><span data-stu-id="56275-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="56275-110">Ancak, uygulamanızı bazı hata sıralaması belirli bir ortamda çalışır durumda tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="56275-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="56275-111">Bu nedenle, uygulamanız dayanıklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56275-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="56275-112">Ağ kesintileri veya düğümler ya da bulutta kilitlenen VM 'Ler gibi kısmi hatalarla başa çıkabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="56275-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="56275-113">Küme içindeki farklı bir düğüme taşınan mikro hizmetler (kapsayıcılar) bile uygulama içinde aralıklı kısa hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="56275-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="56275-114">Uygulamanızın birçok ayrı bileşeni de sistem durumu izleme özellikleri de içermelidir.</span><span class="sxs-lookup"><span data-stu-id="56275-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="56275-115">Bu bölümdeki yönergeleri izleyerek, artma geçici kapalı kalma süresi veya karmaşık ve bulut tabanlı dağıtımlarda oluşan normal hiccups içinde sorunsuz şekilde çalışan bir uygulama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56275-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="56275-116">[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)İleri
>[](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="56275-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
