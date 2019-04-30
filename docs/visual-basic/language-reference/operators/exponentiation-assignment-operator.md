---
title: ^= İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: fe5d7b3dcb55192167512e0934e09cff7dfddb6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778527"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9998c-102">^= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9998c-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="9998c-103">Bir değişken veya özellik değerini bir ifade değeri oluşturur ve sonucu değişken veya özellik için atar.</span><span class="sxs-lookup"><span data-stu-id="9998c-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9998c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9998c-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9998c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9998c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="9998c-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9998c-106">Required.</span></span> <span data-ttu-id="9998c-107">Tüm sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="9998c-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="9998c-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9998c-108">Required.</span></span> <span data-ttu-id="9998c-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9998c-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9998c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9998c-110">Remarks</span></span>  
 <span data-ttu-id="9998c-111">Öğe sol tarafındaki `^=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="9998c-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="9998c-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9998c-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="9998c-113">`^=` İşleci ilk başlatır değişken veya özellik (üzerinde işlecinin sol tarafı) değerini gücüne (işlecin sağ tarafındaki) ifade değeri.</span><span class="sxs-lookup"><span data-stu-id="9998c-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="9998c-114">İşleci, bu işlemin sonucunu daha sonra değişken veya özellik için atar.</span><span class="sxs-lookup"><span data-stu-id="9998c-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="9998c-115">Visual Basic içinde üs her zaman gerçekleştirir [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="9998c-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="9998c-116">Tüm farklı türündeki işlenenler için dönüştürülür `Double`, ve sonucu her zaman `Double`.</span><span class="sxs-lookup"><span data-stu-id="9998c-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="9998c-117">Değerini `expression` kesir olabilir negatif veya her ikisini de.</span><span class="sxs-lookup"><span data-stu-id="9998c-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9998c-118">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="9998c-118">Overloading</span></span>  
 <span data-ttu-id="9998c-119">[^ İşleci](../../../visual-basic/language-reference/operators/exponentiation-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9998c-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9998c-120">Aşırı yükleme `^` işleci davranışını etkileyen `^=` işleci.</span><span class="sxs-lookup"><span data-stu-id="9998c-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="9998c-121">Kodunuzu kullanıyorsa `^=` bir sınıf veya aşırı yapısı `^`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9998c-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9998c-122">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9998c-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9998c-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="9998c-123">Example</span></span>  
 <span data-ttu-id="9998c-124">Aşağıdaki örnekte `^=` değerini artırmak için işleci `Integer` değişkenini ikinci değişken ve ata birinci değişken sonucu.</span><span class="sxs-lookup"><span data-stu-id="9998c-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="9998c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9998c-125">See also</span></span>

- [<span data-ttu-id="9998c-126">^ İşleci</span><span class="sxs-lookup"><span data-stu-id="9998c-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [<span data-ttu-id="9998c-127">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9998c-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="9998c-128">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="9998c-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="9998c-129">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="9998c-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9998c-130">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="9998c-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9998c-131">Deyimler</span><span class="sxs-lookup"><span data-stu-id="9998c-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
