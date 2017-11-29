---
title: WorkflowInstanceID Al
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f1eb6a1d9cd875d0332bb1d59933f75c807f74e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="5e76b-102">WorkflowInstanceID Al</span><span class="sxs-lookup"><span data-stu-id="5e76b-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="5e76b-103">Bu örnek özel etkinlik kullanımı gösterilmiştir `GetWorkflowInstanceId` iş akışı örneği kimliğine döndürmek için</span><span class="sxs-lookup"><span data-stu-id="5e76b-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5e76b-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="5e76b-104">Demonstrates</span></span>  
 <span data-ttu-id="5e76b-105">Özel Etkinlik geliştirme iş akışı örneği erişim.</span><span class="sxs-lookup"><span data-stu-id="5e76b-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5e76b-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="5e76b-106">Discussion</span></span>  
 <span data-ttu-id="5e76b-107">Çalışan bir iş akışı örneği kimliği alma kod yazma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5e76b-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="5e76b-108">Tam bildirim temelli bir iş akışını yazmak istiyorsanız, iş akışı örneği kimliği yazma deneyimini tam bildirim temelli bir iş akışı sağlamak için iş akışı içinde döndürebilir ve böylece etkinliğin başvurulamıyor aktivite gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e76b-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="5e76b-109">Birçok senaryo örneği kimliği erişmesi: günlüğü veya denetim amacıyla ya da bir istemcisine geri gelecekteki ilişkilendirme için örnek kimliği sağlayarak uygulama düzeyi bağıntı yapmak için birkaç örnek verilmiştir (Bu etkinliği içinde kullanarak örneğin, bir SendReply etkinliği).</span><span class="sxs-lookup"><span data-stu-id="5e76b-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="5e76b-110">`GetWorkflowInstanceId`olarak uygulanan bir <xref:System.Activities.CodeActivity%601> türünde bir değer döndürmesi gerekir çünkü <xref:System.Guid>, ve erişimi olmalıdır <xref:System.Activities.CodeActivityContext> iş akışının almak için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="5e76b-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="5e76b-111">Uygulaması oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="5e76b-111">Its implementation is fairly basic.</span></span>  
  
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
>  <span data-ttu-id="5e76b-112">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e76b-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5e76b-113">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5e76b-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5e76b-114">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5e76b-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e76b-115">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5e76b-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
