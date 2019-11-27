---
title: UInteger Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343894"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="d7bc6-102">UInteger veri türü</span><span class="sxs-lookup"><span data-stu-id="d7bc6-102">UInteger data type</span></span>

<span data-ttu-id="d7bc6-103">0 ile 4.294.967.295 arasında değer değişen işaretsiz 32 bitlik (4 baytlık) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7bc6-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7bc6-104">Remarks</span></span>

<span data-ttu-id="d7bc6-105">`UInteger` veri türü en etkili veri genişliğinde en büyük işaretsiz değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="d7bc6-106">`UInteger` varsayılan değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="d7bc6-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="d7bc6-107">Literal assignments</span></span>

<span data-ttu-id="d7bc6-108">Bir `UInteger` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="d7bc6-109">Tamsayı sabit değeri `UInteger` aralığının dışındaysa (yani, <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya <xref:System.UInt32.MaxValue?displayProperty=nameWithType>değerinden daha küçükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="d7bc6-110">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 3.000.000.000 'e eşit tamsayılar `UInteger` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="d7bc6-111">Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="d7bc6-112">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="d7bc6-113">Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_`alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="d7bc6-114">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="d7bc6-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d7bc6-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="d7bc6-116">Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `UInteger` veri türünü belirtmek için `UI` ya da `ui` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="d7bc6-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="d7bc6-117">Programming tips</span></span>

<span data-ttu-id="d7bc6-118">`UInteger` ve `Integer` veri türleri, daha küçük tamsayı türleri (`UShort`, `Short`, `Byte`ve `SByte`), daha az sayıda bit kullansa bile yükleme, depolama ve getirme için daha fazla zaman alan bir 32 bitlik işlemcide en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="d7bc6-119">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="d7bc6-119">**Negative Numbers.**</span></span> <span data-ttu-id="d7bc6-120">`UInteger` işaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="d7bc6-121">`UInteger`türü değerlendirilen bir ifadede birli eksi (`-`) işlecini kullanırsanız, Visual Basic ifadeyi önce `Long` dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="d7bc6-122">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="d7bc6-122">**CLS Compliance.**</span></span> <span data-ttu-id="d7bc6-123">`UInteger` veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="d7bc6-124">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="d7bc6-124">**Interop Considerations.**</span></span> <span data-ttu-id="d7bc6-125">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, `uint` gibi türlerin diğer ortamlarda farklı bir veri genişliğine (16 bit) sahip olabileceğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="d7bc6-126">Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu yönetilen Visual Basic kodunuzda `UInteger` yerine `UShort` olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="d7bc6-127">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="d7bc6-127">**Widening.**</span></span> <span data-ttu-id="d7bc6-128">`UInteger` veri türü `Long`, `ULong`, `Decimal`, `Single`ve `Double`için.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="d7bc6-129">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `UInteger` bu türlerden birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="d7bc6-130">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="d7bc6-130">**Type Characters.**</span></span> <span data-ttu-id="d7bc6-131">Değişmez değer türü karakterlerinin bir hazır `UI` eklenmesi, `UInteger` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="d7bc6-132">`UInteger` tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="d7bc6-133">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="d7bc6-133">**Framework Type.**</span></span> <span data-ttu-id="d7bc6-134">.NET Framework karşılık gelen tür <xref:System.UInt32?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7bc6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7bc6-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="d7bc6-136">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="d7bc6-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d7bc6-137">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d7bc6-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d7bc6-138">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="d7bc6-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="d7bc6-139">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="d7bc6-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="d7bc6-140">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="d7bc6-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
