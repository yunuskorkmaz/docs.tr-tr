---
title: WorkflowInstanceId Alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 37dc0cac9c6ac69b9e430677a9c8cf3f47b200eb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716014"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="2fa2d-102">WorkflowInstanceId Alma</span><span class="sxs-lookup"><span data-stu-id="2fa2d-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="2fa2d-103">Bu örnek, iş akışı örnek KIMLIĞINI döndürmek için `GetWorkflowInstanceId` özel etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2fa2d-104">Gösterir</span><span class="sxs-lookup"><span data-stu-id="2fa2d-104">Demonstrates</span></span>  
 <span data-ttu-id="2fa2d-105">Özel etkinlik geliştirme, iş akışı örneğine erişme.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="2fa2d-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="2fa2d-106">Discussion</span></span>  
 <span data-ttu-id="2fa2d-107">Çalışan bir iş akışının örnek KIMLIĞINI almak için kod yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="2fa2d-108">Tam bildirim temelli bir iş akışı yazmak isterseniz, etkinlik iş akışında, tam bildirim temelli bir iş akışı yazma deneyimi sağlamak üzere başvurulabilmesi için iş akışı örnek KIMLIĞINI döndürebilen bir etkinliğe ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="2fa2d-109">Birçok senaryoda örnek KIMLIĞI için erişim gerekir: birkaç örnek günlüğe kaydetme veya denetim amacıyla veya örnek KIMLIĞINI bir istemciye daha sonra ilişkilendirme için geri (örneğin, bir SendReply etkinliği).</span><span class="sxs-lookup"><span data-stu-id="2fa2d-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="2fa2d-110">`GetWorkflowInstanceId`, <xref:System.Guid>türünde bir değer döndürmesi gerektiğinden <xref:System.Activities.CodeActivity%601> olarak uygulanır ve iş akışının örnek KIMLIĞINI almak için <xref:System.Activities.CodeActivityContext> erişimine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="2fa2d-111">Uygulama oldukça temel.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-111">Its implementation is fairly basic.</span></span>  
  
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
> <span data-ttu-id="2fa2d-112">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2fa2d-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2fa2d-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fa2d-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2fa2d-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
