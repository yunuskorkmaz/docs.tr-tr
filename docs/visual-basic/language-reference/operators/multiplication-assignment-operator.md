---
title: '*= İşleci'
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
ms.openlocfilehash: 4b60fa44a92bff683e13f850da025d7fe753618d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349781"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f0215-102">\*= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0215-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="f0215-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="f0215-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0215-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0215-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f0215-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f0215-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="f0215-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f0215-106">Required.</span></span> <span data-ttu-id="f0215-107">Any numeric variable or property.</span><span class="sxs-lookup"><span data-stu-id="f0215-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="f0215-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f0215-108">Required.</span></span> <span data-ttu-id="f0215-109">Any numeric expression.</span><span class="sxs-lookup"><span data-stu-id="f0215-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0215-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0215-110">Remarks</span></span>  
 <span data-ttu-id="f0215-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="f0215-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f0215-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="f0215-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="f0215-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span><span class="sxs-lookup"><span data-stu-id="f0215-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="f0215-114">The operator then assigns the result of that operation to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="f0215-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f0215-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="f0215-115">Overloading</span></span>  
 <span data-ttu-id="f0215-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="f0215-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f0215-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span><span class="sxs-lookup"><span data-stu-id="f0215-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="f0215-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="f0215-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f0215-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f0215-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0215-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0215-120">Example</span></span>  
 <span data-ttu-id="f0215-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span><span class="sxs-lookup"><span data-stu-id="f0215-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f0215-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0215-122">See also</span></span>

- [<span data-ttu-id="f0215-123">\* İşleci</span><span class="sxs-lookup"><span data-stu-id="f0215-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="f0215-124">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f0215-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="f0215-125">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="f0215-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="f0215-126">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0215-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f0215-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="f0215-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f0215-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="f0215-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
