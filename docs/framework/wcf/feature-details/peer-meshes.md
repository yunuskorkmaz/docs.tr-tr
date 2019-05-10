---
title: Eş Kafesleri
ms.date: 03/30/2017
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
ms.openlocfilehash: 9113fab13da8503e6ce0335e5bb19a2634973dad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654488"
---
# <a name="peer-meshes"></a>Eş Kafesleri
A *mesh* benzersiz kafes kimliği ile tanımlanır ve iletişim kurabilen aralarında eş düğümleri adlandırılmış koleksiyonu (ister birbirine bağlı bir graf) Her düğüm, birden çok düğüme bağlıdır. İyi bağlanmış bir ağ kafes en kenarlarına düğümler arasındaki nispeten daha az sayıda atlamalarla birlikte herhangi iki düğüm arasında bir yolu yoktur ve bazı düğümleri veya bağlantıları doğrudan bile kafes bağlı kalır. Diğer eş bunları bulabilmesi için etkin düğüm ağı içinde karşılık gelen bir ağ kimliği, uç nokta bilgileriyle yayımlayın.  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a>Eş kanalı kullanılarak oluşturulan bir ağ özellikleri  
  
#### <a name="uniquely-identified"></a>Benzersiz şekilde tanımlanır  
  
- Her ağı benzersiz bir kimlik tanımlar. Kafes (veya ağ kimliği) bir etki alanı adı sistemi (DNS) ana bilgisayar adı ile aynı biçimde adıdır. Bu nedenle, bu ağ kimliği kullanılan Çözümleyicisi uygulamasının kapsamı içinde hedeflenen istemci için benzersiz olmalıdır. Ortak ad "MyFamilysPeers" veya "KevinsPokerTable," gibi diğer kullanıcı adlarıyla kolayca çakışabilir ve istenmeyen eş veya gizlilik sorunlarına yol bağlantı gecikme süresini uç nokta bilgileri döndürebilir. Bir sonek benzersiz bir kimliği kafes (örneğin, "KevinsPokerTable90210") için takma ad eklemek için bu sorunlardan kaçınmak için bir yol olabilir.  
  
#### <a name="message-flooding"></a>İleti taşmasını  
  
- Kafes iletileri bir veya daha fazla kullanıcılardan aynı grup içindeki tüm diğer eş düğümlere dağıtılmasını sağlar. Eş düğümleri tarafından yayılan iletileri kullanan ad alanında belirtilen üst bilgiler `http://schemas.microsoft.com/net/2006/05/peer`.  
  
#### <a name="optimized-connections"></a>En iyi duruma getirilmiş bağlantıları  
  
- Düğümleri katılın ve bırakın, tüm düğümler küçük bölümleri (birbirinden yalıtılmış düğümleri gruplar) oluşturma olasılığını ile iyi bağlantı olmasını sağlamak, eş kanalı kafes otomatik olarak ayarlar. Ağ bağlantıları, alıcı gönderenden ileti gecikme süresini olabildiğince az olmasını geçerli trafik düzenlerini esas alarak de dinamik olarak getirilir.  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a>Eş kanal sağlamaz popüler ağ özellikleri  
 Eş kanal sağlamaz popüler ağ özelliklerinin farkında olmak önemlidir. Tüm eş kanalı üzerine oluşturulabilir, bu özellikler şunları içerir:  
  
- **İleti sırası:** Tek bir kaynaktan gelen iletileri aynı sırada ya da kaynağa gönderilen sırayla tüm diğer taraflar gelebilir değil. İletileri gerektiren uygulamalar teslim edilemiyor belirli bir sırada, uygulamalarına (örneğin, tüm iletileri ile artan bir kimliği dahil ederek) oluşturmanız gerekir.  
  
- **Güvenilir Mesajlaşma:** Eş kanal ileti alma tüm eşleri tarafından emin olmak için bir mekanizma içermez. Mesaj teslimatı sağlamak için bir güvenilirlik katmanı eş kanalı üzerine yazmanız gerekir.
