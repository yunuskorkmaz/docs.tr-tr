---
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
ms.openlocfilehash: ee31156e00059699125fd72a7f091afbb21beab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415485"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="3aa3f-102">UShort veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3aa3f-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="3aa3f-103">0 ile 65.535 arasında değer değişen işaretsiz 16 bit (2 baytlık) tamsayılar barındırır.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aa3f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aa3f-104">Remarks</span></span>

 <span data-ttu-id="3aa3f-105">`UShort`İçin çok büyük ikili verileri içeren veri türünü kullanın `Byte` .</span><span class="sxs-lookup"><span data-stu-id="3aa3f-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="3aa3f-106">Varsayılan değeri 0 ' `UShort` dır.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="3aa3f-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="3aa3f-107">Literal assignments</span></span>

<span data-ttu-id="3aa3f-108">Bir `UShort` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="3aa3f-109">Tamsayı sabit değeri aralığın dışındaysa `UShort` (diğer bir deyişle, değerinden küçükse <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.UInt16.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="3aa3f-110">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 65.034 'e eşit tamsayılar `UShort` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="3aa3f-111">Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="3aa3f-112">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="3aa3f-113">Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="3aa3f-114">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="3aa3f-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3aa3f-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="3aa3f-116">Sayısal değişmez değerler, `US` `us` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de veya [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir `UShort` .</span><span class="sxs-lookup"><span data-stu-id="3aa3f-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="3aa3f-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="3aa3f-117">Programming tips</span></span>
  
- <span data-ttu-id="3aa3f-118">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="3aa3f-118">**Negative Numbers.**</span></span> <span data-ttu-id="3aa3f-119">`UShort`İşaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="3aa3f-120">`-`Türü değerlendirilen bir ifadede birli eksi () işlecini kullanırsanız `UShort` , Visual Basic ifadeyi `Integer` önce dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="3aa3f-121">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="3aa3f-121">**CLS Compliance.**</span></span> <span data-ttu-id="3aa3f-122">`UShort`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="3aa3f-123">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="3aa3f-123">**Widening.**</span></span> <span data-ttu-id="3aa3f-124">Veri türü,,,,, `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` `Single` , ve `Double` için widens.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="3aa3f-125">Bu, `UShort` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3aa3f-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="3aa3f-126">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="3aa3f-126">**Type Characters.**</span></span> <span data-ttu-id="3aa3f-127">Değişmez değer türü karakterlerinin `US` bir sabit değere eklenmesi, `UShort` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="3aa3f-128">`UShort`tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="3aa3f-129">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="3aa3f-129">**Framework Type.**</span></span> <span data-ttu-id="3aa3f-130">.NET Framework karşılık gelen tür <xref:System.UInt16?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa3f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aa3f-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="3aa3f-132">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="3aa3f-132">Data Types</span></span>](index.md)
- [<span data-ttu-id="3aa3f-133">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3aa3f-133">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="3aa3f-134">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="3aa3f-134">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="3aa3f-135">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="3aa3f-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="3aa3f-136">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="3aa3f-136">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
