---
title: Hizmet odaklı mimari
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Hizmet odaklı mimari
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ce4addefc7b6b1cf82551bf8304b7f06f1614796
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573821"
---
# <a name="service-oriented-architecture"></a>Hizmet odaklı mimari 

Hizmet odaklı mimari (SOA) aşırı kullanılmasına bir terim oldu ve farklı kişilere farklı işlemler amacı. Ancak ortak payda olarak farklı alt sistemleri veya katmanları gibi olarak sınıflandırılan birden çok hizmetlerine (en yaygın olarak HTTP Hizmetleri) ayırma tarafından uygulamanızı yapısı SOA anlamına gelir.

Kapsayıcı görüntüde tüm bağımlılıkları içerdiğinden bu hizmetleri artık Docker kapsayıcılar olarak hangi dağıtım sorunlarını çözer dağıtılabilir. Ancak, SOA uygulamaları ölçeklendirme gerektiğinde ölçeklenebilirlik olabilir ve tek Docker konaklarda dağıtıyorsanız kullanılabilirlik zorluklar tabanlı. Burada yazılım ya da bir orchestrator kümeleme Docker çıkışı, yardımcı olacak burada biz mikro dağıtım yaklaşımlar açıklamak sonraki bölümlerde açıklandığı gibi budur.

Docker kapsayıcıları yararlı (ancak gerekli değildir) geleneksel hizmet odaklı mimari ve daha gelişmiş mikro mimarileri için.

Mikro SOA türetilen ancak SOA mikro mimarisinden farklı. Büyük merkezi aracıları gibi özellikleri, kuruluş düzeyinde merkezi orchestrators ve [Kurumsal hizmet veri yolu (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) içinde SOA tipik değerlerdir. Ancak, çoğu durumda bunlar mikro hizmet topluluk koruma düzenleri. Aslında, bazı kişiler "mikro hizmet mimarisi doğru şekilde yapabilmeniz SOA olduğunu." karşıdır

Bir SOA yaklaşım mikro hizmet mimarisinde kullanılan teknikleri ve gereksinimleri daha az Düzenleyici olduğundan bu kılavuz mikro üzerinde odaklanmıştır. Mikro hizmet tabanlı bir uygulama oluşturmak nasıl biliyorsanız, ayrıca daha basit bir hizmet odaklı uygulamasının nasıl oluşturulacağını bilmeniz.




>[!div class="step-by-step"]
[Önceki] (docker-uygulama-durumu-data.md) [sonraki] (mikro-architecture.md)
