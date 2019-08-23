---
title: 'Nasıl yapılır: İş Akışı Oluşturma'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: 7f0bef673ff14ded13306a1fc26e09695601799d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962305"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="62ec4-102">Nasıl yapılır: İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62ec4-102">How to: Create a Workflow</span></span>
<span data-ttu-id="62ec4-103">İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="62ec4-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="62ec4-104">Bu bölümdeki konular, <xref:System.Activities.Statements.Flowchart> etkinlik gibi yerleşik etkinlikleri ve önceki [nasıl yapılacağı özel etkinlikleri kullanan bir iş akışı oluşturma yoluyla adım adım ele alınır. Etkinlik](how-to-create-an-activity.md) konusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="62ec4-104">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="62ec4-105">İş akışı, sayıyı tahmin eden bir oyunu modelleyen.</span><span class="sxs-lookup"><span data-stu-id="62ec4-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="62ec4-106">Öğreticiyi tamamlayabilmeniz için bu bölümdeki konulardan yalnızca biri gereklidir; İlgilendiğiniz stili seçmeniz ve bu adımı izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="62ec4-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="62ec4-107">Ancak, isterseniz tüm konuları tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62ec4-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62ec4-108">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="62ec4-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="62ec4-109">Bu konuyu tamamlayabilmeniz için öncelikle [şunları yapmanız gerekir: Etkinlik](how-to-create-an-activity.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="62ec4-109">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62ec4-110">Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="62ec4-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62ec4-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="62ec4-111">In This Section</span></span>  
 [<span data-ttu-id="62ec4-112">Nasıl yapılır: Sıralı Iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="62ec4-112">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="62ec4-113"><xref:System.Activities.Statements.Sequence> Etkinliğini kullanarak sıralı bir iş akışının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="62ec4-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="62ec4-114">Nasıl yapılır: Akış çizelgesi Iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="62ec4-114">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="62ec4-115"><xref:System.Activities.Statements.Flowchart> Etkinliğini kullanarak bir akış çizelgesi iş akışının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="62ec4-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="62ec4-116">Nasıl yapılır: Durum makinesi Iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="62ec4-116">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="62ec4-117"><xref:System.Activities.Statements.StateMachine> Etkinliğini kullanarak bir durum makinesi iş akışının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="62ec4-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ec4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62ec4-118">See also</span></span>

- [<span data-ttu-id="62ec4-119">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="62ec4-119">Windows Workflow Foundation Programming</span></span>](programming.md)
