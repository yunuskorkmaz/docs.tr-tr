---
title: = İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 5e6d34802f5f82373d0e8176f3b732a327c55d01
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965000"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="d2517-102">= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2517-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="d2517-103">Bir değişken veya özellik için bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="d2517-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2517-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2517-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="d2517-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d2517-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d2517-106">Herhangi bir yazılabilir değişkeni veya herhangi bir özelliği.</span><span class="sxs-lookup"><span data-stu-id="d2517-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="d2517-107">Tüm değişmez değeri, sabit veya ifade.</span><span class="sxs-lookup"><span data-stu-id="d2517-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2517-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2517-108">Remarks</span></span>  
 <span data-ttu-id="d2517-109">Eşittir işaretinin sol tarafındaki öğesi (`=`) basit bir skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2517-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d2517-110">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="d2517-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="d2517-111">`=` İşleci sağındakiyle değişkenine değer veya özelliği, sol taraftaki atar.</span><span class="sxs-lookup"><span data-stu-id="d2517-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2517-112">`=` İşleci bir karşılaştırma işleci da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2517-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="d2517-113">Ayrıntılar için bkz [Karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d2517-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d2517-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="d2517-114">Overloading</span></span>  
 <span data-ttu-id="d2517-115">`=` İlişkisel karşılaştırma işleci olarak yalnızca, bir atama işleci olarak değil işleci aşırı yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2517-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="d2517-116">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d2517-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2517-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2517-117">Example</span></span>  
 <span data-ttu-id="d2517-118">Aşağıdaki örnek, atama işlecini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2517-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="d2517-119">Sağdaki değerin sol değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="d2517-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="d2517-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2517-120">See also</span></span>
- [<span data-ttu-id="d2517-121">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="d2517-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="d2517-122">\*= İşleci</span><span class="sxs-lookup"><span data-stu-id="d2517-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="d2517-123">+= İşleci</span><span class="sxs-lookup"><span data-stu-id="d2517-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="d2517-124">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2517-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="d2517-125">/ = İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2517-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="d2517-126">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="d2517-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="d2517-127">^= İşleci</span><span class="sxs-lookup"><span data-stu-id="d2517-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="d2517-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="d2517-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="d2517-129">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d2517-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="d2517-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="d2517-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="d2517-131">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="d2517-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
