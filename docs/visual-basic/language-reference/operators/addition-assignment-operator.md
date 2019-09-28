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
ms.openlocfilehash: 249a19abfb08677c01ac4cc484d049a7ed1a983c
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591643"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="2f94b-102">+= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f94b-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="2f94b-103">Sayısal bir ifadenin değerini bir sayısal değişkenin veya özelliğin değerine ekler ve sonucu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="2f94b-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="2f94b-104">, Bir `String` ifadesini `String` değişkenine veya özelliğine birleştirmek ve sonucu değişkenine veya özelliğe atamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f94b-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f94b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f94b-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="2f94b-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2f94b-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="2f94b-107">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2f94b-107">Required.</span></span> <span data-ttu-id="2f94b-108">Herhangi bir sayısal veya `String` değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="2f94b-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="2f94b-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2f94b-109">Required.</span></span> <span data-ttu-id="2f94b-110">Herhangi bir sayısal veya `String` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="2f94b-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f94b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f94b-111">Remarks</span></span>  
 <span data-ttu-id="2f94b-112">@No__t-0 işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f94b-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="2f94b-113">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="2f94b-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="2f94b-114">@No__t-0 işleci, solundaki değeri, sol taraftaki değişkene veya özelliğe ekler ve sonucu, sol tarafındaki değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="2f94b-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="2f94b-115">@No__t-0 işleci Ayrıca, `String` ifadesini sağdaki `String` değişkenine veya özelliğine birleştirmek için de kullanılabilir ve sonucu, sol tarafında bulunan değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="2f94b-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f94b-116">@No__t-0 işlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f94b-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="2f94b-117">Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için, birleştirmek üzere `&=` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f94b-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="2f94b-118">Bu atama işleci, derleme ortamı katı semantiği zorlarsa, örtülü olarak genişleyen ancak daraltma dönüştürmesi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="2f94b-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="2f94b-119">Bu dönüşümler hakkında daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="2f94b-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="2f94b-120">Katı ve izin veren semantiği hakkında daha fazla bilgi için bkz. [Option Strict deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2f94b-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="2f94b-121">İzin verilen semantiğe izin veriliyorsa `+=` işleci, `+` işleci tarafından gerçekleştirilmiş olanlarla özdeş olarak çeşitli dize ve sayısal dönüşümler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2f94b-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="2f94b-122">Bu dönüşümlerde Ayrıntılar için bkz. [+ işleci](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2f94b-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2f94b-123">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="2f94b-123">Overloading</span></span>  
 <span data-ttu-id="2f94b-124">@No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2f94b-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2f94b-125">@No__t aşırı yükleme-0 işleci `+=` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="2f94b-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="2f94b-126">Kodunuz, `+` ' i aşırı yükleyen bir sınıf veya yapıda `+=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2f94b-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2f94b-127">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2f94b-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f94b-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f94b-128">Example</span></span>  
 <span data-ttu-id="2f94b-129">Aşağıdaki örnek, bir değişkenin değerini diğeri ile birleştirmek için `+=` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f94b-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="2f94b-130">İlk bölüm, bir değeri başka bir değer eklemek için sayısal değişkenlerle `+=` kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f94b-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="2f94b-131">İkinci bölüm, bir değeri başka bir değerle birleştirmek için `String` değişkenleriyle `+=` kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f94b-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="2f94b-132">Her iki durumda da sonuç ilk değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="2f94b-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="2f94b-133">@No__t-0 değeri artık 13 ' dir ve `str1` değeri artık "103".</span><span class="sxs-lookup"><span data-stu-id="2f94b-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f94b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f94b-134">See also</span></span>

- [<span data-ttu-id="2f94b-135">+ İşleci</span><span class="sxs-lookup"><span data-stu-id="2f94b-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="2f94b-136">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="2f94b-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="2f94b-137">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="2f94b-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="2f94b-138">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="2f94b-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="2f94b-139">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="2f94b-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="2f94b-140">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="2f94b-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="2f94b-141">Deyimler</span><span class="sxs-lookup"><span data-stu-id="2f94b-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
