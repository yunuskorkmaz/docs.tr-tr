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
ms.openlocfilehash: 58e5fd72a3748e7af0894093fc461c4efb543608
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925546"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="52e5e-102">|| İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="52e5e-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="52e5e-103">Koşullu-OR işleci (`||`) bir mantıksal OR gerçekleştirir, `bool` işlenen.</span><span class="sxs-lookup"><span data-stu-id="52e5e-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="52e5e-104">Birinci işlenenin değerlendirilirse `true`, ikinci işlenenin değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="52e5e-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="52e5e-105">Birinci işlenenin değerlendirilirse `false`, ikinci işleç veya ifadenin bir bütün olarak değerlendirdiği olup olmadığını belirler. `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="52e5e-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52e5e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52e5e-106">Remarks</span></span>  
 <span data-ttu-id="52e5e-107">İşlemi</span><span class="sxs-lookup"><span data-stu-id="52e5e-107">The operation</span></span>  
  
```csharp  
x || y  
```  
  
 <span data-ttu-id="52e5e-108">işlemine karşılık gelir</span><span class="sxs-lookup"><span data-stu-id="52e5e-108">corresponds to the operation</span></span>  
  
```csharp  
x | y  
```  
  
 <span data-ttu-id="52e5e-109">dışındaki olması durumunda `x` olduğu `true`, `y` veya işlemi olduğundan değerlendirilmez `true` değerinden bağımsız olarak `y`.</span><span class="sxs-lookup"><span data-stu-id="52e5e-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="52e5e-110">Bu kavram, "kısa devre değerlendirmesi gibi" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="52e5e-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="52e5e-111">Koşullu-OR işleci, normal mantıksal işleçler aşırı aşırı yüklenemez ve [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md) işleçleri bazı kısıtlamalar ile ayrıca değerlendirilir aşırı olması Koşullu mantıksal işleçler.</span><span class="sxs-lookup"><span data-stu-id="52e5e-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52e5e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="52e5e-112">Example</span></span>  
 <span data-ttu-id="52e5e-113">Aşağıdaki örneklerde, ifade kullanan `||` yalnızca ilk işlenen değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="52e5e-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="52e5e-114">Kullanan ifade `|` her iki işlenen değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="52e5e-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="52e5e-115">Her iki işlenen değerlendirilir ikinci örnekte, bir çalışma zamanı özel durum ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="52e5e-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="52e5e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52e5e-116">See Also</span></span>

- [<span data-ttu-id="52e5e-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="52e5e-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="52e5e-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="52e5e-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="52e5e-119">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="52e5e-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
