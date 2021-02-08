---
description: 'Daha fazla bilgi için bkz: PNRP önbellekleri'
title: PNRP Önbellekleri
ms.date: 03/30/2017
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
ms.openlocfilehash: a9e64cd647be2fe33863e014ee4c22d1752f56f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794916"
---
# <a name="pnrp-caches"></a>PNRP Önbellekleri

Eş adı çözümleme Protokolü (PNRP) önbellekleri, eşler üzerinde tutulan algorithmically seçili eş uç noktalarının yerel koleksiyonlarıdır.  
  
## <a name="pnrp-cache-initialization"></a>PNRP önbelleği başlatma  

 Bir eş düğüm başlatıldığında, PNRP önbelleğini veya eş adı kayıt koleksiyonunu başlatmak için, bir düğüm aşağıdaki yöntemleri kullanabilir:  
  
- Düğüm kapatıldığında mevcut olan kalıcı önbellek girdileri sabit disk depolamadan yüklenir.  
  
- Bir uygulama P2P işbirliği altyapısını kullanıyorsa, işbirliği bilgileri bu düğüm için Ilgili kişi Yöneticisi ' nde bulunur.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Eş adı çözümlemesini çok düzeyli bir önbellek ile ölçeklendirme  

 PNRP önbelleklerindeki boyutları küçük tutmak için, Eş düğümleri her bir düzeyin en fazla sayıda girdi içerdiği çok düzeyli bir önbellek kullanır. Önbellekteki her düzey, PNRP KIMLIK numarası alanının (2<sup>256</sup>) onuncu daha küçük bir kısmını temsil eder. Önbellekteki en düşük düzey yerel olarak kaydedilmiş bir PNRP KIMLIĞI ve bu değere sayısal olarak yakın olan diğer PNRP kimliklerini içerir. Önbelleğin bir düzeyi en fazla 20 girdi ile doldurulduğundan, yeni bir alt düzey oluşturulur. Önbellekteki Maksimum düzey sayısı, log10 (buluttaki toplam PNRP kimliği sayısı) sırasına göre yapılır. Örneğin, 100.000.000 PNRP kimliği olan küresel bir bulutta, önbellekteki 8 ' den fazla (= log10 (100000000)) düzey ve ad çözümlemesi sırasında bir PNRP KIMLIĞINI çözümlemek için benzer sayıda atlama yoktur. Bu mekanizma, kendisine karşılık gelen CPA ile eş düğüm bulunana kadar PNRP Istek iletilerini bir sonraki en yakın eşe ileterek, rastgele bir PNRP KIMLIĞININ çözülebileceği bir dağıtılmış karma tablo sağlar.  
  
 Çözümlemenin tamamlandığından emin olmak için, bir düğüm önbelleğinin en düşük düzeyine bir giriş eklediğinde, girişin bir kopyasını önbelleğin son düzeyindeki tüm düğümlere yerleştirir.  
  
 Önbellek girdileri zaman içinde yenilenir. Eski olan önbellek girdileri önbellekten kaldırılır. Sonuç olarak, PNRP kimliklerinin dağıtılmış karma tablosu,, adres kayıtlarının ve DNS protokolünün, adresle ilişkili düğümün etkin bir şekilde ağda olduğundan emin olmadan, etkin uç noktaları temel alır.  
  
## <a name="other-pnrp-caches"></a>Diğer PNRP önbellekleri  

 Başka bir kalıcı veri deposu yerel önbelleğidir.  PNRP etkinliği için gereken diğer nesnelere ek olarak, tüm bulut üyeleri arasında güvenli bir şekilde yayınlanan ve eşitlenen bir PNRP bulutu veya işbirliği oturumuyla ilişkili kayıtları da içerebilir. Bu çoğaltılan depo, tüm grup üyeleri için aynı olması gereken grup verilerinin görünümünü temsil eder. Teknik olarak, bu nesneler se başına kayıt değildir, bunun yerine yerel bir önbellek için hedeflenen uygulama, varlık ve nesne verileri. PNRP bulutu kullanımı, nesnelerin işbirliği oturumunda veya PNRP bulutundaki tüm düğümlere yayılmasını sağlar.  Bulut üyeleri arasında kayıt çoğaltma, şifreleme ve veri bütünlüğü sağlamak için SSL kullanır.  
  
 Bir eş bir buluta katıldığında, bunlar, iliştirdikleri konak eşinden otomatik olarak yerel önbellek verileri almaz; uygulama, varlık ve nesne verilerinde güncelleştirmeleri almak için konak eşine abone olmaları gerekir. İlk eşitlemeden sonra, eşler tüm grup üyelerinin tutarlı olarak aynı görünüme sahip olduğundan emin olmak için çoğaltılan mağazalarını düzenli aralıklarla eşitler.  İşbirliği oturumu veya işbirliği oturumunda bulunan uygulamalar aynı işlevi de gerçekleştirebilir.  
  
 Bir buluta yönelik işbirliği oturumu başladıktan sonra, uygulamalar eşler kaydedebilir ve bulut kapsamı tarafından tanımlanan güvenliği kullanarak bilgilerini yayımlamaya başlayabilir. Bir eş bir buluta katıldığında, buluta yönelik güvenlik mekanizmaları, bu kümeye katılacak bir kapsam vererek eşe uygulanır.  Daha sonra kayıtları, bulutun kapsamı içinde güvenli bir şekilde yayımlanabilir. Bulut kapsamının işbirliği uygulama kapsamı ile aynı olamayacağını unutmayın.  
  
 Peers, nesneleri diğer eşlerden almak için ilgi kaydedebilir. Bir nesne güncelleştirilirken, işbirliği uygulamasına bildirilir ve yeni nesne, uygulamanın tüm abonelerine geçirilir. Örneğin, bir grup sohbeti uygulamasındaki bir eş, tüm sohbet kayıtlarını uygulama verileri olarak gönderecek şekilde uygulama bilgileri alma konusunda ilgi kaydedebilir.  Bu, bu BT 'nin bulut içindeki sohbet etkinliğini izlemesine olanak sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer>
