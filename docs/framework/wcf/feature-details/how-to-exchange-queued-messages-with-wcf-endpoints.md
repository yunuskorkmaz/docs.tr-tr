---
title: 'Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 185bcb64522115d0c60ae90ee22a73610139c8c3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747268"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma
Hizmet iletişimi anında kullanılabilir olmasa bile güvenilir Mesajlaşma'nün bir Windows Communication Foundation (WCF) hizmet ve istemci arasında gerçekleşebilir kuyrukları emin olun. Aşağıdaki yordamlar, kalıcı bir istemci ve standart'ı kullanarak bir hizmet arasında bağlayıcı WCF Hizmeti uygularken kuyruğa alınmış iletişim sağlamak nasıl gösterir.  
  
 Bu bölümde, nasıl kullanılacağını açıklar <xref:System.ServiceModel.NetMsmqBinding> bir WCF istemcisi ve bir WCF hizmeti arasında kuyruğa alınan iletişim için.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Bir WCF Hizmeti queuing kullanmak için  
  
1.  İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.ServiceContractAttribute>. Hizmet söyleşmesi parçası arabiriminde işlemleri işaretlemek <xref:System.ServiceModel.OperationContractAttribute> ve yönteme yanıt döndürdüğünden, bunları tek yönlü olarak belirtin. Aşağıdaki kod örneği bir hizmet sözleşmesi ve işlem tanımı sağlar.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  Kullanıcı tanımlı türler hizmet sözleşmesi başarılı olduğunda, bu türleri için veri sözleşme tanımlamanız gerekir. Aşağıdaki kod, iki veri sözleşmeleri göstermektedir `PurchaseOrder` ve `PurchaseOrderLineItem`. Bu iki tür hizmete gönderilen verileri tanımlar. (Bu veri sözleşme tanımlayan sınıfları da bir dizi yöntem tanımlamanız unutmayın. Bu yöntemleri veri sözleşmesinin bir parçası olarak kabul edilmez. İle bildirilen üyeler `DataMember` özniteliği veri anlaşması bir parçasıdır.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  Bir sınıf içinde arabirim içinde tanımlanmış hizmet sözleşmesinin yöntemleri uygulayın.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Bildirim <xref:System.ServiceModel.OperationBehaviorAttribute> yerleştirildiği `SubmitPurchaseOrder` yöntemi. Bu, bu işlem bir işlem içinde çağrılması gerekir ve yöntem tamamlandığında işlem otomatik olarak tamamlanmasını belirtir.  
  
4.  Bir işlem sırası kullanarak oluşturma <xref:System.Messaging>. Bunun yerine Microsoft Message Queuing (MSMQ) Microsoft Yönetim Konsolu (MMC) kullanarak kuyruk oluşturmayı seçebilirsiniz. Bu durumda, bir işlem kuyruğu oluşturma emin olun.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  Tanımlayan bir <xref:System.ServiceModel.Description.ServiceEndpoint> hizmet adresini belirtir ve standart kullanan yapılandırmasında <xref:System.ServiceModel.NetMsmqBinding> bağlama. WCF yapılandırma özelliğini kullanma hakkında daha fazla bilgi için bkz. [Windows Communication Foundation uygulamaları yapılandırma](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
  
  
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
  
  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [İşlem Gerçekleştirilmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Windows Communication Foundation'dan Message Queuing’e](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Message Queuing (MSMQ) Yükleme](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Message Queuing tümleştirme bağlama örnekleri](https://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Message Queuing’den Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
