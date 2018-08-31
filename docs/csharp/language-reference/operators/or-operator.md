---
title: '| İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: d95fe29aa7ffab9938e8edc57999445268fe41a8
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332003"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="33dc5-102">| İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="33dc5-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="33dc5-103">İkili `|` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`.</span><span class="sxs-lookup"><span data-stu-id="33dc5-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="33dc5-104">İntegral türleri için `|` kendi işlenenden bit seviyesinde veya hesaplar.</span><span class="sxs-lookup"><span data-stu-id="33dc5-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="33dc5-105">İçin `bool` işlenenini `|` işlenenleri; mantıksal OR hesaplar diğer bir deyişle, sonucudur `false` , her iki işlenen ve yalnızca, `false`.</span><span class="sxs-lookup"><span data-stu-id="33dc5-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33dc5-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33dc5-106">Remarks</span></span>  
 <span data-ttu-id="33dc5-107">İkili `|` işleci, birinci bağımsız olarak her iki işlenen değerlendirilir değerini, [koşullu-OR işleci] aksine (koşullu veya operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="33dc5-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator]     (conditional-or-operator.md) `||`.</span></span>
 
 <span data-ttu-id="33dc5-108">Kullanıcı tanımlı türler aşırı yükleme `|` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="33dc5-108">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33dc5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="33dc5-109">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="33dc5-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33dc5-110">See Also</span></span>

- [<span data-ttu-id="33dc5-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="33dc5-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="33dc5-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="33dc5-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="33dc5-113">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="33dc5-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
