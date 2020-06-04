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
ms.openlocfilehash: 11070f6c7f3259b8c34528eb54d99b031b68f9f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415550"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="ba817-102">UInteger veri türü</span><span class="sxs-lookup"><span data-stu-id="ba817-102">UInteger data type</span></span>

<span data-ttu-id="ba817-103">0 ile 4.294.967.295 arasında değer değişen işaretsiz 32 bitlik (4 baytlık) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="ba817-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba817-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba817-104">Remarks</span></span>

<span data-ttu-id="ba817-105">`UInteger`Veri türü en etkili veri genişliğinde en büyük işaretsiz değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba817-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="ba817-106">Varsayılan değeri 0 ' `UInteger` dır.</span><span class="sxs-lookup"><span data-stu-id="ba817-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="ba817-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="ba817-107">Literal assignments</span></span>

<span data-ttu-id="ba817-108">Bir `UInteger` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba817-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ba817-109">Tamsayı sabit değeri aralığın dışındaysa `UInteger` (diğer bir deyişle, değerinden küçükse <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.UInt32.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="ba817-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ba817-110">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 3.000.000.000 'e eşit tamsayılar `UInteger` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="ba817-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="ba817-111">Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba817-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ba817-112">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="ba817-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ba817-113">Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba817-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="ba817-114">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba817-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ba817-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ba817-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="ba817-116">Sayısal değişmez değerler, `UI` `ui` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de veya [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir `UInteger` .</span><span class="sxs-lookup"><span data-stu-id="ba817-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="ba817-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="ba817-117">Programming tips</span></span>

<span data-ttu-id="ba817-118">`UInteger`Ve `Integer` veri türleri, daha küçük tamsayı türleri ( `UShort` , `Short` , ve), daha `Byte` `SByte` az bit kullansa bile, yükleme, depolama ve getirme için daha fazla zaman alan bir 32 bitlik işlemcide en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba817-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="ba817-119">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="ba817-119">**Negative Numbers.**</span></span> <span data-ttu-id="ba817-120">`UInteger`İşaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="ba817-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="ba817-121">`-`Türü değerlendirilen bir ifadede birli eksi () işlecini kullanırsanız `UInteger` , Visual Basic ifadeyi `Long` önce dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ba817-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="ba817-122">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="ba817-122">**CLS Compliance.**</span></span> <span data-ttu-id="ba817-123">`UInteger`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.</span><span class="sxs-lookup"><span data-stu-id="ba817-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="ba817-124">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="ba817-124">**Interop Considerations.**</span></span> <span data-ttu-id="ba817-125">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabirimleriniz varsa, gibi türlerin `uint` diğer ortamlarda farklı bir veri genişliğine (16 bit) sahip olabileceğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ba817-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="ba817-126">Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu `UShort` `UInteger` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="ba817-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="ba817-127">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="ba817-127">**Widening.**</span></span> <span data-ttu-id="ba817-128">`UInteger`Veri türü,,,, ve için widens `Long` `ULong` `Decimal` `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="ba817-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="ba817-129">Bu, `UInteger` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ba817-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="ba817-130">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="ba817-130">**Type Characters.**</span></span> <span data-ttu-id="ba817-131">Değişmez değer türü karakterlerinin `UI` bir sabit değere eklenmesi, `UInteger` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="ba817-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="ba817-132">`UInteger`tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="ba817-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="ba817-133">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="ba817-133">**Framework Type.**</span></span> <span data-ttu-id="ba817-134">.NET Framework karşılık gelen tür <xref:System.UInt32?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="ba817-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba817-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba817-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="ba817-136">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="ba817-136">Data Types</span></span>](index.md)
- [<span data-ttu-id="ba817-137">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ba817-137">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="ba817-138">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="ba817-138">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="ba817-139">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="ba817-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="ba817-140">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="ba817-140">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
