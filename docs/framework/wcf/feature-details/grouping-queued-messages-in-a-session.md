---
title: Oturumda Kuyruğa Alınmış İletileri Gruplandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 37f0874ea99ee928e49a54a3e6a05ea4ef06f84e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855926"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="cb1e5-102">Oturumda Kuyruğa Alınmış İletileri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="cb1e5-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="cb1e5-103">Windows Communication Foundation (WCF) tarafından tek bir alıcı uygulamanın bir dizi ilgili ileti işleme için bir arada gruplandırmak izin veren bir oturum sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="cb1e5-104">Bir oturumun parçasıdır iletileri aynı işlemin bir parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="cb1e5-105">Tüm oturum işlenmek üzere bir ileti başarısız olursa tüm iletiler aynı işlemin bir parçası olduğundan geri alınır.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="cb1e5-106">Oturumları edilemeyen ve zehirli kuyrukları benzer davranışlara sahip.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="cb1e5-107">Oturumları için yapılandırılmış bir kuyruğa alınmış bağlaması üzerindeki yaşam süresi (TTL) özelliği zaman oturum bir bütün olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="cb1e5-108">Yalnızca TTL'nin süresi dolmadan önce bazı oturumdaki iletiler gönderilir, tüm oturumda edilemeyen sırasına konur.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="cb1e5-109">Benzer şekilde, uygulama kuyruktan bir uygulamaya gönderilecek bir oturumda ileti başarısız olursa, tüm oturumda (varsa) zehirli sıraya konur.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="cb1e5-110">İleti gruplama örneği</span><span class="sxs-lookup"><span data-stu-id="cb1e5-110">Message Grouping Example</span></span>  
 <span data-ttu-id="cb1e5-111">İletileri gruplandırma yararlı olduğu bir örnek, bir sipariş işleme uygulaması bir WCF hizmeti olarak uygularken verilebilir.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="cb1e5-112">Örneğin, bir istemci birçok öğe içeren bu uygulama için bir sipariş gönderir.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="cb1e5-113">Her öğe için istemci ayrı bir ileti gönderilmekte olan sonuçları hizmetine çağrıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="cb1e5-114">İkinci öğe almak için Sunucu B ve ilk öğeyi almak, hizmet A mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="cb1e5-115">Her zaman uygun sırayı bulmak ve öğe eklemek bu öğe işleme sunucunun sahip bir öğe eklendiğinde, son derece verimsizdir.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="cb1e5-116">Sunucu şu anda işlenmekte olan tüm siparişleri izlemek ve yeni öğenin ait olduğu hangisinin belirlemek için tüm istekleri işleme yalnızca tek bir sunucuyla yine de böyle verimsizlikleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="cb1e5-117">Tüm istekler tek bir sipariş için büyük ölçüde gruplandırma tür bir uygulamanın uygulama basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="cb1e5-118">İstemci uygulama, tek bir sipariş için tüm öğeleri bir oturumda gönderir. hizmet sırası işlediğinde, tek seferde tüm oturum işler için.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="cb1e5-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cb1e5-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="cb1e5-120">Oturumlarının kullanmak için bir hizmet anlaşmasını oluşturan ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cb1e5-120">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="cb1e5-121">Bir oturum gerektiren bir hizmet sözleşmesini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="cb1e5-122">İle bunu <xref:System.ServiceModel.OperationContractAttribute> özniteliği ve belirterek:</span><span class="sxs-lookup"><span data-stu-id="cb1e5-122">Do this with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="cb1e5-123">Bu yöntemlerin herhangi bir şey döndürmeyen çünkü tek yönlü olarak sözleşme işlemlerinde işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="cb1e5-124">Bunun <xref:System.ServiceModel.OperationContractAttribute> özniteliği ve belirterek:</span><span class="sxs-lookup"><span data-stu-id="cb1e5-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="cb1e5-125">Hizmet sözleşmesini uygulama ve belirtin bir `InstanceContextMode` , `PerSession`.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-125">Implement the service contract and specify an `InstanceContextMode` of `PerSession`.</span></span> <span data-ttu-id="cb1e5-126">Bu hizmet her oturum için yalnızca bir kez başlatır.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-126">This instantiates the service only once for each session.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="cb1e5-127">Her hizmet işlemi, bir işlem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="cb1e5-128">Bu konuda belirtin <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="cb1e5-129">İşlem tamamlandığında işlemi de ayarlamalısınız `TransactionAutoComplete` için `true`.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-129">The operation that completes the transaction should also set `TransactionAutoComplete` to `true`.</span></span>  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. <span data-ttu-id="cb1e5-130">Sistem tarafından sağlanan kullanan bir uç nokta yapılandırma `NetMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="cb1e5-131">Bir işlem sırası kullanarak oluşturma <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="cb1e5-132">Message Queuing (MSMQ) veya MMC kullanarak kuyruk oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="cb1e5-133">Bunu yaparsanız, bir işlem kuyruğu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-133">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="cb1e5-134">Kullanarak bir hizmet konağı için hizmet oluşturma <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="cb1e5-135">Hizmet kullanılabilir hale getirmek için hizmet ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="cb1e5-136">Hizmet ana bilgisayarını kapatın.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="cb1e5-137">Bir istemcinin ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cb1e5-137">To set up a client</span></span>  
  
1. <span data-ttu-id="cb1e5-138">İşlem kuyruğa yazmak için bir işlem kapsamı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="cb1e5-139">Kullanarak bir WCF istemcisi oluşturma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="cb1e5-140">Sipariş verin.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-140">Place the order.</span></span>  
  
4. <span data-ttu-id="cb1e5-141">WCF İstemcisi'ni kapatın.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb1e5-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb1e5-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cb1e5-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb1e5-143">Description</span></span>  
 <span data-ttu-id="cb1e5-144">Aşağıdaki örnek kodunu sağlar `IProcessOrder` hizmet ve bir istemci için bu hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="cb1e5-145">Bu, kuyruğa alınmış oturumları WCF gruplandırma davranışı sağlamak için nasıl kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="cb1e5-146">Hizmet kodu</span><span class="sxs-lookup"><span data-stu-id="cb1e5-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="cb1e5-147">İstemci kodu</span><span class="sxs-lookup"><span data-stu-id="cb1e5-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="cb1e5-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb1e5-148">See also</span></span>

- [<span data-ttu-id="cb1e5-149">Oturumlar ve Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="cb1e5-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [<span data-ttu-id="cb1e5-150">Kuyruklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb1e5-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
