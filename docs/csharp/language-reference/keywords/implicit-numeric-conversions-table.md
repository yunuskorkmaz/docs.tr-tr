---
title: Örtük sayısal dönüşümler tablosu (C# Başvurusu)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: c3c0153a0ae3e07839822c8bb978b1a09277bd53
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188709"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="7cac5-102">Örtük sayısal dönüşümler tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7cac5-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="7cac5-103">Aşağıdaki tablo, .NET sayısal türler arasında önceden tanımlanmış örtük dönüştürmeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="7cac5-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="7cac5-104">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="7cac5-104">From</span></span>|<span data-ttu-id="7cac5-105">Bitiş</span><span class="sxs-lookup"><span data-stu-id="7cac5-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="7cac5-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="7cac5-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="7cac5-107">`short`, `int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="7cac5-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7cac5-108">byte</span><span class="sxs-lookup"><span data-stu-id="7cac5-108">byte</span></span>](byte.md)|<span data-ttu-id="7cac5-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="7cac5-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7cac5-110">short</span><span class="sxs-lookup"><span data-stu-id="7cac5-110">short</span></span>](short.md)|<span data-ttu-id="7cac5-111">`int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="7cac5-111">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7cac5-112">ushort</span><span class="sxs-lookup"><span data-stu-id="7cac5-112">ushort</span></span>](ushort.md)|<span data-ttu-id="7cac5-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="7cac5-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7cac5-114">int</span><span class="sxs-lookup"><span data-stu-id="7cac5-114">int</span></span>](int.md)|<span data-ttu-id="7cac5-115">`long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="7cac5-115">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7cac5-116">uint</span><span class="sxs-lookup"><span data-stu-id="7cac5-116">uint</span></span>](uint.md)|<span data-ttu-id="7cac5-117">`long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="7cac5-117">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7cac5-118">long</span><span class="sxs-lookup"><span data-stu-id="7cac5-118">long</span></span>](long.md)|<span data-ttu-id="7cac5-119">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="7cac5-119">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7cac5-120">char</span><span class="sxs-lookup"><span data-stu-id="7cac5-120">char</span></span>](char.md)|<span data-ttu-id="7cac5-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="7cac5-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7cac5-122">float</span><span class="sxs-lookup"><span data-stu-id="7cac5-122">float</span></span>](float.md)|`double`|  
|[<span data-ttu-id="7cac5-123">ulong</span><span class="sxs-lookup"><span data-stu-id="7cac5-123">ulong</span></span>](ulong.md)|<span data-ttu-id="7cac5-124">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="7cac5-124">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cac5-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cac5-125">Remarks</span></span>  

- <span data-ttu-id="7cac5-126">Tüm [integral türü](integral-types-table.md) için örtük olarak dönüştürülebilir [kayan nokta türü](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="7cac5-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="7cac5-127">Duyarlık ancak değil büyüklük kayıp dönüşümlerse içinde `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.</span><span class="sxs-lookup"><span data-stu-id="7cac5-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="7cac5-128">Herhangi bir örtük dönüştürme vardır `char` türü.</span><span class="sxs-lookup"><span data-stu-id="7cac5-128">There are no implicit conversions to the `char` type.</span></span>  
  
- <span data-ttu-id="7cac5-129">Arasında örtük dönüştürme işlemi yok `float` ve `double` türleri ve `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="7cac5-129">There are no implicit conversions between the `float` and `double` types and the `decimal` type.</span></span>  
  
- <span data-ttu-id="7cac5-130">Bir değer türünde sabit bir ifadenin `int` (örneğin, bir tamsayı sabit değeri tarafından temsil edilen bir değer) dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, onu sağlanan Hedef türün aralığı içinde:</span><span class="sxs-lookup"><span data-stu-id="7cac5-130">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="7cac5-131">Örtük dönüştürmeleri hakkında daha fazla bilgi için bkz. [örtük dönüştürmelerin](~/_csharplang/spec/conversions.md#implicit-conversions) bölümünü [C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7cac5-131">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7cac5-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cac5-132">See also</span></span>

- [<span data-ttu-id="7cac5-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7cac5-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7cac5-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7cac5-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7cac5-135">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="7cac5-135">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="7cac5-136">Kayan nokta türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="7cac5-136">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="7cac5-137">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="7cac5-137">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="7cac5-138">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="7cac5-138">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="7cac5-139">Atama ve tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="7cac5-139">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
