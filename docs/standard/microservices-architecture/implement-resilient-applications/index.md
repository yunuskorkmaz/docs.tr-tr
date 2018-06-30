---
title: Esnek uygulamaları uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Esnek uygulamaları uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ddb0f54b15735b9192d2088495947588f59829a0
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106057"
---
# <a name="implementing-resilient-applications"></a>Esnek uygulamaları uygulama

*Mikro hizmet ve bulut tabanlı uygulamalar kesinlikle sonuçta ortaya çıkan kısmi hataları çekirdeğin gerekir. Bu kısmi hatalarına dayanıklı olması için uygulamanız tasarlamanız gerekir.*

Dayanıklılık, arızalardan kurtarmak ve çalışmaya devam yeteneğidir. Hataları, önleme ancak hataları olacağını olgu kabul ettiğini ve bunlara kapalı kalma süresi veya veri kaybı engelleyen bir şekilde yanıt hakkında değil. Dayanıklılık bir hatadan sonra uygulamaya tam çalışır bir duruma geri dönmek için hedefidir.

Tasarım ve mikro tabanlı bir uygulama dağıtım için yeterli görevdir. Ancak uygulamanızın hatası çeşit belirli olduğu bir ortamda çalışmaya devam etmesi gerekir. Bu nedenle, uygulamanızın dayanıklı olması gerekir. Ağ kesintileri veya düğümler veya bulutta kilitlenen VM'ler gibi kısmi hatalarıyla başa çıkacak şekilde tasarlanmalıdır. Bir küme içinde farklı bir düğüme taşınmasını bile mikro (kapsayıcı), uygulama içinde aralıklı kısa hatalarına neden olabilir.

Uygulamanızın birçok ayrı bileşen sistem durumu izleme özelliklerini de eklemeniz gerekir. Bu bölümdeki yönergeleri izleyerek, karmaşık ve bulut tabanlı dağıtımlarda geçici kapalı kalma süresi tüm sorunsuz çalışabilmeniz için bir uygulama veya ortaya normal duraklamalarla oluşturabilirsiniz.


>[!div class="step-by-step"]
[Önceki](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[sonraki](handle-partial-failure.md)
