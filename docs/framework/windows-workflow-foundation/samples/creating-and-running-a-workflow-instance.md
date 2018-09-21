---
title: Oluşturma ve bir iş akışı örneği çalıştırma
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 571d41194ebc98be81646fb5bfdab060225015ca
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481604"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="60d83-102">Oluşturma ve bir iş akışı örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="60d83-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="60d83-103">Bu örnek, bir iş akışı örneği çalıştırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="60d83-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="60d83-104">Bu, zaman uyumlu ve zaman uyumsuz olarak yürütmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="60d83-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="60d83-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="60d83-105">Demonstrates</span></span>  
 <span data-ttu-id="60d83-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="60d83-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="60d83-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="60d83-107">Discussion</span></span>  
 <span data-ttu-id="60d83-108">İlk bölümü örneğinin kullandığı <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="60d83-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="60d83-109">Bu, bir iş akışını yürütmek için en basit yoludur.</span><span class="sxs-lookup"><span data-stu-id="60d83-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="60d83-110">İş akışları ile yürütülen <xref:System.Activities.WorkflowInvoker.Invoke%2A> zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="60d83-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="60d83-111">İkinci bölümü örneğinin kullandığı <xref:System.Activities.WorkflowApplication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="60d83-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="60d83-112"><xref:System.Activities.WorkflowApplication> çalışan bir iş akışı ile etkileşim kurmak için ve zaman uyumsuz iş akışı çalıştırma olanağı dahil olmak üzere her bir örneği hakkında daha fazla denetime sahip olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="60d83-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="60d83-113">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="60d83-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="60d83-114">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="60d83-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="60d83-115">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="60d83-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="60d83-116">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="60d83-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="60d83-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60d83-117">See Also</span></span>  
 [<span data-ttu-id="60d83-118">WorkflowInvoker ve WorkflowApplication Kullanma</span><span class="sxs-lookup"><span data-stu-id="60d83-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
