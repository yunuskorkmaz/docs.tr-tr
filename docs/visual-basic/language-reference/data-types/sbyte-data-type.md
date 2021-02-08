---
description: 'Daha fazla bilgi edinin: SByte veri türü (Visual Basic)'
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
ms.openlocfilehash: e6e314a34469083433289c0fff9b404d4549824d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792173"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="c17ac-103">SByte veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c17ac-103">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="c17ac-104">-128 ile 127 arasında bir değer olan işaretli 8 bit (1 baytlık) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="c17ac-104">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="c17ac-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c17ac-105">Remarks</span></span>

<span data-ttu-id="c17ac-106">`SByte`Veri türünü, tam veri genişliğinin `Integer` veya hatta yarı veri genişliğinin gerekli olmadığı tamsayı değerler içerecek şekilde kullanın `Short` .</span><span class="sxs-lookup"><span data-stu-id="c17ac-106">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="c17ac-107">Bazı durumlarda, ortak dil çalışma zamanı `SByte` değişkenlerinizi birbirine yakından paketlenebilir ve bellek tüketimini kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="c17ac-107">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="c17ac-108">Varsayılan değeri 0 ' `SByte` dır.</span><span class="sxs-lookup"><span data-stu-id="c17ac-108">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="c17ac-109">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="c17ac-109">Literal assignments</span></span>

<span data-ttu-id="c17ac-110">Bir `SByte` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c17ac-110">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="c17ac-111">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen-102 arasındaki tamsayılar `SByte` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="c17ac-111">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="c17ac-112">Bu örnek, `/removeintchecks` derleyici anahtarıyla derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c17ac-112">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="c17ac-113">Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c17ac-113">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="c17ac-114">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="c17ac-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c17ac-115">Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c17ac-115">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="c17ac-116">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c17ac-116">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="c17ac-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c17ac-117">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="c17ac-118">Tamsayı sabit değeri aralığın dışındaysa `SByte` (diğer bir deyişle, değerinden küçükse <xref:System.SByte.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.SByte.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="c17ac-118">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="c17ac-119">Bir tamsayı değişmez değeri hiç sonekine sahip olmadığında, bir [tamsayı](integer-data-type.md) çıkarsanın.</span><span class="sxs-lookup"><span data-stu-id="c17ac-119">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="c17ac-120">Tamsayı sabit değeri tür aralığının dışındaysa `Integer` , [uzun](long-data-type.md) bir değer algılanır.</span><span class="sxs-lookup"><span data-stu-id="c17ac-120">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="c17ac-121">Diğer bir deyişle, önceki örneklerde sayısal değişmez değerler `0x9A` ve `0b10011010` 156 değeri olan 32 bitlik işaretli tamsayılar olarak yorumlanmaktadır <xref:System.SByte.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c17ac-121">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c17ac-122">Öğesine ondalık olmayan bir tamsayı atayan bu gibi bir kodu başarıyla derlemek için aşağıdakilerden birini yapabilirsiniz `SByte` :</span><span class="sxs-lookup"><span data-stu-id="c17ac-122">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="c17ac-123">Derleyici anahtarıyla derleme yaparak tamsayı sınırları denetimlerini devre dışı bırakın `/removeintchecks` .</span><span class="sxs-lookup"><span data-stu-id="c17ac-123">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="c17ac-124">Öğesine atamak istediğiniz sabit değeri açıkça tanımlamak için bir [tür karakteri](../../programming-guide/language-features/data-types/type-characters.md) kullanın `SByte` .</span><span class="sxs-lookup"><span data-stu-id="c17ac-124">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="c17ac-125">Aşağıdaki örnek bir için negatif bir değişmez `Short` değer atar `SByte` .</span><span class="sxs-lookup"><span data-stu-id="c17ac-125">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="c17ac-126">Negatif sayılar için, sayısal sabit değerin yüksek sıralı sözcüğünün yüksek sıralı bitinin ayarlanmış olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c17ac-126">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="c17ac-127">Örneğimizde, bu değer değişmez değerin 15 ' i olur `Short` .</span><span class="sxs-lookup"><span data-stu-id="c17ac-127">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="c17ac-128">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="c17ac-128">Programming tips</span></span>

- <span data-ttu-id="c17ac-129">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="c17ac-129">**CLS Compliance.**</span></span> <span data-ttu-id="c17ac-130">`SByte`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.</span><span class="sxs-lookup"><span data-stu-id="c17ac-130">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="c17ac-131">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="c17ac-131">**Widening.**</span></span> <span data-ttu-id="c17ac-132">`SByte`Veri türü widens,,,, `Short` `Integer` `Long` `Decimal` `Single` , ve `Double` .</span><span class="sxs-lookup"><span data-stu-id="c17ac-132">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="c17ac-133">Bu, `SByte` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c17ac-133">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="c17ac-134">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="c17ac-134">**Type Characters.**</span></span> <span data-ttu-id="c17ac-135">`SByte` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="c17ac-135">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="c17ac-136">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="c17ac-136">**Framework Type.**</span></span> <span data-ttu-id="c17ac-137">.NET Framework karşılık gelen tür <xref:System.SByte?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="c17ac-137">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="c17ac-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c17ac-138">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="c17ac-139">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="c17ac-139">Data Types</span></span>](index.md)
- [<span data-ttu-id="c17ac-140">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c17ac-140">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="c17ac-141">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="c17ac-141">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="c17ac-142">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c17ac-142">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="c17ac-143">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c17ac-143">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="c17ac-144">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c17ac-144">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="c17ac-145">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c17ac-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
