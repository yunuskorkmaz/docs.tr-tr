---
title: Konteyner ve mikrohizmet tabanlı uygulamaların mimarlanması
description: Konteyner ve mikro hizmet tabanlı uygulamaların mimaredilmesi küçük bir başarı değildir ve hafife alınmamalıdır. Bu bölümdeki temel kavramları öğrenin.
ms.date: 09/20/2018
ms.openlocfilehash: aff30c907f1140b94dbcae330ed7cb633b0a744b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70295520"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Konteyner ve mikrohizmet tabanlı uygulamaların mimarlanması

*Microservices büyük faydalar sunmak la birlikte, aynı zamanda büyük yeni zorluklar alametidir. Microservice mimari desenleri, microservice tabanlı bir uygulama oluştururken temel sütunlardır.*

Daha önce bu kılavuzda, konteynerler ve Docker hakkında temel kavramları öğrendim. Konteynerlerle başlamak için gereken minimum bilgi buydu. Konteynerler etkinleştirici ve mikro hizmetler için mükemmel bir uyum olsa bile, bir mikrohizmet mimarisi için zorunlu değildir ve bu mimari bölümündebirçok mimari kavramlar da kapsayıcıolmadan uygulanabilir. Ancak, bu kılavuz zaten kapların tanıtılan önemi nedeniyle her ikisinin de kesiştiği üzerinde duruluyor.

Kurumsal uygulamalar karmaşık olabilir ve genellikle tek bir hizmet tabanlı uygulama yerine birden çok hizmetten oluşur. Bu gibi durumlarda, mikro hizmetler ve belirli Etki Alanı Odaklı Tasarım (DDD) desenleri ve konteyner orkestrasyon kavramları gibi ek mimari yaklaşımları anlamanız gerekir. Bu bölümde sadece kapsayıcılarda mikro hizmetler değil, konteyner uygulamaları da açıklanmaktadır.

## <a name="container-design-principles"></a>Konteyner tasarım ilkeleri

Kapsayıcı modelinde, kapsayıcı görüntü örneği tek bir işlemi temsil eder. Kapsayıcı görüntüsünü bir işlem sınırı olarak tanımlayarak, işlemi ölçeklendirmek veya toplu iş yapmak için kullanılabilecek ilkel bilgiler oluşturabilirsiniz.

Bir kapsayıcı görüntüsü tasarlarken, Dockerfile'da bir [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) tanımı görürsünüz. Bu, kullanım ömrü kapsayıcının ömrünü kontrol eden işlemi tanımlar. İşlem tamamlandığında, kapsayıcı yaşam döngüsü sona erer. Kapsayıcılar web sunucuları gibi uzun süren işlemleri temsil edebilir, ancak daha önce Azure [Web İşleri](https://github.com/Azure/azure-webjobs-sdk/wiki)olarak uygulanmış olabilecek toplu iş işleri gibi kısa ömürlü işlemleri de temsil edebilir.

İşlem başarısız olursa, kapsayıcı sona erer ve orkestratör devralır. Orkestratör beş örneği çalışır durumda tutacak şekilde yapılandırılırsa ve biri başarısız olursa, orkestratör başarısız olan işlemi değiştirmek için başka bir kapsayıcı örneği oluşturur. Toplu iş işinde, işlem parametrelerle başlatılır. İşlem tamamlandığında, çalışma tamamlanır. Bu kılavuz, daha sonra orkestratörleri deşer.

Tek bir kapsayıcıda birden çok işlem çalışmasını istediğiniz bir senaryo bulabilirsiniz. Bu senaryo için, kapsayıcı başına yalnızca bir giriş noktası olabileceğinden, gerektiğinde çok sayıda program başlatan kapsayıcıiçinde bir komut dosyası çalıştırabilirsiniz. Örneğin, tek bir kapsayıcı içinde birden çok işlemi başlatmayı halletmek için [Supervisor](http://supervisord.org/) veya benzer bir aracı kullanabilirsiniz. Ancak, kapsayıcı başına birden çok işlem tutan mimariler bulsanız bile, bu yaklaşım çok yaygın değildir.

>[!div class="step-by-step"]
>[Önceki](../net-core-net-framework-containers/official-net-docker-images.md)
>[Sonraki](containerize-monolithic-applications.md)
