---
description: 'Daha fazla bilgi edinin: eş kafesler'
title: Eş Kafesleri
ms.date: 03/30/2017
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
ms.openlocfilehash: bedb8931c4ed4c4f62cb3556699d7f9f07f6f022
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733391"
---
# <a name="peer-meshes"></a>Eş Kafesleri

*Ağ* , eşler arasında iletişim kurabilen ve benzersiz BIR ağ kimliği tarafından tanımlanan, eş düğümlerin adlandırılmış bir koleksiyonudur (bağlanmış bir grafiktir). Her düğüm birden fazla diğer düğüme bağlanır. İyi bağlanmış bir kafesde, iki düğüm arasında, kafesin en çok kenarlarındaki düğümler arasında görece az atlama olacak bir yol vardır ve bazı düğümler veya bağlantılar kullanıma alsa bile ağ bağlantısı kalır. Kafesteki etkin düğümler, diğer eşlerin onları bulabilmesi için uç nokta bilgilerini ilgili bir ağ KIMLIĞIYLE yayımlar.  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a>Eş kanal kullanılarak oluşturulan bir kafesin özellikleri  
  
#### <a name="uniquely-identified"></a>Benzersiz olarak tanımlandı  
  
- Benzersiz bir KIMLIK her bir ağı tanımlar. Ağ adı (veya ağ KIMLIĞI), etki alanı adı sistemi (DNS) ana bilgisayar adıyla aynı biçimde. Bu nedenle, bu ağ KIMLIĞI, kullanılan çözümleyici kapsamındaki uygulamanın amaçlanan istemcisi için benzersiz olmalıdır. "MyFamilysPeers" veya "KevinsPokerTable" gibi ortak bir ad, diğer kullanıcı adlarıyla kolayca çakışabilir ve istenmeyen eşdüzey uç nokta bilgilerini döndürebilir, bu durum gizlilik sorunlarına yol açabilir veya bağlantı gecikmesini artırabilir. Bu sorunları önlemenin bir yolu, ağ için takma ad (örneğin, "KevinsPokerTable90210") için bir sonek olarak benzersiz bir KIMLIK eklemek olabilir.  
  
#### <a name="message-flooding"></a>İleti taşması  
  
- Ağ, iletilerin bir veya daha fazla göndericinden aynı kafesteki diğer tüm eş düğümlerine yayılmasını sağlar. Eş düğümleri tarafından taşan iletiler, öğesinde ad alanında belirtilen üst bilgileri kullanır `http://schemas.microsoft.com/net/2006/05/peer` .  
  
#### <a name="optimized-connections"></a>İyileştirilmiş bağlantılar  
  
- Düğümler, tüm düğümlerin bölüm oluşturma (birbirinden yalıtılmış düğüm grupları) konusunda çok iyi bağlantı sahibi olduğundan emin olmak için otomatik olarak bir eş kanal ağı ayarlanır ve bırakır. Kafesteki bağlantılar aynı zamanda geçerli trafik desenlerine göre dinamik olarak iyileştirilir, böylece gönderen 'den alıcıya ileti gecikmesi mümkün olduğunca kısa olur.  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a>Eş kanalın sağlamadığı popüler ağ özellikleri  

 Eş kanalın sağlamadığına yönelik popüler ağ özelliklerinin farkında olmak önemlidir. Bu özellikler, hepsi eş kanal üzerine inşa edilebilir, şunları içerir:  
  
- **İleti sıralaması:** Tek bir kaynaktan kaynaklanan iletiler, aynı sırada veya kaynağın gönderildiği sırada diğer tüm taraflara ulaşmayabilir. Belirli bir sırada ileti teslim etmek için gerekli olan uygulamalar, kendi uygulamalarına (örneğin, tüm iletilerle tek bir artan KIMLIĞI ekleyerek) derlenmelidir.  
  
- **Güvenilir Mesajlaşma:** Eş kanal, tüm eşler tarafından ileti alımı sağlamak için bir mekanizma içermez. İleti teslimini güvence altına almak için, eş kanalın en üstüne bir güvenilirlik katmanı yazmanız gerekir.
