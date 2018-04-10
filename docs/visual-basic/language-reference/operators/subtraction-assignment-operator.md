---
title: -= İşleci (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 753e3efca311da9e09c67131969626ff59c130f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="320c6-102">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="320c6-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="320c6-103">Değerinden ifade bir değişken veya özellik değeri çıkarır ve değişken ya da özelliği için sonuç atar.</span><span class="sxs-lookup"><span data-stu-id="320c6-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="320c6-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="320c6-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="320c6-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="320c6-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="320c6-106">Required.</span></span> <span data-ttu-id="320c6-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="320c6-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="320c6-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="320c6-108">Required.</span></span> <span data-ttu-id="320c6-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="320c6-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="320c6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="320c6-110">Remarks</span></span>  
 <span data-ttu-id="320c6-111">Öğe sol tarafındaki `-=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="320c6-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="320c6-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="320c6-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="320c6-113">`-=` İşleci ilk çıkarır (sağ taraftaki işlecinin) ifadesinin değerini değerinden değişkenin ya da özelliği (sol taraftaki işlecinin).</span><span class="sxs-lookup"><span data-stu-id="320c6-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="320c6-114">İşleci değişken veya özelliği daha sonra işlemin sonucunu atar.</span><span class="sxs-lookup"><span data-stu-id="320c6-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="320c6-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="320c6-115">Overloading</span></span>  
 <span data-ttu-id="320c6-116">[-İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="320c6-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="320c6-117">Aşırı yükleme `-` işleci davranışını etkileyen `-=` işleci.</span><span class="sxs-lookup"><span data-stu-id="320c6-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="320c6-118">Kodunuzu kullanıyorsa `-=` bir sınıf veya overloads yapısı `-`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="320c6-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="320c6-119">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="320c6-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="320c6-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="320c6-120">Example</span></span>  
 <span data-ttu-id="320c6-121">Aşağıdaki örnek kullanır `-=` bir çıkartılacak işleci `Integer` başka bir değişken ve ata ikinci değişken sonucu.</span><span class="sxs-lookup"><span data-stu-id="320c6-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="320c6-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="320c6-122">See Also</span></span>  
 [<span data-ttu-id="320c6-123">-İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="320c6-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)  
 [<span data-ttu-id="320c6-124">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="320c6-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="320c6-125">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="320c6-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="320c6-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="320c6-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="320c6-127">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="320c6-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="320c6-128">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="320c6-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
