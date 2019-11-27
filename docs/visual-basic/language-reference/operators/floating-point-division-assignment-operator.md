---
title: /= İşleci
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
ms.openlocfilehash: a8a031e968df90496a4e263ae78d47045ccdc923
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331043"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="af196-102">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af196-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="af196-103">Bir değişkenin veya özelliğin değerini bir ifadenin değerine böler ve kayan nokta sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="af196-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af196-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af196-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="af196-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="af196-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="af196-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="af196-106">Required.</span></span> <span data-ttu-id="af196-107">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="af196-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="af196-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="af196-108">Required.</span></span> <span data-ttu-id="af196-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="af196-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af196-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af196-110">Remarks</span></span>  
 <span data-ttu-id="af196-111">`/=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="af196-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="af196-112">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="af196-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="af196-113">`/=` işleci, ilk olarak değişkenin değerini (işlecin sol tarafında), ifadenin değeri (işlecin sağ tarafında) ile ayırır.</span><span class="sxs-lookup"><span data-stu-id="af196-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="af196-114">İşleci daha sonra bu işlemin kayan nokta sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="af196-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="af196-115">Bu ifade, soldaki değişkene veya özelliğe bir `Double` değeri atar.</span><span class="sxs-lookup"><span data-stu-id="af196-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="af196-116">`Option Strict` `On`, `variableorproperty` bir `Double`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af196-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="af196-117">`Option Strict` `Off`, Visual Basic örtük bir dönüştürme gerçekleştirir ve sonuçta elde edilen değeri, çalışma zamanında olası bir hatayla `variableorproperty`atar.</span><span class="sxs-lookup"><span data-stu-id="af196-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="af196-118">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimdir](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="af196-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="af196-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="af196-119">Overloading</span></span>  
 <span data-ttu-id="af196-120">[/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="af196-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="af196-121">`/` işleci aşırı yükleme `/=` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="af196-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="af196-122">Kodunuz, `/`aşırı yükleyen bir sınıf veya yapı üzerinde `/=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="af196-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="af196-123">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="af196-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="af196-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="af196-124">Example</span></span>  
 <span data-ttu-id="af196-125">Aşağıdaki örnek, bir `Integer` değişkenini ikinci bir kez bölmek ve bölümü ilk değişkene atamak için `/=` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="af196-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="af196-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af196-126">See also</span></span>

- [<span data-ttu-id="af196-127">/İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af196-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="af196-128">\\= Işleci</span><span class="sxs-lookup"><span data-stu-id="af196-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="af196-129">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="af196-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="af196-130">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="af196-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="af196-131">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="af196-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="af196-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="af196-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="af196-133">Deyimler</span><span class="sxs-lookup"><span data-stu-id="af196-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
