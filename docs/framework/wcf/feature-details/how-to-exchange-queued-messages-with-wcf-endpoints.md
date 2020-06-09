---
title: 'Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 7da7ba1b680bae2b29eeff8fe669e097ea8eda32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595381"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma
Kuyruklar, hizmet iletişim sırasında kullanılamasa bile, istemci ve Windows Communication Foundation (WCF) hizmeti arasında güvenilir mesajlaşma 'nın gerçekleşebileceğini güvence altına alır. Aşağıdaki yordamlarda, WCF hizmetini uygularken standart sıraya alınmış bağlamayı kullanarak bir istemci ve hizmet arasında sürekli iletişimin nasıl emin olduğu gösterilmektedir.  
  
 Bu bölümde <xref:System.ServiceModel.NetMsmqBinding> , BIR WCF istemcisi Ile WCF hizmeti arasındaki sıraya alınmış iletişim için nasıl kullanılacağı açıklanmaktadır.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Bir WCF hizmetinde kuyruğu kullanmak için  
  
1. İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın <xref:System.ServiceModel.ServiceContractAttribute> . Hizmet sözleşmesinin bir parçası olan arabirimindeki işlemleri ile birlikte işaretleyin <xref:System.ServiceModel.OperationContractAttribute> ve yönteme yanıt döndürülmediğinden tek yönlü olarak belirtin. Aşağıdaki kod, örnek bir hizmet sözleşmesi ve işlem tanımı sağlar.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. Hizmet sözleşmesi Kullanıcı tanımlı türleri geçtiğinde, bu türler için veri sözleşmeleri tanımlamanız gerekir. Aşağıdaki kod iki veri sözleşmesi gösterir `PurchaseOrder` ve `PurchaseOrderLineItem` . Bu iki tür, hizmete gönderilen verileri tanımlar. (Bu veri sözleşmesini tanımlayan sınıfların de bir dizi yöntem tanımladığına unutmayın. Bu yöntemler veri sözleşmesinin bir parçası olarak kabul edilmez. Yalnızca özniteliğiyle belirtilen Üyeler <xref:System.Runtime.Serialization.DataMemberAttribute> veri sözleşmesinin bir parçasıdır.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. Bir sınıftaki arabirimde tanımlanan hizmet sözleşmesinin yöntemlerini uygulayın.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <xref:System.ServiceModel.OperationBehaviorAttribute>Yöntemine yerleştirilmiş olduğuna dikkat edin `SubmitPurchaseOrder` . Bu işlem, bu işlemin bir işlem içinde çağrılması gerektiğini ve Yöntem tamamlandığında işlemin otomatik olarak tamamlanmasını belirtir.  
  
4. Kullanarak bir işlem kuyruğu oluşturun <xref:System.Messaging> . Bunun yerine Microsoft Message Queuing (MSMQ) Microsoft Yönetim Konsolu 'Nu (MMC) kullanarak kuyruğu oluşturmayı seçebilirsiniz. Bu durumda, bir işlem kuyruğu oluşturduğunuzdan emin olun.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. <xref:System.ServiceModel.Description.ServiceEndpoint>Hizmet adresini belirten ve standart bağlamayı kullanan bir yapılandırmada bir yapılandırma tanımlayın <xref:System.ServiceModel.NetMsmqBinding> . WCF yapılandırmasını kullanma hakkında daha fazla bilgi için bkz. [WCF hizmetlerini yapılandırma](../configuring-services.md).  

6. `OrderProcessing` <xref:System.ServiceModel.ServiceHost> Kuyruktaki iletileri okuyan ve bunları işleyen hizmet için bir konak oluşturun. Hizmeti kullanılabilir hale getirmek için hizmet ana bilgisayarını açın. Kullanıcıya Hizmeti sonlandırmak için herhangi bir tuşa basmasını bildiren bir ileti görüntüler. `ReadLine`Anahtarın basılı olmasını beklemek için çağrısı yapın ve ardından hizmeti kapatın.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Kuyruğa alınmış hizmet için bir istemci oluşturmak için  
  
1. Aşağıdaki örnek, WCF istemcisini oluşturmak için barındırma uygulamasının nasıl çalıştırılacağını ve Svcutil. exe aracını nasıl kullanacağınızı gösterir.  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.NetMsmqBinding> Aşağıdaki örnekte gösterildiği gibi, adresi belirten ve standart bağlamayı kullanan bir yapılandırma belirleyin.  

3. İşlemsel sıraya yazmak için bir işlem kapsamı oluşturun, `SubmitPurchaseOrder` işlemi çağırın ve aşağıdaki örnekte gösterildiği gıbı WCF istemcisini kapatın.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde hizmet kodu, barındırma uygulaması, App. config dosyası ve bu örnek için eklenen istemci kodu gösterilmektedir.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetMsmqBinding>
- [İşlem Gerçekleştirilmiş MSMQ Bağlama](../samples/transacted-msmq-binding.md)
- [WCF'de Kuyruğa Alma](queuing-in-wcf.md)
- [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Windows Communication Foundation'dan İleti Kuyruğuna](../samples/wcf-to-message-queuing.md)
- [İleti Kuyruğa Alma Yükleme (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Windows Communication Foundation'a İleti Kuyruğa Alma](../samples/message-queuing-to-wcf.md)
- [İleti Kuyruğa Alma ile İleti Güvenliği](../samples/message-security-over-message-queuing.md)
