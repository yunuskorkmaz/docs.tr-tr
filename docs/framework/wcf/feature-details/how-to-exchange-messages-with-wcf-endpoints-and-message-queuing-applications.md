---
title: 'Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 807a34ac50ea317ace42ec12eddcd9ec7cf3736b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme
WCF iletileri gelen ve giden MSMQ iletileri dönüştürmek için MSMQ tümleştirme bağlama kullanarak Windows Communication Foundation (WCF) uygulamaları ile Message Queuing (MSMQ) uygulamalarınız tümleştirebilirsiniz. Bu, yanı sıra WCF istemcileri MSMQ alıcı uygulamalardan çağırmak WCF hizmetleri içine MSMQ gönderen uygulamalarından çağırmaları sağlar.  
  
 Bu bölümde, biz nasıl kullanılacağını açıklayan <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> (1) bir WCF istemcisi System.Messaging ve (2) bir MSMQ uygulama istemci ile bir WCF Hizmeti kullanılarak yazılmış bir MSMQ uygulama hizmeti arasındaki kuyruğa alınan iletişim için.  
  
 Bir WCF istemciden MSMQ alıcı uygulamanın nasıl çağırılacağını bir tam örnek için bkz: [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) örnek.  
  
 Bir WCF hizmeti bir MSMQ istemciden nasıl çağırılacağını bir tam örnek için bkz: [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) örnek.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>MSMQ istemciden gelen iletileri alan bir WCF hizmeti oluşturmak için  
  
1.  Aşağıdaki örnek kodda gösterildiği gibi bir MSMQ gönderen uygulamasından sıraya alınan iletileri alan WCF hizmeti için hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  Arabirim uygulamak ve <xref:System.ServiceModel.ServiceBehaviorAttribute> aşağıdaki örnek kodda gösterildiği gibi sınıfa öznitelik.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  Belirten yapılandırma dosyası oluşturma <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
  
  
4.  Örneği bir <xref:System.ServiceModel.ServiceHost> yapılandırılan bağlama kullanan nesnesi.  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>MSMQ alıcı uygulamaya iletileri gönderen bir WCF istemcisi oluşturmak için  
  
1.  Aşağıdaki örnek kodda gösterildiği gibi gönderir MSMQ alıcı iletileri kuyruğa WCF istemcisi için hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  MSMQ alıcı çağırmak için WCF istemcisini kullanan bir istemci sınıfı tanımlar.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  MsmqIntegrationBinding bağlama kullanılmasını belirtiyor. bir yapılandırmasını oluşturun.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  İstemci sınıfı örneği oluşturun ve hizmet alma iletisi tarafından tanımlanan yöntemini çağırın.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Windows Communication Foundation'dan Message Queuing’e](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Message Queuing (MSMQ) Yükleme](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Message Queuing’den Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
