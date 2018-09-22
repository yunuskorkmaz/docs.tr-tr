---
title: UShort Veri Türü (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 038aad2c41f655d0699dab33df276132a70e3ede
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696685"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="2733f-102">UShort veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2733f-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="2733f-103">(Değeri 0 ile 65.535 arasında değişen ayrı tutma imzasız 16-bit 2-bayt) tamsayıları.</span><span class="sxs-lookup"><span data-stu-id="2733f-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2733f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2733f-104">Remarks</span></span>

 <span data-ttu-id="2733f-105">Kullanım `UShort` veri türü için çok büyük ikili veri içermesini `Byte`.</span><span class="sxs-lookup"><span data-stu-id="2733f-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="2733f-106">Varsayılan değer olan `UShort` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="2733f-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="2733f-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="2733f-107">Literal assignments</span></span>

<span data-ttu-id="2733f-108">Bildirmek ve başlatmak bir `UShort` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren).</span><span class="sxs-lookup"><span data-stu-id="2733f-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="2733f-109">Tamsayı sabit değeri aralığının dışında ise `UShort` (diğer bir deyişle, bu ise kısa <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="2733f-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="2733f-110">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 65,034 eşit ve ikili sabit değerler atanır `UShort` değerleri.</span><span class="sxs-lookup"><span data-stu-id="2733f-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="2733f-111">Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="2733f-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="2733f-112">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="2733f-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2733f-113">Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="2733f-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="2733f-114">Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="2733f-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="2733f-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2733f-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="2733f-116">Sayısal değişmez değerleri de dahil edebilirsiniz `US` veya `us` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `UShort` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="2733f-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="2733f-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="2733f-117">Programming tips</span></span>
  
-   <span data-ttu-id="2733f-118">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="2733f-118">**Negative Numbers.**</span></span> <span data-ttu-id="2733f-119">Çünkü `UShort` işaretsiz bir türü, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="2733f-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="2733f-120">Tek işlenenli eksi işareti kullanırsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `UShort`, Visual Basic ifade dönüştürür `Integer` ilk.</span><span class="sxs-lookup"><span data-stu-id="2733f-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="2733f-121">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="2733f-121">**CLS Compliance.**</span></span> <span data-ttu-id="2733f-122">`UShort` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), böylece onu kullanan bileşen CLS uyumlu kod kullanamıyor.</span><span class="sxs-lookup"><span data-stu-id="2733f-122">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="2733f-123">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="2733f-123">**Widening.**</span></span> <span data-ttu-id="2733f-124">`UShort` Widens veri türü için `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, ve `Double`.</span><span class="sxs-lookup"><span data-stu-id="2733f-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="2733f-125">Yani dönüştürebilirsiniz `UShort` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="2733f-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="2733f-126">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="2733f-126">**Type Characters.**</span></span> <span data-ttu-id="2733f-127">Değişmez değer türü karakterleri ekleme `US` sabit değerine zorlar `UShort` veri türü.</span><span class="sxs-lookup"><span data-stu-id="2733f-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="2733f-128">`UShort` hiçbir tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="2733f-128">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="2733f-129">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="2733f-129">**Framework Type.**</span></span> <span data-ttu-id="2733f-130">.NET Framework içinde karşılık gelen türü <xref:System.UInt16?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="2733f-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2733f-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2733f-131">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="2733f-132">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="2733f-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="2733f-133">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2733f-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="2733f-134">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="2733f-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="2733f-135">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="2733f-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="2733f-136">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="2733f-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
