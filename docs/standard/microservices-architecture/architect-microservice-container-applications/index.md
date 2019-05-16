---
title: Kapsayıcı ve mikro hizmet tabanlı uygulama mimarileri oluşturma
description: Kapsayıcı ve mikro hizmet tabanlı uygulamalar tasarlamak, hiçbir küçük bir başarıdır ve hafifçe alınması gerekir. Bu bölümde temel kavramları öğrenin.
ms.date: 09/20/2018
ms.openlocfilehash: aff30c907f1140b94dbcae330ed7cb633b0a744b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644147"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Kapsayıcı ve mikro hizmet tabanlı uygulama mimarileri oluşturma

*Mikro hizmetler, harika avantajlar sağlar ancak büyük yeni zorluklar da Yükselt. Mikro hizmet mimarisi desenleri, mikro hizmet tabanlı bir uygulama oluştururken, temel yapı taşları alır.*

Bu kılavuzda daha önce kapsayıcıları ve Docker hakkında temel kavramları öğrendiniz. Bu, kapsayıcılar ile kullanmaya başlamak gerekli en düşük bilgisini yükleyemedi. Bu mimari bölümdeki kavramları kapsayıcıları etkinleştiricilerden ve mikro hizmet için harika bir uygun olduğunda bile, bunlar bir mikro hizmet mimarisi ve birçok mimari için zorunlu olmasa da, kapsayıcıları çok uygulanabilir. Ancak, bu kılavuz hem kapsayıcıları zaten sunulan önemini nedeniyle kesişimi odaklanır.

Kurumsal uygulamalar genellikle birden çok hizmet yerine tek bir hizmet tabanlı uygulama, oluşan ve karmaşık olabilir. Bu gibi durumlarda, mikro hizmetler ve belirli etki alanı Odaklı Tasarım (DDD) desenleri ve kapsayıcı düzenleme kavramlarını gibi ek mimari yaklaşımlar anlamanız gerekir. Bu bölümde, kapsayıcılar, ancak her kapsayıcılı uygulamayı de yalnızca değil mikro hizmetler açıklanmaktadır unutmayın.

## <a name="container-design-principles"></a>Kapsayıcı tasarım ilkeleri

Kapsayıcı modelinde, bir kapsayıcı görüntü örneğinin tek bir işlem temsil eder. Bir kapsayıcı görüntüsü işlem sınır olarak tanımlayarak işlemin ölçeklendirmek için veya bu toplu iş için kullanılabilir temelleri oluşturabilirsiniz.

Bir kapsayıcı görüntüsü tasarlarken, gördüğünüz bir [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) Dockerfile içinde tanımı. Bu, kapsayıcıyı ömrünü ömürlerinin denetimleri işlem tanımlar. İşlem tamamlandığında, kapsayıcı ömrü sona erer. Kapsayıcılar web sunucuları gibi uzun süre çalışan işlemler temsil, ancak eski adıyla Azure uygulanmıştır toplu temsil kısa süreli işlemler de ister [WebJobs](https://github.com/Azure/azure-webjobs-sdk/wiki).

İşlem başarısız olursa, kapsayıcı sona erer ve orchestrator sürüyorsa. Orchestrator çalışan beş örneklerinin tutmak için yapılandırılmış ve biri başarısız olursa, orchestrator başarısız işlemi değiştirmek için başka bir kapsayıcı örneği oluşturur. Bir batch işinde parametrelerle işlemi başlatıldı. İşlem tamamlandığında, iş tamamlandığında. Bu kılavuz ayrıntısına gitme düzenleyicileri üzerinde daha sonra.

Birden çok işlem tek bir kapsayıcıda çalıştırmak istediğiniz bir senaryo bulabilirsiniz. Bu senaryo için kapsayıcı başına yalnızca bir giriş noktası olabileceği gerektiği gibi çok programları başlatır kapsayıcıdaki bir betik çalıştırabilir. Örneğin, kullanabileceğiniz [gözetmen](http://supervisord.org/) veya birden çok işlem tek bir kapsayıcı içinde başlatılmasını halletmeniz için benzer bir araç. Ancak, tutan kapsayıcı başına birden çok işlem mimarileri bulabilirsiniz olsa da, bu yaklaşım çok yaygın değildir.

>[!div class="step-by-step"]
>[Önceki](../net-core-net-framework-containers/official-net-docker-images.md)
>[İleri](containerize-monolithic-applications.md)
