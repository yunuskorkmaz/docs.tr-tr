---
title: = İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 75f303219b9bf32613989f65f90a9096ef70e02e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350198"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f9aca-102">= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9aca-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="f9aca-103">Bir değişkene veya özelliğe bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="f9aca-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9aca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9aca-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="f9aca-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f9aca-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="f9aca-106">Herhangi bir yazılabilir değişken veya herhangi bir özellik.</span><span class="sxs-lookup"><span data-stu-id="f9aca-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="f9aca-107">Herhangi bir sabit değer, sabit veya ifade.</span><span class="sxs-lookup"><span data-stu-id="f9aca-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9aca-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9aca-108">Remarks</span></span>  
 <span data-ttu-id="f9aca-109">Eşittir işaretinin (`=`) sol tarafındaki öğesi basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9aca-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f9aca-110">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="f9aca-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="f9aca-111">`=` işleci, solundaki değeri, sol tarafındaki değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="f9aca-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9aca-112">`=` işleci bir karşılaştırma işleci olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9aca-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="f9aca-113">Ayrıntılar için bkz. [karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="f9aca-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f9aca-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="f9aca-114">Overloading</span></span>  
 <span data-ttu-id="f9aca-115">`=` işleci, atama işleci olarak değil yalnızca ilişkisel karşılaştırma işleci olarak aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f9aca-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="f9aca-116">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f9aca-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9aca-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9aca-117">Example</span></span>  
 <span data-ttu-id="f9aca-118">Aşağıdaki örnek, atama işlecini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9aca-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="f9aca-119">Sağdaki değer soldaki değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="f9aca-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="f9aca-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9aca-120">See also</span></span>

- [<span data-ttu-id="f9aca-121">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="f9aca-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="f9aca-122">\*= İşleci</span><span class="sxs-lookup"><span data-stu-id="f9aca-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="f9aca-123">+= İşleci</span><span class="sxs-lookup"><span data-stu-id="f9aca-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="f9aca-124">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9aca-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="f9aca-125">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9aca-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="f9aca-126">\\= Işleci</span><span class="sxs-lookup"><span data-stu-id="f9aca-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="f9aca-127">^= İşleci</span><span class="sxs-lookup"><span data-stu-id="f9aca-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="f9aca-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="f9aca-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="f9aca-129">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f9aca-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="f9aca-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="f9aca-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="f9aca-131">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="f9aca-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
