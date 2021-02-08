---
description: ': = Işleci hakkında daha fazla bilgi edinin (Visual Basic)'
title: = İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 3cf45fb93bf5138f9e7fa5a43650019ab58674fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774258"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8fda0-103">= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fda0-103">= Operator (Visual Basic)</span></span>

<span data-ttu-id="8fda0-104">Bir değişkene veya özelliğe bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="8fda0-104">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fda0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8fda0-105">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="8fda0-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8fda0-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="8fda0-107">Herhangi bir yazılabilir değişken veya herhangi bir özellik.</span><span class="sxs-lookup"><span data-stu-id="8fda0-107">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="8fda0-108">Herhangi bir sabit değer, sabit veya ifade.</span><span class="sxs-lookup"><span data-stu-id="8fda0-108">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fda0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fda0-109">Remarks</span></span>  

 <span data-ttu-id="8fda0-110">Eşittir işaretinin () sol tarafındaki öğesi `=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="8fda0-110">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8fda0-111">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="8fda0-111">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="8fda0-112">`=`İşleci değeri, sol tarafında bulunan değişkene veya özelliğe doğru değerini atar.</span><span class="sxs-lookup"><span data-stu-id="8fda0-112">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fda0-113">`=`İşleci bir karşılaştırma işleci olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8fda0-113">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="8fda0-114">Ayrıntılar için bkz. [karşılaştırma işleçleri](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8fda0-114">For details, see [Comparison Operators](comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8fda0-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="8fda0-115">Overloading</span></span>  

 <span data-ttu-id="8fda0-116">`=`İşleci, atama işleci olarak değil yalnızca ilişkisel karşılaştırma işleci olarak aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8fda0-116">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="8fda0-117">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8fda0-117">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fda0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fda0-118">Example</span></span>  

 <span data-ttu-id="8fda0-119">Aşağıdaki örnek, atama işlecini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fda0-119">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="8fda0-120">Sağdaki değer soldaki değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="8fda0-120">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="8fda0-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fda0-121">See also</span></span>

- [<span data-ttu-id="8fda0-122">&= Işleci</span><span class="sxs-lookup"><span data-stu-id="8fda0-122">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="8fda0-123">\* = İşleci</span><span class="sxs-lookup"><span data-stu-id="8fda0-123">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="8fda0-124">+ = İşleci</span><span class="sxs-lookup"><span data-stu-id="8fda0-124">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="8fda0-125">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fda0-125">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="8fda0-126">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fda0-126">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="8fda0-127">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="8fda0-127">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="8fda0-128">^ = İşleci</span><span class="sxs-lookup"><span data-stu-id="8fda0-128">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="8fda0-129">Deyimler</span><span class="sxs-lookup"><span data-stu-id="8fda0-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="8fda0-130">Karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="8fda0-130">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="8fda0-131">Özelliğinin</span><span class="sxs-lookup"><span data-stu-id="8fda0-131">ReadOnly</span></span>](../modifiers/readonly.md)
- [<span data-ttu-id="8fda0-132">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fda0-132">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
