---
title: Short Veri Türü (Visual Basic)
ms.date: 01/31/2018
author: rpetrusha
ms.author: ronpet
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
ms.openlocfilehash: eb218a9b72208b13700ebd18dbf588066839203d
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492924"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="7586c-102">Short veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7586c-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="7586c-103">-32.768 değeri ile 32.767 aralığı 16-bit (2-bayt) tamsayıları tutar imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="7586c-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7586c-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7586c-104">Remarks</span></span>  
 <span data-ttu-id="7586c-105">Kullanım `Short` veri türü, tam veri genişliği gerektirmeyen tamsayı değerler içerecek şekilde `Integer`.</span><span class="sxs-lookup"><span data-stu-id="7586c-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="7586c-106">Bazı durumlarda, ortak dil çalışma zamanı paketi, `Short` değişkenleri yakından birlikte ve bellek tüketimi.</span><span class="sxs-lookup"><span data-stu-id="7586c-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="7586c-107">Varsayılan değer olan `Short` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="7586c-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="7586c-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="7586c-108">Literal assignments</span></span>

<span data-ttu-id="7586c-109">Bildirmek ve başlatmak bir `Short` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren).</span><span class="sxs-lookup"><span data-stu-id="7586c-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="7586c-110">Tamsayı sabit değeri aralığının dışında ise `Short` (diğer bir deyişle, bu ise kısa <xref:System.Int16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Int16.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="7586c-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="7586c-111">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 1,034 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [tamsayı](integer-data-type.md) için `Short` değerleri.</span><span class="sxs-lookup"><span data-stu-id="7586c-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="7586c-112">Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="7586c-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="7586c-113">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="7586c-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="7586c-114">Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="7586c-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="7586c-115">Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="7586c-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="7586c-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7586c-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="7586c-117">Sayısal değişmez değerleri de dahil edebilirsiniz `S` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `Short` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="7586c-117">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="7586c-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="7586c-118">Programming tips</span></span>

-   <span data-ttu-id="7586c-119">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="7586c-119">**Widening.**</span></span> <span data-ttu-id="7586c-120">`Short` Widens veri türü için `Integer`, `Long`, `Decimal`, `Single`, veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="7586c-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="7586c-121">Yani dönüştürebilirsiniz `Short` karşılaşmadan bu türlerden herhangi birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="7586c-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="7586c-122">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="7586c-122">**Type Characters.**</span></span> <span data-ttu-id="7586c-123">Değişmez değer türü karakterinin `S` sabit değerine zorlar `Short` veri türü.</span><span class="sxs-lookup"><span data-stu-id="7586c-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="7586c-124">`Short` hiçbir tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="7586c-124">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="7586c-125">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="7586c-125">**Framework Type.**</span></span> <span data-ttu-id="7586c-126">.NET Framework içinde karşılık gelen türü <xref:System.Int16?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="7586c-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7586c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7586c-127">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="7586c-128">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="7586c-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="7586c-129">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7586c-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="7586c-130">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="7586c-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="7586c-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7586c-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="7586c-132">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7586c-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="7586c-133">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7586c-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
