---
title: Kapsayıcı ve mikro hizmet tabanlı uygulamaları tasarlama
description: Kapsayıcı ve mikro hizmet tabanlı uygulamaların mimarisi, küçük bir Fede değildir ve çok daha fazla alınmamalıdır. Bu bölümdeki temel kavramları öğrenin.
ms.date: 01/13/2021
ms.openlocfilehash: d87633b6c5073a9098c34c1192bcca1abad00e5c
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189492"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Kapsayıcı ve mikro hizmet tabanlı uygulamaları tasarlama

*Mikro hizmetler harika avantajlar sunar, ancak büyük ölçüde yeni zorluk da sunar. Mikro hizmet mimarisi desenleri, mikro hizmet tabanlı bir uygulama oluştururken temel değerler oluşturur.*

Bu kılavuzda daha önce kapsayıcılar ve Docker hakkında temel kavramları öğrendiniz. Bu bilgiler, kapsayıcıları kullanmaya başlamak için gereken en düşük gereksinimdir. Kapsayıcılar, mikro hizmetler için bir mikro hizmet mimarisi ve harika bir uyum olsa da, mikro hizmet mimarisi için zorunlu değildir ve bu mimari bölümünde birçok mimari kavram da kapsayıcı olmadan uygulanabilir. Ancak, bu kılavuz, kapsayıcıların zaten tanıtılmasından kaynaklanan her ikisinin de kesişimine odaklanır.

Kurumsal uygulamalar karmaşık olabilir ve genellikle tek hizmet tabanlı bir uygulama yerine birden çok hizmetten oluşur. Bu gibi durumlarda, mikro hizmetler ve belirli Domain-Driven tasarımı (DDD) desenlerinin yanı sıra kapsayıcı düzenleme kavramları gibi diğer mimari yaklaşımları anlamanız gerekir. Bu bölümde, kapsayıcılar üzerinde yalnızca mikro hizmetler değil, Kapsayıcılı herhangi bir uygulama de açıklanmaktadır.

## <a name="container-design-principles"></a>Kapsayıcı tasarım ilkeleri

Kapsayıcı modelinde bir kapsayıcı görüntüsü örneği tek bir işlemi temsil eder. Bir kapsayıcı görüntüsünü işlem sınırı olarak tanımlayarak, işlemi ölçeklendirmek veya toplu işlem yapmak için kullanılabilen temel öğeler oluşturabilirsiniz.

Bir kapsayıcı görüntüsü tasarladığınızda Dockerfile dosyasında bir [giriş noktası](https://docs.docker.com/engine/reference/builder/#entrypoint) tanımı görürsünüz. Bu tanım, ömrü kapsayıcının ömrünü denetleyen işlemi tanımlar. İşlem tamamlandığında kapsayıcı yaşam döngüsü sona erer. Kapsayıcılar Web sunucuları gibi uzun süreli işlemleri temsil edebilir, ancak daha önce Azure [WebJobs](https://github.com/Azure/azure-webjobs-sdk/wiki)olarak uygulanan toplu işler gibi kısa süreli işlemleri de temsil edebilir.

İşlem başarısız olursa, kapsayıcı sonlanır ve Orchestrator üzerinde sürer. Orchestrator beş örneği çalışır durumda tutmak üzere yapılandırıldıysa ve bir hata başarısız olursa, Orchestrator başarısız işlemi değiştirmek için başka bir kapsayıcı örneği oluşturacaktır. Batch işinde, işlem parametrelerle başlatılır. İşlem tamamlandığında, çalışma tamamlanmıştır. Bu kılavuz, daha sonra, bu kılavuzda daha sonra detaya gider.

Tek bir kapsayıcıda birden çok işlemin çalışmasını istediğiniz bir senaryo bulabilirsiniz. Bu senaryo için, kapsayıcı başına yalnızca bir giriş noktası olduğundan, kapsayıcıda gereken sayıda programı başlatan bir betiği çalıştırabilirsiniz. Örneğin, tek bir kapsayıcı içinde birden çok işlem başlatmaya dikkat çekmek için [Gözetmen](http://supervisord.org/) veya benzer bir araç kullanabilirsiniz. Ancak, kapsayıcı başına birden çok işlem tutan mimariler bulabilse de, bu yaklaşım çok yaygın değildir.

>[!div class="step-by-step"]
>[Önceki](../net-core-net-framework-containers/official-net-docker-images.md) 
> [Sonraki](containerize-monolithic-applications.md)
