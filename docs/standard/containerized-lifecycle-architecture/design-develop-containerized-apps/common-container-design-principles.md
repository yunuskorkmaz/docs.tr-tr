---
title: Ortak kapsayıcı tasarım ilkeleri
description: Temel bir iyi kapsayıcı tasarım ilkesini öğrenin, bir kapsayıcıyı tek bir işlem barındırmamalısınız.
ms.date: 02/15/2019
ms.openlocfilehash: 69f3ff6c9303f0c4082695d861a8c90031295b6a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644805"
---
# <a name="common-container-design-principles"></a>Ortak kapsayıcı tasarım ilkeleri

Önceden geliştirme işlemine başlama kapsayıcıları kullanma ile ilgili bahseden değer birkaç temel kavram vardır.

## <a name="container-equals-a-process"></a>Kapsayıcı işlemi eşittir

Kapsayıcı modelinde, tek bir işlem bir kapsayıcıyı temsil eder. Kapsayıcı işlemi sınır olarak tanımlayarak, Ölçek veya toplu kapalı, işlemleri için kullanılan ilkel oluşturmaya başlamadan. Bir Docker kapsayıcısı çalıştırdığınızda, gördüğünüz bir [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) tanımı. Bu işlem ve kapsayıcı ömrünü tanımlar. İşlem tamamlandığında, kapsayıcı yaşam döngüsü sona erer. Web sunucuları ve Microsoft Azure uygulanmış toplu işler gibi kısa süreli işlemler gibi uzun süre çalışan işlem [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/). İşlem başarısız olursa, kapsayıcı sona erer ve orchestrator sürüyorsa. Orchestrator çalışan beş örneklerinin tutmak istendi ve biri başarısız olursa, orchestrator başarısız işlemi değiştirmek için başka bir kapsayıcı oluşturur. Bir batch işinde parametrelerle işlemi başlatıldı. İşlem tamamlandığında, iş tamamlandığında.

Birden çok işlem tek bir kapsayıcıda çalıştırmak istediğiniz bir senaryo bulabilirsiniz. Herhangi bir mimari belgesinde yoktur hiçbir zaman bir "," ya da her zaman olduğu bir "her zaman." Birden çok işlem gerektiren senaryolar için yaygın bir düzen kullanmaktır [gözetmen](http://supervisord.org/).

>[!div class="step-by-step"]
>[Önceki](design-docker-applications.md)
>[İleri](monolithic-applications.md)
