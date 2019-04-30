---
title: Düzen Dışı İleti İşleme
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 4e1864b25a4dbe8192cd5c692c75645bebbb92d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701248"
---
# <a name="out-of-order-message-processing"></a>Düzen Dışı İleti İşleme
İş akışı Hizmetleri, belirli bir sırada gönderilen iletiler bağlı olabilir. Bir iş akışı hizmeti bir veya daha fazla içeren <xref:System.ServiceModel.Activities.Receive> etkinlikleri ve her <xref:System.ServiceModel.Activities.Receive> etkinlik belirli bir ileti bekleniyor. Belirli taşıma teslimat garantileriyle istemciler tarafından gönderilen iletileri Gecikmeli ve bu nedenle iş akışı hizmeti beklenmedik bir sırada teslim. Uygulama iletileri gerektirmeyen bir iş akışı hizmeti içinde belirli bir gönderme sırası normalde yapılır paralel bir etkinlik kullanılarak. Daha karmaşık bir uygulama protokolü için iş akışının çok hızlı bir şekilde çok karmaşık hale gelir.  Düzen dışı ileti özelliği Windows Communication Foundation (WCF) işleme gibi tüm iç içe geçmiş paralel etkinliklerin karmaşıklık olmadan bir iş akışı oluşturmanıza olanak sağlar. Düzen dışı ileti işleme destekleyen kanalları yalnızca desteklenen <xref:System.ServiceModel.Channels.ReceiveContext> MSMQ WCF bağlamaları gibi.  
  
## <a name="enabling-out-of-order-message-processing"></a>Düzen dışı ileti işleme etkinleştirme  
 Düzen dışı ileti işleme ayarlayarak etkin <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> özelliğini `true` WorkflowService üzerinde. Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> kod özelliği.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Ayrıca uygulayabilirsiniz `AllowBufferedReceive` özniteliği bir XAML iş akışı hizmetinde aşağıdaki örnekte gösterildiği gibi.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Kuyruklar ve Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
