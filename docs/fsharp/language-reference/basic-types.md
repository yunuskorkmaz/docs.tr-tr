---
title: Temel Türler
description: 'F # dilinde kullanılan temel temel türleri bulur.'
ms.date: 08/15/2020
ms.openlocfilehash: 659ac8424c62985affcca1741e1b2a74c9c3ee8d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557704"
---
# <a name="basic-types"></a><span data-ttu-id="4374b-103">Temel türler</span><span class="sxs-lookup"><span data-stu-id="4374b-103">Basic types</span></span>

<span data-ttu-id="4374b-104">Bu konu, F # dilinde tanımlanan temel türleri listeler.</span><span class="sxs-lookup"><span data-stu-id="4374b-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="4374b-105">Bu türler, neredeyse her F # programının temelini oluşturan F # ' da en temel programdır.</span><span class="sxs-lookup"><span data-stu-id="4374b-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="4374b-106">Bunlar .NET temel türlerinin bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="4374b-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="4374b-107">Tür</span><span class="sxs-lookup"><span data-stu-id="4374b-107">Type</span></span>|<span data-ttu-id="4374b-108">.NET türü</span><span class="sxs-lookup"><span data-stu-id="4374b-108">.NET type</span></span>|<span data-ttu-id="4374b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4374b-109">Description</span></span>|<span data-ttu-id="4374b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4374b-110">Example</span></span>|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="4374b-111">Olası değerler şunlardır `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="4374b-111">Possible values are `true` and `false`.</span></span>|`true`/`false`|
|`byte`|<xref:System.Byte>|<span data-ttu-id="4374b-112">0 ile 255 arasında değerler.</span><span class="sxs-lookup"><span data-stu-id="4374b-112">Values from 0 to 255.</span></span>|`1uy`|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="4374b-113">-128 ile 127 arasındaki değerler.</span><span class="sxs-lookup"><span data-stu-id="4374b-113">Values from -128 to 127.</span></span>|`1y`|
|`int16`|<xref:System.Int16>|<span data-ttu-id="4374b-114">-32768 ile 32767 arasındaki değerler.</span><span class="sxs-lookup"><span data-stu-id="4374b-114">Values from -32768 to 32767.</span></span>|`1s`|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="4374b-115">0 ile 65535 arasında değerler.</span><span class="sxs-lookup"><span data-stu-id="4374b-115">Values from 0 to 65535.</span></span>|`1us`|
|`int`|<xref:System.Int32>|<span data-ttu-id="4374b-116">-2.147.483.648 ile 2.147.483.647 arasındaki değerler.</span><span class="sxs-lookup"><span data-stu-id="4374b-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|`1`|
|`uint`|<xref:System.UInt32>|<span data-ttu-id="4374b-117">0 ile 4.294.967.295 arasında değerler.</span><span class="sxs-lookup"><span data-stu-id="4374b-117">Values from 0 to 4,294,967,295.</span></span>|`1u`|
|`int64`|<xref:System.Int64>|<span data-ttu-id="4374b-118">-9223372036854775808-9.223.372.036.854.775.807 arası değerler.</span><span class="sxs-lookup"><span data-stu-id="4374b-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|`1L`|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="4374b-119">0 ile 18446744073709551615 arasında değerler.</span><span class="sxs-lookup"><span data-stu-id="4374b-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|`1UL`|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="4374b-120">İşaretli tamsayı olarak yerel bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4374b-120">A native pointer as a signed integer.</span></span>|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="4374b-121">İşaretsiz tamsayı olarak yerel bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4374b-121">A native pointer as an unsigned integer.</span></span>|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="4374b-122">En az 28 önemli basamağa sahip bir kayan nokta veri türü.</span><span class="sxs-lookup"><span data-stu-id="4374b-122">A floating point data type that has at least 28 significant digits.</span></span>|`1.0`|
|<span data-ttu-id="4374b-123">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="4374b-123">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="4374b-124">64 bitlik kayan nokta türü.</span><span class="sxs-lookup"><span data-stu-id="4374b-124">A 64-bit floating point type.</span></span>|`1.0`|
|<span data-ttu-id="4374b-125">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="4374b-125">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="4374b-126">32 bitlik kayan nokta türü.</span><span class="sxs-lookup"><span data-stu-id="4374b-126">A 32-bit floating point type.</span></span>|`1.0f`|
|`char`|<xref:System.Char>|<span data-ttu-id="4374b-127">Unicode karakter değerleri.</span><span class="sxs-lookup"><span data-stu-id="4374b-127">Unicode character values.</span></span>|`'c'`|
|`string`|<xref:System.String>|<span data-ttu-id="4374b-128">Unicode metin.</span><span class="sxs-lookup"><span data-stu-id="4374b-128">Unicode text.</span></span>|`"str"`|
|`unit`|<span data-ttu-id="4374b-129">uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="4374b-129">not applicable</span></span>|<span data-ttu-id="4374b-130">Gerçek değerin yokluğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4374b-130">Indicates the absence of an actual value.</span></span> <span data-ttu-id="4374b-131">Türün yalnızca bir biçimsel değeri vardır ve bu değer gösterilir `()` .</span><span class="sxs-lookup"><span data-stu-id="4374b-131">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="4374b-132">Birim değeri, `()` genellikle bir değerin gerekli olduğu ancak gerçek bir değer kullanılabilir olmayan bir yer tutucu olarak kullanılır veya anlamlı olur.</span><span class="sxs-lookup"><span data-stu-id="4374b-132">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|`()`|

> [!NOTE]
> <span data-ttu-id="4374b-133">[Tamsayı türü kullanılarak](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) 64 bitlik tamsayı türü için çok büyük tamsayılar içeren hesaplamalar yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4374b-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) type.</span></span> <span data-ttu-id="4374b-134">`bigint` temel tür olarak kabul edilmez; için bir kısaltmadır `System.Numerics.BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="4374b-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4374b-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4374b-135">See also</span></span>

- [<span data-ttu-id="4374b-136">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="4374b-136">F# Language Reference</span></span>](index.md)
