---
title: "Short Veri Türü (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
f1_keywords: vb.Short
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
ms.openlocfilehash: fef948debed69cf9fb7b0e6bb65eb0ddbe497a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="751bf-102">Short veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="751bf-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="751bf-103">Ayrı tutma 32,768 değeri ile 32.767 aralığı 16-bit (2-bayt) tamsayılar imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="751bf-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="751bf-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="751bf-104">Remarks</span></span>  
 <span data-ttu-id="751bf-105">Kullanım `Short` veri türü tam veri genişliği gerektirmeyen tamsayı değerleri içeren `Integer`.</span><span class="sxs-lookup"><span data-stu-id="751bf-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="751bf-106">Bazı durumlarda, ortak dil çalışma zamanı paketi, `Short` değişkenleri yakın işbirliği içinde ve bellek tüketimi.</span><span class="sxs-lookup"><span data-stu-id="751bf-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="751bf-107">Varsayılan değer olan `Short` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="751bf-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="751bf-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="751bf-108">Literal assignments</span></span>

<span data-ttu-id="751bf-109">Bildirme ve başlatma bir `Short` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak).</span><span class="sxs-lookup"><span data-stu-id="751bf-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="751bf-110">Değişmez değer tamsayı aralığı dışında ise `Short` (diğer bir deyişle, bu ise değerinden <xref:System.Int16.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Int16.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="751bf-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="751bf-111">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 1,034 tamsayılar eşit ve ikili değişmez değerleri gelen örtük olarak dönüştürülür [tamsayı](integer-data-type.md) için `Short` değerleri.</span><span class="sxs-lookup"><span data-stu-id="751bf-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="751bf-112">Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="751bf-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="751bf-113">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="751bf-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="751bf-114">Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="751bf-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="751bf-115">Sayısal değişmez değerleri de dahil edebilirsiniz `S` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `Short` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="751bf-115">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H0326S
```

## <a name="programming-tips"></a><span data-ttu-id="751bf-116">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="751bf-116">Programming tips</span></span>

-   <span data-ttu-id="751bf-117">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="751bf-117">**Widening.**</span></span> <span data-ttu-id="751bf-118">`Short` Veri türü widens için `Integer`, `Long`, `Decimal`, `Single`, veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="751bf-118">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="751bf-119">Bu dönüştürebilirsiniz anlamına gelir `Short` karşılaşmadan olmadan bu türlerinden herhangi biri için bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="751bf-119">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="751bf-120">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="751bf-120">**Type Characters.**</span></span> <span data-ttu-id="751bf-121">Değişmez değer türü karakteri ekleme `S` bir hazır değer zorlar `Short` veri türü.</span><span class="sxs-lookup"><span data-stu-id="751bf-121">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="751bf-122">`Short`hiçbir tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="751bf-122">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="751bf-123">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="751bf-123">**Framework Type.**</span></span> <span data-ttu-id="751bf-124">.NET Framework'teki karşılık gelen tür <xref:System.Int16?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="751bf-124">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="751bf-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="751bf-125">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="751bf-126">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="751bf-126">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="751bf-127">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="751bf-127">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="751bf-128">Dönüştürme özeti</span><span class="sxs-lookup"><span data-stu-id="751bf-128">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="751bf-129">Integer veri türü</span><span class="sxs-lookup"><span data-stu-id="751bf-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="751bf-130">Long veri türü</span><span class="sxs-lookup"><span data-stu-id="751bf-130">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="751bf-131">Veri türlerinin etkili kullanımı</span><span class="sxs-lookup"><span data-stu-id="751bf-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
