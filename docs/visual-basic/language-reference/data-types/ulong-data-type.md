---
title: ULong Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: ee9297ae917345d44d8e630bd09beea2245b56da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415524"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="1ec99-102">ULong veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ec99-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="1ec99-103">0 ila 18446744073709551615 (1,84 ' den fazla 10 ^ 19 ' den fazla) değeri değişen işaretsiz 64 bitlik (8 baytlık) tamsayıları barındırır.</span><span class="sxs-lookup"><span data-stu-id="1ec99-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="1ec99-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ec99-104">Remarks</span></span>

<span data-ttu-id="1ec99-105">`ULong`Veri türünü, için çok büyük olan ikili verileri `UInteger` veya en büyük olası işaretsiz tamsayı değerlerini içerecek şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ec99-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="1ec99-106">Varsayılan değeri 0 ' `ULong` dır.</span><span class="sxs-lookup"><span data-stu-id="1ec99-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="1ec99-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="1ec99-107">Literal assignments</span></span>

<span data-ttu-id="1ec99-108">Bir `ULong` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ec99-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="1ec99-109">Tamsayı sabit değeri aralığın dışındaysa `ULong` (diğer bir deyişle, değerinden küçükse <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.UInt64.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="1ec99-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="1ec99-110">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 7.934.076.125 'e eşit tamsayılar `ULong` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="1ec99-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="1ec99-111">Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ec99-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="1ec99-112">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="1ec99-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="1ec99-113">Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ec99-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="1ec99-114">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ec99-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="1ec99-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="1ec99-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="1ec99-116">Sayısal değişmez değerler, `UL` `ul` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de veya [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir `ULong` .</span><span class="sxs-lookup"><span data-stu-id="1ec99-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="1ec99-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="1ec99-117">Programming tips</span></span>

- <span data-ttu-id="1ec99-118">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="1ec99-118">**Negative Numbers.**</span></span> <span data-ttu-id="1ec99-119">`ULong`İşaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="1ec99-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="1ec99-120">`-`Türü değerlendirilen bir ifadede birli eksi () işlecini kullanırsanız `ULong` , Visual Basic ifadeyi `Decimal` önce dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1ec99-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="1ec99-121">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="1ec99-121">**CLS Compliance.**</span></span> <span data-ttu-id="1ec99-122">`ULong`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.</span><span class="sxs-lookup"><span data-stu-id="1ec99-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="1ec99-123">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="1ec99-123">**Interop Considerations.**</span></span> <span data-ttu-id="1ec99-124">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimsiz değilseniz, gibi türlerin `ulong` diğer ortamlarda farklı bir veri genişliğine (32 bit) sahip olabileceğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1ec99-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="1ec99-125">Böyle bir bileşene 32 bitlik bir bağımsız değişken geçiriyorsa, bunu `UInteger` `ULong` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="1ec99-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="1ec99-126">Ayrıca, Otomasyon Windows 95, Windows 98, Windows ME veya Windows 2000 üzerinde 64 bit tamsayıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1ec99-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="1ec99-127">`ULong`Bu platformlarda bir Otomasyon bileşenine Visual Basic bağımsız değişken geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ec99-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="1ec99-128">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="1ec99-128">**Widening.**</span></span> <span data-ttu-id="1ec99-129">`ULong`, Ve için widens veri `Decimal` türü `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="1ec99-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="1ec99-130">Bu, `ULong` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1ec99-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="1ec99-131">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="1ec99-131">**Type Characters.**</span></span> <span data-ttu-id="1ec99-132">Değişmez değer türü karakterlerinin `UL` bir sabit değere eklenmesi, `ULong` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="1ec99-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="1ec99-133">`ULong`tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="1ec99-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="1ec99-134">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="1ec99-134">**Framework Type.**</span></span> <span data-ttu-id="1ec99-135">.NET Framework karşılık gelen tür <xref:System.UInt64?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="1ec99-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ec99-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ec99-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="1ec99-137">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="1ec99-137">Data Types</span></span>](index.md)
- [<span data-ttu-id="1ec99-138">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1ec99-138">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="1ec99-139">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="1ec99-139">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="1ec99-140">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="1ec99-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="1ec99-141">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="1ec99-141">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
