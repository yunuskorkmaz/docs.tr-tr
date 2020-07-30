---
title: Temsilcileri birleştirme (çok noktaya yayın temsilcileri)-C# Programlama Kılavuzu
description: Temsilcileri çok noktaya yayın temsilcileri oluşturmak için birleştirmeyi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d23ea758c9da2c3399f5d98e81360cc250b428a1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302743"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="0e65f-104">Temsilcileri birleştirme (Çok Noktaya Yayın Temsilcileri) (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0e65f-104">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="0e65f-105">Bu örnek, çok noktaya yayın temsilcileri oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e65f-105">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="0e65f-106">[Temsilci](../../language-reference/builtin-types/reference-types.md) nesnelerinin yararlı bir özelliği, işleç kullanılarak bir temsilci örneğine birden çok nesne atanabilmesini sağlar `+` .</span><span class="sxs-lookup"><span data-stu-id="0e65f-106">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="0e65f-107">Çok noktaya yayın temsilcisi, atanan temsilcilerin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0e65f-107">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="0e65f-108">Çok noktaya yayın temsilcisi çağrıldığında, listedeki temsilcileri sırayla çağırır.</span><span class="sxs-lookup"><span data-stu-id="0e65f-108">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="0e65f-109">Yalnızca aynı türde temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0e65f-109">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="0e65f-110">`-`İşleci bir çok noktaya yayın temsilcisinden bir bileşen temsilcisini kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e65f-110">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e65f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e65f-111">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="0e65f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e65f-112">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="0e65f-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0e65f-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0e65f-114">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="0e65f-114">Events</span></span>](../events/index.md)
