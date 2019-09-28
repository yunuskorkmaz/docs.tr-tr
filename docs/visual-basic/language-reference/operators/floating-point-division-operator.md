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
ms.openlocfilehash: 238c062b2dd0744ba96cf9ba8591c0ef39f81bb3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592191"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3b058-102">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b058-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="3b058-103">İki sayıyı böler ve kayan noktalı bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b058-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b058-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b058-104">Syntax</span></span>  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="3b058-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3b058-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="3b058-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3b058-106">Required.</span></span> <span data-ttu-id="3b058-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="3b058-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="3b058-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3b058-108">Required.</span></span> <span data-ttu-id="3b058-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="3b058-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="3b058-110">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="3b058-110">Supported Types</span></span>  
 <span data-ttu-id="3b058-111">İşaretsiz ve kayan nokta türleri ve `Decimal` dahil olmak üzere tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="3b058-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="3b058-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="3b058-112">Result</span></span>  
 <span data-ttu-id="3b058-113">Sonuç, her geri kalanı dahil `expression1` ' ı `expression2` ' in tam bölümü olur.</span><span class="sxs-lookup"><span data-stu-id="3b058-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="3b058-114">[\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) , kalanı döndüren tamsayı bölümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b058-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b058-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b058-115">Remarks</span></span>  
 <span data-ttu-id="3b058-116">Sonucun veri türü, işlenenlerinin türlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b058-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="3b058-117">Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b058-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="3b058-118">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="3b058-118">Operand data types</span></span>|<span data-ttu-id="3b058-119">Sonuç veri türü</span><span class="sxs-lookup"><span data-stu-id="3b058-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="3b058-120">Her iki ifade de İntegral veri türleridir[(SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [ushort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="3b058-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="3b058-121">Tek bir ifade [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) bir veri türüdür ve diğeri [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) değildir</span><span class="sxs-lookup"><span data-stu-id="3b058-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="3b058-122">Bir ifade [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türüdür ve diğeri [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) değil</span><span class="sxs-lookup"><span data-stu-id="3b058-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="3b058-123">İki ifade de bir [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türüdür</span><span class="sxs-lookup"><span data-stu-id="3b058-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="3b058-124">Bölüm gerçekleştirilmeden önce, tüm integral sayısal ifadeler iletildiklerinde `Double` ' dır.</span><span class="sxs-lookup"><span data-stu-id="3b058-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="3b058-125">Sonucu bir integral veri türüne atarsanız, Visual Basic sonucu `Double` ' dan bu türe dönüştürmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="3b058-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="3b058-126">Bu, sonuç bu türe uygun değilse bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="3b058-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="3b058-127">Özellikle, bu Yardım sayfasında "sıfıra bölme yapılmaya çalışıldı" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3b058-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="3b058-128">Ya da hiçbir şey değerlendirilirse, sıfır olarak değerlendirilir. [](../../../visual-basic/language-reference/nothing.md) `expression1` `expression2`</span><span class="sxs-lookup"><span data-stu-id="3b058-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="3b058-129">Sıfıra bölme denendi</span><span class="sxs-lookup"><span data-stu-id="3b058-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="3b058-130">@No__t-0, sıfır olarak değerlendirilirse, `/` işleci farklı işlenen veri türleri için farklı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="3b058-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="3b058-131">Aşağıdaki tabloda olası davranışlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b058-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="3b058-132">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="3b058-132">Operand data types</span></span>|<span data-ttu-id="3b058-133">@No__t-0 sıfırsa davranış</span><span class="sxs-lookup"><span data-stu-id="3b058-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="3b058-134">Kayan nokta (`Single` veya `Double`)</span><span class="sxs-lookup"><span data-stu-id="3b058-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="3b058-135">@No__t-3 de sıfırsa sonsuz (<xref:System.Double.PositiveInfinity> veya <xref:System.Double.NegativeInfinity>) veya <xref:System.Double.NaN> (sayı değil) döndürür</span><span class="sxs-lookup"><span data-stu-id="3b058-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="3b058-136">@No__t oluşturur-0</span><span class="sxs-lookup"><span data-stu-id="3b058-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="3b058-137">Integral (işaretli veya imzasız)</span><span class="sxs-lookup"><span data-stu-id="3b058-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="3b058-138">İntegral türler <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity> veya <xref:System.Double.NaN> ' i kabul edemediği için, <xref:System.OverflowException> ' a geri dönüştürme denendi.</span><span class="sxs-lookup"><span data-stu-id="3b058-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3b058-139">@No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3b058-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3b058-140">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3b058-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3b058-141">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3b058-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b058-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b058-142">Example</span></span>  
 <span data-ttu-id="3b058-143">Bu örnek, kayan nokta bölme gerçekleştirmek için `/` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b058-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="3b058-144">Sonuç iki işlenenin bir bölümü olur.</span><span class="sxs-lookup"><span data-stu-id="3b058-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="3b058-145">Yukarıdaki örnekteki ifadeler 2,5 ve 3,333333 değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b058-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="3b058-146">Her iki işlenen de tamsayı sabitleri olsa da sonucun her zaman kayan nokta (`Double`) olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b058-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b058-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b058-147">See also</span></span>

- [<span data-ttu-id="3b058-148">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b058-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="3b058-149">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b058-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="3b058-150">İşleç Sonuçlarının Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="3b058-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [<span data-ttu-id="3b058-151">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="3b058-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="3b058-152">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="3b058-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="3b058-153">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="3b058-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="3b058-154">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="3b058-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
