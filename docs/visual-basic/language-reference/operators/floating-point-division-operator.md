---
title: / İşleci (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 2036ec8009cfc72a20bcd828d7bc0b252e620cab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610837"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="93099-102">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93099-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="93099-103">İki sayıyı böler ve kayan noktalı bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="93099-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93099-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93099-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="93099-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="93099-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="93099-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="93099-106">Required.</span></span> <span data-ttu-id="93099-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="93099-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="93099-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="93099-108">Required.</span></span> <span data-ttu-id="93099-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="93099-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="93099-110">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="93099-110">Supported Types</span></span>  
 <span data-ttu-id="93099-111">İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türlerin ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="93099-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="93099-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="93099-112">Result</span></span>  
 <span data-ttu-id="93099-113">Tam sayının bölümünü sonucudur `expression1` bölü `expression2`, bir hatırlatıcı dahil.</span><span class="sxs-lookup"><span data-stu-id="93099-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="93099-114">[\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) kalan bıraktığı tamsayı bölümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="93099-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93099-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93099-115">Remarks</span></span>  
 <span data-ttu-id="93099-116">Sonuç veri türü işlenenden türlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="93099-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="93099-117">Aşağıdaki tablo sonuç veri türünü nasıl belirlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="93099-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="93099-118">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="93099-118">Operand data types</span></span>|<span data-ttu-id="93099-119">Sonuç veri türü</span><span class="sxs-lookup"><span data-stu-id="93099-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="93099-120">Her iki ifade de tamsayı veri türleri: ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md), [kısa](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [uzun](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="93099-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="93099-121">Bir ifade bir [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veri türü ve diğer değil bir [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="93099-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="93099-122">Bir ifade bir [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türü ve diğer değil bir [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="93099-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="93099-123">Her iki ifade bir [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türü</span><span class="sxs-lookup"><span data-stu-id="93099-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="93099-124">Bölme işlemi yapıldıktan önce herhangi bir tamsayı sayısal ifadeleri Genişletilmiş `Double`.</span><span class="sxs-lookup"><span data-stu-id="93099-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="93099-125">Visual Basic sonucu bir tam sayı veri türüne atama, sonuç dönüştürmeye çalışır `Double` bu türü.</span><span class="sxs-lookup"><span data-stu-id="93099-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="93099-126">Sonuç türü bu uygun değilse, bunu bir durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="93099-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="93099-127">Özellikle, "Bölüm sıfır olarak çalıştı" Bu Yardım sayfasında bakın.</span><span class="sxs-lookup"><span data-stu-id="93099-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="93099-128">Varsa `expression1` veya `expression2` değerlendiren [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="93099-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="93099-129">Denenen sıfıra bölme</span><span class="sxs-lookup"><span data-stu-id="93099-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="93099-130">Varsa `expression2` sıfır olarak değerlendirilen `/` işleci farklı işlenen veri türleri için farklı davranır.</span><span class="sxs-lookup"><span data-stu-id="93099-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="93099-131">Aşağıdaki tabloda olası davranışları gösterir.</span><span class="sxs-lookup"><span data-stu-id="93099-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="93099-132">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="93099-132">Operand data types</span></span>|<span data-ttu-id="93099-133">Davranış, `expression2` sıfırdır</span><span class="sxs-lookup"><span data-stu-id="93099-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="93099-134">Kayan nokta (`Single` veya `Double`)</span><span class="sxs-lookup"><span data-stu-id="93099-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="93099-135">Sonsuz döndürür (<xref:System.Double.PositiveInfinity> veya <xref:System.Double.NegativeInfinity>), veya <xref:System.Double.NaN> (sayı değil), `expression1` de sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="93099-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="93099-136">Oluşturur <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="93099-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="93099-137">Tamsayı (işaretli veya işaretlenmemiş)</span><span class="sxs-lookup"><span data-stu-id="93099-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="93099-138">İntegral türü atar geri dönüştürme yapılmaya <xref:System.OverflowException> tam sayı türleri kabul edemez çünkü <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, veya <xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="93099-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="93099-139">`/` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="93099-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="93099-140">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="93099-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="93099-141">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="93099-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93099-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="93099-142">Example</span></span>  
 <span data-ttu-id="93099-143">Bu örnekte `/` kayan nokta bölme gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="93099-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="93099-144">Sayının iki işlenenden oluşur.</span><span class="sxs-lookup"><span data-stu-id="93099-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 <span data-ttu-id="93099-145">Önceki örnekte yer alan ifadeleri, 2.5 ve 3.333333 değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="93099-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="93099-146">Sonucu her zaman kayan nokta olduğunu unutmayın (`Double`), her iki işlenen de tamsayı sabitleri olsa bile.</span><span class="sxs-lookup"><span data-stu-id="93099-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93099-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93099-147">See also</span></span>
- [<span data-ttu-id="93099-148">/ = İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93099-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="93099-149">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93099-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="93099-150">İşleç Sonuçlarının Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="93099-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [<span data-ttu-id="93099-151">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="93099-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="93099-152">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="93099-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="93099-153">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="93099-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="93099-154">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="93099-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
