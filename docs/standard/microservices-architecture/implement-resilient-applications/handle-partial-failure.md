---
title: Kısmi hata işleme
description: Kısmi hataları işleyeceğinizi öğrenin. Bir mikro hizmet tam olarak işlevsel olmayabilir ancak yine de bazı faydalı bir iş yapmanız mümkün olabilir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 16b6237f79d6b4bc2bc9152ba6eb023ffbd3899f
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362710"
---
# <a name="handle-partial-failure"></a>Kısmi hata işleme

Mikro hizmet tabanlı uygulamalar gibi dağıtılmış sistemlerde ardı arkası bir kısmi hata riskini yoktur. Örneği için tek bir mikro hizmet/kapsayıcı başarısız olabilir veya yanıtlamak için kısa bir süre kullanılamıyor olabilir veya tek bir VM veya sunucusuna çökebilir. İstemcileri ve Hizmetleri ayrı işlemler olduğundan, hizmet istemci isteğini zamanında bir şekilde yanıt vermesi mümkün olmayabilir. Hizmet aşırı yüklenmiş ve yanıt verdiğinden çok yavaş için istekleri olabilir veya yalnızca ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir.

Örneğin, Sipariş Ayrıntıları sayfasından hizmetine örnek uygulamayı düşünün. Sıralama mikro hizmet yanıt vermiyorsa, kullanıcı çalışır (MVC web uygulaması) istemci işleminin hatalı bir uygulama bir sipariş göndermek — Örneğin, zaman uyumlu RPC hiçbir zaman aşımı ile kullanmak için istemci kodu oluşturduysanız — iş parçacıkları süresiz olarak engeller Yanıt bekleniyor. Olumsuz kullanıcı deneyiminden oluşturma, yanı sıra her yanıt bekleme kullanan veya bir iş parçacığını engeller ve iş parçacığı son derece yüksek oranda ölçeklenebilir uygulamalar değerlidir. Sonuçta pek çok engellenen iş parçacıkları varsa, uygulamanın çalışma zamanı iş parçacığı dışında çalıştırabilirsiniz. Bu durumda, uygulamanın genel yerine bırakabiliyor yalnızca kısmen yanıt Şekil 8-1'de gösterildiği gibi.

![Önceki paragrafta gösteren diyagram](./media/image1.png)

**Şekil 8-1**. Hizmet iş parçacığı kullanılabilirliğini etkileyebilecek bağımlılıklar nedeniyle kısmi hataları

Özellikle çoğu iç mikro hizmetler etkileşimi (Bu bir önleyici deseni olarak kabul edilir) zaman uyumlu HTTP çağrıları alıyorsa bir büyük mikro hizmet tabanlı uygulama içinde kısmi herhangi bir hata, yükseltilmiş. Gelen çağrılar her gün milyonlarca alan bir sistem hakkında düşünün. Zaman uyumlu HTTP çağrıları uzun zincirler dayalı olarak hatalı bir tasarım sisteminiz varsa bu gelen çağrıları giden aramaları (1:4 oranını varsayalım) zaman uyumlu bir bağımlılık olarak iç mikro hizmetler onlarca, pek çok daha fazla milyonlarca neden olabilir. Bu durum, Şekil 8-2'de, özellikle bağımlılık gösterilen \#3.

![Bağımlı diğer mikro hizmetler zincirine bağlı olduğu web uygulama mikro hizmet için hatalı bir tasarım](./media/image2.png)

**Şekil 8-2**. HTTP isteklerini uzun zincirleri özelliklerine sahip hatalı bir tasarım sahip olmanın etkisi

Her bağımlılık mükemmel kullanılabilirlik olsa bile, aralıklı olarak ortaya çıkan hata dağıtılmış ve bulut tabanlı bir sistemde garanti edilir. Bunu göz önünde bulundurmanız gereken bir gerçeğidir.

Daha küçük bir kapalı kalma süreleri, değil tasarlayıp teknikleri hataya dayanıklılık sağlamak için yükseltilmiş. Örneğin, 50 bağımlılıkları her olan % 99,99 oranında kullanılabilirlik birkaç saat kapalı kalma süresi içinde her ay nedeniyle bu dalgalanma etkisine neden olur. Yüksek hacimli istekleriniz işlerken bir mikro hizmet bağımlılık başarısız olduğunda, bu hata hızlı bir şekilde her hizmetin tüm kullanılabilir istek iş parçacıklarının saturate ve tüm uygulama kilitlenme.

![Kısmi hatalar zincirleme bağımlılıklardır ciddi bir şekilde yükseltilmiş](./media/image3.png)

**Şekil 8-3**. Kısmi hata uzun zincirleri zaman uyumlu HTTP çağrıları ile mikro hizmetler tarafından yükseltilmiş

Bölümünde, bu sorunu en aza indirmek için [zaman uyumsuz bir mikro hizmet tümleştirmesi zorunlu mikro hizmet'ın bağımsız çalışma sınırı](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy), bu kılavuzda dahili mikro hizmetler arasında zaman uyumsuz iletişim kullanmanızı önerir.

Ayrıca, temel kısmi hatalarını işlemek için mikro Hizmetleri ve istemci uygulamalarınızı tasarlama — diğer bir deyişle, esnek bir mikro hizmet ve istemci uygulamaları oluşturmak için.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](partial-failure-strategies.md)