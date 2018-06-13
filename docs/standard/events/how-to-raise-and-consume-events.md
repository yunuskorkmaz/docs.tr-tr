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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efeed61c5748a0a6ac731cdcfce1a110982b2941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572729"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="cb32e-102">Nasıl yapılır: Olaylar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="cb32e-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="cb32e-103">Bu konudaki örnekler olayları ile çalışmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb32e-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="cb32e-104">Örnek olarak verilebilir <xref:System.EventHandler> temsilci, <xref:System.EventHandler%601> temsilci ve olayları ile ve veri olmadan göstermek için özel bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="cb32e-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="cb32e-105">Açıklanan kavramları örneklerde [olayları](../../../docs/standard/events/index.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="cb32e-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb32e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb32e-106">Example</span></span>  
 <span data-ttu-id="cb32e-107">İlk örnek, yükseltmek ve veri sahip olmayan bir olay kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb32e-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="cb32e-108">Adlı bir sınıf içeriyor `Counter` adlı bir olay olan `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="cb32e-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="cb32e-109">Bir sayaç değeri değerine eşit veya eşik değeri bu olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="cb32e-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="cb32e-110"><xref:System.EventHandler> Temsilci olduğundan olayla ilişkili olay verisi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cb32e-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="cb32e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb32e-111">Example</span></span>  
 <span data-ttu-id="cb32e-112">Sonraki örnekte, yükseltmek ve veri sağlayan bir olay kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb32e-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="cb32e-113"><xref:System.EventHandler%601> Temsilcisidir olayla ilişkili ve özel bir olay veri nesnesi örneği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cb32e-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="cb32e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb32e-114">Example</span></span>  
 <span data-ttu-id="cb32e-115">Sonraki örnek, bir olay için bir temsilci bildirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb32e-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="cb32e-116">Temsilci adlı `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="cb32e-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="cb32e-117">Bu yalnızca bir çizimidir.</span><span class="sxs-lookup"><span data-stu-id="cb32e-117">This is just an illustration.</span></span> <span data-ttu-id="cb32e-118">Ya da kullanabileceğinizden genellikle, bir olay için bir temsilci bildirmek elinizde <xref:System.EventHandler> veya <xref:System.EventHandler%601> temsilci.</span><span class="sxs-lookup"><span data-stu-id="cb32e-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="cb32e-119">Yalnızca sınıfınız genel türler kullanamazsınız eski kod için kullanılabilir hale getirme gibi nadir senaryolarda bir temsilci bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb32e-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="cb32e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb32e-120">See Also</span></span>  
 [<span data-ttu-id="cb32e-121">Olaylar</span><span class="sxs-lookup"><span data-stu-id="cb32e-121">Events</span></span>](../../../docs/standard/events/index.md)
