---
title: Esnek uygulamalar uygulama
description: Mikro hizmet mimarisinde çekirdek kavram olan esnekliği hakkında bilgi edinin. Meydana geldiğinde geçici hataların düzgün bir şekilde nasıl işleneceğini bilmeniz gerekir.
ms.date: 01/30/2020
ms.openlocfilehash: ccdb2470c727ad4bd89c4e0634da8564b8010e63
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502653"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="89846-104">Esnek uygulamalar uygulama</span><span class="sxs-lookup"><span data-stu-id="89846-104">Implement resilient applications</span></span>

<span data-ttu-id="89846-105">*Mikro hizmetiniz ve bulut tabanlı uygulamalarınız, sonunda tamamen gerçekleşmeyecek olan kısmi hataların ayracına sahip olmalıdır. Uygulamanızı bu kısmi hatalara dayanıklı olacak şekilde tasarlamanız gerekir.*</span><span class="sxs-lookup"><span data-stu-id="89846-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="89846-106">Dayanıklılık, hatalardan kurtulmakta ve çalışmaya devam edebilmesidir.</span><span class="sxs-lookup"><span data-stu-id="89846-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="89846-107">Arızaların oluşması ve bu durum, kapalı kalma süresi veya veri kaybını önleyen bir şekilde hatalara neden olacağı gerçeğini kabul etmeyle ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="89846-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="89846-108">Dayanıklılık amacı, bir hatadan sonra uygulamayı tam çalışır duruma döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="89846-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="89846-109">Mikro hizmet tabanlı bir uygulama tasarlamak ve dağıtmak yeterince zor.</span><span class="sxs-lookup"><span data-stu-id="89846-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="89846-110">Ancak, uygulamanızı bazı hata sıralaması belirli bir ortamda çalışır durumda tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89846-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="89846-111">Bu nedenle, uygulamanız dayanıklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89846-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="89846-112">Ağ kesintileri veya düğümler ya da bulutta kilitlenen VM 'Ler gibi kısmi hatalarla başa çıkabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="89846-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="89846-113">Küme içindeki farklı bir düğüme taşınan mikro hizmetler (kapsayıcılar) bile uygulama içinde aralıklı kısa hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="89846-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="89846-114">Uygulamanızın birçok ayrı bileşeni de sistem durumu izleme özellikleri de içermelidir.</span><span class="sxs-lookup"><span data-stu-id="89846-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="89846-115">Bu bölümdeki yönergeleri izleyerek, artma geçici kapalı kalma süresi veya karmaşık ve bulut tabanlı dağıtımlarda oluşan normal hiccups içinde sorunsuz şekilde çalışan bir uygulama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89846-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="89846-116">eShopOnContainer, sürüm 3.0.0 kadar [yazılan istemcileri](./use-httpclientfactory-to-implement-resilient-http-requests.md) kullanarak dayanıklılık uygulamak Için [Polly kitaplığını](http://www.thepollyproject.org/) kullanıyor vardı.</span><span class="sxs-lookup"><span data-stu-id="89846-116">eShopOnContainer had been using the [Polly library](http://www.thepollyproject.org/) to implement resiliency using [Typed Clients](./use-httpclientfactory-to-implement-resilient-http-requests.md) up until the release 3.0.0.</span></span>
>
> <span data-ttu-id="89846-117">Release 3.0.0 ile başlayarak, HTTP çağrıları dayanıklılığı bir [Kkerd ağı](https://linkerd.io/)kullanılarak, bir Kubernetes kümesi içindeki yeniden denemeleri, koddaki sorunları işlemeye gerek kalmadan, saydam ve yapılandırılabilir biçimde işler.</span><span class="sxs-lookup"><span data-stu-id="89846-117">Starting with release 3.0.0, the HTTP calls resiliency is implemented using a [Linkerd mesh](https://linkerd.io/), that handles retries in transparent and configurable fashion, within a Kubernetes cluster, without having to handle those concerns in the code.</span></span>
>
> <span data-ttu-id="89846-118">Polly kitaplığı, Hizmetleri başlatırken özel olarak esnekliği veritabanı bağlantılarına eklemek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89846-118">The Polly library is still used to add resilience to database connections, specially while starting up the services.</span></span>

>[!WARNING]
> <span data-ttu-id="89846-119">Bu bölümdeki tüm kod örnekleri, Linkerd kullanılmadan önce geçerlidir ve geçerli gerçek kodu yansıtacak şekilde güncellenmez.</span><span class="sxs-lookup"><span data-stu-id="89846-119">All code samples in this section were valid before using Linkerd and are not updated to reflect the current actual code.</span></span> <span data-ttu-id="89846-120">Bu nedenle, bu bölümün bağlamında mantıklı olurlar.</span><span class="sxs-lookup"><span data-stu-id="89846-120">So they make sense in the context of this section.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="89846-121">[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[İleri](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="89846-121">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
