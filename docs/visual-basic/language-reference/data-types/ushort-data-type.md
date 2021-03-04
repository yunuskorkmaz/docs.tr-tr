---
description: 'Hakkında daha fazla bilgi edinin: UShort veri türü (Visual Basic)'
title: UShort Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 43c18bad3e24e14c28d2ca3d5d88170d584e55a8
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106650"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="15918-103">UShort veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15918-103">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="15918-104">0 ile 65.535 arasında değer değişen işaretsiz 16 bit (2 baytlık) tamsayılar barındırır.</span><span class="sxs-lookup"><span data-stu-id="15918-104">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15918-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15918-105">Remarks</span></span>

 <span data-ttu-id="15918-106">`UShort`İçin çok büyük ikili verileri içeren veri türünü kullanın `Byte` .</span><span class="sxs-lookup"><span data-stu-id="15918-106">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="15918-107">Varsayılan değeri 0 ' `UShort` dır.</span><span class="sxs-lookup"><span data-stu-id="15918-107">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="15918-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="15918-108">Literal assignments</span></span>

<span data-ttu-id="15918-109">Bir `UShort` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15918-109">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="15918-110">Tamsayı sabit değeri aralığın dışındaysa `UShort` (diğer bir deyişle, değerinden küçükse <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.UInt16.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="15918-110">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="15918-111">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 65.034 'e eşit tamsayılar `UShort` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="15918-111">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="15918-112">Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="15918-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="15918-113">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="15918-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="15918-114">Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15918-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="15918-115">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15918-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="15918-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="15918-116">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="15918-117">Sayısal değişmez değerler, `US` `us` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de veya [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir `UShort` .</span><span class="sxs-lookup"><span data-stu-id="15918-117">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="15918-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="15918-118">Programming tips</span></span>
  
- <span data-ttu-id="15918-119">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="15918-119">**Negative Numbers.**</span></span> <span data-ttu-id="15918-120">`UShort`İşaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="15918-120">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="15918-121">`-`Türü değerlendirilen bir ifadede birli eksi () işlecini kullanırsanız `UShort` , Visual Basic ifadeyi `Integer` önce dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="15918-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="15918-122">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="15918-122">**CLS Compliance.**</span></span> <span data-ttu-id="15918-123">`UShort`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.</span><span class="sxs-lookup"><span data-stu-id="15918-123">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="15918-124">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="15918-124">**Widening.**</span></span> <span data-ttu-id="15918-125">Veri türü,,,,, `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` `Single` , ve `Double` için widens.</span><span class="sxs-lookup"><span data-stu-id="15918-125">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="15918-126">Bu, `UShort` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="15918-126">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="15918-127">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="15918-127">**Type Characters.**</span></span> <span data-ttu-id="15918-128">Değişmez değer türü karakterlerinin `US` bir sabit değere eklenmesi, `UShort` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="15918-128">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="15918-129">`UShort` tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="15918-129">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="15918-130">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="15918-130">**Framework Type.**</span></span> <span data-ttu-id="15918-131">.NET Framework karşılık gelen tür <xref:System.UInt16?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="15918-131">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15918-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15918-132">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="15918-133">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="15918-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="15918-134">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="15918-134">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="15918-135">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="15918-135">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="15918-136">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="15918-136">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="15918-137">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="15918-137">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
