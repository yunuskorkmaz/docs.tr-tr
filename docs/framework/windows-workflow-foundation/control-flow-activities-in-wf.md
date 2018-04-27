---
title: WF akış etkinliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 91fb4e18d753709ab973730300ffef5a952c56d6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="control-flow-activities-in-wf"></a><span data-ttu-id="b1b24-102">WF akış etkinliği</span><span class="sxs-lookup"><span data-stu-id="b1b24-102">Control Flow Activities in WF</span></span>
<span data-ttu-id="b1b24-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Bir iş akışındaki akışını denetlemek için çeşitli etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1b24-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] provides several activities for controlling flow of execution within a workflow.</span></span> <span data-ttu-id="b1b24-104">Bu etkinliklerin bazıları (gibi `Switch` ve `If`) akış denetim yapıları benzer ortamları gibi Visual C#, diğerlerinin programlama uygulamak (gibi `Pick`) modeli yeni programlama yapıları.</span><span class="sxs-lookup"><span data-stu-id="b1b24-104">Some of these activities (such as `Switch` and `If`) implement flow control structures similar to those in programming environments such as Visual C#, while others (such as `Pick`) model new programming structures.</span></span>  
  
 <span data-ttu-id="b1b24-105">Etkinlikleri sırasında gibi unutmayın `Parallel` ve `ParallelForEach` etkinlikleri zamanlama yürütme için birden çok alt etkinlikler aynı anda, yalnızca tek bir iş parçacığı için iş akışı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1b24-105">Note that while activities such as the `Parallel` and `ParallelForEach` activities schedule multiple child activities for execution simultaneously, only a single thread is used for a workflow.</span></span> <span data-ttu-id="b1b24-106">Bu etkinliklerin her alt etkinlik sıralı olarak yürütür ve önceki etkinliklerini tamamlamak veya boşta Git kadar ardışık etkinlikleri yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b1b24-106">Each child activity of these activities executes sequentially and successive activities do not execute until previous activities either complete or go idle.</span></span> <span data-ttu-id="b1b24-107">Sonuç olarak, bu etkinlikler birkaç olası engelleme etkinlikleri bir araya eklemeli şekilde yürütülmelidir uygulamalar için en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b1b24-107">As a result, these activities are most useful for applications in which several potentially blocking activities must execute in an interleaved fashion.</span></span> <span data-ttu-id="b1b24-108">Bu etkinlikler alt etkinliklerini hiçbiri boşta kalırsa bir `Parallel` etkinlik yürütür tıpkı bir `Sequence` etkinliği ve bir `ParallelForEach` etkinlik yürütür tıpkı bir `ForEach` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b1b24-108">If none of the child activities of these activities go idle, a `Parallel` activity executes just like a `Sequence` activity, and a `ParallelForEach` activity executes just like a `ForEach` activity.</span></span> <span data-ttu-id="b1b24-109">Eğer, ancak, zaman uyumsuz etkinlikleri (öğesinden türetilen etkinlikleri gibi <xref:System.Activities.AsyncCodeActivity>) veya Mesajlaşma etkinlikleri kullanılır, Denetim alt etkinlik alınabilmesi kendi ileti beklerken sonraki şube veya tamamlanması için zaman uyumsuz çalışmasını geçecek.</span><span class="sxs-lookup"><span data-stu-id="b1b24-109">If, however, asynchronous activities (such as activities that derive from <xref:System.Activities.AsyncCodeActivity>) or messaging activities are used, control will pass to the next branch while the child activity waits for its message to be received or its asynchronous work to be completed.</span></span>  
  
## <a name="flow-control-activities"></a><span data-ttu-id="b1b24-110">Akış denetimi etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="b1b24-110">Flow control activities</span></span>  
  
|<span data-ttu-id="b1b24-111">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="b1b24-111">Activity</span></span>|<span data-ttu-id="b1b24-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1b24-112">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|<span data-ttu-id="b1b24-113">İçerilen etkinlikleri bir kez çalıştırır ve bir koşul olsa da bunu yapmak devam `true`.</span><span class="sxs-lookup"><span data-stu-id="b1b24-113">Executes the contained activities once and continues to do so while a condition is `true`.</span></span>|  
|<xref:System.Activities.Statements.ForEach%601>|<span data-ttu-id="b1b24-114">Bir koleksiyondaki her öğe için sıralı bir katıştırılmış deyimini yürütür.</span><span class="sxs-lookup"><span data-stu-id="b1b24-114">Executes an embedded statement in sequence for each element in a collection.</span></span> <span data-ttu-id="b1b24-115"><xref:System.Activities.Statements.ForEach%601> anahtar sözcüğüne benzer `foreach`, bir dil deyimi yerine bir etkinlik olarak uygulanan ancak.</span><span class="sxs-lookup"><span data-stu-id="b1b24-115"><xref:System.Activities.Statements.ForEach%601> is similar to the keyword `foreach`, but is implemented as an activity rather than a language statement.</span></span>|  
|<xref:System.Activities.Statements.If>|<span data-ttu-id="b1b24-116">Bir koşul ise, içerilen etkinlikleri yürütür `true`ve içerdiği etkinlikleri yürütebilir <xref:System.Activities.Statements.If.Else%2A> koşul ise özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="b1b24-116">Executes contained activities if a condition is `true`, and can execute activities contained in the <xref:System.Activities.Statements.If.Else%2A> property if the condition is `false`.</span></span>|  
|<xref:System.Activities.Statements.Parallel>|<span data-ttu-id="b1b24-117">İçerilen etkinlikleri paralel olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="b1b24-117">Executes contained activities in parallel.</span></span>|  
|<xref:System.Activities.Statements.ParallelForEach%601>|<span data-ttu-id="b1b24-118">Bir koleksiyondaki her öğe için paralel bir katıştırılmış deyimini yürütür.</span><span class="sxs-lookup"><span data-stu-id="b1b24-118">Executes an embedded statement in parallel for each element in a collection.</span></span>|  
|<xref:System.Activities.Statements.Pick>|<span data-ttu-id="b1b24-119">Olay tabanlı denetim akışı modelleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1b24-119">Provides event-based control flow modeling.</span></span>|  
|<xref:System.Activities.Statements.PickBranch>|<span data-ttu-id="b1b24-120">Yürütme olası bir yolu temsil eden bir <xref:System.Activities.Statements.Pick> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b1b24-120">Represents a potential path of execution in a <xref:System.Activities.Statements.Pick> activity.</span></span>|  
|<xref:System.Activities.Statements.Sequence>|<span data-ttu-id="b1b24-121">İçerilen etkinlikleri sırayla yürütür.</span><span class="sxs-lookup"><span data-stu-id="b1b24-121">Executes contained activities in sequence.</span></span>|  
|<xref:System.Activities.Statements.Switch%601>|<span data-ttu-id="b1b24-122">Bir seçenek değerine göre belirli bir deyim yürütmek için etkinlikler arasında bir sayı seçer.</span><span class="sxs-lookup"><span data-stu-id="b1b24-122">Selects one choice from a number of activities to execute, based on the value of a given expression.</span></span>|  
|<xref:System.Activities.Statements.While>|<span data-ttu-id="b1b24-123">Bir koşul ederken içerilen etkinlikleri yürütür `true`.</span><span class="sxs-lookup"><span data-stu-id="b1b24-123">Executes contained activities while a condition is `true`.</span></span>|
