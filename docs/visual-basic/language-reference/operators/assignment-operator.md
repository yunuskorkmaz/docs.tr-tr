---
title: "= İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230005640b2b494e5413b14ba13a7cb82ee9f22b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="34e5b-102">= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34e5b-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="34e5b-103">Bir değişkenin veya özelliğin değeri atar.</span><span class="sxs-lookup"><span data-stu-id="34e5b-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34e5b-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="34e5b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="34e5b-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="34e5b-106">Herhangi bir yazılabilir değişken veya herhangi bir özellik.</span><span class="sxs-lookup"><span data-stu-id="34e5b-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="34e5b-107">Herhangi değişmez değeri, sabit değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="34e5b-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34e5b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34e5b-108">Remarks</span></span>  
 <span data-ttu-id="34e5b-109">Eşittir işaretinden sol tarafındaki öğesi (`=`) basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="34e5b-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="34e5b-110">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="34e5b-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="34e5b-111">`=` İşleci değişken, sağdaki değeri veya özelliği, sol taraftaki atar.</span><span class="sxs-lookup"><span data-stu-id="34e5b-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34e5b-112">`=` İşleci bir karşılaştırma işleci da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34e5b-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="34e5b-113">Ayrıntılar için bkz [Karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="34e5b-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="34e5b-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="34e5b-114">Overloading</span></span>  
 <span data-ttu-id="34e5b-115">`=` Yalnızca bir ilişkisel karşılaştırma işleci olarak değil olarak atama işleci işleci aşırı yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="34e5b-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="34e5b-116">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="34e5b-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34e5b-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="34e5b-117">Example</span></span>  
 <span data-ttu-id="34e5b-118">Aşağıdaki örnek, atama işleci gösterir.</span><span class="sxs-lookup"><span data-stu-id="34e5b-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="34e5b-119">Sağdaki değeri, sol taraftaki değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="34e5b-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="34e5b-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34e5b-120">See Also</span></span>  
 [<span data-ttu-id="34e5b-121">& = işleci</span><span class="sxs-lookup"><span data-stu-id="34e5b-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="34e5b-122">* = İşleci</span><span class="sxs-lookup"><span data-stu-id="34e5b-122">*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [<span data-ttu-id="34e5b-123">+= İşleci</span><span class="sxs-lookup"><span data-stu-id="34e5b-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [<span data-ttu-id="34e5b-124">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34e5b-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [<span data-ttu-id="34e5b-125">/ = İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34e5b-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="34e5b-126">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="34e5b-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="34e5b-127">^ = İşleci</span><span class="sxs-lookup"><span data-stu-id="34e5b-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [<span data-ttu-id="34e5b-128">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="34e5b-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="34e5b-129">Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="34e5b-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="34e5b-130">Salt okunur</span><span class="sxs-lookup"><span data-stu-id="34e5b-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="34e5b-131">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="34e5b-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
