---
description: 'Daha fazla bilgi edinin: sıralı Ileti Işleme'
title: Düzen Dışı İleti İşleme
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 4349b7d72c080dff579eda18ce51de99ab5e91fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733612"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="1b9a6-103">Düzen Dışı İleti İşleme</span><span class="sxs-lookup"><span data-stu-id="1b9a6-103">Out-of-Order Message Processing</span></span>

<span data-ttu-id="1b9a6-104">İş akışı hizmetleri, belirli bir sırada gönderilen iletilere bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b9a6-104">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="1b9a6-105">Bir iş akışı hizmeti bir veya daha fazla etkinlik içerir <xref:System.ServiceModel.Activities.Receive> ve her <xref:System.ServiceModel.Activities.Receive> etkinlik belirli bir iletiyi bekliyor.</span><span class="sxs-lookup"><span data-stu-id="1b9a6-105">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="1b9a6-106">Belirli aktarım teslimi garantisi olmadan, istemciler tarafından gönderilen iletiler geciktirilebilir ve bu nedenle iş akışı hizmeti beklenmeyebilir bir sırayla teslim edilebilir.</span><span class="sxs-lookup"><span data-stu-id="1b9a6-106">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="1b9a6-107">İletilerin belirli bir sırada gönderilmesini gerektirmeyen bir iş akışı hizmeti uygulamak, normalde bir paralel etkinlik kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="1b9a6-107">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="1b9a6-108">Daha karmaşık bir uygulama protokolü için iş akışı çok daha karmaşık hale gelir.</span><span class="sxs-lookup"><span data-stu-id="1b9a6-108">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="1b9a6-109">Windows Communication Foundation (WCF) içindeki sıra dışı ileti işleme özelliği, iç içe paralel etkinliklerin karmaşıklığı olmadan böyle bir iş akışı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b9a6-109">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="1b9a6-110">Sıra dışı ileti işleme yalnızca WCF MSMQ bağlamaları gibi destekleyen kanallarda desteklenir <xref:System.ServiceModel.Channels.ReceiveContext> .</span><span class="sxs-lookup"><span data-stu-id="1b9a6-110">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="1b9a6-111">Sıra dışı Ileti Işlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1b9a6-111">Enabling Out-Of-Order Message Processing</span></span>  

 <span data-ttu-id="1b9a6-112"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A>Özelliği WorkflowService üzerinde olarak ayarlanarak sıra dışı ileti işleme etkinleştirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="1b9a6-112">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="1b9a6-113">Aşağıdaki örnek, koddaki özelliğinin nasıl ayarlanacağını gösterir <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> .</span><span class="sxs-lookup"><span data-stu-id="1b9a6-113">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="1b9a6-114">`AllowBufferedReceive`Aşağıdaki örnekte gösterildiği gibi, ÖZNITELIĞINI xaml içindeki bir iş akışı hizmetine de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b9a6-114">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b9a6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b9a6-115">See also</span></span>

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="1b9a6-116">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1b9a6-116">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="1b9a6-117">Kuyruklar ve Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="1b9a6-117">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
