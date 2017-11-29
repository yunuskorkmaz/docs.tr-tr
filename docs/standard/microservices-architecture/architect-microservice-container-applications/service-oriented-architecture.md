---
title: "Hizmet odaklı mimari"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Hizmet odaklı mimari"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 970ff86c77100077d4c7710c0a697d1745d35819
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="service-oriented-architecture"></a>Hizmet odaklı mimari 

Hizmet odaklı mimari (SOA) aşırı kullanılmasına bir terim oldu ve farklı kişilere farklı işlemler amacı. Ancak ortak payda olarak farklı alt sistemleri veya katmanları gibi olarak sınıflandırılan birden çok hizmetlerine (en yaygın olarak HTTP Hizmetleri) ayırma tarafından uygulamanızı yapısı SOA anlamına gelir.

Kapsayıcı görüntüde tüm bağımlılıkları içerdiğinden bu hizmetleri artık Docker kapsayıcılar olarak hangi dağıtım sorunlarını çözer dağıtılabilir. Ancak, SOA uygulamaları ölçeklendirme gerektiğinde ölçeklenebilirlik olabilir ve tek Docker konaklarda dağıtıyorsanız kullanılabilirlik zorluklar tabanlı. Burada yazılım ya da bir orchestrator kümeleme Docker çıkışı, yardımcı olacak burada biz mikro dağıtım yaklaşımlar açıklamak sonraki bölümlerde açıklandığı gibi budur.

Docker kapsayıcıları yararlı (ancak gerekli değildir) geleneksel hizmet odaklı mimari ve daha gelişmiş mikro mimarileri için.

Mikro SOA türetilen ancak SOA mikro mimarisinden farklı. Büyük merkezi aracıları gibi özellikleri, kuruluş düzeyinde merkezi orchestrators ve [Kurumsal hizmet veri yolu (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) içinde SOA tipik değerlerdir. Ancak, çoğu durumda bunlar mikro hizmet topluluk koruma düzenleri. Aslında, bazı kişiler "mikro hizmet mimarisi doğru şekilde yapabilmeniz SOA olduğunu." karşıdır

Bir SOA yaklaşım mikro hizmet mimarisinde kullanılan teknikleri ve gereksinimleri daha az Düzenleyici olduğundan bu kılavuz mikro üzerinde odaklanmıştır. Mikro hizmet tabanlı bir uygulama oluşturmak nasıl biliyorsanız, ayrıca daha basit bir hizmet odaklı uygulamasının nasıl oluşturulacağını bilmeniz.




>[!div class="step-by-step"]
[Önceki] (docker-uygulama-durumu-data.md) [sonraki] (mikro-architecture.md)
