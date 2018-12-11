---
title: SOA uygulamaları
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 7f88daaf0787cf780e7ab9602f35ae4e6ab8308c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155320"
---
# <a name="soa-applications"></a>SOA uygulamaları

SOA aşırı kullanılmasına bir terim olan ve çok sayıda farklı şeyler farklı kişilere geliyordu. Ancak bu, yapı mimarisi (en yaygın olarak HTTP Hizmetleri) farklı türde sınıflandırılabilir birden çok Hizmetleri'nde parçalama tarafından uygulamanızın en az ve kullanımın ortak paydası olmasını, SOA, veya hizmet yönlendirmesi, ortalama olarak alt sistemler ister ya da diğer durumlarda, farklı katmanları.

Bugün, kapsayıcı görüntüsü içinde bulunan tüm bağımlılıkları olduğundan, dağıtımıyla ilgili sorunları çözer. Bu hizmetleri Docker kapsayıcıları olarak dağıtabilirsiniz. Ancak, SOAs genişletmek gerektiğinde bağlı olarak tek örnek dağıtıyorsanız zorlukları karşılaşabilirsiniz. Burada bir Docker yazılım veya orchestrator kümeleme yardımcı olacak budur. Mikro hizmetler yaklaşımları inceleyeceğiz, şu anda sonraki bölümde daha ayrıntılı olarak inceleyeceğiz.

Günün sonunda, kapsayıcı kümeleme çözümleri daha gelişmiş bir mikro hizmetler mimarisi her mikro hizmet kendi veri modelini sahip olduğu veya bir hem bir geleneksel SOA mimarisi için kullanışlı olur. Ayrıca, birden çok veritabanı sayesinde, ayrıca SOA Hizmetleri tarafından paylaşılan tek parça veritabanlarıyla çalışmak yerine veri katmanı ölçeklendirme. Ancak, verileri bölme hakkında bir tartışma tamamen mimari ve tasarım hakkında olur.

>[!div class="step-by-step"]
>[Önceki](state-and-data-in-docker-applications.md)
>[İleri](orchestrate-high-scalability-availability.md)