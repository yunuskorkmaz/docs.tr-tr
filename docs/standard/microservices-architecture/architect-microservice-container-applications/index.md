---
title: Kapsayıcı ve mikro hizmet mimarisi oluşturma tabanlı uygulamaları
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Kapsayıcı ve mikro hizmet mimarisi oluşturma tabanlı uygulamaları
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 185279cb4df70d9896d7e11c995170e7cd214f73
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106820"
---
# <a name="architecting-container--and-microservice-based-applications"></a>Kapsayıcı ve mikro hizmet tabanlı uygulamaları mimarisi oluşturma

*Mikro harika avantajları sunar ancak ayrıca büyük yeni zorluklar Yükselt. Mikro hizmet mimarisi desenleri temel ayaklar mikro hizmet tabanlı bir uygulama oluştururken alır.*

Bu kılavuzda daha önce kapsayıcıları ve Docker hakkında temel kavramları hakkında bilgi edindiniz. İle kapsayıcıları başlamak için gereken en düşük bilgisini yükleyemedi. Bu mimari bölümdeki kavramları kapsayıcıları etkinleştiricilerden ve mikro hizmetler için harika bir sığdırma olsa bile, mikro hizmet mimarisi ve çoğu mimari için zorunlu olmasa da, kapsayıcıları çok uygulanabilir. Ancak, bu kılavuz hem kapsayıcıları zaten sunulan önemini nedeniyle kesişimi odaklanır.

Kuruluş uygulamaları karmaşık olabilir ve genellikle tek bir hizmet tabanlı uygulama yerine birden çok hizmetlerin oluşurlar. Bu durumlarda, mikro ve belirli Domain-Driven tasarım (DDD) desenleri ve kapsayıcı orchestration kavramları gibi ek mimari yaklaşımlar anlamanız gerekir. Bu bölüm yalnızca mikro kapsayıcıları, ancak hiçbir kapsayıcılı uygulaması da açıklanır unutmayın.

## <a name="container-design-principles"></a>Kapsayıcı tasarım ilkeleri

Kapsayıcı modelinde, tek bir işlem bir kapsayıcı görüntü örneğini temsil eder. İşlem sınır olarak bir kapsayıcı görüntüsü tanımlayarak, işlem ölçeklendirmek için veya onu toplu kullanılabilir temelleri oluşturabilirsiniz.

Bir kapsayıcı görüntüsü tasarlarken, göreceğiniz bir [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/) Dockerfile tanımında. Bu, kapsayıcı ömrü, yaşam süresi denetimleri işlemi tanımlar. İşlem tamamlandığında, kapsayıcı ömrü sona erer. Kapsayıcıları uzun süre çalışan işlemleri web sunucuları gibi temsil, ancak temsil kısa süreli işlemleri daha önce Azure uygulanmıştır toplu işleri de ister [WebJobs](https://docs.microsoft.com/azure/app-service-web/websites-webjobs-resources).

İşlem başarısız olur, kapsayıcı sona erer ve orchestrator devreye girer durumunda. Orchestrator beş örnek çalışıyor tutmak için yapılandırılmış ve biri başarısız olursa, orchestrator başarısız işlem değiştirmek için başka bir kapsayıcı örneği oluşturur. Bir toplu işlemde parametrelerle işlemi başlatıldı. İşlem tamamlandığında, iş tamamlanır. Bu kılavuz ayrıntısına gitme orchestrators üzerinde daha sonra.

Tek bir kapsayıcıda çalışan birden çok işlemler istediğiniz bir senaryo bulabilirsiniz. Bu senaryo için olabilir beri kapsayıcı başına yalnızca bir giriş noktası gerektiğinde sayıda programları başlatır kapsayıcı içindeki bir betik çalıştırabilir. Örneğin, kullanabileceğiniz [Supervisor](http://supervisord.org/) veya birden çok işlem tek bir kapsayıcısı içinde başlatma halletmeniz için benzer bir aracı. Kapsayıcı başına birden çok işlem tutun mimarileri bulabilirsiniz olsa bile, ancak, bu yaklaşım, yaygın değildir.


>[!div class="step-by-step"]
[Önceki](../net-core-net-framework-containers/official-net-docker-images.md)
[sonraki](containerize-monolithic-applications.md)
