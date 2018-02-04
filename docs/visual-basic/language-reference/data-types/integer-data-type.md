---
title: "Tamsayı Veri Türü (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba700cac58c96b3d6d2f5ed3c74fdd7e95761352
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="77b4d-102">Tamsayı veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77b4d-102">Integer data type (Visual Basic)</span></span>
<span data-ttu-id="77b4d-103">Değer olarak -2.147.483.648 ile 2.147.483.647 arasında değişen imzalı 32 bitlik (4 bayt) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="77b4d-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77b4d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77b4d-104">Remarks</span></span>
 <span data-ttu-id="77b4d-105">`Integer` Veri türü bir 32-bit işlemci en iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="77b4d-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="77b4d-106">Diğer tamsayı türlerinin bellekten yüklenmesi ve belleğe depolanması daha yavaştır.</span><span class="sxs-lookup"><span data-stu-id="77b4d-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="77b4d-107">Varsayılan değer olan `Integer` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="77b4d-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="77b4d-108">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="77b4d-108">Literal assignments</span></span>

<span data-ttu-id="77b4d-109">Bildirme ve başlatma bir `Integer` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak).</span><span class="sxs-lookup"><span data-stu-id="77b4d-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="77b4d-110">Değişmez değer tamsayı aralığı dışında ise `Integer` (diğer bir deyişle, bu ise değerinden <xref:System.Int32.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Int32.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="77b4d-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="77b4d-111">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 16,342 tamsayılar eşit ve ikili değişmez değerler atanır `Integer` değerleri.</span><span class="sxs-lookup"><span data-stu-id="77b4d-111">In the following example, integers equal to 16,342 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="77b4d-112">Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="77b4d-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="77b4d-113">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="77b4d-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="77b4d-114">Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="77b4d-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="77b4d-115">Visual Basic 15,5 ile başlayarak, alt çizgi karakterini de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizli basamak arasında başında ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="77b4d-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="77b4d-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="77b4d-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="77b4d-117">Sayısal değişmez değerleri de dahil edebilirsiniz `I` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `Integer` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="77b4d-117">Numeric literals can also include the `I` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="77b4d-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="77b4d-118">Programming tips</span></span>

-   <span data-ttu-id="77b4d-119">**Birlikte çalışma hakkında dikkat edilecek noktalar**</span><span class="sxs-lookup"><span data-stu-id="77b4d-119">**Interop Considerations.**</span></span> <span data-ttu-id="77b4d-120">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmaz bileşenleriyle arabirim olmadığını unutmayın `Integer` diğer ortamlarda farklı veri genişliği (16 bit) vardır.</span><span class="sxs-lookup"><span data-stu-id="77b4d-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="77b4d-121">Bir 16 bit bağımsız değişkeni tür bileşen geçirilirse, olarak bildirme `Short` yerine `Integer` yeni Visual Basic kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="77b4d-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="77b4d-122">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="77b4d-122">**Widening.**</span></span> <span data-ttu-id="77b4d-123">`Integer` Veri türü widens için `Long`, `Decimal`, `Single`, veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="77b4d-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="77b4d-124">Bu dönüştürebilirsiniz anlamına gelir `Integer` karşılaşmadan olmadan bu türlerinden herhangi biri için bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="77b4d-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="77b4d-125">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="77b4d-125">**Type Characters.**</span></span> <span data-ttu-id="77b4d-126">Değişmez değer türü karakteri ekleme `I` bir hazır değer zorlar `Integer` veri türü.</span><span class="sxs-lookup"><span data-stu-id="77b4d-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="77b4d-127">Tanımlayıcı türü karakteri ekleme `%` herhangi bir tanımlayıcı zorlar `Integer`.</span><span class="sxs-lookup"><span data-stu-id="77b4d-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
-   <span data-ttu-id="77b4d-128">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="77b4d-128">**Framework Type.**</span></span> <span data-ttu-id="77b4d-129">.NET Framework'teki karşılık gelen tür <xref:System.Int32?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="77b4d-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="77b4d-130">Aralık</span><span class="sxs-lookup"><span data-stu-id="77b4d-130">Range</span></span>

<span data-ttu-id="77b4d-131">Tamsayı türünde bir değişkeni, bu türe ilişkin aralık dışında bir sayıya ayarlamaya çalışırsanız hata meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="77b4d-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="77b4d-132">Bir kesir olarak ayarlamaya çalışırsanız, sayı en yakın tamsayı değerine yukarı veya aşağı yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="77b4d-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="77b4d-133">Sayı iki tamsayı değerine de eşit yakınlıkta ise, değer en yakın çift tamsayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="77b4d-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="77b4d-134">Bu davranış, bir orta nokta değerini tek bir yönde sürekli olarak yuvarlamaktan kaynaklanan yuvarlama hatalarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="77b4d-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="77b4d-135">Aşağıdaki kod, yuvarlama örneklerini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="77b4d-135">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="77b4d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77b4d-136">See also</span></span>

<span data-ttu-id="77b4d-137"><xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="77b4d-137"><xref:System.Int32?displayProperty=nameWithType></span></span>   
 [<span data-ttu-id="77b4d-138">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="77b4d-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="77b4d-139">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="77b4d-139">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="77b4d-140">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="77b4d-140">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="77b4d-141">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="77b4d-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="77b4d-142">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="77b4d-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="77b4d-143">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="77b4d-143">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
