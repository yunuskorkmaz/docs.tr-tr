---
title: Ortak kapsayıcı tasarım ilkeleri
description: İyi kapsayıcı tasarımının temel bir ilkesini öğrenin, kapsayıcının yalnızca bir işlemi barındırması gerekir.
ms.date: 02/15/2019
ms.openlocfilehash: 69f3ff6c9303f0c4082695d861a8c90031295b6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295331"
---
# <a name="common-container-design-principles"></a>Ortak kapsayıcı tasarım ilkeleri

Geliştirme işlemine başlarken, kapsayıcıları nasıl kullanacağınızı gösteren birkaç temel kavram vardır.

## <a name="container-equals-a-process"></a>Kapsayıcı bir işleme eşit

Kapsayıcı modelinde bir kapsayıcı tek bir işlemi temsil eder. Bir kapsayıcıyı işlem sınırı olarak tanımlayarak, ölçeklendirmek veya toplu işlemleri yapmak için kullanılan temel türleri oluşturmaya başlayabilirsiniz. Bir Docker kapsayıcısını çalıştırdığınızda bir [giriş noktası](https://docs.docker.com/engine/reference/builder/#/entrypoint) tanımı görürsünüz. Bu işlem ve kapsayıcının ömrünü tanımlar. İşlem tamamlandığında kapsayıcı yaşam döngüsü sona erer. Web sunucuları gibi uzun süre çalışan işlemler ve toplu işler gibi kısa süreli işlemler, Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/)olarak uygulanmış olabilir. İşlem başarısız olursa, kapsayıcı sonlanır ve Orchestrator üzerinde sürer. Orchestrator 'da beş örnek tutulması ve biri başarısız olursa, Orchestrator başarısız işlemi değiştirmek için başka bir kapsayıcı oluşturur. Batch işinde, işlem parametrelerle başlatılır. İşlem tamamlandığında, çalışma tamamlanmıştır.

Tek bir kapsayıcıda birden çok işlemi çalıştırmak istediğiniz bir senaryo bulabilirsiniz. Herhangi bir mimari belgesinde hiçbir zaman "hiç" değil, her zaman "Always" yoktur. Birden çok işlem gerektiren senaryolar için ortak bir model, [Gözetmen](http://supervisord.org/)kullanmaktır.

>[!div class="step-by-step"]
>[Önceki](design-docker-applications.md)
>[İleri](monolithic-applications.md)
