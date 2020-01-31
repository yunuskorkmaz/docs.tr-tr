---
title: Bulutta yerel dayanıklılık
description: Azure için Cloud Native .NET uygulamaları tasarlama | Cloud Native dayanıklılık
ms.date: 06/30/2019
ms.openlocfilehash: 427405d95534c4467ab519c2188fe88e2f18e2b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781079"
---
# <a name="cloud-native-resiliency"></a>Bulutta yerel dayanıklılık

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Dayanıklılık, sisteminizin hataya tepki verme ve hala işlevsel olmaya devam etme yeteneğidir. Hatanın kaçınılmıyor. Ancak, bu hatanın bulut tabanlı sistemlerde çok fazla tablo olduğunu kabul ediyor ve uygulamanızı yanıt verecek şekilde oluşturuyor. Dayanıklılığın son amacı, bir hatadan sonra uygulamayı tam çalışır duruma döndürmektir.

Her şeyin tek bir işlemde birlikte çalıştığı geleneksel tek parçalı uygulamalardan farklı olarak, bulut Yerel sistemleri Şekil 6-1 ' de gösterildiği gibi, dağıtılmış mimariden yararlanın:

![Dağıtılmış bulutta yerel ortam](./media/distributed-cloud-native-environment.png)

**Şekil 6-1.** Dağıtılmış bulutta yerel ortam

Önceki şekilde, her bir istemci, mikro hizmet ve bulut tabanlı [yedekleme hizmetinin](https://12factor.net/backing-services) , farklı sunucular arasında çalışan, ağ tabanlı çağrılar aracılığıyla iletişim kuran ayrı bir işlem olarak nasıl yürütüldüğünü aklınızda olduğunu fark edin.

Bu nedenle, ne kadar hatalı gidebilirler?

- Beklenmeyen [ağ gecikmesi](https://www.techopedia.com/definition/8553/network-latency).
- [Geçici hatalar](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (geçici ağ bağlantısı hataları).
- Uzun süre çalışan bir zaman uyumlu işlem tarafından engelleniyor.
- Kilitlenen ve yeniden başlatılan veya taşınan bir ana bilgisayar işlemi.
- Kısa bir süre yanıt vermeyen aşırı yüklenmiş bir mikro hizmet.
- Güncelleştirme veya ölçeklendirme işlemi gibi bir uçuş DevOps işlemi.
- Bir hizmeti bir düğümden diğerine taşıma gibi bir Orchestrator işlemi.
- Emtia donanımlarından donanım sorunları.

Dağıtılmış hizmetleri bulut tabanlı altyapıya dağıttığınızda, önceki listedeki faktörler çok gerçek hale gelir ve bunlarla uğraşmak için yüksek savunma ve mimariyi geliştirme yapmanız gerekir.

Küçük ölçekli bir dağıtılmış sistemde, hata sık sık olacaktır, ancak bir sistem ölçeği büyüerek, bu sorunlardan daha fazlasını, kısmi hatanın normal işlem haline geldiği bir noktaya daha fazla deneyim sağlayabilirsiniz.

Bu nedenle, uygulamanız ve altyapınız dayanıklı olmalıdır. Aşağıdaki bölümlerde, uygulamanıza ekleyebileceğiniz savunma tekniklerini ve Kullanıcı deneyiminizin madde işaretine yardımcı olmak için kullanabileceğiniz yerleşik bulut özelliklerini keşfedeceğiz.

>[!div class="step-by-step"]
>[Önceki](elastic-search-in-azure.md)
>[İleri](application-resiliency-patterns.md)
