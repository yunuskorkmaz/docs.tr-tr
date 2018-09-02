---
title: Long Veri Türü (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b3970aad08f2be98d175b4175ef06711bcaf609
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452829"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="786d7-102">Long veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="786d7-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="786d7-103">İmzalı-9,223,372,036,854,775,808 değerden 9.223.372.036.854.775.807 arasında değişen 64-bit (8-bayt) tamsayıları tutar (9.2... E + 18).</span><span class="sxs-lookup"><span data-stu-id="786d7-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="786d7-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="786d7-104">Remarks</span></span>

 <span data-ttu-id="786d7-105">Kullanım `Long` sığacak kadar büyük tamsayı sayılar içeren veri türü `Integer` veri türü.</span><span class="sxs-lookup"><span data-stu-id="786d7-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>  
  
 <span data-ttu-id="786d7-106">Varsayılan değer olan `Long` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="786d7-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="786d7-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="786d7-107">Literal assignments</span></span> 

<span data-ttu-id="786d7-108">Bildirmek ve başlatmak bir `Long` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren).</span><span class="sxs-lookup"><span data-stu-id="786d7-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="786d7-109">Tamsayı sabit değeri aralığının dışında ise `Long` (diğer bir deyişle, bu ise kısa <xref:System.Int64.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Int64.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="786d7-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="786d7-110">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 4,294,967,296 eşit ve ikili sabit değerler atanır `Long` değerleri.</span><span class="sxs-lookup"><span data-stu-id="786d7-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> <span data-ttu-id="786d7-111">Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="786d7-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="786d7-112">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="786d7-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="786d7-113">Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="786d7-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="786d7-114">Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="786d7-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="786d7-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="786d7-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="786d7-116">Sayısal değişmez değerleri de dahil edebilirsiniz `L` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `Long` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="786d7-116">Numeric literals can also include the `L` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="786d7-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="786d7-117">Programming tips</span></span>

-   <span data-ttu-id="786d7-118">**Birlikte çalışabilirlik değerlendirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="786d7-118">**Interop Considerations.**</span></span> <span data-ttu-id="786d7-119">Örnek otomasyon ve COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim olmadığını unutmayın `Long` diğer ortamlarda farklı veri genişliği (32 bit) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="786d7-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="786d7-120">Bir 32-bit bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `Integer` yerine `Long` yeni Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="786d7-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="786d7-121">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="786d7-121">**Widening.**</span></span> <span data-ttu-id="786d7-122">`Long` Widens veri türü için `Decimal`, `Single`, veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="786d7-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="786d7-123">Yani dönüştürebilirsiniz `Long` karşılaşmadan bu türlerden herhangi birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="786d7-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="786d7-124">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="786d7-124">**Type Characters.**</span></span> <span data-ttu-id="786d7-125">Değişmez değer türü karakterinin `L` sabit değerine zorlar `Long` veri türü.</span><span class="sxs-lookup"><span data-stu-id="786d7-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="786d7-126">Tanımlayıcı türü karakteri ekleme `&` herhangi bir tanımlayıcı zorlar `Long`.</span><span class="sxs-lookup"><span data-stu-id="786d7-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>  
  
-   <span data-ttu-id="786d7-127">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="786d7-127">**Framework Type.**</span></span> <span data-ttu-id="786d7-128">.NET Framework içinde karşılık gelen türü <xref:System.Int64?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="786d7-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>  

## <a name="see-also"></a><span data-ttu-id="786d7-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="786d7-129">See also</span></span>

<span data-ttu-id="786d7-130"><xref:System.Int64>
[Veri türleri](../../../visual-basic/language-reference/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="786d7-130"><xref:System.Int64>
[Data Types](../../../visual-basic/language-reference/data-types/index.md) </span></span>  
<span data-ttu-id="786d7-131">[Tamsayı veri türü](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="786d7-131">[Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="786d7-132">[Short veri türü](../../../visual-basic/language-reference/data-types/short-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="786d7-132">[Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md) </span></span>  
<span data-ttu-id="786d7-133">[Tür dönüştürme işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="786d7-133">[Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="786d7-134">[Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="786d7-134">[Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
[<span data-ttu-id="786d7-135">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="786d7-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
