---
title: Kuyruklar ve Güvenilir Oturumlar
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: af45fd86f673d0cc296f6593d9d5709d3e2b616e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596753"
---
# <a name="queues-and-reliable-sessions"></a>Kuyruklar ve Güvenilir Oturumlar
Kuyruklar ve güvenilir oturumlar, güvenilir mesajlaşma uygulayan Windows Communication Foundation (WCF) özelliklerdir. Bu bölümde yer alan konular, WCF güvenilir mesajlaşma özelliklerini tartışır.  
  
 Güvenilir Mesajlaşma, güvenilir bir mesajlaşma kaynağının (kaynak olarak adlandırılır) iletileri güvenilir bir mesajlaşma hedefine güvenilir bir şekilde nasıl aktardığını (hedef olarak adlandırılır) sağlar.  
  
 Güvenilir Mesajlaşma aşağıdaki önemli yönlere sahiptir:  
  
- İleti aktarım hatasından veya aktarım hatalarından bağımsız olarak bir kaynaktan hedefe gönderilen iletiler için ölçü aktarın.  
  
- Kaynağın ve hedefin bağımsız hatası ve kurtarılmasına ve kaynak ya da hedef kullanılamaz olsa bile iletilerin güvenilir bir şekilde aktarılmasına ve teslim edilmesini sağlayan kaynak ve hedefin birbirinden ayrılması.  
  
 Güvenilir Mesajlaşma genellikle yüksek gecikme süresine sahiptir. Gecikme süresi, iletinin kaynaktan hedefe ulaşması için gereken süredir. Bu nedenle, aşağıdaki güvenilir mesajlaşma türlerini sağlar:  
  
- Yüksek gecikme maliyeti olmadan güvenilir aktarım sağlayan [Güvenilir Oturumlar](reliable-sessions.md)  
  
- [WCF 'de](queues-in-wcf.md), kaynak ve hedef arasında hem güvenilir aktarımlar hem de ayrım sağlayan kuyruklar.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 Güvenilir Oturumlar, mesajlaşma (kaynak ve hedef) uç noktalarını ayıran aracıların sayısından veya türünden bağımsız olarak WS-ReliableMessaging protokolünü kullanarak bir kaynak ve hedef arasında iletilerin uçtan uca güvenli aktarılmasını sağlar. Bu, uç noktalar arasında akış yapmak için gereken SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüler) kullanan tüm aktarım aracıları (örneğin, HTTP proxy 'leri) veya aracıları kullanan aracılar içerir. Güvenilir Oturumlar, SOAP ileti düzeyindeki hataların maskesini belirlemek ve aktarım sorunları durumunda bağlantıları yeniden kurmak için bellek içi Aktarım penceresini kullanır.  
  
 Güvenilir Oturumlar, düşük gecikmeli güvenilir ileti aktarımları sağlar. Bunlar, IP köprüleri üzerinde paketlere yönelik olarak TCP 'nin sağladığı tüm proxy 'ler veya aracılar üzerinde SOAP iletileri sağlar. Güvenilir oturumlar hakkında daha fazla bilgi için bkz. [Güvenilir Oturumlar](reliable-sessions.md).  
  
## <a name="queues"></a>Kuyruklar  
 WCF 'de kuyruklar, yüksek gecikme maliyetinde kaynaklar ve hedefler arasında hem güvenilir ileti hem de ayrım sağlar. WCF sıraya alınan iletişim Message Queuing en üstünde (MSMQ olarak da bilinir) oluşturulur.  
  
 MSMQ, NT hizmeti olarak çalışan Windows 'a bir seçenek olarak gönderilir. İletim sırasındaki iletileri kaynak adına yakalar ve bir hedef kuyruğa gönderir. Hedef kuyruk, her ileti için hedef istediğinde, daha sonra teslimin adına iletileri kabul eder. MSMQ kuyruğu yöneticileri, iletilerin iletimde kaybedilmemesi için güvenilir bir ileti aktarımı Protokolü uygular. Protokol yerel veya SOAP tabanlı olabilir; örneğin SOAP Güvenilir Mesajlaşma Protokolü (SRMP).  
  
 Kuyruklar arasındaki güvenilir ileti aktarımları ile bağlanan ayrım, gevşek olarak bağlanmış uygulamaların güvenilir bir şekilde iletişim kurmasına olanak sağlar. Güvenilir oturumlardan farklı olarak, kaynak ve hedefin aynı anda çalışıyor olması gerekmez. Bu, sıranın, kaynak tarafından ileti üretimi ve hedef tarafından ileti tüketiminin oranı arasında uyuşmazlık olduğunda yük dengeleme mekanizması olarak kullanıldığı senaryolara açık bir şekilde izin verir. Kuyruklar hakkında daha fazla bilgi için bkz. [WCF 'de kuyruklar](queues-in-wcf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF'de Kuyruklar](queues-in-wcf.md)
- [WCF'de Kuyruğa Alma](queuing-in-wcf.md)
- [Güvenilir Oturumlar](reliable-sessions.md)
- [Güvenilir Oturumlar Genel Bakış](reliable-sessions-overview.md)
