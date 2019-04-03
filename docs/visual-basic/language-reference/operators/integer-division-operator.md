---
title: '\ İşleci (Visual Basic)'
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
ms.openlocfilehash: 1753199e2ecf3f156b90d8c0a5cacd672397260d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828714"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e4ee7-102">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4ee7-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="e4ee7-103">İki sayıyı böler ve tamsayı sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ee7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4ee7-104">Syntax</span></span>  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="e4ee7-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e4ee7-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="e4ee7-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-106">Required.</span></span> <span data-ttu-id="e4ee7-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="e4ee7-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-108">Required.</span></span> <span data-ttu-id="e4ee7-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="e4ee7-110">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="e4ee7-110">Supported Types</span></span>  
 <span data-ttu-id="e4ee7-111">İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türlerin ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="e4ee7-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="e4ee7-112">Result</span></span>  
 <span data-ttu-id="e4ee7-113">Tamsayı bölümünü sonucudur `expression1` bölü `expression2`, tüm kalan kısmını atar ve yalnızca tamsayı bölümü korur.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="e4ee7-114">Bu olarak bilinir *kesilmesi*.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="e4ee7-115">Sonuç veri türü olan veri türleri için uygun bir sayısal tür `expression1` ve `expression2`.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="e4ee7-116">"Tamsayı aritmetik" tablolarında bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="e4ee7-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="e4ee7-117">[/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) kesirli bölümü kalanı korur tam bölümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4ee7-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4ee7-118">Remarks</span></span>  
 <span data-ttu-id="e4ee7-119">Bölme işlemi gerçekleştirmeden önce Visual Basic herhangi bir kayan nokta sayısal ifade dönüştürmeye çalışır `Long`.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="e4ee7-120">Varsa `Option Strict` olduğu `On`, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="e4ee7-121">Varsa `Option Strict` olduğu `Off`e <xref:System.OverflowException> değer aralığının dışında ise mümkündür [Long veri türü](../../../visual-basic/language-reference/data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e4ee7-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="e4ee7-122">Dönüştürme `Long` de tabi olduğu *banker yuvarlama*.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="e4ee7-123">Daha fazla bilgi için bkz: "Kesirli bölümleri" [tür dönüştürme işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e4ee7-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="e4ee7-124">Varsa `expression1` veya `expression2` değerlendiren [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="e4ee7-125">Denenen sıfıra bölme</span><span class="sxs-lookup"><span data-stu-id="e4ee7-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="e4ee7-126">Varsa `expression2` sıfır olarak değerlendirilen `\` işleci oluşturur bir <xref:System.DivideByZeroException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="e4ee7-127">Bu işlenenlerin tüm sayısal veri türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4ee7-128">`\` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e4ee7-129">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e4ee7-130">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e4ee7-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4ee7-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4ee7-131">Example</span></span>  
 <span data-ttu-id="e4ee7-132">Aşağıdaki örnekte `\` tamsayı bölme gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="e4ee7-133">İki işlenenden tamsayı bölümü atılır geri kalanı ile temsil eden bir tamsayı sonucudur.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="e4ee7-134">Önceki örnekte yer alan ifadeleri sırasıyla 2, 3, 33 ve -22, değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ee7-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4ee7-135">See also</span></span>

- [<span data-ttu-id="e4ee7-136">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="e4ee7-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="e4ee7-137">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4ee7-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="e4ee7-138">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="e4ee7-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="e4ee7-139">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="e4ee7-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="e4ee7-140">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="e4ee7-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e4ee7-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="e4ee7-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e4ee7-142">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="e4ee7-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
