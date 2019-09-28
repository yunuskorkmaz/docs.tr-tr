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
ms.openlocfilehash: b4855e8270a329f9345339060a323b5ca9cd9792
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592183"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="89fc5-102">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89fc5-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="89fc5-103">Bir değişkenin veya özelliğin değerini bir ifadenin değerine böler ve kayan nokta sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="89fc5-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89fc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89fc5-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="89fc5-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="89fc5-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="89fc5-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="89fc5-106">Required.</span></span> <span data-ttu-id="89fc5-107">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="89fc5-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="89fc5-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="89fc5-108">Required.</span></span> <span data-ttu-id="89fc5-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="89fc5-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89fc5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89fc5-110">Remarks</span></span>  
 <span data-ttu-id="89fc5-111">@No__t-0 işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="89fc5-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="89fc5-112">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="89fc5-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="89fc5-113">@No__t-0 işleci ilk olarak değişkenin değerini (işlecin sol tarafında), ifadenin değeri (işlecin sağ tarafında) ile ayırır (işlecin sağ tarafındaki).</span><span class="sxs-lookup"><span data-stu-id="89fc5-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="89fc5-114">İşleci daha sonra bu işlemin kayan nokta sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="89fc5-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="89fc5-115">Bu ifade, soldaki değişkene veya özelliğe `Double` değeri atar.</span><span class="sxs-lookup"><span data-stu-id="89fc5-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="89fc5-116">@No__t-0 `On` ise, `variableorproperty` `Double` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89fc5-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="89fc5-117">@No__t-0 `Off` ise, Visual Basic örtük bir dönüştürme gerçekleştirir ve elde edilen değeri, çalışma zamanında olası bir hatayla `variableorproperty` ' ye atar.</span><span class="sxs-lookup"><span data-stu-id="89fc5-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="89fc5-118">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimdir](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="89fc5-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="89fc5-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="89fc5-119">Overloading</span></span>  
 <span data-ttu-id="89fc5-120">[/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="89fc5-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="89fc5-121">@No__t aşırı yükleme-0 işleci `/=` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="89fc5-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="89fc5-122">Kodunuz, `/` ' i aşırı yükleyen bir sınıf veya yapıda `/=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="89fc5-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="89fc5-123">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="89fc5-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89fc5-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="89fc5-124">Example</span></span>  
 <span data-ttu-id="89fc5-125">Aşağıdaki örnek, bir `Integer` değişkenini ikinci kez bölmek ve bölümü ilk değişkene atamak için `/=` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="89fc5-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="89fc5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89fc5-126">See also</span></span>

- [<span data-ttu-id="89fc5-127">/İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89fc5-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="89fc5-128">\\ = Işleci</span><span class="sxs-lookup"><span data-stu-id="89fc5-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="89fc5-129">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="89fc5-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="89fc5-130">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="89fc5-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="89fc5-131">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="89fc5-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="89fc5-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="89fc5-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="89fc5-133">Deyimler</span><span class="sxs-lookup"><span data-stu-id="89fc5-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
