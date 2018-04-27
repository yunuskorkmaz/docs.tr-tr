---
title: Ortak kapsayıcı tasarım ilkeleri
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6a289cdafc88abe8629638a84eff184829362e16
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="common-container-design-principles"></a>Ortak kapsayıcı tasarım ilkeleri

Şimdi geliştirme işlemine alma kapsayıcıları kullanma açısından söz değerinde birkaç temel kavram vardır.

## <a name="container-equals-a-process"></a>Kapsayıcı bir işlem eşittir

Kapsayıcı modelinde, tek bir işlem bir kapsayıcıyı temsil eder. İşlem sınır olarak bir kapsayıcı tanımlayarak, Ölçek veya toplu kapalı, işlemleri için kullanılan temelleri oluşturmak başlayın. Docker kapsayıcısı çalıştırdığınızda göreceğiniz bir [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) tanımı. Bu işlem ve kapsayıcı ömrü tanımlar. İşlem tamamlandığında, kapsayıcı ömrü sona erer. Web sunucuları ve Microsoft Azure uygulanmamış toplu işler gibi kısa süreli bir işlem gibi uzun süre çalışan işlemlerin [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/). İşlem başarısız olur, kapsayıcı sona erer ve orchestrator devreye girer durumunda. Orchestrator beş örnek çalışıyor tutmak için istendi ve biri başarısız olursa, orchestrator başarısız işlem değiştirmek için başka bir kapsayıcı oluşturun. Bir toplu işlemde parametrelerle işlemi başlatıldı. İşlem tamamlandığında, iş tamamlanır.

Tek bir kapsayıcıda çalışan birden çok işlemler istediğiniz bir senaryo bulabilirsiniz. Herhangi bir mimari belgesinde hiçbir zaman bir "hiçbir değildir," ya da her zaman olduğu bir "her zaman." Birden çok işlem gerektiren senaryolar için genel bir desen kullanmaktır [Supervisor](http://supervisord.org/).


>[!div class="step-by-step"]
[Önceki] (Tasarım-docker-applications.md) [sonraki] (applications.md tek yapılı)
