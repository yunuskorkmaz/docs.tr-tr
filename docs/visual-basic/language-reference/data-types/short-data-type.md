---
title: Short Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343931"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="173a0-102">Short veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="173a0-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="173a0-103">,-32.768 ile 32.767 arasında bir değere kadar olan işaretli 16 bit (2 baytlık) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="173a0-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="173a0-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="173a0-104">Remarks</span></span>  

 <span data-ttu-id="173a0-105">`Integer`tam veri genişliğini gerektirmeyen tamsayı değerleri içermesi için `Short` veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="173a0-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="173a0-106">Bazı durumlarda, ortak dil çalışma zamanı `Short` değişkenlerinizi birbirine yakından paketedebilir ve bellek tüketimini kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="173a0-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="173a0-107">`Short` varsayılan değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="173a0-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="173a0-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="173a0-108">Literal assignments</span></span>

<span data-ttu-id="173a0-109">Bir `Short` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="173a0-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="173a0-110">Tamsayı sabit değeri `Short` aralığının dışındaysa (yani, <xref:System.Int16.MinValue?displayProperty=nameWithType> veya <xref:System.Int16.MaxValue?displayProperty=nameWithType>değerinden daha küçükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="173a0-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="173a0-111">Aşağıdaki örnekte, ondalık, onaltılık ve ikili harfler olarak temsil edilen 1.034 'e eşit tamsayılar, örtük olarak [tam sayıdan](integer-data-type.md) `Short` değerlere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="173a0-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="173a0-112">Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="173a0-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="173a0-113">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="173a0-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="173a0-114">Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_`alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="173a0-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="173a0-115">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="173a0-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="173a0-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="173a0-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="173a0-117">Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `Short` veri türünü belirtmek için `S` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="173a0-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="173a0-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="173a0-118">Programming tips</span></span>

- <span data-ttu-id="173a0-119">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="173a0-119">**Widening.**</span></span> <span data-ttu-id="173a0-120">`Short` veri türü `Integer`, `Long`, `Decimal`, `Single`veya `Double`için.</span><span class="sxs-lookup"><span data-stu-id="173a0-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="173a0-121">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Short` bu türlerden birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="173a0-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="173a0-122">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="173a0-122">**Type Characters.**</span></span> <span data-ttu-id="173a0-123">Değişmez değer türü karakter `S` bir sabit değere eklenmesi, `Short` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="173a0-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="173a0-124">`Short` tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="173a0-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="173a0-125">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="173a0-125">**Framework Type.**</span></span> <span data-ttu-id="173a0-126">.NET Framework karşılık gelen tür <xref:System.Int16?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="173a0-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="173a0-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="173a0-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="173a0-128">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="173a0-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="173a0-129">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="173a0-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="173a0-130">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="173a0-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="173a0-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="173a0-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="173a0-132">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="173a0-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="173a0-133">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="173a0-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
