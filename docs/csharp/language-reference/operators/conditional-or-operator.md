---
title: '|| İşleci (C# Başvurusu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b95fd162c9a89789e1970b32473c8acf16ba5cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b8569-102">|| İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b8569-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="b8569-103">Koşullu-OR işleci (`||`) bir mantıksal-OR, gerçekleştirir, `bool` işlenen.</span><span class="sxs-lookup"><span data-stu-id="b8569-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="b8569-104">İlk işlenen değerlendirilirse `true`, ikinci işlenen hesaplanan değil.</span><span class="sxs-lookup"><span data-stu-id="b8569-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="b8569-105">İlk işlenen değerlendirilirse `false`, ikinci işleci veya ifadesi bir bütün olarak değerlendiren olup olmadığını belirler `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="b8569-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8569-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8569-106">Remarks</span></span>  
 <span data-ttu-id="b8569-107">İşlemi</span><span class="sxs-lookup"><span data-stu-id="b8569-107">The operation</span></span>  
  
```  
x || y  
```  
  
 <span data-ttu-id="b8569-108">işlemine karşılık gelir</span><span class="sxs-lookup"><span data-stu-id="b8569-108">corresponds to the operation</span></span>  
  
```  
x | y  
```  
  
 <span data-ttu-id="b8569-109">dışındaki olması durumunda `x` olan `true`, `y` veya işlemi olduğundan değerlendirilmez `true` değerini bakılmaksızın `y`.</span><span class="sxs-lookup"><span data-stu-id="b8569-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="b8569-110">Bu kavram "değerlendirmesi"olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="b8569-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="b8569-111">Koşullu-OR işleci, normal mantıksal işleçleri aşırı aşırı yüklenemez ve [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md) işleçleri bazı kısıtlamalar ile de değerlendirilir aşırı olmalıdır Koşullu mantıksal işleçler.</span><span class="sxs-lookup"><span data-stu-id="b8569-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8569-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8569-112">Example</span></span>  
 <span data-ttu-id="b8569-113">Aşağıdaki örneklerde, ifade kullanan `||` yalnızca ilk işlenen değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b8569-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="b8569-114">Kullanan deyimi `|` her iki işlenen değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b8569-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="b8569-115">Her iki işlenen değerlendirildiğinde ikinci örnekte, bir çalışma zamanı özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="b8569-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b8569-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8569-116">See Also</span></span>  
 [<span data-ttu-id="b8569-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b8569-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b8569-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b8569-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b8569-119">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="b8569-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
