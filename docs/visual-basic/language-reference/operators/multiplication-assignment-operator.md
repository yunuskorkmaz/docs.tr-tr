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
ms.openlocfilehash: 7c009a6b3acfe1528a2c34ed1e10735ac86507e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839320"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9a35f-102">\*= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a35f-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="9a35f-103">Bir ifadenin değerine göre bir değişken veya özellik değerini çarpar ve sonucu değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="9a35f-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a35f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a35f-104">Syntax</span></span>  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9a35f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9a35f-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="9a35f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9a35f-106">Required.</span></span> <span data-ttu-id="9a35f-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="9a35f-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="9a35f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9a35f-108">Required.</span></span> <span data-ttu-id="9a35f-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9a35f-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a35f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a35f-110">Remarks</span></span>  
 <span data-ttu-id="9a35f-111">Öğe sol tarafındaki `*=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a35f-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="9a35f-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9a35f-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="9a35f-113">`*=` İşleci ilk çarpar (işlecin sağ tarafındaki) ifadenin değerini değişkenin veya özellikte (işlecinin sol tarafı) değeri.</span><span class="sxs-lookup"><span data-stu-id="9a35f-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="9a35f-114">İşleci, bu işlemin sonucunu daha sonra değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="9a35f-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9a35f-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="9a35f-115">Overloading</span></span>  
 <span data-ttu-id="9a35f-116">[\* İşleci](../../../visual-basic/language-reference/operators/multiplication-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9a35f-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9a35f-117">Aşırı yükleme `*` işleci davranışını etkileyen `*=` işleci.</span><span class="sxs-lookup"><span data-stu-id="9a35f-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="9a35f-118">Kodunuzu kullanıyorsa `*=` bir sınıf veya aşırı yapısı `*`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9a35f-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9a35f-119">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9a35f-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a35f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a35f-120">Example</span></span>  
 <span data-ttu-id="9a35f-121">Aşağıdaki örnekte `*=` işleci bir çarpılacak `Integer` değişkenini, saniye ve sonuç ilk değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="9a35f-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="9a35f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a35f-122">See also</span></span>

- [<span data-ttu-id="9a35f-123">\* İşleci</span><span class="sxs-lookup"><span data-stu-id="9a35f-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="9a35f-124">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9a35f-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="9a35f-125">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="9a35f-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="9a35f-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="9a35f-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9a35f-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="9a35f-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9a35f-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="9a35f-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
