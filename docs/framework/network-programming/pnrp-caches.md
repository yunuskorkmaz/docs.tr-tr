---
title: PNRP Önbellekleri
ms.date: 03/30/2017
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
ms.openlocfilehash: 3ed3e11e702c8933b500421de5654b212cdd80d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64622986"
---
# <a name="pnrp-caches"></a>PNRP Önbellekleri
Eş Adı Çözümleme Protokolü (PNRP) önbellekleri, eş üzerinde tutulan algoritmik olarak seçilmiş eş uç noktalarının yerel koleksiyonlarıdır.  
  
## <a name="pnrp-cache-initialization"></a>PNRP Önbellek Başlatma  
 Eş düğümü başlatıldığında, PNRP önbelleğini veya Eş Adı Kaydı Koleksiyonu'nu başlatacak şekilde, bir düğüm aşağıdaki yöntemleri kullanabilir:  
  
- Düğüm kapatıldığında bulunan kalıcı önbellek girişleri sabit disk depolamadan yüklenir.  
  
- Bir uygulama P2P işbirliği altyapısını kullanıyorsa, bu düğüm için İletişim Yöneticisi'nde işbirliği bilgileri kullanılabilir.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Eş Adı Çözümünü Çok Düzeyli Önbellekle Ölçekleme  
 PNRP önbelleklerinin boyutlarını küçük tutmak için eş düğümleri, her düzeyin en fazla sayıda giriş içerdiği çok düzeyli bir önbellek kullanır. Önbellekteki her düzey PNRP kimlik numarası alanının onda bir küçük kısmını temsil eder (2<sup>256).</sup> Önbellekteki en düşük düzey, yerel olarak kaydedilmiş bir PNRP Kimliği ve sayısal olarak yakın olan diğer PNRP kimlikleri içerir. Önbelleğin düzeyi en fazla 20 girişle doldurulduğundan, yeni bir alt düzey oluşturulur. Önbellekteki maksimum düzey sayısı log10 (Buluttaki Toplam PNRP ID sayısı) sırasına göredir. Örneğin, 100 milyon PNRP Kimliğine sahip küresel bir bulut için, önbellekte en fazla 8 (=log10(100.000.000)) düzeyi ve ad çözümlemesi sırasında bir PNRP Kimliğini çözmek için benzer sayıda atlama vardır. Bu mekanizma, ilgili EBM'ye sahip eş bulunana kadar PNRP İstek iletilerini en yakın eşe ileterek rasgele bir PNRP Kimliğinin çözülebileceği dağıtılmış bir karma tabloya olanak tanır.  
  
 Çözünürlüğün tamamlanınabilmesi için, bir düğüm önbelleğinin en alt düzeye her girişinde, önbelleğin son düzeyindeki tüm düğümlere girişin bir kopyasını sel basıyor.  
  
 Önbellek girişleri zaman içinde yenilenir. Eski önbellek girişleri önbellekten kaldırılır. Sonuç olarak, PNRP ID'lerinin dağıtılmış karma tablosu, adres kayıtlarının ve DNS protokolünün adresle ilişkili düğümün ağda etkin olduğuna dair hiçbir garanti vermediği DNS'nin aksine etkin uç noktaları temel almaktadır.  
  
## <a name="other-pnrp-caches"></a>Diğer PNRP Önbellekleri  
 Başka bir kalıcı veri deposu yerel önbellektir.  PNRP etkinliği için gereken diğer nesnelere ek olarak, bir PNRP bulutu veya bulutun tüm üyeleri arasında güvenli bir şekilde yayınlanan ve eşitlenen işbirliği oturumuyla ilişkili kayıtları içerebilir. Bu çoğaltılan depo, tüm grup üyeleri için aynı olması gereken grup verilerinin görünümünü temsil eder. Teknik olarak, bu nesneler kendi başına kayıt değil, daha çok uygulama, durum ve nesne verileri yerel bir önbellek için mukadder. PNRP bulutunun kullanımı, nesnelerin işbirliği oturumundaki veya PNRP bulutundaki tüm düğümlere yayılmasını sağlar.  Bulut üyeleri arasındaki kayıt çoğaltma şifreleme ve veri bütünlüğü sağlamak için SSL kullanır.  
  
 Bir eş bir buluta katıldığında, bağlı oldukları ana bilgisayar eşlerinden yerel önbellek verilerini otomatik olarak almazlar; uygulama, durum ve nesne verilerinde güncelleştirmeler almak için ana bilgisayar eşe abone olmaları gerekir. İlk eşitlemeden sonra, eşler, tüm grup üyelerinin tutarlı bir şekilde aynı görünüme sahip olmasını sağlamak için çoğaltılan depolarını düzenli olarak yeniden eşitler.  İşbirliği oturumu veya işbirliği oturumu içindeki uygulamalar da aynı işlevi gerçekleştirebilir.  
  
 Bulut için bir işbirliği oturumu başladıktan sonra, uygulamalar eşlerini kaydedebilir ve bulut kapsamı tarafından tanımlanan güvenliği kullanarak bilgilerini yayımlamaya başlayabilir. Bir eş buluta katıldığında, bulutun güvenlik mekanizmaları eşe uygulanır ve bu da ona katılacağı bir kapsam verir.  Kayıtları daha sonra bulut kapsamında güvenli bir şekilde yayımlanabilir. Bulut kapsamının işbirliği uygulama kapsamıyla aynı olmayabileceğini unutmayın.  
  
 Eşler, diğer eşlerden nesne alma ilgi kaydedebilirsiniz. Bir nesne güncelleştirildiğinde, işbirliği uygulaması bildirilir ve yeni nesne uygulamanın tüm abonelerine geçirilir. Örneğin, grup sohbet uygulamasındaki bir eş, tüm sohbet kayıtlarını uygulama verisi olarak gönderecek olan uygulama bilgilerini alma ilgisini kaydedebilir.  Bu, bulut içindeki sohbet etkinliğini izlemesine olanak tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer>
