---
title: İlkel Türler (F#)
description: 'F # dilinde kullanılan temel ilkel türler bulur.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 7832151ee211f56547ecad98fc31f1454cb18870
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="primitive-types"></a><span data-ttu-id="c6f64-103">İlkel Türler</span><span class="sxs-lookup"><span data-stu-id="c6f64-103">Primitive Types</span></span>

<span data-ttu-id="c6f64-104">Bu konu F # dilinde kullanılan temel ilkel türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="c6f64-104">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="c6f64-105">Ayrıca karşılık gelen .NET türleri ve minimum ve maksimum değerleri her tür için sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6f64-105">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="c6f64-106">İlkel türler özeti</span><span class="sxs-lookup"><span data-stu-id="c6f64-106">Summary of Primitive Types</span></span>
<span data-ttu-id="c6f64-107">Aşağıdaki tabloda temel F # türleri özelliklerini özetler.</span><span class="sxs-lookup"><span data-stu-id="c6f64-107">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="c6f64-108">Tür</span><span class="sxs-lookup"><span data-stu-id="c6f64-108">Type</span></span>|<span data-ttu-id="c6f64-109">.NET türü</span><span class="sxs-lookup"><span data-stu-id="c6f64-109">.NET type</span></span>|<span data-ttu-id="c6f64-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6f64-110">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="c6f64-111">Olası değerler şunlardır: `true` ve `false`.</span><span class="sxs-lookup"><span data-stu-id="c6f64-111">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="c6f64-112">0 ile 255 değerleri.</span><span class="sxs-lookup"><span data-stu-id="c6f64-112">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="c6f64-113">127 -128 değerleri.</span><span class="sxs-lookup"><span data-stu-id="c6f64-113">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="c6f64-114">-32768 değerleri ile 32767 arasında.</span><span class="sxs-lookup"><span data-stu-id="c6f64-114">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="c6f64-115">0 ile 65535 değerleri.</span><span class="sxs-lookup"><span data-stu-id="c6f64-115">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="c6f64-116">2.147.483.647 değerleri 2,147,483,648.</span><span class="sxs-lookup"><span data-stu-id="c6f64-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="c6f64-117">4.294.967.295 için değerleri 0.</span><span class="sxs-lookup"><span data-stu-id="c6f64-117">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="c6f64-118">9,223,372,036,854,775,807 için-9,223,372,036,854,775,808 değerleri.</span><span class="sxs-lookup"><span data-stu-id="c6f64-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="c6f64-119">18,446,744,073,709,551,615 için değerleri 0.</span><span class="sxs-lookup"><span data-stu-id="c6f64-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="c6f64-120">İmzalı bir tamsayı olarak yerel bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c6f64-120">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="c6f64-121">İmzalanmamış tamsayı olarak yerel bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c6f64-121">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="c6f64-122">Unicode karakter değerleri.</span><span class="sxs-lookup"><span data-stu-id="c6f64-122">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="c6f64-123">Unicode metin.</span><span class="sxs-lookup"><span data-stu-id="c6f64-123">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="c6f64-124">Kayan nokta en az 28 basamaktan oluşur veri türü.</span><span class="sxs-lookup"><span data-stu-id="c6f64-124">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="c6f64-125">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="c6f64-125">not applicable</span></span>|<span data-ttu-id="c6f64-126">Gerçek bir değer yokluğu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6f64-126">Indicates the absence of an actual value.</span></span> <span data-ttu-id="c6f64-127">Gösterilir tek bir resmi değer türüne sahip `()`.</span><span class="sxs-lookup"><span data-stu-id="c6f64-127">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="c6f64-128">Birim değeri `()`, çoğunlukla burada bir değer gerekli ancak herhangi bir gerçek değer kullanılabilir veya anlamlı bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6f64-128">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="c6f64-129">Hiçbir tür veya değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6f64-129">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="c6f64-130">Bir 32 bit kayan nokta türü.</span><span class="sxs-lookup"><span data-stu-id="c6f64-130">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="c6f64-131">Bir 64-bit kayan nokta türü.</span><span class="sxs-lookup"><span data-stu-id="c6f64-131">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="c6f64-132">Kullanarak 64-bit tamsayı türü için çok büyük tamsayılı hesaplamalar gerçekleştirebilirsiniz [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) türü.</span><span class="sxs-lookup"><span data-stu-id="c6f64-132">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="c6f64-133">`bigint` Basit tür olarak kabul edilmez; ifadesinin kısaltmasıdır `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="c6f64-133">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6f64-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6f64-134">See Also</span></span>
[<span data-ttu-id="c6f64-135">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c6f64-135">F# Language Reference</span></span>](index.md)
