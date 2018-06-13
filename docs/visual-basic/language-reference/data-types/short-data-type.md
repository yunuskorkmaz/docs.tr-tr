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
ms.openlocfilehash: ef99743828d8d80844486b651178622ff45fd554
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590718"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="bda7e-102">Short veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bda7e-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="bda7e-103">Ayrı tutma 32,768 değeri ile 32.767 aralığı 16-bit (2-bayt) tamsayılar imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="bda7e-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bda7e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bda7e-104">Remarks</span></span>  
 <span data-ttu-id="bda7e-105">Kullanım `Short` veri türü tam veri genişliği gerektirmeyen tamsayı değerleri içeren `Integer`.</span><span class="sxs-lookup"><span data-stu-id="bda7e-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="bda7e-106">Bazı durumlarda, ortak dil çalışma zamanı paketi, `Short` değişkenleri yakın işbirliği içinde ve bellek tüketimi.</span><span class="sxs-lookup"><span data-stu-id="bda7e-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="bda7e-107">Varsayılan değer olan `Short` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="bda7e-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="bda7e-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="bda7e-108">Literal assignments</span></span>

<span data-ttu-id="bda7e-109">Bildirme ve başlatma bir `Short` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak).</span><span class="sxs-lookup"><span data-stu-id="bda7e-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="bda7e-110">Değişmez değer tamsayı aralığı dışında ise `Short` (diğer bir deyişle, bu ise değerinden <xref:System.Int16.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Int16.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="bda7e-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="bda7e-111">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 1,034 tamsayılar eşit ve ikili değişmez değerleri gelen örtük olarak dönüştürülür [tamsayı](integer-data-type.md) için `Short` değerleri.</span><span class="sxs-lookup"><span data-stu-id="bda7e-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="bda7e-112">Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="bda7e-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="bda7e-113">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="bda7e-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="bda7e-114">Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="bda7e-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="bda7e-115">Visual Basic 15,5 ile başlayarak, alt çizgi karakterini de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizli basamak arasında başında ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="bda7e-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="bda7e-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bda7e-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="bda7e-117">Sayısal değişmez değerleri de dahil edebilirsiniz `S` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `Short` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="bda7e-117">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="bda7e-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="bda7e-118">Programming tips</span></span>

-   <span data-ttu-id="bda7e-119">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="bda7e-119">**Widening.**</span></span> <span data-ttu-id="bda7e-120">`Short` Veri türü widens için `Integer`, `Long`, `Decimal`, `Single`, veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="bda7e-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="bda7e-121">Bu dönüştürebilirsiniz anlamına gelir `Short` karşılaşmadan olmadan bu türlerinden herhangi biri için bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="bda7e-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="bda7e-122">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="bda7e-122">**Type Characters.**</span></span> <span data-ttu-id="bda7e-123">Değişmez değer türü karakteri ekleme `S` bir hazır değer zorlar `Short` veri türü.</span><span class="sxs-lookup"><span data-stu-id="bda7e-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="bda7e-124">`Short` hiçbir tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="bda7e-124">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="bda7e-125">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="bda7e-125">**Framework Type.**</span></span> <span data-ttu-id="bda7e-126">.NET Framework'teki karşılık gelen tür <xref:System.Int16?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="bda7e-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda7e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bda7e-127">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="bda7e-128">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="bda7e-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="bda7e-129">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bda7e-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="bda7e-130">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="bda7e-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="bda7e-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="bda7e-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="bda7e-132">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="bda7e-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="bda7e-133">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="bda7e-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
