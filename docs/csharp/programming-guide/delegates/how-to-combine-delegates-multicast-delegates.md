---
title: Temsilcileri birleştirme (çok noktaya yayın temsilcileri)-C# Programlama Kılavuzu
description: Temsilcileri çok noktaya yayın temsilcileri oluşturmak için birleştirmeyi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 3e86c8ed4b7b091ee8c75930d427c22aa5bc0c52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185957"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="0f7b5-104">Temsilcileri birleştirme (Çok Noktaya Yayın Temsilcileri) (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0f7b5-104">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>

<span data-ttu-id="0f7b5-105">Bu örnek, çok noktaya yayın temsilcileri oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-105">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="0f7b5-106">[Temsilci](../../language-reference/builtin-types/reference-types.md) nesnelerinin yararlı bir özelliği, işleç kullanılarak bir temsilci örneğine birden çok nesne atanabilmesini sağlar `+` .</span><span class="sxs-lookup"><span data-stu-id="0f7b5-106">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="0f7b5-107">Çok noktaya yayın temsilcisi, atanan temsilcilerin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-107">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="0f7b5-108">Çok noktaya yayın temsilcisi çağrıldığında, listedeki temsilcileri sırayla çağırır.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-108">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="0f7b5-109">Yalnızca aynı türde temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-109">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="0f7b5-110">`-`İşleci bir çok noktaya yayın temsilcisinden bir bileşen temsilcisini kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-110">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f7b5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f7b5-111">Example</span></span>  

 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="0f7b5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-112">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="0f7b5-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0f7b5-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0f7b5-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0f7b5-114">Events</span></span>](../events/index.md)
