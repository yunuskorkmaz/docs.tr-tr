---
title: Örtük sayısal dönüşümler tablosu (C# Başvurusu)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: e46816fc8f3a6ff71dcba3561098d3cfce1e1054
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213270"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="53bf7-102">Örtük sayısal dönüşümler tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="53bf7-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="53bf7-103">Aşağıdaki tablo, .NET sayısal türler arasında önceden tanımlanmış örtük dönüştürmeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="53bf7-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="53bf7-104">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="53bf7-104">From</span></span>|<span data-ttu-id="53bf7-105">Bitiş</span><span class="sxs-lookup"><span data-stu-id="53bf7-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="53bf7-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="53bf7-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="53bf7-107">`short`, `int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="53bf7-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="53bf7-108">byte</span><span class="sxs-lookup"><span data-stu-id="53bf7-108">byte</span></span>](byte.md)|<span data-ttu-id="53bf7-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="53bf7-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="53bf7-110">short</span><span class="sxs-lookup"><span data-stu-id="53bf7-110">short</span></span>](short.md)|<span data-ttu-id="53bf7-111">`int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="53bf7-111">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="53bf7-112">ushort</span><span class="sxs-lookup"><span data-stu-id="53bf7-112">ushort</span></span>](ushort.md)|<span data-ttu-id="53bf7-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="53bf7-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="53bf7-114">int</span><span class="sxs-lookup"><span data-stu-id="53bf7-114">int</span></span>](int.md)|<span data-ttu-id="53bf7-115">`long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="53bf7-115">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="53bf7-116">uint</span><span class="sxs-lookup"><span data-stu-id="53bf7-116">uint</span></span>](uint.md)|<span data-ttu-id="53bf7-117">`long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="53bf7-117">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="53bf7-118">long</span><span class="sxs-lookup"><span data-stu-id="53bf7-118">long</span></span>](long.md)|<span data-ttu-id="53bf7-119">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="53bf7-119">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="53bf7-120">char</span><span class="sxs-lookup"><span data-stu-id="53bf7-120">char</span></span>](char.md)|<span data-ttu-id="53bf7-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="53bf7-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="53bf7-122">float</span><span class="sxs-lookup"><span data-stu-id="53bf7-122">float</span></span>](float.md)|`double`|  
|[<span data-ttu-id="53bf7-123">ulong</span><span class="sxs-lookup"><span data-stu-id="53bf7-123">ulong</span></span>](ulong.md)|<span data-ttu-id="53bf7-124">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="53bf7-124">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53bf7-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53bf7-125">Remarks</span></span>  

- <span data-ttu-id="53bf7-126">Tüm [integral türü](integral-types-table.md) için örtük olarak dönüştürülebilir [kayan nokta türü](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="53bf7-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="53bf7-127">Duyarlık ancak değil büyüklük kayıp dönüşümlerse içinde `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.</span><span class="sxs-lookup"><span data-stu-id="53bf7-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="53bf7-128">Herhangi bir örtük dönüştürme vardır `char` türü.</span><span class="sxs-lookup"><span data-stu-id="53bf7-128">There are no implicit conversions to the `char` type.</span></span>  
  
- <span data-ttu-id="53bf7-129">Arasında örtük dönüştürme işlemi yok `float` ve `double` türleri ve `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="53bf7-129">There are no implicit conversions between the `float` and `double` types and the `decimal` type.</span></span>  
  
- <span data-ttu-id="53bf7-130">Bir değer türünde sabit bir ifadenin `int` (örneğin, bir tamsayı sabit değeri tarafından temsil edilen bir değer) dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, onu sağlanan Hedef türün aralığı içinde:</span><span class="sxs-lookup"><span data-stu-id="53bf7-130">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="53bf7-131">Örtük dönüştürmeleri hakkında daha fazla bilgi için bkz. [örtük dönüştürmelerin](/dotnet/csharp/language-reference/language-specification/conversions#implicit-conversions) bölümünü [C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="53bf7-131">For more information about implicit conversions, see the [Implicit conversions](/dotnet/csharp/language-reference/language-specification/conversions#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="53bf7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53bf7-132">See also</span></span>

- [<span data-ttu-id="53bf7-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="53bf7-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="53bf7-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="53bf7-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="53bf7-135">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="53bf7-135">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="53bf7-136">Kayan nokta türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="53bf7-136">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="53bf7-137">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="53bf7-137">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="53bf7-138">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="53bf7-138">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="53bf7-139">Atama ve tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="53bf7-139">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
