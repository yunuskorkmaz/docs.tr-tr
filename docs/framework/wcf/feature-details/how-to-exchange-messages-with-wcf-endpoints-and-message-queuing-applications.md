---
title: 'Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 7463f9cfc37c2bf4f271f6e59896a7d77f3f65cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310312"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme
MSMQ iletileri gelen WCF iletileri ve dönüştürmek için MSMQ tümleştirme bağlama kullanarak Windows Communication Foundation (WCF) uygulamaları ile Message Queuing (MSMQ) uygulamalara tümleştirebilirsiniz. Bu, yanı sıra WCF istemcileri MSMQ alıcı uygulamalardan çağırmak WCF hizmetleri içine MSMQ gönderen uygulamalarından çağırmaları sağlar.  
  
 Bu bölümde, biz nasıl kullanılacağını açıklayan <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> (1) bir WCF istemcisi System.Messaging ve (2) bir MSMQ uygulama istemcisi ve bir WCF Hizmeti kullanılarak yazılmış bir MSMQ uygulama hizmeti arasındaki kuyruğa alınan iletişim için.  
  
 MSMQ alıcı uygulamanın bir WCF istemciden çağırmayı göstermektedir, eksiksiz bir örnek için bkz. [Message Queuing Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) örnek.  
  
 Bir WCF hizmeti bir MSMQ istemciden çağırmayı göstermektedir, eksiksiz bir örnek için bkz. [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) örnek.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>MSMQ istemciden gelen iletileri alan bir WCF hizmeti oluşturmak için  
  
1. Aşağıdaki örnek kodda gösterildiği gibi bir MSMQ gönderen uygulamasından kuyruğa alınmış iletiler alan bir WCF hizmeti için hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. Arabirim uygulamak ve <xref:System.ServiceModel.ServiceBehaviorAttribute> aşağıdaki örnekte gösterildiği gibi Sınıf özniteliği.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. Belirten yapılandırma dosyası oluşturma <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  

4. Örneği bir <xref:System.ServiceModel.ServiceHost> yapılandırılmış bağlama kullanan nesne.  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Bir MSMQ alıcı uygulamasına ileti gönderen bir WCF istemcisi oluşturma  
  
1. Aşağıdaki örnek kodda gösterildiği gibi kuyruğa alınmış iletileri MSMQ alıcısına gönderir WCF istemcisi için hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. MSMQ alıcı çağırmak için WCF istemcisini kullanan bir istemci sınıfı tanımlayın.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. MsmqIntegrationBinding bağlama belirtir bir yapılandırma oluşturun.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. İstemci sınıfı örneğini oluşturmak ve ileti alma hizmeti tarafından tanımlanan yöntemini çağırın.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Nasıl yapılır: WCF uç noktaları ile kuyruğa alınmış iletiler gönderip alır](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Windows Communication Foundation'dan Message Queuing’e](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Message Queuing (MSMQ) Yükleme](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Message Queuing’den Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
