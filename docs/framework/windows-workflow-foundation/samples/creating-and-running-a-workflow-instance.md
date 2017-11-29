---
title: "Oluşturma ve bir iş akışı örneği çalıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d53becfc126f1acee4759ddff956b4435c9aa769
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="c84ea-102">Oluşturma ve bir iş akışı örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c84ea-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="c84ea-103">Bu örnek, bir iş akışı örneği çalıştırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c84ea-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="c84ea-104">Zaman uyumlu ve zaman uyumsuz olarak yürütülecek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="c84ea-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c84ea-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="c84ea-105">Demonstrates</span></span>  
 <span data-ttu-id="c84ea-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="c84ea-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c84ea-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="c84ea-107">Discussion</span></span>  
 <span data-ttu-id="c84ea-108">İlk bölümü örneğinin kullandığı <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="c84ea-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="c84ea-109">Bir iş akışını yürütmek için en temel yolu budur.</span><span class="sxs-lookup"><span data-stu-id="c84ea-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="c84ea-110">İş akışları ile yürütülen <xref:System.Activities.WorkflowInvoker.Invoke%2A> zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c84ea-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="c84ea-111">İkinci bölümü örneğinin kullandığı <xref:System.Activities.WorkflowApplication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c84ea-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="c84ea-112"><xref:System.Activities.WorkflowApplication>çalışan bir iş akışı ile etkileşim kurmak için ve iş akışını zaman uyumsuz olarak çalıştırmak için yeteneği dahil olmak üzere her örneği üzerinde daha fazla denetime sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c84ea-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c84ea-113">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c84ea-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c84ea-114">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c84ea-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c84ea-115">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c84ea-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c84ea-116">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c84ea-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="c84ea-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c84ea-117">See Also</span></span>  
 [<span data-ttu-id="c84ea-118">WorkflowInvoker ve WorkflowApplication kullanma</span><span class="sxs-lookup"><span data-stu-id="c84ea-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
