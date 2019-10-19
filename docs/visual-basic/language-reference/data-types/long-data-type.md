---
title: Long Veri Türü (Visual Basic)
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
ms.openlocfilehash: efbe54c2495d05e8fe215690f60ba3c7ea9cfef6
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582521"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="bbaec-102">Long veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbaec-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="bbaec-103">-9223372036854775808 ile 9.223.372.036.854.775.807 (9.2... E + 18) değerinde değişen 64 bitlik (8 baytlık) tamsayıları barındırır.</span><span class="sxs-lookup"><span data-stu-id="bbaec-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="bbaec-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbaec-104">Remarks</span></span>

<span data-ttu-id="bbaec-105">@No__t_1 veri türüne sığamayacak kadar büyük tamsayı sayılar içermesi için `Long` veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="bbaec-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="bbaec-106">@No__t_0 varsayılan değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="bbaec-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="bbaec-107">Değişmez değer atamaları</span><span class="sxs-lookup"><span data-stu-id="bbaec-107">Literal assignments</span></span>

<span data-ttu-id="bbaec-108">Bir `Long` değişkenini bir ondalık değişmez değeri, onaltılı bir sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaec-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="bbaec-109">Tamsayı sabit değeri `Long` aralığının dışındaysa (yani, <xref:System.Int64.MinValue?displayProperty=nameWithType> veya <xref:System.Int64.MaxValue?displayProperty=nameWithType> değerinden daha küçükse, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="bbaec-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="bbaec-110">Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 4.294.967.296 'e eşit tamsayılar `Long` değerlere atanır.</span><span class="sxs-lookup"><span data-stu-id="bbaec-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="bbaec-111">Ön ek `&h` veya `&H` bir onaltılık sabit değeri, ön ek `&b` veya `&B` bir ikili sabit değer belirtmek için, önek `&o` veya `&O`, sekizlik bir sabit değeri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbaec-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="bbaec-112">Ondalık değişmez değerlerinin ön eki yok.</span><span class="sxs-lookup"><span data-stu-id="bbaec-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="bbaec-113">Visual Basic 2017 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için `_` alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaec-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="bbaec-114">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini (`_`) ön ek ile onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaec-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="bbaec-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bbaec-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="bbaec-116">Sayısal değişmez değerler, aşağıdaki örnekte gösterildiği gibi `Long` veri türünü belirtmek için `L` [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bbaec-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="bbaec-117">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="bbaec-117">Programming tips</span></span>

- <span data-ttu-id="bbaec-118">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="bbaec-118">**Interop Considerations.**</span></span> <span data-ttu-id="bbaec-119">.NET Framework için yazılmayan bileşenlerle (örneğin, Automation veya COM nesneleri) arabirimleriniz varsa, `Long` başka ortamlarda farklı bir veri genişliğine (32 bit) sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bbaec-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="bbaec-120">Böyle bir bileşene 32 bitlik bir bağımsız değişken geçirdiğinizden, bunu yeni Visual Basic kodunuzda `Long` yerine `Integer` olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="bbaec-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="bbaec-121">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="bbaec-121">**Widening.**</span></span> <span data-ttu-id="bbaec-122">@No__t_0 veri türü `Decimal`, `Single` veya `Double` için.</span><span class="sxs-lookup"><span data-stu-id="bbaec-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="bbaec-123">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Long` bu türlerden birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bbaec-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="bbaec-124">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="bbaec-124">**Type Characters.**</span></span> <span data-ttu-id="bbaec-125">Değişmez değer türü karakter `L` bir sabit değere eklenmesi, `Long` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="bbaec-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="bbaec-126">Tanımlayıcı türü karakter `&` herhangi bir tanımlayıcıya eklemek bunu `Long` zorlar.</span><span class="sxs-lookup"><span data-stu-id="bbaec-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="bbaec-127">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="bbaec-127">**Framework Type.**</span></span> <span data-ttu-id="bbaec-128">.NET Framework karşılık gelen tür <xref:System.Int64?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="bbaec-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbaec-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbaec-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="bbaec-130">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="bbaec-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="bbaec-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="bbaec-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="bbaec-132">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="bbaec-132">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="bbaec-133">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bbaec-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="bbaec-134">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="bbaec-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="bbaec-135">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="bbaec-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
