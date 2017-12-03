---
title: "Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 75b18dab37a18723671cebf51c3cc943b907b38a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme
Message Queuing (MSMQ) uygulamalarınız ile tümleştirebilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] gelen ve giden MSMQ iletileri dönüştürmek için MSMQ tümleştirme bağlama kullanarak uygulamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletileri. Bu sayede MSMQ alıcı uygulamalardan çağırmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çağrısına yanı sıra istemcilerin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ Gönderen uygulamalardan Hizmetleri.  
  
 Bu bölümde, biz nasıl kullanılacağını açıklayan <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> arasında kuyruğa alınan iletişim için (1) bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System.Messaging ve (2) bir MSMQ uygulama istemcisi kullanılarak yazılmış bir MSMQ uygulama hizmet ve istemci ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 Bir MSMQ alıcı uygulamasından nasıl çağırılacağını tam bir örnek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, bkz: [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) örnek.  
  
 Nasıl çağırılacağını tam bir örnek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet MSMQ istemciden bkz [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) örnek.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>MSMQ istemciden gelen iletileri alan bir WCF hizmeti oluşturmak için  
  
1.  İçin hizmet sözleşmesini tanımlayan bir arabirim tanımlayın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , alan hizmetini sıraya alınan iletileri bir MSMQ gönderen uygulamasından aşağıdaki örnek kodda gösterildiği gibi.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  Arabirim uygulamak ve <xref:System.ServiceModel.ServiceBehaviorAttribute> aşağıdaki örnek kodda gösterildiği gibi sınıfa öznitelik.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  Belirten yapılandırma dosyası oluşturma <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
  
  
4.  Örneği bir <xref:System.ServiceModel.ServiceHost> yapılandırılan bağlama kullanan nesnesi.  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>MSMQ alıcı uygulamaya iletileri gönderen bir WCF istemcisi oluşturmak için  
  
1.  İçin hizmet sözleşmesini tanımlayan bir arabirim tanımlayın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sıraya alınan gönderen istemci iletileri MSMQ alıcı için aşağıdaki örnek kodda gösterildiği gibi.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  Bir istemci tanımlamak, sınıf [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcisi MSMQ alıcı çağırmak için kullanır.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  MsmqIntegrationBinding bağlama kullanılmasını belirtiyor. bir yapılandırmasını oluşturun.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  İstemci sınıfı örneği oluşturun ve hizmet alma iletisi tarafından tanımlanan yöntemini çağırın.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kuyruklar genel bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Nasıl yapılır: WCF uç noktaları iletileri kuyruğa alınan](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Message Queuing (MSMQ) yükleme](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Windows Communication Foundation'a ileti kuyruğa alma](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [İleti kuyruğa alma ile ileti güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
