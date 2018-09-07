---
title: 'Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e3cc3f9082bd86004a7821b64c01253408c07641
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083283"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="b3215-102">Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b3215-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="b3215-103">Bu örnek, çok noktaya yayın temsilcileri oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3215-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="b3215-104">Kullanışlı bir özelliği [temsilci](../../../csharp/language-reference/keywords/delegate.md) nesneleri, kullanarak birden çok nesne için bir temsilci örneği atanabilir `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="b3215-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="b3215-105">Çok noktaya yayın temsilci atanmış temsilcileri listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b3215-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="b3215-106">Çok noktaya yayın temsilci çağrıldığında listesinde sırada, temsilciler çağırır.</span><span class="sxs-lookup"><span data-stu-id="b3215-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="b3215-107">Yalnızca aynı türdeki temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b3215-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="b3215-108">`-` İşleci, bir bileşen temsilci bir çok noktaya yayın temsilciyi kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3215-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3215-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3215-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b3215-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3215-110">See Also</span></span>

- <xref:System.MulticastDelegate>  
- [<span data-ttu-id="b3215-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b3215-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b3215-112">Olaylar</span><span class="sxs-lookup"><span data-stu-id="b3215-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
