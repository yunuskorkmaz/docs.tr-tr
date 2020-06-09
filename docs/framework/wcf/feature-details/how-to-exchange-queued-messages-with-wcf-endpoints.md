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
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="2c58f-102">Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="2c58f-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="2c58f-103">Kuyruklar, hizmet iletişim sırasında kullanılamasa bile, istemci ve Windows Communication Foundation (WCF) hizmeti arasında güvenilir mesajlaşma 'nın gerçekleşebileceğini güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="2c58f-103">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="2c58f-104">Aşağıdaki yordamlarda, WCF hizmetini uygularken standart sıraya alınmış bağlamayı kullanarak bir istemci ve hizmet arasında sürekli iletişimin nasıl emin olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2c58f-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="2c58f-105">Bu bölümde <xref:System.ServiceModel.NetMsmqBinding> , BIR WCF istemcisi Ile WCF hizmeti arasındaki sıraya alınmış iletişim için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c58f-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="2c58f-106">Bir WCF hizmetinde kuyruğu kullanmak için</span><span class="sxs-lookup"><span data-stu-id="2c58f-106">To use queuing in a WCF service</span></span>  
  
1. <span data-ttu-id="2c58f-107">İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2c58f-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="2c58f-108">Hizmet sözleşmesinin bir parçası olan arabirimindeki işlemleri ile birlikte işaretleyin <xref:System.ServiceModel.OperationContractAttribute> ve yönteme yanıt döndürülmediğinden tek yönlü olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="2c58f-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="2c58f-109">Aşağıdaki kod, örnek bir hizmet sözleşmesi ve işlem tanımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c58f-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. <span data-ttu-id="2c58f-110">Hizmet sözleşmesi Kullanıcı tanımlı türleri geçtiğinde, bu türler için veri sözleşmeleri tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c58f-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="2c58f-111">Aşağıdaki kod iki veri sözleşmesi gösterir `PurchaseOrder` ve `PurchaseOrderLineItem` .</span><span class="sxs-lookup"><span data-stu-id="2c58f-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="2c58f-112">Bu iki tür, hizmete gönderilen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c58f-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="2c58f-113">(Bu veri sözleşmesini tanımlayan sınıfların de bir dizi yöntem tanımladığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2c58f-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="2c58f-114">Bu yöntemler veri sözleşmesinin bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="2c58f-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="2c58f-115">Yalnızca özniteliğiyle belirtilen Üyeler <xref:System.Runtime.Serialization.DataMemberAttribute> veri sözleşmesinin bir parçasıdır.)</span><span class="sxs-lookup"><span data-stu-id="2c58f-115">Only those members that are declared with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. <span data-ttu-id="2c58f-116">Bir sınıftaki arabirimde tanımlanan hizmet sözleşmesinin yöntemlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2c58f-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="2c58f-117"><xref:System.ServiceModel.OperationBehaviorAttribute>Yöntemine yerleştirilmiş olduğuna dikkat edin `SubmitPurchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="2c58f-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="2c58f-118">Bu işlem, bu işlemin bir işlem içinde çağrılması gerektiğini ve Yöntem tamamlandığında işlemin otomatik olarak tamamlanmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c58f-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4. <span data-ttu-id="2c58f-119">Kullanarak bir işlem kuyruğu oluşturun <xref:System.Messaging> .</span><span class="sxs-lookup"><span data-stu-id="2c58f-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="2c58f-120">Bunun yerine Microsoft Message Queuing (MSMQ) Microsoft Yönetim Konsolu 'Nu (MMC) kullanarak kuyruğu oluşturmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c58f-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="2c58f-121">Bu durumda, bir işlem kuyruğu oluşturduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2c58f-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. <span data-ttu-id="2c58f-122"><xref:System.ServiceModel.Description.ServiceEndpoint>Hizmet adresini belirten ve standart bağlamayı kullanan bir yapılandırmada bir yapılandırma tanımlayın <xref:System.ServiceModel.NetMsmqBinding> .</span><span class="sxs-lookup"><span data-stu-id="2c58f-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="2c58f-123">WCF yapılandırmasını kullanma hakkında daha fazla bilgi için bkz. [WCF hizmetlerini yapılandırma](../configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="2c58f-123">For more information about using WCF configuration, see [Configuring WCF services](../configuring-services.md).</span></span>  

6. <span data-ttu-id="2c58f-124">`OrderProcessing` <xref:System.ServiceModel.ServiceHost> Kuyruktaki iletileri okuyan ve bunları işleyen hizmet için bir konak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2c58f-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="2c58f-125">Hizmeti kullanılabilir hale getirmek için hizmet ana bilgisayarını açın.</span><span class="sxs-lookup"><span data-stu-id="2c58f-125">Open the service host to make the service available.</span></span> <span data-ttu-id="2c58f-126">Kullanıcıya Hizmeti sonlandırmak için herhangi bir tuşa basmasını bildiren bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2c58f-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="2c58f-127">`ReadLine`Anahtarın basılı olmasını beklemek için çağrısı yapın ve ardından hizmeti kapatın.</span><span class="sxs-lookup"><span data-stu-id="2c58f-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="2c58f-128">Kuyruğa alınmış hizmet için bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2c58f-128">To create a client for the queued service</span></span>  
  
1. <span data-ttu-id="2c58f-129">Aşağıdaki örnek, WCF istemcisini oluşturmak için barındırma uygulamasının nasıl çalıştırılacağını ve Svcutil. exe aracını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c58f-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. <span data-ttu-id="2c58f-130"><xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.NetMsmqBinding> Aşağıdaki örnekte gösterildiği gibi, adresi belirten ve standart bağlamayı kullanan bir yapılandırma belirleyin.</span><span class="sxs-lookup"><span data-stu-id="2c58f-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  

3. <span data-ttu-id="2c58f-131">İşlemsel sıraya yazmak için bir işlem kapsamı oluşturun, `SubmitPurchaseOrder` işlemi çağırın ve aşağıdaki örnekte gösterildiği gıbı WCF istemcisini kapatın.</span><span class="sxs-lookup"><span data-stu-id="2c58f-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="2c58f-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c58f-132">Example</span></span>  
 <span data-ttu-id="2c58f-133">Aşağıdaki örneklerde hizmet kodu, barındırma uygulaması, App. config dosyası ve bu örnek için eklenen istemci kodu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2c58f-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a><span data-ttu-id="2c58f-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c58f-134">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="2c58f-135">İşlem Gerçekleştirilmiş MSMQ Bağlama</span><span class="sxs-lookup"><span data-stu-id="2c58f-135">Transacted MSMQ Binding</span></span>](../samples/transacted-msmq-binding.md)
- [<span data-ttu-id="2c58f-136">WCF'de Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="2c58f-136">Queuing in WCF</span></span>](queuing-in-wcf.md)
- [<span data-ttu-id="2c58f-137">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="2c58f-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="2c58f-138">Windows Communication Foundation'dan İleti Kuyruğuna</span><span class="sxs-lookup"><span data-stu-id="2c58f-138">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="2c58f-139">İleti Kuyruğa Alma Yükleme (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="2c58f-139">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="2c58f-140">Windows Communication Foundation'a İleti Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="2c58f-140">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="2c58f-141">İleti Kuyruğa Alma ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="2c58f-141">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
