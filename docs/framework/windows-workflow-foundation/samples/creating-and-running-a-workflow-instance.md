---
title: İş Akışı Örneği Oluşturma ve Çalıştırma
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016041"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="8ba3a-102">İş Akışı Örneği Oluşturma ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8ba3a-102">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="8ba3a-103">Bu örnek, bir iş akışı örneğinin nasıl çalıştırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="8ba3a-104">Bu, zaman uyumlu ve zaman uyumsuz olarak nasıl yürütüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-104">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8ba3a-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="8ba3a-105">Demonstrates</span></span>

<span data-ttu-id="8ba3a-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="8ba3a-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="8ba3a-107">Discussion</span></span>

<span data-ttu-id="8ba3a-108">Örneğin ilk bölümü kullanır <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="8ba3a-109">Bu, bir iş akışını yürütmek için en temel yoldur.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="8ba3a-110">İle <xref:System.Activities.WorkflowInvoker.Invoke%2A> yürütülen iş akışları zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="8ba3a-111">Örneğin ikinci bölümü <xref:System.Activities.WorkflowApplication> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="8ba3a-112"><xref:System.Activities.WorkflowApplication>çalışan iş akışıyla etkileşim kurma ve iş akışını zaman uyumsuz olarak çalıştırma özelliği de dahil olmak üzere her bir örnek üzerinde daha fazla denetime sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ba3a-113">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8ba3a-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8ba3a-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8ba3a-116">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="8ba3a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ba3a-117">See also</span></span>

- [<span data-ttu-id="8ba3a-118">WorkflowInvoker ve WorkflowApplication Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ba3a-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
