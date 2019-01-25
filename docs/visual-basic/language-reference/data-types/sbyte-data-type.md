---
title: SByte Veri Türü (Visual Basic)
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: 1da5de4971928ca23a23c4dcfc5f338c4d7a3875
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719579"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="6b382-102">SByte veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b382-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="6b382-103">Değeri -128 ile 127 arasında 8-bit (1-bayt) tamsayıları tutar imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="6b382-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b382-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b382-104">Remarks</span></span>

<span data-ttu-id="6b382-105">Kullanım `SByte` veri türü, tam veri genişliği gerektirmeyen tamsayı değerler içerecek şekilde `Integer` ve hatta yarım veri genişliği `Short`.</span><span class="sxs-lookup"><span data-stu-id="6b382-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="6b382-106">Bazı durumlarda, ortak dil çalışma zamanı paketi mümkün olabilir, `SByte` değişkenleri yakından birlikte ve bellek tüketimi.</span><span class="sxs-lookup"><span data-stu-id="6b382-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="6b382-107">Varsayılan değer olan `SByte` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="6b382-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="6b382-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="6b382-108">Literal assignments</span></span>
  
<span data-ttu-id="6b382-109">Bildirmek ve başlatmak bir `SByte` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren).</span><span class="sxs-lookup"><span data-stu-id="6b382-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="6b382-110">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen-102 eşit ve ikili sabit değerler atanır `SByte` değerleri.</span><span class="sxs-lookup"><span data-stu-id="6b382-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="6b382-111">Bu örnek ile derleme gerektirir `/removeintchecks` derleyici anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6b382-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> <span data-ttu-id="6b382-112">Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6b382-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="6b382-113">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="6b382-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="6b382-114">Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="6b382-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

<span data-ttu-id="6b382-115">Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="6b382-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="6b382-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6b382-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="6b382-117">Tamsayı sabit değeri aralığının dışında ise `SByte` (diğer bir deyişle, bu ise kısa <xref:System.SByte.MinValue?displayProperty=nameWithType> veya ondan <xref:System.SByte.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="6b382-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="6b382-118">Tamsayı sabit değeri, sonek varsa bir [tamsayı](integer-data-type.md) algılanır.</span><span class="sxs-lookup"><span data-stu-id="6b382-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="6b382-119">Tamsayı sabit değeri aralığının dışında ise `Integer` türü, bir [uzun](long-data-type.md) algılanır.</span><span class="sxs-lookup"><span data-stu-id="6b382-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="6b382-120">Bu, önceki örneklerde, sayısal değişmez değerleri anlamına `0x9A` ve `0b10011010` aşıyor 156, değerini 32-bit imzalı tamsayı olarak yorumlanır <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b382-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6b382-121">Başarıyla bir ondalık olmayan tamsayı olarak atar. Bu kodu derlemek için bir `SByte`, aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6b382-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="6b382-122">Tamsayı sınırları denetimlerini ile derleme tarafından devre dışı `/removeintchecks` derleyici anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6b382-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="6b382-123">Kullanım bir [türü karakteri](../../programming-guide/language-features/data-types/type-characters.md) atamak istediğiniz değişmez değer açıkça tanımlamak için `SByte`.</span><span class="sxs-lookup"><span data-stu-id="6b382-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="6b382-124">Aşağıdaki örnek, negatif bir sabit değer atar `Short` değerini bir `SByte`.</span><span class="sxs-lookup"><span data-stu-id="6b382-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="6b382-125">Negatif sayılar için dikkat edin, yüksek sıralı bitten yüksek düzeyli Word sayısal sabit değerinin ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b382-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="6b382-126">Bizim örneğimizde söz konusu olduğunda bu bit sabit değerinin 15 `Short` değeri.</span><span class="sxs-lookup"><span data-stu-id="6b382-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="6b382-127">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="6b382-127">Programming tips</span></span>
  
-   <span data-ttu-id="6b382-128">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="6b382-128">**CLS Compliance.**</span></span> <span data-ttu-id="6b382-129">`SByte` Veri türü değil parçası [ortak dil belirtimi](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), böylece onu kullanan bileşen CLS uyumlu kod kullanamıyor.</span><span class="sxs-lookup"><span data-stu-id="6b382-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

-   <span data-ttu-id="6b382-130">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="6b382-130">**Widening.**</span></span> <span data-ttu-id="6b382-131">`SByte` Widens veri türü için `Short`, `Integer`, `Long`, `Decimal`, `Single`, ve `Double`.</span><span class="sxs-lookup"><span data-stu-id="6b382-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="6b382-132">Yani dönüştürebilirsiniz `SByte` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="6b382-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="6b382-133">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="6b382-133">**Type Characters.**</span></span> <span data-ttu-id="6b382-134">`SByte` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="6b382-134">`SByte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="6b382-135">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="6b382-135">**Framework Type.**</span></span> <span data-ttu-id="6b382-136">.NET Framework içinde karşılık gelen türü <xref:System.SByte?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="6b382-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6b382-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b382-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="6b382-138">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="6b382-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="6b382-139">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6b382-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="6b382-140">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="6b382-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="6b382-141">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="6b382-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="6b382-142">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="6b382-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="6b382-143">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="6b382-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="6b382-144">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="6b382-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
