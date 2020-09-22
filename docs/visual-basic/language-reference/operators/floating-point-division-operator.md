---
title: / İşleci
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
ms.openlocfilehash: 765a80d45908e0ecf17e4c21b748dbf6b2a4c0f5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867035"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="31dd9-102">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31dd9-102">/ Operator (Visual Basic)</span></span>

<span data-ttu-id="31dd9-103">İki sayıyı böler ve kayan noktalı bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="31dd9-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31dd9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31dd9-104">Syntax</span></span>  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="31dd9-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="31dd9-105">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="31dd9-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31dd9-106">Required.</span></span> <span data-ttu-id="31dd9-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="31dd9-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="31dd9-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31dd9-108">Required.</span></span> <span data-ttu-id="31dd9-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="31dd9-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="31dd9-110">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="31dd9-110">Supported Types</span></span>  

 <span data-ttu-id="31dd9-111">İmzasız ve kayan nokta türleri de dahil olmak üzere tüm sayısal türler `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="31dd9-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="31dd9-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="31dd9-112">Result</span></span>  

 <span data-ttu-id="31dd9-113">Sonuç, `expression1` `expression2` kalanı da dahil olmak üzere bölünen tam bölüm.</span><span class="sxs-lookup"><span data-stu-id="31dd9-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="31dd9-114">[\ İşleci (Visual Basic)](integer-division-operator.md) , kalanı döndüren tamsayı bölümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="31dd9-114">The [\ Operator (Visual Basic)](integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31dd9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31dd9-115">Remarks</span></span>  

 <span data-ttu-id="31dd9-116">Sonucun veri türü, işlenenlerinin türlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="31dd9-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="31dd9-117">Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31dd9-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="31dd9-118">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="31dd9-118">Operand data types</span></span>|<span data-ttu-id="31dd9-119">Sonuç veri türü</span><span class="sxs-lookup"><span data-stu-id="31dd9-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="31dd9-120">Her iki ifade de İntegral veri türleridir[(SByte](../data-types/sbyte-data-type.md), [byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [ushort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="31dd9-120">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="31dd9-121">Tek bir ifade [tek](../data-types/single-data-type.md) bir veri türüdür ve diğeri [Double](../data-types/double-data-type.md) değildir</span><span class="sxs-lookup"><span data-stu-id="31dd9-121">One expression is a [Single](../data-types/single-data-type.md) data type and the other is not a [Double](../data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="31dd9-122">Bir ifade [ondalık](../data-types/decimal-data-type.md) veri türüdür ve diğeri [tek](../data-types/single-data-type.md) veya [çift](../data-types/double-data-type.md) değil</span><span class="sxs-lookup"><span data-stu-id="31dd9-122">One expression is a [Decimal](../data-types/decimal-data-type.md) data type and the other is not a [Single](../data-types/single-data-type.md) or a [Double](../data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="31dd9-123">İki ifade de bir [Double](../data-types/double-data-type.md) veri türüdür</span><span class="sxs-lookup"><span data-stu-id="31dd9-123">Either expression is a [Double](../data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="31dd9-124">Bölüm gerçekleştirilmeden önce, tüm integral sayısal ifadeler iletildiklerinde ' dir `Double` .</span><span class="sxs-lookup"><span data-stu-id="31dd9-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="31dd9-125">Sonucu bir integral veri türüne atarsanız, Visual Basic sonucu `Double` Bu türe dönüştürmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="31dd9-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="31dd9-126">Bu, sonuç bu türe uygun değilse bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="31dd9-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="31dd9-127">Özellikle, bu Yardım sayfasında "sıfıra bölme yapılmaya çalışıldı" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="31dd9-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="31dd9-128">`expression1`Ya da `expression2` [hiçbir şey](../nothing.md)değerlendirilirse, sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="31dd9-128">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="31dd9-129">Sıfıra bölme denendi</span><span class="sxs-lookup"><span data-stu-id="31dd9-129">Attempted Division by Zero</span></span>  

 <span data-ttu-id="31dd9-130">`expression2`Sıfır olarak değerlendirilirse, `/` işleç farklı işlenen veri türleri için farklı davranır.</span><span class="sxs-lookup"><span data-stu-id="31dd9-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="31dd9-131">Aşağıdaki tabloda olası davranışlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31dd9-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="31dd9-132">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="31dd9-132">Operand data types</span></span>|<span data-ttu-id="31dd9-133">Sıfır ise davranış `expression2`</span><span class="sxs-lookup"><span data-stu-id="31dd9-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="31dd9-134">Kayan nokta ( `Single` veya `Double` )</span><span class="sxs-lookup"><span data-stu-id="31dd9-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="31dd9-135"><xref:System.Double.PositiveInfinity> <xref:System.Double.NegativeInfinity> Sıfır ise, sonsuz (veya), ya <xref:System.Double.NaN> da (sayı değil) döndürür `expression1`</span><span class="sxs-lookup"><span data-stu-id="31dd9-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="31dd9-136">Oluşturur <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="31dd9-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="31dd9-137">Integral (işaretli veya imzasız)</span><span class="sxs-lookup"><span data-stu-id="31dd9-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="31dd9-138"><xref:System.OverflowException>İntegral türler <xref:System.Double.PositiveInfinity> , veya kabul edilemediğinden integral türüne geri dönüştürme denendi. <xref:System.Double.NegativeInfinity><xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="31dd9-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="31dd9-139">`/`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="31dd9-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="31dd9-140">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="31dd9-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="31dd9-141">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="31dd9-141">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31dd9-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="31dd9-142">Example</span></span>  

 <span data-ttu-id="31dd9-143">Bu örnek, `/` kayan nokta bölme gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="31dd9-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="31dd9-144">Sonuç iki işlenenin bir bölümü olur.</span><span class="sxs-lookup"><span data-stu-id="31dd9-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="31dd9-145">Yukarıdaki örnekteki ifadeler 2,5 ve 3,333333 değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="31dd9-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="31dd9-146">`Double`Her iki işlenen de tamsayı sabiti olsa da sonucun her zaman kayan nokta () olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="31dd9-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31dd9-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31dd9-147">See also</span></span>

- [<span data-ttu-id="31dd9-148">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31dd9-148">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="31dd9-149">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31dd9-149">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="31dd9-150">İşleç Sonuçlarının Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="31dd9-150">Data Types of Operator Results</span></span>](data-types-of-operator-results.md)
- [<span data-ttu-id="31dd9-151">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="31dd9-151">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="31dd9-152">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="31dd9-152">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="31dd9-153">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="31dd9-153">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="31dd9-154">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="31dd9-154">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
