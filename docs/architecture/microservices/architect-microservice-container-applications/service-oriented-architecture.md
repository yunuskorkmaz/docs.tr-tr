---
title: Hizmet odaklı mimari
description: Mikro hizmetler ile Hizmet odaklı mimari (SOA) arasındaki temel farkları öğrenin.
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296217"
---
# <a name="service-oriented-architecture"></a>Hizmet odaklı mimari

Hizmet odaklı mimari (SOA) aşırı kullanılan bir terim di ve farklı insanlar için farklı şeyler anlamına geliyordu. Ancak ortak bir payda olarak SOA, uygulamanızı alt sistemler veya katmanlar gibi farklı türler olarak sınıflandırılabilen birden çok hizmete (en yaygın olarak HTTP hizmetleri olarak) ayrıştırarak yapılandırdığınız anlamına gelir.

Tüm bağımlılıklar kapsayıcı görüntüsüne dahil olduğundan, bu hizmetler artık dağıtım sorunlarını çözen Docker kapsayıcıları olarak dağıtılabilir. Ancak, SOA uygulamalarını ölçeklendirmeniz gerektiğinde, tek Docker ana bilgisayarlarına göre dağıtım yapıyorsanız ölçeklenebilirlik ve kullanılabilirlik zorluklarına sahip olabilirsiniz. Burası Docker kümeleme yazılımının veya bir orkestratörün, mikro hizmetler için dağıtım yaklaşımlarının açıklandığı sonraki bölümlerde açıklandığı gibi size yardımcı olabileceği yerdir.

Docker kapsayıcıları hem geleneksel hizmet odaklı mimariler hem de daha gelişmiş microservices mimarileri için kullanışlıdır (ancak gerekli değildir).

Microservices SOA türetilmiştir, ancak SOA microservices mimarisi farklıdır. Büyük merkezi brokerlar, organizasyon düzeyinde merkezi orkestrasyonlar ve [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) gibi özellikler SOA'da tipiktir. Ama çoğu durumda, bu mikro hizmet toplumda anti-desenler vardır. Aslında, bazı insanlar "microservice mimarisi SOA doğru yapılır" savunuyorlar.

Soa yaklaşımı, mikro hizmet mimarisinde kullanılan gereksinimve tekniklerden daha az açıklayıcı olduğundan, bu kılavuz mikro hizmetlere odaklanır. Mikro hizmet tabanlı bir uygulama oluşturmayı biliyorsanız, daha basit bir hizmet odaklı uygulamayı nasıl oluşturabileceğinizi de bilirsiniz.

>[!div class="step-by-step"]
>[Önceki](docker-application-state-data.md)
>[Sonraki](microservices-architecture.md)
