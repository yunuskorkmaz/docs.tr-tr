---
title: "Kuyruklar ve Güvenilir Oturumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9a78bab9f7c4af23cf01c44e1d22a41a87a96f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="queues-and-reliable-sessions"></a>Kuyruklar ve Güvenilir Oturumlar
Kuyruklar ve güvenilir oturumlar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenilir Mesajlaşma uygulamak özellikleri. Bu bölümde yer alan konuları ele [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma özellikleri.  
  
 Güvenilir Mesajlaşma nasıl (kaynak olarak adlandırılır) güvenilir bir Mesajlaşma kaynağı iletileri güvenilir bir şekilde (hedef olarak adlandırılır) bir güvenilir Mesajlaşma hedefine aktarır olur.  
  
 Güvenilir Mesajlaşma aşağıdaki unsur vardır:  
  
-   Bir kaynaktan bir hedef ileti aktarma hatası veya aktarım hataları bağımsız olarak gönderilen iletileri çıkışların aktarın.  
  
-   Kaynak veya hedef kullanılamaz olmasına rağmen bağımsız hatası ve kaynak ve hedef kurtarma iyi olarak güvenilir aktarımı ve sağlayan iletileri teslimini ayrımı kaynak ve hedef her diğer.  
  
 Güvenilir Mesajlaşma, yüksek gecikme sık gelir. Gecikme iletisinin kaynaktan hedefe ulaşmak gereken süre anlamına gelmektedir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bu nedenle, güvenilir Mesajlaşma aşağıdaki türleri sağlar:  
  
-   [Güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), güvenilir aktarımı maliyeti yüksek gecikme olmadan sunma  
  
-   [Wcf'de kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), güvenilir aktarımları ve kaynak ve hedef arasında ayrım sağlar.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 Güvenilir oturumlar uçtan uca güvenilir iletileri arasında aktarımını bir kaynak ve sayı veya (kaynak ve hedef) Mesajlaşma uç noktaları ayrı aracılar türü ne olursa olsun WS-ReliableMessaging protokolünü kullanarak bir hedef belirtin. Bu SOAP (örneğin, HTTP proxy) kullanmayın herhangi aktarım aracılar içerir veya SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüleri) kullanan uç noktaları arasında akan iletileri için gerekli olan aracılar. Güvenilir oturumlar maskesi SOAP iletisi düzeyi hataları bellek içi aktarımı penceresine kullanın ve aktarım hatası durumunda yeniden bağlantı.  
  
 Güvenilir oturumlar, düşük gecikme süreli güvenilir ileti aktarımları sağlar. SOAP iletilerine için herhangi bir ara sunucuları veya aracılar sağladıkları, hangi TCP eşdeğer IP köprüleri paketler için sağlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]güvenilir oturumlar bkz [güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Kuyruklar  
 İçinde kuyruklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletileri ve ayırma kaynakları ve yüksek gecikme, hedefler arasında güvenilir hem aktarımlarını sağlayın. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Message Queuing üstünde (MSMQ olarak da bilinir) kuyruğa alınan iletişim kurulur.  
  
 MSMQ bir NT hizmeti olarak çalışan Windows ile bir seçenek olarak geliyordu. İletim sırasındaki kaynak adına iletim iletileri yakalar ve bir hedef sıra sunar. Hedef iletileri istediğinde hedef sıra daha sonra gönderim için hedef adına iletileri kabul eder. Böylece iletiler iletim kayboluyor değil MSMQ sırası yöneticilerini güvenilir ileti aktarma protokolü kullanır. Protokol, yerel veya SOAP tabanlı gibi Soap güvenilir Mesajlaşma Protokolü (SRMP) olabilir.  
  
 Kuyruklar arasında güvenilir ileti aktarımı ile bağlı ayırma, güvenilir bir şekilde iletişim kurmak için birbirine sıkı şekilde bağlı uygulamaları etkinleştirir. Güvenilir oturumlar farklı olarak, kaynak ve hedef aynı anda çalışıyor olması gerekmez. Bu örtülü olarak kaynağı tarafından ileti üretim oranını ve hedef ileti tüketimi oranını arasında bir uyumsuzluk olduğunda sıraları yürürlükte, Yük Dengeleme mekanizması olarak kullanıldığı senaryolara olanak sağlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Kuyruklar, bkz: [wcf'de kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de Kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Güvenilir Oturumlara Genel Bakış](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
