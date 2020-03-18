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
# <a name="implement-retries-with-exponential-backoff"></a>Üstel geri tepme ile yeniden denemeler uygulayın

[*Üstel geri leme ile*](/azure/architecture/patterns/retry) yeniden denemeler, bir işlemi, katlanarak artan bekleme süresiyle, maksimum yeniden deneme sayısına ulaşıldı [(üstel gerileme)](https://en.wikipedia.org/wiki/Exponential_backoff)yeniden deneyen bir tekniktir. Bu teknik, bulut kaynaklarının herhangi bir nedenle birkaç saniyeden fazla aralıklı olarak kullanılamayabileceği gerçeğini benimser. Örneğin, bir orkestratör yük dengeleme için bir kümedeki bir kapsayıcıyı başka bir düğüme taşıyor olabilir. Bu süre zarfında, bazı istekler başarısız olabilir. Başka bir örnek, bir veritabanının yük dengelemesi için başka bir sunucuya taşınarak veritabanının birkaç saniye süreyle kullanılamamasına neden olduğu SQL Azure gibi bir veritabanı olabilir.

Üstel geri tepme ile yeniden deneme mantığını uygulamak için birçok yaklaşım vardır.

>[!div class="step-by-step"]
>[Önceki](partial-failure-strategies.md)
>[Sonraki](implement-resilient-entity-framework-core-sql-connections.md)
