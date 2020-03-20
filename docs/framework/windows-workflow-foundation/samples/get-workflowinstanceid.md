---
title: WorkflowInstanceId Alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 8cb83fcf15b814b0ca6f7f95f1a9b8eec70185cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142738"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="e5d4d-102">WorkflowInstanceId Alma</span><span class="sxs-lookup"><span data-stu-id="e5d4d-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="e5d4d-103">Bu örnek, `GetWorkflowInstanceId` iş akışı örneği kimliğini döndürmek için özel etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e5d4d-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="e5d4d-104">Demonstrates</span></span>  
 <span data-ttu-id="e5d4d-105">Özel etkinlik geliştirme, iş akışı örneğine nasıl erişileceği.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e5d4d-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="e5d4d-106">Discussion</span></span>  
 <span data-ttu-id="e5d4d-107">Çalışan bir iş akışının örnek kimliğini almak için kod yazmak gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="e5d4d-108">Tam bildirimsel bir iş akışı yazmak istiyorsanız, tam bildirimsel iş akışı yetkilendirme deneyimi sağlamak için etkinliğin iş akışında başvurulabilmesi için iş akışı örneği kimliğini döndürebilecek bir etkinlik gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="e5d4d-109">Birçok senaryo örnek kimliğine erişim gerektirir: birkaç örnek, günlüğe kaydetme veya denetleme amacıyla veya örnek kimliğini gelecekteki ilişkilendirme için bir istemciye geri sağlayarak uygulama düzeyi korelasyonu yapmak içindir (örneğin, bu etkinliği bir SendReply etkinliği).</span><span class="sxs-lookup"><span data-stu-id="e5d4d-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="e5d4d-110">`GetWorkflowInstanceId`bir tür <xref:System.Activities.CodeActivity%601> <xref:System.Guid>değeri döndürmesi gerektiği ve iş akışının örnek <xref:System.Activities.CodeActivityContext> kimliğini almak için erişmesi gerektiği için bir olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="e5d4d-111">Uygulanması oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-111">Its implementation is fairly basic.</span></span>  
  
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
> <span data-ttu-id="e5d4d-112">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e5d4d-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e5d4d-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e5d4d-115">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5d4d-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
