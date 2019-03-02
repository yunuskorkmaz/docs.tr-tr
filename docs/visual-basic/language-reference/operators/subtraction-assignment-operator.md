---
title: -= İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: c3495c4e45fe5e1d497578ee3ee6afe874e90eed
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203051"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="63fd2-102">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63fd2-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="63fd2-103">Değerin bir ifade bir değişken veya özellik değerini çıkarır ve sonucu değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="63fd2-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63fd2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63fd2-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="63fd2-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="63fd2-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="63fd2-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63fd2-106">Required.</span></span> <span data-ttu-id="63fd2-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="63fd2-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="63fd2-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63fd2-108">Required.</span></span> <span data-ttu-id="63fd2-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="63fd2-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63fd2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63fd2-110">Remarks</span></span>  
 <span data-ttu-id="63fd2-111">Öğe sol tarafındaki `-=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="63fd2-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="63fd2-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="63fd2-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="63fd2-113">`-=` İşleci ilk çıkarır (işlecin sağ tarafındaki) ifade değeri değişken veya özellik (üzerinde işlecinin sol tarafı) değerinden.</span><span class="sxs-lookup"><span data-stu-id="63fd2-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="63fd2-114">İşleci, bu işlemin sonucunu daha sonra değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="63fd2-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="63fd2-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="63fd2-115">Overloading</span></span>  
 <span data-ttu-id="63fd2-116">[-İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="63fd2-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="63fd2-117">Aşırı yükleme `-` işleci davranışını etkileyen `-=` işleci.</span><span class="sxs-lookup"><span data-stu-id="63fd2-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="63fd2-118">Kodunuzu kullanıyorsa `-=` bir sınıf veya aşırı yapısı `-`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="63fd2-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="63fd2-119">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="63fd2-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63fd2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="63fd2-120">Example</span></span>  
 <span data-ttu-id="63fd2-121">Aşağıdaki örnekte `-=` biri çıkarılacak işleci `Integer` başka bir değişken ve sonucu ikinci değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="63fd2-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="63fd2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63fd2-122">See also</span></span>
- [<span data-ttu-id="63fd2-123">-İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63fd2-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="63fd2-124">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="63fd2-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="63fd2-125">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="63fd2-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="63fd2-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="63fd2-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="63fd2-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="63fd2-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="63fd2-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="63fd2-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
