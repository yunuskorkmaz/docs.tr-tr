---
title: '&amp;= İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: dee30096f244adc34b83fdfdc6af0baabd372b4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672415"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="be832-102">&amp;= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be832-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="be832-103">Birleştiren bir `String` ifade bir `String` değişken veya özellik ve sonucu değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="be832-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be832-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be832-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="be832-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="be832-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="be832-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="be832-106">Required.</span></span> <span data-ttu-id="be832-107">Tüm `String` değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="be832-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="be832-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="be832-108">Required.</span></span> <span data-ttu-id="be832-109">Tüm `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="be832-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be832-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be832-110">Remarks</span></span>  
 <span data-ttu-id="be832-111">Öğe sol tarafındaki `&=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="be832-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="be832-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="be832-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="be832-113">`&=` İşleci art arda ekler `String` sağındakiyle için ifade `String` değişken veya özellik, sol taraftaki ve sonucu bir değişken veya özellik, sol taraftaki atar.</span><span class="sxs-lookup"><span data-stu-id="be832-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="be832-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="be832-114">Overloading</span></span>  
 <span data-ttu-id="be832-115">[& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="be832-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="be832-116">Aşırı yükleme `&` işleci davranışını etkileyen `&=` işleci.</span><span class="sxs-lookup"><span data-stu-id="be832-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="be832-117">Kodunuzu kullanıyorsa `&=` bir sınıf veya aşırı yapısı `&`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="be832-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="be832-118">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="be832-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be832-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="be832-119">Example</span></span>  
 <span data-ttu-id="be832-120">Aşağıdaki örnekte `&=` işleci iki birleştirmek için `String` değişkenleri ve sonuç ilk değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="be832-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="be832-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be832-121">See also</span></span>
- [<span data-ttu-id="be832-122">& İşleci</span><span class="sxs-lookup"><span data-stu-id="be832-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="be832-123">+= İşleci</span><span class="sxs-lookup"><span data-stu-id="be832-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="be832-124">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="be832-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="be832-125">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="be832-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="be832-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="be832-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="be832-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="be832-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="be832-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="be832-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
