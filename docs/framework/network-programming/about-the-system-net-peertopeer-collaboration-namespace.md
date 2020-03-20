---
title: System.Net.PeerToPeer.Collaboration Ad Alanı Hakkında
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
ms.openlocfilehash: f0c9ecaacc1d875aac8eed61a85ca7579f5cb8a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64649519"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>System.Net.PeerToPeer.Collaboration Ad Alanı Hakkında
Ad <xref:System.Net.PeerToPeer.Collaboration> alanı, Eşler Arası İşbirliği Altyapısını kullanarak eşler arası işbirliği etkinliklerini uygulamak için kullanılan sınıflar ve API'ler sağlar.  
  
## <a name="classes"></a>Sınıflar  
 Eşler Arası İşbirliği etkinliğinin uygulanmasında kullanılan ana sınıflar şunlardır:  
  
- Eş <xref:System.Net.PeerToPeer.Collaboration.ContactManager>kişileri depolamak için kullanılabilir.  
  
- <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> Oyun, sohbet istemcisi veya konferans çözümü gibi işbirliği yapmak için.  
  
- Bir etkinlikte işbirliği yapacak eşler.  Bu eşler , <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>veya <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> nesneler olarak temsil edilebilir.  
  
- Hangi <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> uygulamaların kullanılabilir olduğunu ve hangi eşlerin bunlara katıldığını belirten statik sınıfın kendisi.  
  
 Yöntemler, <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> eşarkadaşlarını bir işbirliği oturumuna davet etmek için kullanılır.  Çağrı eş, işbirliği oturumuna bağlı uygulama, nesne veya durum bilgilerine sinyal veren olaylar için başka bir eşe abone olabilir. Durum sınıfları, <xref:System.Net.PeerToPeer.Collaboration.Peer> bir eş için <xref:System.Net.PeerToPeer.Collaboration.PeerScope> ne kadar katılıma izin verildiğini belirtmek için <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> bir <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>a'nın kullanılabilir <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>olup olmadığını belirtir: (genel), (alt ağ) veya .  
  
 Bir işbirliği oturumu dört adımdan oluşur:  
  
- Keşif. Uygulamaları, eşleri ve durum bilgilerini keşfedin veya yayımlayın.  Örneğin, yerel alt ağda aynı oyunları yüklü olan diğer kişileri bulun.  
  
- Davet. <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> Oturumları başlatmak veya katılmak için uzak eşler için güvenli davetiyeler gönderin ve kabul edin.  
  
- İletişim Yönetimi. Keşfedilen eşleri bir <xref:System.Net.PeerToPeer.Collaboration.ContactManager>kişi olarak ekleyin.  
  
- Iletişim. İletişim kurulduğunda, çok <xref:System.Net> taraflı iletişim <xref:System.Net.PeerToPeer> için API'leri, API'yi veya Windows Communication Foundation Peer Channel sınıflarını kullanın.  
  
 Örneğin, ana bilgisayar eş bir işbirliği oturumu <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> başlatır ve uzak bir eş ve yerel eşlerinden birini ana bilgisayar eşin Kişi Yöneticisi'ne eklemek için yöntemi kullanır.  Üç kullanıcı daha sonra kendi özel işbirliği oturumuna katılacaktır.  
  
 Tipik P2P uygulamaları şunlardır: ortak not alma veya beyaz tahta, sunucusuz sohbet uygulamaları, etkileşimli reklamlar ve çevrimiçi oyun oturumları için konferans çağrıları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.Collaboration>
