---
title: Kısmi hata işleme
description: Kısmi hataları niçin incelikle işleyeceğinizi öğrenin. Bir microservice tam olarak işlevsel olmayabilir ama yine de bazı yararlı işler yapmak mümkün olabilir.
ms.date: 10/16/2018
ms.openlocfilehash: f00e5349df74b543deb6ac941c751cb130b3837c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73732973"
---
# <a name="handle-partial-failure"></a>Kısmi hata işleme

Mikro hizmetler tabanlı uygulamalar gibi dağıtılmış sistemlerde, kısmi arıza riski her zaman vardır. Örneğin, tek bir microservice/container başarısız olabilir veya kısa bir süre için yanıt vermek için kullanılabilir olmayabilir veya tek bir VM veya sunucu çökebilir. İstemciler ve hizmetler ayrı işlemler olduğundan, bir hizmet istemcinin isteğine zamanında yanıt veremeyebilir. Hizmet aşırı yüklenmiş ve isteklere çok yavaş yanıt verebilir veya ağ sorunları nedeniyle kısa bir süre için erişilemeyebilir.

Örneğin, eShopOnContainers örnek uygulamasından Sipariş ayrıntıları sayfasını göz önünde bulundurun. Kullanıcı bir sipariş göndermeye çalıştığında sipariş mikrohizmeti yanıt vermiyorsa, istemci işleminin kötü bir uygulaması (MVC web uygulaması)—örneğin, istemci kodu zaman olmadan eşzamanlı RPC'ler kullanıyorsa— iş parçacıklarını süresiz olarak engeller bir yanıt bekliyor. Kötü bir kullanıcı deneyimi oluşturmanın yanı sıra, yanıt vermeyen her bekleme bir iş parçacığı tüketir veya engeller ve iş parçacıkları yüksek ölçeklenebilir uygulamalarda son derece değerlidir. Engellenen çok sayıda iş parçacığı varsa, sonunda uygulamanın çalışma zamanı iş parçacıkları tükenebilir. Bu durumda, uygulama Şekil 8-1'de gösterildiği gibi kısmen yanıt vermemek yerine genel olarak yanıt sızabilir.

![Kısmi hataları gösteren diyagram.](./media/handle-partial-failure/partial-failures-diagram.png)

**Şekil 8-1**. Hizmet iş parçacığı kullanılabilirliğini etkileyen bağımlılıklar nedeniyle kısmi hatalar

Büyük bir mikrohizmet tabanlı uygulamada, herhangi bir kısmi hata, özellikle dahili microservices etkileşimin çoğu senkron HTTP çağrıları (bir anti-desen olarak kabul edilir) dayanmaktadır yükseltilebilir. Günde milyonlarca gelen çağrı alan bir sistem düşünün. Sisteminizin uzun eşzamanlı HTTP çağrıları zincirlerine dayanan kötü bir tasarımı varsa, bu gelen aramalar milyonlarca giden çağrıya (1:4'lük bir oranın 1:4 oranında olduğunu varsayalım) ve eşzamanlı bağımlılıklar olarak düzinelerce dahili mikro hizmete neden olabilir. Bu durum Şekil 8-2'de, \#özellikle bağımlılık 3'te gösterilmiştir, bu zincir başlatılır ve bağımlılık #4. hangi aramalar #5.

![Birden çok dağıtılmış bağımlılıkları gösteren diyagram.](./media/handle-partial-failure/multiple-distributed-dependencies.png)

**Şekil 8-2**. UZUN HTTP istekleri zincirlerini içeren yanlış bir tasarıma sahip olmanın etkisi

Her bağımlılığın kendisi mükemmel kullanılabilirlik olsa bile, dağıtılmış ve bulut tabanlı bir sistemde aralıklı hata garanti edilir. Bu göz önünde bulundurman gereken bir gerçek.

Hata toleransı sağlamak için teknikler tasarlamaz ve uygulamazsanız, küçük arıza süreleri bile yükseltilebilir. Örnek olarak, kullanılabilirliğin %99,99'una sahip 50 bağımlılık, bu dalgalanma etkisi nedeniyle her ay birkaç saatlik kapalı kalma süresine neden olur. Bir mikrohizmet bağımlılığı, yüksek sayıda isteği işlerken başarısız olduğunda, bu hata her hizmetteki tüm kullanılabilir istek iş parçacığına hızla doyabilir ve tüm uygulamayı kilitleyebilir.

![Mikro hizmetlerde artırılmış kısmi arızayı gösteren diyagram.](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

**Şekil 8-3**. Senkron UZUN zincirleri ile mikrohizmetler tarafından güçlendirilmiş kısmi başarısızlık HTTP aramaları

Bu sorunu en aza indirmek için, bölümünde [Asynchronous microservice entegrasyonu microservice özerkliğini zorlamak](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy), bu kılavuz da dahili mikro hizmetler arasında asynchronous iletişim kullanmaya teşvik eder.

Buna ek olarak, mikro hizmetlerinizi ve istemci uygulamalarınızı kısmi hataları işlemek için tasarlamanız, yani esnek mikro hizmetler ve istemci uygulamaları oluşturmanız esastır.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](partial-failure-strategies.md)
