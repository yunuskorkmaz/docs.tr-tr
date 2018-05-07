---
title: System.Net.PeerToPeer.Collaboration Namespace hakkında
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5d23fe51249df53b3874a8fd6fda60377f7366ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>System.Net.PeerToPeer.Collaboration Namespace hakkında
<xref:System.Net.PeerToPeer.Collaboration> Ad alanı, sınıflar ve eşler arası işbirliği altyapısı kullanarak eş işbirliği etkinlikleri uygulamak için kullanılan API'ler sağlar.  
  
## <a name="classes"></a>Sınıflar  
 Bir eşler arası işbirliği etkinlik uygulamasında kullanılan ana sınıfları şunlardır:  
  
-   <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, Eş kişileri depolamak için kullanılabilir.  
  
-   <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> , Oyun, sohbet istemcisi veya konferans çözüm gibi işbirliği yapmak üzere.  
  
-   Bir etkinlik işbirliği eşler.  Bu eşlerden olarak temsil edilebilir <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, veya <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> nesneleri.  
  
-   Statik <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> sınıfının kendisini hangi uygulamaların kullanılabilir olduğunu belirtir ve hangi eşlerin katılmasını bunları.  
  
 <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> Yöntemleri işbirliği oturumunu eşlere davet etmek için kullanılır.  Bir arama eş başka bir eşler arası uygulama, nesne veya iletişim durumu bilgilerini sinyal güncelleştirmeleri işbirliği oturumla bağlı olaylar için abone olabilirsiniz. Varlığı sınıflar belirtin olup bir <xref:System.Net.PeerToPeer.Collaboration.Peer> işbirliği için kullanılabilir ve <xref:System.Net.PeerToPeer.Collaboration.PeerScope> sınıfı bir eş için ne kadar katılım izin verildiğini belirtmek için kullanılır: <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (Genel) <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (alt ağ) veya <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.  
  
 İşbirliği oturumunu dört adımdan oluşur:  
  
-   Bulma. Bul veya uygulamalar, eşlerdeki ve iletişim durumu bilgilerini yayımlayın.  Örneğin, aynı oyunlar yüklü olan diğer kişiler yerel alt ağda bulun.  
  
-   Davet. Gönderme ve Başlat veya katılmak uzak peer(s) için güvenli davetlerini kabul <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> oturumları.  
  
-   Yönetim başvurun. Bir kişiye olarak keşfedilen eş eklemek bir <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.  
  
-   İletişim. İletişimi kurulduğunda kullanmak <xref:System.Net> API'leri, <xref:System.Net.PeerToPeer> API ya da çok taraflı iletişimler için Windows Communication Foundation eş kanalı sınıfları.  
  
 Örneğin, ana bilgisayar eş işbirliği oturumu başlatır ve yararlanan <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> uzaktaki bir eş ve yerel eşlerine birini konak eş Contact Manager'a ekleme yöntemi.  Üç kullanıcı daha sonra kendi özel işbirliği oturumunda almayacak.  
  
 Tipik P2P uygulamalar: konferans aramaları işbirliği not alma ya da whiteboarding, sunucusuz sohbet uygulamalar, etkileşimli reklamlar ve çevrimiçi oyunlar oturumları için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer.Collaboration>
