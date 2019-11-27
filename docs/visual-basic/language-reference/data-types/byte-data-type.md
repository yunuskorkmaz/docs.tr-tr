---
title: Byte Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344074"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="ca00a-102">Byte veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca00a-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="ca00a-103">0 ile 255 arasında değer aralığı olan işaretsiz 8 bit (1 baytlık) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="ca00a-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca00a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca00a-104">Remarks</span></span>

<span data-ttu-id="ca00a-105">İkili veri içeren `Byte` veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca00a-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="ca00a-106">`Byte` varsayılan değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="ca00a-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="ca00a-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="ca00a-107">Literal assignments</span></span>

<span data-ttu-id="ca00a-108">Bir `Byte` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca00a-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ca00a-109">İntegral sabit değeri bir `Byte` aralığının dışındaysa (yani, <xref:System.Byte.MinValue?displayProperty=nameWithType> veya <xref:System.Byte.MaxValue?displayProperty=nameWithType>değerinden daha büyükse) bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="ca00a-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="ca00a-110">Aşağıdaki örnekte, ondalık, onaltılık ve ikili harfler olarak temsil edilen 201 'e eşit tamsayılar, örtük olarak [tam sayıdan](integer-data-type.md) `byte` değerlere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ca00a-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="ca00a-111">Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ca00a-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ca00a-112">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="ca00a-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ca00a-113">Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_`alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca00a-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="ca00a-114">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca00a-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ca00a-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ca00a-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="ca00a-116">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="ca00a-116">Programming tips</span></span>

- <span data-ttu-id="ca00a-117">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="ca00a-117">**Negative Numbers.**</span></span> <span data-ttu-id="ca00a-118">`Byte` işaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="ca00a-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="ca00a-119">`Byte`türü değerlendirilen bir ifadede birli eksi (`-`) işlecini kullanırsanız, Visual Basic ifadeyi önce `Short` dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ca00a-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="ca00a-120">**Biçim dönüştürmeleri.**</span><span class="sxs-lookup"><span data-stu-id="ca00a-120">**Format Conversions.**</span></span> <span data-ttu-id="ca00a-121">Visual Basic dosyaları okurken veya yazarken ya da dll 'Leri, yöntemleri ve özellikleri çağırdığında, veri biçimleri arasında otomatik olarak dönüştürme yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca00a-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="ca00a-122">`Byte` değişkenleri ve dizileri içinde depolanan ikili veriler, bu tür biçim dönüştürmeleri sırasında korunur.</span><span class="sxs-lookup"><span data-stu-id="ca00a-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="ca00a-123">İkili veriler için bir `String` değişkeni kullanmamalısınız, çünkü içeriği ANSI ve Unicode biçimleri arasında dönüştürme sırasında bozulabilir.</span><span class="sxs-lookup"><span data-stu-id="ca00a-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="ca00a-124">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="ca00a-124">**Widening.**</span></span> <span data-ttu-id="ca00a-125">`Byte` veri türü `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`veya `Double`için.</span><span class="sxs-lookup"><span data-stu-id="ca00a-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="ca00a-126">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Byte` bu türlerden birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ca00a-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="ca00a-127">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="ca00a-127">**Type Characters.**</span></span> <span data-ttu-id="ca00a-128">`Byte` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="ca00a-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="ca00a-129">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="ca00a-129">**Framework Type.**</span></span> <span data-ttu-id="ca00a-130">.NET Framework karşılık gelen tür <xref:System.Byte?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="ca00a-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="ca00a-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca00a-131">Example</span></span>

 <span data-ttu-id="ca00a-132">Aşağıdaki örnekte, `b` bir `Byte` değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="ca00a-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="ca00a-133">Deyimleri, değişkeninin aralığını ve bit kaydırma operatörlerinin uygulamanın bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca00a-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="ca00a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca00a-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="ca00a-135">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="ca00a-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="ca00a-136">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ca00a-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="ca00a-137">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="ca00a-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="ca00a-138">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="ca00a-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
