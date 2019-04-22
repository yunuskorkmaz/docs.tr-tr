---
title: += İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: 4b8f36397d0f52866ebe9fa188d6b163364aeffc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839028"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c2c8a-102">+= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2c8a-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="c2c8a-103">Sayısal bir ifadenin değerini sayısal değişken veya özellik değerine ekler ve sonucu değişken veya özellik atar.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="c2c8a-104">Birleştirmek için de kullanılabilir bir `String` ifade bir `String` değişken veya özellik ve ata değişken veya özellik sonucu.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c8a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2c8a-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c2c8a-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c2c8a-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="c2c8a-107">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-107">Required.</span></span> <span data-ttu-id="c2c8a-108">Herhangi bir sayısal veya `String` değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="c2c8a-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-109">Required.</span></span> <span data-ttu-id="c2c8a-110">Herhangi bir sayısal veya `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2c8a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2c8a-111">Remarks</span></span>  
 <span data-ttu-id="c2c8a-112">Öğe sol tarafındaki `+=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="c2c8a-113">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="c2c8a-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="c2c8a-114">`+=` İşleci sağındakiyle değişken veya özellik, sol taraftaki değer ekler ve sonucu bir değişken veya özellik, sol taraftaki atar.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="c2c8a-115">`+=` İşleci de kullanılabilir birleştirmek için `String` sağındakiyle için ifade `String` değişken veya özelliği, solda ve sonucu bir değişkene atayın ya da, sol taraftaki özellik.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2c8a-116">Kullanırken `+=` işleci, yükleyemeyebilir eklenmesi veya dize birleştirme gerçekleşip gerçekleşmeyeceğini belirlemek.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="c2c8a-117">Kullanım `&=` birleştirme için işleç belirsizliği ortadan kaldırmak ve kendi kendine belgelendirme kodu sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="c2c8a-118">Bu atama işleci örtük olarak derleme ortamı katı semantiklerini zorlarsa daraltma dönüşümleri değil ancak genişletme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="c2c8a-119">Bu dönüştürmeler hakkında daha fazla bilgi için bkz. [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="c2c8a-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="c2c8a-120">Katı ve esnek semantiği hakkında daha fazla bilgi için bkz. [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c2c8a-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="c2c8a-121">Esnek semantiği izin veriliyorsa `+=` işleci, örtük olarak olanlar tarafından gerçekleştirilen aynı dize ve sayısal dönüştürmeler çeşitli gerçekleştirir `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="c2c8a-122">Bu dönüştürmeler hakkında daha fazla bilgi için bkz: [+ işleci](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c2c8a-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c2c8a-123">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="c2c8a-123">Overloading</span></span>  
 <span data-ttu-id="c2c8a-124">`+` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c2c8a-125">Aşırı yükleme `+` işleci davranışını etkileyen `+=` işleci.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="c2c8a-126">Kodunuzu kullanıyorsa `+=` bir sınıf veya aşırı yapısı `+`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c2c8a-127">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c2c8a-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c8a-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2c8a-128">Example</span></span>  
 <span data-ttu-id="c2c8a-129">Aşağıdaki örnekte `+=` bir değişkenin değerini diğeriyle birleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="c2c8a-130">İlk bölümü kullanan `+=` sayısal değişkenleriyle başka bir değer ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="c2c8a-131">İkinci bölümü'nü kullanan `+=` ile `String` başka bir değerle birleştirilecek değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="c2c8a-132">Her iki durumda da sonucu ilk değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="c2c8a-133">Değerini `num1` 13 ve değerini sunulmuştur `str1` "103" sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c8a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2c8a-134">See also</span></span>

- [<span data-ttu-id="c2c8a-135">+ İşleci</span><span class="sxs-lookup"><span data-stu-id="c2c8a-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="c2c8a-136">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c2c8a-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="c2c8a-137">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="c2c8a-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="c2c8a-138">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c2c8a-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="c2c8a-139">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="c2c8a-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="c2c8a-140">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="c2c8a-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="c2c8a-141">Deyimler</span><span class="sxs-lookup"><span data-stu-id="c2c8a-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
