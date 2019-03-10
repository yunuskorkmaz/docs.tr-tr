---
title: 'Nasıl yapılır: Bir iş akışı oluşturma'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: aaaac74d26421f96a3170b3e5a788145f8ea09fc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704953"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="5694c-102">Nasıl yapılır: Bir iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5694c-102">How to: Create a Workflow</span></span>
<span data-ttu-id="5694c-103">İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5694c-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="5694c-104">Bu bölümdeki konular, her iki yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma işlemi adım adım <xref:System.Activities.Statements.Flowchart> etkinliği ve özel etkinlikler önceki [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) konu.</span><span class="sxs-lookup"><span data-stu-id="5694c-104">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="5694c-105">İş akışı sayısını tahmin eden oyun modelleri.</span><span class="sxs-lookup"><span data-stu-id="5694c-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="5694c-106">Bu öğreticiyi tamamlamak için bu bölümdeki konular, yalnızca biri gereklidir; ilginizi çeken bir stil seçin ve bu adımı izleyin.</span><span class="sxs-lookup"><span data-stu-id="5694c-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="5694c-107">Ancak, isterseniz tüm konu başlıklarınde tamamlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5694c-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5694c-108">Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5694c-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="5694c-109">Bu konuyu tamamlamak için önce tamamlamanız gereken [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="5694c-109">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5694c-110">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="5694c-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5694c-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5694c-111">In This Section</span></span>  
 [<span data-ttu-id="5694c-112">Nasıl yapılır: Sıralı iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5694c-112">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="5694c-113">Kullanarak bir sıralı iş akışı oluşturmayı açıklar <xref:System.Activities.Statements.Sequence> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5694c-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="5694c-114">Nasıl yapılır: Akış Çizelgesi iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5694c-114">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="5694c-115">Kullanarak bir akış çizelgesi iş akışı oluşturmayı açıklar <xref:System.Activities.Statements.Flowchart> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5694c-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="5694c-116">Nasıl yapılır: Bir Durum makinesi iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5694c-116">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="5694c-117">Bir Durum makinesi iş akışı kullanarak oluşturmayı açıklar <xref:System.Activities.Statements.StateMachine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5694c-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5694c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5694c-118">See also</span></span>
- [<span data-ttu-id="5694c-119">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="5694c-119">Windows Workflow Foundation Programming</span></span>](programming.md)
