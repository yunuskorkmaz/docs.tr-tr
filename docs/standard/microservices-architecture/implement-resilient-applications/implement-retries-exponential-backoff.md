---
title: Üstel geri alma ile yeniden denemeleri uygulamanız
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Üstel geri alma ile yeniden denemeleri uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: a5ab15299ecb501691c26bbc6d377e22a38ee51e
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874370"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="423fb-103">Üstel geri alma ile yeniden denemeleri uygulamanız</span><span class="sxs-lookup"><span data-stu-id="423fb-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="423fb-104">[*Üstel geri alma ile yeniden deneme* ](https://docs.microsoft.com/azure/architecture/patterns/retry) maksimum yeniden deneme sayısına ulaşılana kadar bir üssel olarak artan bekleme süresi ile bir işlemi yeniden başlatmayı deneyen bir tekniktir ( [üstel geri alma](https://en.wikipedia.org/wiki/Exponential_backoff) ).</span><span class="sxs-lookup"><span data-stu-id="423fb-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="423fb-105">Bu teknik bulut kaynaklarını aralıklı olarak herhangi bir nedenle birkaç saniye boyunca kullanılamaz olabileceğini olgu kapsar.</span><span class="sxs-lookup"><span data-stu-id="423fb-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="423fb-106">Örneğin, bir orchestrator bir kapsayıcıya Yük Dengeleme için bir kümedeki başka bir düğüme taşıma.</span><span class="sxs-lookup"><span data-stu-id="423fb-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="423fb-107">Bu sırada, bazı istekler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="423fb-107">During that time, some requests might fail.</span></span> <span data-ttu-id="423fb-108">Başka bir örnek burada bir veritabanını başka bir sunucuya Yük Dengeleme, veritabanına neden birkaç saniye boyunca kullanılamaz olarak taşınabilir, SQL Azure gibi bir veritabanı olabilir.</span><span class="sxs-lookup"><span data-stu-id="423fb-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="423fb-109">Üstel geri alma ile yeniden deneme mantığını uygulamak için birçok yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="423fb-109">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="423fb-110">[Önceki](partial-failure-strategies.md)
[İleri](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="423fb-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
