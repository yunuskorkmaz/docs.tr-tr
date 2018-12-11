---
title: Ortak kapsayıcı tasarım ilkeleri
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 8aa388c7c19f532829d64208a48b6e556e43d802
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152883"
---
# <a name="common-container-design-principles"></a>Ortak kapsayıcı tasarım ilkeleri

Önceden geliştirme işlemine başlama kapsayıcıları kullanma ile ilgili bahseden değer birkaç temel kavram vardır.

## <a name="container-equals-a-process"></a>Kapsayıcı işlemi eşittir

Kapsayıcı modelinde, tek bir işlem bir kapsayıcıyı temsil eder. Kapsayıcı işlemi sınır olarak tanımlayarak, Ölçek veya toplu kapalı, işlemleri için kullanılan ilkel oluşturmaya başlamadan. Bir Docker kapsayıcısı çalıştırdığınızda, gördüğünüz bir [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) tanımı. Bu işlem ve kapsayıcı ömrünü tanımlar. İşlem tamamlandığında, kapsayıcı yaşam döngüsü sona erer. Web sunucuları ve Microsoft Azure uygulanmış toplu işler gibi kısa süreli işlemler gibi uzun süre çalışan işlem [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/). İşlem başarısız olursa, kapsayıcı sona erer ve orchestrator sürüyorsa. Orchestrator çalışan beş örneklerinin tutmak istendi ve biri başarısız olursa, orchestrator başarısız işlemi değiştirmek için başka bir kapsayıcı oluşturur. Bir batch işinde parametrelerle işlemi başlatıldı. İşlem tamamlandığında, iş tamamlandığında.

Birden çok işlem tek bir kapsayıcıda çalıştırmak istediğiniz bir senaryo bulabilirsiniz. Herhangi bir mimari belgesinde yoktur hiçbir zaman bir "," ya da her zaman olduğu bir "her zaman." Birden çok işlem gerektiren senaryolar için yaygın bir düzen kullanmaktır [gözetmen](http://supervisord.org/).

>[!div class="step-by-step"]
>[Önceki](design-docker-applications.md)
>[İleri](monolithic-applications.md)