---
title: /= İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 642307bc531e7d9ce21a932b112795b35e7b3182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604100"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f080d-102">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f080d-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="f080d-103">Bir değişken ya da özellik değeri bir ifadenin değerini tarafından böler ve kayan noktalı bir sonuç değişken ya da özelliğin atar.</span><span class="sxs-lookup"><span data-stu-id="f080d-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f080d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f080d-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f080d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f080d-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="f080d-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f080d-106">Required.</span></span> <span data-ttu-id="f080d-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="f080d-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="f080d-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f080d-108">Required.</span></span> <span data-ttu-id="f080d-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="f080d-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f080d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f080d-110">Remarks</span></span>  
 <span data-ttu-id="f080d-111">Öğe sol tarafındaki `/=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="f080d-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f080d-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="f080d-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="f080d-113">`/=` İşleci ilk böler değişkeni veya (sol taraftaki işlecinin) özellik değerini (sağ taraftaki işlecinin) ifadesinin değerini tarafından.</span><span class="sxs-lookup"><span data-stu-id="f080d-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="f080d-114">İşleci kayan nokta işlemin sonucu olarak, değişken veya özellik sonra atar.</span><span class="sxs-lookup"><span data-stu-id="f080d-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="f080d-115">Bu ifade atar bir `Double` değişken ya da sol taraftaki özelliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="f080d-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="f080d-116">Varsa `Option Strict` olan `On`, `variableorproperty` olmalıdır bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="f080d-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="f080d-117">Varsa `Option Strict` olan `Off`, Visual Basic örtük bir dönüştürme gerçekleştirir ve çıkan değeri atar `variableorproperty`, çalışma zamanında olası hata.</span><span class="sxs-lookup"><span data-stu-id="f080d-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="f080d-118">Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f080d-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f080d-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="f080d-119">Overloading</span></span>  
 <span data-ttu-id="f080d-120">[/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f080d-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f080d-121">Aşırı yükleme `/` işleci davranışını etkileyen `/=` işleci.</span><span class="sxs-lookup"><span data-stu-id="f080d-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="f080d-122">Kodunuzu kullanıyorsa `/=` bir sınıf veya overloads yapısı `/`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f080d-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f080d-123">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f080d-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f080d-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f080d-124">Example</span></span>  
 <span data-ttu-id="f080d-125">Aşağıdaki örnek kullanır `/=` bir bölme işleci `Integer` değişken ikinci ve sayının ilk değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="f080d-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f080d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f080d-126">See Also</span></span>  
 [<span data-ttu-id="f080d-127">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f080d-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="f080d-128">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="f080d-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="f080d-129">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f080d-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="f080d-130">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="f080d-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="f080d-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="f080d-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="f080d-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="f080d-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="f080d-133">Deyimler</span><span class="sxs-lookup"><span data-stu-id="f080d-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
