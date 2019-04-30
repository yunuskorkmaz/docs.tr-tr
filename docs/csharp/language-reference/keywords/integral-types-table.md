---
title: Tam sayı türleri tablosu - C# başvurusu
ms.custom: seodec18
description: Yerleşik C# tamsayı türleri'ne genel bakış
ms.date: 08/20/2018
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
ms.openlocfilehash: dc093def716a624162cb695d1151d8a722807094
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661379"
---
# <a name="integral-types-table-c-reference"></a><span data-ttu-id="00c7c-103">Tam sayı türleri tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="00c7c-103">Integral types table (C# Reference)</span></span>

<span data-ttu-id="00c7c-104">Aşağıdaki tabloda, boyutları ve basit türler kümesini oluşturan tam sayı türleri aralığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="00c7c-104">The following table shows the sizes and ranges of the integral types, which constitute a subset of simple types.</span></span>  
  
|<span data-ttu-id="00c7c-105">Tür</span><span class="sxs-lookup"><span data-stu-id="00c7c-105">Type</span></span>|<span data-ttu-id="00c7c-106">Aralık</span><span class="sxs-lookup"><span data-stu-id="00c7c-106">Range</span></span>|<span data-ttu-id="00c7c-107">Boyut</span><span class="sxs-lookup"><span data-stu-id="00c7c-107">Size</span></span>|  
|----------|-----------|----------|  
|[<span data-ttu-id="00c7c-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="00c7c-108">sbyte</span></span>](sbyte.md)|<span data-ttu-id="00c7c-109">-128 ila 127 arasında</span><span class="sxs-lookup"><span data-stu-id="00c7c-109">-128 to 127</span></span>|<span data-ttu-id="00c7c-110">İşaretli 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="00c7c-110">Signed 8-bit integer</span></span>|  
|[<span data-ttu-id="00c7c-111">byte</span><span class="sxs-lookup"><span data-stu-id="00c7c-111">byte</span></span>](byte.md)|<span data-ttu-id="00c7c-112">0 ile 255 arasında</span><span class="sxs-lookup"><span data-stu-id="00c7c-112">0 to 255</span></span>|<span data-ttu-id="00c7c-113">İmzalanmamış 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="00c7c-113">Unsigned 8-bit integer</span></span>|  
|[<span data-ttu-id="00c7c-114">char</span><span class="sxs-lookup"><span data-stu-id="00c7c-114">char</span></span>](char.md)|<span data-ttu-id="00c7c-115">U + 0000'u + ffff için</span><span class="sxs-lookup"><span data-stu-id="00c7c-115">U+0000 to U+ffff</span></span>|<span data-ttu-id="00c7c-116">Unicode 16-bit karakteri</span><span class="sxs-lookup"><span data-stu-id="00c7c-116">Unicode 16-bit character</span></span>|  
|[<span data-ttu-id="00c7c-117">short</span><span class="sxs-lookup"><span data-stu-id="00c7c-117">short</span></span>](short.md)|<span data-ttu-id="00c7c-118">-32.768 için 32.767</span><span class="sxs-lookup"><span data-stu-id="00c7c-118">-32,768 to 32,767</span></span>|<span data-ttu-id="00c7c-119">İşaretli 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="00c7c-119">Signed 16-bit integer</span></span>|  
|[<span data-ttu-id="00c7c-120">ushort</span><span class="sxs-lookup"><span data-stu-id="00c7c-120">ushort</span></span>](ushort.md)|<span data-ttu-id="00c7c-121">0 ile 65.535 arasındaki</span><span class="sxs-lookup"><span data-stu-id="00c7c-121">0 to 65,535</span></span>|<span data-ttu-id="00c7c-122">16 bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="00c7c-122">Unsigned 16-bit integer</span></span>|  
|[<span data-ttu-id="00c7c-123">int</span><span class="sxs-lookup"><span data-stu-id="00c7c-123">int</span></span>](int.md)|<span data-ttu-id="00c7c-124">-2.147.483.648 için 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="00c7c-124">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="00c7c-125">İşaretli 32 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="00c7c-125">Signed 32-bit integer</span></span>|  
|[<span data-ttu-id="00c7c-126">uint</span><span class="sxs-lookup"><span data-stu-id="00c7c-126">uint</span></span>](uint.md)|<span data-ttu-id="00c7c-127">0 için 4.294.967.295'e</span><span class="sxs-lookup"><span data-stu-id="00c7c-127">0 to 4,294,967,295</span></span>|<span data-ttu-id="00c7c-128">32-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="00c7c-128">Unsigned 32-bit integer</span></span>|  
|[<span data-ttu-id="00c7c-129">long</span><span class="sxs-lookup"><span data-stu-id="00c7c-129">long</span></span>](long.md)|<span data-ttu-id="00c7c-130">-9,223,372,036,854,775,808 için 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="00c7c-130">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="00c7c-131">İşaretli 64 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="00c7c-131">Signed 64-bit integer</span></span>|  
|[<span data-ttu-id="00c7c-132">ulong</span><span class="sxs-lookup"><span data-stu-id="00c7c-132">ulong</span></span>](ulong.md)|<span data-ttu-id="00c7c-133">0 için 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="00c7c-133">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="00c7c-134">64-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="00c7c-134">Unsigned 64-bit integer</span></span>|  

## <a name="remarks"></a><span data-ttu-id="00c7c-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00c7c-135">Remarks</span></span>
  
<span data-ttu-id="00c7c-136">Bir tamsayı sabit değeri tarafından temsil edilen değeri aşarsa <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, bir derleyici hatası [CS1021](../../misc/cs1021.md) gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="00c7c-136">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="00c7c-137">Kullanım <xref:System.Numerics.BigInteger?displayProperty=nameWithType> yapısını temsil eden büyük bir işaretli tamsayı.</span><span class="sxs-lookup"><span data-stu-id="00c7c-137">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent an arbitrarily large signed integer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="00c7c-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00c7c-138">See also</span></span>

- [<span data-ttu-id="00c7c-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="00c7c-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="00c7c-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="00c7c-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="00c7c-141">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="00c7c-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="00c7c-142">Türler için başvuru tabloları</span><span class="sxs-lookup"><span data-stu-id="00c7c-142">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="00c7c-143">Kayan nokta türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="00c7c-143">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="00c7c-144">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="00c7c-144">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="00c7c-145">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="00c7c-145">Formatting numeric results table</span></span>](formatting-numeric-results-table.md)
- [<span data-ttu-id="00c7c-146">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="00c7c-146">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="00c7c-147">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="00c7c-147">Numerics in .NET</span></span>](../../../standard/numerics.md)
