---
title: Dayanıklı uygulamalar uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Dayanıklı uygulamalar uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: dc0db8f0cdfa77bcca467c3c632b3d93de8851d8
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875132"
---
# <a name="implementing-resilient-applications"></a>Dayanıklı uygulamalar uygulama

*Bulut tabanlı uygulamalar ve mikro hizmet kesinlikle sonuçta ortaya çıkan hataları kısmi benimseyin gerekir. Bu kısmi hatalara karşı dayanıklı olacak şekilde uygulamanızı tasarlamak gerekir.*

Dayanıklılık, hatalardan kurtularak çalışmaya devam yeteneğidir. Bu hataları önleme ancak hatalar kaçınılmazdır gerçeğini kabul eden ve bunlara kapalı kalma süresi veya veri kaybı engelleyen bir şekilde yanıt ilgili değildir. Dayanıklılığın hedefi, bir hatadan sonra uygulamayı tam çalışır duruma getirmektir.

Tasarım ve mikro hizmet tabanlı bir uygulamayı dağıtmak için yeterli güç olabilir. Ancak uygulamanızın hata çeşit belirli olduğu bir ortamda çalışmaya devam etmesi gerekir. Bu nedenle, uygulamanızı dayanıklı olması gerekir. Ağ kesintileri veya düğümleri veya bulutta kilitlenen VM'ler gibi kısmi hataları olan başa çıkacak şekilde tasarlanmalıdır. Bir kümedeki farklı bir düğüme taşınmasını bile mikro hizmetler (kapsayıcılar), uygulama içinde aralıklı kısa hatalarına neden olabilir.

Uygulamanızın birçok ayrı ayrı bileşen sistem durumu izleme özellikleri de eklemeniz gerekir. Bu bölümdeki yönergeleri izleyerek, karmaşık ve bulut tabanlı dağıtımlarda artma geçici kapalı kalma süresi sorunsuz çalışması bir uygulama veya gerçekleşen normal yürütebilme oluşturabilirsiniz.


>[!div class="step-by-step"]
[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[İleri](handle-partial-failure.md)
