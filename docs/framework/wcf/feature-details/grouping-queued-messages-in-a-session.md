---
title: Oturumda Kuyruğa Alınmış İletileri Gruplandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 995697e618ff5d56a719efc5d69b97583733d980
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892745"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="9702d-102">Oturumda Kuyruğa Alınmış İletileri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="9702d-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="9702d-103">Windows Communication Foundation (WCF), bir dizi ilgili iletiyi tek bir alıcı uygulamayla işlemek üzere gruplandırmaya olanak tanıyan bir oturum sağlar.</span><span class="sxs-lookup"><span data-stu-id="9702d-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="9702d-104">Bir oturumun parçası olan mesajlar aynı işlemin parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9702d-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="9702d-105">Tüm iletiler aynı işlemin parçası olduğundan, bir ileti işlenemezse tüm oturum geri alınır.</span><span class="sxs-lookup"><span data-stu-id="9702d-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="9702d-106">Oturumlar, atılacak ileti kuyrukları ve zarar kuyruklarıyla ilgili benzer davranışları vardır.</span><span class="sxs-lookup"><span data-stu-id="9702d-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="9702d-107">Oturumlar için yapılandırılmış bir sıraya alınmış bağlamada ayarlanan yaşam süresi (TTL) özelliği, oturuma bir bütün olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9702d-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="9702d-108">Oturumun yalnızca bir kısmı TTL 'nin süresi dolmadan önce gönderilirse, tüm oturum atılacak ileti kuyruğuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9702d-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="9702d-109">Benzer şekilde, bir oturumdaki iletiler uygulama kuyruğundan bir uygulamaya gönderilemezse, tüm oturum zarar sırasına (varsa) yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9702d-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="9702d-110">İleti gruplandırma örneği</span><span class="sxs-lookup"><span data-stu-id="9702d-110">Message Grouping Example</span></span>  
 <span data-ttu-id="9702d-111">Bir örnek iletileri, bir WCF hizmeti olarak bir sıra işleme uygulaması uygularken yararlı olduğu bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="9702d-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="9702d-112">Örneğin, bir istemci bu uygulamaya bir dizi öğe içeren bir sıra gönderir.</span><span class="sxs-lookup"><span data-stu-id="9702d-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="9702d-113">İstemci, her öğe için hizmete bir çağrı yapar ve bu, ayrı bir ileti gönderilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="9702d-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="9702d-114">İlk öğeyi almak için A hizmeti ve ikinci öğeyi almak için sunucu B 'yi sağlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9702d-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="9702d-115">Her öğe eklendiğinde, bu öğeyi işleyen sunucu uygun siparişi bulmak ve öğeyi bu öğeye eklemek için çok verimsiz bir işlem olur.</span><span class="sxs-lookup"><span data-stu-id="9702d-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="9702d-116">Yalnızca tüm istekleri işleyen tek bir sunucu ile bu verimsizlikleri içinde çalışmaya devam edersiniz, çünkü sunucu işlenmekte olan tüm siparişlerin izlenmesini ve yeni öğenin ait olduğunu tespit etmelidir.</span><span class="sxs-lookup"><span data-stu-id="9702d-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="9702d-117">Tek bir sıraya yönelik tüm isteklerin gruplandırılması, bu tür bir uygulamanın uygulanmasını büyük ölçüde basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="9702d-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="9702d-118">İstemci uygulaması tüm öğeleri bir oturumda tek bir sıraya gönderir; bu nedenle hizmet siparişi işlediğinde, tüm oturumu aynı anda işler.</span><span class="sxs-lookup"><span data-stu-id="9702d-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="9702d-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9702d-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="9702d-120">Oturumları kullanmak üzere bir hizmet sözleşmesi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9702d-120">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="9702d-121">Oturum gerektiren bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9702d-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="9702d-122">Şunu belirterek bunu özniteliğiyle yapın: <xref:System.ServiceModel.ServiceContractAttribute></span><span class="sxs-lookup"><span data-stu-id="9702d-122">Do this with the <xref:System.ServiceModel.ServiceContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="9702d-123">Bu yöntemlerin hiçbir şey döndürmediği için sözleşmede işlemleri tek yönlü olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="9702d-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="9702d-124">Bu, <xref:System.ServiceModel.OperationContractAttribute> özniteliği belirtilerek yapılır:</span><span class="sxs-lookup"><span data-stu-id="9702d-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="9702d-125">Hizmet sözleşmesini uygulayın ve bir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>' i belirtin.</span><span class="sxs-lookup"><span data-stu-id="9702d-125">Implement the service contract and specify an <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9702d-126">Bu, her oturum için hizmeti yalnızca bir kez başlatır.</span><span class="sxs-lookup"><span data-stu-id="9702d-126">This instantiates the service only once for each session.</span></span>  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="9702d-127">Her hizmet işlemi için bir işlem gerekir.</span><span class="sxs-lookup"><span data-stu-id="9702d-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="9702d-128">Bunu <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliğiyle birlikte belirtin.</span><span class="sxs-lookup"><span data-stu-id="9702d-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="9702d-129">İşlemi tamamlayan işlem de olarak <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> `true`ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9702d-129">The operation that completes the transaction should also set <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> to `true`.</span></span>  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. <span data-ttu-id="9702d-130">Sistem tarafından sağlanmış `NetMsmqBinding` bağlamayı kullanan bir uç nokta yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="9702d-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="9702d-131">Kullanarak <xref:System.Messaging>bir işlem kuyruğu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9702d-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="9702d-132">Kuyruğu Message Queuing (MSMQ) veya MMC kullanarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9702d-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="9702d-133">Bunu yaparsanız, bir işlem kuyruğu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9702d-133">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="9702d-134">Kullanarak <xref:System.ServiceModel.ServiceHost>hizmet için bir hizmet ana bilgisayarı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9702d-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="9702d-135">Hizmeti kullanılabilir hale getirmek için hizmet ana bilgisayarını açın.</span><span class="sxs-lookup"><span data-stu-id="9702d-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="9702d-136">Hizmet konağını kapatın.</span><span class="sxs-lookup"><span data-stu-id="9702d-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="9702d-137">Bir istemciyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9702d-137">To set up a client</span></span>  
  
1. <span data-ttu-id="9702d-138">İşlemsel sıraya yazılacak bir işlem kapsamı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9702d-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="9702d-139">[ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ARACıNı kullanarak WCF istemcisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9702d-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="9702d-140">Siparişi yerleştir.</span><span class="sxs-lookup"><span data-stu-id="9702d-140">Place the order.</span></span>  
  
4. <span data-ttu-id="9702d-141">WCF istemcisini kapatın.</span><span class="sxs-lookup"><span data-stu-id="9702d-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9702d-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="9702d-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9702d-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9702d-143">Description</span></span>  
 <span data-ttu-id="9702d-144">Aşağıdaki örnek, `IProcessOrder` hizmetine ve bu hizmeti kullanan bir istemciye yönelik kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9702d-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="9702d-145">WCF 'nin gruplandırma davranışını sağlamak için sıraya alınan oturumları nasıl kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9702d-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="9702d-146">Hizmet kodu</span><span class="sxs-lookup"><span data-stu-id="9702d-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="9702d-147">Istemci için kod</span><span class="sxs-lookup"><span data-stu-id="9702d-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="9702d-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9702d-148">See also</span></span>

- [<span data-ttu-id="9702d-149">Oturumlar ve Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="9702d-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [<span data-ttu-id="9702d-150">Kuyruklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9702d-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
