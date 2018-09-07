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
ms.openlocfilehash: aa933e0fc589d0dbfec741e9db7fb11222cfdf38
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44065004"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="fd6d5-102">Nasıl yapılır: Olaylar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="fd6d5-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="fd6d5-103">Bu konudaki örnekler, olaylarla nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="fd6d5-104">Örneklerini içerirler <xref:System.EventHandler> temsilcisi, <xref:System.EventHandler%601> temsilci ve olayları verilerle ve Verisiz göstermek için özel bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="fd6d5-105">Örnekler açıklanan kavramları kullanmaktadır [olayları](../../../docs/standard/events/index.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd6d5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd6d5-106">Example</span></span>  
 <span data-ttu-id="fd6d5-107">İlk örnek veri içermeyen bir olay yükseltilip tüketileceğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="fd6d5-108">Adlı bir sınıf içeren `Counter` adlı bir olaya sahip `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="fd6d5-109">Sayaç değeri bir eşik değeri değerine eşit veya bu olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="fd6d5-110"><xref:System.EventHandler> Olay verisi sağlanmadığından temsilcisi olayla ilişkili.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="fd6d5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd6d5-111">Example</span></span>  
 <span data-ttu-id="fd6d5-112">Sonraki örnek veri sağlayan bir olay yükseltilip tüketileceğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="fd6d5-113"><xref:System.EventHandler%601> Temsilcisi olayla ilişkili ve özel olay veri nesnesinin bir örneği sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="fd6d5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd6d5-114">Example</span></span>  
 <span data-ttu-id="fd6d5-115">Sonraki örnek, bir olay için bir temsilcinin nasıl belirtileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="fd6d5-116">Temsilci adlandırılmış `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="fd6d5-117">Bu sadece bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-117">This is just an illustration.</span></span> <span data-ttu-id="fd6d5-118">Ya da kullanabileceğinizden genellikle, bir olayın bir temsilci bildirmeniz erişiminiz yok <xref:System.EventHandler> veya <xref:System.EventHandler%601> temsilci.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="fd6d5-119">Yalnızca kendi sınıfınızı genel türler kullanamayan eski kod için kullanılabilir hale getirme gibi nadir senaryolarda bir temsilci bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="fd6d5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd6d5-120">See also</span></span>

- [<span data-ttu-id="fd6d5-121">Olaylar</span><span class="sxs-lookup"><span data-stu-id="fd6d5-121">Events</span></span>](../../../docs/standard/events/index.md)
