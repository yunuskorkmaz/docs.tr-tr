---
title: '* İşleç (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: b5b601c7604cb7ce1afaebc98b2157634a77fda4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701086"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9e864-102">\* İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e864-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="9e864-103">İki sayıyı çarpar.</span><span class="sxs-lookup"><span data-stu-id="9e864-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e864-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e864-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="9e864-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9e864-105">Parts</span></span>  
  
|<span data-ttu-id="9e864-106">Terim</span><span class="sxs-lookup"><span data-stu-id="9e864-106">Term</span></span>|<span data-ttu-id="9e864-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="9e864-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="9e864-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9e864-108">Required.</span></span> <span data-ttu-id="9e864-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9e864-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="9e864-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9e864-110">Required.</span></span> <span data-ttu-id="9e864-111">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9e864-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="9e864-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="9e864-112">Result</span></span>  
 <span data-ttu-id="9e864-113">Sonuç `number1` ve `number2` ' in ürünüdür.</span><span class="sxs-lookup"><span data-stu-id="9e864-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="9e864-114">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="9e864-114">Supported Types</span></span>  
 <span data-ttu-id="9e864-115">İşaretsiz ve kayan nokta türleri ve `Decimal` dahil olmak üzere tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="9e864-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e864-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e864-116">Remarks</span></span>  
 <span data-ttu-id="9e864-117">Sonucun veri türü, işlenenlerinin türlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e864-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="9e864-118">Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e864-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="9e864-119">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="9e864-119">Operand data types</span></span>|<span data-ttu-id="9e864-120">Sonuç veri türü</span><span class="sxs-lookup"><span data-stu-id="9e864-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="9e864-121">Her iki ifade de İntegral veri türleridir[(SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [ushort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="9e864-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="9e864-122">@No__t-0 ve `number2` veri türleri için uygun bir sayısal veri türü.</span><span class="sxs-lookup"><span data-stu-id="9e864-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="9e864-123">[Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="9e864-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="9e864-124">Her iki ifade de [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="9e864-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="9e864-125">Her iki ifade de [tek](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="9e864-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="9e864-126">Her iki ifade de bir kayan nokta veri türüdür (`Single` veya [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)), ancak `Single` değil (Not `Decimal` kayan nokta veri türü değildir)</span><span class="sxs-lookup"><span data-stu-id="9e864-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="9e864-127">Bir ifade [hiçbir şey](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9e864-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9e864-128">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="9e864-128">Overloading</span></span>  
 <span data-ttu-id="9e864-129">@No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9e864-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9e864-130">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9e864-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9e864-131">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9e864-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e864-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e864-132">Example</span></span>  
 <span data-ttu-id="9e864-133">Bu örnek iki sayıyı çarpmak için `*` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e864-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="9e864-134">Sonuç iki işlenenin ürünüdür.</span><span class="sxs-lookup"><span data-stu-id="9e864-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9e864-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e864-135">See also</span></span>

- [<span data-ttu-id="9e864-136">\*= İşleci</span><span class="sxs-lookup"><span data-stu-id="9e864-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="9e864-137">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="9e864-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="9e864-138">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="9e864-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9e864-139">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="9e864-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9e864-140">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="9e864-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
