---
description: 'Hakkında daha fazla bilgi edinin: System .net. PeerToPeer. Işbirliği ad alanı hakkında'
title: System.Net.PeerToPeer.Collaboration Ad Alanı Hakkında
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
ms.openlocfilehash: cb51208b2424b93e963101943652c57f0266baf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801923"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>System.Net.PeerToPeer.Collaboration Ad Alanı Hakkında

<xref:System.Net.PeerToPeer.Collaboration>Ad alanı, eşler arası Işbirliği altyapısını kullanarak eş işbirliği etkinliklerini uygulamak için kullanılan sınıfları ve API 'leri sağlar.  
  
## <a name="classes"></a>Sınıflar  

 Eşler arası Işbirliği etkinliğinin uygulamasında kullanılan ana sınıflar şunlardır:  
  
- <xref:System.Net.PeerToPeer.Collaboration.ContactManager>Eş kişilerini depolamak için kullanılabilecek.  
  
- <xref:System.Net.PeerToPeer.Collaboration.PeerApplication>Oyun, sohbet istemcisi veya konferans çözümü gibi işbirliği yapılacak.  
  
- Bir etkinlikte işbirliği yapılacak Peers.  Bu Peers <xref:System.Net.PeerToPeer.Collaboration.PeerContact> , veya nesneleri olarak temsil edilebilir <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe> <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> .  
  
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration>Hangi uygulamaların kullanılabilir olduğunu ve bunlara hangi eşlerin katıldığı belirten statik sınıfın kendisi.  
  
 Bu <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> Yöntemler, eşleri bir işbirliği oturumuna davet etmek için kullanılır.  Bir arama eşi, uygulama, nesne veya işbirliği oturumuyla ilişkili olan varlık bilgilerine yönelik güncelleştirmeleri gösteren olaylar için başka bir eşe abone olabilir. Varlık sınıfları bir <xref:System.Net.PeerToPeer.Collaboration.Peer> iş birliği için kullanılabilir olup olmadığını belirtir ve bir <xref:System.Net.PeerToPeer.Collaboration.PeerScope> eş için ne kadar katılım izin verileceğini belirtmek için sınıfı kullanılır:  <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (genel), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe> , (alt ağ) veya <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None> .  
  
 İşbirliği oturumu dört adımdan oluşur:  
  
- Keşif. Uygulamaları, eşleri ve varlık bilgilerini bulun veya yayımlayın.  Örneğin, yerel alt ağda aynı oyunları yüklemiş olan diğer kişileri bulun.  
  
- Esinin. Oturumları başlatmak veya birleştirmek için uzak eşler için güvenli davetleri gönderin ve kabul edin <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> .  
  
- İletişim yönetimi. Bulunan eşleri bir kişi olarak öğesine ekleyin <xref:System.Net.PeerToPeer.Collaboration.ContactManager> .  
  
- Kurulan. İletişim oluşturulduğunda, <xref:System.Net> <xref:System.Net.PeerToPeer> çok taraflı iletişimler için API 'leri, API 'yi veya Windows Communication Foundation Eş kanal sınıflarını kullanın.  
  
 Örneğin, ana bilgisayar eşi bir işbirliği oturumu başlatır ve bir <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> uzak eş ve yerel eşlerinden birini, konak eşinin Ilgili kişi yöneticisine eklemek için yöntemini kullanır.  Bu üç Kullanıcı daha sonra kendi özel işbirliği oturumuna katılabilir.  
  
 Tipik P2P uygulamaları şunlardır: işbirliğine dayalı tanıtım veya beyaz taslak, sunucusuz sohbet uygulamaları, etkileşimli tanıtımlar ve çevrimiçi oyun oturumları için konferans çağrıları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.Collaboration>
