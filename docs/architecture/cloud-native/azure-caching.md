---
title: Bulutta yerel bir uygulamada önbelleğe alma
description: Bulut Yerel uygulamasındaki önbelleğe alma stratejilerini öğrenin.
author: robvet
ms.date: 05/17/2020
ms.openlocfilehash: a33f143499b5f9545493bc4bc757cc3d152f7aa9
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557522"
---
# <a name="caching-in-a-cloud-native-app"></a>Bulutta yerel bir uygulamada önbelleğe alma

Önbelleğe almanın avantajları iyi anlaşılmıştır. Bu yöntem, sık erişilen verileri bir arka uç veri deposundan geçici olarak uygulamaya daha yakın olan *hızlı depolamaya* kopyalayarak işe yarar. Önbelleğe alma işlemi genellikle şu şekilde uygulanır...

- Veriler nispeten statik kalır.
- Veri erişimi, özellikle önbelleğin hızına kıyasla yavaş olur.
- Veriler yüksek çekişme düzeylerine tabidir.

## <a name="why"></a>Neden?

Önbelleğe alma, [Microsoft önbelleğe alma kılavuzunda](https://docs.microsoft.com/azure/architecture/best-practices/caching)anlatıldığı gibi tek tek mikro hizmetler ve sistem için performansı, ölçeklenebilirliği ve kullanılabilirliği bir bütün olarak artırabilir. Çok sayıda eşzamanlı isteği bir veri deposuna işlemenin gecikme süresini ve çekişmesini azaltır. Veri hacmi ve Kullanıcı sayısı arttıkça, önbelleğe almanın avantajları artar.

Bir istemci, sabit olan veya seyrek değişen verileri sürekli okuduğu zaman önbelleğe alma işlemi en etkilidir. Örnek olarak ürün ve fiyatlandırma bilgileri gibi başvuru bilgileri ya da yapı maliyeti olan paylaşılan statik kaynaklar sayılabilir.

Mikro hizmetler durum bilgisiz olsa da, dağıtılmış bir önbellek, kesinlikle gerekli olduğunda oturum durumu verilerine eşzamanlı erişimi destekleyebilir.

Ayrıca yinelenen hesaplamaları önlemek için önbelleğe almayı göz önünde bulundurun. Bir işlem verileri dönüştürirse veya karmaşık bir hesaplama gerçekleştiriyorsa, sonraki isteklerin sonucunu önbelleğe alma.

## <a name="caching-architecture"></a>Önbelleğe alma mimarisi

Bulutta yerel uygulamalar genellikle dağıtılmış bir önbelleğe alma mimarisi uygular. Önbellek, mikro hizmetlerden ayrı olarak bulut tabanlı bir [yedekleme hizmeti](./definition.md#backing-services)olarak barındırılır. Şekil 5-15, mimariyi gösterir.

![Cloud Native bir uygulamada önbelleğe alma](media/caching-in-a-cloud-native-app.png)

**Şekil 5-15**: bir bulutta yerel uygulamada önbelleğe alma

Önceki şekilde, önbelleğin mikro hizmetlerden nasıl bağımsız olduğunu ve bu hizmetin nasıl paylaşıldığını aklınızda. Bu senaryoda, önbellek [API ağ geçidi](./front-end-communication.md)tarafından çağrılır. Bölüm 4 ' te anlatıldığı gibi, ağ geçidi tüm gelen istekler için ön uç işlevi görür. Dağıtılmış önbellek, mümkün olduğunda önbelleğe alınmış verileri döndürerek sistem yanıt hızını artırır. Ayrıca, önbelleğin hizmetten ayrılması, önbelleğin artan trafik taleplerini karşılamak için bağımsız olarak ölçeği artırma veya genişletme olanağı sağlar.

Önceki şekil, [önbellek stili](https://docs.microsoft.com/azure/architecture/patterns/cache-aside)olarak bilinen ortak bir önbelleğe alma deseninin olduğunu gösterir. Gelen bir istek için, ilk olarak \# bir yanıt için önbelleği (1. adım) sorgulayın. Bulunursa, veriler hemen döndürülür. Veriler önbellekte yoksa ( [önbellek isabetsizliği](https://www.techopedia.com/definition/6308/cache-miss)olarak bilinir), bir aşağı akış hizmetindeki yerel bir veritabanından alınır ( \# 2. adım). Daha sonra gelecek istekler için önbelleğe yazılır (3. adım \# ) ve çağırana döndürülür. Sistemin zamanında ve tutarlı kalması için düzenli olarak önbelleğe alınmış verileri çıkarmak üzere dikkatli olunmalıdır.

Paylaşılan bir önbellek büyüdükçe, verilerin birden çok düğüm arasında bölümlenmesi yararlı olabilir. Bunun yapılması çekişmeyi en aza indirmeye ve ölçeklenebilirliği iyileştirmenize yardımcı olabilir. Birçok önbelleğe alma hizmeti, düğümleri dinamik olarak ekleme ve kaldırma ve verileri bölümler arasında yeniden Dengeleme özelliğini destekler. Bu yaklaşım genellikle kümeleme içerir. Kümeleme, bir Federasyon düğümleri koleksiyonunu sorunsuz, tek bir önbellek olarak kullanıma sunar. Bununla birlikte, veriler, yükü eşit olarak dengeleyen önceden tanımlanmış bir dağıtım stratejisi izleyen düğümlere dağıtılır.

## <a name="azure-cache-for-redis"></a>Redis için Azure Cache

[Redsıs Için Azure önbelleği](https://azure.microsoft.com/services/cache/) , Microsoft tarafından tam olarak yönetilen, güvenli bir veri önbelleğe alma ve mesajlaşma Aracısı hizmetidir. Hizmet olarak platform (PaaS) teklifi olarak tüketilen verilere yüksek aktarım hızı ve düşük gecikmeli erişim sağlar. Hizmet, Azure içindeki veya dışındaki tüm uygulamalar tarafından erişilebilir.

Redsıs hizmeti için Azure önbelleği, Azure veri merkezleri genelinde barındırılan açık kaynaklı Redsıs sunucularına erişimi yönetir. Hizmet, yönetim, erişim denetimi ve güvenlik sağlayan bir façlade işlevi görür. Hizmet, dizeler, karmalar, listeler ve kümeler dahil zengin bir veri yapıları kümesini yerel olarak destekler. Uygulamanız zaten Redsıs kullanıyorsa, bu,-olduğu gibi çalışır.

Redsıs için Azure önbelleği, basit bir önbellek sunucusundan daha fazla. Mikro hizmet mimarisini geliştirmeye yönelik bir dizi senaryoyu destekleyebilir:

- Bellek içi veri deposu
- Dağıtılmış ilişkisel olmayan veritabanı
- İleti Aracısı
- Yapılandırma veya bulma sunucusu
  
Gelişmiş senaryolarda, önbelleğe alınmış verilerin bir kopyası [diskte kalıcı](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-how-to-premium-persistence)hale getirilir. Çok zararlı bir olay hem birincil hem de çoğaltma önbelleklerini devre dışı bırakırsa, önbellek en son anlık görüntüden yeniden oluşturulur.

Azure Redis Cache, bir dizi önceden tanımlanmış yapılandırmada ve fiyatlandırma katmanlarında kullanılabilir. [Premium katman](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-overview#service-tiers) kümeleme, veri kalıcılığı, coğrafi çoğaltma ve sanal ağ yalıtımı gibi birçok kurumsal düzey özelliği sunar.

>[!div class="step-by-step"]
>[Önceki](relational-vs-nosql-data.md) 
> [Sonraki](elastic-search-in-azure.md)
