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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400731"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="fcbf1-102">Kısa veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcbf1-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="fcbf1-103">-32.768 ile 32.767 arasında değişen imzalı 16 bit (2 bayt) tümsedoları tutar.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcbf1-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcbf1-104">Remarks</span></span>  

 <span data-ttu-id="fcbf1-105">Tam `Short` veri genişliği gerektirmeyen tamsayı değerlerini içerecek şekilde veri türünü kullanın. `Integer`</span><span class="sxs-lookup"><span data-stu-id="fcbf1-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="fcbf1-106">Bazı durumlarda, ortak dil çalışma süresi `Short` değişkenlerinizi birbirine yakın bir şekilde paketleyebilir ve bellek tüketiminden tasarruf edebilir.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="fcbf1-107">Varsayılan değeri `Short` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="fcbf1-108">Gerçek atamalar</span><span class="sxs-lookup"><span data-stu-id="fcbf1-108">Literal assignments</span></span>

<span data-ttu-id="fcbf1-109">Bir `Short` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="fcbf1-110">Tamsayı literal aralığının `Short` dışında ysa (yani, daha az <xref:System.Int16.MinValue?displayProperty=nameWithType> veya daha <xref:System.Int16.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="fcbf1-111">Aşağıdaki örnekte, ondalık, heksadesimal ve ikili literalolarak temsil edilen 1.034'e eşit tamsayılar dolaylı olarak `Short` [Tamsayı'dan](integer-data-type.md) değerlere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="fcbf1-112">`&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="fcbf1-113">Ondalık edebi hiçbir önek var.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="fcbf1-114">Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="fcbf1-115">Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="fcbf1-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="fcbf1-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="fcbf1-117">Sayısal literals, aşağıdaki örnekte görüldüğü `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Short` gibi, veri türünü ifade etmek için tür karakterini de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="fcbf1-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="fcbf1-118">Programming tips</span></span>

- <span data-ttu-id="fcbf1-119">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="fcbf1-119">**Widening.**</span></span> <span data-ttu-id="fcbf1-120">Veri `Short` `Integer`türü , , `Long` `Decimal` `Single`, , `Double`veya .</span><span class="sxs-lookup"><span data-stu-id="fcbf1-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="fcbf1-121">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `Short` hatayla karşılaşmadan bu türlerden herhangi birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="fcbf1-122">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="fcbf1-122">**Type Characters.**</span></span> <span data-ttu-id="fcbf1-123">Gerçek tür karakterini `S` bir edebi karaktere ekler, `Short` onu veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="fcbf1-124">`Short`tanımlayıcı türü karakteri yoktur.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="fcbf1-125">**Çerçeve Türü.**</span><span class="sxs-lookup"><span data-stu-id="fcbf1-125">**Framework Type.**</span></span> <span data-ttu-id="fcbf1-126">.NET Framework'de karşılık gelen <xref:System.Int16?displayProperty=nameWithType> tür yapıdır.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbf1-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="fcbf1-128">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="fcbf1-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="fcbf1-129">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fcbf1-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="fcbf1-130">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="fcbf1-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="fcbf1-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="fcbf1-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="fcbf1-132">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="fcbf1-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="fcbf1-133">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="fcbf1-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
