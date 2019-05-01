---
title: SOA uygulamaları
description: Kapsayıcıları SOA uygulamalar için kullanışlı bir dağıtım seçeneği de olabilir aklınızda size aittir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: ee71873ac15246f979fd2b08d92280ba797ff6ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795414"
---
# <a name="service-oriented-applications"></a>Hizmet odaklı uygulamalar

Hizmet odaklı mimari (SOA) birçok farklı şey farklı kişilere geliyordu aşırı kullanılmasına bir terim oluştu. Ancak, alt sistemleri gibi farklı türlerde veya diğer durumlarda, katmanları olarak sınıflandırılan çeşitli Hizmetleri (en yaygın olarak HTTP Hizmetleri) parçalama tarafından uygulamanızın mimarisini yapısı bir ortak paydası SOA anlamına gelir.

Bugün, bu hizmetler, tüm bağımlılıkları kapsayıcı görüntüsüne dahil olduğu dağıtımıyla ilgili sorunları çözmeye Docker kapsayıcıları olarak dağıtabilirsiniz. Ancak, out SOAs Ölçeklendirmesi gerektiğinde, bağlı olarak tek örnek dağıtıyorsanız zorlukları karşılaşabilirsiniz. Bu sınama, yazılım veya bir orchestrator kümeleme Docker kullanarak işlenebilir. Mikro hizmetler yaklaşımları inceleyeceğiz, sonraki bölümde daha ayrıntılı düzenleyicileri şu konuları inceleyeceğiz.

Docker kapsayıcıları yararlı (ancak gerekli değil) hizmet odaklı geleneksel mimarilerde hem de daha gelişmiş bir mikro hizmet mimarileri için.

Günün sonunda, kapsayıcı kümeleme çözümleri ve her bir mikro hizmet kendi veri modelini sahibi olan daha gelişmiş bir mikro hizmet mimarisi bir hem bir geleneksel SOA mimarisi için yararlı olur. Ve birden çok veritabanı sayesinde, ayrıca SOA Hizmetleri tarafından paylaşılan tek parça veritabanlarıyla çalışmak yerine veri katmanı ölçeğini genişletebilirsiniz. Ancak, verileri bölme hakkında bir tartışma tamamen mimari ve tasarım hakkında olur.

>[!div class="step-by-step"]
>[Önceki](state-and-data-in-docker-applications.md)
>[İleri](orchestrate-high-scalability-availability.md)
