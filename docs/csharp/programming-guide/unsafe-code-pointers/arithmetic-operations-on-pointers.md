---
title: İşaretçilerde Aritmetik İşlemler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: c40b125e42649093aa1f1fe860a3e8f5d2690359
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324307"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="03ca0-102">İşaretçilerde Aritmetik İşlemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="03ca0-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="03ca0-103">Aritmetik işleçler kullanarak bu konuda ele alınmıştır `+` ve **-** işaretçileri yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="03ca0-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03ca0-104">Void işaretçileri hiçbir aritmetik işlemler gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="03ca0-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="03ca0-105">Ekleme ve çıkarma sayısal değerler için veya işaretçileri</span><span class="sxs-lookup"><span data-stu-id="03ca0-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="03ca0-106">Bir değer ekleyebilirsiniz `n` türü [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), veya [ulong](../../../csharp/language-reference/keywords/ulong.md) bir işaretçi için `p`, herhangi bir türde `void*`.</span><span class="sxs-lookup"><span data-stu-id="03ca0-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="03ca0-107">Sonuç `p+n` eklemelerini kaynaklanan işaretçi `n * sizeof(p) to the address of p`.</span><span class="sxs-lookup"><span data-stu-id="03ca0-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="03ca0-108">Benzer şekilde, `p-n` alanından çıkarılmasıyla elde edilen işaretçi `n * sizeof(p)` adresinden gelen `p`.</span><span class="sxs-lookup"><span data-stu-id="03ca0-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="03ca0-109">İşaretçileri çıkarma</span><span class="sxs-lookup"><span data-stu-id="03ca0-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="03ca0-110">Aynı türde işaretçileri çıkarın.</span><span class="sxs-lookup"><span data-stu-id="03ca0-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="03ca0-111">Sonuç her zaman türüdür `long`.</span><span class="sxs-lookup"><span data-stu-id="03ca0-111">The result is always of the type `long`.</span></span> <span data-ttu-id="03ca0-112">Örneğin, varsa `p1` ve `p2` türü işaretçileridir `pointer-type*`, ardından ifade `p1-p2` sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="03ca0-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="03ca0-113">Hiçbir özel durum, etki alanı işaretçinin aritmetik işlemin taşar ve sonucu uygulamasına bağlıdır, üretilir.</span><span class="sxs-lookup"><span data-stu-id="03ca0-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03ca0-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="03ca0-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="03ca0-115">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="03ca0-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="03ca0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03ca0-116">See Also</span></span>  
 [<span data-ttu-id="03ca0-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="03ca0-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="03ca0-118">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="03ca0-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="03ca0-119">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="03ca0-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="03ca0-120">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="03ca0-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="03ca0-121">İşaretçileri İşleme</span><span class="sxs-lookup"><span data-stu-id="03ca0-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="03ca0-122">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="03ca0-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="03ca0-123">Türler</span><span class="sxs-lookup"><span data-stu-id="03ca0-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="03ca0-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="03ca0-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="03ca0-125">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="03ca0-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="03ca0-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="03ca0-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
