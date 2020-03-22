---
title: UShort Veri Türü
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
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400696"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="70074-102">UShort veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70074-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="70074-103">0 ile 65.535 arasında değişen imzasız 16 bit (2 bayt) tümsedoları tutar.</span><span class="sxs-lookup"><span data-stu-id="70074-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70074-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70074-104">Remarks</span></span>

 <span data-ttu-id="70074-105">`UShort` Için çok büyük ikili veri içerecek `Byte`şekilde veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="70074-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="70074-106">Varsayılan değeri `UShort` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="70074-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="70074-107">Gerçek atamalar</span><span class="sxs-lookup"><span data-stu-id="70074-107">Literal assignments</span></span>

<span data-ttu-id="70074-108">Bir `UShort` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70074-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="70074-109">Tamsayı literal aralığının `UShort` dışında ysa (yani, daha az <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya daha <xref:System.UInt16.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="70074-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="70074-110">Aşağıdaki örnekte, ondalık, heksadeondamal ve ikili literaller olarak temsil edilen 65.034'e eşit tamsayılar değerlere `UShort` atanır.</span><span class="sxs-lookup"><span data-stu-id="70074-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="70074-111">`&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="70074-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="70074-112">Ondalık edebi hiçbir önek var.</span><span class="sxs-lookup"><span data-stu-id="70074-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="70074-113">Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70074-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="70074-114">Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70074-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="70074-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="70074-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="70074-116">Sayısal literals, aşağıdaki `US` örnekte `us` görüldüğü `UShort` gibi, veri türünü ifade etmek için veya [türü karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="70074-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="70074-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="70074-117">Programming tips</span></span>
  
- <span data-ttu-id="70074-118">**Negatif Sayılar.**</span><span class="sxs-lookup"><span data-stu-id="70074-118">**Negative Numbers.**</span></span> <span data-ttu-id="70074-119">İmzalanmamış bir tür `UShort` olduğundan, negatif bir sayıyı temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="70074-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="70074-120">Unary eksi (`-`) işleci, yazmayı `UShort`değerlendiren bir ifadeüzerinde kullanırsanız, `Integer` Visual Basic ifadeyi önce dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="70074-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="70074-121">**CLS Uyumluluğu.**</span><span class="sxs-lookup"><span data-stu-id="70074-121">**CLS Compliance.**</span></span> <span data-ttu-id="70074-122">Veri `UShort` türü Ortak Dil [Belirtimi'nin](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketemez.</span><span class="sxs-lookup"><span data-stu-id="70074-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="70074-123">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="70074-123">**Widening.**</span></span> <span data-ttu-id="70074-124">Veri `UShort` `Integer`türü , , `UInteger` `Long` `ULong`, `Decimal`, `Single`, `Double`ve .</span><span class="sxs-lookup"><span data-stu-id="70074-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="70074-125">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `UShort` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="70074-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="70074-126">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="70074-126">**Type Characters.**</span></span> <span data-ttu-id="70074-127">Gerçek türdeki `US` karakterleri `UShort` bir edebi aygıta ekler, onu veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="70074-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="70074-128">`UShort`tanımlayıcı türü karakteri yoktur.</span><span class="sxs-lookup"><span data-stu-id="70074-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="70074-129">**Çerçeve Türü.**</span><span class="sxs-lookup"><span data-stu-id="70074-129">**Framework Type.**</span></span> <span data-ttu-id="70074-130">.NET Framework'de karşılık gelen <xref:System.UInt16?displayProperty=nameWithType> tür yapıdır.</span><span class="sxs-lookup"><span data-stu-id="70074-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70074-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70074-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="70074-132">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="70074-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="70074-133">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="70074-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="70074-134">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="70074-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="70074-135">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="70074-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="70074-136">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="70074-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
