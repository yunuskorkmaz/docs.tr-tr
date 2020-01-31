---
title: Bulutta yerel dayanıklılık
description: Azure için Cloud Native .NET uygulamaları tasarlama | Cloud Native dayanıklılık
ms.date: 06/30/2019
ms.openlocfilehash: 427405d95534c4467ab519c2188fe88e2f18e2b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781079"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="c3679-103">Bulutta yerel dayanıklılık</span><span class="sxs-lookup"><span data-stu-id="c3679-103">Cloud-native resiliency</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c3679-104">Dayanıklılık, sisteminizin hataya tepki verme ve hala işlevsel olmaya devam etme yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="c3679-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="c3679-105">Hatanın kaçınılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c3679-105">It isn't about avoiding failure.</span></span> <span data-ttu-id="c3679-106">Ancak, bu hatanın bulut tabanlı sistemlerde çok fazla tablo olduğunu kabul ediyor ve uygulamanızı yanıt verecek şekilde oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="c3679-106">But it's about accepting that failure is inevitable in cloud-based systems and building your application to respond to it.</span></span> <span data-ttu-id="c3679-107">Dayanıklılığın son amacı, bir hatadan sonra uygulamayı tam çalışır duruma döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="c3679-107">The end-goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="c3679-108">Her şeyin tek bir işlemde birlikte çalıştığı geleneksel tek parçalı uygulamalardan farklı olarak, bulut Yerel sistemleri Şekil 6-1 ' de gösterildiği gibi, dağıtılmış mimariden yararlanın:</span><span class="sxs-lookup"><span data-stu-id="c3679-108">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace distributed architecture as shown in Figure 6-1:</span></span>

![Dağıtılmış bulutta yerel ortam](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="c3679-110">**Şekil 6-1.**</span><span class="sxs-lookup"><span data-stu-id="c3679-110">**Figure 6-1.**</span></span> <span data-ttu-id="c3679-111">Dağıtılmış bulutta yerel ortam</span><span class="sxs-lookup"><span data-stu-id="c3679-111">Distributed cloud-native environment</span></span>

<span data-ttu-id="c3679-112">Önceki şekilde, her bir istemci, mikro hizmet ve bulut tabanlı [yedekleme hizmetinin](https://12factor.net/backing-services) , farklı sunucular arasında çalışan, ağ tabanlı çağrılar aracılığıyla iletişim kuran ayrı bir işlem olarak nasıl yürütüldüğünü aklınızda olduğunu fark edin.</span><span class="sxs-lookup"><span data-stu-id="c3679-112">In the previous figure, note how each client, microservice, and cloud-based [backing service](https://12factor.net/backing-services) executes as a separate process, running across different servers, all communicating via network-based calls.</span></span>

<span data-ttu-id="c3679-113">Bu nedenle, ne kadar hatalı gidebilirler?</span><span class="sxs-lookup"><span data-stu-id="c3679-113">So, what could go wrong?</span></span>

- <span data-ttu-id="c3679-114">Beklenmeyen [ağ gecikmesi](https://www.techopedia.com/definition/8553/network-latency).</span><span class="sxs-lookup"><span data-stu-id="c3679-114">Unexpected [network latency](https://www.techopedia.com/definition/8553/network-latency).</span></span>
- <span data-ttu-id="c3679-115">[Geçici hatalar](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (geçici ağ bağlantısı hataları).</span><span class="sxs-lookup"><span data-stu-id="c3679-115">[Transient faults](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (temporary network connectivity errors).</span></span>
- <span data-ttu-id="c3679-116">Uzun süre çalışan bir zaman uyumlu işlem tarafından engelleniyor.</span><span class="sxs-lookup"><span data-stu-id="c3679-116">Blocking by a long-running synchronous operation.</span></span>
- <span data-ttu-id="c3679-117">Kilitlenen ve yeniden başlatılan veya taşınan bir ana bilgisayar işlemi.</span><span class="sxs-lookup"><span data-stu-id="c3679-117">A host process that has crashed and is being restarted or moved.</span></span>
- <span data-ttu-id="c3679-118">Kısa bir süre yanıt vermeyen aşırı yüklenmiş bir mikro hizmet.</span><span class="sxs-lookup"><span data-stu-id="c3679-118">An overloaded microservice that can't respond for a short time.</span></span>
- <span data-ttu-id="c3679-119">Güncelleştirme veya ölçeklendirme işlemi gibi bir uçuş DevOps işlemi.</span><span class="sxs-lookup"><span data-stu-id="c3679-119">An in-flight DevOps operation such as an update or scaling operation.</span></span>
- <span data-ttu-id="c3679-120">Bir hizmeti bir düğümden diğerine taşıma gibi bir Orchestrator işlemi.</span><span class="sxs-lookup"><span data-stu-id="c3679-120">An Orchestrator operation such as moving a service from one node to another.</span></span>
- <span data-ttu-id="c3679-121">Emtia donanımlarından donanım sorunları.</span><span class="sxs-lookup"><span data-stu-id="c3679-121">Hardware failures from commodity hardware.</span></span>

<span data-ttu-id="c3679-122">Dağıtılmış hizmetleri bulut tabanlı altyapıya dağıttığınızda, önceki listedeki faktörler çok gerçek hale gelir ve bunlarla uğraşmak için yüksek savunma ve mimariyi geliştirme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3679-122">When deploying distributed services into cloud-based infrastructure, the factors from the previous list become very real and you must architect and develop defensively to deal with them.</span></span>

<span data-ttu-id="c3679-123">Küçük ölçekli bir dağıtılmış sistemde, hata sık sık olacaktır, ancak bir sistem ölçeği büyüerek, bu sorunlardan daha fazlasını, kısmi hatanın normal işlem haline geldiği bir noktaya daha fazla deneyim sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3679-123">In a small-scale distributed system, failure will be less frequent, but as a system scales up and out, you can expect to experience more of these issues to a point where partial failure becomes normal operation.</span></span>

<span data-ttu-id="c3679-124">Bu nedenle, uygulamanız ve altyapınız dayanıklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3679-124">Therefore, your application and infrastructure must be resilient.</span></span> <span data-ttu-id="c3679-125">Aşağıdaki bölümlerde, uygulamanıza ekleyebileceğiniz savunma tekniklerini ve Kullanıcı deneyiminizin madde işaretine yardımcı olmak için kullanabileceğiniz yerleşik bulut özelliklerini keşfedeceğiz.</span><span class="sxs-lookup"><span data-stu-id="c3679-125">In the following sections, we'll explore defensive techniques that you can add to your application and built-in cloud features that you can leverage to help bullet-proof your user's experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c3679-126">[Önceki](elastic-search-in-azure.md)
>[İleri](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="c3679-126">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>
