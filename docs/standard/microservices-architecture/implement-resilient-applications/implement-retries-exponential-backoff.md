---
title: Üstel geri alma ile yeniden denemeleri uygulamanız
description: Üstel geri alma ile yeniden denemeleri uygulamanız hakkında bilgi edinin.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644205"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="c5d4a-103">Üstel geri alma ile yeniden denemeleri uygulamanız</span><span class="sxs-lookup"><span data-stu-id="c5d4a-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="c5d4a-104">[*Üstel geri alma ile yeniden* ](/azure/architecture/patterns/retry) olduğundan, en fazla yeniden deneme sayısına kadar bir üssel olarak artan bekleme süresi ile bir işlem yeniden deneme bir teknik ulaşıldı ( [üstel geri alma](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="c5d4a-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="c5d4a-105">Bu teknik bulut kaynaklarını aralıklı olarak herhangi bir nedenle birkaç saniye boyunca kullanılamaz olabileceğini olgu kapsar.</span><span class="sxs-lookup"><span data-stu-id="c5d4a-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="c5d4a-106">Örneğin, bir orchestrator bir kapsayıcıya Yük Dengeleme için bir kümedeki başka bir düğüme taşıma.</span><span class="sxs-lookup"><span data-stu-id="c5d4a-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="c5d4a-107">Bu sırada, bazı istekler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d4a-107">During that time, some requests might fail.</span></span> <span data-ttu-id="c5d4a-108">Başka bir örnek burada bir veritabanını başka bir sunucuya Yük Dengeleme, veritabanına neden birkaç saniye boyunca kullanılamaz olarak taşınabilir, SQL Azure gibi bir veritabanı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d4a-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="c5d4a-109">Üstel geri alma ile yeniden deneme mantığını uygulamak için birçok yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="c5d4a-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c5d4a-110">[Önceki](partial-failure-strategies.md)
>[İleri](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="c5d4a-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
