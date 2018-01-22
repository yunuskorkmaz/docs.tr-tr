---
title: "Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma"
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
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba057a0b96d393a5efbaf054e75c34f446c7dde6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma
Kuyruklar olun güvenilir Mesajlaşma bir istemci arasında oluşabilir ve bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet iletişimi aynı anda kullanılabilir olsa bile, hizmet. Aşağıdaki yordamlar dayanıklı standart kullanarak bir hizmet ile bir istemci arasında kuyruğa alınmış iletişim bağlayıcı uygularken emin olmak nasıl gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 Bu bölümde nasıl kullanılacağı açıklanmaktadır <xref:System.ServiceModel.NetMsmqBinding> arasında kuyruğa alınan iletişim için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Bir WCF Hizmeti queuing kullanmak için  
  
1.  İle işaretlenen arabirimini kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.ServiceContractAttribute>. Hizmet sözleşmesine parçası olan arabirimi işlemlerinde işaretlemek <xref:System.ServiceModel.OperationContractAttribute> ve yanıt yöntemine döndürdüğünden tek yönlü olarak belirtin. Aşağıdaki kod, bir örnek hizmet sözleşmesini ve işlem tanımını sağlar.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  Hizmet sözleşmesi kullanıcı tanımlı türler geçtiğinde, bu türleri için veri sözleşmeleri tanımlamanız gerekir. Aşağıdaki kod iki veri sözleşmeleri gösterir `PurchaseOrder` ve `PurchaseOrderLineItem`. Bu iki tür hizmete gönderilen verileri tanımlamak. (Bu veri sözleşmesi tanımlayan sınıflar ayrıca çeşitli yöntemler tanımlamanız unutmayın. Bu yöntemlerin veri sözleşmenin parçası dikkate alınmaz. İle bildirilen üyeleri `DataMember` özniteliği veri sözleşmesi bir parçasıdır.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  Bir sınıf arabiriminde tanımlanan hizmet sözleşmesini yöntemleri uygulayın.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Bildirim <xref:System.ServiceModel.OperationBehaviorAttribute> getirilen `SubmitPurchaseOrder` yöntemi. Bu, bu işlem bir işlem içinde çağırılmalıdır ve yöntemi tamamlandığında işlem otomatik olarak tamamlar olduğunu belirtir.  
  
4.  Kullanarak bir işlem sırası oluşturmak <xref:System.Messaging>. Bunun yerine Microsoft Message Queuing (MSMQ) Microsoft Yönetim Konsolu (MMC) kullanarak sıraya oluşturmayı seçebilirsiniz. Bu durumda, bir işlem sırası oluşturduğunuzdan emin olun.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  Tanımlayan bir <xref:System.ServiceModel.Description.ServiceEndpoint> hizmet adresini belirtir ve standart kullanan yapılandırmasında <xref:System.ServiceModel.NetMsmqBinding> bağlama. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapılandırma, bkz: [Windows Communication Foundation uygulamaları yapılandırma](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
  
  
6.  Bir ana bilgisayar için oluşturun `OrderProcessing` kullanarak hizmet <xref:System.ServiceModel.ServiceHost> kuyruktan iletileri okuyan ve bunları işler. Hizmetin kullanılabilmesi için hizmet ana bilgisayarı açın. Hizmet sonlandırmak için herhangi bir tuşa basın kullanıcıya bildiren bir ileti görüntüler. Çağrı `ReadLine` tuşuna basıldığında ve hizmet kapatmak beklenecek.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Sıraya alınan hizmet için bir istemci oluşturmak için  
  
1.  Aşağıdaki örnek barındırma uygulamayı çalıştırın ve oluşturmak için Svcutil.exe aracını kullanın gösterilmektedir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci.  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  Tanımlayan bir <xref:System.ServiceModel.Description.ServiceEndpoint> adresini belirtir ve standart kullanan yapılandırmasında <xref:System.ServiceModel.NetMsmqBinding> , aşağıdaki örnekte gösterildiği gibi bağlama.  
  
  
  
3.  İşlem sırası çağrısı yazmak için bir işlem kapsamı oluşturma `SubmitPurchaseOrder` işlemi ve close [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki örnekte gösterildiği gibi istemci.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler, servis kodu, barındırma uygulama, App.config dosyası ve bu örnek için dahil istemci kodu gösterir.  
  
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
 [Message Queuing tümleştirme bağlama örnekleri](http://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Message Queuing’den Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
