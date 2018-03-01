---
title: "&amp;&amp;İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16bc2fa650031d2b1f6cfaf7d128ba487963f707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="210a8-102">&amp;&amp;İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="210a8-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="210a8-103">Koşullu- ve işleci (`&&`) bir mantıksal gerçekleştirir- ve kendi `bool` işlenenler, ancak yalnızca kendi ikinci işlenen gerekirse değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="210a8-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="210a8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="210a8-104">Remarks</span></span>  
 <span data-ttu-id="210a8-105">İşlemi</span><span class="sxs-lookup"><span data-stu-id="210a8-105">The operation</span></span>  
  
```  
x && y  
```  
  
 <span data-ttu-id="210a8-106">işlemine karşılık gelir</span><span class="sxs-lookup"><span data-stu-id="210a8-106">corresponds to the operation</span></span>  
  
```  
x & y  
```  
  
 <span data-ttu-id="210a8-107">dışındaki olması durumunda `x` olan `false`, `y` ve işleminin sonucu olduğundan, değerlendirilmez `false` hangi değerini olsun `y` değil.</span><span class="sxs-lookup"><span data-stu-id="210a8-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="210a8-108">Bu "değerlendirmesi"olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="210a8-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="210a8-109">Koşullu- ve işleci aşırı yüklenmiş, olamaz, ancak normal mantıksal işleçleri aşırı ve işleçleri [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md) bazı kısıtlamalar ile de aşırı olarak kabul edilir Koşullu mantıksal işleçler.</span><span class="sxs-lookup"><span data-stu-id="210a8-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="210a8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="210a8-110">Example</span></span>  
 <span data-ttu-id="210a8-111">Aşağıdaki örnekte, koşullu ifade ikinci `if` deyimi değerlendirir yalnızca ilk işlenen işleneni döndürdüğünden `false`.</span><span class="sxs-lookup"><span data-stu-id="210a8-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="210a8-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="210a8-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="210a8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="210a8-113">See Also</span></span>  
 [<span data-ttu-id="210a8-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="210a8-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="210a8-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="210a8-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="210a8-116">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="210a8-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
