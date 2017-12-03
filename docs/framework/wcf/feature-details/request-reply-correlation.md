---
title: "İstek-Yanıt Bağıntısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29286950cfef7d8e3e2c453bbdcc307c26e641de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="request-reply-correlation"></a>İstek-Yanıt Bağıntısı
İstek-yanıt bağıntısı ile kullanılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti ile bir iş akışı hizmeti de iki yönlü bir işlem uygulamak için bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> iki yönlü bir işlem başka bir Web çağırır çifti hizmet. İki yönlü bir işlemde çağrılırken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet, hizmet ya da bir geleneksel kesinliği kod tabanlı olabilir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti veya bir iş akışı hizmeti olabilir. İstek-yanıt bağıntısı iki yönlü bir bağlama kullanılmalıdır, gibi kullanmak için <xref:System.ServiceModel.BasicHttpBinding>. Çağırma veya iki yönlü bir işlem uygulama olup olmadığını bağıntı başlatma adımları benzerdir ve bu bölümde ele alınmıştır.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Bağıntı alma SendReply ile iki yönlü bir işlemi kullanarak  
 A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti bir iş akışı hizmetinde bir iki yönlü işlemi uygulamak için kullanılır. Çalışma zamanı istek-yanıt bağıntısı yanıtı doğru çağırana gönderilir emin olmak için kullanır. Bir iş akışı kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı hizmetleri söz konusu olduğu ve ardından varsayılan bağıntı başlatma yeterlidir. Bu senaryoda, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti, bir iş akışı tarafından kullanılır ve belirli bağıntı yapılandırması gereklidir.  
  
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
 İki yönlü diğer işlemleri paralel olarak varsa, bağıntı açıkça yapılandırılmalıdır. Bu belirterek yapılabilir bir <xref:System.ServiceModel.Activities.CorrelationHandle> ve <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, veya yerleştirerek <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> içine bir <xref:System.ServiceModel.Activities.CorrelationScope>. Bu örnekte, istek-yanıt bağıntısı yapılandırılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti.  
  
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
  
 Açıkça bağıntı yapılandırma yerine bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik kullanılabilir. <xref:System.ServiceModel.Activities.CorrelationScope>örtülü sağlar <xref:System.ServiceModel.Activities.CorrelationHandle> içerdiği Mesajlaşma etkinlikleri için. Bu örnekte, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti içinde barındırılan bir <xref:System.ServiceModel.Activities.CorrelationScope>. Hiçbir açık bağıntı yapılandırması gereklidir.  
  
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
  
 Ek bağıntıları gerekli sonra kullanılarak yapılandırılabilir <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> istenen kullanarak ilgili Mesajlaşma etkinlikleri özelliğinin `CorrelationInitializer` türleri.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Gönder/ReceiveReply ile iki yönlü bir işlemle bağıntı kullanma  
 Sırada <xref:System.ServiceModel.Activities.Receive> etkinliği yalnızca kullanılabilir tarafından barındırılan bir iş akışı hizmetinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çifti, bir Web hizmeti yöntemi çağırmanız gerekir herhangi bir iş akışında kullanılabilir. İş akışını kullanarak barındırılıyorsa <xref:System.ServiceModel.Activities.WorkflowServiceHost> önceki bölümde açıklanan varsayılan bağıntı uygulanır, ancak Aksi durumda, ardından bağıntı ya da istenen kullanılarak açıkça yapılandırılmalıdır sonra <xref:System.ServiceModel.Activities.CorrelationInitializer> ve <xref:System.ServiceModel.Activities.CorrelationHandle>, ya da örtük kullanarak yönetimini ele <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Kullanırken **hizmet Başvurusu Ekle** iki yönlü işlemleri olan bir hizmette etkinlikleri oluşturulan bu kaydırma bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> istek/yanıt bağıntı dahili etkinlikle açıkça eşleştirin Belirtilen.
