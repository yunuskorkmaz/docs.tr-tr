---
title: Hizmet odaklı mimari
description: Mikro hizmetler ile hizmet odaklı mimari (SOA) arasındaki temel farklılıkları öğrenin.
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296217"
---
# <a name="service-oriented-architecture"></a>Hizmet odaklı mimari

Hizmet odaklı mimari (SOA), aşırı kullanılan bir terimdir ve farklı kişilere farklı şeyler sunmaktır. Ancak, ortak paydası olarak, SOA, alt sistemler veya Katmanlar gibi farklı türler olarak sınıflandırılabilen birden fazla hizmete (en yaygın olarak HTTP Hizmetleri) oluşturarak uygulamanızı yapılandıracağı anlamına gelir.

Bu hizmetler artık, dağıtım sorunlarını çözen Docker Kapsayıcıları olarak dağıtılabilir, çünkü tüm bağımlılıklar kapsayıcı görüntüsüne dahil edilmiştir. Ancak, SOA uygulamalarını ölçeklendirmeniz gerektiğinde, tek Docker konaklarına dayalı dağıtım yapıyorsanız ölçeklenebilirlik ve kullanılabilirlik güçlüklerine sahip olabilirsiniz. Bu, daha sonraki bölümlerde, mikro hizmetler için dağıtım yaklaşımlarının açıklandığı gibi Docker kümeleme yazılımının veya bir Orchestrator tarafından size yardımcı olabilir.

Docker Kapsayıcıları hem geleneksel hizmet yönelimli mimariler hem de daha gelişmiş mikro hizmet mimarileri için yararlıdır (ancak gerekli değildir).

Mikro hizmetler SOA 'den türetilir, ancak SOA, mikro hizmetler mimarisinden farklıdır. Büyük merkezi aracılar, kuruluş düzeyindeki merkezi düzenleyiciler ve [kurumsal Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) gibi özellikler Ise genellikle SOA 'de bulunur. Ancak çoğu durumda bunlar, mikro hizmet topluluğundaki daha etkili bir alışkanlığa sahiptir. Aslında, bazı kişiler "mikro hizmet mimarisi SOA tamamlandı."

Bu kılavuz, mikro hizmetlere odaklandığı için, bir SOA yaklaşımı mikro hizmet mimarisinde kullanılan gereksinimlerden ve tekniklerin daha az bir şekilde düşüktür. Mikro hizmet tabanlı bir uygulamanın nasıl oluşturulduğunu biliyorsanız, daha basit bir hizmet yönelimli uygulama oluşturmayı da bilirsiniz.

>[!div class="step-by-step"]
>[Önceki](docker-application-state-data.md)
>[İleri](microservices-architecture.md)
