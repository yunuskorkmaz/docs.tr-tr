---
title: '\= İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: bcfc59efda0627f83713fe9ada24cedc20d823e3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776255"
---
# <a name="-operator"></a><span data-ttu-id="20ea8-102">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="20ea8-102">\\= Operator</span></span>
<span data-ttu-id="20ea8-103">Bir değişken veya özellik değeri tarafından bir ifadenin değerine böler ve tamsayı sonuç değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="20ea8-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ea8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20ea8-104">Syntax</span></span>  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="20ea8-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="20ea8-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="20ea8-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="20ea8-106">Required.</span></span> <span data-ttu-id="20ea8-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="20ea8-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="20ea8-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="20ea8-108">Required.</span></span> <span data-ttu-id="20ea8-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="20ea8-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20ea8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20ea8-110">Remarks</span></span>  
 <span data-ttu-id="20ea8-111">Öğe sol tarafındaki `\=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="20ea8-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="20ea8-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="20ea8-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="20ea8-113">`\=` İşleci değere bir değişken veya özellik, sol taraftaki değer sağındakiyle böler ve tamsayı sonuç değişken veya özellik, sol taraftaki atar</span><span class="sxs-lookup"><span data-stu-id="20ea8-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="20ea8-114">Tamsayı bölme hakkında daha fazla bilgi için bkz: [\ işleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="20ea8-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="20ea8-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="20ea8-115">Overloading</span></span>  
 <span data-ttu-id="20ea8-116">`\` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="20ea8-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="20ea8-117">Aşırı yükleme `\` işleci davranışını etkileyen `\=` işleci.</span><span class="sxs-lookup"><span data-stu-id="20ea8-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="20ea8-118">Kodunuzu kullanıyorsa `\=` bir sınıf veya aşırı yapısı `\`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="20ea8-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="20ea8-119">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="20ea8-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20ea8-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="20ea8-120">Example</span></span>  
 <span data-ttu-id="20ea8-121">Aşağıdaki örnekte `\=` bir bölme işleci `Integer` değişkenini, saniye ve tamsayı sonuç ilk değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="20ea8-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="20ea8-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20ea8-122">See Also</span></span>  
 [<span data-ttu-id="20ea8-123">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20ea8-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="20ea8-124">/ = İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20ea8-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="20ea8-125">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="20ea8-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="20ea8-126">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="20ea8-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="20ea8-127">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="20ea8-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="20ea8-128">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="20ea8-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="20ea8-129">Deyimler</span><span class="sxs-lookup"><span data-stu-id="20ea8-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
