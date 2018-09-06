---
title: Windows Communication Foundation'da Kuyruklar
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: 46d70a0b0ccc33755666867240be8778b5638947
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858375"
---
# <a name="queues-in-windows-communication-foundation"></a>Windows Communication Foundation'da Kuyruklar
Bu bölümdeki konular, kuyruklar için Windows Communication Foundation (WCF) desteği açıklanmaktadır. WCF yararlanarak Microsoft Message (daha önce MSMQ da bilinir) Queuing tarafından bir aktarım olarak queuing için destek sağlar ve aşağıdaki senaryolara olanak tanır:  
  
-   Gevşek bağlantılı uygulamalar. Gönderen uygulamaların, kuyruklara alıcı uygulamanın iletiyi işlemek kullanılabilir olup olmadığını bilmek gerek kalmadan iletileri gönderebilir. Kuyruğa alma uygulamaları iletileri ne kadar hızlı işleyebilir bağlı olmayan bir hızda kuyruğa ileti göndermek bir gönderme uygulaması sağlayan işleme bağımsızlığı sağlar. Bir kuyruğa ileti göndermek için ileti işleme sıkıca değil, genel sistem kullanılabilirliği artırır.  
  
-   Hata Yalıtımı. Gönderme ve ileti kuyruğa alma uygulamaları birbirini etkilemeden başarısız olabilir. Örneğin, alıcı uygulama başarısız olursa, kuyruğa ileti göndermek uygulama göndermeye devam edebilirsiniz. Alıcı yeniden sakınca yoktur, bu kuyruktan iletileri işleyebilir. Hata yalıtımı, genel sistem güvenilirliğini ve kullanılabilirliğini artırır.  
  
-   Yük Dengeleme. Gönderen uygulamaların alma uygulamaları ile ileti sık zora sokar. Bir alıcı kısası olmaması eşleşmeyen ileti üretim ve tüketim ücretleri kuyruklar yönetebilirsiniz.  
  
-   Bağlantısı kesilmiş işlemler. Gönderme, alma ve işleme gibi yüksek Gecikmeli ağlar veya sınırlı kullanılabilirlik ağlar üzerinden mobil cihazlar söz konusu olduğunda iletişim kaybedebilir. Kuyruklar, bu işlemler devam etmek bile uç noktaları ne zaman kesilir izin verin. Bağlantı kurulduğunda, alıcı uygulamasına iletileri kuyruğa gönderir.  
  
 WCF uygulaması kuyrukları özelliği kullanmak için standart bağlamaları birini kullanabilirsiniz veya standart bağlamaları birini gereksinimlerinize uygun değil, özel bir bağlama oluşturabilirsiniz. İlgili standart bağlamaları ve bir seçim yapma hakkında daha fazla bilgi için bkz: [nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamaları ile Exchange ileti](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Özel bağlamalar oluşturma hakkında daha fazla bilgi için bkz. [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Message queuing kavramları genel bakış.  
  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 WCF kuyruk desteğine genel bakış.  
  
 [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Nasıl kullanılacağını açıklar <xref:System.ServiceModel.NetMsmqBinding> bir WCF istemcisi ve WCF hizmeti arasında iletişim kurmak için sınıf.  
  
 [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Nasıl kullanılacağını açıklar <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> WCF ve Message Queuing uygulamalar arasında iletişim kurmak için.  
  
 [Oturumda Kuyruğa Alınmış İletileri Gruplandırma](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Tek bir alıcı uygulamayla ilişkili ileti işleme kolaylaştırmak için sıradaki iletilerin Grup açıklanmaktadır.  
  
 [Bir İşlemde Toplu İleti İşleme](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Toplu işlem iletileri açıklanmaktadır.  
  
 [İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Teslim edilemeyen kullanarak ileti aktarım ve teslim hatalarını işlemek nasıl ve geçerliliğini yitirmiş kuyruk gelen iletileri işlemek nasıl açıklar.  
  
 [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Zehirli iletileri (alıcı uygulamasına teslim denemesi üst sınırını aştınız iletileri) ele alınacağını açıklar.  
  
 [Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 WCF kuyrukları özelliği farklar özetlenmektedir [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Aktarım Güvenliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Sıraya alınan iletileri güvenli hale getirmek için Aktarım güvenliği kullanmayı açıklar.  
  
 [İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Sıraya alınan iletileri güvenli hale getirmek için ileti güvenliği kullanmayı açıklar.  
  
 [Kuyruğa Alınan İletilerde Sorun Giderme](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Ortak kuyruk sorunları gidermek nasıl açıklar.  
  
 [Kuyruğa Alınan İletişim için En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Kuyruğa alınmış iletişim WCF kullanmak için en iyi uygulamalar açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Message Queuing](https://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)
