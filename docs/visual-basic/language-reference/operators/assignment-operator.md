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
ms.openlocfilehash: d260dffb7175e9dddcbf9acb75415f5f973727e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962011"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="5c26c-102">= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c26c-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="5c26c-103">Bir değişkene veya özelliğe bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="5c26c-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c26c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c26c-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="5c26c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5c26c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="5c26c-106">Herhangi bir yazılabilir değişken veya herhangi bir özellik.</span><span class="sxs-lookup"><span data-stu-id="5c26c-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="5c26c-107">Herhangi bir sabit değer, sabit veya ifade.</span><span class="sxs-lookup"><span data-stu-id="5c26c-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c26c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c26c-108">Remarks</span></span>  
 <span data-ttu-id="5c26c-109">Eşittir işaretinin (`=`) sol tarafındaki öğesi basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c26c-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="5c26c-110">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="5c26c-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="5c26c-111">`=` İşleci değeri, sol tarafında bulunan değişkene veya özelliğe doğru değerini atar.</span><span class="sxs-lookup"><span data-stu-id="5c26c-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c26c-112">`=` İşleci bir karşılaştırma işleci olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c26c-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="5c26c-113">Ayrıntılar için bkz. [karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5c26c-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5c26c-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="5c26c-114">Overloading</span></span>  
 <span data-ttu-id="5c26c-115">`=` İşleci, atama işleci olarak değil yalnızca ilişkisel karşılaştırma işleci olarak aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="5c26c-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="5c26c-116">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5c26c-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c26c-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c26c-117">Example</span></span>  
 <span data-ttu-id="5c26c-118">Aşağıdaki örnek, atama işlecini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c26c-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="5c26c-119">Sağdaki değer soldaki değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="5c26c-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="5c26c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c26c-120">See also</span></span>

- [<span data-ttu-id="5c26c-121">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="5c26c-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="5c26c-122">\*= İşleci</span><span class="sxs-lookup"><span data-stu-id="5c26c-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="5c26c-123">+= İşleci</span><span class="sxs-lookup"><span data-stu-id="5c26c-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="5c26c-124">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c26c-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="5c26c-125">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c26c-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="5c26c-126">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="5c26c-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="5c26c-127">^= İşleci</span><span class="sxs-lookup"><span data-stu-id="5c26c-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="5c26c-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="5c26c-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="5c26c-129">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="5c26c-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="5c26c-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="5c26c-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="5c26c-131">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="5c26c-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
