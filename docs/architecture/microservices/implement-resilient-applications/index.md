---
title: Esnek uygulamaları uygulayın
description: Mikro hizmetler mimarisinde temel bir kavram olan esneklik hakkında bilgi edinin. Geçici hatalar oluştuğunda incelikle nasıl işleyeceğinizi bilmeniz gerekir.
ms.date: 01/30/2020
ms.openlocfilehash: 46276a6b9b36a494bfae657275692ca9d5554d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78847238"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="53a70-104">Esnek uygulamaları uygulayın</span><span class="sxs-lookup"><span data-stu-id="53a70-104">Implement resilient applications</span></span>

<span data-ttu-id="53a70-105">*Mikro hizmet ve bulut tabanlı uygulamalarınız, eninde sonunda kesinlikle ortaya çıkacak kısmi hataları benimsemelidir. Uygulamanızı bu kısmi hatalara karşı dirençli olacak şekilde tasarlamanız gerekir.*</span><span class="sxs-lookup"><span data-stu-id="53a70-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="53a70-106">Esneklik, başarısızlıklardan kurtulma ve çalışmaya devam etme yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="53a70-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="53a70-107">Bu hatalardan kaçınmakla ilgili değil, hataların gerçekleşeceği gerçeğini kabul etmek ve bunlara kapalı kalma süresini veya veri kaybını önleyecek şekilde yanıt vermektir.</span><span class="sxs-lookup"><span data-stu-id="53a70-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="53a70-108">Esnekliğin amacı, bir hatadan sonra uygulamayı tam olarak işleyen bir duruma döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="53a70-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="53a70-109">Mikro hizmetler tabanlı bir uygulama tasarlamak ve dağıtmak için yeterince zor.</span><span class="sxs-lookup"><span data-stu-id="53a70-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="53a70-110">Ancak, uygulamanızın bir tür hatanın kesin olduğu bir ortamda çalışmasını da engellemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="53a70-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="53a70-111">Bu nedenle, uygulamanız esnek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53a70-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="53a70-112">Ağ kesintileri veya düğümler veya bulutta çöken VM'ler gibi kısmi hatalarla başa çıkacak şekilde tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53a70-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="53a70-113">Bir küme içinde farklı bir düğüme taşınan mikro hizmetler (kapsayıcılar) bile uygulama içinde aralıklı kısa arızalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="53a70-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="53a70-114">Uygulamanızın birçok bireysel bileşeni, sistem durumu izleme özelliklerini de dahil etmelidir.</span><span class="sxs-lookup"><span data-stu-id="53a70-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="53a70-115">Bu bölümdeki yönergeleri izleyerek, geçici kapalı kalma süresine veya karmaşık ve bulut tabanlı dağıtımlarda oluşan normal hıçkırıklara rağmen sorunsuz çalışabilen bir uygulama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53a70-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="53a70-116">eShopOnContainer, [Polly kitaplığını](http://www.thepollyproject.org/) kullanarak 3.0.0 sürümüne kadar [Typed Clients'ı](./use-httpclientfactory-to-implement-resilient-http-requests.md) kullanarak esneklik uygulamaktadır.</span><span class="sxs-lookup"><span data-stu-id="53a70-116">eShopOnContainer had been using the [Polly library](http://www.thepollyproject.org/) to implement resiliency using [Typed Clients](./use-httpclientfactory-to-implement-resilient-http-requests.md) up until the release 3.0.0.</span></span>
>
> <span data-ttu-id="53a70-117">Sürüm 3.0.0 ile başlayarak, HTTP çağrıları esneklik bir [Linkerd örgü](https://linkerd.io/)kullanılarak uygulanır , şeffaf ve yapılandırılabilir bir şekilde retries işler, bir Kubernetes küme içinde, kodbu endişeleri işlemek zorunda kalmadan.</span><span class="sxs-lookup"><span data-stu-id="53a70-117">Starting with release 3.0.0, the HTTP calls resiliency is implemented using a [Linkerd mesh](https://linkerd.io/), that handles retries in a transparent and configurable fashion, within a Kubernetes cluster, without having to handle those concerns in the code.</span></span>
>
> <span data-ttu-id="53a70-118">Polly kitaplığı, özellikle hizmetleri başlatırken veritabanı bağlantılarına esneklik eklemek için hala kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53a70-118">The Polly library is still used to add resilience to database connections, specially while starting up the services.</span></span>

>[!WARNING]
> <span data-ttu-id="53a70-119">Bu bölümdeki tüm kod örnekleri Linkerd kullanmadan önce geçerliydi ve geçerli gerçek kodu yansıtacak şekilde güncelleştirilmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="53a70-119">All code samples in this section were valid before using Linkerd and are not updated to reflect the current actual code.</span></span> <span data-ttu-id="53a70-120">Bu yüzden bu bölümün bağlamında mantıklı.</span><span class="sxs-lookup"><span data-stu-id="53a70-120">So they make sense in the context of this section.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="53a70-121">[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Sonraki](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="53a70-121">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
