---
title: Kısmi hata işleme
description: Kısmi hataların sorunsuz bir şekilde nasıl işleneceğini öğrenin. Mikro hizmet tamamen işlevsel olmayabilir, ancak yine de yararlı bir iş yapabiliyor olabilir.
ms.date: 10/16/2018
ms.openlocfilehash: 3345fffe3a38b8336d71ebb9c88e76d3315fd2e2
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738768"
---
# <a name="handle-partial-failure"></a>Tanıtıcı kısmen hatası

Mikro hizmet tabanlı uygulamalar gibi dağıtılmış sistemlerde, kısmi hata riski vardır. Örneğin, tek bir mikro hizmet/kapsayıcı başarısız olabilir veya kısa bir süre için yanıt veremeyebilir ya da tek bir VM veya sunucu kilitlenebilir. İstemciler ve hizmetler ayrı süreçler olduğundan, bir hizmet istemcinin isteğine zamanında yanıt veremeyebilir. Hizmet aşırı yüklenmiş ve isteklere çok yavaş yanıt veriyor olabilir veya ağ sorunları nedeniyle kısa bir süre boyunca yalnızca erişilebilir olmayabilir.

Örneğin, eShopOnContainers örnek uygulamasından Order details sayfasını göz önünde bulundurun. Kullanıcı bir siparişi göndermeyi denediğinde sıralama mikro hizmeti yanıt vermezse (örneğin, istemci kodu zaman aşımı olmadan zaman uyumlu RPC 'ler kullanıyorsa), yanıt için süresiz olarak yanıt bekleyen iş parçacıklarını engeller. Kötü bir kullanıcı deneyimi oluşturmanın yanı sıra, yanıt vermeyen her bekleme, bir iş parçacığını kullanır veya engeller ve iş parçacıkları son derece ölçeklenebilir uygulamalarda oldukça değerlidir. Engellenen çok sayıda iş parçacığı varsa, sonuçta uygulamanın çalışma zamanının iş parçacığı tükenmesine devam edebilir. Bu durumda, Şekil 8-1 ' de gösterildiği gibi uygulama yalnızca kısmen yanıt vermemeye karşı genel olarak yanıt vermeyebilir.

![Kısmi hataların gösterildiği diyagram.](./media/handle-partial-failure/partial-failures-diagram.png)

**Şekil 8-1**. Hizmet iş parçacığı kullanılabilirliğini etkileyen bağımlılıklardan dolayı kısmi arızalar

Büyük bir mikro hizmet tabanlı uygulamada, özellikle de iç mikro hizmet etkileşiminin büyük bir kısmı zaman uyumlu HTTP çağrılarını temel alıyorsa (bir anti-model olarak kabul edilir), kısmi bir hata oluşabilir. Gün başına milyonlarca gelen çağrı alan bir sistem hakkında düşünün. Sisteminizde zaman uyumlu HTTP çağrılarının uzun zincirlerini temel alan hatalı bir tasarım varsa, bu gelen çağrılar birçok milyonlarca giden çağrıya (1:4 oranını varsayalım) zaman uyumlu bağımlılıklar olarak onlarca iç mikro hizmet ile sonuçlanabilir. Bu durum Şekil 8-2, özellikle bağımlılık \# #4 çağıran ve sonra da #5 çağıran bağımlılık 3 ' te gösterilmiştir.

![Birden çok dağıtılmış bağımlılığı gösteren diyagram.](./media/handle-partial-failure/multiple-distributed-dependencies.png)

**Şekil 8-2**. Yanlış bir tasarıma sahip olmanın etkisi, HTTP isteklerinin uzun zincirlerine sahiptir

Her bağımlılığın mükemmel bir kullanılabilirliği olsa bile, dağıtılmış ve bulut tabanlı bir sistemde aralıklı hata garanti edilir. Göz önünde bulundurmanız gereken bir olgu vardır.

Hata toleransını güvence altına almak için tasarlayamazsınız ve daha küçük bir küçüklükte olabilir. Örnek olarak, her biri kullanılabilirliği% 99,99 olan 50 bağımlılık, bu Ripple etkisi nedeniyle her ay birkaç saatlik kapalı kalma süresine neden olur. Yüksek bir istek hacmi işlenirken bir mikro hizmet bağımlılığı başarısız olduğunda, bu hata her bir hizmette bulunan tüm kullanılabilir istek iş parçacıklarını hızla doygunluğu ve tüm uygulamayı kilitlebilirler.

![Mikro hizmetlerde oluşan kısmen hatalı hata gösteren diyagram.](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

**Şekil 8-3**. Zaman uyumlu HTTP çağrılarının uzun zincirleriyle mikro hizmetlerden oluşan kısmi hata

Bu sorunu en aza indirmek için, [zaman uyumsuz mikro hizmet tümleştirmesi mikro hizmetin bağımsız çalışma sınırı 'i zorlayacağı](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy)için bu kılavuz, iç mikro hizmetlerde zaman uyumsuz iletişim kullanmanızı önerir.

Ayrıca, mikro hizmetlerinizi ve istemci uygulamalarınızı kısmi hataların (yani dayanıklı mikro hizmetler ve istemci uygulamaları oluşturmak için) tasarlamanızı da öneririz.

>[!div class="step-by-step"]
>[Önceki](index.md) 
> [Sonraki](partial-failure-strategies.md)
