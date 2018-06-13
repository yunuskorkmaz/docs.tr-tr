---
title: .NET uygulamaları tasarlama ve birden çok kapsayıcı ve mikro hizmet geliştirirken dayalı
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET uygulamaları tasarlama ve birden çok kapsayıcı ve mikro hizmet geliştirirken dayalı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 297a53d6d6d37b1fa4a0e021919c9df86edeca03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571962"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Tasarlama ve birden çok kapsayıcı ve mikro hizmet tabanlı .NET uygulamaları geliştirme

*Kapsayıcılı mikro hizmet uygulamaları geliştirme çok kapsayıcı uygulamaları oluşturmakta olduğunuz anlamına gelir. Ancak, birden çok kapsayıcı uygulama de daha basit olabilir — örneğin, üç katmanlı uygulama — ve mikro hizmet mimarisi girilmesine değil.*

Daha önce biz "Docker mikro hizmet mimarisi oluştururken gerekli mi?" sorusunu gerçekleşti Yanıt bir Temizle Hayır'dır. Docker bir etkinleştiricisi ve önemli avantajlar sağlar ancak kapsayıcıları ve Docker mikro için sabit bir gereklilik değildir. Örneğin, mikro tabanlı bir uygulama ile veya olmadan Docker basit işlemler veya Docker kapsayıcılar olarak çalışan mikro destekleyen Azure Service Fabric kullanırken oluşturabilirsiniz.

Ayrıca Docker kapsayıcılarında tabanlı mikro tabanlı bir uygulama tasarlayıp nasıl biliyorsanız, diğer, daha basit uygulama modeli tasarlayıp mümkün olacaktır. Örneğin, aynı zamanda birden çok kapsayıcı yaklaşımı gerektirir üç katmanlı uygulama tasarlayabilirsiniz. Nedeniyle ve mikro hizmet mimarisi önemli bir eğilim kapsayıcı world içinde olduğundan, bu alt bölüm Docker kapsayıcıları kullanma mikro hizmet mimarisi uygulama üzerinde odaklanmıştır.


>[!div class="step-by-step"]
[Önceki] (.. /containerize-NET-Framework-Applications/index.MD) [sonraki] (mikro hizmet uygulama design.md)
