---
title: 'Nasıl yapılır: temsilcileri birleştirme (çok noktaya yayın temsilcileri C# )-Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d7098bb5518b92b407f905ddabbfafdcb77536bf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423344"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="91fc4-102">Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="91fc4-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="91fc4-103">Bu örnek, çok noktaya yayın temsilcileri oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="91fc4-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="91fc4-104">[Temsilci](../../language-reference/builtin-types/reference-types.md) nesnelerinin yararlı bir özelliği, `+` işleci kullanılarak bir temsilci örneğine birden çok nesne atanabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="91fc4-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="91fc4-105">Çok noktaya yayın temsilcisi, atanan temsilcilerin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="91fc4-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="91fc4-106">Çok noktaya yayın temsilcisi çağrıldığında, listedeki temsilcileri sırayla çağırır.</span><span class="sxs-lookup"><span data-stu-id="91fc4-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="91fc4-107">Yalnızca aynı türde temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="91fc4-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="91fc4-108">`-` işleci bir çok noktaya yayın temsilcisinden bir bileşen temsilcisini kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91fc4-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91fc4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="91fc4-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="91fc4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91fc4-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="91fc4-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="91fc4-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="91fc4-112">Olaylar</span><span class="sxs-lookup"><span data-stu-id="91fc4-112">Events</span></span>](../events/index.md)
