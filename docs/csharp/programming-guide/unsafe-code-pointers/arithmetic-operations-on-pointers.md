---
title: -İşaretçilerde aritmetik işlemler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: b08f9dbf8137e483bd38a4f396732191598532cf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635228"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="94edd-102">İşaretçilerde aritmetik işlemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="94edd-102">Arithmetic operations on pointers (C# Programming Guide)</span></span>
<span data-ttu-id="94edd-103">Aritmetik işleçler kullanarak bu konuda ele alınmıştır `+` ve `-` işaretçileri işlemek için.</span><span class="sxs-lookup"><span data-stu-id="94edd-103">This topic discusses using the arithmetic operators `+` and `-` to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94edd-104">Tüm void işaretçilerde aritmetik işlemler gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="94edd-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="94edd-105">Ekleme ve çıkarma işaretçileri gelen veya sayısal değerler</span><span class="sxs-lookup"><span data-stu-id="94edd-105">Adding and subtracting numeric values to or from pointers</span></span>  
 <span data-ttu-id="94edd-106">Bir değer eklediğiniz `n` türü [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), veya [ulong](../../../csharp/language-reference/keywords/ulong.md) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="94edd-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer.</span></span> <span data-ttu-id="94edd-107">Varsa `p` bir işaretçi türü `pointer-type*`, sonuç `p+n` eklemesini elde edilen işaretçi `n * sizeof(pointer-type)` adresine `p`.</span><span class="sxs-lookup"><span data-stu-id="94edd-107">If `p` is a pointer of the type `pointer-type*`, the result `p+n` is the pointer resulting from adding `n * sizeof(pointer-type)` to the address of `p`.</span></span> <span data-ttu-id="94edd-108">Benzer şekilde, `p-n` arasındaki çıkarma işleminin sonucu işaretçi `n * sizeof(pointer-type)` adresinden `p`.</span><span class="sxs-lookup"><span data-stu-id="94edd-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(pointer-type)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="94edd-109">Çıkarma işaretçileri</span><span class="sxs-lookup"><span data-stu-id="94edd-109">Subtracting pointers</span></span>  
 <span data-ttu-id="94edd-110">Ayrıca, aynı türde işaretçileri çıkarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94edd-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="94edd-111">Sonucu her zaman türüdür `long`.</span><span class="sxs-lookup"><span data-stu-id="94edd-111">The result is always of the type `long`.</span></span> <span data-ttu-id="94edd-112">Örneğin, varsa `p1` ve `p2` türünde işaretçiler `pointer-type*`, ifade `p1-p2` sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="94edd-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 <span data-ttu-id="94edd-113">Hiçbir özel durum, etki alanı işaretçinin aritmetik işlemi taşıyor ve sonuç uygulamasının bağlıdır, üretilir.</span><span class="sxs-lookup"><span data-stu-id="94edd-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94edd-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="94edd-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#14)]  
  
 [!code-csharp[csProgGuidePointers#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#15)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="94edd-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="94edd-115">C# language specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94edd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94edd-116">See also</span></span>

- [<span data-ttu-id="94edd-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="94edd-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="94edd-118">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="94edd-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="94edd-119">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="94edd-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="94edd-120">İşaretçileri İşleme</span><span class="sxs-lookup"><span data-stu-id="94edd-120">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [<span data-ttu-id="94edd-121">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="94edd-121">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="94edd-122">Türler</span><span class="sxs-lookup"><span data-stu-id="94edd-122">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="94edd-123">unsafe</span><span class="sxs-lookup"><span data-stu-id="94edd-123">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="94edd-124">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="94edd-124">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="94edd-125">stackalloc</span><span class="sxs-lookup"><span data-stu-id="94edd-125">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
