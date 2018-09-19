---
title: WorkflowInstanceID alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 6725ed92bf785e5b7f7d61332944fcce8427388a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007288"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="685ba-102">WorkflowInstanceID alma</span><span class="sxs-lookup"><span data-stu-id="685ba-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="685ba-103">Bu örnek özel etkinlik kullanma işlemini gösterir `GetWorkflowInstanceId` iş akışı örnek kimliğini döndürmek için</span><span class="sxs-lookup"><span data-stu-id="685ba-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="685ba-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="685ba-104">Demonstrates</span></span>  
 <span data-ttu-id="685ba-105">Özel Etkinlik geliştirme iş akışı örneği erişme.</span><span class="sxs-lookup"><span data-stu-id="685ba-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="685ba-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="685ba-106">Discussion</span></span>  
 <span data-ttu-id="685ba-107">Çalışan bir iş akışı örnek kimliği başarmak için kod yazma gerekir.</span><span class="sxs-lookup"><span data-stu-id="685ba-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="685ba-108">Tam bildirim temelli bir iş akışını yazmak istiyorsanız, tam bildirim temelli bir iş akışı yazma deneyimini sağlamak için iş akışı içinde iş akışı örnek Kimliğini döndürebilir ve böylece etkinlik başvurulabilen bir etkinlik gerekir.</span><span class="sxs-lookup"><span data-stu-id="685ba-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="685ba-109">Örnek kimliği birçok senaryo erişmesi: günlüğe kaydetme veya denetim amacıyla veya örnek kimliği bir istemciye sağlayarak gelecekteki ilişkilendirme için uygulama düzeyi bağıntısı yapmak için birkaç örnek verilmiştir (Bu etkinliği içinde kullanarak örneğin, bir SendReply etkinliği).</span><span class="sxs-lookup"><span data-stu-id="685ba-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="685ba-110">`GetWorkflowInstanceId` olarak uygulanan bir <xref:System.Activities.CodeActivity%601> türünde bir değer döndürmesi gerekir çünkü <xref:System.Guid>, ve erişimi bulunmalıdır <xref:System.Activities.CodeActivityContext> iş akışının almak için örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="685ba-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="685ba-111">Uygulanması oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="685ba-111">Its implementation is fairly basic.</span></span>  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="685ba-112">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="685ba-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="685ba-113">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="685ba-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="685ba-114">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="685ba-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="685ba-115">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="685ba-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
