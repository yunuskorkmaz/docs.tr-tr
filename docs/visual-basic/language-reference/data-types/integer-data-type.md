---
title: Tamsayı Veri Türü
ms.date: 01/31/2018
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
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400738"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="ba949-102">Sonda veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba949-102">Integer data type (Visual Basic)</span></span>

<span data-ttu-id="ba949-103">Değer olarak -2.147.483.648 ile 2.147.483.647 arasında değişen imzalı 32 bitlik (4 bayt) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="ba949-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba949-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba949-104">Remarks</span></span>

 <span data-ttu-id="ba949-105">Veri `Integer` türü, 32 bit işlemcide en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba949-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="ba949-106">Diğer tamsayı türlerinin bellekten yüklenmesi ve belleğe depolanması daha yavaştır.</span><span class="sxs-lookup"><span data-stu-id="ba949-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="ba949-107">Varsayılan değeri `Integer` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="ba949-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="ba949-108">Gerçek atamalar</span><span class="sxs-lookup"><span data-stu-id="ba949-108">Literal assignments</span></span>

<span data-ttu-id="ba949-109">Bir `Integer` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba949-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ba949-110">Tamsayı literal aralığının `Integer` dışında ysa (yani, daha az <xref:System.Int32.MinValue?displayProperty=nameWithType> veya daha <xref:System.Int32.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="ba949-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ba949-111">Aşağıdaki örnekte, ondalık, heksadeondamal ve ikili literaller olarak temsil edilen 90.946'ya eşit tamsayılar değerlere `Integer` atanır.</span><span class="sxs-lookup"><span data-stu-id="ba949-111">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="ba949-112">`&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ba949-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ba949-113">Ondalık edebi hiçbir önek var.</span><span class="sxs-lookup"><span data-stu-id="ba949-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ba949-114">Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba949-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="ba949-115">Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba949-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ba949-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ba949-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="ba949-117">Sayısal literals, aşağıdaki örnekte görüldüğü `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Integer` gibi, veri türünü ifade etmek için tür karakterini de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ba949-117">Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="ba949-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="ba949-118">Programming tips</span></span>

- <span data-ttu-id="ba949-119">**Interop Hususlar.**</span><span class="sxs-lookup"><span data-stu-id="ba949-119">**Interop Considerations.**</span></span> <span data-ttu-id="ba949-120">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle bir `Integer` arada bulunuyorsanız, diğer ortamlarda farklı veri genişliğine (16 bit) sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ba949-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="ba949-121">Böyle bir bileşene 16 bitlik bir bağımsız değişken `Short` geçiyorsanız, bunu yeni Visual Basic kodunuzda değil, `Integer` olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="ba949-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="ba949-122">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="ba949-122">**Widening.**</span></span> <span data-ttu-id="ba949-123">Veri `Integer` türü `Long`, , `Decimal`, `Single`veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="ba949-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="ba949-124">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `Integer` hatayla karşılaşmadan bu türlerden herhangi birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ba949-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="ba949-125">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="ba949-125">**Type Characters.**</span></span> <span data-ttu-id="ba949-126">Gerçek tür karakterini `I` bir edebi karaktere ekler, `Integer` onu veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="ba949-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="ba949-127">Tanımlayıcı türü karakterini `%` herhangi bir tanımlayıcıya `Integer`ekolarak .</span><span class="sxs-lookup"><span data-stu-id="ba949-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
- <span data-ttu-id="ba949-128">**Çerçeve Türü.**</span><span class="sxs-lookup"><span data-stu-id="ba949-128">**Framework Type.**</span></span> <span data-ttu-id="ba949-129">.NET Framework'de karşılık gelen <xref:System.Int32?displayProperty=nameWithType> tür yapıdır.</span><span class="sxs-lookup"><span data-stu-id="ba949-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="ba949-130">Aralık</span><span class="sxs-lookup"><span data-stu-id="ba949-130">Range</span></span>

<span data-ttu-id="ba949-131">Tamsayı türünde bir değişkeni, bu türe ilişkin aralık dışında bir sayıya ayarlamaya çalışırsanız hata meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="ba949-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="ba949-132">Bir kesir olarak ayarlamaya çalışırsanız, sayı en yakın tamsayı değerine yukarı veya aşağı yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="ba949-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="ba949-133">Sayı iki tamsayı değerine de eşit yakınlıkta ise, değer en yakın çift tamsayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="ba949-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="ba949-134">Bu davranış, bir orta nokta değerini tek bir yönde sürekli olarak yuvarlamaktan kaynaklanan yuvarlama hatalarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="ba949-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="ba949-135">Aşağıdaki kod, yuvarlama örneklerini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ba949-135">The following code shows examples of rounding.</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="ba949-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba949-136">See also</span></span>

- <xref:System.Int32?displayProperty=nameWithType>
- [<span data-ttu-id="ba949-137">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="ba949-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="ba949-138">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ba949-138">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="ba949-139">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ba949-139">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="ba949-140">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ba949-140">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="ba949-141">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="ba949-141">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="ba949-142">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="ba949-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
