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
# <a name="request-reply-correlation"></a>İstek-Yanıt Bağıntısı
İstek-yanıt korelasyon bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> iş akışı hizmetinde iki yönlü bir işlem <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> uygulamak için bir çift ve başka bir Web hizmetinde iki yönlü bir işlem çağıran bir çift ile kullanılır. Bir WCF hizmetinde iki yönlü bir işlem çağırıldığında, hizmet geleneksel zorunlu kod tabanlı Windows Communication Foundation (WCF) hizmeti veya bir iş akışı hizmeti olabilir. İstek-yanıt bağıntısı kullanmak için iki yönlü <xref:System.ServiceModel.BasicHttpBinding>bir bağlama kullanılmalıdır. İster iki yönlü bir işlem çağırın ister uygulayın, korelasyon başlatma adımları benzerdir ve bu bölümde ele alınmıştır.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Receive/SendReply ile İki Yönlü Bir İşlemde Korelasyon Kullanma  
 <xref:System.ServiceModel.Activities.Receive> / Bir <xref:System.ServiceModel.Activities.SendReply> çift, iş akışı hizmetinde iki yönlü bir işlem uygulamak için kullanılır. Çalışma süresi, yanıtın doğru arayana gönderilmesini sağlamak için istek-yanıt korelasyonuna neden olabilir. İş akışı hizmetleri için <xref:System.ServiceModel.Activities.WorkflowServiceHost>geçerli olan bir iş akışı barındırıldığında, varsayılan korelasyon başlatma yeterlidir. Bu senaryoda, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> bir çift bir iş akışı tarafından kullanılır ve belirli bir korelasyon yapılandırması gereklidir.  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>İstek-Yanıt İlişkisi'ni Açıkça Başlatma  
 Diğer iki yönlü işlemler paralelse, korelasyon açıkça yapılandırılmalıdır. Bu bir <xref:System.ServiceModel.Activities.CorrelationHandle> belirterek yapılabilir <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>ve , ya <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> da <xref:System.ServiceModel.Activities.CorrelationScope>bir içine yerleştirerek . Bu örnekte, istek-yanıt korelasyon <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> bir çift üzerinde yapılandırılır.  
  
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
  
 Korelasyon açıkça yapılandırılma <xref:System.ServiceModel.Activities.CorrelationScope> yerine, bir etkinlik kullanılabilir. <xref:System.ServiceModel.Activities.CorrelationScope>içerdiği ileti <xref:System.ServiceModel.Activities.CorrelationHandle> etkinliklerine örtülü olarak yer alır. Bu örnekte, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> bir çift <xref:System.ServiceModel.Activities.CorrelationScope>içinde yer alan . Açık bir korelasyon yapılandırması gerekmez.  
  
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
  
 Ek korelasyonlar gerekiyorsa, istenilen <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> `CorrelationInitializer` türleri kullanarak ilgili ileti etkinliklerinin özelliği kullanılarak yapılandırılabilir.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Gönder/Al Yanıtla İki Yönlü Bir İşlemde Korelasyon Kullanma  
 <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.WorkflowServiceHost>Etkinlik yalnızca barındırılan bir iş akışı hizmetinde <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> kullanılabilirken ve çift, Web hizmetinde bir yöntem çağırması gereken herhangi bir iş akışında kullanılabilir. İş akışı önceki bölümde <xref:System.ServiceModel.Activities.WorkflowServiceHost> açıklanan varsayılan korelasyon kullanılarak barındırılırsa, ancak yoksa, korelasyon açıkça istenilen <xref:System.ServiceModel.Activities.CorrelationInitializer> kullanılarak <xref:System.ServiceModel.Activities.CorrelationHandle>ve , ya da örtülü tutamaç yönetimi kullanılarak yapılandırılmalıdır . <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 İki yönlü işlemleri olan bir hizmette **Hizmet Başvurusu Ekle'yi** kullanırken, açıkça belirtilen İstek/Yanıt korelasyonla bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çifti dahili olarak saran etkinlikler oluşturulur.
