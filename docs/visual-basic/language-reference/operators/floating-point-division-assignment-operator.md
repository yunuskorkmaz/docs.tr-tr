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
ms.openlocfilehash: d9d3fa021654d3be1b9d304beb83caa737660264
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813996"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="54aa2-102">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54aa2-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="54aa2-103">Bir değişken veya özellik değeri tarafından bir ifadenin değerine böler ve kayan noktalı bir sonuç değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="54aa2-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54aa2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54aa2-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="54aa2-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="54aa2-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="54aa2-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="54aa2-106">Required.</span></span> <span data-ttu-id="54aa2-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="54aa2-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="54aa2-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="54aa2-108">Required.</span></span> <span data-ttu-id="54aa2-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="54aa2-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54aa2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54aa2-110">Remarks</span></span>  
 <span data-ttu-id="54aa2-111">Öğe sol tarafındaki `/=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="54aa2-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="54aa2-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="54aa2-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="54aa2-113">`/=` İşleci ilk ayırır değişken veya özellikte (işlecinin sol tarafı) değerini (işlecin sağ tarafındaki) ifadesinin değere göre.</span><span class="sxs-lookup"><span data-stu-id="54aa2-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="54aa2-114">İşleci, kayan nokta, işlemin sonucunu daha sonra değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="54aa2-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="54aa2-115">Bu bildirimi atar bir `Double` değişken ya da sol taraftaki özelliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="54aa2-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="54aa2-116">Varsa `Option Strict` olduğu `On`, `variableorproperty` olmalıdır bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="54aa2-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="54aa2-117">Varsa `Option Strict` olduğu `Off`, Visual Basic örtülü bir dönüştürme uygulayan ve çıkan değeri atar `variableorproperty`, çalışma zamanında olası bir hata ile.</span><span class="sxs-lookup"><span data-stu-id="54aa2-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="54aa2-118">Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="54aa2-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="54aa2-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="54aa2-119">Overloading</span></span>  
 <span data-ttu-id="54aa2-120">[/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="54aa2-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="54aa2-121">Aşırı yükleme `/` işleci davranışını etkileyen `/=` işleci.</span><span class="sxs-lookup"><span data-stu-id="54aa2-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="54aa2-122">Kodunuzu kullanıyorsa `/=` bir sınıf veya aşırı yapısı `/`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="54aa2-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="54aa2-123">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="54aa2-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54aa2-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="54aa2-124">Example</span></span>  
 <span data-ttu-id="54aa2-125">Aşağıdaki örnekte `/=` bir bölme işleci `Integer` değişkenini, saniye ve sayının ilk değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="54aa2-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="54aa2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54aa2-126">See also</span></span>

- [<span data-ttu-id="54aa2-127">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54aa2-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="54aa2-128">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="54aa2-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="54aa2-129">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="54aa2-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="54aa2-130">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="54aa2-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="54aa2-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="54aa2-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="54aa2-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="54aa2-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="54aa2-133">Deyimler</span><span class="sxs-lookup"><span data-stu-id="54aa2-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
