---
title: PNRP önbellekler
ms.date: 03/30/2017
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: dfa7da476bd56b34d3fcb7b7e0f3bcc33fee032b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397487"
---
# <a name="pnrp-caches"></a>PNRP önbellekler
Eş Adı Çözümleme Protokolü (PNRP) önbellekleri eş tutulan algorithmically seçili eş uç noktaları yerel koleksiyonlarıdır.  
  
## <a name="pnrp-cache-initialization"></a>PNRP Önbelleği başlatma  
 Eş düğüm başlatıldığında PNRP önbellek ya da eş adı kayıt koleksiyonu başlatmak için bir düğüm aşağıdaki yöntemleri kullanabilirsiniz:  
  
-   Düğüm kapatıldığı sırada mevcut kalıcı önbellek girişlerinin sabit disk depolama alanından yüklenir.  
  
-   Bir uygulama P2P işbirliği altyapınızın kullanıyorsa, kişiyi Yöneticisi'nde bu düğüm için işbirliği bilgisi yok.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Eş adı çözümleme çok düzeyli bir önbellek ile ölçeklendirme  
 PNRP önbellekleri boyutunu küçük tutmak için her düzeyi giriş sayısı üst sınırı içeren birden çok düzeyli bir önbellek eş düğümleri kullanın. Her düzey önbelleğinde PNRP kimliği sayısı alanı bir milimetrenin onda küçük bölümünü temsil eder (2<sup>256</sup>). Önbellekteki en alt düzeyin bir yerel olarak kayıtlı PNRP kimliği ve diğer PNRP sayısal onu yakın kimliklerini içerir. Önbellek düzeyini en fazla 20 girişleri ile doldurulur gibi yeni bir alt düzey oluşturulur. En fazla önbellek düzeylerini terabayt log10 sayısıdır (PNRP kimlikleri bulutta toplam sayısı). Örneğin, 100 milyon PNRP kimlikleri genel bulut için vardır en fazla 8 (=log10(100,000,000)) düzeyleri önbellek ve benzer bir ad çözümlemesi sırasında PNRP kimliği çözümlemeye atlama sayısı. Rastgele bir PNRP kimliği için çözülebilir karşılık gelen CPA Eşle bulunana kadar sonraki en yakın eşler arası PNRP isteği iletilerinin ileterek dağıtılmış karma tablo bu mekanizma sağlar.  
  
 Çözüm, her seferinde bir düğümü en düşük düzeyde, önbellek, bir giriş ekler tamamlamasını sağlamak için önbellek son düzeyi içindeki tüm düğümler girişe kopyasını şişirir.  
  
 Önbellek girişlerinin zamanla yenilenir. Eski önbellek girişlerinin önbellekten kaldırılır. DNS adresi kayıtlarını ve DNS protokolü adresi ile ilişkili düğümü ağ üzerinde etkin olduğu garanti sağlayan aksine etkin uç noktaları PNRP kimlikleri dağıtılmış karma tablosu dayalı sonucudur.  
  
## <a name="other-pnrp-caches"></a>Diğer PNRP önbellekler  
 Başka bir kalıcı veri yerel önbelleği deposudur.  PNRP etkinliği için gerekli diğer bir nesneler yanı sıra, güvenli bir şekilde yayımlanan ve tüm bulut üyeleri arasında eşitlenen bir PNRP Bulut veya işbirliği oturumu ilişkili kayıtları içerebilir. Bu çoğaltılan depo tüm Grup üyeleri için aynı olması gerekir Grup verilerin görünümünü temsil eder. Teknik olarak, bu nesnelerin kayıtları başına uzatılmasında yerine uygulama, durum ve nesne verileri için yerel önbellek hedefleyen ama değildir. Nesneleri işbirliği oturumu veya PNRP bulut tüm düğümlere yayılır PNRP bulut kullanımı sağlar.  Kayıt çoğaltma bulut üyeleri arasında şifreleme ve veri bütünlüğünü sağlamak için SSL kullanır.  
  
 Bir eş Bulutu katıldığında, otomatik olarak yerel önbelleği veri ekleme bunlar konak eşten almazlar; Uygulama, durum ve nesne verilerini güncelleştirmeleri almak için konak eş abone olmak sahiptirler. Başlangıç eşitlemesinden sonra eş çoğaltılmış mağazaları tüm Grup üyeleri aynı görünüm tutarlı olmasını sağlamak için düzenli aralıklarla yeniden eşitleyin.  Ayrıca işbirliği oturumunu veya uygulamaları işbirliği oturumu içinde aynı işlevi gerçekleştirebilir.  
  
 İşbirliği oturum için bir bulut başladıktan sonra uygulamaları eş kaydetmek ve bulut kapsamı tarafından tanımlanan güvenlik kullanarak kendi bilgilerini yayımlama başlayın. Bir eş Bulutu katıldığında, bulut için güvenlik mekanizmaları katılmak üzere bir kapsam vermiş eş uygulanır.  Kayıtlarını ardından güvenli bir şekilde buluta kapsamında yayımlanabilir. Bulut kapsamını işbirliği uygulama kapsamı ile aynı olabileceğini unutmayın.  
  
 Eş diğer eşlerden nesneleri alma ilgi kaydedebilirsiniz. Bir nesne güncelleştirildiğinde işbirliği uygulama bildirilir ve yeni bir nesne uygulamanın tüm abonelere geçirilir. Örneğin, bir grup sohbet uygulaması bir eş uygulama verileri olarak tüm sohbet kayıtları göndereceğiniz uygulama bilgilerini alma ilgi kaydedebilirsiniz.  Bu bulut içinde sohbet etkinliğini izlemek için sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer>
