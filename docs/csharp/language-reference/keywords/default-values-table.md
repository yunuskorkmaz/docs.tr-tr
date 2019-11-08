---
title: Varsayılan değerler tablo- C# başvuru
ms.custom: seodec18
description: C# Türlerin varsayılan değerlerini öğrenin.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 02f86ef8ee73ff31a6c5c9d17a44a443f72ef05e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739289"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="8eca7-103">Varsayılan değerler tablosu (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="8eca7-103">Default values table (C# reference)</span></span>

<span data-ttu-id="8eca7-104">Aşağıdaki tabloda, C# türlerin varsayılan değerleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8eca7-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="8eca7-105">Tür</span><span class="sxs-lookup"><span data-stu-id="8eca7-105">Type</span></span>|<span data-ttu-id="8eca7-106">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="8eca7-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="8eca7-107">Herhangi bir başvuru türü</span><span class="sxs-lookup"><span data-stu-id="8eca7-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="8eca7-108">Herhangi bir [yerleşik integral sayısal türü](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="8eca7-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="8eca7-109">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="8eca7-109">0 (zero)</span></span>|
|<span data-ttu-id="8eca7-110">Herhangi bir [yerleşik kayan nokta sayısal türü](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="8eca7-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="8eca7-111">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="8eca7-111">0 (zero)</span></span>|
|[<span data-ttu-id="8eca7-112">bool</span><span class="sxs-lookup"><span data-stu-id="8eca7-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="8eca7-113">char</span><span class="sxs-lookup"><span data-stu-id="8eca7-113">char</span></span>](char.md)|<span data-ttu-id="8eca7-114">`'\0'` (U + 0000)</span><span class="sxs-lookup"><span data-stu-id="8eca7-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="8eca7-115">enum</span><span class="sxs-lookup"><span data-stu-id="8eca7-115">enum</span></span>](enum.md)|<span data-ttu-id="8eca7-116">İfade tarafından üretilen değer `(E)0`, burada `E` enum tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="8eca7-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="8eca7-117">struct</span><span class="sxs-lookup"><span data-stu-id="8eca7-117">struct</span></span>](struct.md)|<span data-ttu-id="8eca7-118">Tüm değer türü alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak oluşturulan değer `null`.</span><span class="sxs-lookup"><span data-stu-id="8eca7-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="8eca7-119">Herhangi bir [Nullable değer türü](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="8eca7-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span></span>|<span data-ttu-id="8eca7-120"><xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız bir örnek.</span><span class="sxs-lookup"><span data-stu-id="8eca7-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="8eca7-121">Bu varsayılan değer null olabilen bir değer türünün *null* değeri olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="8eca7-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="8eca7-122">Aşağıdaki örnekte gösterildiği gibi, bir türün varsayılan değerini oluşturmak için [varsayılan işleci](../operators/default.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="8eca7-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="8eca7-123">7,1 ' C# den başlayarak, türü varsayılan değeri olan bir değişkeni başlatmak için [`default` değişmez](../operators/default.md#default-literal) değerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8eca7-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="8eca7-124">Bir değer türü için, örtük parametresiz Oluşturucu, aşağıdaki örnekte gösterildiği gibi türün varsayılan değerini de üretir:</span><span class="sxs-lookup"><span data-stu-id="8eca7-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="8eca7-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8eca7-125">C# language specification</span></span>

<span data-ttu-id="8eca7-126">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="8eca7-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8eca7-127">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="8eca7-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="8eca7-128">Varsayılan oluşturucular</span><span class="sxs-lookup"><span data-stu-id="8eca7-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="8eca7-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eca7-129">See also</span></span>

- [<span data-ttu-id="8eca7-130">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="8eca7-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8eca7-131">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8eca7-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="8eca7-132">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="8eca7-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="8eca7-133">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="8eca7-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
