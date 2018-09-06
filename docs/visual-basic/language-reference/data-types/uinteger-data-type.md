---
title: Uınteger veri türü (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df89c099042de8acef687a5fd11fc0dbf7de86a7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733007"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="769fc-102">UInteger veri türü</span><span class="sxs-lookup"><span data-stu-id="769fc-102">UInteger data type</span></span>

<span data-ttu-id="769fc-103">Değeri 0'dan 4.294.967.295'e arasında değişen ayrı tutma işaretsiz 32-bit (4-bayt) tam sayı.</span><span class="sxs-lookup"><span data-stu-id="769fc-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="769fc-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="769fc-104">Remarks</span></span>

 <span data-ttu-id="769fc-105">`UInteger` Veri türünü işaretsiz en büyük değeri en verimli veri genişliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="769fc-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="769fc-106">Varsayılan değer olan `UInteger` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="769fc-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="769fc-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="769fc-107">Literal assignments</span></span>

<span data-ttu-id="769fc-108">Bildirmek ve başlatmak bir `UInteger` değişkenini, bir ondalık sabit değeri, onaltılık bir sabit değer, sekizlik bir sabit değer atama ya da (ikili değişmez değer Visual Basic 2017'den itibaren).</span><span class="sxs-lookup"><span data-stu-id="769fc-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="769fc-109">Tamsayı sabit değeri aralığının dışında ise `UInteger` (diğer bir deyişle, bu ise kısa <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="769fc-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="769fc-110">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 3,000,000,000 eşit ve ikili sabit değerler atanır `UInteger` değerleri.</span><span class="sxs-lookup"><span data-stu-id="769fc-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="769fc-111">Önek kullanın `&h` veya `&H` önek onaltılık bir sabit belirtmek için `&b` veya `&B` ikili sabit ve öneki belirtmek için `&o` veya `&O` sekizlik bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="769fc-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="769fc-112">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="769fc-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="769fc-113">Visual Basic 2017'den itibaren alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliği artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="769fc-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="769fc-114">Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="769fc-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="769fc-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="769fc-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="769fc-116">Sayısal değişmez değerleri de dahil edebilirsiniz `UI` veya `ui` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `UInteger` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="769fc-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="769fc-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="769fc-117">Programming tips</span></span>

 <span data-ttu-id="769fc-118">`UInteger` Ve `Integer` veri türleri olduğundan bu en iyi performansı bir 32-bit işlemci üzerinde sağlamak daha küçük tamsayı türleri (`UShort`, `Short`, `Byte`, ve `SByte`), daha az BITS kullandıkları olsa bile daha fazla sürebilir Yükleme, depolama ve getirme.</span><span class="sxs-lookup"><span data-stu-id="769fc-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
-   <span data-ttu-id="769fc-119">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="769fc-119">**Negative Numbers.**</span></span> <span data-ttu-id="769fc-120">Çünkü `UInteger` işaretsiz bir türü, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="769fc-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="769fc-121">Tek işlenenli eksi işareti kullanırsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `UInteger`, Visual Basic ifade dönüştürür `Long` ilk.</span><span class="sxs-lookup"><span data-stu-id="769fc-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
-   <span data-ttu-id="769fc-122">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="769fc-122">**CLS Compliance.**</span></span> <span data-ttu-id="769fc-123">`UInteger` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), böylece onu kullanan bileşen CLS uyumlu kod kullanamıyor.</span><span class="sxs-lookup"><span data-stu-id="769fc-123">The `UInteger` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="769fc-124">**Birlikte çalışabilirlik değerlendirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="769fc-124">**Interop Considerations.**</span></span> <span data-ttu-id="769fc-125">Örnek otomasyon ve COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim, gibi türleri akılda tutulması `uint` diğer ortamlarda farklı veri genişliği (16 bit) olabilir.</span><span class="sxs-lookup"><span data-stu-id="769fc-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="769fc-126">Bir 16 bit bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `UShort` yerine `UInteger` Yönetilen Visual Basic kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="769fc-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
-   <span data-ttu-id="769fc-127">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="769fc-127">**Widening.**</span></span> <span data-ttu-id="769fc-128">`UInteger` Widens veri türü için `Long`, `ULong`, `Decimal`, `Single`, ve `Double`.</span><span class="sxs-lookup"><span data-stu-id="769fc-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="769fc-129">Yani dönüştürebilirsiniz `UInteger` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="769fc-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="769fc-130">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="769fc-130">**Type Characters.**</span></span> <span data-ttu-id="769fc-131">Değişmez değer türü karakterleri ekleme `UI` sabit değerine zorlar `UInteger` veri türü.</span><span class="sxs-lookup"><span data-stu-id="769fc-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="769fc-132">`UInteger` hiçbir tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="769fc-132">`UInteger` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="769fc-133">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="769fc-133">**Framework Type.**</span></span> <span data-ttu-id="769fc-134">.NET Framework içinde karşılık gelen türü <xref:System.UInt32?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="769fc-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769fc-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="769fc-135">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="769fc-136">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="769fc-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="769fc-137">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="769fc-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="769fc-138">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="769fc-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="769fc-139">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="769fc-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="769fc-140">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="769fc-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
