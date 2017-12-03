---
title: "Düzen Dışı İleti İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f70283e15bbfaf111c8e677641682538a2361942
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="out-of-order-message-processing"></a>Düzen Dışı İleti İşleme
İş akışı hizmetleri belirli bir sırada gönderilen iletiler bağlı. Bir veya daha fazla iş akışı hizmeti içeren <xref:System.ServiceModel.Activities.Receive> etkinlikleri ve her <xref:System.ServiceModel.Activities.Receive> etkinlik belirli bir ileti bekleniyor. Belirli aktarım teslim, istemciler tarafından gönderilen iletileri Gecikmeli ve bu nedenle iş akışı hizmeti beklenmedik bir sırayla teslim. İletileri gerektirmeyen bir iş akışı hizmeti uygulama özel gönderilmesini sipariş normal olarak yapılan bir paralel etkinlik kullanarak. Daha karmaşık bir uygulama protokolü için iş akışı çok hızlı bir şekilde çok karmaşık hale.  Düzen dışı ileti işleme özelliği [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] gibi bir iş akışı tüm iç içe geçmiş paralel etkinliklerin karmaşıklık olmadan oluşturmanıza olanak sağlar. Düzen dışı ileti işleme destekleyen kanalları yalnızca desteklenen <xref:System.ServiceModel.Channels.ReceiveContext> gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ bağlar.  
  
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
 [İş akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Kuyruklar ve güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
