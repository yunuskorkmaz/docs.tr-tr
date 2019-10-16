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
ms.openlocfilehash: 78f492c7a7c5abd7b72c40fc5695b8d56003f822
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319881"
---
# <a name="reliable-services"></a>Güvenilir Hizmetler
Kuyruklar ve güvenilir oturumlar, güvenilir mesajlaşma uygulayan Windows Communication Foundation (WCF) özelliklerdir. Bu konuda, WCF 'nin güvenilir mesajlaşma özellikleri açıklanmaktadır.  
  
 Güvenilir *mesajlaşma* , güvenilir bir mesajlaşma kaynağının ( *kaynak*olarak adlandırılır) iletileri güvenilir bir mesajlaşma hedefine güvenilir bir şekilde nasıl aktardığını ( *hedef*olarak adlandırılır) sağlar.  
  
 Güvenilir Mesajlaşma aşağıdaki işlevleri gerçekleştirir:  
  
- İleti aktarımı veya aktarım arızalarından bağımsız olarak bir kaynaktan hedefe gönderilen iletiler için asslıkları aktarır.  
  
- Kaynağı ve hedefi birbirinden ayırır. Bu, kaynağın ve hedefin bağımsız hata ve kurtarılmasına ve kaynak ya da hedef kullanılamadığında bile iletilerin güvenilir bir şekilde aktarılmasına ve teslimini sağlar.  
  
 Güvenilir Mesajlaşma genellikle yüksek gecikme süresine sahiptir. *Gecikme süresi* , iletinin kaynaktan hedefe ulaşması için gereken süredir. Bu nedenle, aşağıdaki güvenilir mesajlaşma türlerini sağlar:  
  
- Yüksek gecikme maliyeti olmadan güvenilir aktarım sağlayan [Güvenilir Oturumlar](./feature-details/reliable-sessions.md).  
  
- [WCF 'de](./feature-details/queues-in-wcf.md), kaynak ve hedef arasında hem güvenilir aktarımlar hem de ayrım sağlayan kuyruklar.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 Güvenilir Oturumlar, mesajlaşma (kaynak ve hedef) uç noktalarını ayıran aracıların sayısından veya türünden bağımsız olarak, WS-güvenilir mesajlaşma protokolünü kullanarak bir kaynak ve hedef arasında iletilerin uçtan uca güvenli aktarılmasını sağlar. Bu, uç noktalar arasında akış yapmak için gereken SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüler) kullanan tüm aktarım aracıları (örneğin, HTTP proxy 'leri) veya aracıları kullanan aracılar içerir. Güvenilir Oturumlar, SOAP ileti düzeyindeki hataların maskesini belirlemek ve aktarım sorunları durumunda bağlantıları yeniden kurmak için bellek içi Aktarım penceresini kullanır.  
  
 Güvenilir Oturumlar, düşük gecikmeli güvenilir ileti aktarımları sağlar. Bunlar, IP köprüleri üzerinde paketlere yönelik olarak TCP 'nin sağladığı tüm proxy 'ler veya aracılar üzerinde SOAP iletileri sağlar. Güvenilir oturumlar hakkında daha fazla bilgi için bkz. [Güvenilir Oturumlar](./feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Kuyruklar  
 WCF 'de kuyruklar, yüksek gecikme maliyetinde kaynaklar ve hedefler arasında hem güvenilir ileti hem de ayrım sağlar. WCF sıraya alınan iletişim Message Queuing (MSMQ) üzerinde oluşturulmuştur.  
  
 MSMQ, Windows ile isteğe bağlı bir bileşen olarak gelir. MSMQ hizmeti bir Windows hizmeti olarak çalışır. İletim sırasındaki iletileri kaynak adına yakalar ve bir hedef kuyruğa gönderir. Hedef sıra, hedef her ileti istediğinde, daha sonra teslim için hedef adına iletileri kabul eder. MSMQ yöneticileri, iletilerin iletimde kaybedilmemesi için güvenilir bir ileti aktarımı Protokolü uygular. Protokol yerel veya SOAP ile güvenilir mesajlaşma Protokolü (SRMP) adlı SOAP tabanlı bir protokol olabilir.  
  
 Kuyruklar arasındaki güvenilir ileti aktarımları ile bağlanan ayrım, gevşek olarak bağlanmış uygulamaların güvenilir bir şekilde iletişim kurmasına olanak sağlar. Güvenilir oturumlardan farklı olarak, kaynak ve hedefin aynı anda çalışıyor olması gerekmez. Bu, sıranın ileti üretimi ve hedefin ileti tüketiminin oranı eşleşmediği zaman bir yük dengeleme mekanizması olarak kullanıldığı, sıranın etkin olduğu senaryolara açık olarak izin verir. Kuyruklar hakkında daha fazla bilgi için bkz. [WCF 'de kuyruklar](./feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenilir Oturumlara Genel Bakış](./feature-details/reliable-sessions-overview.md)
- [WCF'de Kuyruğa Alma](./feature-details/queuing-in-wcf.md)
