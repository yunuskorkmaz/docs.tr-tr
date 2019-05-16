---
title: SOA uygulamaları
description: Kapsayıcıları SOA uygulamalar için kullanışlı bir dağıtım seçeneği de olabilir aklınızda size aittir.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644760"
---
# <a name="service-oriented-applications"></a>Hizmet odaklı uygulamalar

Hizmet odaklı mimari (SOA) birçok farklı şey farklı kişilere geliyordu aşırı kullanılmasına bir terim oluştu. Ancak, alt sistemleri gibi farklı türlerde veya diğer durumlarda, katmanları olarak sınıflandırılan çeşitli Hizmetleri (en yaygın olarak HTTP Hizmetleri) parçalama tarafından uygulamanızın mimarisini yapısı bir ortak paydası SOA anlamına gelir.

Bugün, bu hizmetler, tüm bağımlılıkları kapsayıcı görüntüsüne dahil olduğu dağıtımıyla ilgili sorunları çözmeye Docker kapsayıcıları olarak dağıtabilirsiniz. Ancak, out SOAs Ölçeklendirmesi gerektiğinde, bağlı olarak tek örnek dağıtıyorsanız zorlukları karşılaşabilirsiniz. Bu sınama, yazılım veya bir orchestrator kümeleme Docker kullanarak işlenebilir. Mikro hizmetler yaklaşımları inceleyeceğiz, sonraki bölümde daha ayrıntılı düzenleyicileri şu konuları inceleyeceğiz.

Docker kapsayıcıları yararlı (ancak gerekli değil) hizmet odaklı geleneksel mimarilerde hem de daha gelişmiş bir mikro hizmet mimarileri için.

Günün sonunda, kapsayıcı kümeleme çözümleri ve her bir mikro hizmet kendi veri modelini sahibi olan daha gelişmiş bir mikro hizmet mimarisi bir hem bir geleneksel SOA mimarisi için yararlı olur. Ve birden çok veritabanı sayesinde, ayrıca SOA Hizmetleri tarafından paylaşılan tek parça veritabanlarıyla çalışmak yerine veri katmanı ölçeğini genişletebilirsiniz. Ancak, verileri bölme hakkında bir tartışma tamamen mimari ve tasarım hakkında olur.

>[!div class="step-by-step"]
>[Önceki](state-and-data-in-docker-applications.md)
>[İleri](orchestrate-high-scalability-availability.md)
