---
title: .NET uygulamaları tasarlayıp geliştirerek çok kapsayıcılı ve mikro hizmet tabanlı
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Dış mimarisi tasarlama ve geliştirme çok kapsayıcılı ve mikro hizmet tabanlı .NET uygulamaları için anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639467"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>.NET çok kapsayıcılı ve mikro hizmet tabanlı uygulamalar tasarlayıp geliştirerek

*Kapsayıcılı mikro hizmet uygulamaları geliştirme, çok kapsayıcılı uygulamalar oluşturmakta olduğunuz anlamına gelir. Ancak, çok kapsayıcılı bir uygulama aynı zamanda daha basit olabilir — örneğin, bir üç katmanlı uygulama — ve mikro hizmet mimarisi kullanılarak oluşturulmamış olabilir.*

Daha önce biz "Docker mikro hizmet mimarisi oluşturma sırasında gerekli mi?" sorusunu oluşturuldu Yanıttır Temizle yok. Docker bir Etkinleştirici ve önemli avantajlar sağlayabilir, ancak kapsayıcıları ve Docker mikro hizmetlere yönelik bir gereksinim değildir. Örneğin, bir mikro hizmet tabanlı uygulama ile veya olmadan Docker basit işlemler veya Docker kapsayıcıları olarak çalışan mikro hizmetler destekleyen Azure Service Fabric kullanırken oluşturabilirsiniz.

Ayrıca Docker kapsayıcılarında alan bir mikro hizmet tabanlı uygulama tasarlayıp oluşturmayı biliyorsanız, diğer herhangi bir basit uygulama modeli tasarlayıp mümkün olacaktır. Örneğin, aynı zamanda çok kapsayıcılı bir yaklaşım gerektirir ve üç katmanlı bir uygulama tasarlayabilirsiniz. Nedeniyle ve mikro hizmet mimarileri kapsayıcı dünyanın içinde önemli bir eğilim olduğundan, bu bölüm Docker kapsayıcılarını kullanarak bir mikro hizmet mimarisi uygulaması üzerinde odaklanır.

>[!div class="step-by-step"]
>[Önceki](../docker-application-development-process/docker-app-development-workflow.md)
>[İleri](microservice-application-design.md)
