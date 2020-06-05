---
title: += İşleci
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
ms.openlocfilehash: c2ce384901a9f0207e8279a5a07a88600c875e7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372213"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="2cb79-102">+= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cb79-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="2cb79-103">Sayısal bir ifadenin değerini bir sayısal değişkenin veya özelliğin değerine ekler ve sonucu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="2cb79-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="2cb79-104">, Bir `String` ifadeyi bir `String` değişkene veya özelliğe birleştirmek ve sonucu değişkene veya özelliğe atamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2cb79-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb79-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cb79-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="2cb79-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2cb79-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="2cb79-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2cb79-107">Required.</span></span> <span data-ttu-id="2cb79-108">Herhangi bir sayısal veya `String` değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="2cb79-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="2cb79-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2cb79-109">Required.</span></span> <span data-ttu-id="2cb79-110">Herhangi bir sayısal or `String` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="2cb79-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb79-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cb79-111">Remarks</span></span>  
 <span data-ttu-id="2cb79-112">İşlecinin sol tarafındaki öğesi `+=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2cb79-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="2cb79-113">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="2cb79-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="2cb79-114">`+=`İşleci, solundaki değeri, sol taraftaki değişkene veya özelliğe ekler ve sonucu, sol tarafında değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="2cb79-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="2cb79-115">`+=`İşleci Ayrıca, sol tarafında bulunan `String` değişken veya özellik için ifadeyi sağ tarafta birleştirmek `String` ve sonucu, sol tarafında değişken veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="2cb79-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cb79-116">`+=`İşlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cb79-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="2cb79-117">`&=`Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için birleştirme işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2cb79-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="2cb79-118">Bu atama işleci, derleme ortamı katı semantiği zorlarsa, örtülü olarak genişleyen ancak daraltma dönüştürmesi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="2cb79-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="2cb79-119">Bu dönüşümler hakkında daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="2cb79-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="2cb79-120">Katı ve izin veren semantiği hakkında daha fazla bilgi için bkz. [Option Strict deyimin](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2cb79-120">For more information on strict and permissive semantics, see [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="2cb79-121">İzin verilen semantiğe izin veriliyorsa, `+=` işleç örtük olarak işleç tarafından gerçekleştirenlerle aynı şekilde çeşitli dize ve sayısal dönüşümler gerçekleştirir `+` .</span><span class="sxs-lookup"><span data-stu-id="2cb79-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="2cb79-122">Bu dönüşümlerde Ayrıntılar için bkz. [+ işleci](addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2cb79-122">For details on these conversions, see [+ Operator](addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2cb79-123">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="2cb79-123">Overloading</span></span>  
 <span data-ttu-id="2cb79-124">`+`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2cb79-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2cb79-125">İşleci aşırı yüklemek `+` işlecin davranışını etkiler `+=` .</span><span class="sxs-lookup"><span data-stu-id="2cb79-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="2cb79-126">Kodunuzun `+=` bir sınıf veya yapı üzerinde kullanması durumunda `+` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2cb79-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2cb79-127">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2cb79-127">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb79-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cb79-128">Example</span></span>  
 <span data-ttu-id="2cb79-129">Aşağıdaki örnek, `+=` bir değişkenin değerini diğeri ile birleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cb79-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="2cb79-130">İlk bölüm, bir `+=` değeri başka bir değer eklemek için sayısal değişkenlerle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cb79-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="2cb79-131">İkinci bölüm, `+=` `String` bir değeri başka bir değerle birleştirmek için değişkenlerle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cb79-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="2cb79-132">Her iki durumda da sonuç ilk değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="2cb79-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="2cb79-133">Değeri `num1` artık 13 ' dir ve değeri `str1` artık "103".</span><span class="sxs-lookup"><span data-stu-id="2cb79-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb79-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cb79-134">See also</span></span>

- [<span data-ttu-id="2cb79-135">+ İşleci</span><span class="sxs-lookup"><span data-stu-id="2cb79-135">+ Operator</span></span>](addition-operator.md)
- [<span data-ttu-id="2cb79-136">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="2cb79-136">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="2cb79-137">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="2cb79-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="2cb79-138">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="2cb79-138">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="2cb79-139">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="2cb79-139">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="2cb79-140">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="2cb79-140">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="2cb79-141">Deyimler</span><span class="sxs-lookup"><span data-stu-id="2cb79-141">Statements</span></span>](../../programming-guide/language-features/statements.md)
