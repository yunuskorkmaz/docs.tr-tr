---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: WCF uç noktaları ile sıraya alınan Iletileri değiştirme'
title: 'Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: fe7195719c57454cb0035c1b6f06134cf3380a46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802898"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="8ccf4-103">Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="8ccf4-103">How to: Exchange Queued Messages with WCF Endpoints</span></span>

<span data-ttu-id="8ccf4-104">Kuyruklar, hizmet iletişim sırasında kullanılamasa bile, istemci ve Windows Communication Foundation (WCF) hizmeti arasında güvenilir mesajlaşma 'nın gerçekleşebileceğini güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-104">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="8ccf4-105">Aşağıdaki yordamlarda, WCF hizmetini uygularken standart sıraya alınmış bağlamayı kullanarak bir istemci ve hizmet arasında sürekli iletişimin nasıl emin olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-105">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="8ccf4-106">Bu bölümde <xref:System.ServiceModel.NetMsmqBinding> , BIR WCF istemcisi Ile WCF hizmeti arasındaki sıraya alınmış iletişim için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-106">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="8ccf4-107">Bir WCF hizmetinde kuyruğu kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8ccf4-107">To use queuing in a WCF service</span></span>  
  
1. <span data-ttu-id="8ccf4-108">İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="8ccf4-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="8ccf4-109">Hizmet sözleşmesinin bir parçası olan arabirimindeki işlemleri ile birlikte işaretleyin <xref:System.ServiceModel.OperationContractAttribute> ve yönteme yanıt döndürülmediğinden tek yönlü olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-109">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="8ccf4-110">Aşağıdaki kod, örnek bir hizmet sözleşmesi ve işlem tanımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-110">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. <span data-ttu-id="8ccf4-111">Hizmet sözleşmesi Kullanıcı tanımlı türleri geçtiğinde, bu türler için veri sözleşmeleri tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-111">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="8ccf4-112">Aşağıdaki kod iki veri sözleşmesi gösterir `PurchaseOrder` ve `PurchaseOrderLineItem` .</span><span class="sxs-lookup"><span data-stu-id="8ccf4-112">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="8ccf4-113">Bu iki tür, hizmete gönderilen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-113">These two types define data that is sent to the service.</span></span> <span data-ttu-id="8ccf4-114">(Bu veri sözleşmesini tanımlayan sınıfların de bir dizi yöntem tanımladığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-114">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="8ccf4-115">Bu yöntemler veri sözleşmesinin bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-115">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="8ccf4-116">Yalnızca özniteliğiyle belirtilen Üyeler <xref:System.Runtime.Serialization.DataMemberAttribute> veri sözleşmesinin bir parçasıdır.)</span><span class="sxs-lookup"><span data-stu-id="8ccf4-116">Only those members that are declared with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. <span data-ttu-id="8ccf4-117">Bir sınıftaki arabirimde tanımlanan hizmet sözleşmesinin yöntemlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-117">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="8ccf4-118"><xref:System.ServiceModel.OperationBehaviorAttribute>Yöntemine yerleştirilmiş olduğuna dikkat edin `SubmitPurchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="8ccf4-118">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="8ccf4-119">Bu işlem, bu işlemin bir işlem içinde çağrılması gerektiğini ve Yöntem tamamlandığında işlemin otomatik olarak tamamlanmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-119">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4. <span data-ttu-id="8ccf4-120">Kullanarak bir işlem kuyruğu oluşturun <xref:System.Messaging> .</span><span class="sxs-lookup"><span data-stu-id="8ccf4-120">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="8ccf4-121">Bunun yerine Microsoft Message Queuing (MSMQ) Microsoft Yönetim Konsolu 'Nu (MMC) kullanarak kuyruğu oluşturmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-121">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="8ccf4-122">Bu durumda, bir işlem kuyruğu oluşturduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-122">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. <span data-ttu-id="8ccf4-123"><xref:System.ServiceModel.Description.ServiceEndpoint>Hizmet adresini belirten ve standart bağlamayı kullanan bir yapılandırmada bir yapılandırma tanımlayın <xref:System.ServiceModel.NetMsmqBinding> .</span><span class="sxs-lookup"><span data-stu-id="8ccf4-123">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="8ccf4-124">WCF yapılandırmasını kullanma hakkında daha fazla bilgi için bkz. [WCF hizmetlerini yapılandırma](../configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="8ccf4-124">For more information about using WCF configuration, see [Configuring WCF services](../configuring-services.md).</span></span>  

6. <span data-ttu-id="8ccf4-125">`OrderProcessing` <xref:System.ServiceModel.ServiceHost> Kuyruktaki iletileri okuyan ve bunları işleyen hizmet için bir konak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-125">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="8ccf4-126">Hizmeti kullanılabilir hale getirmek için hizmet ana bilgisayarını açın.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-126">Open the service host to make the service available.</span></span> <span data-ttu-id="8ccf4-127">Kullanıcıya Hizmeti sonlandırmak için herhangi bir tuşa basmasını bildiren bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-127">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="8ccf4-128">`ReadLine`Anahtarın basılı olmasını beklemek için çağrısı yapın ve ardından hizmeti kapatın.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-128">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="8ccf4-129">Kuyruğa alınmış hizmet için bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8ccf4-129">To create a client for the queued service</span></span>  
  
1. <span data-ttu-id="8ccf4-130">Aşağıdaki örnek, bir barındırma uygulamasının nasıl çalıştırılacağını ve WCF istemcisini oluşturmak için Svcutil.exe aracının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-130">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. <span data-ttu-id="8ccf4-131"><xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.NetMsmqBinding> Aşağıdaki örnekte gösterildiği gibi, adresi belirten ve standart bağlamayı kullanan bir yapılandırma belirleyin.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-131">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  

3. <span data-ttu-id="8ccf4-132">İşlemsel sıraya yazmak için bir işlem kapsamı oluşturun, `SubmitPurchaseOrder` işlemi çağırın ve aşağıdaki örnekte gösterildiği gıbı WCF istemcisini kapatın.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-132">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="8ccf4-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ccf4-133">Example</span></span>  

 <span data-ttu-id="8ccf4-134">Aşağıdaki örneklerde hizmet kodu, barındırma uygulaması, App.config dosyası ve bu örneğe dahil edilen istemci kodu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-134">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a><span data-ttu-id="8ccf4-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ccf4-135">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="8ccf4-136">İşlem Gerçekleştirilmiş MSMQ Bağlama</span><span class="sxs-lookup"><span data-stu-id="8ccf4-136">Transacted MSMQ Binding</span></span>](../samples/transacted-msmq-binding.md)
- [<span data-ttu-id="8ccf4-137">WCF'de Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="8ccf4-137">Queuing in WCF</span></span>](queuing-in-wcf.md)
- [<span data-ttu-id="8ccf4-138">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="8ccf4-138">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="8ccf4-139">Windows Communication Foundation'dan İleti Kuyruğuna</span><span class="sxs-lookup"><span data-stu-id="8ccf4-139">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="8ccf4-140">İleti Kuyruğa Alma Yükleme (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="8ccf4-140">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="8ccf4-141">Windows Communication Foundation'a İleti Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="8ccf4-141">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="8ccf4-142">İleti Kuyruğa Alma ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8ccf4-142">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
