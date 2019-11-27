---
title: ^= İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: fe5e8fc2b64b9e7c33483612071d338a0ee22768
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331301"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="6b313-102">^= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b313-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="6b313-103">Bir değişkenin veya özelliğin değerini bir ifadenin gücüne yükseltir ve sonucu değişkene veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="6b313-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b313-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b313-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="6b313-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="6b313-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="6b313-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6b313-106">Required.</span></span> <span data-ttu-id="6b313-107">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="6b313-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="6b313-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6b313-108">Required.</span></span> <span data-ttu-id="6b313-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="6b313-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b313-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b313-110">Remarks</span></span>  
 <span data-ttu-id="6b313-111">`^=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b313-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="6b313-112">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="6b313-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="6b313-113">`^=` işleci ilk olarak, değişkenin veya özelliğin değerini (işlecin sol tarafında) ifadenin değerinin (işlecinin sağ tarafında) kuvvetine yükseltir (işlecin sağ tarafındaki).</span><span class="sxs-lookup"><span data-stu-id="6b313-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="6b313-114">İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="6b313-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="6b313-115">Visual Basic her zaman [Double veri türünde](../../../visual-basic/language-reference/data-types/double-data-type.md)üs gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6b313-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="6b313-116">Farklı türdeki işlenenler `Double`dönüştürülür ve sonuç her zaman `Double`.</span><span class="sxs-lookup"><span data-stu-id="6b313-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="6b313-117">`expression` değeri kesirli, negatif veya her ikisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b313-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="6b313-118">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="6b313-118">Overloading</span></span>  
 <span data-ttu-id="6b313-119">[^ İşleci](../../../visual-basic/language-reference/operators/exponentiation-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6b313-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6b313-120">`^` işleci aşırı yükleme `^=` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="6b313-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="6b313-121">Kodunuz, `^`aşırı yükleyen bir sınıf veya yapı üzerinde `^=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6b313-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6b313-122">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6b313-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b313-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b313-123">Example</span></span>  
 <span data-ttu-id="6b313-124">Aşağıdaki örnek, bir `Integer` değişkeninin değerini ikinci bir değişkenin gücüne yükseltmek ve sonucu ilk değişkene atamak için `^=` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b313-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="6b313-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b313-125">See also</span></span>

- [<span data-ttu-id="6b313-126">^ İşleci</span><span class="sxs-lookup"><span data-stu-id="6b313-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [<span data-ttu-id="6b313-127">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="6b313-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="6b313-128">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="6b313-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="6b313-129">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="6b313-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="6b313-130">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="6b313-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="6b313-131">Deyimler</span><span class="sxs-lookup"><span data-stu-id="6b313-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
