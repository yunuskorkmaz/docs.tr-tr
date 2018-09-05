---
title: 'Nasıl yapılır: Olay Örneklerini Depolamak için Sözlük Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: c3a804ce1bf1f5ac8db47f0f0c1f37d1ca5f781b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43673742"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="771da-102">Nasıl yapılır: Olay Örneklerini Depolamak için Sözlük Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="771da-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="771da-103">Bir kullanımı `accessor-declarations` her olay için bir alan ayırma, ancak bunun yerine olay örneklerini depolamak için bir sözlük kullanarak çok sayıda olay kullanıma sunulmasıdır.</span><span class="sxs-lookup"><span data-stu-id="771da-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="771da-104">Bu yalnızca çok sayıda olay olması, ancak çoğu olayların uygulanmadı beklediğiniz yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="771da-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="771da-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="771da-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="771da-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="771da-106">See Also</span></span>

- [<span data-ttu-id="771da-107">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="771da-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="771da-108">Olaylar</span><span class="sxs-lookup"><span data-stu-id="771da-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="771da-109">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="771da-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
