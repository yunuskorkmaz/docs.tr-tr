---
title: 'Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 185bcb64522115d0c60ae90ee22a73610139c8c3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536640"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="4a576-102">Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="4a576-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="4a576-103">Hizmet iletişimi anında kullanılabilir olmasa bile güvenilir Mesajlaşma'nün bir Windows Communication Foundation (WCF) hizmet ve istemci arasında gerçekleşebilir kuyrukları emin olun.</span><span class="sxs-lookup"><span data-stu-id="4a576-103">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="4a576-104">Aşağıdaki yordamlar, kalıcı bir istemci ve standart'ı kullanarak bir hizmet arasında bağlayıcı WCF Hizmeti uygularken kuyruğa alınmış iletişim sağlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a576-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="4a576-105">Bu bölümde, nasıl kullanılacağını açıklar <xref:System.ServiceModel.NetMsmqBinding> bir WCF istemcisi ve bir WCF hizmeti arasında kuyruğa alınan iletişim için.</span><span class="sxs-lookup"><span data-stu-id="4a576-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="4a576-106">Bir WCF Hizmeti queuing kullanmak için</span><span class="sxs-lookup"><span data-stu-id="4a576-106">To use queuing in a WCF service</span></span>  
  
1.  <span data-ttu-id="4a576-107">İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4a576-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="4a576-108">Hizmet söyleşmesi parçası arabiriminde işlemleri işaretlemek <xref:System.ServiceModel.OperationContractAttribute> ve yönteme yanıt döndürdüğünden, bunları tek yönlü olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="4a576-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="4a576-109">Aşağıdaki kod örneği bir hizmet sözleşmesi ve işlem tanımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a576-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  <span data-ttu-id="4a576-110">Kullanıcı tanımlı türler hizmet sözleşmesi başarılı olduğunda, bu türleri için veri sözleşme tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a576-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="4a576-111">Aşağıdaki kod, iki veri sözleşmeleri göstermektedir `PurchaseOrder` ve `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="4a576-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="4a576-112">Bu iki tür hizmete gönderilen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a576-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="4a576-113">(Bu veri sözleşme tanımlayan sınıfları da bir dizi yöntem tanımlamanız unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4a576-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="4a576-114">Bu yöntemleri veri sözleşmesinin bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="4a576-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="4a576-115">İle bildirilen üyeler `DataMember` özniteliği veri anlaşması bir parçasıdır.)</span><span class="sxs-lookup"><span data-stu-id="4a576-115">Only those members that are declared with the `DataMember` attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  <span data-ttu-id="4a576-116">Bir sınıf içinde arabirim içinde tanımlanmış hizmet sözleşmesinin yöntemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4a576-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="4a576-117">Bildirim <xref:System.ServiceModel.OperationBehaviorAttribute> yerleştirildiği `SubmitPurchaseOrder` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4a576-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="4a576-118">Bu, bu işlem bir işlem içinde çağrılması gerekir ve yöntem tamamlandığında işlem otomatik olarak tamamlanmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a576-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4.  <span data-ttu-id="4a576-119">Bir işlem sırası kullanarak oluşturma <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="4a576-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="4a576-120">Bunun yerine Microsoft Message Queuing (MSMQ) Microsoft Yönetim Konsolu (MMC) kullanarak kuyruk oluşturmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a576-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="4a576-121">Bu durumda, bir işlem kuyruğu oluşturma emin olun.</span><span class="sxs-lookup"><span data-stu-id="4a576-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  <span data-ttu-id="4a576-122">Tanımlayan bir <xref:System.ServiceModel.Description.ServiceEndpoint> hizmet adresini belirtir ve standart kullanan yapılandırmasında <xref:System.ServiceModel.NetMsmqBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="4a576-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="4a576-123">WCF yapılandırma özelliğini kullanma hakkında daha fazla bilgi için bkz. [Windows Communication Foundation uygulamaları yapılandırma](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="4a576-123">For more information about using WCF configuration, see [Configuring Windows Communication Foundation Applications](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
  
  
6.  <span data-ttu-id="4a576-124">Bir konağı için oluşturmayı `OrderProcessing` kullanarak hizmet <xref:System.ServiceModel.ServiceHost> kuyruktan iletileri okuyan ve işler.</span><span class="sxs-lookup"><span data-stu-id="4a576-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="4a576-125">Hizmet kullanılabilir hale getirmek için hizmet ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="4a576-125">Open the service host to make the service available.</span></span> <span data-ttu-id="4a576-126">Hizmeti sonlandırmak için herhangi bir tuşa basın kullanıcıya bildiren bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4a576-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="4a576-127">Çağrı `ReadLine` anahtar basıldığında ve ardından hizmeti kapatmak beklenecek.</span><span class="sxs-lookup"><span data-stu-id="4a576-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="4a576-128">Sıraya alınan hizmet için bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4a576-128">To create a client for the queued service</span></span>  
  
1.  <span data-ttu-id="4a576-129">Aşağıdaki örnek, barındırma uygulamasını çalıştırmak ve WCF istemcisi oluşturma için Svcutil.exe aracını kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a576-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  <span data-ttu-id="4a576-130">Tanımlayan bir <xref:System.ServiceModel.Description.ServiceEndpoint> adresini belirtir ve standart kullanan yapılandırmasında <xref:System.ServiceModel.NetMsmqBinding> aşağıdaki örnekte gösterildiği gibi bağlama.</span><span class="sxs-lookup"><span data-stu-id="4a576-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  
  
  
  
3.  <span data-ttu-id="4a576-131">İşlem sırası çağrı yazmak için bir işlem kapsamı oluşturma `SubmitPurchaseOrder` işlemi ve Kapat WCF istemcisi, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4a576-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="4a576-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a576-132">Example</span></span>  
 <span data-ttu-id="4a576-133">Aşağıdaki örnekler, hizmet kodunu, barındırma uygulaması, App.config dosyası ve bu örnek için istemci kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a576-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="4a576-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a576-134">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [<span data-ttu-id="4a576-135">İşlem Gerçekleştirilmiş MSMQ Bağlama</span><span class="sxs-lookup"><span data-stu-id="4a576-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [<span data-ttu-id="4a576-136">WCF'de Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="4a576-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="4a576-137">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="4a576-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="4a576-138">Windows Communication Foundation'dan Message Queuing’e</span><span class="sxs-lookup"><span data-stu-id="4a576-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="4a576-139">Message Queuing (MSMQ) Yükleme</span><span class="sxs-lookup"><span data-stu-id="4a576-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="4a576-140">Message Queuing tümleştirme bağlama örnekleri</span><span class="sxs-lookup"><span data-stu-id="4a576-140">Message Queuing Integration Binding Samples</span></span>](https://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [<span data-ttu-id="4a576-141">Message Queuing’den Windows Communication Foundation'a</span><span class="sxs-lookup"><span data-stu-id="4a576-141">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="4a576-142">Message Queuing Üzerinden İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4a576-142">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
