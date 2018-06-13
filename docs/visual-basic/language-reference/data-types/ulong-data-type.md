---
title: ULong Veri Türü (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b0137f0f33abfdb3f03758323edeaa63ac60117
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591566"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="9222d-102">ULong veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9222d-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="9222d-103">İşaretsiz 64-bit (8-bayt) tamsayı değeri 0'dan 18,446,744,073,709,551,615 arasında değişen tutar (1.84 kereden fazla 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="9222d-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9222d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9222d-104">Remarks</span></span>

<span data-ttu-id="9222d-105">Kullanım `ULong` veri türü için çok büyük ikili verileri içerecek şekilde `UInteger`, veya en büyük olası imzasız tamsayı değerleri.</span><span class="sxs-lookup"><span data-stu-id="9222d-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>  
  
<span data-ttu-id="9222d-106">Varsayılan değer olan `ULong` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="9222d-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="9222d-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="9222d-107">Literal assignments</span></span>

<span data-ttu-id="9222d-108">Bildirme ve başlatma bir `ULong` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak).</span><span class="sxs-lookup"><span data-stu-id="9222d-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="9222d-109">Değişmez değer tamsayı aralığı dışında ise `ULong` (diğer bir deyişle, bu ise değerinden <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="9222d-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="9222d-110">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 7,934,076,125 tamsayılar eşit ve ikili değişmez değerler atanır `ULong` değerleri.</span><span class="sxs-lookup"><span data-stu-id="9222d-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> <span data-ttu-id="9222d-111">Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="9222d-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="9222d-112">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="9222d-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="9222d-113">Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="9222d-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="9222d-114">Visual Basic 15,5 ile başlayarak, alt çizgi karakterini de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizli basamak arasında başında ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="9222d-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="9222d-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9222d-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="9222d-116">Sayısal değişmez değerleri de dahil edebilirsiniz `UL` veya `ul` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `ULong` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="9222d-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="9222d-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="9222d-117">Programming tips</span></span>
  
-   <span data-ttu-id="9222d-118">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="9222d-118">**Negative Numbers.**</span></span> <span data-ttu-id="9222d-119">Çünkü `ULong` imzasız bir tür negatif bir sayı temsil edilemez.</span><span class="sxs-lookup"><span data-stu-id="9222d-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="9222d-120">Tekli eksi kullanıyorsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `ULong`, Visual Basic ifade dönüştürür `Decimal` ilk.</span><span class="sxs-lookup"><span data-stu-id="9222d-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>  
  
-   <span data-ttu-id="9222d-121">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="9222d-121">**CLS Compliance.**</span></span> <span data-ttu-id="9222d-122">`ULong` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), CLS uyumlu kod kullandığı bir bileşen kullanamayacaklarını şekilde.</span><span class="sxs-lookup"><span data-stu-id="9222d-122">The `ULong` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="9222d-123">**Birlikte çalışma hakkında dikkat edilecek noktalar**</span><span class="sxs-lookup"><span data-stu-id="9222d-123">**Interop Considerations.**</span></span> <span data-ttu-id="9222d-124">Örnek otomasyon veya COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim varsa gibi türleri göz önünde bulundurmanız `ulong` farklı veri genişliği (32 bit) diğer ortamlarda olabilir.</span><span class="sxs-lookup"><span data-stu-id="9222d-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="9222d-125">Bu tür bir bileşen için 32-bit bağımsız değişkeni geçirilirse olarak bildirme `UInteger` yerine `ULong` Yönetilen Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="9222d-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>  
  
     <span data-ttu-id="9222d-126">Ayrıca, Windows 95, Windows 98, Windows ME veya Windows 2000 üzerinde Otomasyon 64-bit tamsayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9222d-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="9222d-127">Visual Basic geçiremezsiniz `ULong` bir Otomasyon bileşen bu platformlarda bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="9222d-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>  
  
-   <span data-ttu-id="9222d-128">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="9222d-128">**Widening.**</span></span> <span data-ttu-id="9222d-129">`ULong` Veri türü widens için `Decimal`, `Single`, ve `Double`.</span><span class="sxs-lookup"><span data-stu-id="9222d-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="9222d-130">Bu dönüştürebilirsiniz anlamına gelir `ULong` karşılaşmadan olmadan bu türdeki herhangi bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="9222d-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="9222d-131">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="9222d-131">**Type Characters.**</span></span> <span data-ttu-id="9222d-132">Değişmez değer türü karakterleri ekleme `UL` bir hazır değer zorlar `ULong` veri türü.</span><span class="sxs-lookup"><span data-stu-id="9222d-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="9222d-133">`ULong` hiçbir tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="9222d-133">`ULong` has no identifier type character.</span></span>
  
-   <span data-ttu-id="9222d-134">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="9222d-134">**Framework Type.**</span></span> <span data-ttu-id="9222d-135">.NET Framework'teki karşılık gelen tür <xref:System.UInt64?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="9222d-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9222d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9222d-136">See also</span></span>

 <xref:System.UInt64>  
 [<span data-ttu-id="9222d-137">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="9222d-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="9222d-138">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9222d-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="9222d-139">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="9222d-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="9222d-140">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="9222d-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="9222d-141">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="9222d-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
