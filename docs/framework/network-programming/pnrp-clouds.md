---
title: PNRP Bulutlar
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ef3f4fd2f7333c5a78024edf7eb536e9254c0293
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="pnrp-clouds"></a>PNRP Bulutlar
PNRP "bulut" ağ üzerinden birbirleriyle iletişim düğümler kümesini temsil eder. "Bulut" terimi "eş kafes" ve "eşler arası grafik" ile eşanlamlıdır.  
  
 Düğümler arasında iletişim hiçbir zaman bir buluttan diğerine çıkarmanız gerekir. A <xref:System.Net.PeerToPeer.Cloud> örneği duyarlıdır adıyla tarafından tanımlanan benzersiz olarak. Tek bir eş veya düğüm için birden fazla bulut bağlı olabilir.  
  
 Bulut ağ arabirimlerine çok yakından bağlıdır.  Bir çok konaklı makinede farklı alt ağa bağlı iki ağ kartı olan üç bulut döndürülür: her arabirimi ve tek bir genel kapsam Bulutu başına bağlantı yerel adresler için bir tane.  
  
 "Bir kapsam bir gruplandırma birbirine bulamıyor bilgisayarların olduğu üç bulut kapsamlar", PNRP kullanır:  
  
-   Genel bulut genel IPv6 adresi kapsamını ve genel adresleri karşılık gelir ve tüm IPv6 Internet üzerindeki tüm bilgisayarlar temsil eder. Yalnızca tek bir genel bulut yok.  
  
-   Bağlantı-yerel bulutta bağlantı-yerel adresleri ve bağlantı yerel IPv6 adresi kapsamını karşılık gelir. Bağlantı-yerel bulutta, genellikle yerel olarak bağlı alt ağ ile aynı olan belirli bir bağlantı içindir. Birden çok bağlantı-yerel Bulutlar olabilir.  
  
 Üçüncü Bulutu, siteye özgü bulut site IPv6 adresi kapsamı ve site-yerel adresleri karşılık gelir. Yine PNRP desteklenmesine karşın, bu bulut onaylanmaz.  
  
## <a name="clouds"></a>Bulutlar  
 PNRP bulut örneği tarafından temsil edilen <xref:System.Net.PeerToPeer.Cloud> sınıfı. Bulut grupları kullanılan bir eş numaralandırılabilir örneği tarafından temsil edilen <xref:System.Net.PeerToPeer.CloudCollection> sınıfı. Geçerli eşler arası bilinen PNRP bulut koleksiyonları elde edilebilir statik çağırarak <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> yöntemi.  
  
 Tek tek bulut 256 karakter Unicode dize olarak temsil benzersiz adlara sahip. Bu adları benzersiz sınıfın örnekleri, bulut oluşturmak için yukarıda belirtilen kapsamı ile birlikte kullanılır. Bu örnekler serileştirilmiş ve kalıcı kullanım için yeniden kullanabilirsiniz.  
  
 Bir bulut örneği oluşturulan ya da elde sonra eş adlarını bilinen eş kafes oluşturmak için kaydedilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer.Cloud>  
 [Eş Adı Çözümleme Protokolü](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
