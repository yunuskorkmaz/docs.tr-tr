---
title: 'Nasıl yapılır: İş Akışı Oluşturma'
description: Bu Iş akışı altyapısı öğreticisinin bir parçası olarak iş akışı oluşturmak için bu bölümdeki üç seçenekten birini doldurun.
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: 1b2b03d672f86a351bcf36343d6a17e351d40ed0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248792"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="8f31a-103">Nasıl yapılır: İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f31a-103">How to: Create a Workflow</span></span>

<span data-ttu-id="8f31a-104">İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="8f31a-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="8f31a-105">Bu bölümdeki konular, etkinlik gibi yerleşik etkinlikleri <xref:System.Activities.Statements.Flowchart> ve önceki [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md) konusunun özel etkinliklerini kullanan bir iş akışı oluşturma yoluyla adım adım anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f31a-105">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="8f31a-106">İş akışı, sayıyı tahmin eden bir oyunu modelleyen.</span><span class="sxs-lookup"><span data-stu-id="8f31a-106">The workflow models a number guessing game.</span></span> <span data-ttu-id="8f31a-107">Öğreticiyi tamamlayabilmeniz için bu bölümdeki konulardan yalnızca biri gereklidir; İlgilendiğiniz stili seçmeniz ve bu adımı izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f31a-107">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="8f31a-108">Ancak, isterseniz tüm konuları tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f31a-108">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f31a-109">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8f31a-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="8f31a-110">Bu konuyu tamamlayabilmeniz için öncelikle [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md)' yı tamamlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="8f31a-110">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f31a-111">Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="8f31a-111">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f31a-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8f31a-112">In This Section</span></span>  

 [<span data-ttu-id="8f31a-113">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f31a-113">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="8f31a-114">Etkinliğini kullanarak sıralı bir iş akışının nasıl oluşturulacağını açıklar <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="8f31a-114">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="8f31a-115">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f31a-115">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="8f31a-116">Etkinliğini kullanarak bir akış çizelgesi iş akışının nasıl oluşturulacağını açıklar <xref:System.Activities.Statements.Flowchart> .</span><span class="sxs-lookup"><span data-stu-id="8f31a-116">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="8f31a-117">Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f31a-117">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="8f31a-118">Etkinliğini kullanarak bir durum makinesi iş akışının nasıl oluşturulacağını açıklar <xref:System.Activities.Statements.StateMachine> .</span><span class="sxs-lookup"><span data-stu-id="8f31a-118">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f31a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f31a-119">See also</span></span>

- [<span data-ttu-id="8f31a-120">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="8f31a-120">Windows Workflow Foundation Programming</span></span>](programming.md)
