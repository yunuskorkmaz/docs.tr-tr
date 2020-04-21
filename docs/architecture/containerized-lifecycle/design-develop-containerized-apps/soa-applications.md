---
title: SOA uygulamaları
description: Kapsayıcıların SOA uygulamaları için yararlı bir dağıtım seçeneği olabileceğini unutmayın.
ms.date: 02/15/2019
ms.openlocfilehash: f8619cb50a7d90b911db9ff2c8ef37c3c5fde210
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738382"
---
# <a name="service-oriented-applications"></a>Hizmet odaklı uygulamalar

Hizmet Odaklı Mimari (SOA) farklı insanlar için çok farklı şeyler anlamına gelen aşırı kullanılan bir terimoldu. Ancak ortak payda olarak SOA, uygulamanızın mimarisini alt sistemler veya diğer durumlarda katman lar gibi farklı türlerde sınıflandırılabilen çeşitli hizmetlere (en yaygın olarak HTTP hizmetleri olarak) ayrıştırarak yapılandırdığınız anlamına gelir.

Bugün, tüm bağımlılıklar kapsayıcı görüntüsüne dahil olduğundan dağıtımla ilgili sorunları çözen bu hizmetleri Docker kapsayıcıları olarak dağıtabilirsiniz. Ancak, SOA'ları ölçeklendirmeniz gerektiğinde, tek bir örneğe göre dağıtım yapıyorsunuz zorluklarla karşılaşabilirsiniz. Bu sorun Docker kümeleme yazılımı veya bir orkestratör kullanılarak ele alınabilir. Mikro hizmetler yaklaşımlarını incelediğimiz de orkestratörlere bir sonraki bölümde daha ayrıntılı olarak bakacağız.

Docker kapsayıcıları hem geleneksel hizmet odaklı mimariler hem de daha gelişmiş microservices mimarileri için kullanışlıdır (ancak gerekli değildir).

Günün sonunda, konteyner kümeleme çözümleri hem geleneksel SOA mimarisi hem de her microservice'in kendi veri modeline sahip olduğu daha gelişmiş bir mikrohizmet mimarisi için yararlıdır. Birden çok veritabanı sayesinde, SOA hizmetleri tarafından paylaşılan yekpare veritabanlarıyla çalışmak yerine veri katmanını da ölçeklendirebilirsiniz. Ancak, verileri bölme ile ilgili tartışma tamamen mimari ve tasarım ile ilgilidir.

>[!div class="step-by-step"]
>[Önceki](state-and-data-in-docker-applications.md)
>[Sonraki](orchestrate-high-scalability-availability.md)
