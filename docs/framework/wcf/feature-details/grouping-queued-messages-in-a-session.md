---
title: "Oturumda Kuyruğa Alınmış İletileri Gruplandırma"
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
helpviewer_keywords: queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0dbd9d28d56d8d473b9e92d977da409b74290224
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="de10b-102">Oturumda Kuyruğa Alınmış İletileri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="de10b-102">Grouping Queued Messages in a Session</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="de10b-103">tek bir alıcı uygulama tarafından bir dizi ilgili ileti işleme için bir arada gruplandırmak izin veren bir oturum sağlar.</span><span class="sxs-lookup"><span data-stu-id="de10b-103"> provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="de10b-104">Oturumun bir parçası olan iletiler aynı işlemin parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de10b-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="de10b-105">Tüm oturum işlenmek üzere bir ileti başarısız olursa tüm iletileri aynı işlemin bir parçası olduğundan geri alınır.</span><span class="sxs-lookup"><span data-stu-id="de10b-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="de10b-106">Oturumu sıralarındaki ve zararlı sıraları açısından benzer davranışları yok.</span><span class="sxs-lookup"><span data-stu-id="de10b-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="de10b-107">Oturumları için yapılandırılmış bir sıralı bağlama üzerinde ayarlanan yaşam süresi (TTL) özelliği için zaman oturum bir bütün olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="de10b-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="de10b-108">Yalnızca TTL süresi dolmadan önce bazı iletiler oturumunda gönderilen tüm oturum sahipsiz sıraya konur.</span><span class="sxs-lookup"><span data-stu-id="de10b-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="de10b-109">Benzer şekilde, bir uygulama için uygulama sırasından gönderilmek üzere bir oturumdaki iletilerin başarısız olduğunda, tüm oturum zararlı sırasına (varsa) yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="de10b-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="de10b-110">İleti gruplama örneği</span><span class="sxs-lookup"><span data-stu-id="de10b-110">Message Grouping Example</span></span>  
 <span data-ttu-id="de10b-111">İletileri gruplandırma olduğu yararlı bir örnektir bir sipariş işleme uygulama olarak uygularken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="de10b-111">One example where grouping messages is helpful is when implementing an order-processing application as a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="de10b-112">Örneğin, bir istemci bir öğe sayısı içeren bu uygulamaya yönelik bir sipariş gönderir.</span><span class="sxs-lookup"><span data-stu-id="de10b-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="de10b-113">Her öğe için istemci gönderilmekte olan ayrı bir iletide sonuçları hizmetine yapılan bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="de10b-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="de10b-114">Hizmet vermemesini A ilk öğe ve ikinci öğe almak için Sunucu B almaya mümkündür.</span><span class="sxs-lookup"><span data-stu-id="de10b-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="de10b-115">Uygun sırayla bulmak ve kendisine, öğeyi eklemek bu öğeyi işleyen sunucu sahip bir öğe eklenir her zaman son derece verimsiz olduğu.</span><span class="sxs-lookup"><span data-stu-id="de10b-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="de10b-116">Hala sunucu şu anda işlenmekte olan tüm siparişleri izlemek ve yeni öğe ait hangisinin belirlemek için tüm istekleri işleme yalnızca tek bir sunucuyla böyle verimsiz çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="de10b-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="de10b-117">Tüm istekler için tek bir sıralamayı büyük ölçüde gruplandırma bu tür bir uygulama, uygulanmasını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="de10b-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="de10b-118">İstemci uygulaması için tek bir sıralamayı tüm öğeleri bir oturumda gönderir hizmet sırası işlediğinde, tek seferde tüm oturum işler şekilde.</span><span class="sxs-lookup"><span data-stu-id="de10b-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="de10b-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="de10b-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="de10b-120">Oturumları kullanmak için bir hizmet sözleşmesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="de10b-120">To set up a service contract to use sessions</span></span>  
  
1.  <span data-ttu-id="de10b-121">Bir oturum gerektiren bir hizmet sözleşmesini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="de10b-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="de10b-122">Bunu yapmak <xref:System.ServiceModel.OperationContractAttribute> özniteliği ve belirterek:</span><span class="sxs-lookup"><span data-stu-id="de10b-122">Do this with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  <span data-ttu-id="de10b-123">Bu yöntemlerin herhangi bir şey döndürmeyen çünkü tek yönlü olarak sözleşme işlemlerinde işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="de10b-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="de10b-124">Bu gerçekleştirilir <xref:System.ServiceModel.OperationContractAttribute> özniteliği ve belirterek:</span><span class="sxs-lookup"><span data-stu-id="de10b-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  <span data-ttu-id="de10b-125">Hizmet sözleşmesini uygulama ve belirtin bir `InstanceContextMode` , `PerSession`.</span><span class="sxs-lookup"><span data-stu-id="de10b-125">Implement the service contract and specify an `InstanceContextMode` of `PerSession`.</span></span> <span data-ttu-id="de10b-126">Bu hizmet yalnızca bir kez her oturum başlatır.</span><span class="sxs-lookup"><span data-stu-id="de10b-126">This instantiates the service only once for each session.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  <span data-ttu-id="de10b-127">Her hizmet işlemi, bir işlem gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="de10b-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="de10b-128">Bu konuda belirtin <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="de10b-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="de10b-129">İşlem tamamlandığında işlemi de ayarlamalısınız `TransactionAutoComplete` için `true`.</span><span class="sxs-lookup"><span data-stu-id="de10b-129">The operation that completes the transaction should also set `TransactionAutoComplete` to `true`.</span></span>  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  <span data-ttu-id="de10b-130">Sistem tarafından sağlanan kullanan bir uç nokta yapılandırma `NetMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="de10b-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6.  <span data-ttu-id="de10b-131">Kullanarak bir işlem sırası oluşturmak <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="de10b-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="de10b-132">Sıranın Message Queuing (MSMQ) veya MMC kullanarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de10b-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="de10b-133">Bunu yaparsanız, bir işlem sırası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="de10b-133">If you do, create a transactional queue.</span></span>  
  
7.  <span data-ttu-id="de10b-134">Kullanarak bir hizmet ana bilgisayar hizmeti oluşturma <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="de10b-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8.  <span data-ttu-id="de10b-135">Hizmetin kullanılabilmesi için hizmet ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="de10b-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="de10b-136">Hizmet ana bilgisayarını kapatın.</span><span class="sxs-lookup"><span data-stu-id="de10b-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="de10b-137">Bir istemcinin ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="de10b-137">To set up a client</span></span>  
  
1.  <span data-ttu-id="de10b-138">İşlem sırası yazmak için bir işlem kapsamı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="de10b-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2.  <span data-ttu-id="de10b-139">Oluşturma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan istemci [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="de10b-139">Create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3.  <span data-ttu-id="de10b-140">Sipariş verin.</span><span class="sxs-lookup"><span data-stu-id="de10b-140">Place the order.</span></span>  
  
4.  <span data-ttu-id="de10b-141">Kapat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci.</span><span class="sxs-lookup"><span data-stu-id="de10b-141">Close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de10b-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="de10b-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="de10b-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de10b-143">Description</span></span>  
 <span data-ttu-id="de10b-144">Aşağıdaki örnek kodunu sağlar `IProcessOrder` hizmet ve bir istemci için bu hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="de10b-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="de10b-145">Bunu gösterir nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan kuyruğa alınan oturumları gruplandırma davranışı sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="de10b-145">It shows how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="de10b-146">Hizmet için kodu</span><span class="sxs-lookup"><span data-stu-id="de10b-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a><span data-ttu-id="de10b-147">İstemci kodu</span><span class="sxs-lookup"><span data-stu-id="de10b-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="de10b-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de10b-148">See Also</span></span>  
 [<span data-ttu-id="de10b-149">Oturumlar ve Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="de10b-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [<span data-ttu-id="de10b-150">Kuyruklar genel bakış</span><span class="sxs-lookup"><span data-stu-id="de10b-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
