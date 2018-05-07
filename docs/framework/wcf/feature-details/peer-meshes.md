---
title: Eş Kafesleri
ms.date: 03/30/2017
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
ms.openlocfilehash: afd9eae36f28c28b33b74c4456feb4ba8c91314d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="peer-meshes"></a>Eş Kafesleri
A *mesh* iletişim kendilerini arasında ve bir benzersiz kafes kimliği tarafından tanımlanan eş düğümlerinin adlandırılmış koleksiyonu (birbirine bağlı bir grafik) Her düğüm için birden çok diğer düğümlere bağlanır. İyi bağlantılı bir kafes kafes en ilerideki kenarlarında düğümler arasında nispeten az durakları herhangi iki düğüm arasında bir yolu yoktur ve bazı düğümler veya bağlantıları bırakma olsa bile kafes bağlı kalır. Diğer eş bunları bulabilmesi için Kafes etkin düğüm karşılık gelen bir kafes kimliği ile uç nokta bilgilerini yayımlayabilir.  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a>Eş kanalı kullanılarak oluşturulan bir kafes özellikleri  
  
#### <a name="uniquely-identified"></a>Benzersiz olarak tanımlanır  
  
-   Benzersiz bir kimliği her kafes tanımlar. Bir etki alanı adı sistemi (DNS) ana bilgisayar adı ile aynı biçimi kafes (veya ağ kimliği) adı kullanılıyor. Bu nedenle, bu kafes kimliği uygulama kapsamı içinde kullanılan çözümleyicinin amaçlanan istemci için benzersiz olmalıdır. Bir ortak adı "MyFamilysPeers" veya "KevinsPokerTable," gibi başka bir kullanıcı adı ile kolayca çakışabilir ve istenmeyen eş gizlilik sorunlara neden veya bağlantı gecikmesi artırın uç nokta bilgileri döndürebilir. Benzersiz bir kimliği (örneğin, "KevinsPokerTable90210") kafes için takma ad sonek eklemek için bu sorunları önlemek için bir yol olabilir.  
  
#### <a name="message-flooding"></a>İleti taşmasını  
  
-   Mesh iletileri bir veya daha fazla göndericilerden aynı kafes içindeki tüm diğer eş düğümlere dağıtılmasını sağlar. Eş düğümleri tarafından yayılan iletileri kullanan ad alanında belirtilen üstbilgileri `http://schemas.microsoft.com/net/2006/05/peer`.  
  
#### <a name="optimized-connections"></a>En iyi duruma getirilmiş bağlantıları  
  
-   Düğümleri katılma ve bırakın, tüm düğümler bölümleri (birbirlerinden düğümlerinin grup) oluşturma az olasılığını düzgün bağlantısı sahip olduktan eş kanalı kafes otomatik olarak ayarlanır. Ağ bağlantıları da dinamik alıcı gönderenden ileti gecikme süresini olabildiğince küçük böylece geçerli trafik düzenlerini esas alarak en iyi duruma getirilir.  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a>Eş kanal sağlamaz popüler ağ özellikleri  
 Eş kanal sağlamaz popüler ağ özelliklerini haberdar olmanız önemlidir. Tüm eş kanalı üstünde oluşturulmuş, bu özellikler şunları içerir:  
  
-   **İleti sıralama:** iletiler tek bir kaynaktan kaynaklanan tüm diğer taraflar aynı sırada veya kaynak gönderilen sırada değil geldiğinde. İletileri gerektiren uygulamalar içinde teslim edilemiyor belirli bir sipariş, uygulamalarına (örneğin, tüm iletileri artan Kimliğiyle ekleyerek) oluşturmanız gerekir.  
  
-   **Güvenilir Mesajlaşma:** eş kanalı ileti alma tüm eşleri tarafından emin olmak için bir mekanizma içermez. İleti teslimi güvence altına almak için güvenilirlik katmanı eş kanal üzerine yazması gerekir.
