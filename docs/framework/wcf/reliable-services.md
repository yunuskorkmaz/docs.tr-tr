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
ms.openlocfilehash: 67da784646cd918d7ce4a269311eedb6abee5013
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651032"
---
# <a name="reliable-services"></a>Güvenilir Hizmetler
Kuyruklar ve güvenilir oturumlar güvenilir Mesajlaşma uygulayan Windows Communication Foundation (WCF) özellikleridir. Bu konu, WCF güvenilir Mesajlaşma özelliklerini açıklar.  
  
 *Güvenilir Mesajlaşma* güvenilir bir Mesajlaşma kaynağı nasıl (adlı *kaynak*) aktarır iletileri güvenilir bir şekilde güvenilir bir Mesajlaşma hedefe (adlı *hedef*).  
  
 Güvenilir Mesajlaşma aşağıdaki işlevleri gerçekleştirir:  
  
- Bir kaynaktan bir hedefe ileti aktarma veya taşıma hatalarından bağımsız olarak gönderilen iletiler için Güvenceleri aktarır.  
  
- Kaynak ve hedef birbirinden ayırır. Kaynak veya hedef kullanılabilir olsa bile bu bağımsız hatası ve kaynak ve hedef olarak güvenilir aktarım kurtarma ve ileti teslimini sağlar.  
  
 Güvenilir Mesajlaşma sık yüksek gecikme karşılığında sunulur. *Gecikme süresi* iletisinin kaynaktan hedefe ulaşmak gereken süre anlamına gelmektedir. WCF, bu nedenle, aşağıdaki türleri güvenilir Mesajlaşma sağlar:  
  
- [Güvenilir oturumlar](../../../docs/framework/wcf/feature-details/reliable-sessions.md), güvenilir aktarım gecikme süresi yüksek bir maliyet olmadan sunar.  
  
- [Wcf'de kuyruklar](../../../docs/framework/wcf/feature-details/queues-in-wcf.md), hem güvenilir aktarımları hem de kaynak ve hedef arasında ayrım sağlar.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 Güvenilir oturumlar uçtan uca güvenilir iletiler arasında aktarımı bir kaynak hem de sayı veya (kaynak ve hedef) Mesajlaşma uç noktaları ayrı aracılar türü ne olursa olsun WS-güvenilir Mesajlaşma protokolü kullanarak bir hedef sağlayın. Bu, SOAP (örneğin, HTTP proxy) kullanmayan herhangi bir aktarım aracılar içerir veya akış uç noktaları arasında iletileri için gerekli olan SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüler) kullanan aracılar. Güvenilir oturumlar maskesi SOAP ileti düzeyi hataları bir bellek içi aktarım penceresini kullanma ve aktarım hatası durumunda bağlantıları yeniden oluşturun.  
  
 Güvenilir oturumlar, düşük gecikmeli güvenilir ileti aktarımları sağlar. SOAP iletileri için herhangi bir ara sunucuları veya aracılar üzerinde sağlarlar, hangi TCP eşdeğer IP köprüleri paketleri için sağlar. Güvenilir oturumlar hakkında daha fazla bilgi için bkz: [güvenilir oturumlar](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Kuyruklar  
 Wcf'de kuyruklar, kaynaklar ve hedefler, yüksek gecikme süresi arasında iletileri ve ayırma hem güvenilir aktarımları sağlar. WCF kuyruğa alınan iletişim, Message Queuing (MSMQ en üstünde) oluşturulur.  
  
 MSMQ Windows ile isteğe bağlı bir bileşen olarak gelir. MSMQ hizmeti bir Windows hizmeti çalışır. İletim kaynak adına iletim kuyruktaki iletileri yakalar ve bir hedef kuyruğa gönderir. Hedef iletileri istediğinde hedef kuyruk iletileri için daha sonra gönderim hedefi adına kabul eder. Böylece iletiler iletim kaybolmaz MSMQ yöneticilerini güvenilir ileti aktarım protokolünü kullanır. Protokol, yerel veya SOAP Güvenilir Mesajlaşma Protokolü (SRMP) adlı bir SOAP tabanlı Protokolü olabilir.  
  
 Kuyruklar arasında güvenilir ileti aktarımları ile birlikte ayırma, güvenilir bir şekilde iletişim kurmak için gevşek uygulamalar sağlar. Güvenilir oturumlar, kaynak ve hedef aynı anda çalıştırılması gerekmez. Bu senaryo ileti üretim kaynağının oranını ve hedefin ileti tüketim oranı eşleşmiyor, kuyrukları aslında bir Yük Dengeleme mekanizması olarak kullanıldığı örtük olarak sağlar. Kuyruklar hakkında daha fazla bilgi için bkz: [wcf'de kuyruklar](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenilir Oturumlara Genel Bakış](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
- [WCF'de Kuyruğa Alma](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
