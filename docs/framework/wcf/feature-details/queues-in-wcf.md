---
title: Windows Communication Foundation'da Kuyruklar
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: fbe3a546fd431beb5ddf1d71153d38580a19ecc9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348347"
---
# <a name="queues-in-windows-communication-foundation"></a>Windows Communication Foundation'da Kuyruklar
Bu bölümdeki konular, kuyruklar için Windows Communication Foundation (WCF) desteğini tartışır. WCF, bir taşıma olarak Microsoft Message Queuing (daha önce MSMQ olarak bilinir) kullanarak sıraya alma desteği sağlar ve aşağıdaki senaryoları sağlar:  
  
- Gevşek olarak bağlanmış uygulamalar. Uygulamaları göndermek, alıcı uygulamanın iletiyi işlemek için kullanılabilir olup olmadığını bilmeleri gerekmeden iletileri sıralara gönderebilir. Sıra, gönderen uygulamanın iletileri işlemeye ne kadar hızlı bir şekilde işleyebildiğini bağlı olmayan bir hızda sıraya ileti göndermesini sağlayan işleme bağımsızlık sağlar. Bir kuyruğa ileti gönderilirken genel sistem kullanılabilirliği artar ve ileti işlemeye sıkı bir şekilde bağlı değildir.  
  
- Hata yalıtımı. Bir kuyruğa ileti gönderen veya alan uygulamalar birbirini etkilemeden başarısız olabilir. Örneğin, alıcı uygulama başarısız olursa, gönderen uygulama iletileri kuyruğa göndermeye devam edebilir. Alıcı tekrar çalışır duruma geldiğinde iletileri kuyruktan işleyebilir. Hata yalıtımı genel sistem güvenilirliğini ve kullanılabilirliğini artırır.  
  
- Yük dengeleme. Uygulamaları göndermek, iletilerle birlikte uygulamaları alabilir. Kuyruklar, uyumsuz ileti üretimini ve tüketim hızlarını yönetebilir ve böylece bir alıcı aşırı olmaz.  
  
- Bağlantısı kesilen işlemler. Mobil cihazlarda olduğu gibi, yüksek gecikmeli ağlar veya sınırlı kullanılabilirlik ağları üzerinden iletişim kurulurken, gönderme, alma ve işleme işlemleri kesilebilir. Kuyruklar, uç noktaların bağlantısı kesildiğinde bile bu işlemlerin devam etmesine izin verir. Bağlantı yeniden kurulduğunda, kuyruk iletileri alıcı uygulamaya iletir.  
  
 Bir WCF uygulamasında kuyruklar özelliğini kullanmak için standart bağlamalardan birini kullanabilir veya standart bağlamalardan biri gereksinimlerinizi karşılamadığı takdirde özel bir bağlama oluşturabilirsiniz. İlgili standart bağlamalar ve bir tane seçme hakkında daha fazla bilgi için bkz. [nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamaları Ile Exchange iletileri](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Özel Bağlamalar Oluşturma hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Message Queuing kavramlarına genel bakış.  
  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 WCF kuyruğu desteğine genel bakış.  
  
 [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 WCF istemcisi ve WCF hizmeti arasında iletişim kurmak için <xref:System.ServiceModel.NetMsmqBinding> sınıfının nasıl kullanılacağını açıklar.  
  
 [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 WCF ve Message Queuing uygulamalar arasında iletişim kurmak için <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nasıl kullanılacağını açıklar.  
  
 [Oturumda Kuyruğa Alınmış İletileri Gruplandırma](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Tek bir alan uygulama tarafından bağıntılı ileti işlemeyi kolaylaştırmak için bir kuyruktaki iletilerin nasıl gruplandırılacağını açıklar.  
  
 [Bir İşlemde Toplu İleti İşleme](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Bir işlemdeki toplu iletileri nasıl kullanacağınızı açıklar.  
  
 [İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 İleti aktarımı ve teslim hatalarının, atılacak ileti kuyruklarını kullanarak nasıl işleneceğini ve atılacak ileti sırasından iletilerin nasıl işleneceğini açıklar.  
  
 [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Zarar iletilerinin nasıl işleneceğini açıklar (alıcı uygulamaya en fazla teslim girişimi sayısını aşmış olan mesajlar).  
  
 [Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Windows Vista, Windows Server 2003 ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]arasındaki WCF kuyrukları özelliğindeki farklılıkları özetler.  
  
 [Aktarım Güvenliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Sıraya alınan iletileri güvenli hale getirmek için Transport Security 'nin nasıl kullanılacağını açıklar.  
  
 [İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Sıraya alınan iletileri güvenli hale getirmek için ileti güvenliğinin nasıl kullanılacağını açıklar.  
  
 [Kuyruğa Alınan İletilerde Sorun Giderme](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Genel sıraya alma sorunlarını nasıl giderebileceğinizi açıklar.  
  
 [Kuyruğa Alınan İletişim için En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 WCF sıraya alınmış iletişimi kullanmak için en iyi yöntemleri açıklar.  
