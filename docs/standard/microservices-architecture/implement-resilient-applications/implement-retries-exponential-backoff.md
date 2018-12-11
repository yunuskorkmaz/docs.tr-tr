---
title: Üstel geri alma ile yeniden denemeleri uygulamanız
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Üstel geri alma ile yeniden denemeleri uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: e0758ee8fe28cb45ecd35ad07ddc738c12614973
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148775"
---
# <a name="implement-retries-with-exponential-backoff"></a>Üstel geri alma ile yeniden denemeleri uygulamanız

[*Üstel geri alma ile yeniden deneme* ](https://docs.microsoft.com/azure/architecture/patterns/retry) maksimum yeniden deneme sayısına ulaşılana kadar bir üssel olarak artan bekleme süresi ile bir işlemi yeniden başlatmayı deneyen bir tekniktir ( [üstel geri alma](https://en.wikipedia.org/wiki/Exponential_backoff) ). Bu teknik bulut kaynaklarını aralıklı olarak herhangi bir nedenle birkaç saniye boyunca kullanılamaz olabileceğini olgu kapsar. Örneğin, bir orchestrator bir kapsayıcıya Yük Dengeleme için bir kümedeki başka bir düğüme taşıma. Bu sırada, bazı istekler başarısız olabilir. Başka bir örnek burada bir veritabanını başka bir sunucuya Yük Dengeleme, veritabanına neden birkaç saniye boyunca kullanılamaz olarak taşınabilir, SQL Azure gibi bir veritabanı olabilir.

Üstel geri alma ile yeniden deneme mantığını uygulamak için birçok yaklaşım vardır.

>[!div class="step-by-step"]
>[Önceki](partial-failure-strategies.md)
>[İleri](implement-resilient-entity-framework-core-sql-connections.md)