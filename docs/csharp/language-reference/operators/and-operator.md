---
title: '&amp; İşleci (C# Başvurusu)'
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 59813b4bc5781776c9f9741c3e49e660c684bff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267886"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="c727f-102">&amp; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c727f-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="c727f-103">`&` İşleci bir birli ya da bir ikili işleç olarak işlev görebilir.</span><span class="sxs-lookup"><span data-stu-id="c727f-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c727f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c727f-104">Remarks</span></span>  
 <span data-ttu-id="c727f-105">Birli `&` işleci, kendi işleneni adresini döndürür (gerektirir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlam).</span><span class="sxs-lookup"><span data-stu-id="c727f-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="c727f-106">İkili `&` işleçleri tam sayı türleri için önceden tanımlanmış ve `bool`.</span><span class="sxs-lookup"><span data-stu-id="c727f-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="c727f-107">İntegral için türleri & işlenenleri mantıksal bit düzeyinde AND hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c727f-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="c727f-108">İçin `bool` işlenenler & mantıksal hesaplar ve onun işlenenleri; diğer bir deyişle, sonuç `true` , her iki işlenen ve yalnızca, `true`.</span><span class="sxs-lookup"><span data-stu-id="c727f-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="c727f-109">İkili `&` işleci değerlendirir ilk bağımsız olarak her iki işleçler kılavuzuna değerini, buna karşılık [koşullu AND işleci](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span><span class="sxs-lookup"><span data-stu-id="c727f-109">The binary `&` operator evaluates both operators regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="c727f-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c727f-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="c727f-111">Kullanıcı tanımlı türler ikili aşırı yükleme `&` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c727f-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="c727f-112">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c727f-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="c727f-113">İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="c727f-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c727f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c727f-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c727f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c727f-115">See Also</span></span>  
 [<span data-ttu-id="c727f-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c727f-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c727f-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c727f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c727f-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c727f-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
