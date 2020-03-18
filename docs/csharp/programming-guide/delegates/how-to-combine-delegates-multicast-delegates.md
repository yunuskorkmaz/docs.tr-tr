---
title: Nasıl temsilcileri (Multicast Delegates) birleştirmek için - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705385"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="b1669-102">Temsilcileri birleştirme (Çok Noktaya Yayın Temsilcileri) (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b1669-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="b1669-103">Bu örnek, çok noktaya yayın temsilcilerinin nasıl oluşturulurunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1669-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="b1669-104">[Temsilci](../../language-reference/builtin-types/reference-types.md) nesnelerin kullanışlı bir özelliği, `+` işleç kullanılarak bir temsilci örneğine birden çok nesne atanabilir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b1669-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="b1669-105">Çok noktaya yayın temsilcisi, atanan temsilcilerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b1669-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="b1669-106">Çok noktaya yayın temsilcisi çağrıldığında, listedeki delegeleri sırayla çağırır.</span><span class="sxs-lookup"><span data-stu-id="b1669-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="b1669-107">Yalnızca aynı türden temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b1669-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="b1669-108">İşleç, `-` bir bileşen temsilcisini çok noktaya yayın temsilcisinden kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1669-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1669-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1669-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="b1669-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1669-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="b1669-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b1669-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b1669-112">Olaylar</span><span class="sxs-lookup"><span data-stu-id="b1669-112">Events</span></span>](../events/index.md)
