---
title: "* İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 450d728e44ef5639d75369e05b47cb3009b4d769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="dc795-102">\* İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc795-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="dc795-103">İki sayıyı çarpar.</span><span class="sxs-lookup"><span data-stu-id="dc795-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc795-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc795-104">Syntax</span></span>  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="dc795-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="dc795-105">Parts</span></span>  
  
|<span data-ttu-id="dc795-106">Terim</span><span class="sxs-lookup"><span data-stu-id="dc795-106">Term</span></span>|<span data-ttu-id="dc795-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="dc795-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="dc795-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="dc795-108">Required.</span></span> <span data-ttu-id="dc795-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="dc795-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="dc795-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="dc795-110">Required.</span></span> <span data-ttu-id="dc795-111">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="dc795-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="dc795-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="dc795-112">Result</span></span>  
 <span data-ttu-id="dc795-113">Sonuç ürünüdür `number1` ve `number2`.</span><span class="sxs-lookup"><span data-stu-id="dc795-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="dc795-114">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="dc795-114">Supported Types</span></span>  
 <span data-ttu-id="dc795-115">İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türler ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc795-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc795-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc795-116">Remarks</span></span>  
 <span data-ttu-id="dc795-117">Sonuç veri türü işlenen türlerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc795-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="dc795-118">Aşağıdaki tabloda, sonuç veri türü nasıl belirlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc795-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="dc795-119">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="dc795-119">Operand data types</span></span>|<span data-ttu-id="dc795-120">Sonuç veri türü</span><span class="sxs-lookup"><span data-stu-id="dc795-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="dc795-121">Her iki ifadelerini tam sayı veri türleri ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md), [kısa](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [uzun](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="dc795-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="dc795-122">Veri türleri için uygun bir sayısal veri türü `number1` ve `number2`.</span><span class="sxs-lookup"><span data-stu-id="dc795-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="dc795-123">"Tamsayı aritmetiğini" tablolarda bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="dc795-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="dc795-124">Her iki ifadelerini [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="dc795-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="dc795-125">Her iki ifadelerini [tek](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="dc795-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="dc795-126">Kayan nokta veri türü ya da ifadesidir (`Single` veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md)) ancak ikisini `Single` (Not `Decimal` bir kayan nokta veri türü değil)</span><span class="sxs-lookup"><span data-stu-id="dc795-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="dc795-127">Bir ifade değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="dc795-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="dc795-128">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="dc795-128">Overloading</span></span>  
 <span data-ttu-id="dc795-129">`*` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dc795-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="dc795-130">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="dc795-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="dc795-131">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="dc795-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc795-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc795-132">Example</span></span>  
 <span data-ttu-id="dc795-133">Bu örnekte `*` iki sayının Çarp işleci.</span><span class="sxs-lookup"><span data-stu-id="dc795-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="dc795-134">Sonuç iki işlenen ürünüdür.</span><span class="sxs-lookup"><span data-stu-id="dc795-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dc795-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc795-135">See Also</span></span>  
 [<span data-ttu-id="dc795-136">\* = İşleci</span><span class="sxs-lookup"><span data-stu-id="dc795-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [<span data-ttu-id="dc795-137">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="dc795-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="dc795-138">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="dc795-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="dc795-139">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="dc795-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="dc795-140">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="dc795-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
