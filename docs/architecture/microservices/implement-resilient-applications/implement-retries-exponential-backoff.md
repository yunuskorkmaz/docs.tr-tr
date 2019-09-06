---
title: Üstel geri alma ile yeniden denemeler uygulama
description: Üstel geri alma ile yeniden denemeler uygulamayı öğrenin.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296065"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="8eac5-103">Üstel geri alma ile yeniden denemeler uygulama</span><span class="sxs-lookup"><span data-stu-id="8eac5-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="8eac5-104">[*Üstel geri alma Ile yeniden denemeler*](/azure/architecture/patterns/retry) , bir işlemi yeniden denemeden, en fazla yeniden deneme sayısına ( [üstel geri](https://en.wikipedia.org/wiki/Exponential_backoff)alma) kadar bir işlem yeniden deneme süresini üstel olarak artırır.</span><span class="sxs-lookup"><span data-stu-id="8eac5-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="8eac5-105">Bu teknik, bulut kaynaklarının her zaman birkaç saniyeden uzun süre boyunca kullanılamamasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8eac5-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="8eac5-106">Örneğin, bir Orchestrator yük dengeleme için bir kapsayıcıyı bir kümedeki başka bir düğüme taşıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8eac5-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="8eac5-107">Bu süre boyunca bazı istekler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="8eac5-107">During that time, some requests might fail.</span></span> <span data-ttu-id="8eac5-108">Başka bir örnek, bir veritabanının yük dengeleme için başka bir sunucuya taşınabileceği SQL Azure gibi bir veritabanı olabilir ve veritabanının birkaç saniye boyunca kullanılamamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8eac5-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="8eac5-109">Üstel geri alma ile yeniden denemeler mantığı uygulamak için birçok yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="8eac5-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8eac5-110">[Önceki](partial-failure-strategies.md)İleri
>[](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="8eac5-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
