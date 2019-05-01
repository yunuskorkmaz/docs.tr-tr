---
title: İstek-Yanıt Bağıntısı
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991139"
---
# <a name="request-reply-correlation"></a>İstek-Yanıt Bağıntısı
İstek-yanıt bağıntısı ile kullanılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti ile bir iş akışı hizmeti içinde bir iki yönlü işlemini uygulamak için bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> başka bir Web iki yönlü bir işlem çağıran çifti hizmeti. İki yönlü bir WCF hizmeti işlemi çağrılırken bir hizmet ya da geleneksel olabilir kesinlik temelli kod tabanlı Windows Communication Foundation (WCF) hizmetini veya bir iş akışı hizmeti olabilir. İki yönlü bir bağlama kullanılmalıdır, gibi istek-yanıt bağıntısı kullanılacak <xref:System.ServiceModel.BasicHttpBinding>. Çağırma veya iki yönlü bir işlem uygulama bağıntı başlatma adımları benzerdir ve bu bölümde ele alınmıştır.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Alma/SendReply ile iki yönlü bir işlemde bağıntı kullanma  
 A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti, bir iş akışı hizmetinde bir iki yönlü işlemi uygulamak için kullanılır. Çalışma zamanı yanıtı doğru çağırana gönderilir emin olmak için istek-yanıt bağıntısı kullanır. Bir iş akışı kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı hizmetleri için durum ve ardından varsayılan bağıntı başlatma yeterlidir. Bu senaryoda, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti, bir iş akışı tarafından kullanılır ve belirli bağıntı yapılandırma gerekmiyor.  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>İstek-yanıt bağıntısı açıkça başlatılıyor  
 İki yönlü diğer işlemler paralel olarak ise bağıntı açıkça yapılandırılmalıdır. Bu belirterek yapılabilir bir <xref:System.ServiceModel.Activities.CorrelationHandle> ve <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, veya yerleştirerek <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> içine bir <xref:System.ServiceModel.Activities.CorrelationScope>. Bu örnekte, istek-yanıt bağıntısı üzerinde yapılandırılmış bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti.  
  
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
  
 Bağıntı açıkça yapılandırmak yerine bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik kullanılabilir. <xref:System.ServiceModel.Activities.CorrelationScope> örtük sağlar <xref:System.ServiceModel.Activities.CorrelationHandle> içerdiği ileti etkinliklere. Bu örnekte, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti içinde barındırılan bir <xref:System.ServiceModel.Activities.CorrelationScope>. Açık bağıntı yapılandırma gerekmiyor.  
  
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
  
 Ek bağıntılar gerekli sonra kullanılarak yapılandırılabilir <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> istenen kullanarak ilgili Mesajlaşma etkinlikleri özelliği `CorrelationInitializer` türleri.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Gönder/ReceiveReply olan iki yönlü bir işlem korelasyon kullanma  
 Sırada <xref:System.ServiceModel.Activities.Receive> etkinliği yalnızca kullanılabilir tarafından barındırılan bir iş akışı hizmeti içinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çifti, bir Web hizmeti yöntemini çağırmanız gerekir herhangi bir iş akışında kullanılabilir. İş akışı kullanılarak barındırılıyorsa <xref:System.ServiceModel.Activities.WorkflowServiceHost> önceki bölümde açıklanan varsayılan bağıntı geçerlidir ancak Aksi takdirde, ardından bağıntı ya da açıkça istenen kullanılarak yapılandırılması gerekir <xref:System.ServiceModel.Activities.CorrelationInitializer> ve <xref:System.ServiceModel.Activities.CorrelationHandle>, ya da örtük kullanarak Yönetimi gerçekleştirdiğine <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Kullanırken **hizmet Başvurusu Ekle** etkinlikler iki yönlü işlemleri ile bir hizmet üzerinde oluşturulan, kaydırma bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği istek/yanıt bağıntı ile dahili olarak açıkça eşleştirin. Belirtilen.
