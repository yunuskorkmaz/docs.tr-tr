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
ms.openlocfilehash: 7c076cd2198c85560f7c63c69e051697966c9524
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415602"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="2d50a-102">Long veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d50a-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="2d50a-103">-9223372036854775808 ile 9.223.372.036.854.775.807 (9.2... E + 18) değerinde değişen 64 bitlik (8 baytlık) tamsayıları barındırır.</span><span class="sxs-lookup"><span data-stu-id="2d50a-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="2d50a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d50a-104">Remarks</span></span>

<span data-ttu-id="2d50a-105">Veri türüne `Long` sığmayacak kadar büyük olan tamsayı sayılarını içermesi için veri türünü kullanın `Integer` .</span><span class="sxs-lookup"><span data-stu-id="2d50a-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="2d50a-106">Varsayılan değeri 0 ' `Long` dır.</span><span class="sxs-lookup"><span data-stu-id="2d50a-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="2d50a-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="2d50a-107">Literal assignments</span></span>

<span data-ttu-id="2d50a-108">Bir `Long` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d50a-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="2d50a-109">Tamsayı sabit değeri aralığın dışındaysa `Long` (diğer bir deyişle, değerinden küçükse <xref:System.Int64.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.Int64.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="2d50a-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="2d50a-110">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 4.294.967.296 'e eşit tamsayılar `Long` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="2d50a-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="2d50a-111">Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2d50a-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="2d50a-112">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="2d50a-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2d50a-113">Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d50a-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="2d50a-114">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d50a-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="2d50a-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2d50a-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="2d50a-116">Sayısal değişmez değerler, `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) `Long` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de tür karakterini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2d50a-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="2d50a-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="2d50a-117">Programming tips</span></span>

- <span data-ttu-id="2d50a-118">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="2d50a-118">**Interop Considerations.**</span></span> <span data-ttu-id="2d50a-119">.NET Framework için yazılmayan bileşenlerle (örneğin, Otomasyon veya COM nesneleri) arabirimleriniz varsa, `Long` diğer ortamlarda farklı bir veri genişliğine (32 bit) sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2d50a-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="2d50a-120">Böyle bir bileşene 32 bitlik bir bağımsız değişken geçirıyorsanız, bunu `Integer` `Long` Yeni Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="2d50a-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="2d50a-121">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="2d50a-121">**Widening.**</span></span> <span data-ttu-id="2d50a-122">`Long`Veri türü widens, `Decimal` `Single` , veya `Double` .</span><span class="sxs-lookup"><span data-stu-id="2d50a-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="2d50a-123">Bu, `Long` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2d50a-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="2d50a-124">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="2d50a-124">**Type Characters.**</span></span> <span data-ttu-id="2d50a-125">Değişmez değer türü karakterini `L` bir sabit değere eklemek, `Long` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="2d50a-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="2d50a-126">Tanımlayıcı türü karakteri `&` herhangi bir tanımlayıcıya eklemek bunu öğesine zorlar `Long` .</span><span class="sxs-lookup"><span data-stu-id="2d50a-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="2d50a-127">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="2d50a-127">**Framework Type.**</span></span> <span data-ttu-id="2d50a-128">.NET Framework karşılık gelen tür <xref:System.Int64?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="2d50a-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d50a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d50a-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="2d50a-130">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="2d50a-130">Data Types</span></span>](index.md)
- [<span data-ttu-id="2d50a-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2d50a-131">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="2d50a-132">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2d50a-132">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="2d50a-133">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2d50a-133">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="2d50a-134">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="2d50a-134">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="2d50a-135">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="2d50a-135">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
