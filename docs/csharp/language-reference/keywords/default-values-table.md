---
title: Varsayılan değerler tablosu (C# Başvurusu)
description: Varsayılan Oluşturucu tarafından döndürülen değer türlerinin varsayılan değerleri ne olduğunu öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218796"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="f1c52-103">Varsayılan değerler tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f1c52-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="f1c52-104">Aşağıdaki tabloda, varsayılan oluşturucular tarafından döndürülen değer türlerinin varsayılan değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1c52-104">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="f1c52-105">Varsayılan Oluşturucu çağrılır kullanarak `new` şekilde işleci:</span><span class="sxs-lookup"><span data-stu-id="f1c52-105">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="f1c52-106">Önceki deyimi aşağıdaki ifadeyi aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f1c52-106">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="f1c52-107">Başlatılmamış değişkenleri C# kullanarak verilmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f1c52-107">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="f1c52-108">Değer türü</span><span class="sxs-lookup"><span data-stu-id="f1c52-108">Value type</span></span>|<span data-ttu-id="f1c52-109">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="f1c52-109">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="f1c52-110">bool</span><span class="sxs-lookup"><span data-stu-id="f1c52-110">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="f1c52-111">byte</span><span class="sxs-lookup"><span data-stu-id="f1c52-111">byte</span></span>](byte.md)|<span data-ttu-id="f1c52-112">0</span><span class="sxs-lookup"><span data-stu-id="f1c52-112">0</span></span>|
|[<span data-ttu-id="f1c52-113">char</span><span class="sxs-lookup"><span data-stu-id="f1c52-113">char</span></span>](char.md)|<span data-ttu-id="f1c52-114">'\0'</span><span class="sxs-lookup"><span data-stu-id="f1c52-114">'\0'</span></span>|
|[<span data-ttu-id="f1c52-115">decimal</span><span class="sxs-lookup"><span data-stu-id="f1c52-115">decimal</span></span>](decimal.md)|<span data-ttu-id="f1c52-116">0M</span><span class="sxs-lookup"><span data-stu-id="f1c52-116">0M</span></span>|
|[<span data-ttu-id="f1c52-117">double</span><span class="sxs-lookup"><span data-stu-id="f1c52-117">double</span></span>](double.md)|<span data-ttu-id="f1c52-118">0,0 D</span><span class="sxs-lookup"><span data-stu-id="f1c52-118">0.0D</span></span>|
|[<span data-ttu-id="f1c52-119">enum</span><span class="sxs-lookup"><span data-stu-id="f1c52-119">enum</span></span>](enum.md)|<span data-ttu-id="f1c52-120">Burada E enum tanımlayıcısıdır (E) 0, deyim tarafından üretilen değeri.</span><span class="sxs-lookup"><span data-stu-id="f1c52-120">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="f1c52-121">float</span><span class="sxs-lookup"><span data-stu-id="f1c52-121">float</span></span>](float.md)|<span data-ttu-id="f1c52-122">0.0F</span><span class="sxs-lookup"><span data-stu-id="f1c52-122">0.0F</span></span>|
|[<span data-ttu-id="f1c52-123">int</span><span class="sxs-lookup"><span data-stu-id="f1c52-123">int</span></span>](int.md)|<span data-ttu-id="f1c52-124">0</span><span class="sxs-lookup"><span data-stu-id="f1c52-124">0</span></span>|
|[<span data-ttu-id="f1c52-125">long</span><span class="sxs-lookup"><span data-stu-id="f1c52-125">long</span></span>](long.md)|<span data-ttu-id="f1c52-126">0 M</span><span class="sxs-lookup"><span data-stu-id="f1c52-126">0L</span></span>|
|[<span data-ttu-id="f1c52-127">sbyte</span><span class="sxs-lookup"><span data-stu-id="f1c52-127">sbyte</span></span>](sbyte.md)|<span data-ttu-id="f1c52-128">0</span><span class="sxs-lookup"><span data-stu-id="f1c52-128">0</span></span>|
|[<span data-ttu-id="f1c52-129">short</span><span class="sxs-lookup"><span data-stu-id="f1c52-129">short</span></span>](short.md)|<span data-ttu-id="f1c52-130">0</span><span class="sxs-lookup"><span data-stu-id="f1c52-130">0</span></span>|
|[<span data-ttu-id="f1c52-131">struct</span><span class="sxs-lookup"><span data-stu-id="f1c52-131">struct</span></span>](struct.md)|<span data-ttu-id="f1c52-132">Değer üretilen tüm değer tür alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak `null`.</span><span class="sxs-lookup"><span data-stu-id="f1c52-132">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="f1c52-133">uint</span><span class="sxs-lookup"><span data-stu-id="f1c52-133">uint</span></span>](uint.md)|<span data-ttu-id="f1c52-134">0</span><span class="sxs-lookup"><span data-stu-id="f1c52-134">0</span></span>|
|[<span data-ttu-id="f1c52-135">ulong</span><span class="sxs-lookup"><span data-stu-id="f1c52-135">ulong</span></span>](ulong.md)|<span data-ttu-id="f1c52-136">0</span><span class="sxs-lookup"><span data-stu-id="f1c52-136">0</span></span>|
|[<span data-ttu-id="f1c52-137">ushort</span><span class="sxs-lookup"><span data-stu-id="f1c52-137">ushort</span></span>](ushort.md)|<span data-ttu-id="f1c52-138">0</span><span class="sxs-lookup"><span data-stu-id="f1c52-138">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="f1c52-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1c52-139">See also</span></span>
 [<span data-ttu-id="f1c52-140">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f1c52-140">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="f1c52-141">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f1c52-141">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="f1c52-142">Değer Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="f1c52-142">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="f1c52-143">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="f1c52-143">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="f1c52-144">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="f1c52-144">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="f1c52-145">Türler için Başvuru Tabloları</span><span class="sxs-lookup"><span data-stu-id="f1c52-145">Reference Tables for Types</span></span>](reference-tables-for-types.md)
