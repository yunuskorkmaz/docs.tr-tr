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
ms.openlocfilehash: a6c50d9c6740b0c680e349a71bf4b3bdece2b34f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="792da-102">Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="792da-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="792da-103">Kuyruklar olun güvenilir Mesajlaşma bir istemci arasında oluşabilir ve bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet iletişimi aynı anda kullanılabilir olsa bile, hizmet.</span><span class="sxs-lookup"><span data-stu-id="792da-103">Queues ensure that reliable messaging can occur between a client and a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="792da-104">Aşağıdaki yordamlar dayanıklı standart kullanarak bir hizmet ile bir istemci arasında kuyruğa alınmış iletişim bağlayıcı uygularken emin olmak nasıl gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="792da-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="792da-105">Bu bölümde nasıl kullanılacağı açıklanmaktadır <xref:System.ServiceModel.NetMsmqBinding> arasında kuyruğa alınan iletişim için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="792da-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="792da-106">Bir WCF Hizmeti queuing kullanmak için</span><span class="sxs-lookup"><span data-stu-id="792da-106">To use queuing in a WCF service</span></span>  
  
1.  <span data-ttu-id="792da-107">İle işaretlenen arabirimini kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="792da-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="792da-108">Hizmet sözleşmesine parçası olan arabirimi işlemlerinde işaretlemek <xref:System.ServiceModel.OperationContractAttribute> ve yanıt yöntemine döndürdüğünden tek yönlü olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="792da-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="792da-109">Aşağıdaki kod, bir örnek hizmet sözleşmesini ve işlem tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="792da-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  <span data-ttu-id="792da-110">Hizmet sözleşmesi kullanıcı tanımlı türler geçtiğinde, bu türleri için veri sözleşmeleri tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="792da-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="792da-111">Aşağıdaki kod iki veri sözleşmeleri gösterir `PurchaseOrder` ve `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="792da-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="792da-112">Bu iki tür hizmete gönderilen verileri tanımlamak.</span><span class="sxs-lookup"><span data-stu-id="792da-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="792da-113">(Bu veri sözleşmesi tanımlayan sınıflar ayrıca çeşitli yöntemler tanımlamanız unutmayın.</span><span class="sxs-lookup"><span data-stu-id="792da-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="792da-114">Bu yöntemlerin veri sözleşmenin parçası dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="792da-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="792da-115">İle bildirilen üyeleri `DataMember` özniteliği veri sözleşmesi bir parçasıdır.)</span><span class="sxs-lookup"><span data-stu-id="792da-115">Only those members that are declared with the `DataMember` attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  <span data-ttu-id="792da-116">Bir sınıf arabiriminde tanımlanan hizmet sözleşmesini yöntemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="792da-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="792da-117">Bildirim <xref:System.ServiceModel.OperationBehaviorAttribute> getirilen `SubmitPurchaseOrder` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="792da-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="792da-118">Bu, bu işlem bir işlem içinde çağırılmalıdır ve yöntemi tamamlandığında işlem otomatik olarak tamamlar olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="792da-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4.  <span data-ttu-id="792da-119">Kullanarak bir işlem sırası oluşturmak <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="792da-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="792da-120">Bunun yerine Microsoft Message Queuing (MSMQ) Microsoft Yönetim Konsolu (MMC) kullanarak sıraya oluşturmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="792da-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="792da-121">Bu durumda, bir işlem sırası oluşturduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="792da-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  <span data-ttu-id="792da-122">Tanımlayan bir <xref:System.ServiceModel.Description.ServiceEndpoint> hizmet adresini belirtir ve standart kullanan yapılandırmasında <xref:System.ServiceModel.NetMsmqBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="792da-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="792da-123">kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapılandırma, bkz: [Windows Communication Foundation uygulamaları yapılandırma](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="792da-123"> using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
  
  
6.  <span data-ttu-id="792da-124">Bir ana bilgisayar için oluşturun `OrderProcessing` kullanarak hizmet <xref:System.ServiceModel.ServiceHost> kuyruktan iletileri okuyan ve bunları işler.</span><span class="sxs-lookup"><span data-stu-id="792da-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="792da-125">Hizmetin kullanılabilmesi için hizmet ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="792da-125">Open the service host to make the service available.</span></span> <span data-ttu-id="792da-126">Hizmet sonlandırmak için herhangi bir tuşa basın kullanıcıya bildiren bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="792da-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="792da-127">Çağrı `ReadLine` tuşuna basıldığında ve hizmet kapatmak beklenecek.</span><span class="sxs-lookup"><span data-stu-id="792da-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="792da-128">Sıraya alınan hizmet için bir istemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="792da-128">To create a client for the queued service</span></span>  
  
1.  <span data-ttu-id="792da-129">Aşağıdaki örnek barındırma uygulamayı çalıştırın ve oluşturmak için Svcutil.exe aracını kullanın gösterilmektedir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci.</span><span class="sxs-lookup"><span data-stu-id="792da-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  <span data-ttu-id="792da-130">Tanımlayan bir <xref:System.ServiceModel.Description.ServiceEndpoint> adresini belirtir ve standart kullanan yapılandırmasında <xref:System.ServiceModel.NetMsmqBinding> , aşağıdaki örnekte gösterildiği gibi bağlama.</span><span class="sxs-lookup"><span data-stu-id="792da-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  
  
  
  
3.  <span data-ttu-id="792da-131">İşlem sırası çağrısı yazmak için bir işlem kapsamı oluşturma `SubmitPurchaseOrder` işlemi ve close [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki örnekte gösterildiği gibi istemci.</span><span class="sxs-lookup"><span data-stu-id="792da-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="792da-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="792da-132">Example</span></span>  
 <span data-ttu-id="792da-133">Aşağıdaki örnekler, servis kodu, barındırma uygulama, App.config dosyası ve bu örnek için dahil istemci kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="792da-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="792da-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="792da-134">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [<span data-ttu-id="792da-135">İşlem gerçekleştirilmiş MSMQ bağlama</span><span class="sxs-lookup"><span data-stu-id="792da-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [<span data-ttu-id="792da-136">WCF'de kuyruğa alma</span><span class="sxs-lookup"><span data-stu-id="792da-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="792da-137">Nasıl yapılır: WCF uç noktaları iletileri Exchange ve Message Queuing uygulamaları</span><span class="sxs-lookup"><span data-stu-id="792da-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="792da-138">Message Queuing için Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="792da-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="792da-139">Message Queuing (MSMQ) yükleme</span><span class="sxs-lookup"><span data-stu-id="792da-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="792da-140">Message Queuing tümleştirme bağlama örnekleri</span><span class="sxs-lookup"><span data-stu-id="792da-140">Message Queuing Integration Binding Samples</span></span>](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [<span data-ttu-id="792da-141">Windows Communication Foundation'a ileti kuyruğa alma</span><span class="sxs-lookup"><span data-stu-id="792da-141">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="792da-142">İleti kuyruğa alma ile ileti güvenliği</span><span class="sxs-lookup"><span data-stu-id="792da-142">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
