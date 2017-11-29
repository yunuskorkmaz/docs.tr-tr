---
title: "Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ddb4ecbbf456179e91aa0003c2dc5653f153411f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="d7581-102">Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d7581-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="d7581-103">Bu örnek çok noktaya yayın temsilcileri oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7581-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="d7581-104">Kullanışlı bir özelliği [temsilci](../../../csharp/language-reference/keywords/delegate.md) nesnedir kullanarak birden çok nesne bir temsilci örneğine atanabilir `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="d7581-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="d7581-105">Çok noktaya yayın temsilci atanan temsilcileri listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d7581-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="d7581-106">Çok noktaya yayın temsilci çağrıldığında, sırayla listesinde temsilcileri çağırır.</span><span class="sxs-lookup"><span data-stu-id="d7581-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="d7581-107">Yalnızca aynı türdeki temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d7581-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="d7581-108">`-` İşleci, çok noktaya yayın bir temsilciyi bileşen temsilciyi kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7581-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7581-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7581-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d7581-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7581-110">See Also</span></span>  
 <xref:System.MulticastDelegate>  
 [<span data-ttu-id="d7581-111">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d7581-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d7581-112">Olayları</span><span class="sxs-lookup"><span data-stu-id="d7581-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
