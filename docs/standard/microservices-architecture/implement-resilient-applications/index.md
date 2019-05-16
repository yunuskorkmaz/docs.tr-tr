---
title: Dayanıklı Uygulamalar Uygulama
description: Dayanıklılık, mikro hizmetler mimarisinde bir temel kavramlar hakkında bilgi edinin. Geçici hatalar meydana gelir çünkü düzgün bir şekilde işlemek nasıl bilmeniz gerekir.
ms.date: 10/16/2018
ms.openlocfilehash: 766349e72389f848b0a741b020707cc7acf3410d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639852"
---
# <a name="implement-resilient-applications"></a>Dayanıklı uygulamalar uygulama

*Bulut tabanlı uygulamalar ve mikro hizmet kesinlikle sonuçta ortaya çıkan hataları kısmi benimseyin gerekir. Uygulamanız bu kısmi hatalara karşı dayanıklı olacak şekilde tasarlamanız gerekir.*

Dayanıklılık, hatalardan kurtularak çalışmaya devam yeteneğidir. Hatalarını önleme ancak hatalar kaçınılmazdır gerçeğini kabul eden ve bunlara kapalı kalma süresi veya veri kaybı engelleyen bir şekilde yanıt ilgili değildir. Dayanıklılığın hedefi, bir hatadan sonra uygulamayı tam çalışır duruma getirmektir.

Tasarım ve mikro hizmet tabanlı bir uygulamayı dağıtmak için yeterli güç olabilir. Ancak uygulamanızın hata çeşit belirli olduğu bir ortamda çalışmaya devam etmesi gerekir. Bu nedenle, uygulamanızı dayanıklı olması gerekir. Ağ kesintileri veya düğümleri veya bulutta kilitlenen VM'ler gibi kısmi hataları olan başa çıkacak şekilde tasarlanmalıdır. Bir kümedeki farklı bir düğüme taşınmasını bile mikro hizmetler (kapsayıcılar), uygulama içinde aralıklı kısa hatalarına neden olabilir.

Uygulamanızın birçok ayrı ayrı bileşen sistem durumu izleme özellikleri de eklemeniz gerekir. Bu bölümdeki yönergeleri izleyerek, karmaşık ve bulut tabanlı dağıtımlarda artma geçici kapalı kalma süresi sorunsuz çalışması bir uygulama veya gerçekleşen normal yürütebilme oluşturabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[İleri](handle-partial-failure.md)
