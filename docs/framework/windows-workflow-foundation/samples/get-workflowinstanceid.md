---
description: 'Hakkında daha fazla bilgi edinin: WorkflowInstanceId alma'
title: WorkflowInstanceId Alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 3be6c36e6a6996a11ad1e26414fa25f1e32399e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755323"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="bcc34-103">WorkflowInstanceId Alma</span><span class="sxs-lookup"><span data-stu-id="bcc34-103">Get WorkflowInstanceId</span></span>

<span data-ttu-id="bcc34-104">Bu örnek, `GetWorkflowInstanceId` iş akışı örnek kimliğini döndürmek için özel etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bcc34-104">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bcc34-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="bcc34-105">Demonstrates</span></span>  

 <span data-ttu-id="bcc34-106">Özel etkinlik geliştirme, iş akışı örneğine erişme.</span><span class="sxs-lookup"><span data-stu-id="bcc34-106">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="bcc34-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="bcc34-107">Discussion</span></span>  

 <span data-ttu-id="bcc34-108">Çalışan bir iş akışının örnek KIMLIĞINI almak için kod yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bcc34-108">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="bcc34-109">Tam bildirim temelli bir iş akışı yazmak isterseniz, etkinlik iş akışında, tam bildirim temelli bir iş akışı yazma deneyimi sağlamak üzere başvurulabilmesi için iş akışı örnek KIMLIĞINI döndürebilen bir etkinliğe ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="bcc34-109">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="bcc34-110">Birçok senaryoda örnek KIMLIĞI için erişim gerekir: birkaç örnek günlüğe kaydetme veya denetim amacıyla veya örnek KIMLIĞINI bir istemciye daha sonra ilişkilendirme için geri (örneğin, bir SendReply etkinliği içinde kullanarak) sağlayarak uygulama düzeyinde bağıntı oluşturma amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="bcc34-110">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="bcc34-111">`GetWorkflowInstanceId` , ' a bir <xref:System.Activities.CodeActivity%601> değer döndürmesi gerektiğinden <xref:System.Guid> , <xref:System.Activities.CodeActivityContext> Iş akışının örnek kimliğini almak için öğesine erişiminin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bcc34-111">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="bcc34-112">Uygulama oldukça temel.</span><span class="sxs-lookup"><span data-stu-id="bcc34-112">Its implementation is fairly basic.</span></span>  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> <span data-ttu-id="bcc34-113">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="bcc34-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bcc34-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bcc34-114">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bcc34-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bcc34-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bcc34-116">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="bcc34-116">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
