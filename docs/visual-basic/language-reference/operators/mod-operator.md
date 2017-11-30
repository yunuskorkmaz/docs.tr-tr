---
title: "Mod İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="42f3f-102">Mod İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42f3f-102">Mod Operator (Visual Basic)</span></span>
<span data-ttu-id="42f3f-103">İki sayıyı böler ve yalnızca kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="42f3f-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42f3f-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="42f3f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="42f3f-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="42f3f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="42f3f-106">Required.</span></span> <span data-ttu-id="42f3f-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="42f3f-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="42f3f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="42f3f-108">Required.</span></span> <span data-ttu-id="42f3f-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="42f3f-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="42f3f-110">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="42f3f-110">Supported Types</span></span>  
 <span data-ttu-id="42f3f-111">Tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="42f3f-111">All numeric types.</span></span> <span data-ttu-id="42f3f-112">Bu imzasız ve kayan nokta türleri içerir ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="42f3f-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="42f3f-113">Sonuç</span><span class="sxs-lookup"><span data-stu-id="42f3f-113">Result</span></span>  
 <span data-ttu-id="42f3f-114">Sonra geri kalan sonucudur `number1` bölünür `number2`.</span><span class="sxs-lookup"><span data-stu-id="42f3f-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="42f3f-115">Örneğin, ifade `14 Mod 4` 2 olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="42f3f-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42f3f-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42f3f-116">Remarks</span></span>  
 <span data-ttu-id="42f3f-117">Her iki `number1` veya `number2` bir kayan nokta bölme kayan nokta kalanı döndürülen değerdir.</span><span class="sxs-lookup"><span data-stu-id="42f3f-117">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="42f3f-118">Sonuç veri türü veri türlerini bölme kaynaklanan tüm olası değerler tutabileceği en küçük veri türüdür `number1` ve `number2`.</span><span class="sxs-lookup"><span data-stu-id="42f3f-118">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="42f3f-119">Varsa `number1` veya `number2` değerlendiren [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="42f3f-119">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="42f3f-120">İlgili işleçleri aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="42f3f-120">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="42f3f-121">[\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) bir bölümünün tamsayı bölümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="42f3f-121">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="42f3f-122">Örneğin, ifade `14 \ 4` 3 olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="42f3f-122">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="42f3f-123">[/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) bir kayan noktalı sayı olarak kalan dahil olmak üzere tam sayının döndürür.</span><span class="sxs-lookup"><span data-stu-id="42f3f-123">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="42f3f-124">Örneğin, ifade `14 / 4` 3.5 değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="42f3f-124">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="42f3f-125">Denenen sıfıra</span><span class="sxs-lookup"><span data-stu-id="42f3f-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="42f3f-126">Varsa `number2` sıfır olarak davranışını değerlendirir `Mod` işleci işlenen veri türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="42f3f-126">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="42f3f-127">Tamsayı bölme oluşturur bir <xref:System.DivideByZeroException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="42f3f-127">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="42f3f-128">Kayan nokta bölme döndürür <xref:System.Double.NaN>.</span><span class="sxs-lookup"><span data-stu-id="42f3f-128">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="42f3f-129">Eşdeğer formülü</span><span class="sxs-lookup"><span data-stu-id="42f3f-129">Equivalent Formula</span></span>  
 <span data-ttu-id="42f3f-130">İfade `a Mod b` da aşağıdaki formüller eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="42f3f-130">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="42f3f-131">Kayan nokta Imprecision</span><span class="sxs-lookup"><span data-stu-id="42f3f-131">Floating-Point Imprecision</span></span>  
 <span data-ttu-id="42f3f-132">Kayan nokta sayıları ile çalışırken, bunlar her zaman kesin bir gösterimi belleğe sahip olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="42f3f-132">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="42f3f-133">Değer karşılaştırması gibi bazı işlemleri alanından bu beklenmeyen sonuçlara neden ve `Mod` işleci.</span><span class="sxs-lookup"><span data-stu-id="42f3f-133">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="42f3f-134">Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="42f3f-134">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="42f3f-135">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="42f3f-135">Overloading</span></span>  
 <span data-ttu-id="42f3f-136">`Mod` İşleci olabilir *aşırı*, yani bir sınıf veya yapı davranışını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42f3f-136">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="42f3f-137">Kodunuzu geçerliyse `Mod` bir sınıf ya da böyle bir aşırı içerir yapısı bir örneğine yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="42f3f-137">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="42f3f-138">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="42f3f-138">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42f3f-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="42f3f-139">Example</span></span>  
 <span data-ttu-id="42f3f-140">Aşağıdaki örnek kullanır `Mod` işleci iki sayı bölme ve yalnızca kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="42f3f-140">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="42f3f-141">Her iki sayı kayan noktalı sayı ise kalan temsil eden bir kayan noktalı sayı sonucudur.</span><span class="sxs-lookup"><span data-stu-id="42f3f-141">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="42f3f-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="42f3f-142">Example</span></span>  
 <span data-ttu-id="42f3f-143">Aşağıdaki örnek, kayan nokta işlenenleri imprecision olası gösterir.</span><span class="sxs-lookup"><span data-stu-id="42f3f-143">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="42f3f-144">İşlenen ilk deyiminde olan `Double`, ve 0.2 sonsuz yinelenen bir ikili Kesir 0.20000000000000001 depolanan değeri.</span><span class="sxs-lookup"><span data-stu-id="42f3f-144">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="42f3f-145">İkinci deyiminde sabit değer türü karakteri `D` her iki işlenen zorlar `Decimal`, ve 0.2 kesin bir gösterimi.</span><span class="sxs-lookup"><span data-stu-id="42f3f-145">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="42f3f-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42f3f-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="42f3f-147">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="42f3f-147">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="42f3f-148">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="42f3f-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="42f3f-149">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="42f3f-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="42f3f-150">Veri türleri sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="42f3f-150">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="42f3f-151">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="42f3f-151">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="42f3f-152">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42f3f-152">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
