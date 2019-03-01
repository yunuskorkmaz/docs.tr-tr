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
ms.openlocfilehash: d672ac147a4d7b2c21f4fcb7ee6cdf91b8b4924b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965338"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="795ec-102">\*= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="795ec-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="795ec-103">Bir ifadenin değerine göre bir değişken veya özellik değerini çarpar ve sonucu değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="795ec-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="795ec-104">Syntax</span></span>  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="795ec-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="795ec-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="795ec-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="795ec-106">Required.</span></span> <span data-ttu-id="795ec-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="795ec-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="795ec-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="795ec-108">Required.</span></span> <span data-ttu-id="795ec-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="795ec-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="795ec-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="795ec-110">Remarks</span></span>  
 <span data-ttu-id="795ec-111">Öğe sol tarafındaki `*=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="795ec-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="795ec-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="795ec-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="795ec-113">`*=` İşleci ilk çarpar (işlecin sağ tarafındaki) ifadenin değerini değişkenin veya özellikte (işlecinin sol tarafı) değeri.</span><span class="sxs-lookup"><span data-stu-id="795ec-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="795ec-114">İşleci, bu işlemin sonucunu daha sonra değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="795ec-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="795ec-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="795ec-115">Overloading</span></span>  
 <span data-ttu-id="795ec-116">[\* İşleci](../../../visual-basic/language-reference/operators/multiplication-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="795ec-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="795ec-117">Aşırı yükleme `*` işleci davranışını etkileyen `*=` işleci.</span><span class="sxs-lookup"><span data-stu-id="795ec-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="795ec-118">Kodunuzu kullanıyorsa `*=` bir sınıf veya aşırı yapısı `*`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="795ec-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="795ec-119">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="795ec-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="795ec-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="795ec-120">Example</span></span>  
 <span data-ttu-id="795ec-121">Aşağıdaki örnekte `*=` işleci bir çarpılacak `Integer` değişkenini, saniye ve sonuç ilk değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="795ec-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="795ec-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="795ec-122">See also</span></span>
- [<span data-ttu-id="795ec-123">\* İşleci</span><span class="sxs-lookup"><span data-stu-id="795ec-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="795ec-124">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="795ec-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="795ec-125">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="795ec-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="795ec-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="795ec-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="795ec-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="795ec-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="795ec-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="795ec-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
