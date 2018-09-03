---
title: 'Bağlam Değişimi Bağıntısı '
ms.date: 03/30/2017
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
ms.openlocfilehash: d9de111fa08b4a398bba52bc903ea1fec8c7f298
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483703"
---
# <a name="context-exchange-correlation"></a><span data-ttu-id="b3b3a-102">Bağlam Değişimi Bağıntısı </span><span class="sxs-lookup"><span data-stu-id="b3b3a-102">Context Exchange Correlation</span></span>
<span data-ttu-id="b3b3a-103">Bağlam bağıntı açıklanan bağlam değişimi mekanizması temel [.NET bağlam değişimi protokolü belirtimi](https://go.microsoft.com/fwlink/?LinkId=166059).</span><span class="sxs-lookup"><span data-stu-id="b3b3a-103">Context correlation is based on the context exchange mechanism described in the [.NET Context Exchange Protocol Specification](https://go.microsoft.com/fwlink/?LinkId=166059).</span></span> <span data-ttu-id="b3b3a-104">Bağlam bağıntı iletileri doğru örneğini ilişkilendirmek için iyi bilinen bağlam üst bilgi veya tanımlama bilgisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-104">Context correlation uses a well-known context header or cookie to relate messages to the correct instance.</span></span> <span data-ttu-id="b3b3a-105">Bir bağlam tabanlı gibi bağlama, bağlam bağıntı kullanılacak <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, veya <xref:System.ServiceModel.NetTcpContextBinding> sağlanan uç nokta üzerinde kullanılmalıdır <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-105">To use context correlation, a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, or <xref:System.ServiceModel.NetTcpContextBinding> must be used on the endpoint provided to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="b3b3a-106">Bu konuda, Mesajlaşma etkinlikleriyle iş akışı hizmeti içinde bağlam bağıntı kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-106">This topic explains how to use context correlation with messaging activities in a workflow service.</span></span>  
  
## <a name="using-context-correlation"></a><span data-ttu-id="b3b3a-107">Bağlam bağıntı kullanma</span><span class="sxs-lookup"><span data-stu-id="b3b3a-107">Using Context Correlation</span></span>  
 <span data-ttu-id="b3b3a-108">Bir istemci, yinelenen bir iş akışı hizmeti çağrılarını yapmanız gerekir ve bağlam bağlamaları birini kullanarak barındırılan Hizmet bağlamı bağıntı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-108">Context correlation is used when a client must make repeated calls into a workflow service and the service is hosted using one of the context bindings.</span></span> <span data-ttu-id="b3b3a-109">Bu tür bir bağıntı tarafından başlatılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti içindeki iş akışı hizmeti.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-109">This type of correlation is initialized by a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair in the workflow service.</span></span> <span data-ttu-id="b3b3a-110">Bağlam istemcisine yanıtla birlikte gönderilir ve ardından istemci hizmeti arka arkaya çağrı bu bağlam ekler.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-110">The context is sent back to the client together with the reply, and then the client attaches this context on subsequent calls to the service.</span></span>  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a><span data-ttu-id="b3b3a-111">Bir iş akışı hizmetinde bağlam bağıntı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b3b3a-111">Configuring Context Correlation in a Workflow Service</span></span>  
 <span data-ttu-id="b3b3a-112">Bağlam bağıntı kullanarak tarafından başlatılan bir <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> ilişkili <xref:System.ServiceModel.Activities.SendReply> ilk gelen iletiye yanıt etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-112">Context correlation is initialized by using a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> that is associated with the <xref:System.ServiceModel.Activities.SendReply> activity that replies to the initial incoming message.</span></span> <span data-ttu-id="b3b3a-113">Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.SendReply> bağlam bağıntı başlatmak üzere yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-113">In the following example, the <xref:System.ServiceModel.Activities.SendReply> is configured to initialize a context correlation.</span></span>  
  
```csharp  
Variable<string> Item = new Variable<string>();  
Variable<CorrelationHandle> OrderHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IOrderService",  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    CorrelationInitializers =  
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = OrderHandle  
        }  
    }  
};  
```  
  
> [!NOTE]
>  <span data-ttu-id="b3b3a-114">Bu örnekte kullanılan bağıntı aslında iki tür vardır: bağlam bağıntı ve istek-yanıt bağıntısı.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-114">In this example, there are actually two types of correlation being used: context correlation and request-reply correlation.</span></span> <span data-ttu-id="b3b3a-115">İstemcilerden gelen çağrıları doğru örneğini yönlendirilebilmesi bağlam bağıntı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-115">The context correlation is used so that calls from clients are routed to the correct instance.</span></span> <span data-ttu-id="b3b3a-116">İstek-yanıt bağıntısı tarafından kullanılan <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler birlikte iki yönlü işlemi uygulamak için bu etkinlikleri tarafından modellenir.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-116">The request-reply correlation is used by the <xref:System.ServiceModel.Activities.Receive> and the <xref:System.ServiceModel.Activities.SendReply> activities together to implement the two-way operation modeled by these activities.</span></span> <span data-ttu-id="b3b3a-117">Bu örnekte, yalnızca bağlam bağıntı açıkça yapılandırılmış ve <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çiftini örtük tarafından sağlanan varsayılan istek-yanıt bağıntısı kullanarak <xref:System.ServiceModel.Activities.CorrelationHandle> yönetimini <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-117">In this example, only the context correlation is explicitly configured, and the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is using the default request-reply correlation that is provided by the implicit <xref:System.ServiceModel.Activities.CorrelationHandle> management of <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="b3b3a-118">Kullanırken **ReceiveAndSendReply** etkinlik iş akışı Tasarımcısı, istek-yanıt bağıntısı şablonda açıkça yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-118">When using the **ReceiveAndSendReply** activity template in the workflow designer, request-reply correlation is explicitly configured.</span></span> <span data-ttu-id="b3b3a-119">İstek-yanıt bağıntısı ve örtük bağıntı tanıtıcısı yönetimi hakkında daha fazla bilgi için bkz. [istek-yanıt](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) ve [bağıntı genel bakış](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b3b3a-119">For more information about request-reply correlation and implicit correlation handle management, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) and [Correlation Overview](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span></span> <span data-ttu-id="b3b3a-120">Hakkında daha fazla bilgi için **ReceiveAndSendReply** etkinlik şablonu görmek [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span><span class="sxs-lookup"><span data-stu-id="b3b3a-120">For more information about the **ReceiveAndSendReply** activity template, see [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span></span>  
  
 <span data-ttu-id="b3b3a-121">Sonraki <xref:System.ServiceModel.Activities.Receive> etkinlikleri iş akışı hizmeti içinde başvurabilir <xref:System.ServiceModel.Activities.CorrelationHandle> , başlatılan tarafından <xref:System.ServiceModel.Activities.SendReply> önceki örnekte.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-121">Subsequent <xref:System.ServiceModel.Activities.Receive> activities in the workflow service can reference the <xref:System.ServiceModel.Activities.CorrelationHandle> that was initialized by the <xref:System.ServiceModel.Activities.SendReply> in the previous example.</span></span>  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 <span data-ttu-id="b3b3a-122">Uç nokta üzerinde yapılandırılır <xref:System.ServiceModel.Activities.WorkflowServiceHost> Bağlam tabanlı, gibi bağlama kullanılacak <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-122">The endpoint is then configured on the <xref:System.ServiceModel.Activities.WorkflowServiceHost> to use a context-based binding, such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span>  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a><span data-ttu-id="b3b3a-123">Bir iş akışı istemcisinde bağlam bağıntı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b3b3a-123">Configuring Context Correlation in a Workflow Client</span></span>  
 <span data-ttu-id="b3b3a-124">İstemci başka bir iş akışı olduğunda, bağlam bağıntı istemcide yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-124">When the client is another workflow, context correlation must be configured on the client as well.</span></span> <span data-ttu-id="b3b3a-125">İstemci iş akışındaki <xref:System.ServiceModel.Activities.ReceiveReply> , <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> iş akışı hizmeti ilk çağrıda çifti ile yapılandırılması gerekir bir <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-125">On the client workflow, the <xref:System.ServiceModel.Activities.ReceiveReply> of the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that makes the initial call to the workflow service must be configured with a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span></span>  
  
```csharp  
Variable<CorrelationHandle> cchandle = new Variable<CorrelationHandle>();  
Send request = new Send  
{  
    // Activity configuration omitted.  
};  
  
ReceiveReply reply = new ReceiveReply  
{  
    Request = request,  
    CorrelationInitializers =   
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = cchandle  
        }  
    }  
};  
```  
  
 <span data-ttu-id="b3b3a-126">Bağıntı sonra başlatılmış, sonraki <xref:System.ServiceModel.Activities.Send> etkinlikleri kullanma <xref:System.ServiceModel.Activities.CorrelationHandle> aynı hizmet örneği üzerinde yöntem çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-126">After the correlation is initialized, subsequent <xref:System.ServiceModel.Activities.Send> activities can use the <xref:System.ServiceModel.Activities.CorrelationHandle> to invoke methods on the same service instance.</span></span>  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 <span data-ttu-id="b3b3a-127">Bu örneklerde, bağlam bağıntı açıkça yapılandırılmış olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-127">Note that in these examples, the context correlation has been explicitly configured.</span></span> <span data-ttu-id="b3b3a-128">İstemci iş akışı da içinde barındırılmaması durumunda bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>, etkinlikleri içerdiği sürece bağıntı açıkça, yapılandırılmalıdır bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-128">If the client workflow is not also hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, then correlation must be explicitly configured, unless the activities are contained within a <xref:System.ServiceModel.Activities.CorrelationScope> activity.</span></span> <span data-ttu-id="b3b3a-129">Bağlam bağıntı hakkında daha fazla bilgi için bkz: [NetContextExchangeCorrelation](https://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) örnek.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-129">For more information about context correlation, see the [NetContextExchangeCorrelation](https://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) sample.</span></span>  
  
 <span data-ttu-id="b3b3a-130">İş akışı hizmetine çağrı yapan istemcinin bir iş akışı değilse, onu açıkça geri iş akışı hizmeti ilk çağrısından döndürülen bağlamı geçirir sürece ardından, hala yinelenen çağrıları zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-130">If the client that is making calls to the workflow service is not a workflow, then it can still make repeated calls as long as it explicitly passes back the context that is returned from the first call to the workflow service.</span></span> <span data-ttu-id="b3b3a-131">Bir hizmet başvurusu ekleyerek oluşturulan Proxy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] depolayabilir ve varsayılan olarak bu bağlamı.</span><span class="sxs-lookup"><span data-stu-id="b3b3a-131">Proxies generated by adding a service reference in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] store and pass this context by default.</span></span>
