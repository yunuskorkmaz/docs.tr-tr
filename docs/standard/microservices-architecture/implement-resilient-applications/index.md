---
title: Dayanıklı uygulamalar uygulama
description: Dayanıklılık, mikro hizmetler mimarisinde bir temel kavramlar hakkında bilgi edinin. Geçici hatalar meydana gelir çünkü düzgün bir şekilde işlemek nasıl bilmeniz gerekir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 00724509ba6e027ef73f72bfb6f85b8ec0aa9d25
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362749"
---
# <a name="implement-resilient-applications"></a>Dayanıklı uygulamalar uygulama

*Bulut tabanlı uygulamalar ve mikro hizmet kesinlikle sonuçta ortaya çıkan hataları kısmi benimseyin gerekir. Uygulamanız bu kısmi hatalara karşı dayanıklı olacak şekilde tasarlamanız gerekir.*

Dayanıklılık, hatalardan kurtularak çalışmaya devam yeteneğidir. Hatalarını önleme ancak hatalar kaçınılmazdır gerçeğini kabul eden ve bunlara kapalı kalma süresi veya veri kaybı engelleyen bir şekilde yanıt ilgili değildir. Dayanıklılığın hedefi, bir hatadan sonra uygulamayı tam çalışır duruma getirmektir.

Tasarım ve mikro hizmet tabanlı bir uygulamayı dağıtmak için yeterli güç olabilir. Ancak uygulamanızın hata çeşit belirli olduğu bir ortamda çalışmaya devam etmesi gerekir. Bu nedenle, uygulamanızı dayanıklı olması gerekir. Ağ kesintileri veya düğümleri veya bulutta kilitlenen VM'ler gibi kısmi hataları olan başa çıkacak şekilde tasarlanmalıdır. Bir kümedeki farklı bir düğüme taşınmasını bile mikro hizmetler (kapsayıcılar), uygulama içinde aralıklı kısa hatalarına neden olabilir.

Uygulamanızın birçok ayrı ayrı bileşen sistem durumu izleme özellikleri de eklemeniz gerekir. Bu bölümdeki yönergeleri izleyerek, karmaşık ve bulut tabanlı dağıtımlarda artma geçici kapalı kalma süresi sorunsuz çalışması bir uygulama veya gerçekleşen normal yürütebilme oluşturabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[İleri](handle-partial-failure.md)