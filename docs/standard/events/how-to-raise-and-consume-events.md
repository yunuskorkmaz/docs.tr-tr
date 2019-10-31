---
title: 'Nasıl yapılır: Olaylar Oluşturma ve Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 256b5ae9ac2145e339136985872dfa5423aca730
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131591"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="7eb34-102">Nasıl yapılır: Olaylar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="7eb34-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="7eb34-103">Bu konudaki örneklerde, olaylarla nasıl çalışılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7eb34-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="7eb34-104">Bunlar, verileri içeren ve olmayan olayları göstermek için <xref:System.EventHandler> temsilci, <xref:System.EventHandler%601> temsilcisi ve özel bir temsilci örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7eb34-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="7eb34-105">Örnekler, [Olaylar](../../../docs/standard/events/index.md) makalesinde açıklanan kavramları kullanır.</span><span class="sxs-lookup"><span data-stu-id="7eb34-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7eb34-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7eb34-106">Example</span></span>  
 <span data-ttu-id="7eb34-107">İlk örnek, verileri olmayan bir olayın nasıl oluşturulduğunu ve kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7eb34-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="7eb34-108">`ThresholdReached`adlı bir olaya sahip `Counter` adlı bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="7eb34-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="7eb34-109">Bu olay, bir sayaç değeri bir eşik değerini eşitse veya aştığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="7eb34-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="7eb34-110">Olay verileri sağlanmadığından <xref:System.EventHandler> temsilcisi olayla ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="7eb34-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="7eb34-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7eb34-111">Example</span></span>  
 <span data-ttu-id="7eb34-112">Sonraki örnekte, veri sağlayan bir olayın nasıl oluşturulduğu ve kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7eb34-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="7eb34-113"><xref:System.EventHandler%601> temsilci olayla ilişkilendirilir ve bir özel olay veri nesnesi örneği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7eb34-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="7eb34-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="7eb34-114">Example</span></span>  
 <span data-ttu-id="7eb34-115">Sonraki örnekte bir olay için nasıl temsilci bildirireceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7eb34-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="7eb34-116">Temsilci `ThresholdReachedEventHandler`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7eb34-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="7eb34-117">Bu yalnızca bir çizim.</span><span class="sxs-lookup"><span data-stu-id="7eb34-117">This is just an illustration.</span></span> <span data-ttu-id="7eb34-118">Genellikle, bir olay için temsilci bildirmeniz gerekmez, çünkü <xref:System.EventHandler> ya da <xref:System.EventHandler%601> temsilcisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eb34-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="7eb34-119">Bir temsilciyi yalnızca nadir senaryolar halinde bildirmeniz gerekir. Örneğin, sınıfınızın genel türler kullanamaz eski kod için kullanılabilir hale getirilmesi.</span><span class="sxs-lookup"><span data-stu-id="7eb34-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="7eb34-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7eb34-120">See also</span></span>

- [<span data-ttu-id="7eb34-121">Olaylar</span><span class="sxs-lookup"><span data-stu-id="7eb34-121">Events</span></span>](../../../docs/standard/events/index.md)
