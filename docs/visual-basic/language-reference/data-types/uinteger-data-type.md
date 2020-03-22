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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400787"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="01fa2-102">UInteger veri türü</span><span class="sxs-lookup"><span data-stu-id="01fa2-102">UInteger data type</span></span>

<span data-ttu-id="01fa2-103">0 ile 4.294.967.295 arasında değişen imzasız 32 bit (4 bayt) tümsedoları tutar.</span><span class="sxs-lookup"><span data-stu-id="01fa2-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="01fa2-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01fa2-104">Remarks</span></span>

<span data-ttu-id="01fa2-105">Veri `UInteger` türü, en verimli veri genişliğindeki en büyük imzasız değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="01fa2-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="01fa2-106">Varsayılan değeri `UInteger` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="01fa2-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="01fa2-107">Gerçek atamalar</span><span class="sxs-lookup"><span data-stu-id="01fa2-107">Literal assignments</span></span>

<span data-ttu-id="01fa2-108">Bir `UInteger` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01fa2-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="01fa2-109">Tamsayı literal aralığının `UInteger` dışında ysa (yani, daha az <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya daha <xref:System.UInt32.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="01fa2-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="01fa2-110">Aşağıdaki örnekte, ondalık, heksadesibel ve ikili edebi değerler olarak temsil edilen 3.000.000.000'e `UInteger` eşit tamsayılar değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="01fa2-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="01fa2-111">`&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="01fa2-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="01fa2-112">Ondalık edebi hiçbir önek var.</span><span class="sxs-lookup"><span data-stu-id="01fa2-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="01fa2-113">Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01fa2-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="01fa2-114">Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01fa2-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="01fa2-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="01fa2-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="01fa2-116">Sayısal literals, aşağıdaki `UI` örnekte `ui` görüldüğü `UInteger` gibi, veri türünü ifade etmek için veya [türü karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="01fa2-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="01fa2-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="01fa2-117">Programming tips</span></span>

<span data-ttu-id="01fa2-118">Daha `UInteger` `Integer` küçük tamsayı türleri (,`UShort`, `Short` `Byte`, ve `SByte`), daha az bit kullansalar bile, yüklemek, depolamak ve getirmek daha fazla zaman alsalar da, 32 bitlik bir işlemcide en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="01fa2-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="01fa2-119">**Negatif Sayılar.**</span><span class="sxs-lookup"><span data-stu-id="01fa2-119">**Negative Numbers.**</span></span> <span data-ttu-id="01fa2-120">İmzalanmamış bir tür `UInteger` olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="01fa2-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="01fa2-121">Unary eksi (`-`) işleci, yazmayı `UInteger`değerlendiren bir ifadeüzerinde kullanırsanız, `Long` Visual Basic ifadeyi önce dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="01fa2-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="01fa2-122">**CLS Uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="01fa2-122">**CLS Compliance.**</span></span> <span data-ttu-id="01fa2-123">Veri `UInteger` türü Ortak Dil [Belirtimi'nin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketemez.</span><span class="sxs-lookup"><span data-stu-id="01fa2-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="01fa2-124">**Interop Hususlar.**</span><span class="sxs-lookup"><span data-stu-id="01fa2-124">**Interop Considerations.**</span></span> <span data-ttu-id="01fa2-125">.NET Framework için yazılmayan bileşenlerle (örneğin Otomasyon veya COM nesneleri) bir araya `uint` geliyorsanız, diğer ortamlarda farklı veri genişliğine (16 bit) sahip olabilecek türler olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="01fa2-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="01fa2-126">Böyle bir bileşene 16 bitlik bir bağımsız değişken `UShort` geçiyorsanız, bunu yönetilen Visual Basic kodunuz yerine `UInteger` olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="01fa2-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="01fa2-127">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="01fa2-127">**Widening.**</span></span> <span data-ttu-id="01fa2-128">Veri `UInteger` `Long`türü , , `ULong` `Decimal`, `Single`, `Double`ve .</span><span class="sxs-lookup"><span data-stu-id="01fa2-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="01fa2-129">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `UInteger` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="01fa2-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="01fa2-130">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="01fa2-130">**Type Characters.**</span></span> <span data-ttu-id="01fa2-131">Gerçek türdeki `UI` karakterleri `UInteger` bir edebi aygıta ekler, onu veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="01fa2-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="01fa2-132">`UInteger`tanımlayıcı türü karakteri yoktur.</span><span class="sxs-lookup"><span data-stu-id="01fa2-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="01fa2-133">**Çerçeve Türü.**</span><span class="sxs-lookup"><span data-stu-id="01fa2-133">**Framework Type.**</span></span> <span data-ttu-id="01fa2-134">.NET Framework'de karşılık gelen <xref:System.UInt32?displayProperty=nameWithType> tür yapıdır.</span><span class="sxs-lookup"><span data-stu-id="01fa2-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="01fa2-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01fa2-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="01fa2-136">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="01fa2-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="01fa2-137">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="01fa2-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="01fa2-138">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="01fa2-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="01fa2-139">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="01fa2-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="01fa2-140">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="01fa2-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
