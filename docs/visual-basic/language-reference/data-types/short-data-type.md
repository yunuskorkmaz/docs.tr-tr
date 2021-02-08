---
description: 'Hakkında daha fazla bilgi edinin: kısa veri türü (Visual Basic)'
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
ms.openlocfilehash: 8c6bee45355548b3a32d74d059159918b4009fbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792147"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="52f51-103">Short veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52f51-103">Short data type (Visual Basic)</span></span>

<span data-ttu-id="52f51-104">,-32.768 ile 32.767 arasında bir değere kadar olan işaretli 16 bit (2 baytlık) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="52f51-104">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52f51-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52f51-105">Remarks</span></span>  

 <span data-ttu-id="52f51-106">`Short`Veri türünü, tam veri genişliği gerektirmeyen tamsayı değerler içerecek şekilde kullanın `Integer` .</span><span class="sxs-lookup"><span data-stu-id="52f51-106">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="52f51-107">Bazı durumlarda, ortak dil çalışma zamanı `Short` değişkenlerinizi birbirine yakından paketedebilir ve bellek tüketimini kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="52f51-107">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="52f51-108">Varsayılan değeri 0 ' `Short` dır.</span><span class="sxs-lookup"><span data-stu-id="52f51-108">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="52f51-109">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="52f51-109">Literal assignments</span></span>

<span data-ttu-id="52f51-110">Bir `Short` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52f51-110">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="52f51-111">Tamsayı sabit değeri aralığın dışındaysa `Short` (diğer bir deyişle, değerinden küçükse <xref:System.Int16.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.Int16.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="52f51-111">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="52f51-112">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 1.034 'e eşit tamsayılar, örtük olarak [tam sayıdan](integer-data-type.md) `Short` değerlere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="52f51-112">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="52f51-113">Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="52f51-113">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="52f51-114">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="52f51-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="52f51-115">Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52f51-115">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="52f51-116">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52f51-116">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="52f51-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="52f51-117">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="52f51-118">Sayısal değişmez değerler, `S` [](../../programming-guide/language-features/data-types/type-characters.md) `Short` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de tür karakterini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="52f51-118">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="52f51-119">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="52f51-119">Programming tips</span></span>

- <span data-ttu-id="52f51-120">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="52f51-120">**Widening.**</span></span> <span data-ttu-id="52f51-121">`Short`Veri türü widens,,,, `Integer` `Long` `Decimal` `Single` veya `Double` .</span><span class="sxs-lookup"><span data-stu-id="52f51-121">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="52f51-122">Bu, `Short` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="52f51-122">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="52f51-123">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="52f51-123">**Type Characters.**</span></span> <span data-ttu-id="52f51-124">Değişmez değer türü karakterini `S` bir sabit değere eklemek, `Short` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="52f51-124">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="52f51-125">`Short` tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="52f51-125">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="52f51-126">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="52f51-126">**Framework Type.**</span></span> <span data-ttu-id="52f51-127">.NET Framework karşılık gelen tür <xref:System.Int16?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="52f51-127">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f51-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52f51-128">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="52f51-129">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="52f51-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="52f51-130">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="52f51-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="52f51-131">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="52f51-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="52f51-132">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="52f51-132">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="52f51-133">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="52f51-133">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="52f51-134">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="52f51-134">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
