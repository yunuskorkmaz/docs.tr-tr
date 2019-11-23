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
# <a name="implement-retries-with-exponential-backoff"></a>Üstel geri alma ile yeniden denemeler uygulama

[*Üstel geri alma Ile yeniden denemeler*](/azure/architecture/patterns/retry) , bir işlemi yeniden denemeden, en fazla yeniden deneme sayısına ( [üstel geri](https://en.wikipedia.org/wiki/Exponential_backoff)alma) kadar bir işlem yeniden deneme süresini üstel olarak artırır. Bu teknik, bulut kaynaklarının her zaman birkaç saniyeden uzun süre boyunca kullanılamamasına neden olabilir. Örneğin, bir Orchestrator yük dengeleme için bir kapsayıcıyı bir kümedeki başka bir düğüme taşıyor olabilir. Bu süre boyunca bazı istekler başarısız olabilir. Başka bir örnek, bir veritabanının yük dengeleme için başka bir sunucuya taşınabileceği SQL Azure gibi bir veritabanı olabilir ve veritabanının birkaç saniye boyunca kullanılamamasına neden olur.

Üstel geri alma ile yeniden denemeler mantığı uygulamak için birçok yaklaşım vardır.

>[!div class="step-by-step"]
>[Önceki](partial-failure-strategies.md)
>[İleri](implement-resilient-entity-framework-core-sql-connections.md)
