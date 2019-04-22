---
title: İşleçlerin Etkili Bileşimi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841279"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="66249-102">İşleçlerin Etkili Bileşimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66249-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="66249-103">Birçok farklı işleçleri karmaşık ifadeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="66249-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="66249-104">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="66249-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="66249-105">Bir önceki örnekte gibi karmaşık ifadeler oluşturmak için işleç önceliği kurallarına Azure'un gerekir.</span><span class="sxs-lookup"><span data-stu-id="66249-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="66249-106">Daha fazla bilgi için [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="66249-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="66249-107">Parantez içinde ifadeler</span><span class="sxs-lookup"><span data-stu-id="66249-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="66249-108">Çoğu zaman İşleç önceliği tarafından belirlenen olanlardan farklı bir düzende devam etmek için işlem ister.</span><span class="sxs-lookup"><span data-stu-id="66249-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="66249-109">Aşağıdaki örnek göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="66249-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="66249-110">Yukarıdaki örnekte çarpar `z` tarafından `y`, ardından sonuca ekler `4`.</span><span class="sxs-lookup"><span data-stu-id="66249-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="66249-111">Ancak eklemek istiyorsanız `y` ve `4` sonucu çarpmadan önce `z`, parantezler kullanarak normal İşleç önceliği geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66249-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="66249-112">Bir ifadeyi parantez içine alarak, ilk olarak, İşleç önceliği bağımsız olarak değerlendirilecek ifade zorlar.</span><span class="sxs-lookup"><span data-stu-id="66249-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="66249-113">Ayrıca ilk yapmak için önceki örnekte zorlamak için aşağıdaki örnekte olduğu gibi yeniden yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66249-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="66249-114">Yukarıdaki örnekte ekler `y` ve `4`, ardından toplamı ile çarpar `z`.</span><span class="sxs-lookup"><span data-stu-id="66249-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="66249-115">Parantez içinde iç içe geçmiş ifadeler</span><span class="sxs-lookup"><span data-stu-id="66249-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="66249-116">Daha da önceliği geçersiz kılmak için parantez, birden çok düzeyi ifadelerini iç içe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66249-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="66249-117">Parantez içine en derin yuvalanmış ifadeleri en, vb. az derin şekilde iç içe geçmiş ve son olarak parantez dışında ifadeleri iç içe girmiş sonraki ardından ilk olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="66249-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="66249-118">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="66249-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="66249-119">Önceki örnekte `z + 2` değerlendirilen ilk sonra parantez içinde bir ifade.</span><span class="sxs-lookup"><span data-stu-id="66249-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="66249-120">Diğer ifadeler ayraç içindeki çünkü normalde toplama veya çarpma daha yüksek bir önceliğe sahiptir, üs olarak gösterme Bu örnekte son değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="66249-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66249-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66249-121">See also</span></span>

- [<span data-ttu-id="66249-122">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="66249-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="66249-123">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="66249-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="66249-124">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="66249-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="66249-125">Mantıksal/bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66249-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="66249-126">Boole İfadeleri</span><span class="sxs-lookup"><span data-stu-id="66249-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="66249-127">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="66249-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="66249-128">Nasıl yapılır: Sayısal değerleri hesaplama</span><span class="sxs-lookup"><span data-stu-id="66249-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="66249-129">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="66249-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
