---
title: Varsayılan değerler tablosu - C# başvurusu
ms.custom: seodec18
description: C# değer türleri için varsayılan değerleri ne olduğunu öğrenin.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 19e9e4f94ab573f2313c185a08192d89103b98fd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237044"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="b9849-103">Varsayılan değerler tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b9849-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="b9849-104">Varsayılan değerleri aşağıdaki tabloda gösterilmektedir [değer türleri](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="b9849-104">The following table shows the default values of [value types](value-types.md).</span></span>

|<span data-ttu-id="b9849-105">Değer türü</span><span class="sxs-lookup"><span data-stu-id="b9849-105">Value type</span></span>|<span data-ttu-id="b9849-106">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="b9849-106">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="b9849-107">bool</span><span class="sxs-lookup"><span data-stu-id="b9849-107">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="b9849-108">byte</span><span class="sxs-lookup"><span data-stu-id="b9849-108">byte</span></span>](byte.md)|<span data-ttu-id="b9849-109">0</span><span class="sxs-lookup"><span data-stu-id="b9849-109">0</span></span>|
|[<span data-ttu-id="b9849-110">char</span><span class="sxs-lookup"><span data-stu-id="b9849-110">char</span></span>](char.md)|<span data-ttu-id="b9849-111">'\0'</span><span class="sxs-lookup"><span data-stu-id="b9849-111">'\0'</span></span>|
|[<span data-ttu-id="b9849-112">decimal</span><span class="sxs-lookup"><span data-stu-id="b9849-112">decimal</span></span>](decimal.md)|<span data-ttu-id="b9849-113">0M</span><span class="sxs-lookup"><span data-stu-id="b9849-113">0M</span></span>|
|[<span data-ttu-id="b9849-114">double</span><span class="sxs-lookup"><span data-stu-id="b9849-114">double</span></span>](double.md)|<span data-ttu-id="b9849-115">0,0 D</span><span class="sxs-lookup"><span data-stu-id="b9849-115">0.0D</span></span>|
|[<span data-ttu-id="b9849-116">enum</span><span class="sxs-lookup"><span data-stu-id="b9849-116">enum</span></span>](enum.md)|<span data-ttu-id="b9849-117">Değer ifade tarafından üretilen `(E)0`burada `E` numaralandırma tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="b9849-117">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="b9849-118">float</span><span class="sxs-lookup"><span data-stu-id="b9849-118">float</span></span>](float.md)|<span data-ttu-id="b9849-119">0.0F</span><span class="sxs-lookup"><span data-stu-id="b9849-119">0.0F</span></span>|
|[<span data-ttu-id="b9849-120">int</span><span class="sxs-lookup"><span data-stu-id="b9849-120">int</span></span>](int.md)|<span data-ttu-id="b9849-121">0</span><span class="sxs-lookup"><span data-stu-id="b9849-121">0</span></span>|
|[<span data-ttu-id="b9849-122">long</span><span class="sxs-lookup"><span data-stu-id="b9849-122">long</span></span>](long.md)|<span data-ttu-id="b9849-123">0 M</span><span class="sxs-lookup"><span data-stu-id="b9849-123">0L</span></span>|
|[<span data-ttu-id="b9849-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="b9849-124">sbyte</span></span>](sbyte.md)|<span data-ttu-id="b9849-125">0</span><span class="sxs-lookup"><span data-stu-id="b9849-125">0</span></span>|
|[<span data-ttu-id="b9849-126">short</span><span class="sxs-lookup"><span data-stu-id="b9849-126">short</span></span>](short.md)|<span data-ttu-id="b9849-127">0</span><span class="sxs-lookup"><span data-stu-id="b9849-127">0</span></span>|
|[<span data-ttu-id="b9849-128">struct</span><span class="sxs-lookup"><span data-stu-id="b9849-128">struct</span></span>](struct.md)|<span data-ttu-id="b9849-129">Değer üretilmediğini tüm değer tür alanları varsayılan değerlerine ve tüm başvuru türü alanları ayarlayarak `null`.</span><span class="sxs-lookup"><span data-stu-id="b9849-129">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="b9849-130">uint</span><span class="sxs-lookup"><span data-stu-id="b9849-130">uint</span></span>](uint.md)|<span data-ttu-id="b9849-131">0</span><span class="sxs-lookup"><span data-stu-id="b9849-131">0</span></span>|
|[<span data-ttu-id="b9849-132">ulong</span><span class="sxs-lookup"><span data-stu-id="b9849-132">ulong</span></span>](ulong.md)|<span data-ttu-id="b9849-133">0</span><span class="sxs-lookup"><span data-stu-id="b9849-133">0</span></span>|
|[<span data-ttu-id="b9849-134">ushort</span><span class="sxs-lookup"><span data-stu-id="b9849-134">ushort</span></span>](ushort.md)|<span data-ttu-id="b9849-135">0</span><span class="sxs-lookup"><span data-stu-id="b9849-135">0</span></span>|

## <a name="remarks"></a><span data-ttu-id="b9849-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9849-136">Remarks</span></span>

<span data-ttu-id="b9849-137">C# dilinde başlatılmamış değişkenler kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b9849-137">You cannot use uninitialized variables in C#.</span></span> <span data-ttu-id="b9849-138">Varsayılan değer türüne sahip bir değişken başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9849-138">You can initialize a variable with the default value of its type.</span></span> <span data-ttu-id="b9849-139">Bir yöntemin varsayılan değerini belirtmek için varsayılan değer olan bir türü kullanabilirsiniz [isteğe bağlı bağımsız değişkeni](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span><span class="sxs-lookup"><span data-stu-id="b9849-139">You also can use the default value of a type to specify the default value of a method's [optional argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span></span>

<span data-ttu-id="b9849-140">Kullanım [varsayılan değer ifadesi](../../programming-guide/statements-expressions-operators/default-value-expressions.md) aşağıdaki örnekte gösterildiği gibi bir türü varsayılan değerini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="b9849-140">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="b9849-141">Kullanabileceğiniz C# 7.1 ile başlayarak, [ `default` değişmez değer](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) varsayılan değer türüne sahip bir değişken başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="b9849-141">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="b9849-142">Aşağıdaki örnekte gösterildiği gibi bir değer türünün varsayılan değeri üretmek için varsayılan oluşturucu veya örtülü varsayılan oluşturucu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9849-142">You also can use the default constructor or the implicit default constructor to produce the default value of a value type, as the following example shows.</span></span> <span data-ttu-id="b9849-143">Oluşturucular hakkında daha fazla bilgi için bkz. [oluşturucular](../../programming-guide/classes-and-structs/constructors.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="b9849-143">For more information about constructors, see the [Constructors](../../programming-guide/classes-and-structs/constructors.md) article.</span></span>

```csharp
int a = new int();
```

<span data-ttu-id="b9849-144">Varsayılan değer aşağıdakilerden [başvuru türüne](reference-types.md) olduğu `null`.</span><span class="sxs-lookup"><span data-stu-id="b9849-144">The default value of any [reference type](reference-types.md) is `null`.</span></span> <span data-ttu-id="b9849-145">Varsayılan değer olan bir [boş değer atanabilir tür](../../programming-guide/nullable-types/index.md) bir örneği olduğu <xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız.</span><span class="sxs-lookup"><span data-stu-id="b9849-145">The default value of a [nullable type](../../programming-guide/nullable-types/index.md) is an instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9849-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9849-146">See also</span></span>

- [<span data-ttu-id="b9849-147">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b9849-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b9849-148">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b9849-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b9849-149">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b9849-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b9849-150">Türler için başvuru tabloları</span><span class="sxs-lookup"><span data-stu-id="b9849-150">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="b9849-151">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="b9849-151">Value types</span></span>](value-types.md)
- [<span data-ttu-id="b9849-152">Değer türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="b9849-152">Value types table</span></span>](value-types-table.md)
- [<span data-ttu-id="b9849-153">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="b9849-153">Built-in types table</span></span>](built-in-types-table.md)
