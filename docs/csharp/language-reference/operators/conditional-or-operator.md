---
title: '|| İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: d22e57d097edb0fe52b604e9c6431e167c410f0b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171812"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cd173-102">|| İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cd173-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="cd173-103">Koşullu-OR işleci (`||`) bir mantıksal-OR, gerçekleştirir, `bool` işlenen.</span><span class="sxs-lookup"><span data-stu-id="cd173-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="cd173-104">İlk işlenen değerlendirilirse `true`, ikinci işlenen hesaplanan değil.</span><span class="sxs-lookup"><span data-stu-id="cd173-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="cd173-105">İlk işlenen değerlendirilirse `false`, ikinci işleci veya ifadesi bir bütün olarak değerlendiren olup olmadığını belirler `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="cd173-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd173-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd173-106">Remarks</span></span>  
 <span data-ttu-id="cd173-107">İşlemi</span><span class="sxs-lookup"><span data-stu-id="cd173-107">The operation</span></span>  
  
```csharp  
x || y  
```  
  
 <span data-ttu-id="cd173-108">işlemine karşılık gelir</span><span class="sxs-lookup"><span data-stu-id="cd173-108">corresponds to the operation</span></span>  
  
```csharp  
x | y  
```  
  
 <span data-ttu-id="cd173-109">dışındaki olması durumunda `x` olan `true`, `y` veya işlemi olduğundan değerlendirilmez `true` değerini bakılmaksızın `y`.</span><span class="sxs-lookup"><span data-stu-id="cd173-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="cd173-110">Bu kavram "değerlendirmesi"olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="cd173-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="cd173-111">Koşullu-OR işleci, normal mantıksal işleçleri aşırı aşırı yüklenemez ve [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md) işleçleri bazı kısıtlamalar ile de değerlendirilir aşırı olmalıdır Koşullu mantıksal işleçler.</span><span class="sxs-lookup"><span data-stu-id="cd173-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd173-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd173-112">Example</span></span>  
 <span data-ttu-id="cd173-113">Aşağıdaki örneklerde, ifade kullanan `||` yalnızca ilk işlenen değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="cd173-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="cd173-114">Kullanan deyimi `|` her iki işlenen değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="cd173-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="cd173-115">Her iki işlenen değerlendirildiğinde ikinci örnekte, bir çalışma zamanı özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="cd173-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cd173-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd173-116">See Also</span></span>  
 [<span data-ttu-id="cd173-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="cd173-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cd173-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cd173-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cd173-119">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="cd173-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
