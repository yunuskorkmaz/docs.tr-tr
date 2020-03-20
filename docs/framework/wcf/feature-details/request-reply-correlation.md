---
title: İstek-Yanıt Bağıntısı
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: 34a41a149e740faf0f3816bba2c9bd9b47d4996e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184552"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="60280-102">İstek-Yanıt Bağıntısı</span><span class="sxs-lookup"><span data-stu-id="60280-102">Request-Reply Correlation</span></span>
<span data-ttu-id="60280-103">İstek-yanıt korelasyon bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> iş akışı hizmetinde iki yönlü bir işlem <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> uygulamak için bir çift ve başka bir Web hizmetinde iki yönlü bir işlem çağıran bir çift ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60280-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="60280-104">Bir WCF hizmetinde iki yönlü bir işlem çağırıldığında, hizmet geleneksel zorunlu kod tabanlı Windows Communication Foundation (WCF) hizmeti veya bir iş akışı hizmeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="60280-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="60280-105">İstek-yanıt bağıntısı kullanmak için iki yönlü <xref:System.ServiceModel.BasicHttpBinding>bir bağlama kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60280-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="60280-106">İster iki yönlü bir işlem çağırın ister uygulayın, korelasyon başlatma adımları benzerdir ve bu bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="60280-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="60280-107">Receive/SendReply ile İki Yönlü Bir İşlemde Korelasyon Kullanma</span><span class="sxs-lookup"><span data-stu-id="60280-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="60280-108"><xref:System.ServiceModel.Activities.Receive> / Bir <xref:System.ServiceModel.Activities.SendReply> çift, iş akışı hizmetinde iki yönlü bir işlem uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60280-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="60280-109">Çalışma süresi, yanıtın doğru arayana gönderilmesini sağlamak için istek-yanıt korelasyonuna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="60280-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="60280-110">İş akışı hizmetleri için <xref:System.ServiceModel.Activities.WorkflowServiceHost>geçerli olan bir iş akışı barındırıldığında, varsayılan korelasyon başlatma yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="60280-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="60280-111">Bu senaryoda, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> bir çift bir iş akışı tarafından kullanılır ve belirli bir korelasyon yapılandırması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="60280-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="60280-112">İstek-Yanıt İlişkisi'ni Açıkça Başlatma</span><span class="sxs-lookup"><span data-stu-id="60280-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="60280-113">Diğer iki yönlü işlemler paralelse, korelasyon açıkça yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60280-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="60280-114">Bu bir <xref:System.ServiceModel.Activities.CorrelationHandle> belirterek yapılabilir <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>ve , ya <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> da <xref:System.ServiceModel.Activities.CorrelationScope>bir içine yerleştirerek .</span><span class="sxs-lookup"><span data-stu-id="60280-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="60280-115">Bu örnekte, istek-yanıt korelasyon <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> bir çift üzerinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="60280-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
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
  
 <span data-ttu-id="60280-116">Korelasyon açıkça yapılandırılma <xref:System.ServiceModel.Activities.CorrelationScope> yerine, bir etkinlik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60280-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="60280-117"><xref:System.ServiceModel.Activities.CorrelationScope>içerdiği ileti <xref:System.ServiceModel.Activities.CorrelationHandle> etkinliklerine örtülü olarak yer alır.</span><span class="sxs-lookup"><span data-stu-id="60280-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="60280-118">Bu örnekte, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> bir çift <xref:System.ServiceModel.Activities.CorrelationScope>içinde yer alan .</span><span class="sxs-lookup"><span data-stu-id="60280-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="60280-119">Açık bir korelasyon yapılandırması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="60280-119">No explicit correlation configuration is required.</span></span>  
  
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
  
 <span data-ttu-id="60280-120">Ek korelasyonlar gerekiyorsa, istenilen <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> `CorrelationInitializer` türleri kullanarak ilgili ileti etkinliklerinin özelliği kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="60280-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="60280-121">Gönder/Al Yanıtla İki Yönlü Bir İşlemde Korelasyon Kullanma</span><span class="sxs-lookup"><span data-stu-id="60280-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="60280-122"><xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.WorkflowServiceHost>Etkinlik yalnızca barındırılan bir iş akışı hizmetinde <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> kullanılabilirken ve çift, Web hizmetinde bir yöntem çağırması gereken herhangi bir iş akışında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60280-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="60280-123">İş akışı önceki bölümde <xref:System.ServiceModel.Activities.WorkflowServiceHost> açıklanan varsayılan korelasyon kullanılarak barındırılırsa, ancak yoksa, korelasyon açıkça istenilen <xref:System.ServiceModel.Activities.CorrelationInitializer> kullanılarak <xref:System.ServiceModel.Activities.CorrelationHandle>ve , ya da örtülü tutamaç yönetimi kullanılarak yapılandırılmalıdır . <xref:System.ServiceModel.Activities.CorrelationScope></span><span class="sxs-lookup"><span data-stu-id="60280-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="60280-124">İki yönlü işlemleri olan bir hizmette **Hizmet Başvurusu Ekle'yi** kullanırken, açıkça belirtilen İstek/Yanıt korelasyonla bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çifti dahili olarak saran etkinlikler oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="60280-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
