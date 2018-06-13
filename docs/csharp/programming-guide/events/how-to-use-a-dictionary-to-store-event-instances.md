---
title: 'Nasıl yapılır: Olay Örneklerini Depolamak için Sözlük Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 97a7b0f168e4a1c81ec396f42b731dabb45b3516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327222"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="55c4c-102">Nasıl yapılır: Olay Örneklerini Depolamak için Sözlük Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="55c4c-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="55c4c-103">Bir kullanım için `accessor-declarations` her olay için alan ayırma, ancak bunun yerine olay örneklerini depolamak için Sözlük kullanma olmadan birçok olaylar oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="55c4c-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="55c4c-104">Bu yalnızca çok sayıda olay varsa, ancak çoğu olayların uygulanmadı beklediğiniz yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="55c4c-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55c4c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="55c4c-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="55c4c-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55c4c-106">See Also</span></span>  
 [<span data-ttu-id="55c4c-107">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="55c4c-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="55c4c-108">Olaylar</span><span class="sxs-lookup"><span data-stu-id="55c4c-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="55c4c-109">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="55c4c-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
