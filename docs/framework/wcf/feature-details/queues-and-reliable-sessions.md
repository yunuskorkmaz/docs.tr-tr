---
title: Kuyruklar ve Güvenilir Oturumlar
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: a60f409a0f5c237c372fe3303d67ef979950eab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494676"
---
# <a name="queues-and-reliable-sessions"></a>Kuyruklar ve Güvenilir Oturumlar
Kuyruklar ve güvenilir oturumlar güvenilir Mesajlaşma uygulayan Windows Communication Foundation (WCF) özellikleridir. Bu bölümdeki konular, WCF güvenilir Mesajlaşma ele alınmaktadır.  
  
 Güvenilir Mesajlaşma nasıl (kaynak olarak adlandırılır) güvenilir bir Mesajlaşma kaynağı iletileri güvenilir bir şekilde (hedef olarak adlandırılır) bir güvenilir Mesajlaşma hedefine aktarır olur.  
  
 Güvenilir Mesajlaşma aşağıdaki unsur vardır:  
  
-   Bir kaynaktan bir hedef ileti aktarma hatası veya aktarım hataları bağımsız olarak gönderilen iletileri çıkışların aktarın.  
  
-   Kaynak veya hedef kullanılamaz olmasına rağmen bağımsız hatası ve kaynak ve hedef kurtarma iyi olarak güvenilir aktarımı ve sağlayan iletileri teslimini ayrımı kaynak ve hedef her diğer.  
  
 Güvenilir Mesajlaşma, yüksek gecikme sık gelir. Gecikme iletisinin kaynaktan hedefe ulaşmak gereken süre anlamına gelmektedir. WCF, bu nedenle, güvenilir Mesajlaşma aşağıdaki türleri sağlar:  
  
-   [Güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), güvenilir aktarımı maliyeti yüksek gecikme olmadan sunma  
  
-   [Wcf'de kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), güvenilir aktarımları ve kaynak ve hedef arasında ayrım sağlar.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 Güvenilir oturumlar uçtan uca güvenilir iletileri arasında aktarımını bir kaynak ve sayı veya (kaynak ve hedef) Mesajlaşma uç noktaları ayrı aracılar türü ne olursa olsun WS-ReliableMessaging protokolünü kullanarak bir hedef belirtin. Bu SOAP (örneğin, HTTP proxy) kullanmayın herhangi aktarım aracılar içerir veya SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüleri) kullanan uç noktaları arasında akan iletileri için gerekli olan aracılar. Güvenilir oturumlar maskesi SOAP iletisi düzeyi hataları bellek içi aktarımı penceresine kullanın ve aktarım hatası durumunda yeniden bağlantı.  
  
 Güvenilir oturumlar, düşük gecikme süreli güvenilir ileti aktarımları sağlar. SOAP iletilerine için herhangi bir ara sunucuları veya aracılar sağladıkları, hangi TCP eşdeğer IP köprüleri paketler için sağlar. Güvenilir oturumlar hakkında daha fazla bilgi için bkz: [güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Kuyruklar  
 Wcf'de kuyruklar hem güvenilir aktarımlarını iletileri ve ayırma kaynakları ve yüksek gecikme, hedefler arasında sağlar. WCF kuyruğa alınan iletişim, Message Queuing üstünde (MSMQ olarak da bilinir) oluşturulur.  
  
 MSMQ bir NT hizmeti olarak çalışan Windows ile bir seçenek olarak geliyordu. İletim sırasındaki kaynak adına iletim iletileri yakalar ve bir hedef sıra sunar. Hedef iletileri istediğinde hedef sıra daha sonra gönderim için hedef adına iletileri kabul eder. Böylece iletiler iletim kayboluyor değil MSMQ sırası yöneticilerini güvenilir ileti aktarma protokolü kullanır. Protokol, yerel veya SOAP tabanlı gibi Soap güvenilir Mesajlaşma Protokolü (SRMP) olabilir.  
  
 Kuyruklar arasında güvenilir ileti aktarımı ile bağlı ayırma, güvenilir bir şekilde iletişim kurmak için birbirine sıkı şekilde bağlı uygulamaları etkinleştirir. Güvenilir oturumlar farklı olarak, kaynak ve hedef aynı anda çalışıyor olması gerekmez. Bu örtülü olarak kaynağı tarafından ileti üretim oranını ve hedef ileti tüketimi oranını arasında bir uyumsuzluk olduğunda sıraları yürürlükte, Yük Dengeleme mekanizması olarak kullanıldığı senaryolara olanak sağlar. Kuyruklar hakkında daha fazla bilgi için bkz: [wcf'de kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de Kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Güvenilir Oturumlara Genel Bakış](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
