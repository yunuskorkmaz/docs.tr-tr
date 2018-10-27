---
title: PNRP önbellekleri
ms.date: 03/30/2017
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
ms.openlocfilehash: 53df90a9bb3da90145ebe30bb274b4ff4950c00f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180971"
---
# <a name="pnrp-caches"></a>PNRP önbellekleri
Eş Adı Çözümleme Protokolü (PNRP) önbellekler algorithmically seçili eş uç noktaları eş tutulan yerel koleksiyonlarıdır.  
  
## <a name="pnrp-cache-initialization"></a>PNRP önbellek başlatma  
 Bir eşdüzey düğüm başlatıldığında PNRP önbellek ya da eş ad kaydı koleksiyonuna başlatmak için bir düğüm aşağıdaki yöntemleri kullanabilirsiniz:  
  
-   Düğüm kapatıldığı sırada mevcut kalıcı önbellek girişlerinin sabit disk depolama alanından yüklenir.  
  
-   Bir uygulama P2P işbirliği altyapınızın kullanıyorsa, kişinin Yöneticisi'nde bu düğüm için işbirliği bilgileri kullanılabilir.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Eş adı çözümleme çok düzeyli bir önbellek ile ölçeklendirme  
 PNRP önbellekleri boyutlarını küçük tutmak için her düzeyi bir giriş sayısı üst sınırı içeren, çok düzeyli bir önbellek eş düğümleri kullanın. Önbellekteki her düzeyi bir saniyenin onda daha küçük bir bölümünü PNRP kimlik numarası alanı temsil eder (2<sup>256</sup>). Önbellekteki en alt düzeyin bir yerel olarak kayıtlı PNRP kimliği ve sayısal olarak onu yakın olan diğer PNRP kimlikleri içeriyor. Yeni bir alt düzey önbelleği düzeyini, en fazla 20 girişleri ile doldurulmuş şekilde oluşturulur. Log10 bazında önbelleğinde düzeylerinin sayısı olan (PNRP kimlikleri bulutta toplam sayısı). Örneğin, bir genel bulut için 100 milyon PNRP kimlikleri vardır en fazla 8 (=log10(100,000,000)) düzeyleri önbellek ve benzer bir ad çözümlemesi sırasında PNRP kimliği çözmek için atlama sayısı. Bir rastgele PNRP kimliği için çözülebilir karşılık gelen CPA Eşle bulunana kadar PNRP istek iletilerini sonraki en yakın eşler arası iletme tarafından dağıtılmış karma tablo bu mekanizma sağlar.  
  
 Çözüm, bir düğüm bir giriş, önbellek, en düşük düzeyine eklediği her durumda tamamlamasını sağlamak için giriş son düzey önbellek içindeki tüm düğümlere bir kopyasını şişirir.  
  
 Önbellek girişlerinin zamanla yenilenir. Eski önbellek girişlerinin önbellekten kaldırılır. Etkin uç noktaları, farklı DNS adresi kayıtlarını ve DNS protokolünü adresle ilişkilendirilen düğümü etkin olduğundan garanti sağlayan dağıtılmış bir karma tablo PNRP kimlikleri dayalı sonucudur.  
  
## <a name="other-pnrp-caches"></a>Diğer PNRP önbellekleri  
 Başka bir kalıcı veri deposu yerel bir önbellektir.  PNRP etkinliği için gereken diğer bir nesnelerin yanı sıra, bu, güvenli bir şekilde yayımlanan ve tüm bulut üyeleri arasında eşitlenen bir PNRP Bulut veya işbirliği oturumu ile ilişkili kayıt içerebilir. Çoğaltılan bu depo, tüm Grup üyeleri için aynı olmalıdır Grup verileri görünümünü temsil eder. Teknik olarak, bu nesneler kayıt başına uzatılmasında yerine uygulama, durum ve nesne verileri için yerel önbelleğin hedefleyen ancak değildir. PNRP bulut işbirliği oturumu veya PNRP bulut nesneleri tüm düğümlere yayılır sağlar.  Kayıt çoğaltma bulut üyeleri arasında şifreleme ve veri bütünlüğünü sağlamak için SSL kullanır.  
  
 Bir eş Bulutu katıldığında, otomatik olarak yerel önbellek veri ekleme, konak eşten aldıkları değil; Uygulama, durum ve nesne verilerini güncelleştirmeleri almak için konağı eş abone olmak sahiptirler. İlk eşitleme sonrasında eşleri çoğaltılmış mağazalarındaki tüm Grup üyeleri aynı görünümde tutarlı olmasını sağlamak için düzenli aralıklarla yeniden eşitleyin.  Ayrıca işbirliği oturumu veya işbirliği oturum içindeki uygulamalar aynı işlevi gerçekleştirebilir.  
  
 İçin bulut işbirliği oturumu başladıktan sonra uygulamaları eş kaydedebilir veya Bulut kapsamı tarafından tanımlanan güvenlik kullanarak kendi bilgilerini yayımlama başlayın. Bir eş Bulutu katıldığında, bulut için güvenlik mekanizmaları katılmak için kapsamda vererek çiftine uygulanır.  Kayıtlarını ardından güvenli bir şekilde bulut kapsamında yayımlanabilir. Bulut kapsamına işbirliği uygulama kapsamı aynı olabileceğini unutmayın.  
  
 Eş diğer eşlerden nesneler alınıyor ilgi azalmasını kaydedebilirsiniz. Bir nesne güncelleştirildiğinde işbirliği uygulaması bildirilir ve uygulamanın tüm abonelerine yeni bir nesne geçirilir. Örneğin, bir grup sohbet uygulaması bir eş sohbet kayıtları tüm uygulama verileri olarak gönderir, uygulama bilgilerini alma ilgi kaydedebilirsiniz.  Bu bulut içinde sohbet etkinliğini izlemesine izin verir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer>
