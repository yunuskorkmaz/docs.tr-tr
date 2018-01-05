---
title: "Nasıl yapılır: bir iş akışı oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e619fa7fa6437b60b1d3cd6b50a2a68229899f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="3bddf-102">Nasıl yapılır: bir iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="3bddf-102">How to: Create a Workflow</span></span>
<span data-ttu-id="3bddf-103">İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="3bddf-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="3bddf-104">Bu konular hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma aracılığıyla bu bölümde adımda <xref:System.Activities.Statements.Flowchart> etkinliği ve önceki özel etkinlikler [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) konu.</span><span class="sxs-lookup"><span data-stu-id="3bddf-104">This topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="3bddf-105">Sayı tahmin eden oyun iş akışını modeller.</span><span class="sxs-lookup"><span data-stu-id="3bddf-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="3bddf-106">Bu bölümdeki konular, yalnızca biri, öğreticiyi tamamlamak için gereklidir; ilginizi çeken stil seçin ve bu adımı izleyin.</span><span class="sxs-lookup"><span data-stu-id="3bddf-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="3bddf-107">Ancak, isterseniz tüm konuları tamamlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3bddf-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bddf-108">Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3bddf-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="3bddf-109">Bu konuda tamamlamak için önce tamamlamanız gereken [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="3bddf-109">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bddf-110">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="3bddf-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bddf-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3bddf-111">In This Section</span></span>  
 [<span data-ttu-id="3bddf-112">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3bddf-112">How to: Create a Sequential Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="3bddf-113">Kullanarak bir sıralı iş akışı oluşturmayı açıklar <xref:System.Activities.Statements.Sequence> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="3bddf-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="3bddf-114">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3bddf-114">How to: Create a Flowchart Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="3bddf-115">Kullanarak bir akış iş akışı oluşturmayı açıklar <xref:System.Activities.Statements.Flowchart> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="3bddf-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="3bddf-116">Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3bddf-116">How to: Create a State Machine Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="3bddf-117">Durumu kullanarak bir makine iş akışı oluşturmayı açıklar <xref:System.Activities.Statements.StateMachine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="3bddf-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bddf-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3bddf-118">See Also</span></span>  
 [<span data-ttu-id="3bddf-119">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="3bddf-119">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
