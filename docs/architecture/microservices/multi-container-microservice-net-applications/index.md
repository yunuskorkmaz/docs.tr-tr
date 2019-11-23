---
title: Çoklu kapsayıcı ve mikro hizmet tabanlı .NET uygulamaları tasarlama ve geliştirme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Çoklu kapsayıcı ve mikro hizmet tabanlı .NET uygulamaları tasarlama ve geliştirme için dış mimariyi anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296628"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Çok Kapsayıcılı ve mikro hizmet tabanlı .NET uygulamaları tasarlama ve geliştirme

*Kapsayıcılı mikro hizmet uygulamalarının geliştirilmesi, çok Kapsayıcılı uygulamalar oluşturduğunuz anlamına gelir. Ancak, çok kapsayıcılı bir uygulama da daha basit olabilir — Örneğin, üç katmanlı bir uygulama — ve mikro hizmet mimarisi kullanılarak derlenmeyebilir.*

Daha önce "bir mikro hizmet mimarisi oluştururken Docker gereklidir?" sorusunu yaptık. Yanıt, açık bir hayır. Docker bir etkinleştiricisidir ve önemli avantajlar sağlayabilir, ancak kapsayıcılar ve Docker mikro hizmetler için bir sabit gereksinimdir. Örnek olarak, basit süreçler veya Docker Kapsayıcıları olarak çalışan mikro hizmetleri destekleyen Azure Service Fabric kullanırken Docker ile veya olmayan mikro hizmetler tabanlı bir uygulama oluşturabilirsiniz.

Ancak, Docker kapsayıcılarına dayalı olarak da mikro hizmetler tabanlı bir uygulamayı tasarlamayı ve geliştirmeyi biliyorsanız, başka, daha basit bir uygulama modeli tasarlayabilecek ve geliştirebileceksiniz. Örneğin, çok kapsayıcılı bir yaklaşım gerektiren üç katmanlı bir uygulama tasarlayabilmeniz gerekir. Bu nedenle, mikro hizmet mimarileri kapsayıcı dünyasında önemli bir eğilim olduğundan, bu bölüm Docker Kapsayıcıları kullanılarak bir mikro hizmet mimarisi uygulamasına odaklanır.

>[!div class="step-by-step"]
>[Önceki](../docker-application-development-process/docker-app-development-workflow.md)
>[İleri](microservice-application-design.md)
