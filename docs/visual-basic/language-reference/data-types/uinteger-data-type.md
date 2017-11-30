---
title: "UInteger Veri Türü"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.uinteger
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
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f3852bd56d11c19e327e6c2f3e23cfb082a54e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="uinteger-data-type"></a><span data-ttu-id="18b97-102">UInteger veri türü</span><span class="sxs-lookup"><span data-stu-id="18b97-102">UInteger data type</span></span>

<span data-ttu-id="18b97-103">Değer 0 ile 4.294.967.295 arasında değişen ayrı tutma işaretsiz 32-bit (4-bayt) tamsayı.</span><span class="sxs-lookup"><span data-stu-id="18b97-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18b97-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18b97-104">Remarks</span></span>

 <span data-ttu-id="18b97-105">`UInteger` Veri türü imzasız en büyük değeri en verimli veri genişliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="18b97-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="18b97-106">Varsayılan değer olan `UInteger` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="18b97-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="18b97-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="18b97-107">Literal assignments</span></span>

<span data-ttu-id="18b97-108">Bildirme ve başlatma bir `UInteger` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak).</span><span class="sxs-lookup"><span data-stu-id="18b97-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="18b97-109">Değişmez değer tamsayı aralığı dışında ise `UInteger` (diğer bir deyişle, bu ise değerinden <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="18b97-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="18b97-110">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 3,000,000,000 tamsayılar eşit ve ikili değişmez değerler atanır `UInteger` değerleri.</span><span class="sxs-lookup"><span data-stu-id="18b97-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="18b97-111">Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="18b97-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="18b97-112">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="18b97-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="18b97-113">Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="18b97-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="18b97-114">Sayısal değişmez değerleri de dahil edebilirsiniz `UI` veya `ui` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `UInteger` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="18b97-114">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H0FAC14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="18b97-115">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="18b97-115">Programming tips</span></span>

 <span data-ttu-id="18b97-116">`UInteger` Ve `Integer` veri türleri için bu en iyi performansı bir 32-bit işlemci sağlayan küçük tamsayı türleri (`UShort`, `Short`, `Byte`, ve `SByte`), daha az BITS kullanmasına karşın daha uzun yüklemek için depolama ve getirme.</span><span class="sxs-lookup"><span data-stu-id="18b97-116">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
-   <span data-ttu-id="18b97-117">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="18b97-117">**Negative Numbers.**</span></span> <span data-ttu-id="18b97-118">Çünkü `UInteger` imzasız bir tür negatif bir sayı temsil edilemez.</span><span class="sxs-lookup"><span data-stu-id="18b97-118">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="18b97-119">Tekli eksi kullanıyorsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `UInteger`, Visual Basic ifade dönüştürür `Long` ilk.</span><span class="sxs-lookup"><span data-stu-id="18b97-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
-   <span data-ttu-id="18b97-120">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="18b97-120">**CLS Compliance.**</span></span> <span data-ttu-id="18b97-121">`UInteger` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), CLS uyumlu kod kullandığı bir bileşen kullanamayacaklarını şekilde.</span><span class="sxs-lookup"><span data-stu-id="18b97-121">The `UInteger` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="18b97-122">**Birlikte çalışma hakkında dikkat edilecek noktalar**</span><span class="sxs-lookup"><span data-stu-id="18b97-122">**Interop Considerations.**</span></span> <span data-ttu-id="18b97-123">Örnek otomasyon veya COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim varsa gibi türleri göz önünde bulundurmanız `uint` farklı veri genişliği (16 bit) diğer ortamlarda olabilir.</span><span class="sxs-lookup"><span data-stu-id="18b97-123">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="18b97-124">Bir 16 bit bağımsız değişkeni tür bileşen geçirilirse, olarak bildirme `UShort` yerine `UInteger` Yönetilen Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="18b97-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
-   <span data-ttu-id="18b97-125">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="18b97-125">**Widening.**</span></span> <span data-ttu-id="18b97-126">`UInteger` Veri türü widens için `Long`, `ULong`, `Decimal`, `Single`, ve `Double`.</span><span class="sxs-lookup"><span data-stu-id="18b97-126">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="18b97-127">Bu dönüştürebilirsiniz anlamına gelir `UInteger` karşılaşmadan olmadan bu türdeki herhangi bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="18b97-127">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="18b97-128">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="18b97-128">**Type Characters.**</span></span> <span data-ttu-id="18b97-129">Değişmez değer türü karakterleri ekleme `UI` bir hazır değer zorlar `UInteger` veri türü.</span><span class="sxs-lookup"><span data-stu-id="18b97-129">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="18b97-130">`UInteger`hiçbir tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="18b97-130">`UInteger` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="18b97-131">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="18b97-131">**Framework Type.**</span></span> <span data-ttu-id="18b97-132">.NET Framework'teki karşılık gelen tür <xref:System.UInt32?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="18b97-132">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b97-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18b97-133">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="18b97-134">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="18b97-134">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="18b97-135">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="18b97-135">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="18b97-136">Dönüştürme özeti</span><span class="sxs-lookup"><span data-stu-id="18b97-136">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="18b97-137">Nasıl yapılır: imzalanmamış türler isteyen bir Windows işlevi çağırma</span><span class="sxs-lookup"><span data-stu-id="18b97-137">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="18b97-138">Veri türlerinin etkili kullanımı</span><span class="sxs-lookup"><span data-stu-id="18b97-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
