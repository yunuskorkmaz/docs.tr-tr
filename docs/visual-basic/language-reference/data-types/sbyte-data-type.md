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
ms.openlocfilehash: a962200195002858257b92e92e0dd1383d4fb2d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582513"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="d0e30-102">SByte veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0e30-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="d0e30-103">-128 ile 127 arasında bir değer olan işaretli 8 bit (1 baytlık) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="d0e30-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0e30-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0e30-104">Remarks</span></span>

<span data-ttu-id="d0e30-105">@No__t_1 tam veri genişliğine veya `Short` yarı veri genişliğine gerek gerektirmeyen tamsayı değerleri içermesi için `SByte` veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0e30-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="d0e30-106">Bazı durumlarda, ortak dil çalışma zamanı `SByte` değişkenlerinizi birbirine yakından paketlenebilir ve bellek tüketimini kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="d0e30-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="d0e30-107">@No__t_0 varsayılan değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="d0e30-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="d0e30-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="d0e30-108">Literal assignments</span></span>

<span data-ttu-id="d0e30-109">Bir `SByte` değişkeni bir ondalık sabit değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0e30-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="d0e30-110">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen-102 ' e eşit tamsayılar `SByte` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="d0e30-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="d0e30-111">Bu örnek, `/removeintchecks` derleyici anahtarıyla derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0e30-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="d0e30-112">Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0e30-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="d0e30-113">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="d0e30-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="d0e30-114">Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_` alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0e30-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="d0e30-115">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0e30-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="d0e30-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d0e30-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="d0e30-117">Tamsayı sabit değeri `SByte` aralığının dışındaysa (yani, <xref:System.SByte.MinValue?displayProperty=nameWithType> veya <xref:System.SByte.MaxValue?displayProperty=nameWithType> değerinden daha küçükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d0e30-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="d0e30-118">Bir tamsayı değişmez değeri hiç sonekine sahip olmadığında, bir [tamsayı](integer-data-type.md) çıkarsanın.</span><span class="sxs-lookup"><span data-stu-id="d0e30-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="d0e30-119">Tamsayı sabit değeri `Integer` türü aralığının dışındaysa [Long](long-data-type.md) değeri algılanır.</span><span class="sxs-lookup"><span data-stu-id="d0e30-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="d0e30-120">Yani, önceki örneklerde `0x9A` ve `0b10011010` sayısal değişmez değerler 156 değerine sahip 32 bitlik işaretli tamsayılar olarak yorumlanır ve bu da <xref:System.SByte.MaxValue?displayProperty=nameWithType> değerini aşar.</span><span class="sxs-lookup"><span data-stu-id="d0e30-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d0e30-121">Bir `SByte` ondalık olmayan bir tamsayı atayan bu gibi bir kodu başarıyla derlemek için aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0e30-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="d0e30-122">@No__t_0 derleyici anahtarıyla derleme yaparak tamsayı sınırları denetimlerini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="d0e30-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="d0e30-123">@No__t_1 atamak istediğiniz sabit değeri açıkça tanımlamak için bir [tür karakteri](../../programming-guide/language-features/data-types/type-characters.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0e30-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="d0e30-124">Aşağıdaki örnek bir `SByte` negatif değişmez değer `Short` değeri atar.</span><span class="sxs-lookup"><span data-stu-id="d0e30-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="d0e30-125">Negatif sayılar için, sayısal sabit değerin yüksek sıralı sözcüğünün yüksek sıralı bitinin ayarlanmış olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d0e30-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="d0e30-126">Örneğimizde bu, sabit değer `Short` değerinin 15 bit değeridir.</span><span class="sxs-lookup"><span data-stu-id="d0e30-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="d0e30-127">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="d0e30-127">Programming tips</span></span>

- <span data-ttu-id="d0e30-128">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="d0e30-128">**CLS Compliance.**</span></span> <span data-ttu-id="d0e30-129">@No__t_0 veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.</span><span class="sxs-lookup"><span data-stu-id="d0e30-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="d0e30-130">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="d0e30-130">**Widening.**</span></span> <span data-ttu-id="d0e30-131">@No__t_0 veri türü `Short`, `Integer`, `Long`, `Decimal`, `Single` ve `Double` için.</span><span class="sxs-lookup"><span data-stu-id="d0e30-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="d0e30-132">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `SByte` bu türlerden birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d0e30-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="d0e30-133">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="d0e30-133">**Type Characters.**</span></span> <span data-ttu-id="d0e30-134">`SByte` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="d0e30-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="d0e30-135">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="d0e30-135">**Framework Type.**</span></span> <span data-ttu-id="d0e30-136">.NET Framework karşılık gelen tür <xref:System.SByte?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="d0e30-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0e30-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0e30-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="d0e30-138">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="d0e30-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d0e30-139">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d0e30-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d0e30-140">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="d0e30-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="d0e30-141">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d0e30-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="d0e30-142">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d0e30-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="d0e30-143">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d0e30-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="d0e30-144">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="d0e30-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
