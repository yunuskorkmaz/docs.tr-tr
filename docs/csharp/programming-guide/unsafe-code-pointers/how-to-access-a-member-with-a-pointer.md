---
title: 'Nasıl yapılır: İşaretçiyle bir Üyeye Erişme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 20f0dd18bb5ca132d05335953958d8f747b6abc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332208"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="07dd9-102">Nasıl yapılır: İşaretçiyle bir Üyeye Erişme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="07dd9-102">How to: Access a Member with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="07dd9-103">Güvenli olmayan bir içerikte bildirilmiş bir yapı üyesi erişmek için üye erişimi işleci aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz `p` gösteren bir işaretçidir bir [yapısı](../../../csharp/language-reference/keywords/struct.md) üyesi içeren `x`.</span><span class="sxs-lookup"><span data-stu-id="07dd9-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="07dd9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="07dd9-104">Example</span></span>  
 <span data-ttu-id="07dd9-105">Bu örnekte, bir [yapısı](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, iki koordinat içeren `x` ve `y` bildirilir ve örneği.</span><span class="sxs-lookup"><span data-stu-id="07dd9-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="07dd9-106">Üye erişimi işleci kullanılarak `->` örneğini gösteren bir işaretçi `home`, `x` ve `y` değerler atanır.</span><span class="sxs-lookup"><span data-stu-id="07dd9-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07dd9-107">Dikkat ifade `p->x` ifade eşdeğerdir `(*p).x`, ve iki ifadeye birini kullanarak aynı sonucu elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07dd9-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="07dd9-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07dd9-108">See Also</span></span>  
 [<span data-ttu-id="07dd9-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="07dd9-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="07dd9-110">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="07dd9-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="07dd9-111">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="07dd9-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="07dd9-112">Türler</span><span class="sxs-lookup"><span data-stu-id="07dd9-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="07dd9-113">unsafe</span><span class="sxs-lookup"><span data-stu-id="07dd9-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="07dd9-114">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="07dd9-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="07dd9-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="07dd9-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
