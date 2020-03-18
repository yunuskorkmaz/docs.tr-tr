---
title: Ortak kapsayıcı tasarım ilkeleri
description: Iyi konteyner tasarımı temel bir ilke öğrenin, bir konteyner sadece bir süreç barındırmak gerektiğidir.
ms.date: 02/15/2019
ms.openlocfilehash: 69f3ff6c9303f0c4082695d861a8c90031295b6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295331"
---
# <a name="common-container-design-principles"></a>Ortak kapsayıcı tasarım ilkeleri

Geliştirme sürecine girmeden önce, kapsayıcıları nasıl kullandığınıza ilişkin olarak belirtilmesi gereken birkaç temel kavram vardır.

## <a name="container-equals-a-process"></a>Kapsayıcı bir işlem eşittir

Kapsayıcı modelinde, bir kapsayıcı tek bir işlemi temsil eder. Bir kapsayıcıyı işlem sınırı olarak tanımlayarak, işlemleri ölçeklendirmek veya toplu olarak kapatmak için kullanılan ilkel leri oluşturmaya başlarsınız. Docker kapsayıcısı çalıştırdığınızda, bir [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) tanımı görürsünüz. Bu işlem ve kapsayıcının ömrünü tanımlar. İşlem tamamlandığında, kapsayıcı yaşam döngüsü sona erer. Web sunucuları gibi uzun süren işlemler ve Microsoft Azure [Web İşleri](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/)olarak uygulanmış olabilecek toplu iş işleri gibi kısa ömürlü işlemler vardır. İşlem başarısız olursa, kapsayıcı sona erer ve orkestratör devralır. Orkestratöre beş örneği çalışır durumda tutması ve biri başarısız olursa, orkestratör başarısız olan işlemin yerini alacak başka bir kapsayıcı oluşturur. Toplu iş işinde, işlem parametrelerle başlatılır. İşlem tamamlandığında, çalışma tamamlanır.

Tek bir kapsayıcıda birden çok işlem çalışmasını istediğiniz bir senaryo bulabilirsiniz. Herhangi bir mimari belgede asla "asla" ya da her zaman "her zaman" yoktur. Birden çok işlem gerektiren senaryolar için, ortak bir desen [Supervisor](http://supervisord.org/)kullanmaktır.

>[!div class="step-by-step"]
>[Önceki](design-docker-applications.md)
>[Sonraki](monolithic-applications.md)
