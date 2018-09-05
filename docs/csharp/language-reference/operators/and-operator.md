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
ms.openlocfilehash: b257c7d41618464e26ab3b54bcfb1f1e2c2e420e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510984"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="96cf3-102">&amp; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="96cf3-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="96cf3-103">`&` İşleci bir birli veya ikili işleç olarak işlev görebilir.</span><span class="sxs-lookup"><span data-stu-id="96cf3-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96cf3-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96cf3-104">Remarks</span></span>  
 <span data-ttu-id="96cf3-105">Birli `&` işleci, işlenenin adresini verir (gerektirir [güvenli](../../../csharp/language-reference/keywords/unsafe.md) bağlamı).</span><span class="sxs-lookup"><span data-stu-id="96cf3-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="96cf3-106">İkili `&` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`.</span><span class="sxs-lookup"><span data-stu-id="96cf3-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="96cf3-107">İçin tam sayı türleri & mantıksal bit seviyesinde ve işlenenleri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="96cf3-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="96cf3-108">İçin `bool` işlenenler & mantıksal hesaplar ve işlenenleri; diğer bir deyişle, sonuç `true` , her iki işlenen ve yalnızca, `true`.</span><span class="sxs-lookup"><span data-stu-id="96cf3-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="96cf3-109">İkili `&` işleci, birinci bağımsız olarak her iki işlenen değerlendirilir değerini, buna için [koşullu AND işleci](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span><span class="sxs-lookup"><span data-stu-id="96cf3-109">The binary `&` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="96cf3-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="96cf3-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="96cf3-111">Kullanıcı tanımlı türler ikili aşırı yükleme `&` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="96cf3-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="96cf3-112">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="96cf3-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="96cf3-113">İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="96cf3-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96cf3-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="96cf3-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="96cf3-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96cf3-115">See Also</span></span>

- [<span data-ttu-id="96cf3-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="96cf3-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="96cf3-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="96cf3-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="96cf3-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="96cf3-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
