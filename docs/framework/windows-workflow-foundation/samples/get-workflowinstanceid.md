---
title: WorkflowInstanceId Alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: db06b30f24a2d620406b3e6a35bba3a1fca70a9c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251561"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="29afd-102">WorkflowInstanceId Alma</span><span class="sxs-lookup"><span data-stu-id="29afd-102">Get WorkflowInstanceId</span></span>

<span data-ttu-id="29afd-103">Bu örnek, `GetWorkflowInstanceId` iş akışı örnek kimliğini döndürmek için özel etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29afd-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="29afd-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="29afd-104">Demonstrates</span></span>  

 <span data-ttu-id="29afd-105">Özel etkinlik geliştirme, iş akışı örneğine erişme.</span><span class="sxs-lookup"><span data-stu-id="29afd-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="29afd-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="29afd-106">Discussion</span></span>  

 <span data-ttu-id="29afd-107">Çalışan bir iş akışının örnek KIMLIĞINI almak için kod yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="29afd-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="29afd-108">Tam bildirim temelli bir iş akışı yazmak isterseniz, etkinlik iş akışında, tam bildirim temelli bir iş akışı yazma deneyimi sağlamak üzere başvurulabilmesi için iş akışı örnek KIMLIĞINI döndürebilen bir etkinliğe ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="29afd-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="29afd-109">Birçok senaryoda örnek KIMLIĞI için erişim gerekir: birkaç örnek günlüğe kaydetme veya denetim amacıyla veya örnek KIMLIĞINI bir istemciye daha sonra ilişkilendirme için geri (örneğin, bir SendReply etkinliği içinde kullanarak) sağlayarak uygulama düzeyinde bağıntı oluşturma amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="29afd-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="29afd-110">`GetWorkflowInstanceId` , ' a bir <xref:System.Activities.CodeActivity%601> değer döndürmesi gerektiğinden <xref:System.Guid> , <xref:System.Activities.CodeActivityContext> Iş akışının örnek kimliğini almak için öğesine erişiminin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="29afd-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="29afd-111">Uygulama oldukça temel.</span><span class="sxs-lookup"><span data-stu-id="29afd-111">Its implementation is fairly basic.</span></span>  
  
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
> <span data-ttu-id="29afd-112">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="29afd-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="29afd-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="29afd-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="29afd-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="29afd-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="29afd-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="29afd-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
