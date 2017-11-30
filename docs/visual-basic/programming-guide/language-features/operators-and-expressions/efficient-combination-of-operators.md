---
title: "İşleçlerin Etkili Bileşimi (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b0f1d637bc1757515cf271a8c70d62effab0843
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="02619-102">İşleçlerin Etkili Bileşimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02619-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="02619-103">Karmaşık ifadeler birçok farklı işleçleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="02619-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="02619-104">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="02619-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="02619-105">Bir önceki örnekte gibi karmaşık ifadeler oluşturma İşleç önceliği kuralları kapsamlı olarak anlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="02619-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="02619-106">Daha fazla bilgi için bkz: [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="02619-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="02619-107">Parantez içinde ifadeler</span><span class="sxs-lookup"><span data-stu-id="02619-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="02619-108">Genellikle operations İşleç önceliği tarafından belirlenen ile farklı sırada devam etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="02619-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="02619-109">Aşağıdaki örnek göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="02619-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="02619-110">Önceki örnekte çarpar `z` tarafından `y`, sonuca ekler `4`.</span><span class="sxs-lookup"><span data-stu-id="02619-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="02619-111">Ancak eklemek istiyorsanız `y` ve `4` sonucu çarparak önce `z`, parantez kullanarak normal İşleç önceliği geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02619-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="02619-112">Bir ifade parantez içinde kapsayan tarafından ilk olarak, İşleç önceliği bağımsız olarak değerlendirilecek ifade zorlar.</span><span class="sxs-lookup"><span data-stu-id="02619-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="02619-113">Ayrıca ilk yapmak için önceki örnekte zorlamak için aşağıdaki örnekte olduğu gibi yeniden yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02619-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="02619-114">Önceki örnekte ekler `y` ve `4`, toplamı tarafından çarpar `z`.</span><span class="sxs-lookup"><span data-stu-id="02619-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="02619-115">İç içe geçmiş parantez içinde ifadeler</span><span class="sxs-lookup"><span data-stu-id="02619-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="02619-116">Parantez daha önceliği geçersiz kılmak için birden çok düzeyi ifadelerinde yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02619-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="02619-117">En fazla parantez içinde iç içe ifadeler, ilk olarak, en fazla, vb. az iç içe ve son olarak parantez dışında ifadeleri iç içe sonraki arkasından değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="02619-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="02619-118">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="02619-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="02619-119">Önceki örnekte `z + 2` değerlendirilen ilk sonra parantez içinde bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="02619-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="02619-120">Diğer ifadeler parantez içine alınmış olduğundan normalde toplama veya çarpma daha yüksek önceliğe sahiptir, üs son Bu örnekte değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="02619-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02619-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02619-121">See Also</span></span>  
 [<span data-ttu-id="02619-122">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="02619-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="02619-123">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="02619-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="02619-124">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="02619-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="02619-125">Mantıksal ve bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02619-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="02619-126">Boole ifadeleri</span><span class="sxs-lookup"><span data-stu-id="02619-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="02619-127">Değer karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="02619-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="02619-128">Nasıl yapılır: sayısal değerleri hesaplama</span><span class="sxs-lookup"><span data-stu-id="02619-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="02619-129">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="02619-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
