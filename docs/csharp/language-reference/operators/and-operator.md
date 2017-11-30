---
title: "&amp;İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eceee8e01ba46f65c6b182a40d14e62aaba5dd53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="48371-102">&amp;İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="48371-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="48371-103">& İşleci bir birli ya da bir ikili işleç olarak işlev görebilir.</span><span class="sxs-lookup"><span data-stu-id="48371-103">The & operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48371-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48371-104">Remarks</span></span>  
 <span data-ttu-id="48371-105">Birli & işleci, işlenen adresini döndürür (gerektirir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlam).</span><span class="sxs-lookup"><span data-stu-id="48371-105">The unary & operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="48371-106">İkili & işleçleri tam sayı türleri için önceden tanımlanmış ve `bool`.</span><span class="sxs-lookup"><span data-stu-id="48371-106">Binary & operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="48371-107">İntegral için türleri & işlenenleri mantıksal bit düzeyinde AND hesaplar.</span><span class="sxs-lookup"><span data-stu-id="48371-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="48371-108">İçin `bool` işlenenler & mantıksal hesaplar ve onun işlenenleri; diğer bir deyişle, sonuç `true` , her iki işlenen ve yalnızca, `true`.</span><span class="sxs-lookup"><span data-stu-id="48371-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="48371-109">`&` İşleci değerlendirir ilk bağımsız olarak her iki işleçler kılavuzuna değeri.</span><span class="sxs-lookup"><span data-stu-id="48371-109">The `&` operator evaluates both operators regardless of the first one's value.</span></span> <span data-ttu-id="48371-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="48371-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="48371-111">Kullanıcı tanımlı türler ikili aşırı yükleme `&` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="48371-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="48371-112">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="48371-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="48371-113">İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="48371-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48371-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="48371-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="48371-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48371-115">See Also</span></span>  
 [<span data-ttu-id="48371-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="48371-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="48371-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="48371-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="48371-118">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="48371-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
