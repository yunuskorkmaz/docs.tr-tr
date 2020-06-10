---
title: Düzen Dışı İleti İşleme
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 7930f26cf5957158a16d65085267cf1bab2e4504
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598729"
---
# <a name="out-of-order-message-processing"></a>Düzen Dışı İleti İşleme
İş akışı hizmetleri, belirli bir sırada gönderilen iletilere bağlı olabilir. Bir iş akışı hizmeti bir veya daha fazla etkinlik içerir <xref:System.ServiceModel.Activities.Receive> ve her <xref:System.ServiceModel.Activities.Receive> etkinlik belirli bir iletiyi bekliyor. Belirli aktarım teslimi garantisi olmadan, istemciler tarafından gönderilen iletiler geciktirilebilir ve bu nedenle iş akışı hizmeti beklenmeyebilir bir sırayla teslim edilebilir. İletilerin belirli bir sırada gönderilmesini gerektirmeyen bir iş akışı hizmeti uygulamak, normalde bir paralel etkinlik kullanılarak yapılır. Daha karmaşık bir uygulama protokolü için iş akışı çok daha karmaşık hale gelir.  Windows Communication Foundation (WCF) içindeki sıra dışı ileti işleme özelliği, iç içe paralel etkinliklerin karmaşıklığı olmadan böyle bir iş akışı oluşturmanıza olanak sağlar. Sıra dışı ileti işleme yalnızca WCF MSMQ bağlamaları gibi destekleyen kanallarda desteklenir <xref:System.ServiceModel.Channels.ReceiveContext> .  
  
## <a name="enabling-out-of-order-message-processing"></a>Sıra dışı Ileti Işlemeyi etkinleştirme  
 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A>Özelliği WorkflowService üzerinde olarak ayarlanarak sıra dışı ileti işleme etkinleştirilir `true` . Aşağıdaki örnek, koddaki özelliğinin nasıl ayarlanacağını gösterir <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> .  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 `AllowBufferedReceive`Aşağıdaki örnekte gösterildiği gibi, ÖZNITELIĞINI xaml içindeki bir iş akışı hizmetine de uygulayabilirsiniz.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [İş Akışı Hizmetleri](workflow-services.md)
- [Kuyruklar ve Güvenilir Oturumlar](queues-and-reliable-sessions.md)
