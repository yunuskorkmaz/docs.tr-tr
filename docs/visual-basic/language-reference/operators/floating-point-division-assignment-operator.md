---
title: "/= İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94448856072a949582e64577287134c4b975bfec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e0cfc-102">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0cfc-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="e0cfc-103">Bir değişken ya da özellik değeri bir ifadenin değerini tarafından böler ve kayan noktalı bir sonuç değişken ya da özelliğin atar.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0cfc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0cfc-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="e0cfc-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e0cfc-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="e0cfc-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-106">Required.</span></span> <span data-ttu-id="e0cfc-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="e0cfc-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-108">Required.</span></span> <span data-ttu-id="e0cfc-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0cfc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0cfc-110">Remarks</span></span>  
 <span data-ttu-id="e0cfc-111">Öğe sol tarafındaki `/=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e0cfc-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="e0cfc-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e0cfc-113">`/=` İşleci ilk böler değişkeni veya (sol taraftaki işlecinin) özellik değerini (sağ taraftaki işlecinin) ifadesinin değerini tarafından.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="e0cfc-114">İşleci kayan nokta işlemin sonucu olarak, değişken veya özellik sonra atar.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="e0cfc-115">Bu ifade atar bir `Double` değişken ya da sol taraftaki özelliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="e0cfc-116">Varsa `Option Strict` olan `On`, `variableorproperty` olmalıdır bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="e0cfc-117">Varsa `Option Strict` olan `Off`, Visual Basic örtük bir dönüştürme gerçekleştirir ve çıkan değeri atar `variableorproperty`, çalışma zamanında olası hata.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="e0cfc-118">Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e0cfc-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e0cfc-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="e0cfc-119">Overloading</span></span>  
 <span data-ttu-id="e0cfc-120">[/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e0cfc-121">Aşırı yükleme `/` işleci davranışını etkileyen `/=` işleci.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="e0cfc-122">Kodunuzu kullanıyorsa `/=` bir sınıf veya overloads yapısı `/`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e0cfc-123">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e0cfc-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0cfc-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0cfc-124">Example</span></span>  
 <span data-ttu-id="e0cfc-125">Aşağıdaki örnek kullanır `/=` bir bölme işleci `Integer` değişken ikinci ve sayının ilk değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e0cfc-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0cfc-126">See Also</span></span>  
 [<span data-ttu-id="e0cfc-127">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0cfc-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="e0cfc-128">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="e0cfc-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="e0cfc-129">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="e0cfc-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="e0cfc-130">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="e0cfc-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="e0cfc-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="e0cfc-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="e0cfc-132">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="e0cfc-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="e0cfc-133">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="e0cfc-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
