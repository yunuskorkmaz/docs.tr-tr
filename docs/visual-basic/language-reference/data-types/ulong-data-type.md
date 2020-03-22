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
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400703"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="4a084-102">ULong veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a084-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="4a084-103">0 ile 18.446.744.073.709.551.615 (1,84 çarpı 10 ^ 19) arasında değişen imzasız 64 bit (8 bayt) tümsedoları tutar.</span><span class="sxs-lookup"><span data-stu-id="4a084-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="4a084-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a084-104">Remarks</span></span>

<span data-ttu-id="4a084-105">`ULong` Veri türünü, olası en büyük `UInteger`imzasız tümsado değeri için çok büyük ikili veriler veya içerecek şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a084-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="4a084-106">Varsayılan değeri `ULong` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="4a084-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="4a084-107">Gerçek atamalar</span><span class="sxs-lookup"><span data-stu-id="4a084-107">Literal assignments</span></span>

<span data-ttu-id="4a084-108">Bir `ULong` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a084-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="4a084-109">Tamsayı literal aralığının `ULong` dışında ysa (yani, daha az <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya daha <xref:System.UInt64.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="4a084-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="4a084-110">Aşağıdaki örnekte, ondalık, heksadesibel ve ikili edebi değerler olarak temsil edilen 7.934.076.125'e `ULong` eşit tamsayılar değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="4a084-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="4a084-111">`&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="4a084-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="4a084-112">Ondalık edebi hiçbir önek var.</span><span class="sxs-lookup"><span data-stu-id="4a084-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="4a084-113">Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a084-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="4a084-114">Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a084-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="4a084-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="4a084-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="4a084-116">Sayısal literals, aşağıdaki `UL` örnekte `ul` görüldüğü `ULong` gibi, veri türünü ifade etmek için veya [türü karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4a084-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="4a084-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="4a084-117">Programming tips</span></span>

- <span data-ttu-id="4a084-118">**Negatif Sayılar.**</span><span class="sxs-lookup"><span data-stu-id="4a084-118">**Negative Numbers.**</span></span> <span data-ttu-id="4a084-119">İmzalanmamış bir tür `ULong` olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="4a084-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="4a084-120">Unary eksi (`-`) işleci, yazmayı `ULong`değerlendiren bir ifadeüzerinde kullanırsanız, `Decimal` Visual Basic ifadeyi önce dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="4a084-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="4a084-121">**CLS Uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="4a084-121">**CLS Compliance.**</span></span> <span data-ttu-id="4a084-122">Veri `ULong` türü Ortak Dil [Belirtimi'nin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketemez.</span><span class="sxs-lookup"><span data-stu-id="4a084-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="4a084-123">**Interop Hususlar.**</span><span class="sxs-lookup"><span data-stu-id="4a084-123">**Interop Considerations.**</span></span> <span data-ttu-id="4a084-124">.NET Framework için yazılmayan bileşenlerle (örneğin Otomasyon veya COM nesneleri) bir araya `ulong` geliyorsanız, diğer ortamlarda farklı veri genişliğine (32 bit) sahip olabilecek türler olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4a084-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="4a084-125">Böyle bir bileşene 32 bitlik bir bağımsız değişken `UInteger` geçiyorsanız, bunu yönetilen Visual Basic kodunuz yerine `ULong` olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="4a084-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="4a084-126">Ayrıca, Otomasyon Windows 95, Windows 98, Windows ME veya Windows 2000'deki 64 bit'lik tümseleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4a084-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="4a084-127">Visual Basic `ULong` bağımsız değişkenini bu platformlardaki bir Otomasyon bileşenine geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a084-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="4a084-128">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="4a084-128">**Widening.**</span></span> <span data-ttu-id="4a084-129">Veri `ULong` türü `Decimal`, , `Single`ve `Double`.</span><span class="sxs-lookup"><span data-stu-id="4a084-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="4a084-130">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `ULong` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4a084-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="4a084-131">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="4a084-131">**Type Characters.**</span></span> <span data-ttu-id="4a084-132">Gerçek türdeki `UL` karakterleri `ULong` bir edebi aygıta ekler, onu veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="4a084-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="4a084-133">`ULong`tanımlayıcı türü karakteri yoktur.</span><span class="sxs-lookup"><span data-stu-id="4a084-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="4a084-134">**Çerçeve Türü.**</span><span class="sxs-lookup"><span data-stu-id="4a084-134">**Framework Type.**</span></span> <span data-ttu-id="4a084-135">.NET Framework'de karşılık gelen <xref:System.UInt64?displayProperty=nameWithType> tür yapıdır.</span><span class="sxs-lookup"><span data-stu-id="4a084-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a084-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a084-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="4a084-137">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="4a084-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="4a084-138">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4a084-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="4a084-139">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="4a084-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="4a084-140">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="4a084-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="4a084-141">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4a084-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
