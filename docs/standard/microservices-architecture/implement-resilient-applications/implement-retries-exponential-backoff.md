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
# <a name="implement-retries-with-exponential-backoff"></a>Üstel geri alma ile yeniden denemeleri uygulamanız

[*Üstel geri alma ile yeniden* ](/azure/architecture/patterns/retry) olduğundan, en fazla yeniden deneme sayısına kadar bir üssel olarak artan bekleme süresi ile bir işlem yeniden deneme bir teknik ulaşıldı ( [üstel geri alma](https://en.wikipedia.org/wiki/Exponential_backoff)). Bu teknik bulut kaynaklarını aralıklı olarak herhangi bir nedenle birkaç saniye boyunca kullanılamaz olabileceğini olgu kapsar. Örneğin, bir orchestrator bir kapsayıcıya Yük Dengeleme için bir kümedeki başka bir düğüme taşıma. Bu sırada, bazı istekler başarısız olabilir. Başka bir örnek burada bir veritabanını başka bir sunucuya Yük Dengeleme, veritabanına neden birkaç saniye boyunca kullanılamaz olarak taşınabilir, SQL Azure gibi bir veritabanı olabilir.

Üstel geri alma ile yeniden deneme mantığını uygulamak için birçok yaklaşım vardır.

>[!div class="step-by-step"]
>[Önceki](partial-failure-strategies.md)
>[İleri](implement-resilient-entity-framework-core-sql-connections.md)
