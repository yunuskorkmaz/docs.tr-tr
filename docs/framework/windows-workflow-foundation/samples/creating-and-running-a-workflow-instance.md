---
description: 'Hakkında daha fazla bilgi edinin: Iş akışı örneği oluşturma ve çalıştırma'
title: İş Akışı Örneği Oluşturma ve Çalıştırma
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 2efd4a0017f450c21954e363af33be69c659624e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787857"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="77bac-103">İş Akışı Örneği Oluşturma ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="77bac-103">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="77bac-104">Bu örnek, bir iş akışı örneğinin nasıl çalıştırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="77bac-104">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="77bac-105">Bu, zaman uyumlu ve zaman uyumsuz olarak nasıl yürütüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77bac-105">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="77bac-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="77bac-106">Demonstrates</span></span>

<span data-ttu-id="77bac-107"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="77bac-107"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="77bac-108">Tartışma</span><span class="sxs-lookup"><span data-stu-id="77bac-108">Discussion</span></span>

<span data-ttu-id="77bac-109">Örneğin ilk bölümü kullanır <xref:System.Activities.WorkflowInvoker.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="77bac-109">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="77bac-110">Bu, bir iş akışını yürütmek için en temel yoldur.</span><span class="sxs-lookup"><span data-stu-id="77bac-110">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="77bac-111">İle yürütülen iş akışları <xref:System.Activities.WorkflowInvoker.Invoke%2A> zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="77bac-111">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="77bac-112">Örneğin ikinci bölümü <xref:System.Activities.WorkflowApplication> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="77bac-112">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="77bac-113"><xref:System.Activities.WorkflowApplication> çalışan iş akışıyla etkileşim kurma ve iş akışını zaman uyumsuz olarak çalıştırma özelliği de dahil olmak üzere her bir örnek üzerinde daha fazla denetime sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="77bac-113"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="77bac-114">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="77bac-114">The samples may already be installed on your machine.</span></span> <span data-ttu-id="77bac-115">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="77bac-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="77bac-116">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="77bac-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="77bac-117">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="77bac-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="77bac-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77bac-118">See also</span></span>

- [<span data-ttu-id="77bac-119">WorkflowInvoker ve WorkflowApplication Kullanma</span><span class="sxs-lookup"><span data-stu-id="77bac-119">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
