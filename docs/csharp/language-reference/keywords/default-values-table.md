---
title: Varsayılan değerler tablosu (C# Başvurusu)
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e249dd2f352fe6177f3afbfd089fc4dc9b1b7798
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="deb6e-102">Varsayılan değerler tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="deb6e-102">Default values table (C# Reference)</span></span>

<span data-ttu-id="deb6e-103">Aşağıdaki tabloda, varsayılan oluşturucular tarafından döndürülen değer türlerinin varsayılan değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="deb6e-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="deb6e-104">Varsayılan Oluşturucu çağrılır kullanarak `new` şekilde işleci:</span><span class="sxs-lookup"><span data-stu-id="deb6e-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="deb6e-105">Önceki deyimi aşağıdaki ifadeyi aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="deb6e-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="deb6e-106">Başlatılmamış değişkenleri C# kullanarak verilmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="deb6e-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="deb6e-107">Değer türü</span><span class="sxs-lookup"><span data-stu-id="deb6e-107">Value type</span></span>|<span data-ttu-id="deb6e-108">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="deb6e-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="deb6e-109">bool</span><span class="sxs-lookup"><span data-stu-id="deb6e-109">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="deb6e-110">byte</span><span class="sxs-lookup"><span data-stu-id="deb6e-110">byte</span></span>](byte.md)|<span data-ttu-id="deb6e-111">0</span><span class="sxs-lookup"><span data-stu-id="deb6e-111">0</span></span>|
|[<span data-ttu-id="deb6e-112">char</span><span class="sxs-lookup"><span data-stu-id="deb6e-112">char</span></span>](char.md)|<span data-ttu-id="deb6e-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="deb6e-113">'\0'</span></span>|
|[<span data-ttu-id="deb6e-114">decimal</span><span class="sxs-lookup"><span data-stu-id="deb6e-114">decimal</span></span>](decimal.md)|<span data-ttu-id="deb6e-115">0M</span><span class="sxs-lookup"><span data-stu-id="deb6e-115">0M</span></span>|
|[<span data-ttu-id="deb6e-116">double</span><span class="sxs-lookup"><span data-stu-id="deb6e-116">double</span></span>](double.md)|<span data-ttu-id="deb6e-117">0,0 D</span><span class="sxs-lookup"><span data-stu-id="deb6e-117">0.0D</span></span>|
|[<span data-ttu-id="deb6e-118">enum</span><span class="sxs-lookup"><span data-stu-id="deb6e-118">enum</span></span>](enum.md)|<span data-ttu-id="deb6e-119">Burada E enum tanımlayıcısıdır (E) 0, deyim tarafından üretilen değeri.</span><span class="sxs-lookup"><span data-stu-id="deb6e-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="deb6e-120">float</span><span class="sxs-lookup"><span data-stu-id="deb6e-120">float</span></span>](float.md)|<span data-ttu-id="deb6e-121">0.0F</span><span class="sxs-lookup"><span data-stu-id="deb6e-121">0.0F</span></span>|
|[<span data-ttu-id="deb6e-122">int</span><span class="sxs-lookup"><span data-stu-id="deb6e-122">int</span></span>](int.md)|<span data-ttu-id="deb6e-123">0</span><span class="sxs-lookup"><span data-stu-id="deb6e-123">0</span></span>|
|[<span data-ttu-id="deb6e-124">long</span><span class="sxs-lookup"><span data-stu-id="deb6e-124">long</span></span>](long.md)|<span data-ttu-id="deb6e-125">0 M</span><span class="sxs-lookup"><span data-stu-id="deb6e-125">0L</span></span>|
|[<span data-ttu-id="deb6e-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="deb6e-126">sbyte</span></span>](sbyte.md)|<span data-ttu-id="deb6e-127">0</span><span class="sxs-lookup"><span data-stu-id="deb6e-127">0</span></span>|
|[<span data-ttu-id="deb6e-128">short</span><span class="sxs-lookup"><span data-stu-id="deb6e-128">short</span></span>](short.md)|<span data-ttu-id="deb6e-129">0</span><span class="sxs-lookup"><span data-stu-id="deb6e-129">0</span></span>|
|[<span data-ttu-id="deb6e-130">struct</span><span class="sxs-lookup"><span data-stu-id="deb6e-130">struct</span></span>](struct.md)|<span data-ttu-id="deb6e-131">Değer üretilen tüm değer tür alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak `null`.</span><span class="sxs-lookup"><span data-stu-id="deb6e-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="deb6e-132">uint</span><span class="sxs-lookup"><span data-stu-id="deb6e-132">uint</span></span>](uint.md)|<span data-ttu-id="deb6e-133">0</span><span class="sxs-lookup"><span data-stu-id="deb6e-133">0</span></span>|
|[<span data-ttu-id="deb6e-134">ulong</span><span class="sxs-lookup"><span data-stu-id="deb6e-134">ulong</span></span>](ulong.md)|<span data-ttu-id="deb6e-135">0</span><span class="sxs-lookup"><span data-stu-id="deb6e-135">0</span></span>|
|[<span data-ttu-id="deb6e-136">ushort</span><span class="sxs-lookup"><span data-stu-id="deb6e-136">ushort</span></span>](ushort.md)|<span data-ttu-id="deb6e-137">0</span><span class="sxs-lookup"><span data-stu-id="deb6e-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="deb6e-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deb6e-138">See also</span></span>
 [<span data-ttu-id="deb6e-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="deb6e-139">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="deb6e-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="deb6e-140">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="deb6e-141">Değer Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="deb6e-141">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="deb6e-142">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="deb6e-142">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="deb6e-143">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="deb6e-143">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="deb6e-144">Türler için Başvuru Tabloları</span><span class="sxs-lookup"><span data-stu-id="deb6e-144">Reference Tables for Types</span></span>](reference-tables-for-types.md)
