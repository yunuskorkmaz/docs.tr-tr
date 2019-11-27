---
title: '\ İşleci'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 2b4cca99ed54195162530bb8eb950bd251bfbff9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347115"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="60c6f-102">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60c6f-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="60c6f-103">İki sayıyı böler ve bir tamsayı sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="60c6f-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c6f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60c6f-104">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="60c6f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="60c6f-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="60c6f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="60c6f-106">Required.</span></span> <span data-ttu-id="60c6f-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="60c6f-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="60c6f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="60c6f-108">Required.</span></span> <span data-ttu-id="60c6f-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="60c6f-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="60c6f-110">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="60c6f-110">Supported Types</span></span>  
 <span data-ttu-id="60c6f-111">İşaretsiz ve kayan nokta türleri ve `Decimal`dahil olmak üzere tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="60c6f-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="60c6f-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="60c6f-112">Result</span></span>  
 <span data-ttu-id="60c6f-113">Sonuç, `expression2`tarafından bölünen `expression1` tamsayı bölümüdür ve bu, kalanı atar ve yalnızca tamsayı kısmını korur.</span><span class="sxs-lookup"><span data-stu-id="60c6f-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="60c6f-114">Bu, *kesme*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="60c6f-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="60c6f-115">Sonuç veri türü, `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür.</span><span class="sxs-lookup"><span data-stu-id="60c6f-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="60c6f-116">[Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="60c6f-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="60c6f-117">[/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) , kesir bölümünde kalanı tutan tam bölümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="60c6f-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60c6f-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60c6f-118">Remarks</span></span>  
 <span data-ttu-id="60c6f-119">Bölme işlemini gerçekleştirmeden önce, Visual Basic herhangi bir kayan nokta sayısal ifadesini `Long`dönüştürmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="60c6f-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="60c6f-120">`Option Strict` `On`, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="60c6f-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="60c6f-121">`Option Strict` `Off`ise, değer [uzun veri türü](../../../visual-basic/language-reference/data-types/long-data-type.md)aralığının dışındaysa bir <xref:System.OverflowException> mümkündür.</span><span class="sxs-lookup"><span data-stu-id="60c6f-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="60c6f-122">`Long` dönüştürme işlemi, *banker 'in yuvarlanması*için de tabidir.</span><span class="sxs-lookup"><span data-stu-id="60c6f-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="60c6f-123">Daha fazla bilgi için [tür dönüştürme işlevlerinde](../../../visual-basic/language-reference/functions/type-conversion-functions.md)"kesirli parçalar" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="60c6f-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="60c6f-124">`expression1` veya `expression2` [Nothing](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="60c6f-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="60c6f-125">Sıfıra bölme denendi</span><span class="sxs-lookup"><span data-stu-id="60c6f-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="60c6f-126">`expression2` sıfır olarak değerlendirilirse, `\` işleci bir <xref:System.DivideByZeroException> özel durumu atar.</span><span class="sxs-lookup"><span data-stu-id="60c6f-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="60c6f-127">Bu, işlenenlerin tüm sayısal veri türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="60c6f-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60c6f-128">`\` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="60c6f-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="60c6f-129">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="60c6f-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="60c6f-130">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="60c6f-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60c6f-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="60c6f-131">Example</span></span>  
 <span data-ttu-id="60c6f-132">Aşağıdaki örnek, tamsayı bölme gerçekleştirmek için `\` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="60c6f-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="60c6f-133">Sonuç, geri kalan atılan iki işlenenin tamsayı bölümünü temsil eden bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="60c6f-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="60c6f-134">Yukarıdaki örnekteki ifadeler sırasıyla 2, 3, 33 ve-22 değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="60c6f-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c6f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60c6f-135">See also</span></span>

- [<span data-ttu-id="60c6f-136">\\= Işleci</span><span class="sxs-lookup"><span data-stu-id="60c6f-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="60c6f-137">/İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60c6f-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="60c6f-138">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="60c6f-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="60c6f-139">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="60c6f-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="60c6f-140">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="60c6f-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="60c6f-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="60c6f-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="60c6f-142">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="60c6f-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
