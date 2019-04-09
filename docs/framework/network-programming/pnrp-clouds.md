---
title: PNRP Bulutları
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: 943cad880885a624c0ed0798738665c8bcd7036f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110051"
---
# <a name="pnrp-clouds"></a>PNRP Bulutları
Bir PNRP "bulut" ağ üzerinden birbiriyle iletişim kurabilir düğümleri kümesini temsil eder. "Bulut" terimi, "eş kafes" ve "eşler arası grafik" ile eşanlamlıdır.  
  
 Düğümler arasında iletişim hiçbir zaman bir buluttan diğerine çıkarmanız gerekir. A <xref:System.Net.PeerToPeer.Cloud> örneği büyük küçük harfe duyarlıdır ve adıyla benzersiz şekilde tanımlanır. Tek bir eş veya düğüm birden fazla buluta bağlı olabilir.  
  
 Bulut ağ arabirimlerinde çok yakın bir şekilde bağlıdır.  Bir çok ana bilgisayarlı makinede farklı alt ağlara bağlı iki ağ kartı olan üç bulut döndürülür: her arabirim ve tek bir genel kapsam bulut başına bağlantı yerel adresi.  
  
 "Bir kapsam bir gruplandırma birbirine bulamadı bilgisayarların olduğu üç bulut kapsamların" PNRP kullanır:  
  
-   Genel bulut, genel IPv6 adresi kapsamını ve genel adres karşılık gelen ve tüm IPv6 Internet üzerindeki tüm bilgisayarları gösterir. Yalnızca tek bir genel bulut yok.  
  
-   Bağlantı-yerel bulut bağlantı-yerel adresleri ve bağlantı-yerel IPv6 adresi kapsamını karşılık gelir. Genellikle yerel olarak bağlı alt ağ ile aynı belirli bir bağlantı, bağlantı-yerel bulut içindir. Birden çok bağlantı-yerel bulut olabilir.  
  
 Siteye özel bulut, üçüncü bir bulut site IPv6 adresi kapsamını ve site-yerel adresleri karşılık gelir. Bu bulut, PNRP hala desteklenmektedir ancak kullanım dışıdır.  
  
## <a name="clouds"></a>Bulutlar  
 PNRP Bulutları örnekleri tarafından temsil edilen <xref:System.Net.PeerToPeer.Cloud> sınıfı. Bulut grupları kullanılan bir eş numaralandırılabilir örnekleri tarafından temsil edilen <xref:System.Net.PeerToPeer.CloudCollection> sınıfı. Statik çağırarak geçerli eşler arası bilinen PNRP Bulutları koleksiyonlarının edinilebilir <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> yöntemi.  
  
 Bağımsız Bulutlar 256 karakter Unicode dize olarak temsil edilen benzersiz adlara sahip. Bu adlar benzersiz bulut sınıfının örneklerini oluşturmak için yukarıda belirtilen kapsam ile birlikte kullanılır. Bu örnek serileştirilmiş ve için kalıcı kullanım reconstructed.  
  
 Bir bulut örneği oluşturulduğunda veya elde sonra eş adları bilinen eş ağ oluşturmak için kaydedilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.Cloud>
- [Eş Adı Çözümleme Protokolü](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
