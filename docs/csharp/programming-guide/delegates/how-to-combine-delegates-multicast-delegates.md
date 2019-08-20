---
title: 'Nasıl yapılır: Temsilcileri birleştirme (çok noktaya yayın temsilcileri C# )-Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d9430021e6a9b438822f1a6dc201f64adf4fdb0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590670"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="f8bd9-102">Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f8bd9-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="f8bd9-103">Bu örnek, çok noktaya yayın temsilcileri oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="f8bd9-104">[Temsilci](../../language-reference/keywords/delegate.md) nesnelerinin yararlı bir özelliği, `+` işleç kullanılarak bir temsilci örneğine birden çok nesne atanabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-104">A useful property of [delegate](../../language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="f8bd9-105">Çok noktaya yayın temsilcisi, atanan temsilcilerin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="f8bd9-106">Çok noktaya yayın temsilcisi çağrıldığında, listedeki temsilcileri sırayla çağırır.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="f8bd9-107">Yalnızca aynı türde temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="f8bd9-108">`-` İşleci bir çok noktaya yayın temsilcisinden bir bileşen temsilcisini kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8bd9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8bd9-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="f8bd9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="f8bd9-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f8bd9-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f8bd9-112">Olaylar</span><span class="sxs-lookup"><span data-stu-id="f8bd9-112">Events</span></span>](../events/index.md)
