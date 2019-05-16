---
title: Hizmet odaklı mimari
description: Mikro hizmetler ve hizmet odaklı mimari (SOA) arasındaki temel farklar öğrenin.
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640062"
---
# <a name="service-oriented-architecture"></a>Hizmet odaklı mimari

Hizmet odaklı mimari (SOA) olan bir aşırı kullanılmasına terim ve farklı kişiler için farklı şeyler hazırlanmıştır. Ancak, bir ortak paydası (en yaygın olarak HTTP Hizmetleri) farklı alt sistemler veya katmanları gibi olarak sınıflandırılan birden çok hizmetlerine parçalama tarafından uygulamanızı yapı SOA anlamına gelir.

Kapsayıcı görüntüsü dahil tüm bağımlılıkları olmadığından bu hizmetleri artık Docker kapsayıcıları olarak hangi dağıtım sorunlarını çözer dağıtılabilir. Ancak, SOA uygulamaları Ölçeklendirmesi gerektiğinde, ölçeklenebilirlik olabilir ve dağıtım yapıyorsanız kullanılabilirlik sorunları tek Docker konakları üzerinde temel. Docker kümeleme yazılım ya da bir orchestrator, burada sağlayabilirsiniz mikro hizmetlere yönelik dağıtım yaklaşımları burada açıklanan sonraki bölümlerde açıklandığı gibi budur.

Docker kapsayıcıları yararlı (ancak gerekli değil) hizmet odaklı geleneksel mimarilerde hem de daha gelişmiş bir mikro hizmet mimarileri için.

Mikro hizmetler SOA türetilen ancak mikro hizmetler mimarisi SOA farklıdır. Büyük merkezi aracıları gibi özellikler, kuruluş düzeyindeki merkez düzenleyiciler ve [Enterprise Service Bus'ı (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) SOA içinde normal. Ancak, çoğu durumda, bunlar mikro hizmet topluluğundaki ters desenler. Aslında, bazı kişiler "mikro hizmet mimarisi doğru yapıldığında SOA olduğunu." buna

Bir mikro hizmet mimarisinde kullanılır teknikler ve gereksinimleri daha az öngörücü SOA yaklaşımdır çünkü bu kılavuz, mikro hizmetler üzerinde odaklanır. Bir mikro hizmet tabanlı uygulama oluşturmayı biliyorsanız, ayrıca hizmet odaklı basit bir uygulamanın nasıl oluşturulacağını bilmeniz.

>[!div class="step-by-step"]
>[Önceki](docker-application-state-data.md)
>[İleri](microservices-architecture.md)
