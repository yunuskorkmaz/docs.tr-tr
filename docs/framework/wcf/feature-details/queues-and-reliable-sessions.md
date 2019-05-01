---
title: Kuyruklar ve Güvenilir Oturumlar
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: 1fb7d7db36aa51c63789b6daf0ac3689c87ace5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946698"
---
# <a name="queues-and-reliable-sessions"></a>Kuyruklar ve Güvenilir Oturumlar
Kuyruklar ve güvenilir oturumlar güvenilir Mesajlaşma uygulayan Windows Communication Foundation (WCF) özellikleridir. Bu bölümdeki konular, WCF güvenilir Mesajlaşma ele alınmaktadır.  
  
 Güvenilir Mesajlaşma hizmeti nasıl (kaynak olarak adlandırılır) güvenilir bir Mesajlaşma kaynak iletileri güvenilir bir şekilde (hedef olarak adlandırılır) bir güvenilir Mesajlaşma hedefe aktarır.  
  
 Güvenilir Mesajlaşma aşağıdaki önemli noktalar vardır:  
  
- Bir kaynaktan bir hedefe ileti aktarım hatası veya aktarım hataları bağımsız olarak gönderilen iletiler için Güvenceleri aktarın.  
  
- Kaynak veya hedef kullanılamaz durumda olsa da bağımsız hatası ve kaynak ve hedef kurtarma iyi şekilde güvenilir aktarım ve sağlayan iletileri teslim ayrılması, kaynak ve hedef her diğer.  
  
 Güvenilir Mesajlaşma sık yüksek gecikme karşılığında sunulur. Gecikme süresi kaynaktan hedefe ulaşmak ileti geçen süredir. WCF, bu nedenle, aşağıdaki türleri güvenilir Mesajlaşma sağlar:  
  
- [Güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), güvenilir aktarım gecikme süresi yüksek bir maliyet olmadan sunar  
  
- [Wcf'de kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), hem güvenilir aktarımları hem de kaynak ve hedef arasında ayrım sağlar.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 Güvenilir oturumlar arasında bir kaynak ve hedef sayısı veya türü (kaynak ve hedef) Mesajlaşma uç noktaları ayrı aracılar bağımsız olarak WS-ReliableMessaging protokolünü kullanarak uçtan uca güvenilir aktarım ileti sağlayın. Bu, SOAP (örneğin, HTTP proxy) kullanmayan herhangi bir aktarım aracılar içerir veya akış uç noktaları arasında iletileri için gerekli olan SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüler) kullanan aracılar. Güvenilir oturumlar maskesi SOAP ileti düzeyi hataları bir bellek içi aktarım penceresini kullanma ve aktarım hatası durumunda bağlantıları yeniden oluşturun.  
  
 Güvenilir oturumlar, düşük gecikmeli güvenilir ileti aktarımları sağlar. SOAP iletileri için herhangi bir ara sunucuları veya aracılar üzerinde sağlarlar, hangi TCP eşdeğer IP köprüleri paketleri için sağlar. Güvenilir oturumlar hakkında daha fazla bilgi için bkz: [güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Kuyruklar  
 Wcf'de kuyruklar, kaynaklar ve hedefler, yüksek gecikme süresi arasında iletileri ve ayırma hem güvenilir aktarımları sağlar. WCF kuyruğa alınan iletişim, Message Queuing en üstünde (MSMQ olarak da bilinir) oluşturulur.  
  
 MSMQ bir NT hizmeti olarak çalışan Windows ile bir seçenek olarak sevk edilir. İletim kaynak adına iletim kuyruktaki iletileri yakalar ve bir hedef kuyruğa gönderir. Hedef iletileri istediğinde hedef sıra adına daha sonra gönderim için hedef iletileri kabul eder. Böylece iletiler iletim kaybolmaz MSMQ sırası yöneticilerini güvenilir ileti aktarım protokolü kullanır. Protokol, yerel veya SOAP tabanlı gibi Soap güvenilir Mesajlaşma Protokolü (SRMP) olabilir.  
  
 Kuyruklar arasında güvenilir ileti aktarımları ile birlikte ayırma, güvenilir bir şekilde iletişim kurmak için gevşek uygulamalar sağlar. Güvenilir oturumlar, kaynak ve hedef aynı anda çalıştırılması gerekmez. Bu senaryo ileti üretim kaynağı tarafından oranını ve hedef iletiyi tüketimi oranını arasında bir uyuşmazlık olduğunda kuyrukları aslında bir Yük Dengeleme mekanizması olarak kullanıldığı örtük olarak sağlar. Kuyruklar hakkında daha fazla bilgi için bkz: [wcf'de kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF'de Kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
- [Güvenilir Oturumlara Genel Bakış](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
