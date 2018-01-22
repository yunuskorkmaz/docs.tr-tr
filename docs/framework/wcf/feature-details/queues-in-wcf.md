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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dfc78d355db4bd8c9d43541545e6fac35086b39
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="queues-in-windows-communication-foundation"></a>Windows Communication Foundation'da Kuyruklar
Bu bölümdeki konular ele [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] desteklemek için sıralar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir taşıma olarak (daha önce MSMQ da bilinir) Microsoft Message Queuing yararlanarak queuing için destek sağlar ve aşağıdaki senaryolara olanak sağlar:  
  
-   Gevşek bağlı uygulamalar. Gönderen uygulamaların, sıraya alma işlemini yapan uygulamanın iletiyi işlemek kullanılabilir olup olmadığını bilmenize gerek olmadan iletileri gönderebilir. Sıranın kuyruğa alma uygulamaları iletileri ne kadar hızlı işleyebilir bağlı olmayan bir hızda iletileri göndermek gönderen bir uygulama sağlar işleme bağımsızlığı sağlar. Kuyruğa ileti gönderme sıkı bir şekilde ileti işleme değil birleştirildiğinde genel sistem kullanılabilirliğini artırır.  
  
-   Hata Yalıtımı. Gönderme veya ileti kuyruğa alma uygulamaları birbirine etkilemeden başarısız olabilir. Örneğin, alıcı uygulama başarısız olursa, gönderen uygulama kuyruğa ileti göndermek devam edebilirsiniz. Alıcı yukarı yeniden olduğunda, sıraya alınan iletileri işleyebilir. Hata yalıtım kullanılabilirlik ve genel sistem güvenilirliğini artırır.  
  
-   Yük Dengeleme. Gönderen uygulamaların iletilerle alıcı uygulamalar doldurmaya. Bir alıcı kısası olmaması sıraları eşleşmeyen ileti üretim ve tüketim hızları yönetebilirsiniz.  
  
-   Bağlantısı kesilmiş işlemleri. Gönderme, alma ve işlemlerinde gibi yüksek Gecikmeli ağlarda veya sınırlı kullanılabilirlik, mobil cihazlar söz konusu olduğunda iletişim kurarken kaybedebilir. Kuyruklar devam etmek bile zaman uç noktalar bağlantısı kesilen bu işlemler sağlar. Bağlantı kurulduğunda, sıraya alma işlemini yapan uygulamanın iletileri iletir.  
  
 Kuyruklar özelliğini kullanmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama standart bağlamaları birini kullanabilirsiniz veya standart bağlamaları biri, gereksinimlerinize uygun değil, özel bir bağlama oluşturabilirsiniz. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ilgili standart bağlamalar ve bir seçim yapma bkz [nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamaları ile Exchange iletileri](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özel bağlama oluşturma, bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Message queuing kavramları genel bakış.  
  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Genel bir bakış [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sıraya desteği.  
  
 [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Nasıl kullanılacağı açıklanmaktadır <xref:System.ServiceModel.NetMsmqBinding> arasında iletişim kurmak için sınıf bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Nasıl kullanılacağı açıklanmaktadır <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> arasında iletişim kurmak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve Message Queuing uygulamaları.  
  
 [Oturumda Kuyruğa Alınmış İletileri Gruplandırma](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Tek bir alıcı uygulamayla ilişkili ileti işleme kolaylaştırmak için bir sıradaki iletiler Grup açıklanmaktadır.  
  
 [Bir İşlemde Toplu İleti İşleme](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 İletileri bir işlemde toplu açıklanmaktadır.  
  
 [İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Teslim edilemeyen iletiler sırası kullanma ileti aktarımı ve teslimat hatalarının nasıl ele alınacağını ve sahipsiz sıraya alınan iletileri işlemek nasıl açıklanmaktadır.  
  
 [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Zehirli ileti (teslim alma işlemini yapan uygulamanın girişimleri üst sınırını aştınız iletileri) nasıl ele alınacağını açıklar.  
  
 [Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Farkları özetler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sıraları özellik arasında [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Aktarım Güvenliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Taşıma güvenliği sıraya alınan iletileri güvenli hale getirmek için nasıl kullanılacağını açıklar.  
  
 [İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 İleti güvenliği sıraya alınan iletileri güvenli hale getirmek için nasıl kullanılacağını açıklar.  
  
 [Kuyruğa Alınan İletilerde Sorun Giderme](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Genel sıraya alma sorunlarının nasıl giderileceği açıklanmaktadır.  
  
 [Kuyruğa Alınan İletişim için En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Kullanmak için en iyi uygulamalar açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kuyruğa alınmış iletişim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Message Queuing](http://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)
