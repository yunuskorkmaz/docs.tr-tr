---
title: SOA uygulamaları
description: Kapsayıcıları SOA uygulamalar için kullanışlı bir dağıtım seçeneği de olabilir aklınızda size aittir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 4fd39e075c5730cf7fddb0138cdb5267a914c91f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221270"
---
# <a name="soa-applications"></a>SOA uygulamaları

SOA aşırı kullanılmasına bir terim olan ve çok sayıda farklı şeyler farklı kişilere geliyordu. Ancak bu, yapı mimarisi (en yaygın olarak HTTP Hizmetleri) farklı türde sınıflandırılabilir birden çok Hizmetleri'nde parçalama tarafından uygulamanızın en az ve kullanımın ortak paydası olmasını, SOA, veya hizmet yönlendirmesi, ortalama olarak alt sistemler ister ya da diğer durumlarda, farklı katmanları.

Bugün, kapsayıcı görüntüsü içinde bulunan tüm bağımlılıkları olduğundan, dağıtımıyla ilgili sorunları çözer. Bu hizmetleri Docker kapsayıcıları olarak dağıtabilirsiniz. Ancak, SOAs genişletmek gerektiğinde bağlı olarak tek örnek dağıtıyorsanız zorlukları karşılaşabilirsiniz. Burada bir Docker yazılım veya orchestrator kümeleme yardımcı olacak budur. Mikro hizmetler yaklaşımları inceleyeceğiz, şu anda sonraki bölümde daha ayrıntılı olarak inceleyeceğiz.

Günün sonunda, kapsayıcı kümeleme çözümleri daha gelişmiş bir mikro hizmetler mimarisi her mikro hizmet kendi veri modelini sahip olduğu veya bir hem bir geleneksel SOA mimarisi için kullanışlı olur. Ayrıca, birden çok veritabanı sayesinde, ayrıca SOA Hizmetleri tarafından paylaşılan tek parça veritabanlarıyla çalışmak yerine veri katmanı ölçeklendirme. Ancak, verileri bölme hakkında bir tartışma tamamen mimari ve tasarım hakkında olur.

>[!div class="step-by-step"]
>[Önceki](state-and-data-in-docker-applications.md)
>[İleri](orchestrate-high-scalability-availability.md)