---
title: .NET uygulamaları tasarlayıp geliştirerek çok kapsayıcılı ve mikro hizmet tabanlı
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Dış mimarisi tasarlama ve geliştirme çok kapsayıcılı ve mikro hizmet tabanlı .NET uygulamaları için anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 3bbf746aa9c0b66a097b8c4df2964b5679342fd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973634"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>.NET çok kapsayıcılı ve mikro hizmet tabanlı uygulamalar tasarlayıp geliştirerek

*Kapsayıcılı mikro hizmet uygulamaları geliştirme, çok kapsayıcılı uygulamalar oluşturmakta olduğunuz anlamına gelir. Ancak, çok kapsayıcılı bir uygulama aynı zamanda daha basit olabilir — örneğin, bir üç katmanlı uygulama — ve mikro hizmet mimarisi kullanılarak oluşturulmamış olabilir.*

Daha önce biz "Docker mikro hizmet mimarisi oluşturma sırasında gerekli mi?" sorusunu oluşturuldu Yanıttır Temizle yok. Docker bir Etkinleştirici ve önemli avantajlar sağlayabilir, ancak kapsayıcıları ve Docker mikro hizmetlere yönelik bir gereksinim değildir. Örneğin, bir mikro hizmet tabanlı uygulama ile veya olmadan Docker basit işlemler veya Docker kapsayıcıları olarak çalışan mikro hizmetler destekleyen Azure Service Fabric kullanırken oluşturabilirsiniz.

Ayrıca Docker kapsayıcılarında alan bir mikro hizmet tabanlı uygulama tasarlayıp oluşturmayı biliyorsanız, diğer herhangi bir basit uygulama modeli tasarlayıp mümkün olacaktır. Örneğin, aynı zamanda çok kapsayıcılı bir yaklaşım gerektirir ve üç katmanlı bir uygulama tasarlayabilirsiniz. Nedeniyle ve mikro hizmet mimarileri kapsayıcı dünyanın içinde önemli bir eğilim olduğundan, bu bölüm Docker kapsayıcılarını kullanarak bir mikro hizmet mimarisi uygulaması üzerinde odaklanır.

>[!div class="step-by-step"]
>[Önceki](../docker-application-development-process/docker-app-development-workflow.md)
>[İleri](microservice-application-design.md)