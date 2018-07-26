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
# <a name="implement-retries-with-exponential-backoff"></a>Üstel geri alma ile yeniden denemeleri uygulamanız

[*Üstel geri alma ile yeniden deneme* ](https://docs.microsoft.com/azure/architecture/patterns/retry) maksimum yeniden deneme sayısına ulaşılana kadar bir üssel olarak artan bekleme süresi ile bir işlemi yeniden başlatmayı deneyen bir tekniktir ( [üstel geri alma](https://en.wikipedia.org/wiki/Exponential_backoff) ). Bu teknik bulut kaynaklarını aralıklı olarak herhangi bir nedenle birkaç saniye boyunca kullanılamaz olabileceğini olgu kapsar. Örneğin, bir orchestrator bir kapsayıcıya Yük Dengeleme için bir kümedeki başka bir düğüme taşıma. Bu sırada, bazı istekler başarısız olabilir. Başka bir örnek burada bir veritabanını başka bir sunucuya Yük Dengeleme, veritabanına neden birkaç saniye boyunca kullanılamaz olarak taşınabilir, SQL Azure gibi bir veritabanı olabilir.

Üstel geri alma ile yeniden deneme mantığını uygulamak için birçok yaklaşım vardır.


>[!div class="step-by-step"]
[Önceki](partial-failure-strategies.md)
[İleri](implement-resilient-entity-framework-core-sql-connections.md)
