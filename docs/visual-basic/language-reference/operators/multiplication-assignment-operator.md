---
title: '*= İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 47d3239af6ff24501e6babc23c0db4103c477796
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701062"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="35afe-102">\*= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35afe-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="35afe-103">Bir değişkenin veya özelliğin değerini bir ifadenin değeri ile çarpar ve sonucu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="35afe-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35afe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35afe-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="35afe-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="35afe-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="35afe-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="35afe-106">Required.</span></span> <span data-ttu-id="35afe-107">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="35afe-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="35afe-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="35afe-108">Required.</span></span> <span data-ttu-id="35afe-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="35afe-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35afe-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35afe-110">Remarks</span></span>  
 <span data-ttu-id="35afe-111">@No__t-0 işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="35afe-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="35afe-112">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="35afe-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="35afe-113">@No__t-0 işleci ilk olarak, ifadenin değerini (işlecin sağ tarafında) değişkenin veya özelliğin değerine (işlecin sol tarafında) çarpar.</span><span class="sxs-lookup"><span data-stu-id="35afe-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="35afe-114">İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="35afe-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="35afe-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="35afe-115">Overloading</span></span>  
 <span data-ttu-id="35afe-116">[\* İşleci](../../../visual-basic/language-reference/operators/multiplication-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="35afe-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="35afe-117">@No__t aşırı yükleme-0 işleci `*=` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="35afe-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="35afe-118">Kodunuz, `*` ' i aşırı yükleyen bir sınıf veya yapıda `*=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="35afe-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="35afe-119">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="35afe-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35afe-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="35afe-120">Example</span></span>  
 <span data-ttu-id="35afe-121">Aşağıdaki örnek, bir `Integer` değişkenini ikinci olarak çarpmak ve sonucu ilk değişkene atamak için `*=` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="35afe-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="35afe-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35afe-122">See also</span></span>

- [<span data-ttu-id="35afe-123">\* İşleci</span><span class="sxs-lookup"><span data-stu-id="35afe-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="35afe-124">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="35afe-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="35afe-125">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="35afe-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="35afe-126">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="35afe-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="35afe-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="35afe-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="35afe-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="35afe-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
