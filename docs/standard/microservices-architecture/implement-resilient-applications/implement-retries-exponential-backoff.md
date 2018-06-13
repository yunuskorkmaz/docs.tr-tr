---
title: Yeniden deneme üstel geri alma ile uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Yeniden deneme üstel geri alma ile uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7f909c6f81abce80bfdf118112271f1f87254793
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571429"
---
# <a name="implementing-retries-with-exponential-backoff"></a><span data-ttu-id="4d719-103">Yeniden deneme üstel geri alma ile uygulama</span><span class="sxs-lookup"><span data-stu-id="4d719-103">Implementing retries with exponential backoff</span></span>

<span data-ttu-id="4d719-104">[*Üstel geri alma ile yeniden deneme* ](https://docs.microsoft.com/azure/architecture/patterns/retry) bir işlem, en fazla yeniden deneme sayısı üst sınırına kadar bir katlanarak artan bekleme süresi, yeniden deneme girişiminde bir tekniktir ( [üstel geri alma](https://en.wikipedia.org/wiki/Exponential_backoff) ).</span><span class="sxs-lookup"><span data-stu-id="4d719-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="4d719-105">Bu teknik bulut kaynaklarına aralıklı birden fazla birkaç saniye boyunca herhangi bir nedenle kullanılamaz durumda olabilir, olgu çalışır.</span><span class="sxs-lookup"><span data-stu-id="4d719-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="4d719-106">Örneğin, bir orchestrator bir kapsayıcı Yük Dengeleme için bir kümedeki başka bir düğüme taşınıyor.</span><span class="sxs-lookup"><span data-stu-id="4d719-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="4d719-107">Bu işlem sırasında bazı istekler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d719-107">During that time, some requests might fail.</span></span> <span data-ttu-id="4d719-108">Bir veritabanı SQL Azure, burada bir veritabanı başka bir sunucuya Yük Dengeleme, veritabanı neden birkaç saniye kullanılamaz hale gelmesine taşınabilir gibi başka bir örnek olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d719-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="4d719-109">Yeniden deneme mantığı üstel geri alma ile uygulamak için birçok yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="4d719-109">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="4d719-110">[Önceki] (kısmi-hatası-strategies.md) [sonraki] (implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="4d719-110">[Previous] (partial-failure-strategies.md) [Next] (implement-resilient-entity-framework-core-sql-connections.md)</span></span>
