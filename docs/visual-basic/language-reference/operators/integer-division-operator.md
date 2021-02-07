---
description: ': Işleci hakkında daha fazla bilgi edinin (Visual Basic)'
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
ms.openlocfilehash: e15a630d37e423b7a7d0040e495f2543889f37b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665789"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9ea22-103">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ea22-103">\ Operator (Visual Basic)</span></span>

<span data-ttu-id="9ea22-104">İki sayıyı böler ve bir tamsayı sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ea22-104">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ea22-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ea22-105">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="9ea22-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9ea22-106">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="9ea22-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9ea22-107">Required.</span></span> <span data-ttu-id="9ea22-108">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9ea22-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="9ea22-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9ea22-109">Required.</span></span> <span data-ttu-id="9ea22-110">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9ea22-110">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="9ea22-111">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="9ea22-111">Supported Types</span></span>  

 <span data-ttu-id="9ea22-112">İmzasız ve kayan nokta türleri de dahil olmak üzere tüm sayısal türler `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="9ea22-112">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="9ea22-113">Sonuç</span><span class="sxs-lookup"><span data-stu-id="9ea22-113">Result</span></span>  

 <span data-ttu-id="9ea22-114">Sonuç, `expression1` ' ın bölünen tamsayı `expression2` bölümüdür. Bu, kalanı atar ve yalnızca tamsayı kısmını korur.</span><span class="sxs-lookup"><span data-stu-id="9ea22-114">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="9ea22-115">Bu, *kesme* olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="9ea22-115">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="9ea22-116">Sonuç veri türü ve veri türleri için uygun bir sayısal türdür `expression1` `expression2` .</span><span class="sxs-lookup"><span data-stu-id="9ea22-116">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="9ea22-117">[Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="9ea22-117">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="9ea22-118">[/İşleci (Visual Basic)](floating-point-division-operator.md) , kesir bölümünde kalanı tutan tam bölümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ea22-118">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ea22-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ea22-119">Remarks</span></span>  

 <span data-ttu-id="9ea22-120">Bölme işlemini gerçekleştirmeden önce, Visual Basic herhangi bir kayan nokta sayısal ifadesini öğesine dönüştürmeye çalışır `Long` .</span><span class="sxs-lookup"><span data-stu-id="9ea22-120">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="9ea22-121">`Option Strict`İse `On` , bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="9ea22-121">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="9ea22-122">`Option Strict`İse `Off` , <xref:System.OverflowException> değer [uzun veri türü](../data-types/long-data-type.md)aralığının dışında ise mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9ea22-122">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../data-types/long-data-type.md).</span></span> <span data-ttu-id="9ea22-123">Dönüşümü, `Long` *banker 'in yuvarlanması* için de tabidir.</span><span class="sxs-lookup"><span data-stu-id="9ea22-123">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="9ea22-124">Daha fazla bilgi için [tür dönüştürme işlevlerinde](../functions/type-conversion-functions.md)"kesirli parçalar" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9ea22-124">For more information, see "Fractional Parts" in [Type Conversion Functions](../functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="9ea22-125">`expression1`Ya da `expression2` [hiçbir şey](../nothing.md)değerlendirilirse, sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9ea22-125">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="9ea22-126">Sıfıra bölme denendi</span><span class="sxs-lookup"><span data-stu-id="9ea22-126">Attempted Division by Zero</span></span>  

 <span data-ttu-id="9ea22-127">`expression2`Sıfır olarak değerlendirilirse, `\` işleci bir <xref:System.DivideByZeroException> özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="9ea22-127">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="9ea22-128">Bu, işlenenlerin tüm sayısal veri türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9ea22-128">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ea22-129">`\`İşleç *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9ea22-129">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9ea22-130">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9ea22-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9ea22-131">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9ea22-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ea22-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ea22-132">Example</span></span>  

 <span data-ttu-id="9ea22-133">Aşağıdaki örnek, `\` tam sayı bölümü yapmak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ea22-133">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="9ea22-134">Sonuç, geri kalan atılan iki işlenenin tamsayı bölümünü temsil eden bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="9ea22-134">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="9ea22-135">Yukarıdaki örnekteki ifadeler sırasıyla 2, 3, 33 ve-22 değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ea22-135">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea22-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ea22-136">See also</span></span>

- [<span data-ttu-id="9ea22-137">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="9ea22-137">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="9ea22-138">/İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ea22-138">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="9ea22-139">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="9ea22-139">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="9ea22-140">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="9ea22-140">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="9ea22-141">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="9ea22-141">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="9ea22-142">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="9ea22-142">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="9ea22-143">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="9ea22-143">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
