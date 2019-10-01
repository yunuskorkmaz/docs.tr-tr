---
title: '\= Işleci (Visual Basic)'
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
ms.openlocfilehash: d7b4a6946cc38984272a6b63e14e8c1db2825a5e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700674"
---
# <a name="-operator"></a><span data-ttu-id="090f7-102">\\ = Işleci</span><span class="sxs-lookup"><span data-stu-id="090f7-102">\\= Operator</span></span>
<span data-ttu-id="090f7-103">Bir değişkenin veya özelliğin değerini bir ifadenin değerine böler ve tamsayı sonucunu değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="090f7-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090f7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="090f7-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="090f7-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="090f7-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="090f7-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="090f7-106">Required.</span></span> <span data-ttu-id="090f7-107">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="090f7-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="090f7-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="090f7-108">Required.</span></span> <span data-ttu-id="090f7-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="090f7-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="090f7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="090f7-110">Remarks</span></span>  
 <span data-ttu-id="090f7-111">@No__t-0 işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="090f7-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="090f7-112">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="090f7-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="090f7-113">@No__t-0 işleci, bir değişkenin veya özelliğin değerini solundaki değer ile sola böler ve tamsayı sonucunu sol tarafındaki değişkene veya özelliğe atar</span><span class="sxs-lookup"><span data-stu-id="090f7-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="090f7-114">Tamsayı bölme hakkında daha fazla bilgi için bkz. [\ işleç (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="090f7-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="090f7-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="090f7-115">Overloading</span></span>  
 <span data-ttu-id="090f7-116">@No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="090f7-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="090f7-117">@No__t aşırı yükleme-0 işleci `\=` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="090f7-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="090f7-118">Kodunuz, `\` ' i aşırı yükleyen bir sınıf veya yapıda `\=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="090f7-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="090f7-119">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="090f7-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="090f7-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="090f7-120">Example</span></span>  
 <span data-ttu-id="090f7-121">Aşağıdaki örnek, bir `Integer` değişkenini ikinci bir kez bölmek için `\=` işlecini kullanır ve tamsayı sonucunu ilk değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="090f7-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="090f7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="090f7-122">See also</span></span>

- [<span data-ttu-id="090f7-123">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="090f7-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="090f7-124">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="090f7-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="090f7-125">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="090f7-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="090f7-126">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="090f7-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="090f7-127">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="090f7-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="090f7-128">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="090f7-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="090f7-129">Deyimler</span><span class="sxs-lookup"><span data-stu-id="090f7-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
