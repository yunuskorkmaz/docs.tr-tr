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
ms.openlocfilehash: 520c21d4df5c340b41a8b1e9055b3fadddfdf6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590374"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="44775-102">UShort veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44775-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="44775-103">Değer 0'dan 65.535 arasında değişen ayrı tutma işaretsiz 16-bit (2-bayt) tamsayı.</span><span class="sxs-lookup"><span data-stu-id="44775-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44775-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44775-104">Remarks</span></span>

 <span data-ttu-id="44775-105">Kullanım `UShort` veri türü için çok büyük ikili verileri içerecek şekilde `Byte`.</span><span class="sxs-lookup"><span data-stu-id="44775-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="44775-106">Varsayılan değer olan `UShort` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="44775-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="44775-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="44775-107">Literal assignments</span></span>

<span data-ttu-id="44775-108">Bildirme ve başlatma bir `UShort` değişken bir ondalık değişmez değeri, onaltılık değişmez değeri bir sekizlik değişmez değeri atama veya (Visual Basic 2017 ile ikili bir hazır değer başlayarak).</span><span class="sxs-lookup"><span data-stu-id="44775-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="44775-109">Değişmez değer tamsayı aralığı dışında ise `UShort` (diğer bir deyişle, bu ise değerinden <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="44775-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="44775-110">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 65,034 tamsayılar eşit ve ikili değişmez değerler atanır `UShort` değerleri.</span><span class="sxs-lookup"><span data-stu-id="44775-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="44775-111">Önek kullanması `&h` veya `&H` bir onaltılık değişmez değeri, öneki belirtmek için `&b` veya `&B` ikili bir hazır değer ve öneki belirtmek için `&o` veya `&O` sekizlik değişmez değeri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="44775-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="44775-112">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="44775-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="44775-113">Visual Basic 2017 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz `_`, okunabilirliğini artırmak için bir basamak ayırıcı olarak, aşağıdaki örnekte görüldüğü gibi.</span><span class="sxs-lookup"><span data-stu-id="44775-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="44775-114">Visual Basic 15,5 ile başlayarak, alt çizgi karakterini de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizli basamak arasında başında ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="44775-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="44775-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="44775-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="44775-116">Sayısal değişmez değerleri de dahil edebilirsiniz `US` veya `us` [türü karakteri](../../programming-guide\language-features\data-types/type-characters.md) belirtmek için `UShort` aşağıdaki örnekte gösterildiği gibi veri türü.</span><span class="sxs-lookup"><span data-stu-id="44775-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="44775-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="44775-117">Programming tips</span></span>
  
-   <span data-ttu-id="44775-118">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="44775-118">**Negative Numbers.**</span></span> <span data-ttu-id="44775-119">Çünkü `UShort` imzasız bir tür negatif bir sayı temsil edilemez.</span><span class="sxs-lookup"><span data-stu-id="44775-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="44775-120">Tekli eksi kullanıyorsanız (`-`) yazmak için değerlendirilen bir ifade işlecinin `UShort`, Visual Basic ifade dönüştürür `Integer` ilk.</span><span class="sxs-lookup"><span data-stu-id="44775-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="44775-121">**CLS uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="44775-121">**CLS Compliance.**</span></span> <span data-ttu-id="44775-122">`UShort` Veri türü değil parçası [ortak dil belirtimi](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), CLS uyumlu kod kullandığı bir bileşen kullanamayacaklarını şekilde.</span><span class="sxs-lookup"><span data-stu-id="44775-122">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="44775-123">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="44775-123">**Widening.**</span></span> <span data-ttu-id="44775-124">`UShort` Veri türü widens için `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, ve `Double`.</span><span class="sxs-lookup"><span data-stu-id="44775-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="44775-125">Bu dönüştürebilirsiniz anlamına gelir `UShort` karşılaşmadan olmadan bu türdeki herhangi bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="44775-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="44775-126">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="44775-126">**Type Characters.**</span></span> <span data-ttu-id="44775-127">Değişmez değer türü karakterleri ekleme `US` bir hazır değer zorlar `UShort` veri türü.</span><span class="sxs-lookup"><span data-stu-id="44775-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="44775-128">`UShort` hiçbir tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="44775-128">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="44775-129">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="44775-129">**Framework Type.**</span></span> <span data-ttu-id="44775-130">.NET Framework'teki karşılık gelen tür <xref:System.UInt16?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="44775-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44775-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44775-131">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="44775-132">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="44775-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="44775-133">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="44775-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="44775-134">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="44775-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="44775-135">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="44775-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="44775-136">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="44775-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
