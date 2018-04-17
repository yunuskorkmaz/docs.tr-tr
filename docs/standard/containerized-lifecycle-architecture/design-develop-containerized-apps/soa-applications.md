---
title: SOA uygulamaları
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 48dc0f038cee8ddc9555881f2143b566df223a04
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="soa-applications"></a>SOA uygulamaları

SOA aşırı kullanılmasına bir terim oldu ve farklı kişilere çok sayıda farklı işlemler anlamına gelir. Ancak en az bir ortak payda, SOA, ya da hizmet yönlendirmesi, ortalama olarak, bu yapıyı uygulamanız farklı türde sınıflandırılabilir birden çok hizmetlerinde (en yaygın olarak HTTP Hizmetleri) ayırma tarafından mimarisi gibi ve alt sistemleri ya da diğer durumlarda, farklı katmanlarını.

Bugün, tüm bağımlılıklarıyla içinde kapsayıcı görüntü dahil olduğundan, dağıtım ile ilgili sorunları çözer bu hizmetlerin Docker kapsayıcılar olarak dağıtabilirsiniz. Ancak, SOAs genişletmek gerektiğinde, bağlı tek örneklerini dağıtıyorsanız zorluklar karşılaşabilirsiniz. Burada yazılım veya orchestrator kümeleme Docker yardımcı olacak budur. Biz mikro yaklaşımlar incelediğinizde biz şu anda sonraki bölümde daha ayrıntılı göreceğiz.

Günün sonunda, kapsayıcı kümeleme çözümleri her mikro hizmet kendi veri modelini sahibi daha gelişmiş bir mikro mimarisi veya bir hem bir geleneksel SOA mimarisi için faydalıdır. Ve birden çok veritabanı sayesinde, ayrıca SOA Hizmetleri tarafından paylaşılan tek yapılı veritabanlarıyla çalışma yerine veri katmanı genişletme. Ancak, veri bölme hakkında tartışma tamamen mimarisi ve tasarım hakkında ' dir.


>[!div class="step-by-step"]
[Önceki] (state-and-data-in-docker-applications.md) [sonraki] (düzenlemek-yüksek-ölçeklenebilirlik-availability.md)
