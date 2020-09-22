---
title: '* Operatör'
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
ms.openlocfilehash: 7038fef4258d190b726a851b26f2a2840ff3c0ea
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873373"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="2a3cf-102">\* İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a3cf-102">\* Operator (Visual Basic)</span></span>

<span data-ttu-id="2a3cf-103">İki sayıyı çarpar.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a3cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a3cf-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="2a3cf-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2a3cf-105">Parts</span></span>  
  
|<span data-ttu-id="2a3cf-106">Terim</span><span class="sxs-lookup"><span data-stu-id="2a3cf-106">Term</span></span>|<span data-ttu-id="2a3cf-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="2a3cf-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="2a3cf-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-108">Required.</span></span> <span data-ttu-id="2a3cf-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="2a3cf-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-110">Required.</span></span> <span data-ttu-id="2a3cf-111">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="2a3cf-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="2a3cf-112">Result</span></span>  

 <span data-ttu-id="2a3cf-113">Sonuç, `number1` ve ürünüdür `number2` .</span><span class="sxs-lookup"><span data-stu-id="2a3cf-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="2a3cf-114">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="2a3cf-114">Supported Types</span></span>  

 <span data-ttu-id="2a3cf-115">İmzasız ve kayan nokta türleri de dahil olmak üzere tüm sayısal türler `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="2a3cf-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a3cf-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a3cf-116">Remarks</span></span>  

 <span data-ttu-id="2a3cf-117">Sonucun veri türü, işlenenlerinin türlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="2a3cf-118">Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="2a3cf-119">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="2a3cf-119">Operand data types</span></span>|<span data-ttu-id="2a3cf-120">Sonuç veri türü</span><span class="sxs-lookup"><span data-stu-id="2a3cf-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="2a3cf-121">Her iki ifade de İntegral veri türleridir[(SByte](../data-types/sbyte-data-type.md), [byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [ushort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="2a3cf-121">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="2a3cf-122">Ve veri türleri için uygun bir sayısal veri türü `number1` `number2` .</span><span class="sxs-lookup"><span data-stu-id="2a3cf-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="2a3cf-123">[Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="2a3cf-124">Her iki ifade de [Decimal](../data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="2a3cf-124">Both expressions are [Decimal](../data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="2a3cf-125">Her iki ifade de [tek](../data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="2a3cf-125">Both expressions are [Single](../data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="2a3cf-126">İki ifade de kayan nokta veri türü ( `Single` veya [Double](../data-types/double-data-type.md)), ancak her ikisi birden değil `Single` (Not `Decimal` kayan nokta veri türü değildir)</span><span class="sxs-lookup"><span data-stu-id="2a3cf-126">Either expression is a floating-point data type (`Single` or [Double](../data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="2a3cf-127">Bir ifade [hiçbir şey](../nothing.md)olarak değerlendirilirse, sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-127">If an expression evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2a3cf-128">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="2a3cf-128">Overloading</span></span>  

 <span data-ttu-id="2a3cf-129">`*`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2a3cf-130">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2a3cf-131">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2a3cf-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a3cf-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a3cf-132">Example</span></span>  

 <span data-ttu-id="2a3cf-133">Bu örnek, `*` iki sayıyı çarpmak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="2a3cf-134">Sonuç iki işlenenin ürünüdür.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2a3cf-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a3cf-135">See also</span></span>

- [<span data-ttu-id="2a3cf-136">\* = İşleci</span><span class="sxs-lookup"><span data-stu-id="2a3cf-136">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="2a3cf-137">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="2a3cf-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="2a3cf-138">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="2a3cf-138">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="2a3cf-139">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="2a3cf-139">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="2a3cf-140">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="2a3cf-140">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
