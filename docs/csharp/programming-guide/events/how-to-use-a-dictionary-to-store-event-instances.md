---
title: 'Nasıl yapılır: Store olay örnekleri için-Sözlük kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f3b8e313bd0b1bd3973102caebb9bbc9da620ae6
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203038"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="dc00b-102">Nasıl yapılır: Store olay örnekleri için Sözlük kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="dc00b-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="dc00b-103">Bir kullanımı `accessor-declarations` her olay için bir alan ayırma, ancak bunun yerine olay örneklerini depolamak için bir sözlük kullanarak çok sayıda olay kullanıma sunulmasıdır.</span><span class="sxs-lookup"><span data-stu-id="dc00b-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="dc00b-104">Bu yalnızca çok sayıda olay olması, ancak çoğu olayların uygulanmadı beklediğiniz yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc00b-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc00b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc00b-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="dc00b-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc00b-106">See also</span></span>

- [<span data-ttu-id="dc00b-107">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dc00b-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="dc00b-108">Olaylar</span><span class="sxs-lookup"><span data-stu-id="dc00b-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="dc00b-109">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="dc00b-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
