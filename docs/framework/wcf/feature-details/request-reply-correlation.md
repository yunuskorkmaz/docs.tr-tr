---
description: 'Hakkında daha fazla bilgi edinin: Request-Reply bağıntı'
title: İstek-Yanıt Bağıntısı
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: e745c9061f227e08400973f43613da73e68c8d70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632847"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="0f4ca-103">İstek-Yanıt Bağıntısı</span><span class="sxs-lookup"><span data-stu-id="0f4ca-103">Request-Reply Correlation</span></span>

<span data-ttu-id="0f4ca-104">İstek-Yanıt Bağıntısı, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> iş akışı hizmetinde iki yönlü bir işlem ve <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> başka bir Web hizmetinde iki yönlü bir işlem çağıran bir çifte bir çifte birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-104">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="0f4ca-105">Bir WCF hizmetinde iki yönlü bir işlem çağrılırken, hizmet geleneksel bir zorunlu kod tabanlı Windows Communication Foundation (WCF) hizmeti olabilir veya bir iş akışı hizmeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-105">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="0f4ca-106">İstek-yanıt bağıntısını kullanmak için iki yönlü bir bağlama kullanılmalıdır, örneğin <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="0f4ca-106">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="0f4ca-107">İki yönlü bir işlemi çağırarak veya uyguladığınızda, bağıntı başlatma adımları benzerdir ve bu bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-107">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="0f4ca-108">Alma/SendReply ile Two-Way Işleminde bağıntı kullanma</span><span class="sxs-lookup"><span data-stu-id="0f4ca-108">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  

 <span data-ttu-id="0f4ca-109"><xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Çift yönlü bir işlemi bir iş akışı hizmetinde uygulamak için bir çift kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-109">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="0f4ca-110">Çalışma zamanı, yanıtın doğru arayana dağıtılması için istek-yanıt bağıntısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-110">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="0f4ca-111">Bir iş akışı kullanılarak barındırıldığı zaman <xref:System.ServiceModel.Activities.WorkflowServiceHost> , iş akışı hizmetleri için bu durum, varsayılan bağıntı başlatması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-111">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="0f4ca-112">Bu senaryoda, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çift iş akışı tarafından kullanılır ve belirli bir bağıntı yapılandırması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-112">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="0f4ca-113">Request-Reply bağıntı açıkça başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="0f4ca-113">Explicitly Initializing Request-Reply Correlation</span></span>  

 <span data-ttu-id="0f4ca-114">Diğer iki yönlü işlemler paralel ise, bağıntı açıkça yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-114">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="0f4ca-115">Bu, <xref:System.ServiceModel.Activities.CorrelationHandle> ve <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> ' i belirterek ya da içine yerleştirerek yapılabilir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.CorrelationScope> .</span><span class="sxs-lookup"><span data-stu-id="0f4ca-115">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="0f4ca-116">Bu örnekte, istek-yanıt bağıntı bir çift üzerinde yapılandırılır <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> .</span><span class="sxs-lookup"><span data-stu-id="0f4ca-116">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="0f4ca-117">Bağıntıyı açıkça yapılandırmak yerine bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-117">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="0f4ca-118"><xref:System.ServiceModel.Activities.CorrelationScope> , <xref:System.ServiceModel.Activities.CorrelationHandle> içerdiği mesajlaşma etkinliklerini örtülü olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-118"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="0f4ca-119">Bu örnekte, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> bir çift içinde bulunur <xref:System.ServiceModel.Activities.CorrelationScope> .</span><span class="sxs-lookup"><span data-stu-id="0f4ca-119">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="0f4ca-120">Açık bağıntı yapılandırması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-120">No explicit correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 <span data-ttu-id="0f4ca-121">Ek bağıntılar gerekliyse, <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> istenen türleri kullanarak ilgili mesajlaşma etkinliklerinin özelliği kullanılarak yapılandırılabilirler `CorrelationInitializer` .</span><span class="sxs-lookup"><span data-stu-id="0f4ca-121">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="0f4ca-122">Send/ReceiveReply ile Two-Way Işleminde bağıntı kullanma</span><span class="sxs-lookup"><span data-stu-id="0f4ca-122">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  

 <span data-ttu-id="0f4ca-123"><xref:System.ServiceModel.Activities.Receive>Etkinlik yalnızca tarafından barındırılan bir iş akışı hizmetinde kullanılabilir ancak <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çift bir Web hizmetindeki yöntemi çağırması gereken herhangi bir iş akışında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-123">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="0f4ca-124">İş akışı daha sonra kullanılarak barındırılıyorsa <xref:System.ServiceModel.Activities.WorkflowServiceHost> , önceki bölümde açıklanan varsayılan bağıntı uygulanır, ancak yoksa, bağıntı doğrudan istenen <xref:System.ServiceModel.Activities.CorrelationInitializer> ve <xref:System.ServiceModel.Activities.CorrelationHandle> veya ' nin örtük tanıtıcı Yönetimi kullanılarak yapılandırılmalıdır <xref:System.ServiceModel.Activities.CorrelationScope> .</span><span class="sxs-lookup"><span data-stu-id="0f4ca-124">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="0f4ca-125">İki yönlü işlemlerle bir hizmette **hizmet başvurusu Ekle** kullanırken, etkinlik, <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> isteğe bağlı olarak istek/yanıt bağıntısı ile dahili olarak bir çift olarak sarılacağı şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0f4ca-125">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
