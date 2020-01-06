---
title: Akış Hizmetleri ile yinelenen alanlar-WCF geliştiricileri için gRPC
description: GRPC ile veri koleksiyonlarını geçirme yöntemi olarak yinelenen alanları akış Hizmetleri ile karşılaştırın.
ms.date: 09/02/2019
ms.openlocfilehash: 46586ab08df6b136cdafb990ce8be75435a6bf6c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337863"
---
# <a name="grpc-streaming-services-versus-repeated-fields"></a>gRPC akış Hizmetleri ve yinelenen alanlara karşı

gRPC Hizmetleri, veri kümelerini veya nesne listelerini döndürmenin iki yolunu sağlar. Protokol arabellekleri ileti belirtimi, başka bir iletideki ileti türlerini veya ileti dizilerini bildirmek için `repeated` anahtar sözcüğünü kullanır. GRPC hizmeti belirtimi, birden fazla iletinin gönderildiği ve tek tek işlenebileceği uzun süre çalışan kalıcı bir bağlantı bildirmek için `stream` anahtar sözcüğünü kullanır. `stream` özelliği, bildirimler veya günlük iletileri gibi uzun süre çalışan zamana bağlı veriler için de kullanılabilir, ancak bu bölüm, tek bir veri kümesi döndürmek için kullanımını göz önünde bulunduracaktır.

Kullanmanız gereken, veri kümesinin genel boyutu, istemci veya sunucu ucunda veri kümesini oluşturmak için geçen süre ve veri kümesinin tüketicisi ilk öğe kullanılabilir duruma geldiğinde bu işlemi yapmaya başlayıp başlamadığı gibi çeşitli faktörlere bağlıdır. ya da tüm yararlı bir işlem yapmak için veri kümesinin tamamını gerektirir.

## <a name="when-to-use-repeated-fields"></a>`repeated` alanları ne zaman kullanılır?

Boyut açısından kısıtlanmış olan ve kısa bir süre içinde tek bir şekilde oluşturulabilecek tüm veri kümeleri için — bir saniyenin altında, normal bir prototipleme iletisinde `repeated` alanı kullanmanız gerekir. Örneğin, bir e-ticaret sisteminde, bir sipariş içindeki öğelerin listesini oluşturmak büyük olasılıkla hızlıdır ve liste çok büyük olmaz. `repeated` alanla tek bir ileti döndürülmesi, `stream` kullanmaktan daha hızlı bir sıralama düzeni ve daha az ağ yükü doğurur.

İstemci, işleme başlamadan önce tüm verilere ihtiyaç duyuyorsa ve veri kümesi bellekte oluşturmaya yetecek kadar küçükse, sunucudaki bellekte veri kümesinin gerçek oluşturma işlemi daha yavaş olsa bile bir `repeated` alanı kullanmayı düşünün.

## <a name="when-to-use-stream-methods"></a>`stream` yöntemlerinin ne zaman kullanılacağı

İleti nesnelerinin potansiyel olarak çok büyük olduğu veri kümeleri, akış istekleri veya yanıtları kullanılarak en iyi şekilde aktarılır. Bellekte büyük bir nesne oluşturmak, ağa yazmak ve sonra kaynakları boşaltmak daha etkilidir. Bu yaklaşım, hizmetinizin ölçeklenebilirliğini geliştirir.

Benzer şekilde, bu dosyaları oluştururken belleğin tükenmemesi için, kısıtlanmış olmayan boyutun veri kümelerinin akış üzerinden gönderilmesi gerekir.

Her bir öğenin tüketici tarafından ayrı olarak işlenebildiği veri kümelerinde, ilerlemenin son kullanıcıya belirtilebileceği anlamına gelir. Bu, uygulamanın genel performansına karşı dengelenmesi gerekse de bir uygulamanın görünen yanıt hızını iyileştirebilir.

Akışların yararlı olabilecek başka bir senaryo da birçok hizmet arasında bir iletinin işlendiği yerdir. Bir zincirdeki her bir hizmet bir akış döndürürse, Terminal Hizmeti (diğer bir deyişle, zincirdeki son), işlenen ve bir akış döndürebilen ya da bir akışa geri alınabilecek iletileri geri dönerek tek bir yanıt iletisine neden olur. Bu yaklaşım, eşleme/azaltma gibi desenlerin kendisini geliştirir.

>[!div class="step-by-step"]
>[Önceki](migrate-duplex-services.md)
>[İleri](client-libraries.md)
