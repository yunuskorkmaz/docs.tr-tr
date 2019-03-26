---
title: 'Nasıl yapılır: WCF uç noktaları ile kuyruğa alınmış iletiler gönderip alır'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: ea052a2dd843205a8108ea48f17ea84577817215
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411037"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Nasıl yapılır: WCF uç noktaları ile kuyruğa alınmış iletiler gönderip alır
Hizmet iletişimi anında kullanılabilir olmasa bile güvenilir Mesajlaşma'nün bir Windows Communication Foundation (WCF) hizmet ve istemci arasında gerçekleşebilir kuyrukları emin olun. Aşağıdaki yordamlar, kalıcı bir istemci ve standart'ı kullanarak bir hizmet arasında bağlayıcı WCF Hizmeti uygularken kuyruğa alınmış iletişim sağlamak nasıl gösterir.  
  
 Bu bölümde, nasıl kullanılacağını açıklar <xref:System.ServiceModel.NetMsmqBinding> bir WCF istemcisi ve bir WCF hizmeti arasında kuyruğa alınan iletişim için.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Bir WCF Hizmeti queuing kullanmak için  
  
1.  İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.ServiceContractAttribute>. Hizmet söyleşmesi parçası arabiriminde işlemleri işaretlemek <xref:System.ServiceModel.OperationContractAttribute> ve yönteme yanıt döndürdüğünden, bunları tek yönlü olarak belirtin. Aşağıdaki kod örneği bir hizmet sözleşmesi ve işlem tanımı sağlar.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  Kullanıcı tanımlı türler hizmet sözleşmesi başarılı olduğunda, bu türleri için veri sözleşme tanımlamanız gerekir. Aşağıdaki kod, iki veri sözleşmeleri göstermektedir `PurchaseOrder` ve `PurchaseOrderLineItem`. Bu iki tür hizmete gönderilen verileri tanımlar. (Bu veri sözleşme tanımlayan sınıfları da bir dizi yöntem tanımlamanız unutmayın. Bu yöntemleri veri sözleşmesinin bir parçası olarak kabul edilmez. İle bildirilen üyeler <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği veri anlaşması bir parçasıdır.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  Bir sınıf içinde arabirim içinde tanımlanmış hizmet sözleşmesinin yöntemleri uygulayın.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Bildirim <xref:System.ServiceModel.OperationBehaviorAttribute> yerleştirildiği `SubmitPurchaseOrder` yöntemi. Bu, bu işlem bir işlem içinde çağrılması gerekir ve yöntem tamamlandığında işlem otomatik olarak tamamlanmasını belirtir.  
  
4.  Bir işlem sırası kullanarak oluşturma <xref:System.Messaging>. Bunun yerine Microsoft Message Queuing (MSMQ) Microsoft Yönetim Konsolu (MMC) kullanarak kuyruk oluşturmayı seçebilirsiniz. Bu durumda, bir işlem kuyruğu oluşturma emin olun.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  Tanımlayan bir <xref:System.ServiceModel.Description.ServiceEndpoint> hizmet adresini belirtir ve standart kullanan yapılandırmasında <xref:System.ServiceModel.NetMsmqBinding> bağlama. WCF yapılandırma özelliğini kullanma hakkında daha fazla bilgi için bkz. [yapılandırma WCF hizmetleri](../configuring-services.md).  
  
  
  
6.  Bir konağı için oluşturmayı `OrderProcessing` kullanarak hizmet <xref:System.ServiceModel.ServiceHost> kuyruktan iletileri okuyan ve işler. Hizmet kullanılabilir hale getirmek için hizmet ana bilgisayarı açın. Hizmeti sonlandırmak için herhangi bir tuşa basın kullanıcıya bildiren bir ileti görüntüler. Çağrı `ReadLine` anahtar basıldığında ve ardından hizmeti kapatmak beklenecek.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Sıraya alınan hizmet için bir istemci oluşturmak için  
  
1.  Aşağıdaki örnek, barındırma uygulamasını çalıştırmak ve WCF istemcisi oluşturma için Svcutil.exe aracını kullanma gösterilmektedir.  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  Tanımlayan bir <xref:System.ServiceModel.Description.ServiceEndpoint> adresini belirtir ve standart kullanan yapılandırmasında <xref:System.ServiceModel.NetMsmqBinding> aşağıdaki örnekte gösterildiği gibi bağlama.  
  
  
  
3.  İşlem sırası çağrı yazmak için bir işlem kapsamı oluşturma `SubmitPurchaseOrder` işlemi ve Kapat WCF istemcisi, aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler, hizmet kodunu, barındırma uygulaması, App.config dosyası ve bu örnek için istemci kodu gösterir.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.NetMsmqBinding>
- [İşlem Gerçekleştirilmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)
- [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Nasıl yapılır: WCF uç noktaları ve ileti uygulamaları ile Exchange ileti](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Windows Communication Foundation'dan Message Queuing’e](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Message Queuing (MSMQ) Yükleme](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Message Queuing’den Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
