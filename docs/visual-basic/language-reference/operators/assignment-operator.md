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
ms.openlocfilehash: ca4c519dd80c07f54dc1c3dfe70daf6948446363
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591834"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ce495-102">= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce495-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="ce495-103">Bir değişkene veya özelliğe bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="ce495-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce495-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce495-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="ce495-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ce495-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="ce495-106">Herhangi bir yazılabilir değişken veya herhangi bir özellik.</span><span class="sxs-lookup"><span data-stu-id="ce495-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="ce495-107">Herhangi bir sabit değer, sabit veya ifade.</span><span class="sxs-lookup"><span data-stu-id="ce495-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce495-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce495-108">Remarks</span></span>  
 <span data-ttu-id="ce495-109">Eşittir işaretinin (`=`) sol tarafındaki öğesi basit bir skaler değişken, özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce495-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ce495-110">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="ce495-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="ce495-111">@No__t-0 işleci, solundaki değeri sağ taraftaki değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="ce495-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce495-112">@No__t-0 işleci bir karşılaştırma işleci olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce495-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="ce495-113">Ayrıntılar için bkz. [karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ce495-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ce495-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="ce495-114">Overloading</span></span>  
 <span data-ttu-id="ce495-115">@No__t-0 işleci, atama işleci olarak değil yalnızca ilişkisel karşılaştırma işleci olarak aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ce495-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="ce495-116">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ce495-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce495-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce495-117">Example</span></span>  
 <span data-ttu-id="ce495-118">Aşağıdaki örnek, atama işlecini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce495-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="ce495-119">Sağdaki değer soldaki değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="ce495-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="ce495-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce495-120">See also</span></span>

- [<span data-ttu-id="ce495-121">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="ce495-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="ce495-122">\*= İşleci</span><span class="sxs-lookup"><span data-stu-id="ce495-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="ce495-123">+= İşleci</span><span class="sxs-lookup"><span data-stu-id="ce495-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="ce495-124">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce495-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="ce495-125">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce495-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="ce495-126">\\ = Işleci</span><span class="sxs-lookup"><span data-stu-id="ce495-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="ce495-127">^= İşleci</span><span class="sxs-lookup"><span data-stu-id="ce495-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="ce495-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="ce495-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="ce495-129">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="ce495-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="ce495-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="ce495-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="ce495-131">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="ce495-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
