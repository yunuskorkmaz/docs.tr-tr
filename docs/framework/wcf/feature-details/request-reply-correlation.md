---
title: İstek-Yanıt Bağıntısı
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497210"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="e2ea6-102">İstek-Yanıt Bağıntısı</span><span class="sxs-lookup"><span data-stu-id="e2ea6-102">Request-Reply Correlation</span></span>
<span data-ttu-id="e2ea6-103">İstek-yanıt bağıntısı ile kullanılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti ile bir iş akışı hizmeti de iki yönlü bir işlem uygulamak için bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> iki yönlü bir işlem başka bir Web çağırır çifti hizmet.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="e2ea6-104">Bir WCF hizmetindeki iki yönlü bir işlem çağrılırken, hizmet ya da bir geleneksel olabilir kesinlik temelli kod tabanlı Windows Communication Foundation (WCF) hizmetini veya bir iş akışı hizmeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="e2ea6-105">İstek-yanıt bağıntısı iki yönlü bir bağlama kullanılmalıdır, gibi kullanmak için <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="e2ea6-106">Çağırma veya iki yönlü bir işlem uygulama olup olmadığını bağıntı başlatma adımları benzerdir ve bu bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="e2ea6-107">Bağıntı alma SendReply ile iki yönlü bir işlemi kullanarak</span><span class="sxs-lookup"><span data-stu-id="e2ea6-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="e2ea6-108">A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti bir iş akışı hizmetinde bir iki yönlü işlemi uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="e2ea6-109">Çalışma zamanı istek-yanıt bağıntısı yanıtı doğru çağırana gönderilir emin olmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="e2ea6-110">Bir iş akışı kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı hizmetleri söz konusu olduğu ve ardından varsayılan bağıntı başlatma yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="e2ea6-111">Bu senaryoda, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti, bir iş akışı tarafından kullanılır ve belirli bağıntı yapılandırması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="e2ea6-112">İstek-yanıt bağıntısı açıkça başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="e2ea6-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="e2ea6-113">İki yönlü diğer işlemleri paralel olarak varsa, bağıntı açıkça yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="e2ea6-114">Bu belirterek yapılabilir bir <xref:System.ServiceModel.Activities.CorrelationHandle> ve <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, veya yerleştirerek <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> içine bir <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="e2ea6-115">Bu örnekte, istek-yanıt bağıntısı yapılandırılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
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
  
 <span data-ttu-id="e2ea6-116">Açıkça bağıntı yapılandırma yerine bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="e2ea6-117"><xref:System.ServiceModel.Activities.CorrelationScope> örtülü sağlar <xref:System.ServiceModel.Activities.CorrelationHandle> içerdiği Mesajlaşma etkinlikleri için.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="e2ea6-118">Bu örnekte, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti içinde barındırılan bir <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="e2ea6-119">Hiçbir açık bağıntı yapılandırması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-119">No explicit correlation configuration is required.</span></span>  
  
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
  
 <span data-ttu-id="e2ea6-120">Ek bağıntıları gerekli sonra kullanılarak yapılandırılabilir <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> istenen kullanarak ilgili Mesajlaşma etkinlikleri özelliğinin `CorrelationInitializer` türleri.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="e2ea6-121">Gönder/ReceiveReply ile iki yönlü bir işlemle bağıntı kullanma</span><span class="sxs-lookup"><span data-stu-id="e2ea6-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="e2ea6-122">Sırada <xref:System.ServiceModel.Activities.Receive> etkinliği yalnızca kullanılabilir tarafından barındırılan bir iş akışı hizmetinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çifti, bir Web hizmeti yöntemi çağırmanız gerekir herhangi bir iş akışında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="e2ea6-123">İş akışını kullanarak barındırılıyorsa <xref:System.ServiceModel.Activities.WorkflowServiceHost> önceki bölümde açıklanan varsayılan bağıntı uygulanır, ancak Aksi durumda, ardından bağıntı ya da istenen kullanılarak açıkça yapılandırılmalıdır sonra <xref:System.ServiceModel.Activities.CorrelationInitializer> ve <xref:System.ServiceModel.Activities.CorrelationHandle>, ya da örtük kullanarak yönetimini ele <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="e2ea6-124">Kullanırken **hizmet Başvurusu Ekle** iki yönlü işlemleri olan bir hizmette etkinlikleri oluşturulan bu kaydırma bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> istek/yanıt bağıntı dahili etkinlikle açıkça eşleştirin Belirtilen.</span><span class="sxs-lookup"><span data-stu-id="e2ea6-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
