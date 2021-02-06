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
# <a name="request-reply-correlation"></a>İstek-Yanıt Bağıntısı

İstek-Yanıt Bağıntısı, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> iş akışı hizmetinde iki yönlü bir işlem ve <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> başka bir Web hizmetinde iki yönlü bir işlem çağıran bir çifte bir çifte birlikte kullanılır. Bir WCF hizmetinde iki yönlü bir işlem çağrılırken, hizmet geleneksel bir zorunlu kod tabanlı Windows Communication Foundation (WCF) hizmeti olabilir veya bir iş akışı hizmeti olabilir. İstek-yanıt bağıntısını kullanmak için iki yönlü bir bağlama kullanılmalıdır, örneğin <xref:System.ServiceModel.BasicHttpBinding> . İki yönlü bir işlemi çağırarak veya uyguladığınızda, bağıntı başlatma adımları benzerdir ve bu bölümde ele alınmıştır.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Alma/SendReply ile Two-Way Işleminde bağıntı kullanma  

 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Çift yönlü bir işlemi bir iş akışı hizmetinde uygulamak için bir çift kullanılır. Çalışma zamanı, yanıtın doğru arayana dağıtılması için istek-yanıt bağıntısını kullanır. Bir iş akışı kullanılarak barındırıldığı zaman <xref:System.ServiceModel.Activities.WorkflowServiceHost> , iş akışı hizmetleri için bu durum, varsayılan bağıntı başlatması yeterlidir. Bu senaryoda, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çift iş akışı tarafından kullanılır ve belirli bir bağıntı yapılandırması gerekli değildir.  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Request-Reply bağıntı açıkça başlatılıyor  

 Diğer iki yönlü işlemler paralel ise, bağıntı açıkça yapılandırılmalıdır. Bu, <xref:System.ServiceModel.Activities.CorrelationHandle> ve <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> ' i belirterek ya da içine yerleştirerek yapılabilir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.CorrelationScope> . Bu örnekte, istek-yanıt bağıntı bir çift üzerinde yapılandırılır <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> .  
  
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
  
 Bağıntıyı açıkça yapılandırmak yerine bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik kullanılabilir. <xref:System.ServiceModel.Activities.CorrelationScope> , <xref:System.ServiceModel.Activities.CorrelationHandle> içerdiği mesajlaşma etkinliklerini örtülü olarak sağlar. Bu örnekte, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> bir çift içinde bulunur <xref:System.ServiceModel.Activities.CorrelationScope> . Açık bağıntı yapılandırması gerekli değildir.  
  
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
  
 Ek bağıntılar gerekliyse, <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> istenen türleri kullanarak ilgili mesajlaşma etkinliklerinin özelliği kullanılarak yapılandırılabilirler `CorrelationInitializer` .  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Send/ReceiveReply ile Two-Way Işleminde bağıntı kullanma  

 <xref:System.ServiceModel.Activities.Receive>Etkinlik yalnızca tarafından barındırılan bir iş akışı hizmetinde kullanılabilir ancak <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çift bir Web hizmetindeki yöntemi çağırması gereken herhangi bir iş akışında kullanılabilir. İş akışı daha sonra kullanılarak barındırılıyorsa <xref:System.ServiceModel.Activities.WorkflowServiceHost> , önceki bölümde açıklanan varsayılan bağıntı uygulanır, ancak yoksa, bağıntı doğrudan istenen <xref:System.ServiceModel.Activities.CorrelationInitializer> ve <xref:System.ServiceModel.Activities.CorrelationHandle> veya ' nin örtük tanıtıcı Yönetimi kullanılarak yapılandırılmalıdır <xref:System.ServiceModel.Activities.CorrelationScope> .  
  
 İki yönlü işlemlerle bir hizmette **hizmet başvurusu Ekle** kullanırken, etkinlik, <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> isteğe bağlı olarak istek/yanıt bağıntısı ile dahili olarak bir çift olarak sarılacağı şekilde oluşturulur.
