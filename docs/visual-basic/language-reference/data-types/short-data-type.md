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
ms.openlocfilehash: 176d27c86127dac1d9c9c0231790f7a5c2a2fefc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415563"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="ff6d5-102">Short veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff6d5-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="ff6d5-103">,-32.768 ile 32.767 arasında bir değere kadar olan işaretli 16 bit (2 baytlık) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff6d5-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff6d5-104">Remarks</span></span>  

 <span data-ttu-id="ff6d5-105">`Short`Veri türünü, tam veri genişliği gerektirmeyen tamsayı değerler içerecek şekilde kullanın `Integer` .</span><span class="sxs-lookup"><span data-stu-id="ff6d5-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="ff6d5-106">Bazı durumlarda, ortak dil çalışma zamanı `Short` değişkenlerinizi birbirine yakından paketedebilir ve bellek tüketimini kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="ff6d5-107">Varsayılan değeri 0 ' `Short` dır.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="ff6d5-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="ff6d5-108">Literal assignments</span></span>

<span data-ttu-id="ff6d5-109">Bir `Short` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ff6d5-110">Tamsayı sabit değeri aralığın dışındaysa `Short` (diğer bir deyişle, değerinden küçükse <xref:System.Int16.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.Int16.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ff6d5-111">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 1.034 'e eşit tamsayılar, örtük olarak [tam sayıdan](integer-data-type.md) `Short` değerlere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="ff6d5-112">Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ff6d5-113">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ff6d5-114">Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="ff6d5-115">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ff6d5-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ff6d5-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="ff6d5-117">Sayısal değişmez değerler, `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Short` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de tür karakterini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="ff6d5-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="ff6d5-118">Programming tips</span></span>

- <span data-ttu-id="ff6d5-119">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="ff6d5-119">**Widening.**</span></span> <span data-ttu-id="ff6d5-120">`Short`Veri türü widens,,,, `Integer` `Long` `Decimal` `Single` veya `Double` .</span><span class="sxs-lookup"><span data-stu-id="ff6d5-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="ff6d5-121">Bu, `Short` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ff6d5-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="ff6d5-122">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="ff6d5-122">**Type Characters.**</span></span> <span data-ttu-id="ff6d5-123">Değişmez değer türü karakterini `S` bir sabit değere eklemek, `Short` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="ff6d5-124">`Short`tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="ff6d5-125">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="ff6d5-125">**Framework Type.**</span></span> <span data-ttu-id="ff6d5-126">.NET Framework karşılık gelen tür <xref:System.Int16?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6d5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff6d5-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="ff6d5-128">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="ff6d5-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="ff6d5-129">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ff6d5-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="ff6d5-130">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="ff6d5-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="ff6d5-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ff6d5-131">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="ff6d5-132">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ff6d5-132">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="ff6d5-133">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="ff6d5-133">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
