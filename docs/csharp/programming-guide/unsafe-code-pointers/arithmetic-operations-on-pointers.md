---
title: "İşaretçilerde Aritmetik İşlemler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 54c439aab8b6cd34a796db8d31f9eabeefddf9f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="867ea-102">İşaretçilerde Aritmetik İşlemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="867ea-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="867ea-103">Aritmetik işleçler kullanarak bu konuda ele alınmıştır `+` ve  **-**  işaretçileri yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="867ea-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="867ea-104">Void işaretçileri hiçbir aritmetik işlemler gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="867ea-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="867ea-105">Ekleme ve çıkarma sayısal değerler için veya işaretçileri</span><span class="sxs-lookup"><span data-stu-id="867ea-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="867ea-106">Bir değer ekleyebilirsiniz `n` türü [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), veya [ulong](../../../csharp/language-reference/keywords/ulong.md) bir işaretçi için `p`, herhangi bir türde `void*`.</span><span class="sxs-lookup"><span data-stu-id="867ea-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="867ea-107">Sonuç `p+n` eklemelerini kaynaklanan işaretçi `n * sizeof(p) to the address of p`.</span><span class="sxs-lookup"><span data-stu-id="867ea-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="867ea-108">Benzer şekilde, `p-n` alanından çıkarılmasıyla elde edilen işaretçi `n * sizeof(p)` adresinden gelen `p`.</span><span class="sxs-lookup"><span data-stu-id="867ea-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="867ea-109">İşaretçileri çıkarma</span><span class="sxs-lookup"><span data-stu-id="867ea-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="867ea-110">Aynı türde işaretçileri çıkarın.</span><span class="sxs-lookup"><span data-stu-id="867ea-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="867ea-111">Sonuç her zaman türüdür `long`.</span><span class="sxs-lookup"><span data-stu-id="867ea-111">The result is always of the type `long`.</span></span> <span data-ttu-id="867ea-112">Örneğin, varsa `p1` ve `p2` türü işaretçileridir `pointer-type*`, ardından ifade `p1-p2` sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="867ea-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="867ea-113">Hiçbir özel durum, etki alanı işaretçinin aritmetik işlemin taşar ve sonucu uygulamasına bağlıdır, üretilir.</span><span class="sxs-lookup"><span data-stu-id="867ea-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="867ea-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="867ea-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="867ea-115">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="867ea-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="867ea-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="867ea-116">See Also</span></span>  
 [<span data-ttu-id="867ea-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="867ea-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="867ea-118">Güvenli olmayan kod ve işaretçiler</span><span class="sxs-lookup"><span data-stu-id="867ea-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="867ea-119">İşaretçi ifadeleri</span><span class="sxs-lookup"><span data-stu-id="867ea-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="867ea-120">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="867ea-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="867ea-121">İşaretçileri işleme</span><span class="sxs-lookup"><span data-stu-id="867ea-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="867ea-122">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="867ea-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="867ea-123">Türler</span><span class="sxs-lookup"><span data-stu-id="867ea-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="867ea-124">güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="867ea-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="867ea-125">fixed deyimi</span><span class="sxs-lookup"><span data-stu-id="867ea-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="867ea-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="867ea-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
