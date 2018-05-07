---
title: Güvenilir Hizmetler
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
ms.openlocfilehash: 02e0b8822c29490462fe74803a34222188afc910
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-services"></a>Güvenilir Hizmetler
Kuyruklar ve güvenilir oturumlar güvenilir Mesajlaşma uygulayan Windows Communication Foundation (WCF) özellikleridir. Bu konuda, güvenilir Mesajlaşma özellikleri açıklanmıştır [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 *Güvenilir Mesajlaşma* güvenilir Mesajlaşma kaynağı nasıl (adlı *kaynak*) aktarır iletileri güvenilir bir şekilde güvenilir bir ileti hedefine (adlı *hedef*).  
  
 Güvenilir Mesajlaşma aşağıdaki işlevleri gerçekleştirir:  
  
-   İleti aktarma veya taşıma hatalarının bakılmaksızın bir hedefe bir kaynaktan gönderilen iletiler için güvence aktarır.  
  
-   Kaynak ve hedef birbirinden ayırır. Kaynak veya hedef kullanılabilir olsa bile bu bağımsız hatası ve kaynak ve hedef aynı zamanda güvenilir aktarımı kurtarılması ve iletileri teslimini sağlar.  
  
 Güvenilir Mesajlaşma, yüksek gecikme sık gelir. *Gecikme süresi* iletisinin kaynaktan hedefe ulaşmak gereken süre anlamına gelmektedir. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], bu nedenle, güvenilir Mesajlaşma aşağıdaki türleri sağlar:  
  
-   [Güvenilir oturumlar](../../../docs/framework/wcf/feature-details/reliable-sessions.md), güvenilir aktarımı maliyeti yüksek gecikme olmadan sunar.  
  
-   [Wcf'de kuyruklar](../../../docs/framework/wcf/feature-details/queues-in-wcf.md), güvenilir aktarımları ve kaynak ve hedef arasında ayrım sağlar.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 Güvenilir oturumlar uçtan uca güvenilir iletileri arasında aktarımını bir kaynak ve sayı veya (kaynak ve hedef) Mesajlaşma uç noktaları ayrı aracılar türü ne olursa olsun WS-güvenilir Mesajlaşma protokolü kullanarak bir hedef belirtin. Bu SOAP (örneğin, HTTP proxy) kullanmayın herhangi aktarım aracılar içerir veya SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüleri) kullanan uç noktaları arasında akan iletileri için gerekli olan aracılar. Güvenilir oturumlar maskesi SOAP iletisi düzeyi hataları bellek içi aktarımı penceresine kullanın ve aktarım hatası durumunda yeniden bağlantı.  
  
 Güvenilir oturumlar, düşük gecikme süreli güvenilir ileti aktarımları sağlar. SOAP iletilerine için herhangi bir ara sunucuları veya aracılar sağladıkları, hangi TCP eşdeğer IP köprüleri paketler için sağlar. Güvenilir oturumlar hakkında daha fazla bilgi için bkz: [güvenilir oturumlar](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Kuyruklar  
 İçinde kuyruklar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] iletileri ve ayırma kaynakları ve yüksek gecikme, hedefler arasında güvenilir hem aktarımlarını sağlayın. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kuyruğa alınan iletişim Message Queuing (MSMQ en üstünde) yerleşik olarak bulunur.  
  
 MSMQ Windows ile isteğe bağlı bir bileşen olarak gelir. MSMQ hizmeti bir Windows hizmet olarak çalışır. İletim sırasındaki kaynak adına iletim iletileri yakalar ve bir hedef sıra sunar. Hedef iletileri istediğinde hedef sıra daha sonra gönderim için hedef adına iletileri kabul eder. Böylece iletiler iletim kayboluyor değil MSMQ yöneticilerini güvenilir ileti aktarım protokolünü kullanır. Protokol, yerel veya SOAP Güvenilir Mesajlaşma Protokolü (SRMP) adlı bir SOAP tabanlı Protokolü olabilir.  
  
 Kuyruklar arasında güvenilir ileti aktarımı ile bağlı ayırma, güvenilir bir şekilde iletişim kurmak için birbirine sıkı şekilde bağlı uygulamaları etkinleştirir. Güvenilir oturumlar farklı olarak, kaynak ve hedef aynı anda çalışıyor olması gerekmez. Bu örtülü olarak ileti üretim kaynağının oranını ve ileti tüketim hedef oranını eşleşmiyor burada sıraları yürürlükte, Yük Dengeleme mekanizması olarak kullanılan senaryolara olanak sağlar. Kuyruklar hakkında daha fazla bilgi için bkz: [wcf'de kuyruklar](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenilir Oturumlara Genel Bakış](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)  
 [WCF'de Kuyruğa Alma](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
