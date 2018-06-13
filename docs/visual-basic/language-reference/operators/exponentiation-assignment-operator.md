---
title: ^= İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 571ef26eb188d9044ec8f6c8e6e4b490780f17a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603502"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="7d274-102">^= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d274-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="7d274-103">Bir değişken ya da ifade gücüne özellik değerini başlatır ve değişken veya özelliği için sonuç atar.</span><span class="sxs-lookup"><span data-stu-id="7d274-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d274-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d274-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="7d274-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7d274-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="7d274-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7d274-106">Required.</span></span> <span data-ttu-id="7d274-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="7d274-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="7d274-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7d274-108">Required.</span></span> <span data-ttu-id="7d274-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="7d274-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d274-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d274-110">Remarks</span></span>  
 <span data-ttu-id="7d274-111">Öğe sol tarafındaki `^=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d274-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="7d274-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="7d274-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="7d274-113">`^=` İşleci ilk başlatır değişken veya özellik (sol taraftaki işlecinin) değeri (sağ taraftaki işlecinin) ifadesinin değerini güç için.</span><span class="sxs-lookup"><span data-stu-id="7d274-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="7d274-114">İşleci, daha sonra değişken veya özellik için bu işlemin sonucu olarak atar.</span><span class="sxs-lookup"><span data-stu-id="7d274-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="7d274-115">Visual Basic her zaman içinde üs gerçekleştirir [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="7d274-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="7d274-116">Tüm farklı türündeki işlenenler için dönüştürülür `Double`, ve sonucu her zaman `Double`.</span><span class="sxs-lookup"><span data-stu-id="7d274-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="7d274-117">Değeri `expression` kesir olabilir negatif veya her ikisi de.</span><span class="sxs-lookup"><span data-stu-id="7d274-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="7d274-118">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="7d274-118">Overloading</span></span>  
 <span data-ttu-id="7d274-119">[^ İşleci](../../../visual-basic/language-reference/operators/exponentiation-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7d274-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7d274-120">Aşırı yükleme `^` işleci davranışını etkileyen `^=` işleci.</span><span class="sxs-lookup"><span data-stu-id="7d274-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="7d274-121">Kodunuzu kullanıyorsa `^=` bir sınıf veya overloads yapısı `^`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7d274-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7d274-122">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7d274-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d274-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d274-123">Example</span></span>  
 <span data-ttu-id="7d274-124">Aşağıdaki örnek kullanır `^=` bir değeri yükseltmek için işleci `Integer` ikinci bir değişken ve ata ilk değişkenin sonucu gücünü değişken.</span><span class="sxs-lookup"><span data-stu-id="7d274-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7d274-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d274-125">See Also</span></span>  
 [<span data-ttu-id="7d274-126">^ İşleci</span><span class="sxs-lookup"><span data-stu-id="7d274-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [<span data-ttu-id="7d274-127">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="7d274-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="7d274-128">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="7d274-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="7d274-129">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="7d274-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="7d274-130">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="7d274-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="7d274-131">Deyimler</span><span class="sxs-lookup"><span data-stu-id="7d274-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
