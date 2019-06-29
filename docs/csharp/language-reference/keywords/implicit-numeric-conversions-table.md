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
ms.openlocfilehash: 9c3efe1dbea355e8bc00ef44e08efcc9d0e0bdca
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424173"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="8e457-102">Örtük sayısal dönüşümler tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8e457-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="8e457-103">Aşağıdaki tablo, .NET sayısal türler arasında önceden tanımlanmış örtük dönüştürmeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e457-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="8e457-104">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="8e457-104">From</span></span>|<span data-ttu-id="8e457-105">Bitiş</span><span class="sxs-lookup"><span data-stu-id="8e457-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="8e457-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="8e457-106">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="8e457-107">`short`, `int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="8e457-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="8e457-108">byte</span><span class="sxs-lookup"><span data-stu-id="8e457-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="8e457-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="8e457-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="8e457-110">char</span><span class="sxs-lookup"><span data-stu-id="8e457-110">char</span></span>](char.md)|<span data-ttu-id="8e457-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="8e457-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="8e457-112">short</span><span class="sxs-lookup"><span data-stu-id="8e457-112">short</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="8e457-113">`int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="8e457-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="8e457-114">ushort</span><span class="sxs-lookup"><span data-stu-id="8e457-114">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="8e457-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="8e457-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="8e457-116">int</span><span class="sxs-lookup"><span data-stu-id="8e457-116">int</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="8e457-117">`long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="8e457-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="8e457-118">uint</span><span class="sxs-lookup"><span data-stu-id="8e457-118">uint</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="8e457-119">`long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="8e457-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="8e457-120">long</span><span class="sxs-lookup"><span data-stu-id="8e457-120">long</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="8e457-121">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="8e457-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="8e457-122">ulong</span><span class="sxs-lookup"><span data-stu-id="8e457-122">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="8e457-123">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="8e457-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="8e457-124">float</span><span class="sxs-lookup"><span data-stu-id="8e457-124">float</span></span>](float.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="8e457-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e457-125">Remarks</span></span>  

- <span data-ttu-id="8e457-126">Tüm [integral türü](../builtin-types/integral-numeric-types.md) için örtük olarak dönüştürülebilir [kayan nokta türü](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="8e457-126">Any [integral type](../builtin-types/integral-numeric-types.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="8e457-127">Duyarlık ancak değil büyüklük kayıp dönüşümlerse içinde `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.</span><span class="sxs-lookup"><span data-stu-id="8e457-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="8e457-128">Herhangi bir örtük dönüştürme vardır `char`, `byte`, ve `sbyte` türleri.</span><span class="sxs-lookup"><span data-stu-id="8e457-128">There are no implicit conversions to the `char`, `byte`, and `sbyte` types.</span></span>  

- <span data-ttu-id="8e457-129">Öğesinden örtük dönüştürme işlemi yok `double` ve `decimal` türleri.</span><span class="sxs-lookup"><span data-stu-id="8e457-129">There are no implicit conversions from the `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="8e457-130">Arasında örtük dönüştürme işlemi yok `decimal` türü ve `float` veya `double` türleri.</span><span class="sxs-lookup"><span data-stu-id="8e457-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="8e457-131">Bir değer türünde sabit bir ifadenin `int` (örneğin, bir tamsayı sabit değeri tarafından temsil edilen bir değer) dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, onu sağlanan Hedef türün aralığı içinde:</span><span class="sxs-lookup"><span data-stu-id="8e457-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="8e457-132">Örtük dönüştürmeleri hakkında daha fazla bilgi için bkz. [örtük dönüştürmelerin](~/_csharplang/spec/conversions.md#implicit-conversions) bölümünü [C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e457-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8e457-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e457-133">See also</span></span>

- [<span data-ttu-id="8e457-134">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8e457-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8e457-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8e457-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8e457-136">Tam sayı türleri</span><span class="sxs-lookup"><span data-stu-id="8e457-136">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="8e457-137">Kayan nokta türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="8e457-137">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="8e457-138">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="8e457-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="8e457-139">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="8e457-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="8e457-140">Atama ve tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="8e457-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
