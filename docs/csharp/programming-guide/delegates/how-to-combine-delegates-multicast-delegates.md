---
title: Temsilcileri birleştirme (çok noktaya yayın temsilcileri)- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705385"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="03c35-102">Temsilcileri birleştirme (Çok Noktaya Yayın Temsilcileri) (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="03c35-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="03c35-103">Bu örnek, çok noktaya yayın temsilcileri oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="03c35-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="03c35-104">[Temsilci](../../language-reference/builtin-types/reference-types.md) nesnelerinin yararlı bir özelliği, `+` işleci kullanılarak bir temsilci örneğine birden çok nesne atanabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="03c35-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="03c35-105">Çok noktaya yayın temsilcisi, atanan temsilcilerin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="03c35-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="03c35-106">Çok noktaya yayın temsilcisi çağrıldığında, listedeki temsilcileri sırayla çağırır.</span><span class="sxs-lookup"><span data-stu-id="03c35-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="03c35-107">Yalnızca aynı türde temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="03c35-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="03c35-108">`-` işleci bir çok noktaya yayın temsilcisinden bir bileşen temsilcisini kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03c35-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03c35-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="03c35-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="03c35-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03c35-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="03c35-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="03c35-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="03c35-112">Olaylar</span><span class="sxs-lookup"><span data-stu-id="03c35-112">Events</span></span>](../events/index.md)
