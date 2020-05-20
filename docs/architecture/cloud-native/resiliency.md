---
title: Bulutta yerel dayanıklılık
description: Azure için Cloud Native .NET uygulamaları tasarlama | Cloud Native dayanıklılık
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: f3aa89e3ae21b13a31f65013b59636b3f931553c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613778"
---
# <a name="cloud-native-resiliency"></a>Bulutta yerel dayanıklılık

Dayanıklılık, sisteminizin hataya tepki verme ve hala işlevsel olmaya devam etme yeteneğidir. Hatayı önleme, ancak hatayı kabul etme ve buluta yerel hizmetlerinizi oluşturma hakkında bilgi almak için bu değildir. Mümkün olduğunca hızlı bir şekilde çalışır duruma geri dönmek istiyorsunuz.

Her şeyin tek bir işlemde birlikte çalıştığı geleneksel tek parçalı uygulamalardan farklı olarak, bulutta yerel sistemler Şekil 6-1 ' de gösterildiği gibi dağıtılmış bir mimarinin ayracına sahiptir:

![Dağıtılmış bulutta yerel ortam](./media/distributed-cloud-native-environment.png)

**Şekil 6-1.** Dağıtılmış bulutta yerel ortam

Önceki şekilde, her mikro hizmet ve bulut tabanlı [yedekleme hizmeti](https://12factor.net/backing-services) , ağ tabanlı çağrılar üzerinden iletişim kurarak sunucu altyapısı genelinde ayrı bir işlemde yürütülür.

Bu ortamda çalışırken, bir hizmet birçok farklı güçlüklere duyarlı olmalıdır:

- Beklenmeyen ağ gecikmesi-bir hizmet isteğinin alıcıya ve geri yolculuğu için geçen süre.

- [Geçici hatalar](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) -kısa süreli ağ bağlantısı hataları.

- Uzun süre çalışan bir zaman uyumlu işlem ile engelleme.

- Kilitlenen ve yeniden başlatılan veya taşınan bir ana bilgisayar işlemi.

- Kısa bir süre yanıt vermeyen aşırı yüklenmiş bir mikro hizmet.

- Sıralı yükseltme veya bir hizmeti bir düğümden diğerine taşıma gibi uçuş için bir Orchestrator işlemi.

- Donanım sorunları.

Bulut platformları, bu altyapı sorunlarının çoğunu algılayabilir ve azaltır. Hizmetinizi yeniden başlatabilir, ölçeklendirebilir ve hatta farklı bir düğüme yeniden dağıtabilir.  Ancak, bu yerleşik korumadan tam olarak yararlanabilmek için, bu dinamik ortamda BT ve Misyonumuz 'e tepki vermek üzere hizmetlerinizi tasarlamanız gerekir.

Aşağıdaki bölümlerde, hizmet ve yönetilen bulut kaynaklarınızın kapalı kalma süresini ve kesintiyi en aza indirmek için yararlanabilen savunma tekniklerini keşfedeceğiz.

>[!div class="step-by-step"]
>[Önceki](elastic-search-in-azure.md) 
> [Sonraki](application-resiliency-patterns.md)
