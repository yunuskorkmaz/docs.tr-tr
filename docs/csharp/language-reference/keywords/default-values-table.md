---
title: "Varsayılan değerler tablosu (C# Başvurusu)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
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
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034c1daf495c50e299fec4c5bf399652dad08ce
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2017
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="96512-102">Varsayılan değerler tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="96512-102">Default values table (C# Reference)</span></span>
<span data-ttu-id="96512-103">Aşağıdaki tabloda, varsayılan oluşturucular tarafından döndürülen değer türlerinin varsayılan değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="96512-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="96512-104">Varsayılan Oluşturucu çağrılır kullanarak `new` şekilde işleci:</span><span class="sxs-lookup"><span data-stu-id="96512-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="96512-105">Önceki deyimi aşağıdaki ifadeyi aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="96512-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="96512-106">Başlatılmamış değişkenleri C# kullanarak verilmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="96512-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="96512-107">Değer türü</span><span class="sxs-lookup"><span data-stu-id="96512-107">Value type</span></span>|<span data-ttu-id="96512-108">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="96512-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="96512-109">bool</span><span class="sxs-lookup"><span data-stu-id="96512-109">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="96512-110">bayt</span><span class="sxs-lookup"><span data-stu-id="96512-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="96512-111">0</span><span class="sxs-lookup"><span data-stu-id="96512-111">0</span></span>|
|[<span data-ttu-id="96512-112">char</span><span class="sxs-lookup"><span data-stu-id="96512-112">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="96512-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="96512-113">'\0'</span></span>|
|[<span data-ttu-id="96512-114">ondalık</span><span class="sxs-lookup"><span data-stu-id="96512-114">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="96512-115">0M</span><span class="sxs-lookup"><span data-stu-id="96512-115">0M</span></span>|
|[<span data-ttu-id="96512-116">çift</span><span class="sxs-lookup"><span data-stu-id="96512-116">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="96512-117">0,0 D</span><span class="sxs-lookup"><span data-stu-id="96512-117">0.0D</span></span>|
|[<span data-ttu-id="96512-118">Enum</span><span class="sxs-lookup"><span data-stu-id="96512-118">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)|<span data-ttu-id="96512-119">Burada E enum tanımlayıcısıdır (E) 0, deyim tarafından üretilen değeri.</span><span class="sxs-lookup"><span data-stu-id="96512-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="96512-120">kayan nokta</span><span class="sxs-lookup"><span data-stu-id="96512-120">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="96512-121">0.0F</span><span class="sxs-lookup"><span data-stu-id="96512-121">0.0F</span></span>|
|[<span data-ttu-id="96512-122">int</span><span class="sxs-lookup"><span data-stu-id="96512-122">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="96512-123">0</span><span class="sxs-lookup"><span data-stu-id="96512-123">0</span></span>|
|[<span data-ttu-id="96512-124">uzun</span><span class="sxs-lookup"><span data-stu-id="96512-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="96512-125">0 M</span><span class="sxs-lookup"><span data-stu-id="96512-125">0L</span></span>|
|[<span data-ttu-id="96512-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="96512-126">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="96512-127">0</span><span class="sxs-lookup"><span data-stu-id="96512-127">0</span></span>|
|[<span data-ttu-id="96512-128">kısa</span><span class="sxs-lookup"><span data-stu-id="96512-128">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="96512-129">0</span><span class="sxs-lookup"><span data-stu-id="96512-129">0</span></span>|
|[<span data-ttu-id="96512-130">yapısı</span><span class="sxs-lookup"><span data-stu-id="96512-130">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)|<span data-ttu-id="96512-131">Değer üretilen tüm değer tür alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak `null`.</span><span class="sxs-lookup"><span data-stu-id="96512-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="96512-132">uint</span><span class="sxs-lookup"><span data-stu-id="96512-132">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="96512-133">0</span><span class="sxs-lookup"><span data-stu-id="96512-133">0</span></span>|
|[<span data-ttu-id="96512-134">ulong</span><span class="sxs-lookup"><span data-stu-id="96512-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="96512-135">0</span><span class="sxs-lookup"><span data-stu-id="96512-135">0</span></span>|
|[<span data-ttu-id="96512-136">ushort</span><span class="sxs-lookup"><span data-stu-id="96512-136">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="96512-137">0</span><span class="sxs-lookup"><span data-stu-id="96512-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="96512-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96512-138">See also</span></span>
 [<span data-ttu-id="96512-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="96512-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="96512-140">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="96512-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="96512-141">Değer türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="96512-141">Value Types Table</span></span>](../../../csharp/language-reference/keywords/value-types-table.md)  
 [<span data-ttu-id="96512-142">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="96512-142">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="96512-143">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="96512-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="96512-144">Türler için başvuru tabloları</span><span class="sxs-lookup"><span data-stu-id="96512-144">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
