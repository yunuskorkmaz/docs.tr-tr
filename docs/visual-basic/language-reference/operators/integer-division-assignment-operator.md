---
title: "\\=İşleci"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ba74f7a433687b306e8b4273f3a2a6d60583396
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator"></a><span data-ttu-id="cbab9-102">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="cbab9-102">\\= Operator</span></span>
<span data-ttu-id="cbab9-103">Bir değişken ya da özellik değeri bir ifadenin değerini tarafından böler ve tamsayı sonuç değişken ya da özelliğin atar.</span><span class="sxs-lookup"><span data-stu-id="cbab9-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbab9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbab9-104">Syntax</span></span>  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="cbab9-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="cbab9-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="cbab9-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="cbab9-106">Required.</span></span> <span data-ttu-id="cbab9-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="cbab9-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="cbab9-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="cbab9-108">Required.</span></span> <span data-ttu-id="cbab9-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="cbab9-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbab9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbab9-110">Remarks</span></span>  
 <span data-ttu-id="cbab9-111">Öğe sol tarafındaki `\=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="cbab9-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="cbab9-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="cbab9-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="cbab9-113">`\=` İşleci bir değişken ya da kendi soldaki özellik değeri, sağdaki değeriyle böler ve tamsayı sonuç değişkenin veya özelliğin, sol taraftaki atar</span><span class="sxs-lookup"><span data-stu-id="cbab9-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="cbab9-114">Tamsayı bölme hakkında daha fazla bilgi için bkz: [\ işleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="cbab9-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="cbab9-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="cbab9-115">Overloading</span></span>  
 <span data-ttu-id="cbab9-116">`\` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cbab9-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="cbab9-117">Aşırı yükleme `\` işleci davranışını etkileyen `\=` işleci.</span><span class="sxs-lookup"><span data-stu-id="cbab9-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="cbab9-118">Kodunuzu kullanıyorsa `\=` bir sınıf veya overloads yapısı `\`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cbab9-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cbab9-119">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cbab9-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbab9-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="cbab9-120">Example</span></span>  
 <span data-ttu-id="cbab9-121">Aşağıdaki örnek kullanır `\=` bir bölme işleci `Integer` değişken ikinci ve tamsayı sonuç ilk değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="cbab9-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cbab9-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbab9-122">See Also</span></span>  
 [<span data-ttu-id="cbab9-123">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbab9-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="cbab9-124">/ = İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbab9-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="cbab9-125">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="cbab9-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="cbab9-126">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="cbab9-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="cbab9-127">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="cbab9-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="cbab9-128">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="cbab9-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="cbab9-129">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="cbab9-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
