---
title: WorkflowInstanceID Al
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: fbfaf52931345571e5125200fe467dcc098b9dc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513912"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="88e25-102">WorkflowInstanceID Al</span><span class="sxs-lookup"><span data-stu-id="88e25-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="88e25-103">Bu örnek özel etkinlik kullanımı gösterilmiştir `GetWorkflowInstanceId` iş akışı örneği kimliğine döndürmek için</span><span class="sxs-lookup"><span data-stu-id="88e25-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="88e25-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="88e25-104">Demonstrates</span></span>  
 <span data-ttu-id="88e25-105">Özel Etkinlik geliştirme iş akışı örneği erişim.</span><span class="sxs-lookup"><span data-stu-id="88e25-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="88e25-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="88e25-106">Discussion</span></span>  
 <span data-ttu-id="88e25-107">Çalışan bir iş akışı örneği kimliği alma kod yazma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="88e25-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="88e25-108">Tam bildirim temelli bir iş akışını yazmak istiyorsanız, iş akışı örneği kimliği yazma deneyimini tam bildirim temelli bir iş akışı sağlamak için iş akışı içinde döndürebilir ve böylece etkinliğin başvurulamıyor aktivite gerekir.</span><span class="sxs-lookup"><span data-stu-id="88e25-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="88e25-109">Birçok senaryo örneği kimliği erişmesi: günlüğü veya denetim amacıyla ya da bir istemcisine geri gelecekteki ilişkilendirme için örnek kimliği sağlayarak uygulama düzeyi bağıntı yapmak için birkaç örnek verilmiştir (Bu etkinliği içinde kullanarak örneğin, bir SendReply etkinliği).</span><span class="sxs-lookup"><span data-stu-id="88e25-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="88e25-110">`GetWorkflowInstanceId` olarak uygulanan bir <xref:System.Activities.CodeActivity%601> türünde bir değer döndürmesi gerekir çünkü <xref:System.Guid>, ve erişimi olmalıdır <xref:System.Activities.CodeActivityContext> iş akışının almak için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="88e25-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="88e25-111">Uygulaması oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="88e25-111">Its implementation is fairly basic.</span></span>  
  
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
>  <span data-ttu-id="88e25-112">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="88e25-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="88e25-113">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="88e25-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="88e25-114">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="88e25-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="88e25-115">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="88e25-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
