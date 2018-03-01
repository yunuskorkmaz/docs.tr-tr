---
title: "/ İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f221e863725b9aeb0b3fa3219b3a881541e2be0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="a2b7b-102">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2b7b-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="a2b7b-103">İki sayıyı böler ve kayan noktalı bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b7b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2b7b-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a2b7b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a2b7b-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="a2b7b-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-106">Required.</span></span> <span data-ttu-id="a2b7b-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a2b7b-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-108">Required.</span></span> <span data-ttu-id="a2b7b-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="a2b7b-110">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="a2b7b-110">Supported Types</span></span>  
 <span data-ttu-id="a2b7b-111">İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türler ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="a2b7b-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="a2b7b-112">Result</span></span>  
 <span data-ttu-id="a2b7b-113">Tam sayının bölümünü sonucudur `expression1` bölü `expression2`, tüm kalan dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="a2b7b-114">[\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) kalan bırakır tamsayı bölümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2b7b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2b7b-115">Remarks</span></span>  
 <span data-ttu-id="a2b7b-116">Sonuç veri türü işlenen türlerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="a2b7b-117">Aşağıdaki tabloda, sonuç veri türü nasıl belirlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="a2b7b-118">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="a2b7b-118">Operand data types</span></span>|<span data-ttu-id="a2b7b-119">Sonuç veri türü</span><span class="sxs-lookup"><span data-stu-id="a2b7b-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="a2b7b-120">Her iki ifadelerini tam sayı veri türleri ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md), [kısa](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [uzun](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="a2b7b-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="a2b7b-121">Bir ifade bir [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veri türü ve diğer değil bir [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="a2b7b-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="a2b7b-122">Bir ifade bir [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türü ve diğer değil bir [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="a2b7b-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="a2b7b-123">Ya da ifade bir [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türü</span><span class="sxs-lookup"><span data-stu-id="a2b7b-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="a2b7b-124">Tam sayı tüm sayısal ifadeleri devam bölme gerçekleştirilmeden önce `Double`.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="a2b7b-125">Bir tam sayı veri türü sonucu atarsanız, Visual Basic sonucundan dönüştürmeye çalışır `Double` bu türü.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="a2b7b-126">Sonuç bu tür uygun değilse, bu bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="a2b7b-127">Özellikle, "Bölme sıfır tarafından çalıştı" Bu yardım sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="a2b7b-128">Varsa `expression1` veya `expression2` değerlendiren [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="a2b7b-129">Denenen sıfıra</span><span class="sxs-lookup"><span data-stu-id="a2b7b-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="a2b7b-130">Varsa `expression2` sıfır olarak değerlendirilir `/` işleci farklı işlenen veri türleri için farklı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="a2b7b-131">Aşağıdaki tabloda olası davranışları gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="a2b7b-132">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="a2b7b-132">Operand data types</span></span>|<span data-ttu-id="a2b7b-133">Davranış, `expression2` sıfır</span><span class="sxs-lookup"><span data-stu-id="a2b7b-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="a2b7b-134">Kayan nokta (`Single` veya `Double`)</span><span class="sxs-lookup"><span data-stu-id="a2b7b-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="a2b7b-135">Sonsuz döndürür (<xref:System.Double.PositiveInfinity> veya <xref:System.Double.NegativeInfinity>), veya <xref:System.Double.NaN> (sayı değil), `expression1` de sıfırdır</span><span class="sxs-lookup"><span data-stu-id="a2b7b-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="a2b7b-136">Oluşturur<xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="a2b7b-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="a2b7b-137">İntegral (imzalı veya imzasız)</span><span class="sxs-lookup"><span data-stu-id="a2b7b-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="a2b7b-138">Tam sayı türü atar geri dönüştürme yapılmaya <xref:System.OverflowException> tam sayı türleri kabul edemiyor çünkü <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, veya<xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="a2b7b-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a2b7b-139">`/` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a2b7b-140">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a2b7b-141">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a2b7b-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2b7b-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2b7b-142">Example</span></span>  
 <span data-ttu-id="a2b7b-143">Bu örnekte `/` işleci kayan nokta bölme gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="a2b7b-144">İki işlenen sayının sonucudur.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 <span data-ttu-id="a2b7b-145">Önceki örnekte ifadeleri 2.5 ve 3.333333 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="a2b7b-146">Sonuç her zaman kayan nokta olduğuna dikkat edin (`Double`), her iki işlenen tamsayı sabitleri olsa bile.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b7b-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b7b-147">See Also</span></span>  
 [<span data-ttu-id="a2b7b-148">/ = İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2b7b-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="a2b7b-149">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2b7b-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="a2b7b-150">İşleç sonuçlarının veri türleri</span><span class="sxs-lookup"><span data-stu-id="a2b7b-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [<span data-ttu-id="a2b7b-151">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="a2b7b-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="a2b7b-152">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="a2b7b-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="a2b7b-153">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="a2b7b-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="a2b7b-154">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="a2b7b-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
