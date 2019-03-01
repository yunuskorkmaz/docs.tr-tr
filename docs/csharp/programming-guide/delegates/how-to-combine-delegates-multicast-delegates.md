---
title: 'Nasıl yapılır: Temsilcileri (çok noktaya yayın temsilcileri) birleştirme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 426b9f91d3e3328522ec5c7ab043d5074ececc43
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970122"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="a76e3-102">Nasıl yapılır: (Çok noktaya yayın temsilcileri) temsilcileri birleştirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a76e3-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="a76e3-103">Bu örnek, çok noktaya yayın temsilcileri oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a76e3-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="a76e3-104">Kullanışlı bir özelliği [temsilci](../../../csharp/language-reference/keywords/delegate.md) nesneleri, kullanarak birden çok nesne için bir temsilci örneği atanabilir `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="a76e3-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="a76e3-105">Çok noktaya yayın temsilci atanmış temsilcileri listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="a76e3-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="a76e3-106">Çok noktaya yayın temsilci çağrıldığında listesinde sırada, temsilciler çağırır.</span><span class="sxs-lookup"><span data-stu-id="a76e3-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="a76e3-107">Yalnızca aynı türdeki temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a76e3-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="a76e3-108">`-` İşleci, bir bileşen temsilci bir çok noktaya yayın temsilciyi kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a76e3-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a76e3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a76e3-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="a76e3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a76e3-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="a76e3-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a76e3-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a76e3-112">Olaylar</span><span class="sxs-lookup"><span data-stu-id="a76e3-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
