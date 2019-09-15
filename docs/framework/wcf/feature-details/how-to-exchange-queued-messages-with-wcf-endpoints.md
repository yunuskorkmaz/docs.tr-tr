---
title: 'Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 09b21c9483b4f2716409b560dbbb478fe5a6badd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972219"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="45c47-102">Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="45c47-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="45c47-103">Kuyruklar, hizmet iletişim sırasında kullanılamasa bile, istemci ve Windows Communication Foundation (WCF) hizmeti arasında güvenilir mesajlaşma 'nın gerçekleşebileceğini güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="45c47-103">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="45c47-104">Aşağıdaki yordamlarda, WCF hizmetini uygularken standart sıraya alınmış bağlamayı kullanarak bir istemci ve hizmet arasında sürekli iletişimin nasıl emin olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="45c47-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="45c47-105">Bu bölümde, bir WCF istemcisi <xref:System.ServiceModel.NetMsmqBinding> ile WCF hizmeti arasındaki sıraya alınmış iletişim için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45c47-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="45c47-106">Bir WCF hizmetinde kuyruğu kullanmak için</span><span class="sxs-lookup"><span data-stu-id="45c47-106">To use queuing in a WCF service</span></span>  
  
1. <span data-ttu-id="45c47-107">İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="45c47-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="45c47-108">Hizmet sözleşmesinin bir parçası olan arabirimindeki işlemleri ile birlikte <xref:System.ServiceModel.OperationContractAttribute> işaretleyin ve yönteme yanıt döndürülmediğinden tek yönlü olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="45c47-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="45c47-109">Aşağıdaki kod, örnek bir hizmet sözleşmesi ve işlem tanımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="45c47-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. <span data-ttu-id="45c47-110">Hizmet sözleşmesi Kullanıcı tanımlı türleri geçtiğinde, bu türler için veri sözleşmeleri tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="45c47-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="45c47-111">Aşağıdaki kod iki veri sözleşmesi `PurchaseOrder` gösterir ve. `PurchaseOrderLineItem`</span><span class="sxs-lookup"><span data-stu-id="45c47-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="45c47-112">Bu iki tür, hizmete gönderilen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="45c47-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="45c47-113">(Bu veri sözleşmesini tanımlayan sınıfların de bir dizi yöntem tanımladığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="45c47-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="45c47-114">Bu yöntemler veri sözleşmesinin bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="45c47-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="45c47-115">Yalnızca <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğiyle belirtilen Üyeler veri sözleşmesinin bir parçasıdır.)</span><span class="sxs-lookup"><span data-stu-id="45c47-115">Only those members that are declared with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. <span data-ttu-id="45c47-116">Bir sınıftaki arabirimde tanımlanan hizmet sözleşmesinin yöntemlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="45c47-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="45c47-117">`SubmitPurchaseOrder` Yöntemine yerleştirilmiş <xref:System.ServiceModel.OperationBehaviorAttribute> olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="45c47-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="45c47-118">Bu işlem, bu işlemin bir işlem içinde çağrılması gerektiğini ve Yöntem tamamlandığında işlemin otomatik olarak tamamlanmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45c47-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4. <span data-ttu-id="45c47-119">Kullanarak <xref:System.Messaging>bir işlem kuyruğu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="45c47-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="45c47-120">Bunun yerine Microsoft Message Queuing (MSMQ) Microsoft Yönetim Konsolu 'Nu (MMC) kullanarak kuyruğu oluşturmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45c47-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="45c47-121">Bu durumda, bir işlem kuyruğu oluşturduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="45c47-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. <span data-ttu-id="45c47-122">Hizmet adresini <xref:System.ServiceModel.Description.ServiceEndpoint> belirten ve standart <xref:System.ServiceModel.NetMsmqBinding> bağlamayı kullanan bir yapılandırmada bir yapılandırma tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="45c47-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="45c47-123">WCF yapılandırmasını kullanma hakkında daha fazla bilgi için bkz. [WCF hizmetlerini yapılandırma](../configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="45c47-123">For more information about using WCF configuration, see [Configuring WCF services](../configuring-services.md).</span></span>  

6. <span data-ttu-id="45c47-124">Kuyruktaki iletileri okuyan ve bunları `OrderProcessing` işleyen <xref:System.ServiceModel.ServiceHost> hizmet için bir konak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="45c47-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="45c47-125">Hizmeti kullanılabilir hale getirmek için hizmet ana bilgisayarını açın.</span><span class="sxs-lookup"><span data-stu-id="45c47-125">Open the service host to make the service available.</span></span> <span data-ttu-id="45c47-126">Kullanıcıya Hizmeti sonlandırmak için herhangi bir tuşa basmasını bildiren bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45c47-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="45c47-127">Anahtarın `ReadLine` basılı olmasını beklemek için çağrısı yapın ve ardından hizmeti kapatın.</span><span class="sxs-lookup"><span data-stu-id="45c47-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="45c47-128">Kuyruğa alınmış hizmet için bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="45c47-128">To create a client for the queued service</span></span>  
  
1. <span data-ttu-id="45c47-129">Aşağıdaki örnek, WCF istemcisini oluşturmak için barındırma uygulamasının nasıl çalıştırılacağını ve Svcutil. exe aracını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="45c47-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. <span data-ttu-id="45c47-130">Aşağıdaki örnekte <xref:System.ServiceModel.Description.ServiceEndpoint> gösterildiği gibi, adresi belirten ve standart <xref:System.ServiceModel.NetMsmqBinding> bağlamayı kullanan bir yapılandırma belirleyin.</span><span class="sxs-lookup"><span data-stu-id="45c47-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  

3. <span data-ttu-id="45c47-131">İşlemsel sıraya yazmak için bir işlem kapsamı oluşturun, `SubmitPurchaseOrder` işlemi çağırın ve aşağıdaki örnekte gösterildiği gibi WCF istemcisini kapatın.</span><span class="sxs-lookup"><span data-stu-id="45c47-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="45c47-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="45c47-132">Example</span></span>  
 <span data-ttu-id="45c47-133">Aşağıdaki örneklerde hizmet kodu, barındırma uygulaması, App. config dosyası ve bu örnek için eklenen istemci kodu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="45c47-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a><span data-ttu-id="45c47-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45c47-134">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="45c47-135">İşlem Gerçekleştirilmiş MSMQ Bağlama</span><span class="sxs-lookup"><span data-stu-id="45c47-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)
- [<span data-ttu-id="45c47-136">WCF'de Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="45c47-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="45c47-137">Nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamalarla Exchange Iletileri</span><span class="sxs-lookup"><span data-stu-id="45c47-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="45c47-138">Windows Communication Foundation'dan Message Queuing’e</span><span class="sxs-lookup"><span data-stu-id="45c47-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="45c47-139">Message Queuing (MSMQ) Yükleme</span><span class="sxs-lookup"><span data-stu-id="45c47-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="45c47-140">Message Queuing’den Windows Communication Foundation'a</span><span class="sxs-lookup"><span data-stu-id="45c47-140">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="45c47-141">Message Queuing Üzerinden İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="45c47-141">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
