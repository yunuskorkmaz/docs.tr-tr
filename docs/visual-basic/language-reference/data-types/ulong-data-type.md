---
description: 'Daha fazla bilgi edinin: ULong veri türü (Visual Basic)'
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
ms.openlocfilehash: 9082fc9444f0754c60a6aa3f9b58db1d833349b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792095"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="d0f7e-103">ULong veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0f7e-103">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="d0f7e-104">0 ila 18446744073709551615 (1,84 ' den fazla 10 ^ 19 ' den fazla) değeri değişen işaretsiz 64 bitlik (8 baytlık) tamsayıları barındırır.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-104">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="d0f7e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0f7e-105">Remarks</span></span>

<span data-ttu-id="d0f7e-106">`ULong`Veri türünü, için çok büyük olan ikili verileri `UInteger` veya en büyük olası işaretsiz tamsayı değerlerini içerecek şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-106">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="d0f7e-107">Varsayılan değeri 0 ' `ULong` dır.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-107">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="d0f7e-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="d0f7e-108">Literal assignments</span></span>

<span data-ttu-id="d0f7e-109">Bir `ULong` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-109">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="d0f7e-110">Tamsayı sabit değeri aralığın dışındaysa `ULong` (diğer bir deyişle, değerinden küçükse <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.UInt64.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-110">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="d0f7e-111">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 7.934.076.125 'e eşit tamsayılar `ULong` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-111">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="d0f7e-112">Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="d0f7e-113">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="d0f7e-114">Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="d0f7e-115">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="d0f7e-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d0f7e-116">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="d0f7e-117">Sayısal değişmez değerler, `UL` `ul` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de veya [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir `ULong` .</span><span class="sxs-lookup"><span data-stu-id="d0f7e-117">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="d0f7e-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="d0f7e-118">Programming tips</span></span>

- <span data-ttu-id="d0f7e-119">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="d0f7e-119">**Negative Numbers.**</span></span> <span data-ttu-id="d0f7e-120">`ULong`İşaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-120">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="d0f7e-121">`-`Türü değerlendirilen bir ifadede birli eksi () işlecini kullanırsanız `ULong` , Visual Basic ifadeyi `Decimal` önce dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="d0f7e-122">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="d0f7e-122">**CLS Compliance.**</span></span> <span data-ttu-id="d0f7e-123">`ULong`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-123">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="d0f7e-124">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="d0f7e-124">**Interop Considerations.**</span></span> <span data-ttu-id="d0f7e-125">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimsiz değilseniz, gibi türlerin `ulong` diğer ortamlarda farklı bir veri genişliğine (32 bit) sahip olabileceğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="d0f7e-126">Böyle bir bileşene 32 bitlik bir bağımsız değişken geçiriyorsa, bunu `UInteger` `ULong` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-126">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="d0f7e-127">Ayrıca, Otomasyon Windows 95, Windows 98, Windows ME veya Windows 2000 üzerinde 64 bit tamsayıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-127">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="d0f7e-128">`ULong`Bu platformlarda bir Otomasyon bileşenine Visual Basic bağımsız değişken geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-128">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="d0f7e-129">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="d0f7e-129">**Widening.**</span></span> <span data-ttu-id="d0f7e-130">`ULong`, Ve için widens veri `Decimal` türü `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="d0f7e-130">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="d0f7e-131">Bu, `ULong` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d0f7e-131">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="d0f7e-132">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="d0f7e-132">**Type Characters.**</span></span> <span data-ttu-id="d0f7e-133">Değişmez değer türü karakterlerinin `UL` bir sabit değere eklenmesi, `ULong` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-133">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="d0f7e-134">`ULong` tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-134">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="d0f7e-135">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="d0f7e-135">**Framework Type.**</span></span> <span data-ttu-id="d0f7e-136">.NET Framework karşılık gelen tür <xref:System.UInt64?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-136">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0f7e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-137">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="d0f7e-138">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="d0f7e-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="d0f7e-139">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d0f7e-139">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="d0f7e-140">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="d0f7e-140">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="d0f7e-141">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="d0f7e-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="d0f7e-142">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="d0f7e-142">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
