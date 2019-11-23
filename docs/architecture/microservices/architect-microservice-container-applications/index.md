---
title: Kapsayıcı ve mikro hizmet tabanlı uygulamaları tasarlama
description: Kapsayıcı ve mikro hizmet tabanlı uygulamaların mimarisi, küçük bir Fede değildir ve çok daha fazla alınmamalıdır. Bu bölümdeki temel kavramları öğrenin.
ms.date: 09/20/2018
ms.openlocfilehash: aff30c907f1140b94dbcae330ed7cb633b0a744b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295520"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Kapsayıcı ve mikro hizmet tabanlı uygulamaları tasarlama

*Mikro hizmetler harika avantajlar sunar, ancak büyük ölçüde yeni zorluk da sunar. Mikro hizmet mimarisi desenleri, mikro hizmet tabanlı bir uygulama oluştururken temel değerler oluşturur.*

Bu kılavuzda daha önce kapsayıcılar ve Docker hakkında temel kavramları öğrendiniz. Bu, kapsayıcıları kullanmaya başlamak için gereken en az bilgi. Kapsayıcılar, kapsayıcılar, mikro hizmetler için çok büyük olsa da, mikro hizmet mimarisi için zorunlu değildir ve bu mimari bölümünde çok sayıda mimari kavram, kapsayıcılar olmadan da uygulanabilir. Ancak, bu kılavuz, kapsayıcıların zaten tanıtılmasından kaynaklanan her ikisinin de kesişimine odaklanır.

Kurumsal uygulamalar karmaşık olabilir ve genellikle tek hizmet tabanlı bir uygulama yerine birden çok hizmetten oluşur. Bu gibi durumlarda, mikro hizmetler ve bazı etki alanı odaklı tasarım (DDD) desenleri ve kapsayıcı düzenleme kavramları gibi ek mimari yaklaşımları anlamanız gerekir. Bu bölümde, kapsayıcılar üzerinde yalnızca mikro hizmetler değil, Kapsayıcılı herhangi bir uygulama de açıklanmaktadır.

## <a name="container-design-principles"></a>Kapsayıcı tasarım ilkeleri

Kapsayıcı modelinde bir kapsayıcı görüntüsü örneği tek bir işlemi temsil eder. Bir kapsayıcı görüntüsünü işlem sınırı olarak tanımlayarak, işlemi ölçeklendirmek veya toplu işlem yapmak için kullanılabilen temel öğeler oluşturabilirsiniz.

Bir kapsayıcı görüntüsü tasarladığınızda Dockerfile dosyasında bir [giriş noktası](https://docs.docker.com/engine/reference/builder/#entrypoint) tanımı görürsünüz. Bu işlem ömrü kapsayıcının ömrünü denetleyen işlemi tanımlar. İşlem tamamlandığında kapsayıcı yaşam döngüsü sona erer. Kapsayıcılar Web sunucuları gibi uzun süreli işlemleri temsil edebilir, ancak daha önce Azure [WebJobs](https://github.com/Azure/azure-webjobs-sdk/wiki)olarak uygulanan toplu işler gibi kısa süreli işlemleri de temsil edebilir.

İşlem başarısız olursa, kapsayıcı sonlanır ve Orchestrator üzerinde sürer. Orchestrator beş örneği çalışır durumda tutmak üzere yapılandırıldıysa ve bir hata başarısız olursa, Orchestrator başarısız işlemi değiştirmek için başka bir kapsayıcı örneği oluşturacaktır. Batch işinde, işlem parametrelerle başlatılır. İşlem tamamlandığında, çalışma tamamlanmıştır. Bu kılavuz, daha sonra, bu kılavuzda daha sonra detaya gider.

Tek bir kapsayıcıda birden çok işlemin çalışmasını istediğiniz bir senaryo bulabilirsiniz. Bu senaryo için, kapsayıcı başına yalnızca bir giriş noktası olduğundan, kapsayıcıda gereken sayıda programı başlatan bir betiği çalıştırabilirsiniz. Örneğin, tek bir kapsayıcı içinde birden çok işlem başlatmaya dikkat çekmek için [Gözetmen](http://supervisord.org/) veya benzer bir araç kullanabilirsiniz. Ancak, kapsayıcı başına birden çok işlem tutan mimariler bulabilse de, bu yaklaşım çok yaygın değildir.

>[!div class="step-by-step"]
>[Önceki](../net-core-net-framework-containers/official-net-docker-images.md)
>[İleri](containerize-monolithic-applications.md)
