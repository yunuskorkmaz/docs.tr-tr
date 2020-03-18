---
title: Akış hizmetleri ve tekrarlanan alanlar - WCF geliştiricileri için gRPC
description: Yinelenen alanları, gRPC kullanarak veri koleksiyonlarını geçirme yolları olarak akış hizmetleriyle karşılaştırın.
ms.date: 09/02/2019
ms.openlocfilehash: 542ebc393f9c9c1ad717d02d01fab33d85c18917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147756"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>gRPC akış hizmetleri ile yinelenen alanlar karşılaştırması

gRPC hizmetleri, veri kümelerini veya nesne listelerini döndürmenin iki yolunu sağlar. Protokol Arabellekleri ileti `repeated` belirtimi, başka bir iletiiçinde liste veya ileti dizilerini bildirmek için anahtar sözcüğü kullanır. gRPC hizmet belirtimi, uzun süredir devam eden kalıcı bağlantıyı bildirmek için `stream` anahtar sözcüğü kullanır. Bu bağlantı üzerinden, birden çok ileti gönderilir ve tek tek işlenebilir.

Bu `stream` özelliği, bildirimler veya günlük iletileri gibi uzun süreli zamansal veriler için de kullanabilirsiniz. Ancak bu bölüm, tek bir veri kümesini döndürmek için kullanımını dikkate alacaktır.

Kullanmanız gereken ler aşağıdaki gibi etkenlere bağlıdır:

- Veri kümesinin genel boyutu.
- İstemci veya sunucu sonunda veri kümesi oluşturmak için gereken süre.
- Veri kümesinin tüketicisi ilk öğe kullanılabilir olur olmaz harekete geçer başlamalı veya yararlı bir şey yapmak için tam veri kümesine ihtiyaç dolup taşabilir.

## <a name="when-to-use-repeated-fields"></a>Alanların ne `repeated` zaman kullanılacağı

Boyutu kısıtlı olan ve kısa bir süre içinde bütünüyle oluşturulabilen herhangi bir veri kümesi için-örneğin, `repeated` bir saniyenin altında- normal bir Protobuf iletisinde bir alan kullanmanız gerekir. Örneğin, bir e-ticaret sisteminde, bir sipariş içindeki öğelerin listesini oluşturmak büyük olasılıkla hızlıdır ve liste çok büyük olmayacaktır. Bir alanla tek `repeated` bir iletiyi döndürme, `stream` kullanmaktan daha hızlı bir büyüklük sırasıdır ve daha az ağ yüküne neden olur.

İstemci işlemeye başlamadan önce tüm verilere ihtiyaç duyarsa ve veri kümesi bellekte oluşturmak için yeterince küçükse, bir `repeated` alan kullanmayı düşünün. Sunucudaki bellekte veri kümesinin oluşturulması daha yavaş olsa bile bunu göz önünde bulundurun.

## <a name="when-to-use-stream-methods"></a>Yöntemler ne `stream` zaman kullanılır?

Veri kümelerinizdeki ileti nesneleri büyük ölçüde çok büyükse, akış isteklerini veya yanıtlarını kullanarak bunları aktarabilirsiniz. Bellekte büyük bir nesne oluşturmak, ağa yazmak ve kaynakları boşaltmak daha verimlidir. Bu yaklaşım, hizmetinölçeklenebilirliğini artırır.

Benzer şekilde, bunları yaparken bellek tükenen önlemek için akışları üzerinde sınırlandırılmamış boyutta veri kümeleri göndermelisiniz.

Tüketicinin her öğeyi ayrı ayrı işleyebilir veri kümeleri için, ilerlemenin kullanıcıya gösterilebildiği anlamına geliyorsa bir akış kullanmayı düşünmelisiniz. Akış kullanmak bir uygulamanın yanıt verme yeteneğini artırabilir, ancak bunu uygulamanın genel performansına göre dengelemeniz gerekir.

Akışların yararlı olabileceği başka bir senaryo da, iletinin birden çok hizmet arasında işlendiği yerdir. Zincirdeki her hizmet bir akışı döndürürse, terminal hizmeti (diğer bir deyişle, zincirdeki son hizmet) iletileri döndürmeye başlayabilir. Bu iletiler işlenebilir ve zincir boyunca orijinal istekte bulunup aktarılabilir. İstekçi bir akışı döndürebilir veya sonuçları tek bir yanıt iletisine toplayabilir. Bu yaklaşım, MapReduce gibi desenlere iyi bir şekilde katkıda bulunmaktadır.

>[!div class="step-by-step"]
>[Önceki](migrate-duplex-services.md)
>[Sonraki](client-libraries.md)
