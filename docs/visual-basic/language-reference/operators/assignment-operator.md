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
ms.openlocfilehash: 516cb21e02d9fb2cd4b8d72282bb74163e1fb14b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371771"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="528ab-102">= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="528ab-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="528ab-103">Bir değişkene veya özelliğe bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="528ab-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="528ab-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="528ab-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="528ab-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="528ab-106">Herhangi bir yazılabilir değişken veya herhangi bir özellik.</span><span class="sxs-lookup"><span data-stu-id="528ab-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="528ab-107">Herhangi bir sabit değer, sabit veya ifade.</span><span class="sxs-lookup"><span data-stu-id="528ab-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="528ab-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="528ab-108">Remarks</span></span>  
 <span data-ttu-id="528ab-109">Eşittir işaretinin () sol tarafındaki öğesi `=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="528ab-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="528ab-110">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="528ab-110">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="528ab-111">`=`İşleci değeri, sol tarafında bulunan değişkene veya özelliğe doğru değerini atar.</span><span class="sxs-lookup"><span data-stu-id="528ab-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="528ab-112">`=`İşleci bir karşılaştırma işleci olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="528ab-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="528ab-113">Ayrıntılar için bkz. [karşılaştırma işleçleri](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="528ab-113">For details, see [Comparison Operators](comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="528ab-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="528ab-114">Overloading</span></span>  
 <span data-ttu-id="528ab-115">`=`İşleci, atama işleci olarak değil yalnızca ilişkisel karşılaştırma işleci olarak aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="528ab-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="528ab-116">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="528ab-116">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="528ab-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="528ab-117">Example</span></span>  
 <span data-ttu-id="528ab-118">Aşağıdaki örnek, atama işlecini gösterir.</span><span class="sxs-lookup"><span data-stu-id="528ab-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="528ab-119">Sağdaki değer soldaki değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="528ab-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="528ab-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="528ab-120">See also</span></span>

- [<span data-ttu-id="528ab-121">&= Işleci</span><span class="sxs-lookup"><span data-stu-id="528ab-121">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="528ab-122">\* = İşleci</span><span class="sxs-lookup"><span data-stu-id="528ab-122">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="528ab-123">+ = İşleci</span><span class="sxs-lookup"><span data-stu-id="528ab-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="528ab-124">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="528ab-124">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="528ab-125">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="528ab-125">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="528ab-126">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="528ab-126">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="528ab-127">^ = İşleci</span><span class="sxs-lookup"><span data-stu-id="528ab-127">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="528ab-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="528ab-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="528ab-129">Karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="528ab-129">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="528ab-130">Özelliğinin</span><span class="sxs-lookup"><span data-stu-id="528ab-130">ReadOnly</span></span>](../modifiers/readonly.md)
- [<span data-ttu-id="528ab-131">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="528ab-131">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
