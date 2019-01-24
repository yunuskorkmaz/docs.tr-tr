---
title: 'Nasıl yapılır: Store olay örnekleri için-Sözlük kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 8f0284c5637890f35642346880d035619bc0e1e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560067"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="e0c10-102">Nasıl yapılır: Store olay örnekleri için Sözlük kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e0c10-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="e0c10-103">Bir kullanımı `accessor-declarations` her olay için bir alan ayırma, ancak bunun yerine olay örneklerini depolamak için bir sözlük kullanarak çok sayıda olay kullanıma sunulmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e0c10-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="e0c10-104">Bu yalnızca çok sayıda olay olması, ancak çoğu olayların uygulanmadı beklediğiniz yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0c10-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0c10-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0c10-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e0c10-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0c10-106">See also</span></span>

- [<span data-ttu-id="e0c10-107">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e0c10-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e0c10-108">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e0c10-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="e0c10-109">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e0c10-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
