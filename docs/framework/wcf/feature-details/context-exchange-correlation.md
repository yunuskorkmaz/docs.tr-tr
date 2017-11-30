---
title: "Bağlam Değişimi Bağıntısı "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e21c6eb15e305584b86c35f8a3cb4a7e549b7cae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="context-exchange-correlation"></a><span data-ttu-id="1b1f5-102">Bağlam Değişimi Bağıntısı </span><span class="sxs-lookup"><span data-stu-id="1b1f5-102">Context Exchange Correlation</span></span>
<span data-ttu-id="1b1f5-103">Bağlam bağıntı açıklanan bağlam değişimi mekanizması temel [.NET bağlam değişimi protokolü belirtimi](http://go.microsoft.com/fwlink/?LinkId=166059).</span><span class="sxs-lookup"><span data-stu-id="1b1f5-103">Context correlation is based on the context exchange mechanism described in the [.NET Context Exchange Protocol Specification](http://go.microsoft.com/fwlink/?LinkId=166059).</span></span> <span data-ttu-id="1b1f5-104">Bağlam bağıntı, doğru örneğini iletileri ilişkilendirmek için iyi bilinen içerik üstbilgisi veya tanımlama bilgisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-104">Context correlation uses a well-known context header or cookie to relate messages to the correct instance.</span></span> <span data-ttu-id="1b1f5-105">Bir bağlam tabanlı gibi bağlama bağlamı bağıntı kullanılacak <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, veya <xref:System.ServiceModel.NetTcpContextBinding> için sağlanan uç kullanılmalıdır <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-105">To use context correlation, a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, or <xref:System.ServiceModel.NetTcpContextBinding> must be used on the endpoint provided to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="1b1f5-106">Bu konu bir iş akışı hizmeti Mesajlaşma etkinliklerle bağlam bağıntı kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-106">This topic explains how to use context correlation with messaging activities in a workflow service.</span></span>  
  
## <a name="using-context-correlation"></a><span data-ttu-id="1b1f5-107">Bağlam bağıntı kullanma</span><span class="sxs-lookup"><span data-stu-id="1b1f5-107">Using Context Correlation</span></span>  
 <span data-ttu-id="1b1f5-108">Bağlam bağıntı bir istemci bir iş akışı hizmeti yinelenen çağrılarını yapmanız gerekir ve bağlam bağlamaları birini kullanarak barındırılan hizmetin olmadığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-108">Context correlation is used when a client must make repeated calls into a workflow service and the service is hosted using one of the context bindings.</span></span> <span data-ttu-id="1b1f5-109">Bu tür bir bağıntı tarafından başlatılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> iş akışı hizmetinde çifti.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-109">This type of correlation is initialized by a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair in the workflow service.</span></span> <span data-ttu-id="1b1f5-110">Bağlam istemciyi yanıtla birlikte gönderilir ve sonra istemci hizmete sonraki çağrılar bu bağlamda ekler.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-110">The context is sent back to the client together with the reply, and then the client attaches this context on subsequent calls to the service.</span></span>  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a><span data-ttu-id="1b1f5-111">Bir iş akışı hizmetinde bağlam bağıntı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1b1f5-111">Configuring Context Correlation in a Workflow Service</span></span>  
 <span data-ttu-id="1b1f5-112">Bağlam bağıntı başlatıldığı kullanarak bir <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> ile ilişkili <xref:System.ServiceModel.Activities.SendReply> ilk gelen iletisini yanıtladığı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-112">Context correlation is initialized by using a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> that is associated with the <xref:System.ServiceModel.Activities.SendReply> activity that replies to the initial incoming message.</span></span> <span data-ttu-id="1b1f5-113">Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.SendReply> bağlamı bağıntı başlatmak için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-113">In the following example, the <xref:System.ServiceModel.Activities.SendReply> is configured to initialize a context correlation.</span></span>  
  
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
>  <span data-ttu-id="1b1f5-114">Bu örnekte kullanılan bağıntı gerçekte iki tür vardır: bağlam bağıntı ve istek-yanıt bağıntısı.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-114">In this example, there are actually two types of correlation being used: context correlation and request-reply correlation.</span></span> <span data-ttu-id="1b1f5-115">Böylece istemcilerden çağrılarını doğru örneğine yönlendirilecek bağlam bağıntı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-115">The context correlation is used so that calls from clients are routed to the correct instance.</span></span> <span data-ttu-id="1b1f5-116">İstek-yanıt bağıntısı tarafından kullanılan <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri birlikte iki yönlü işlemi uygulamak için bu etkinlikler tarafından modellenir.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-116">The request-reply correlation is used by the <xref:System.ServiceModel.Activities.Receive> and the <xref:System.ServiceModel.Activities.SendReply> activities together to implement the two-way operation modeled by these activities.</span></span> <span data-ttu-id="1b1f5-117">Bu örnekte, yalnızca bağlam bağıntı açıkça yapılandırılmış ve <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti örtük tarafından sağlanan varsayılan istek-yanıt bağıntısı kullanarak <xref:System.ServiceModel.Activities.CorrelationHandle> yönetimini <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-117">In this example, only the context correlation is explicitly configured, and the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is using the default request-reply correlation that is provided by the implicit <xref:System.ServiceModel.Activities.CorrelationHandle> management of <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="1b1f5-118">Kullanırken **ReceiveAndSendReply** iş akışı Tasarımcısı, istek-yanıt bağıntısı etkinlik şablonu açıkça yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-118">When using the **ReceiveAndSendReply** activity template in the workflow designer, request-reply correlation is explicitly configured.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1b1f5-119">İstek-yanıt bağıntısı ve örtük bağıntı tanıtıcısı yönetimi Bkz [istek-yanıt](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) ve [bağıntı genel bakış](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b1f5-119"> request-reply correlation and implicit correlation handle management, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) and [Correlation Overview](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1b1f5-120">**ReceiveAndSendReply** etkinlik şablonu bkz [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span><span class="sxs-lookup"><span data-stu-id="1b1f5-120"> the **ReceiveAndSendReply** activity template, see [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span></span>  
  
 <span data-ttu-id="1b1f5-121">Sonraki <xref:System.ServiceModel.Activities.Receive> iş akışı hizmetinde etkinlikleri başvuru <xref:System.ServiceModel.Activities.CorrelationHandle> , başlatılmış tarafından <xref:System.ServiceModel.Activities.SendReply> önceki örnekte.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-121">Subsequent <xref:System.ServiceModel.Activities.Receive> activities in the workflow service can reference the <xref:System.ServiceModel.Activities.CorrelationHandle> that was initialized by the <xref:System.ServiceModel.Activities.SendReply> in the previous example.</span></span>  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 <span data-ttu-id="1b1f5-122">Uç nokta sonra yapılandırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir bağlam tabanlı, gibi bağlama kullanmak için <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-122">The endpoint is then configured on the <xref:System.ServiceModel.Activities.WorkflowServiceHost> to use a context-based binding, such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span>  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a><span data-ttu-id="1b1f5-123">Bir iş akışı istemcisinde bağlam bağıntı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1b1f5-123">Configuring Context Correlation in a Workflow Client</span></span>  
 <span data-ttu-id="1b1f5-124">İstemci başka bir iş akışı olduğunda, bağlam bağıntı istemcide yapılandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-124">When the client is another workflow, context correlation must be configured on the client as well.</span></span> <span data-ttu-id="1b1f5-125">İstemci akışında <xref:System.ServiceModel.Activities.ReceiveReply> , <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> iş akışı hizmeti ilk çağrıda çifti ile yapılandırılması gerekir bir <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-125">On the client workflow, the <xref:System.ServiceModel.Activities.ReceiveReply> of the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that makes the initial call to the workflow service must be configured with a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span></span>  
  
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
  
 <span data-ttu-id="1b1f5-126">Bağıntı sonra başlatılmış, sonraki <xref:System.ServiceModel.Activities.Send> etkinlikleri kullanma <xref:System.ServiceModel.Activities.CorrelationHandle> aynı hizmet örneği üzerinde yöntemleri çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-126">After the correlation is initialized, subsequent <xref:System.ServiceModel.Activities.Send> activities can use the <xref:System.ServiceModel.Activities.CorrelationHandle> to invoke methods on the same service instance.</span></span>  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 <span data-ttu-id="1b1f5-127">Bu örneklerde, bağlam bağıntı açıkça yapılandırıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-127">Note that in these examples, the context correlation has been explicitly configured.</span></span> <span data-ttu-id="1b1f5-128">İstemci iş akışı ayrıca içinde barındırılmıyorsa bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>, etkinlikleri içerdiği sürece bağıntı açıkça, yapılandırılmalıdır sonra bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-128">If the client workflow is not also hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, then correlation must be explicitly configured, unless the activities are contained within a <xref:System.ServiceModel.Activities.CorrelationScope> activity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1b1f5-129">bağlam bağıntı bkz [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) örnek.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-129"> context correlation, see the [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) sample.</span></span>  
  
 <span data-ttu-id="1b1f5-130">İş akışı hizmeti çağrıları yapma istemci bir iş akışı değilse, bunu açıkça geri iş akışı hizmeti için ilk çağrısından döndürülen bağlam geçirir sürece sonra bunu hala yinelenen aramaları yapabilir.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-130">If the client that is making calls to the workflow service is not a workflow, then it can still make repeated calls as long as it explicitly passes back the context that is returned from the first call to the workflow service.</span></span> <span data-ttu-id="1b1f5-131">Hizmet başvuru ekleyerek oluşturulan proxy'leri [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] depolamak ve varsayılan olarak bu bağlamda geçer.</span><span class="sxs-lookup"><span data-stu-id="1b1f5-131">Proxies generated by adding a service reference in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] store and pass this context by default.</span></span>
