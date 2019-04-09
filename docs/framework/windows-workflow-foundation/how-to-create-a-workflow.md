---
title: 'Nasıl yapılır: İş Akışı Oluşturma'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: 4b24e57cce4d42645fc1750ac932e5f24cf24913
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134803"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="bdea0-102">Nasıl yapılır: İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdea0-102">How to: Create a Workflow</span></span>
<span data-ttu-id="bdea0-103">İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="bdea0-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="bdea0-104">Bu bölümdeki konular, her iki yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma işlemi adım adım <xref:System.Activities.Statements.Flowchart> etkinliği ve özel etkinlikler önceki [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) konu.</span><span class="sxs-lookup"><span data-stu-id="bdea0-104">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="bdea0-105">İş akışı sayısını tahmin eden oyun modelleri.</span><span class="sxs-lookup"><span data-stu-id="bdea0-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="bdea0-106">Bu öğreticiyi tamamlamak için bu bölümdeki konular, yalnızca biri gereklidir; ilginizi çeken bir stil seçin ve bu adımı izleyin.</span><span class="sxs-lookup"><span data-stu-id="bdea0-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="bdea0-107">Ancak, isterseniz tüm konu başlıklarınde tamamlanabilir.</span><span class="sxs-lookup"><span data-stu-id="bdea0-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdea0-108">Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bdea0-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="bdea0-109">Bu konuyu tamamlamak için önce tamamlamanız gereken [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="bdea0-109">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdea0-110">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="bdea0-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdea0-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bdea0-111">In This Section</span></span>  
 [<span data-ttu-id="bdea0-112">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdea0-112">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="bdea0-113">Kullanarak bir sıralı iş akışı oluşturmayı açıklar <xref:System.Activities.Statements.Sequence> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="bdea0-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="bdea0-114">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdea0-114">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="bdea0-115">Kullanarak bir akış çizelgesi iş akışı oluşturmayı açıklar <xref:System.Activities.Statements.Flowchart> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="bdea0-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="bdea0-116">Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdea0-116">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="bdea0-117">Bir Durum makinesi iş akışı kullanarak oluşturmayı açıklar <xref:System.Activities.Statements.StateMachine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="bdea0-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdea0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdea0-118">See also</span></span>

- [<span data-ttu-id="bdea0-119">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="bdea0-119">Windows Workflow Foundation Programming</span></span>](programming.md)
