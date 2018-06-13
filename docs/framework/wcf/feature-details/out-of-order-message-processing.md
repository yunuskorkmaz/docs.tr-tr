---
title: Düzen Dışı İleti İşleme
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: a7839b60dbad7919a644c196a1c63f6bc46fb5d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492951"
---
# <a name="out-of-order-message-processing"></a>Düzen Dışı İleti İşleme
İş akışı hizmetleri belirli bir sırada gönderilen iletiler bağlı. Bir veya daha fazla iş akışı hizmeti içeren <xref:System.ServiceModel.Activities.Receive> etkinlikleri ve her <xref:System.ServiceModel.Activities.Receive> etkinlik belirli bir ileti bekleniyor. Belirli aktarım teslim, istemciler tarafından gönderilen iletileri Gecikmeli ve bu nedenle iş akışı hizmeti beklenmedik bir sırayla teslim. İletileri gerektirmeyen bir iş akışı hizmeti uygulama özel gönderilmesini sipariş normal olarak yapılan bir paralel etkinlik kullanarak. Daha karmaşık bir uygulama protokolü için iş akışı çok hızlı bir şekilde çok karmaşık hale.  Düzen dışı ileti işleme özelliği Windows Communication Foundation (WCF) gibi bir iş akışı tüm iç içe geçmiş paralel etkinliklerin karmaşıklık olmadan oluşturmanıza olanak sağlar. Düzen dışı ileti işleme destekleyen kanalları yalnızca desteklenen <xref:System.ServiceModel.Channels.ReceiveContext> WCF MSMQ bağlamaları gibi.  
  
## <a name="enabling-out-of-order-message-processing"></a>Düzen dışı ileti işleme etkinleştirme  
 Düzen dışı ileti işleme ayarlayarak etkin <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> özelliğine `true` WorkflowService üzerinde. Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> kodda özelliği.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Ayrıca uygulayabilirsiniz `AllowBufferedReceive` özniteliğini XAML iş akışı hizmetinde aşağıdaki örnekte gösterildiği gibi.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Kuyruklar ve Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
