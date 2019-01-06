---
title: Örtük sayısal dönüşümler tablosu - C# başvurusu
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: ab6506e619c675ddd68237c4ddca870e9e14098f
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058470"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="4a05b-102">Örtük sayısal dönüşümler tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4a05b-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="4a05b-103">Aşağıdaki tablo, .NET sayısal türler arasında önceden tanımlanmış örtük dönüştürmeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a05b-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="4a05b-104">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="4a05b-104">From</span></span>|<span data-ttu-id="4a05b-105">Bitiş</span><span class="sxs-lookup"><span data-stu-id="4a05b-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="4a05b-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="4a05b-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="4a05b-107">`short`, `int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a05b-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4a05b-108">byte</span><span class="sxs-lookup"><span data-stu-id="4a05b-108">byte</span></span>](byte.md)|<span data-ttu-id="4a05b-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a05b-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4a05b-110">char</span><span class="sxs-lookup"><span data-stu-id="4a05b-110">char</span></span>](char.md)|<span data-ttu-id="4a05b-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a05b-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4a05b-112">short</span><span class="sxs-lookup"><span data-stu-id="4a05b-112">short</span></span>](short.md)|<span data-ttu-id="4a05b-113">`int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a05b-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4a05b-114">ushort</span><span class="sxs-lookup"><span data-stu-id="4a05b-114">ushort</span></span>](ushort.md)|<span data-ttu-id="4a05b-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a05b-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4a05b-116">int</span><span class="sxs-lookup"><span data-stu-id="4a05b-116">int</span></span>](int.md)|<span data-ttu-id="4a05b-117">`long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a05b-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4a05b-118">uint</span><span class="sxs-lookup"><span data-stu-id="4a05b-118">uint</span></span>](uint.md)|<span data-ttu-id="4a05b-119">`long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a05b-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4a05b-120">long</span><span class="sxs-lookup"><span data-stu-id="4a05b-120">long</span></span>](long.md)|<span data-ttu-id="4a05b-121">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a05b-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4a05b-122">ulong</span><span class="sxs-lookup"><span data-stu-id="4a05b-122">ulong</span></span>](ulong.md)|<span data-ttu-id="4a05b-123">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a05b-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4a05b-124">float</span><span class="sxs-lookup"><span data-stu-id="4a05b-124">float</span></span>](float.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="4a05b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a05b-125">Remarks</span></span>  

- <span data-ttu-id="4a05b-126">Tüm [integral türü](integral-types-table.md) için örtük olarak dönüştürülebilir [kayan nokta türü](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="4a05b-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="4a05b-127">Duyarlık ancak değil büyüklük kayıp dönüşümlerse içinde `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.</span><span class="sxs-lookup"><span data-stu-id="4a05b-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="4a05b-128">Herhangi bir örtük dönüştürme vardır `char`, `byte` ve `sbyte` türleri.</span><span class="sxs-lookup"><span data-stu-id="4a05b-128">There are no implicit conversions to the `char`, `byte` and `sbyte` types.</span></span>  

- <span data-ttu-id="4a05b-129">Öğesinden örtük dönüştürme işlemi yok `char`, `double` ve `decimal` türleri.</span><span class="sxs-lookup"><span data-stu-id="4a05b-129">There are no implicit conversions from the `char`, `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="4a05b-130">Arasında örtük dönüştürme işlemi yok `decimal` türü ve `float` veya `double` türleri.</span><span class="sxs-lookup"><span data-stu-id="4a05b-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="4a05b-131">Bir değer türünde sabit bir ifadenin `int` (örneğin, bir tamsayı sabit değeri tarafından temsil edilen bir değer) dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, onu sağlanan Hedef türün aralığı içinde:</span><span class="sxs-lookup"><span data-stu-id="4a05b-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="4a05b-132">Örtük dönüştürmeleri hakkında daha fazla bilgi için bkz. [örtük dönüştürmelerin](~/_csharplang/spec/conversions.md#implicit-conversions) bölümünü [C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a05b-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4a05b-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a05b-133">See also</span></span>

- [<span data-ttu-id="4a05b-134">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4a05b-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4a05b-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4a05b-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4a05b-136">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="4a05b-136">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="4a05b-137">Kayan nokta türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="4a05b-137">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="4a05b-138">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="4a05b-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="4a05b-139">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="4a05b-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="4a05b-140">Atama ve tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="4a05b-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
