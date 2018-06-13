---
title: '&amp;&amp; İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 15bb3e9702f04cc805af63767c7ecbfc68160368
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171921"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="5ad2c-102">&amp;&amp; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5ad2c-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="5ad2c-103">Koşullu- ve işleci (`&&`) bir mantıksal gerçekleştirir- ve kendi `bool` işlenenler, ancak yalnızca kendi ikinci işlenen gerekirse değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="5ad2c-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ad2c-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ad2c-104">Remarks</span></span>  
 <span data-ttu-id="5ad2c-105">İşlemi</span><span class="sxs-lookup"><span data-stu-id="5ad2c-105">The operation</span></span>  
  
```csharp  
x && y  
```  
  
 <span data-ttu-id="5ad2c-106">işlemine karşılık gelir</span><span class="sxs-lookup"><span data-stu-id="5ad2c-106">corresponds to the operation</span></span>  
  
```csharp  
x & y  
```  
  
 <span data-ttu-id="5ad2c-107">dışındaki olması durumunda `x` olan `false`, `y` ve işleminin sonucu olduğundan, değerlendirilmez `false` hangi değerini olsun `y` değil.</span><span class="sxs-lookup"><span data-stu-id="5ad2c-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="5ad2c-108">Bu "değerlendirmesi"olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="5ad2c-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="5ad2c-109">Koşullu- ve işleci aşırı yüklenmiş, olamaz, ancak normal mantıksal işleçleri aşırı ve işleçleri [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md) bazı kısıtlamalar ile de aşırı olarak kabul edilir Koşullu mantıksal işleçler.</span><span class="sxs-lookup"><span data-stu-id="5ad2c-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ad2c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ad2c-110">Example</span></span>  
 <span data-ttu-id="5ad2c-111">Aşağıdaki örnekte, koşullu ifade ikinci `if` deyimi değerlendirir yalnızca ilk işlenen işleneni döndürdüğünden `false`.</span><span class="sxs-lookup"><span data-stu-id="5ad2c-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5ad2c-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5ad2c-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5ad2c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ad2c-113">See Also</span></span>  
 [<span data-ttu-id="5ad2c-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5ad2c-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5ad2c-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5ad2c-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5ad2c-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="5ad2c-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
