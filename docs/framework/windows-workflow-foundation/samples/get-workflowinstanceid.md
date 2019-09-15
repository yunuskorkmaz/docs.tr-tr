---
title: WorkflowInstanceId Alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: f8bd3205f5b7a4b3bae5203dc90a3c393cedcbdd
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989377"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="8a785-102">WorkflowInstanceId Alma</span><span class="sxs-lookup"><span data-stu-id="8a785-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="8a785-103">Bu örnek, `GetWorkflowInstanceId` iş akışı örnek kimliğini döndürmek için özel etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a785-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8a785-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="8a785-104">Demonstrates</span></span>  
 <span data-ttu-id="8a785-105">Özel etkinlik geliştirme, iş akışı örneğine erişme.</span><span class="sxs-lookup"><span data-stu-id="8a785-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8a785-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="8a785-106">Discussion</span></span>  
 <span data-ttu-id="8a785-107">Çalışan bir iş akışının örnek KIMLIĞINI almak için kod yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a785-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="8a785-108">Tam bildirim temelli bir iş akışı yazmak isterseniz, etkinlik iş akışında, tam bildirim temelli bir iş akışı yazma deneyimi sağlamak üzere başvurulabilmesi için iş akışı örnek KIMLIĞINI döndürebilen bir etkinliğe ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="8a785-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="8a785-109">Birçok senaryoda örnek KIMLIĞI için erişim gerekir: birkaç örnek günlüğe kaydetme veya denetim amacıyla veya örnek KIMLIĞINI bir istemciye daha sonra ilişkilendirme için geri (örneğin, bir SendReply etkinliği).</span><span class="sxs-lookup"><span data-stu-id="8a785-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="8a785-110">`GetWorkflowInstanceId`, <xref:System.Guid>' a bir <xref:System.Activities.CodeActivity%601> değer döndürmesi gerektiğinden, iş akışının örnek kimliğini almak <xref:System.Activities.CodeActivityContext> için öğesine erişiminin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a785-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="8a785-111">Uygulama oldukça temel.</span><span class="sxs-lookup"><span data-stu-id="8a785-111">Its implementation is fairly basic.</span></span>  
  
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
> <span data-ttu-id="8a785-112">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a785-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8a785-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8a785-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8a785-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="8a785-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a785-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8a785-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
