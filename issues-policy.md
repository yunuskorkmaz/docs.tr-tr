---
ms.openlocfilehash: 33178637c4fcfb21e8190c3d2593f09326ea5995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73554850"
---
# <a name="github-issues-process-and-policy"></a>GitHub sorunları süreci ve ilkesi

Sürecin hedefleri şunlardır:

1. Dokümanlarımızdaki hataların veya eksikliklerin müşteri başarısını engellemediğinden emin olun.
1. Müşteri geri bildirimlerine ve endişelerine duyarlı olun.
1. Müşteri deneyimini sürekli olarak geliştirmek.
1. Zorluklar ve çözümler hakkında açık iletişim yoluyla müşteri deneyimleri hakkında daha fazla bilgi edinin.

İşlem, çalışmaya öncelik verirken yanıt verme işlemini sağlamak için iki aşama kullanır. İlk aşama sorunu tanılar ve triyajlar. İkinci aşama sorunu çözer. Bir sorun hem kolay hem de acil olduğunda, iki aşama birleştirilebilir.

İşlem, sabit zaman ayırmalarına sahip görevleri içerir:

- Her ekip üyesi, ilk yanıtlar da dahil olmak üzere [gelen sorunları sınıflandırarak](#diagnosis-phase)her iş günü için 1/2 saate kadar zaman harcar. Bu, yeni sorunlara yanıt vermemizi sağlar.
- Her ekip üyesi, müşteri tarafından oluşturulan GitHub sorunlarını gidermek için [belgeleri güncellemek](#resolution-phase) için haftada 1/2 güne kadar zaman harcar.

## <a name="diagnosis-phase"></a>Tanı aşaması

Her ekip üyesi iş günü başına en fazla 30 dakika ya da yeni sorunları kategorilere ayırarak harcar. Aşağıdaki soruları yanıtlıyoruz:

- Sorun bir doküman sorunu mu yoksa ürün sorunu mu?
- Bu bir sorun değil, bir soru daha iyi bir forum veya destek sitesi için uygun mu?
- Konu ne kadar öncelikli?
- Bu sorunu hangi alan yönetir?

Bu soruların ilk sınavda cevaplanaması halinde, yorumlarda açıklayıcı sorular sorarız.

Tanı ve triyaj aşamasında kapanan sorun türleri vardır:

- **kudos**: Biz teşekkür ifade ve sorunu kapatın.
- **ürün konusu**: Ürünle ilgili değil, dokümantasyonuyla ilgili konular kapatılır. Aşağıda açıklandığı gibi ek eylemlerde de bulunabiliriz.
- **COC ihlalleri**: [CoC ihlali](https://dotnetfoundation.org/code-of-conduct) raporlama yı ve engellemeyi hak ederse, bu sorunlar kapatılır ve raporlanır.
- **yinelenenler**: Yinelenenler, varolan soruna atıfta bulunan bir açıklamayla kapatılır.
- **doc-ok**: Müşteri yanlış ve doküman doğrudur.
- **forum**: Destek veya forum istekleri olan sorunlar Stack Overflow veya diğer destek sitelerine yönlendirilir ve kapatılır.

### <a name="actions-on-product-issues"></a>Ürün sorunlarıyla ilgili eylemler

Ürün sorununun niteliğine bağlı olarak, aşağıdakileri seçebiliriz:

- Sorunu uygun ürün deposuna aktarın.
- Sorunu, varolan ürün isteklerinin bir kopyası olarak kapatın.
- Ürün deposunda açmak için bir öneri ile sorunu kapatın.

Doğru eylem inisiyatifini değerlendirmek özneldir. Ekip üyeleri doğru eylem kendi yargı kullanın.

### <a name="actions-on-content-issues"></a>İçerik sorunlarıyla ilgili eylemler

Diğer sorunlar için, takım:

- Öncelik atar
- Genellikle "Biriktirme Listesi" olan bir kilometre taşı atar
- Bir sorunun iyi bir "kapma için hazır" bir sorun olup olmadığını veya [.NET Topluluk Katılımcıları Için Projeler'i](https://github.com/dotnet/docs/projects/35) değerlendirir

Öncelik düzeyleri aşağıdaki yönergelere dayanır, ancak özneldir. Kilometre taşları da özneldir ve mevcut ürün yayın programları ve yaklaşan lansmanlar gibi diğer öncelikleri temel alınmaktadır.

- **P0**: Dokümanların ihmali veya hatası, müşterilerin ortak bir senaryoda başarılı olmasını engeller.
  - **P0** sorunları, önceden planlanmış çalışma üzerinde öncelikli, önümüzdeki üç hafta içinde ele alınır.
- **P1**: Bir dokümanihmali veya hatası, yaygın bir senaryoyu çok daha zor hale getirir veya diğer iyi bilinen senaryoları engeller.
  - **P1** sorunları zamanında zamanlanır. Genellikle, P1 sorunları yaklaşan bir kilometre taşı için planlanır.
- **P2**: Küçük rahatsızlıklara neden olan veya düşük sayfa görünümü makalesini etkileyen sorunlar.
  - Bir makale daha yüksek öncelikli nedenlerle güncelleştirildiğinde, **P2** sorunları genellikle düzeltilir.
- **P3**: Kenar durum senaryoları için istekolan sorunlar.
  - **P3** sorunları biriktirme listesine yerleştirilir ve makaleler daha yüksek öncelikli nedenlerle güncelleştirildiğinde güncelleştirme olarak kabul edilir.

Ekip üyeleri, zamanlanmış görevlerde ilerleme kaydedebilmeleri için tanı ve triyaj üzerinde sınırlı bir süre harcarlar. Her ekip üyesi tanı ve triyaj günde en fazla 30 dakika geçirir.

Bir sorun bir topluluk üyesinin (muhtemelen yazar) düzeltme göndermesi için iyi bir aday **olduğunda, up-for-grabs** etiketi uygulanır. **Up-for-grabs** etiketini uygulayan ekip üyesi, topluluk üyelerinin PR oluşturma sürecinde çalışmasına yardımcı olacak veya birini bulacak. [Topluluk Katkısı projelerine](https://github.com/dotnet/docs/projects/35) sık sık "kapmaya hazır" olan konular eklenir

> NOT: Biz sadece son zamanlarda önceki sözleşme kabul ettik. Etiketi ekleyen kişi sizi yardımcı olacak başka bir ekip üyesine yönlendirebilir.

## <a name="resolution-phase"></a>Çözünürlük aşaması

Müşteri tarafından oluşturulan sorunlar, zamanlanan görev planlamasının bir parçası olarak ağırlıklandırılır. Her ekip üyesi, en yüksek öncelikli müşteri sorunlarını ele almak için haftada 4 saat ayırır.

Sorun çözümü tanı sırasında belirlenen öncelik düzeyinden izler. Gelen müşteri sorunları, benzer önceliğe sahip diğer zamanlanmış çalışmayla öncelike

- **P0**: En kısa sürede makul olarak, önümüzdeki üç hafta boyunca.
- **P1**: Planlanan diğer P1 çalışmaları ile zamanlanır. Bu genellikle önümüzdeki üç ay içinde anlamına gelir.
- **P2**: Planlanan diğer P2 çalışmaları ile zamanlanır. P2 sorunları düzenli olarak alan ve görünürlüğe göre zamanlanır. Daha sık, bir makale güncelleştirildiğinde P2 sorunları giderilecektir.
- **P3**: Düzeltme tarihinde garanti yoktur. Bir makale güncelleştirildiğinde, aynı makaledeki diğer sorunlar için biriktirme listesini inceleriz.

Yeni geri bildirimlere ve makale görünürlüğü yle ilgili verilere dayanarak sorunlar yeniden önceliklendirilebilir.
