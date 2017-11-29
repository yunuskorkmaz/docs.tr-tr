---
title: Windows Communication Foundation'da Kuyruklar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 279f6094b7e41549a285ac0175c3f949f9d8e7e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="queues-in-windows-communication-foundation"></a>Windows Communication Foundation'da Kuyruklar
Bu bölümdeki konular ele [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] desteklemek için sıralar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir taşıma olarak (daha önce MSMQ da bilinir) Microsoft Message Queuing yararlanarak queuing için destek sağlar ve aşağıdaki senaryolara olanak sağlar:  
  
-   Gevşek bağlı uygulamalar. Gönderen uygulamaların, sıraya alma işlemini yapan uygulamanın iletiyi işlemek kullanılabilir olup olmadığını bilmenize gerek olmadan iletileri gönderebilir. Sıranın kuyruğa alma uygulamaları iletileri ne kadar hızlı işleyebilir bağlı olmayan bir hızda iletileri göndermek gönderen bir uygulama sağlar işleme bağımsızlığı sağlar. Kuyruğa ileti gönderme sıkı bir şekilde ileti işleme değil birleştirildiğinde genel sistem kullanılabilirliğini artırır.  
  
-   Hata Yalıtımı. Gönderme veya ileti kuyruğa alma uygulamaları birbirine etkilemeden başarısız olabilir. Örneğin, alıcı uygulama başarısız olursa, gönderen uygulama kuyruğa ileti göndermek devam edebilirsiniz. Alıcı yukarı yeniden olduğunda, sıraya alınan iletileri işleyebilir. Hata yalıtım kullanılabilirlik ve genel sistem güvenilirliğini artırır.  
  
-   Yük Dengeleme. Gönderen uygulamaların iletilerle alıcı uygulamalar doldurmaya. Bir alıcı kısası olmaması sıraları eşleşmeyen ileti üretim ve tüketim hızları yönetebilirsiniz.  
  
-   Bağlantısı kesilmiş işlemleri. Gönderme, alma ve işlemlerinde gibi yüksek Gecikmeli ağlarda veya sınırlı kullanılabilirlik, mobil cihazlar söz konusu olduğunda iletişim kurarken kaybedebilir. Kuyruklar devam etmek bile zaman uç noktalar bağlantısı kesilen bu işlemler sağlar. Bağlantı kurulduğunda, sıraya alma işlemini yapan uygulamanın iletileri iletir.  
  
 Kuyruklar özelliğini kullanmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama standart bağlamaları birini kullanabilirsiniz veya standart bağlamaları biri, gereksinimlerinize uygun değil, özel bir bağlama oluşturabilirsiniz. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ilgili standart bağlamalar ve bir seçim yapma bkz [nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamaları ile Exchange iletileri](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özel bağlama oluşturma, bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Kuyruklar genel bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Message queuing kavramları genel bakış.  
  
 [WCF'de kuyruğa alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Genel bir bakış [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sıraya desteği.  
  
 [Nasıl yapılır: WCF uç noktaları iletileri kuyruğa alınan](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Nasıl kullanılacağı açıklanmaktadır <xref:System.ServiceModel.NetMsmqBinding> arasında iletişim kurmak için sınıf bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 [Nasıl yapılır: WCF uç noktaları iletileri Exchange ve Message Queuing uygulamaları](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Nasıl kullanılacağı açıklanmaktadır <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> arasında iletişim kurmak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve Message Queuing uygulamaları.  
  
 [Kuyruğa alınmış iletileri bir oturumda gruplandırma](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Tek bir alıcı uygulamayla ilişkili ileti işleme kolaylaştırmak için bir sıradaki iletiler Grup açıklanmaktadır.  
  
 [Bir işlemde toplu ileti işleme](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 İletileri bir işlemde toplu açıklanmaktadır.  
  
 [İleti aktarımı hatalarını işlemek için teslim edilemeyen iletiler sırası kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Teslim edilemeyen iletiler sırası kullanma ileti aktarımı ve teslimat hatalarının nasıl ele alınacağını ve sahipsiz sıraya alınan iletileri işlemek nasıl açıklanmaktadır.  
  
 [Zehirli ileti işleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Zehirli ileti (teslim alma işlemini yapan uygulamanın girişimleri üst sınırını aştınız iletileri) nasıl ele alınacağını açıklar.  
  
 [Windows Vista, Windows Server 2003 ve Windows XP'de kuyruğa alma özelliği farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Farkları özetler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sıraları özellik arasında [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Taşıma Güveliği kullanarak iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Taşıma güvenliği sıraya alınan iletileri güvenli hale getirmek için nasıl kullanılacağını açıklar.  
  
 [İleti Güveliği kullanarak iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 İleti güvenliği sıraya alınan iletileri güvenli hale getirmek için nasıl kullanılacağını açıklar.  
  
 [Kuyruğa Alınan iletilerde sorun giderme](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Genel sıraya alma sorunlarının nasıl giderileceği açıklanmaktadır.  
  
 [Kuyruğa alınan iletişim için en iyi yöntemler](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Kullanmak için en iyi uygulamalar açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kuyruğa alınmış iletişim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Message Queuing](http://msdn.microsoft.com/en-us/ff917e87-05d5-478f-9430-0f560675ece1)
