---
title: 'Nasıl yapılır: Olaylar Oluşturma ve Kullanma'
description: .NET ' te & tüketme olayları yükseltin. Özel bir temsilciyi & EventHandler temsilcisini kullanan örneklere bakın <TEventArgs> .
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET], raising
- raising events
- events [.NET], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 22e62dd8e14696273923873353b1bd19d8507ab7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697460"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="ed1c4-104">Nasıl yapılır: Olaylar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="ed1c4-104">How to: Raise and Consume Events</span></span>

<span data-ttu-id="ed1c4-105">Bu konudaki örneklerde, olaylarla nasıl çalışılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-105">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="ed1c4-106">Bu kişiler, <xref:System.EventHandler> <xref:System.EventHandler%601> verileri içeren ve olmayan olayları göstermek için temsilci, temsilci ve özel bir temsilci örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-106">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="ed1c4-107">Örnekler, [Olaylar](index.md) makalesinde açıklanan kavramları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-107">The examples use concepts described in the [Events](index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed1c4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed1c4-108">Example</span></span>  

 <span data-ttu-id="ed1c4-109">İlk örnek, verileri olmayan bir olayın nasıl oluşturulduğunu ve kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-109">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="ed1c4-110">Adında bir olayı olan adlı bir sınıfı içerir `Counter` `ThresholdReached` .</span><span class="sxs-lookup"><span data-stu-id="ed1c4-110">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="ed1c4-111">Bu olay, bir sayaç değeri bir eşik değerini eşitse veya aştığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-111">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="ed1c4-112"><xref:System.EventHandler>Olay verileri sağlanmadığından temsilci olayla ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-112">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ed1c4-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed1c4-113">Example</span></span>  

 <span data-ttu-id="ed1c4-114">Sonraki örnekte, veri sağlayan bir olayın nasıl oluşturulduğu ve kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-114">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="ed1c4-115"><xref:System.EventHandler%601>Temsilci olayla ilişkilendirilir ve bir özel olay veri nesnesi örneği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-115">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="ed1c4-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed1c4-116">Example</span></span>  

 <span data-ttu-id="ed1c4-117">Sonraki örnekte bir olay için nasıl temsilci bildirireceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-117">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="ed1c4-118">Temsilcinin adı `ThresholdReachedEventHandler` .</span><span class="sxs-lookup"><span data-stu-id="ed1c4-118">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="ed1c4-119">Bu yalnızca bir çizim.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-119">This is just an illustration.</span></span> <span data-ttu-id="ed1c4-120">Genellikle, ya da temsilcisini kullanabilmeniz için bir olay için temsilci bildirmeniz gerekmez <xref:System.EventHandler> <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="ed1c4-120">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="ed1c4-121">Bir temsilciyi yalnızca nadir senaryolar halinde bildirmeniz gerekir. Örneğin, sınıfınızın genel türler kullanamaz eski kod için kullanılabilir hale getirilmesi.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-121">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="ed1c4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed1c4-122">See also</span></span>

- [<span data-ttu-id="ed1c4-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ed1c4-123">Events</span></span>](index.md)
