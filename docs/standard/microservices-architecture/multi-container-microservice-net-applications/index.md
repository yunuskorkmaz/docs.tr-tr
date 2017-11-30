---
title: ".NET uygulamaları tasarlama ve birden çok kapsayıcı ve mikro hizmet geliştirirken dayalı"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET uygulamaları tasarlama ve birden çok kapsayıcı ve mikro hizmet geliştirirken dayalı"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 46d2859fa3b739b1a2a8b1502d4e418fab204648
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Tasarlama ve birden çok kapsayıcı ve mikro hizmet tabanlı .NET uygulamaları geliştirme

*Kapsayıcılı mikro hizmet uygulamaları geliştirme çok kapsayıcı uygulamaları oluşturmakta olduğunuz anlamına gelir. Ancak, birden çok kapsayıcı uygulama de daha basit olabilir — örneğin, üç katmanlı uygulama — ve mikro hizmet mimarisi girilmesine değil.*

Daha önce biz "Docker mikro hizmet mimarisi oluştururken gerekli mi?" sorusunu gerçekleşti Yanıt bir Temizle Hayır'dır. Docker bir etkinleştiricisi ve önemli avantajlar sağlar ancak kapsayıcıları ve Docker mikro için sabit bir gereklilik değildir. Örneğin, mikro tabanlı bir uygulama ile veya olmadan Docker basit işlemler veya Docker kapsayıcılar olarak çalışan mikro destekleyen Azure Service Fabric kullanırken oluşturabilirsiniz.

Ayrıca Docker kapsayıcılarında tabanlı mikro tabanlı bir uygulama tasarlayıp nasıl biliyorsanız, diğer, daha basit uygulama modeli tasarlayıp mümkün olacaktır. Örneğin, aynı zamanda birden çok kapsayıcı yaklaşımı gerektirir üç katmanlı uygulama tasarlayabilirsiniz. Nedeniyle ve mikro hizmet mimarisi önemli bir eğilim kapsayıcı world içinde olduğundan, bu alt bölüm Docker kapsayıcıları kullanma mikro hizmet mimarisi uygulama üzerinde odaklanmıştır.


>[!div class="step-by-step"]
[Önceki] (.. /containerize-NET-Framework-Applications/index.MD) [sonraki] (mikro hizmet uygulama design.md)
