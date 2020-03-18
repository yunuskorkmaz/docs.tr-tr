---
title: Üstel geri tepme ile yeniden denemeler uygulayın
description: Üstel geri dönüşlü yeniden denemeleri nasıl uygulayacağınızı öğrenin.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296065"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="9edd9-103">Üstel geri tepme ile yeniden denemeler uygulayın</span><span class="sxs-lookup"><span data-stu-id="9edd9-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="9edd9-104">[*Üstel geri leme ile*](/azure/architecture/patterns/retry) yeniden denemeler, bir işlemi, katlanarak artan bekleme süresiyle, maksimum yeniden deneme sayısına ulaşıldı [(üstel gerileme)](https://en.wikipedia.org/wiki/Exponential_backoff)yeniden deneyen bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="9edd9-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="9edd9-105">Bu teknik, bulut kaynaklarının herhangi bir nedenle birkaç saniyeden fazla aralıklı olarak kullanılamayabileceği gerçeğini benimser.</span><span class="sxs-lookup"><span data-stu-id="9edd9-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="9edd9-106">Örneğin, bir orkestratör yük dengeleme için bir kümedeki bir kapsayıcıyı başka bir düğüme taşıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9edd9-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="9edd9-107">Bu süre zarfında, bazı istekler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="9edd9-107">During that time, some requests might fail.</span></span> <span data-ttu-id="9edd9-108">Başka bir örnek, bir veritabanının yük dengelemesi için başka bir sunucuya taşınarak veritabanının birkaç saniye süreyle kullanılamamasına neden olduğu SQL Azure gibi bir veritabanı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9edd9-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="9edd9-109">Üstel geri tepme ile yeniden deneme mantığını uygulamak için birçok yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="9edd9-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9edd9-110">[Önceki](partial-failure-strategies.md)
>[Sonraki](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="9edd9-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
