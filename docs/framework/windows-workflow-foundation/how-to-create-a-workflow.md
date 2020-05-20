---
title: 'Nasıl yapılır: İş Akışı Oluşturma'
description: Bu Iş akışı altyapısı öğreticisinin bir parçası olarak iş akışı oluşturmak için bu bölümdeki üç seçenekten birini doldurun.
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: 7e4575436405e74b7575e55bea37a1a99d879a3e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419570"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="3c817-103">Nasıl yapılır: İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c817-103">How to: Create a Workflow</span></span>
<span data-ttu-id="3c817-104">İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="3c817-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="3c817-105">Bu bölümdeki konular, etkinlik gibi yerleşik etkinlikleri <xref:System.Activities.Statements.Flowchart> ve önceki [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md) konusunun özel etkinliklerini kullanan bir iş akışı oluşturma yoluyla adım adım anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c817-105">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="3c817-106">İş akışı, sayıyı tahmin eden bir oyunu modelleyen.</span><span class="sxs-lookup"><span data-stu-id="3c817-106">The workflow models a number guessing game.</span></span> <span data-ttu-id="3c817-107">Öğreticiyi tamamlayabilmeniz için bu bölümdeki konulardan yalnızca biri gereklidir; İlgilendiğiniz stili seçmeniz ve bu adımı izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c817-107">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="3c817-108">Ancak, isterseniz tüm konuları tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c817-108">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c817-109">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3c817-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="3c817-110">Bu konuyu tamamlayabilmeniz için öncelikle [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md)' yı tamamlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="3c817-110">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c817-111">Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="3c817-111">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c817-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3c817-112">In This Section</span></span>  
 [<span data-ttu-id="3c817-113">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c817-113">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="3c817-114">Etkinliğini kullanarak sıralı bir iş akışının nasıl oluşturulacağını açıklar <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="3c817-114">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="3c817-115">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c817-115">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="3c817-116">Etkinliğini kullanarak bir akış çizelgesi iş akışının nasıl oluşturulacağını açıklar <xref:System.Activities.Statements.Flowchart> .</span><span class="sxs-lookup"><span data-stu-id="3c817-116">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="3c817-117">Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c817-117">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="3c817-118">Etkinliğini kullanarak bir durum makinesi iş akışının nasıl oluşturulacağını açıklar <xref:System.Activities.Statements.StateMachine> .</span><span class="sxs-lookup"><span data-stu-id="3c817-118">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c817-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c817-119">See also</span></span>

- [<span data-ttu-id="3c817-120">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="3c817-120">Windows Workflow Foundation Programming</span></span>](programming.md)
