---
title: Akış Hizmetleri ile yinelenen alanlar-WCF geliştiricileri için gRPC
description: GRPC kullanarak veri koleksiyonlarını geçirme yöntemi olarak, yinelenen alanları akış Hizmetleri ile karşılaştırın.
ms.date: 09/02/2019
ms.openlocfilehash: 0e717df57ba2bb52d63a063072d8a45bf0f7e395
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503378"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>gRPC akış Hizmetleri ile yinelenen alanlar

gRPC Hizmetleri, veri kümelerini veya nesne listelerini döndürmenin iki yolunu sağlar. Protokol arabellekleri ileti belirtimi, başka bir iletideki ileti türlerini veya ileti dizilerini bildirmek için `repeated` anahtar sözcüğünü kullanır. GRPC hizmeti belirtimi, uzun süre çalışan kalıcı bir bağlantı bildirmek için `stream` anahtar sözcüğünü kullanır. Bu bağlantı üzerinde, birden çok ileti gönderilir ve tek tek işlenebilir. 

Ayrıca, bildirimler veya günlük iletileri gibi uzun süre çalışan zamana bağlı veriler için `stream` özelliğini de kullanabilirsiniz. Ancak bu bölüm, tek bir veri kümesi döndürmek için kullanımını göz önünde bulunduracaktır.

Kullanmanız gereken etkenlere bağlıdır, örneğin:

- Veri kümesinin genel boyutu.
- Veri kümesini istemci ya da sunucu ucunda oluşturmak için geçen süre.
- Veri kümesinin tüketicisinin, ilk öğe kullanılabilir duruma geldiğinde hemen üzerinde işlem yapıp başlatamayacağını veya her şeyi yararlı hale yapması için tüm veri kümesine ihtiyacı olup olmadığı.

## <a name="when-to-use-repeated-fields"></a>`repeated` alanları ne zaman kullanılır?

Boyut açısından kısıtlanmış olan ve kısa bir süre içinde tek bir şekilde oluşturulabilecek tüm veri kümeleri için — bir saniyenin altında, normal bir prototipleme iletisinde `repeated` alanı kullanmanız gerekir. Örneğin, bir e-ticaret sisteminde, bir sipariş içindeki öğelerin listesini oluşturmak büyük olasılıkla hızlıdır ve liste çok büyük olmaz. `repeated` alanla tek bir ileti döndürülmesi `stream` kullanmaktan daha hızlı bir sıralama düzeni ve daha az ağ yükü doğurur.

İstemciye, işleme başlamadan önce tüm veriler gerekiyorsa ve veri kümesi bellekte oluşturmaya yetecek kadar küçükse, bir `repeated` alanı kullanmayı göz önünde bulundurun. Sunucu üzerindeki bellekte veri kümesinin oluşturulması daha yavaş olsa bile bunu göz önünde bulundurun.

## <a name="when-to-use-stream-methods"></a>`stream` yöntemlerinin ne zaman kullanılacağı

Veri kümelerinizde bulunan ileti nesneleri çok büyükse, akış isteklerini veya yanıtlarını kullanarak bunları aktarmanız en iyisidir. Bellekte büyük bir nesne oluşturmak, ağa yazmak ve sonra kaynakları boşaltmak daha etkilidir. Bu yaklaşım, hizmetinizin ölçeklenebilirliğini geliştirir.

Benzer şekilde, bunları oluştururken belleğin tükenmesinden kaçınmak için, akış üzerinde kısıtlanmış olmayan boyut veri kümelerini göndermeniz gerekir.

Tüketicinin her bir öğeyi ayrı olarak işleyebildiği veri kümeleri için, ilerlemenin kullanıcıya belirtilebileceği anlamına gelir. Bir akışın kullanılması, bir uygulamanın yanıt hızını iyileştirebilir, ancak uygulamanın genel performansına karşı dengelenmesi gerekir.

Akışların yararlı olabilecek başka bir senaryo da birçok hizmet arasında bir iletinin işlendiği yerdir. Bir zincirdeki her hizmet bir akış döndürürse, Terminal Hizmeti (diğer bir deyişle, zincirdeki son) iletileri döndürmeye başlayabilir. Bu iletiler işlenebilir ve özgün istek sahibine zincirde geri geçirilebilir. İstek sahibi, bir akış döndürebilir ya da sonuçları tek bir yanıt iletisine toplayabilirler. Bu yaklaşım MapReduce gibi desenlerin kendisini geliştirir.

>[!div class="step-by-step"]
>[Önceki](migrate-duplex-services.md)
>[İleri](client-libraries.md)
