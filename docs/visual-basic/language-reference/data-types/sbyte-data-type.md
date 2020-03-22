---
title: SByte Veri Türü
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
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400794"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="2fbef-102">SByte veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fbef-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="2fbef-103">-128 ile 127 arasında değişen imzalı 8 bit (1 bayt) tümseci tutar.</span><span class="sxs-lookup"><span data-stu-id="2fbef-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fbef-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fbef-104">Remarks</span></span>

<span data-ttu-id="2fbef-105">Tam `SByte` veri genişliği `Integer` ve hatta yarım veri genişliği gerektirmeyen tamsayı değerlerini içerecek şekilde veri türünü kullanın. `Short`</span><span class="sxs-lookup"><span data-stu-id="2fbef-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="2fbef-106">Bazı durumlarda, ortak dil çalışma süresi değişkenlerinizi `SByte` birbirine yakın bir şekilde paketleyebilir ve bellek tüketiminden tasarruf edebilir.</span><span class="sxs-lookup"><span data-stu-id="2fbef-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="2fbef-107">Varsayılan değeri `SByte` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="2fbef-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="2fbef-108">Gerçek atamalar</span><span class="sxs-lookup"><span data-stu-id="2fbef-108">Literal assignments</span></span>

<span data-ttu-id="2fbef-109">Bir `SByte` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fbef-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="2fbef-110">Aşağıdaki örnekte, ondalık, hexadecimal ve ikili literals olarak temsil edilen -102'ye `SByte` eşit tamsayılar değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="2fbef-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="2fbef-111">Bu örnek, `/removeintchecks` derleyici anahtarı yla derlemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2fbef-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="2fbef-112">`&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2fbef-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="2fbef-113">Ondalık edebi hiçbir önek var.</span><span class="sxs-lookup"><span data-stu-id="2fbef-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2fbef-114">Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fbef-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="2fbef-115">Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fbef-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="2fbef-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2fbef-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="2fbef-117">Tamsayı literal aralığının `SByte` dışında ysa (yani, daha az <xref:System.SByte.MinValue?displayProperty=nameWithType> veya daha <xref:System.SByte.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="2fbef-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="2fbef-118">Bir sondanın sonek yoksa, bir [Integer](integer-data-type.md) çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="2fbef-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="2fbef-119">Tamsayı literal `Integer` türünün aralığının dışındaysa, [Uzun](long-data-type.md) çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="2fbef-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="2fbef-120">Bu, önceki örneklerde, sayısal literals `0x9A` ve `0b10011010` 32-bit imzalı tamsayılar 156 değerini aşan, aşan olarak yorumlanır anlamına gelir. <xref:System.SByte.MaxValue?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2fbef-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2fbef-121">Ondalık olmayan bir tamsayıyı bir `SByte`nesle atayan bu gibi kodu başarılı bir şekilde derlemek için aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2fbef-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="2fbef-122">`/removeintchecks` Derleme anahtarıyla derleyerek, tümsesayı sınır denetimlerini devre dışı.</span><span class="sxs-lookup"><span data-stu-id="2fbef-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="2fbef-123">'ye atamak istediğiniz gerçek değeri açıkça tanımlamak için bir tür karakteri kullanın [type character](../../programming-guide/language-features/data-types/type-characters.md) `SByte`</span><span class="sxs-lookup"><span data-stu-id="2fbef-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="2fbef-124">Aşağıdaki örnek, negatif bir `Short` edebi değer `SByte`atar.</span><span class="sxs-lookup"><span data-stu-id="2fbef-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="2fbef-125">Negatif sayılar için sayısal kelimenin yüksek sıralı sözcüğünün yüksek sıralı bitinin ayarlanılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2fbef-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="2fbef-126">Örneğimizde, bu gerçek `Short` değerin bit 15'idir.</span><span class="sxs-lookup"><span data-stu-id="2fbef-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="2fbef-127">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="2fbef-127">Programming tips</span></span>

- <span data-ttu-id="2fbef-128">**CLS Uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="2fbef-128">**CLS Compliance.**</span></span> <span data-ttu-id="2fbef-129">Veri `SByte` türü Ortak Dil [Belirtimi'nin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketemez.</span><span class="sxs-lookup"><span data-stu-id="2fbef-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="2fbef-130">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="2fbef-130">**Widening.**</span></span> <span data-ttu-id="2fbef-131">Veri `SByte` `Short`türü , , `Integer`, `Long` `Decimal` `Single`, ve `Double`.</span><span class="sxs-lookup"><span data-stu-id="2fbef-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="2fbef-132">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `SByte` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2fbef-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="2fbef-133">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="2fbef-133">**Type Characters.**</span></span> <span data-ttu-id="2fbef-134">`SByte`gerçek bir tür karakteri veya tanımlayıcı türü karakteri yoktur.</span><span class="sxs-lookup"><span data-stu-id="2fbef-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="2fbef-135">**Çerçeve Türü.**</span><span class="sxs-lookup"><span data-stu-id="2fbef-135">**Framework Type.**</span></span> <span data-ttu-id="2fbef-136">.NET Framework'de karşılık gelen <xref:System.SByte?displayProperty=nameWithType> tür yapıdır.</span><span class="sxs-lookup"><span data-stu-id="2fbef-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fbef-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fbef-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="2fbef-138">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="2fbef-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="2fbef-139">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2fbef-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="2fbef-140">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="2fbef-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="2fbef-141">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2fbef-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="2fbef-142">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2fbef-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="2fbef-143">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2fbef-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="2fbef-144">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="2fbef-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
