---
title: PNRP Bulutları
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: dd27e61fe1f648dcaf4ee4dd5f5119d33913c63a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047367"
---
# <a name="pnrp-clouds"></a>PNRP Bulutları
PNRP "bulutu", ağ üzerinden birbirleriyle iletişim kurabilen bir düğüm kümesini temsil eder. "Bulut" terimi "eş-eş örgü" ve "eşler arası grafik" ile eşanlamlıdır.  
  
 Düğümler arasındaki iletişim asla bir buluttan diğerine geçmemelidir. Bir <xref:System.Net.PeerToPeer.Cloud> örnek, büyük/küçük harf duyarlı olan adıyla benzersiz olarak tanımlanır. Tek bir eş veya düğüm birden fazla buluta bağlanabilir.  
  
 Bulutlar ağ arabirimlerine çok yakından bağlıdır.  Farklı alt ağlara bağlı iki ağ kartı bulunan çok yuvalı bir makinede, üç bulut döndürülür: arabirim başına bağlantı yerel adreslerinin her biri için bir tane ve tek bir küresel kapsam bulutu.  
  
 PNRP, kapsamın birbirini bulabilen bilgisayarların bir gruplandırması olduğu üç bulut "kapsamı" kullanır:  
  
- Küresel bulut, genel IPv6 adres kapsamına ve genel adreslere karşılık gelir ve tüm IPv6 Internet'teki tüm bilgisayarları temsil eder. Sadece tek bir küresel bulut var.  
  
- Bağlantı yerel bulutu, bağlantı yerel IPv6 adres kapsamı ve bağlantı yerel adreslerine karşılık gelir. Bağlantı yerel bulutu, genellikle yerel olarak bağlı alt ağla aynı olan belirli bir bağlantı içindir. Birden çok bağlantı yerel bulutlar olabilir.  
  
 Üçüncü bir bulut, siteye özgü bulut, site IPv6 adres kapsamı ve site yerel adresleri karşılık gelir. PNRP'de hala desteklenmiş olsa da, bu bulut amortismana kaldırıldı.  
  
## <a name="clouds"></a>Bulutlar  
 PNRP bulutları <xref:System.Net.PeerToPeer.Cloud> sınıfın örnekleriyle temsil edilir. Eş olarak kullanılan bulut grupları, sayısalsınıf <xref:System.Net.PeerToPeer.CloudCollection> örnekleriyle temsil edilir. Geçerli eş tarafından bilinen PNRP bulutlarının koleksiyonları statik <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> yöntem çağırılarak elde edilebilir.  
  
 Tek tek bulutların benzersiz adları vardır ve 256 karakterli Unicode dizesi olarak temsil edilir. Bu adlar, yukarıda belirtilen kapsamla birlikte, Bulut sınıfının benzersiz örneklerini oluşturmak için kullanılır. Bu örnekler seri hale getirilebilir ve kalıcı kullanım için yeniden oluşturulabilir.  
  
 Bir Bulut örneği oluşturulduktan veya elde edildikten sonra, bilinen eşlerden oluşan bir ağ oluşturmak için eş adları bu örnağa kaydedilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.Cloud>
- [Eş Adı Çözümleme Protokolü](peer-name-resolution-protocol.md)
