---
title: Long Veri Türü
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
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400815"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="6022e-102">Uzun veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6022e-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="6022e-103">-9.223.372.036.854.775.808 ile 9.223.036.854.775.807 (9.2...E+18) değerinde 64 bit (8 bayt) tümleç ler imzalı tutar.</span><span class="sxs-lookup"><span data-stu-id="6022e-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="6022e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6022e-104">Remarks</span></span>

<span data-ttu-id="6022e-105">`Integer` Veri türüne `Long` sığmayacak kadar büyük tamsayı numaraları içerecek şekilde veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="6022e-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="6022e-106">Varsayılan değeri `Long` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="6022e-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="6022e-107">Gerçek atamalar</span><span class="sxs-lookup"><span data-stu-id="6022e-107">Literal assignments</span></span>

<span data-ttu-id="6022e-108">Bir `Long` değişkeni ondalık edebi, hekzadesmal literal, sekizli bir literal veya (Visual Basic 2017 ile başlayan) ikili bir edebi olarak atayarak bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6022e-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="6022e-109">Tamsayı literal aralığının `Long` dışında ysa (yani, daha az <xref:System.Int64.MinValue?displayProperty=nameWithType> veya daha <xref:System.Int64.MaxValue?displayProperty=nameWithType>büyükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="6022e-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="6022e-110">Aşağıdaki örnekte, ondalık, heksadesibel ve ikili edebi değerlerolarak temsil edilen 4.294.967.296'ya `Long` eşit tamsayılar atamıştır.</span><span class="sxs-lookup"><span data-stu-id="6022e-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="6022e-111">`&h` Önek'i veya `&H` hexadecimal literal'ı, önek'i `&b` `&B` veya ikili bir edebi yi `&o` belirtmek `&O` için ve önek'i veya bir sekizli edebi yi belirtmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6022e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="6022e-112">Ondalık edebi hiçbir önek var.</span><span class="sxs-lookup"><span data-stu-id="6022e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="6022e-113">Visual Basic 2017'den başlayarak, aşağıdaki örnekte de görüldüğü gibi okunabilirliği artırmak için alt puan `_`karakterini, basamak ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6022e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="6022e-114">Visual Basic 15.5 ile başlayarak, önek`_`ile heksadecimal, ikili veya sekizli basamaklar arasında baş ayırıcı olarak alt çizilme karakterini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6022e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="6022e-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6022e-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="6022e-116">Sayısal literals, aşağıdaki örnekte görüldüğü `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Long` gibi, veri türünü ifade etmek için tür karakterini de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6022e-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="6022e-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="6022e-117">Programming tips</span></span>

- <span data-ttu-id="6022e-118">**Interop Hususlar.**</span><span class="sxs-lookup"><span data-stu-id="6022e-118">**Interop Considerations.**</span></span> <span data-ttu-id="6022e-119">.NET Framework için yazılmayan bileşenlerle (örneğin Otomasyon veya COM nesneleri) `Long` bir araya geldiyseniz, diğer ortamlarda farklı veri genişliğine (32 bit) sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6022e-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="6022e-120">Böyle bir bileşene 32 bitlik bir bağımsız değişken `Integer` geçiyorsanız, bunu yeni Visual Basic kodunuzda değil, `Long` olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="6022e-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="6022e-121">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="6022e-121">**Widening.**</span></span> <span data-ttu-id="6022e-122">Veri `Long` türü `Decimal`, veya `Single` `Double`.</span><span class="sxs-lookup"><span data-stu-id="6022e-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="6022e-123">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `Long` hatayla karşılaşmadan bu türlerden herhangi birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6022e-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="6022e-124">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="6022e-124">**Type Characters.**</span></span> <span data-ttu-id="6022e-125">Gerçek tür karakterini `L` bir edebi karaktere ekler, `Long` onu veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="6022e-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="6022e-126">Tanımlayıcı türü karakterini `&` herhangi bir tanımlayıcıya `Long`ekolarak .</span><span class="sxs-lookup"><span data-stu-id="6022e-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="6022e-127">**Çerçeve Türü.**</span><span class="sxs-lookup"><span data-stu-id="6022e-127">**Framework Type.**</span></span> <span data-ttu-id="6022e-128">.NET Framework'de karşılık gelen <xref:System.Int64?displayProperty=nameWithType> tür yapıdır.</span><span class="sxs-lookup"><span data-stu-id="6022e-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="6022e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6022e-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="6022e-130">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="6022e-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="6022e-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="6022e-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="6022e-132">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="6022e-132">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="6022e-133">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6022e-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="6022e-134">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="6022e-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="6022e-135">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="6022e-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
