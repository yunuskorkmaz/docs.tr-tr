---
title: Oluşturma ve bir iş akışı örneği çalıştırma
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 3bfcde3dd635820fa66d639134a43e5e43186c17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513692"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="41185-102">Oluşturma ve bir iş akışı örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="41185-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="41185-103">Bu örnek, bir iş akışı örneği çalıştırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41185-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="41185-104">Zaman uyumlu ve zaman uyumsuz olarak yürütülecek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="41185-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="41185-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="41185-105">Demonstrates</span></span>  
 <span data-ttu-id="41185-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="41185-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="41185-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="41185-107">Discussion</span></span>  
 <span data-ttu-id="41185-108">İlk bölümü örneğinin kullandığı <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="41185-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="41185-109">Bir iş akışını yürütmek için en temel yolu budur.</span><span class="sxs-lookup"><span data-stu-id="41185-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="41185-110">İş akışları ile yürütülen <xref:System.Activities.WorkflowInvoker.Invoke%2A> zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="41185-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="41185-111">İkinci bölümü örneğinin kullandığı <xref:System.Activities.WorkflowApplication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="41185-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="41185-112"><xref:System.Activities.WorkflowApplication> çalışan bir iş akışı ile etkileşim kurmak için ve iş akışını zaman uyumsuz olarak çalıştırmak için yeteneği dahil olmak üzere her örneği üzerinde daha fazla denetime sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="41185-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="41185-113">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="41185-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="41185-114">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="41185-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="41185-115">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="41185-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41185-116">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="41185-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="41185-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41185-117">See Also</span></span>  
 [<span data-ttu-id="41185-118">WorkflowInvoker ve WorkflowApplication Kullanma</span><span class="sxs-lookup"><span data-stu-id="41185-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
