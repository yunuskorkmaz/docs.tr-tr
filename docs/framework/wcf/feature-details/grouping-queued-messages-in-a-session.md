---
title: Oturumda Kuyruğa Alınmış İletileri Gruplandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 231310e5c427f507141e3c144cb02b8e848d4fbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185154"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="49955-102">Oturumda Kuyruğa Alınmış İletileri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="49955-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="49955-103">Windows Communication Foundation (WCF), ilgili iletiler kümesini tek bir alıcı uygulama tarafından işlenmek üzere gruplandırmanızı sağlayan bir oturum sağlar.</span><span class="sxs-lookup"><span data-stu-id="49955-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="49955-104">Oturumun parçası olan iletiler aynı işlemin parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="49955-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="49955-105">Tüm iletiler aynı işlemin parçası olduğundan, bir ileti işlenmezse tüm oturum geri alınır.</span><span class="sxs-lookup"><span data-stu-id="49955-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="49955-106">Oturumlar ölü harf kuyrukları ve zehir kuyrukları ile ilgili benzer davranışlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="49955-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="49955-107">Oturumlar için yapılandırılan sıralı bir bağlama üzerinde ayarlanmış Yaşam Süresi (TTL) özelliği oturuma bir bütün olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="49955-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="49955-108">Oturumdaki iletilerin yalnızca bazıları TTL'nin süresi dolmadan önce gönderilirse, oturumun tamamı ölü harf sırasına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="49955-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="49955-109">Benzer şekilde, oturumdaki iletiler uygulama kuyruğundan bir uygulamaya gönderilmediğinde, tüm oturum zehir kuyruğuna (varsa) yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="49955-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="49955-110">İleti Gruplandırma Örneği</span><span class="sxs-lookup"><span data-stu-id="49955-110">Message Grouping Example</span></span>  
 <span data-ttu-id="49955-111">İletileri gruplandırmanın yararlı olduğu durumlardan biri, bir Sipariş işleme uygulamasını WCF hizmeti olarak uygularken elde edilir.</span><span class="sxs-lookup"><span data-stu-id="49955-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="49955-112">Örneğin, bir istemci bu uygulamaya bir dizi öğe içeren bir sipariş gönderir.</span><span class="sxs-lookup"><span data-stu-id="49955-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="49955-113">Her öğe için istemci hizmete çağrı yapar ve bu da ayrı bir iletinin gönderilmesiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="49955-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="49955-114">Hizmetin A'nın ilk öğeyi alması, Sunucu B'nin ikinci öğeyi alması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="49955-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="49955-115">Her öğe eklendiğinde, sunucu bu öğeyi işleme uygun siparişi bulmak ve son derece verimsiz olan öğeyi eklemek zorundadır.</span><span class="sxs-lookup"><span data-stu-id="49955-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="49955-116">Sunucunun şu anda işlenen tüm siparişleri izlemesi ve yeni öğenin hangisine ait olduğunu belirlemesi gerektiğinden, tüm istekleri yalnızca tek bir sunucuyla bu tür verimsizliklerle karşınıza çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49955-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="49955-117">Tek bir sipariş için tüm istekleri gruplandırma büyük ölçüde böyle bir uygulamanın uygulanmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="49955-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="49955-118">İstemci uygulaması bir oturumda tek bir sipariş için tüm öğeleri gönderir, bu nedenle hizmet siparişi işlerse, tüm oturumu aynı anda işler.</span><span class="sxs-lookup"><span data-stu-id="49955-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="49955-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="49955-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="49955-120">Oturumları kullanmak için bir hizmet sözleşmesi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="49955-120">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="49955-121">Oturum gerektiren bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="49955-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="49955-122">Belirterek öznitelik ile <xref:System.ServiceModel.ServiceContractAttribute> bunu yapın:</span><span class="sxs-lookup"><span data-stu-id="49955-122">Do this with the <xref:System.ServiceModel.ServiceContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="49955-123">Bu yöntemler hiçbir şeyi döndürmediği için sözleşmedeki işlemleri tek yönlü olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="49955-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="49955-124">Bu belirterek <xref:System.ServiceModel.OperationContractAttribute> öznitelik ile yapılır:</span><span class="sxs-lookup"><span data-stu-id="49955-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="49955-125">Hizmet sözleşmesini uygulayın <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> ve <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>bir .</span><span class="sxs-lookup"><span data-stu-id="49955-125">Implement the service contract and specify an <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>.</span></span> <span data-ttu-id="49955-126">Bu, her oturum için yalnızca bir kez hizmeti anında verir.</span><span class="sxs-lookup"><span data-stu-id="49955-126">This instantiates the service only once for each session.</span></span>  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="49955-127">Her hizmet işlemi bir işlem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="49955-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="49955-128">Bunu öznitelik <xref:System.ServiceModel.OperationBehaviorAttribute> ile belirtin.</span><span class="sxs-lookup"><span data-stu-id="49955-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="49955-129">İşlemi tamamlayan işlem de ' <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> `true`olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="49955-129">The operation that completes the transaction should also set <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> to `true`.</span></span>  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. <span data-ttu-id="49955-130">Sistem tarafından sağlanan `NetMsmqBinding` bağlamayı kullanan bir bitiş noktası yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="49955-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="49955-131">'yi kullanarak <xref:System.Messaging>bir işlem sırası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49955-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="49955-132">İleti Sıralaması (MSMQ) veya MMC'yi kullanarak da sıra oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49955-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="49955-133">Bunu yaparsanız, bir işlem sırası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49955-133">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="49955-134">Kullanarak hizmet için bir hizmet <xref:System.ServiceModel.ServiceHost>ana bilgisayar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49955-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="49955-135">Hizmeti kullanılabilir hale getirmek için servis ana bilgisayarını açın.</span><span class="sxs-lookup"><span data-stu-id="49955-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="49955-136">Servis ana bilgisayarını kapatın.</span><span class="sxs-lookup"><span data-stu-id="49955-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="49955-137">İstemci ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="49955-137">To set up a client</span></span>  
  
1. <span data-ttu-id="49955-138">İşlem sırasına yazmak için bir hareket kapsamı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49955-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="49955-139">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracını kullanarak WCF istemcisini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49955-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="49955-140">Siparişi ver.</span><span class="sxs-lookup"><span data-stu-id="49955-140">Place the order.</span></span>  
  
4. <span data-ttu-id="49955-141">WCF istemcisini kapatın.</span><span class="sxs-lookup"><span data-stu-id="49955-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49955-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="49955-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="49955-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49955-143">Description</span></span>  
 <span data-ttu-id="49955-144">Aşağıdaki örnek, hizmetin `IProcessOrder` ve bu hizmeti kullanan bir istemcinin kodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="49955-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="49955-145">WCF'nin gruplandırma davranışını sağlamak için sıraya girilen oturumları nasıl kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="49955-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="49955-146">Hizmet Kodu</span><span class="sxs-lookup"><span data-stu-id="49955-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="49955-147">İstemci kodu</span><span class="sxs-lookup"><span data-stu-id="49955-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="49955-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49955-148">See also</span></span>

- [<span data-ttu-id="49955-149">Oturumlar ve Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="49955-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [<span data-ttu-id="49955-150">Kuyruklar Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="49955-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
