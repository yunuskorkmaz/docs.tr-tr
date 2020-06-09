---
title: 'Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 0775de90903aed27a8d0006614a4b6f2d857eee3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597104"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme
MSMQ iletilerini WCF iletilerine dönüştürmek için MSMQ tümleştirme bağlamasını kullanarak mevcut Message Queuing (MSMQ) uygulamalarını Windows Communication Foundation (WCF) uygulamalarıyla tümleştirebilirsiniz. Bu, WCF istemcilerinden MSMQ alıcı uygulamalarına ve MSMQ gönderici uygulamalarından WCF Hizmetleri 'ne çağrı yapmanıza olanak sağlar.  
  
 Bu bölümde, <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> (1) BIR WCF istemcisi Ile System. Messaging ve (2) ile BIR MSMQ uygulama istemcisi ve bır WCF hizmeti kullanılarak yazılan BIR MSMQ uygulama hizmeti arasındaki sıraya alınmış iletişim için nasıl kullanılacağını açıkladık.  
  
 Bir WCF istemcisinden MSMQ alıcı uygulamasının nasıl çağrılacağını gösteren bir örnek için, [Windows Communication Foundation Message Queuing](../samples/wcf-to-message-queuing.md) örneğe bakın.  
  
 Bir MSMQ istemcisinden bir WCF hizmetinin nasıl çağrılacağını gösteren bir örnek için, [Message Queuing Windows Communication Foundation](../samples/message-queuing-to-wcf.md) örneğe bakın.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>MSMQ istemcisinden iletiler alan bir WCF hizmeti oluşturmak için  
  
1. Aşağıdaki örnek kodda gösterildiği gibi, bir MSMQ gönderici uygulamasından sıraya alınan iletileri alan WCF hizmeti için hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <xref:System.ServiceModel.ServiceBehaviorAttribute>Aşağıdaki örnek kodda gösterildiği gibi, arabirimini uygulayın ve özniteliğini sınıfına uygulayın.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. Öğesini belirten bir yapılandırma dosyası oluşturun <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> .  

4. <xref:System.ServiceModel.ServiceHost>Yapılandırılmış bağlamayı kullanan bir nesne örneğini oluşturun.  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>MSMQ alıcı uygulamasına ileti gönderen bir WCF istemcisi oluşturmak için  
  
1. Aşağıdaki örnek kodda gösterildiği gibi, MSMQ alıcısına sıraya alınan iletileri gönderen WCF istemcisinin hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. WCF istemcisinin MSMQ alıcısını çağırmak için kullandığı bir istemci sınıfı tanımlayın.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. MsmqIntegrationBinding bağlamasının kullanımını belirten bir yapılandırma oluşturun.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. İstemci sınıfının bir örneğini oluşturun ve ileti alma hizmeti tarafından tanımlanan yöntemi çağırın.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklar Genel Bakış](queues-overview.md)
- [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Windows Communication Foundation'dan İleti Kuyruğuna](../samples/wcf-to-message-queuing.md)
- [İleti Kuyruğa Alma Yükleme (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Windows Communication Foundation'a İleti Kuyruğa Alma](../samples/message-queuing-to-wcf.md)
- [İleti Kuyruğa Alma ile İleti Güvenliği](../samples/message-security-over-message-queuing.md)
