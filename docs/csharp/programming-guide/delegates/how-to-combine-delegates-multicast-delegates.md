---
title: 'Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e1214a4d281dbcb9d8186770b68510d3d9a4b15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327401"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="04ca0-102">Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="04ca0-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="04ca0-103">Bu örnek çok noktaya yayın temsilcileri oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="04ca0-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="04ca0-104">Kullanışlı bir özelliği [temsilci](../../../csharp/language-reference/keywords/delegate.md) nesnedir kullanarak birden çok nesne bir temsilci örneğine atanabilir `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="04ca0-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="04ca0-105">Çok noktaya yayın temsilci atanan temsilcileri listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="04ca0-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="04ca0-106">Çok noktaya yayın temsilci çağrıldığında, sırayla listesinde temsilcileri çağırır.</span><span class="sxs-lookup"><span data-stu-id="04ca0-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="04ca0-107">Yalnızca aynı türdeki temsilciler birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="04ca0-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="04ca0-108">`-` İşleci, çok noktaya yayın bir temsilciyi bileşen temsilciyi kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04ca0-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04ca0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="04ca0-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="04ca0-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04ca0-110">See Also</span></span>  
 <xref:System.MulticastDelegate>  
 [<span data-ttu-id="04ca0-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="04ca0-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="04ca0-112">Olaylar</span><span class="sxs-lookup"><span data-stu-id="04ca0-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
