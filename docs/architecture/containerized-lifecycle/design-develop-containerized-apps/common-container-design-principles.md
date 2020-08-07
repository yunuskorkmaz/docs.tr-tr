---
title: Ortak kapsayıcı tasarım ilkeleri
description: İyi kapsayıcı tasarımının temel bir ilkesini öğrenin, kapsayıcının yalnızca bir işlemi barındırması gerekir.
ms.date: 08/06/2020
ms.openlocfilehash: 7dcf4b4af3385a2a500c5bc16a889b56fa2c25d5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916010"
---
# <a name="common-container-design-principles"></a>Ortak kapsayıcı tasarım ilkeleri

Geliştirme işlemine başlarken, kapsayıcıları nasıl kullanacağınızı gösteren birkaç temel kavram vardır.

## <a name="container-equals-a-process"></a>Kapsayıcı bir işleme eşit

Kapsayıcı modelinde bir kapsayıcı tek bir işlemi temsil eder. Bir kapsayıcıyı işlem sınırı olarak tanımlayarak, ölçeklendirmek veya toplu işlemleri yapmak için kullanılan temel türleri oluşturmaya başlayabilirsiniz. Bir Docker kapsayıcısını çalıştırdığınızda bir [giriş noktası](https://docs.docker.com/engine/reference/builder/#entrypoint) tanımı görürsünüz. Bu işlem ve kapsayıcının ömrünü tanımlar. İşlem tamamlandığında kapsayıcı yaşam döngüsü sona erer. Web sunucuları gibi uzun süre çalışan işlemler ve toplu işler gibi kısa süreli işlemler, Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/)olarak uygulanmış olabilir. İşlem başarısız olursa, kapsayıcı sonlanır ve Orchestrator üzerinde sürer. Orchestrator 'da beş örnek tutulması ve biri başarısız olursa, Orchestrator başarısız işlemi değiştirmek için başka bir kapsayıcı oluşturur. Batch işinde, işlem parametrelerle başlatılır. İşlem tamamlandığında, çalışma tamamlanmıştır.

Tek bir kapsayıcıda birden çok işlemi çalıştırmak istediğiniz bir senaryo bulabilirsiniz. Herhangi bir mimari belgesinde hiçbir zaman "hiç" değil, her zaman "Always" yoktur. Birden çok işlem gerektiren senaryolar için ortak bir model, [Gözetmen](http://supervisord.org/)kullanmaktır.

>[!div class="step-by-step"]
>[Önceki](design-docker-applications.md) 
> [Sonraki](monolithic-applications.md)
