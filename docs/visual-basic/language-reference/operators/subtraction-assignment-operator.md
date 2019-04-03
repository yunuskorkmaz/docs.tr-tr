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
ms.openlocfilehash: be1ff4f10f6b30d8448d2441ee3ad2c1e2f80e2d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815907"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="144e1-102">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="144e1-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="144e1-103">Değerin bir ifade bir değişken veya özellik değerini çıkarır ve sonucu değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="144e1-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="144e1-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="144e1-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="144e1-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="144e1-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="144e1-106">Required.</span></span> <span data-ttu-id="144e1-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="144e1-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="144e1-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="144e1-108">Required.</span></span> <span data-ttu-id="144e1-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="144e1-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="144e1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="144e1-110">Remarks</span></span>  
 <span data-ttu-id="144e1-111">Öğe sol tarafındaki `-=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="144e1-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="144e1-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="144e1-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="144e1-113">`-=` İşleci ilk çıkarır (işlecin sağ tarafındaki) ifade değeri değişken veya özellik (üzerinde işlecinin sol tarafı) değerinden.</span><span class="sxs-lookup"><span data-stu-id="144e1-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="144e1-114">İşleci, bu işlemin sonucunu daha sonra değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="144e1-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="144e1-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="144e1-115">Overloading</span></span>  
 <span data-ttu-id="144e1-116">[-İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="144e1-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="144e1-117">Aşırı yükleme `-` işleci davranışını etkileyen `-=` işleci.</span><span class="sxs-lookup"><span data-stu-id="144e1-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="144e1-118">Kodunuzu kullanıyorsa `-=` bir sınıf veya aşırı yapısı `-`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="144e1-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="144e1-119">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="144e1-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="144e1-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="144e1-120">Example</span></span>  
 <span data-ttu-id="144e1-121">Aşağıdaki örnekte `-=` biri çıkarılacak işleci `Integer` başka bir değişken ve sonucu ikinci değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="144e1-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="144e1-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="144e1-122">See also</span></span>

- [<span data-ttu-id="144e1-123">-İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="144e1-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="144e1-124">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="144e1-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="144e1-125">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="144e1-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="144e1-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="144e1-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="144e1-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="144e1-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="144e1-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="144e1-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
