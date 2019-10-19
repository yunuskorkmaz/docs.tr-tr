---
title: ULong Veri Türü (Visual Basic)
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
ms.openlocfilehash: 19a75f056436b858a22588d7ac5f37df5dd326f2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583121"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="4fd07-102">ULong veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fd07-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="4fd07-103">0 ila 18446744073709551615 (1,84 ' den fazla 10 ^ 19 ' den fazla) değeri değişen işaretsiz 64 bitlik (8 baytlık) tamsayıları barındırır.</span><span class="sxs-lookup"><span data-stu-id="4fd07-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="4fd07-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fd07-104">Remarks</span></span>

<span data-ttu-id="4fd07-105">@No__t_1 için çok büyük olan ikili verileri veya en büyük olası işaretsiz tamsayı değerlerini içeren `ULong` veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="4fd07-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="4fd07-106">@No__t_0 varsayılan değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="4fd07-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="4fd07-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="4fd07-107">Literal assignments</span></span>

<span data-ttu-id="4fd07-108">Bir `ULong` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fd07-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="4fd07-109">Tamsayı sabit değeri `ULong` aralığının dışındaysa (yani, <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya <xref:System.UInt64.MaxValue?displayProperty=nameWithType> değerinden daha küçükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="4fd07-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="4fd07-110">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 7.934.076.125 'e eşit tamsayılar `ULong` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="4fd07-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="4fd07-111">Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4fd07-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="4fd07-112">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="4fd07-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="4fd07-113">Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_` alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fd07-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="4fd07-114">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fd07-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="4fd07-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4fd07-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="4fd07-116">Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `ULong` veri türünü belirtmek için `UL` ya da `ul` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4fd07-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="4fd07-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="4fd07-117">Programming tips</span></span>

- <span data-ttu-id="4fd07-118">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="4fd07-118">**Negative Numbers.**</span></span> <span data-ttu-id="4fd07-119">@No__t_0 işaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="4fd07-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="4fd07-120">@No__t_1 türü değerlendirilen bir ifadede birli eksi (`-`) işlecini kullanırsanız, Visual Basic ifadeyi önce `Decimal` dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="4fd07-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="4fd07-121">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="4fd07-121">**CLS Compliance.**</span></span> <span data-ttu-id="4fd07-122">@No__t_0 veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.</span><span class="sxs-lookup"><span data-stu-id="4fd07-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="4fd07-123">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="4fd07-123">**Interop Considerations.**</span></span> <span data-ttu-id="4fd07-124">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, `ulong` gibi türlerin diğer ortamlarda farklı bir veri genişliğine (32 bit) sahip olabileceğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="4fd07-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="4fd07-125">Böyle bir bileşene 32 bitlik bir bağımsız değişken geçirıyorsanız, bunu yönetilen Visual Basic kodunuzda `ULong` yerine `UInteger` olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="4fd07-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="4fd07-126">Ayrıca, Otomasyon Windows 95, Windows 98, Windows ME veya Windows 2000 üzerinde 64 bit tamsayıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4fd07-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="4fd07-127">Bu platformlarda bir Otomasyon bileşenine Visual Basic `ULong` bağımsız değişkeni geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fd07-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="4fd07-128">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="4fd07-128">**Widening.**</span></span> <span data-ttu-id="4fd07-129">@No__t_0 veri türü `Decimal`, `Single` ve `Double` için.</span><span class="sxs-lookup"><span data-stu-id="4fd07-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="4fd07-130">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `ULong` bu türlerden birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4fd07-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="4fd07-131">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="4fd07-131">**Type Characters.**</span></span> <span data-ttu-id="4fd07-132">Değişmez değer türü karakterlerinin bir hazır `UL` eklenmesi, `ULong` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="4fd07-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="4fd07-133">`ULong` tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="4fd07-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="4fd07-134">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="4fd07-134">**Framework Type.**</span></span> <span data-ttu-id="4fd07-135">.NET Framework karşılık gelen tür <xref:System.UInt64?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="4fd07-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fd07-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fd07-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="4fd07-137">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="4fd07-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="4fd07-138">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4fd07-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="4fd07-139">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="4fd07-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="4fd07-140">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="4fd07-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="4fd07-141">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4fd07-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
