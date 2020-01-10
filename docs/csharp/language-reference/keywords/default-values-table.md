---
title: Varsayılan değerler tablo- C# başvuru
description: C# Türlerin varsayılan değerlerini öğrenin.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: b15da080c34e2c24ff2a0ecda639f7fe68fb7573
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713635"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="fe825-103">Varsayılan değerler tablosu (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="fe825-103">Default values table (C# reference)</span></span>

<span data-ttu-id="fe825-104">Aşağıdaki tabloda, C# türlerin varsayılan değerleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="fe825-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="fe825-105">Tür</span><span class="sxs-lookup"><span data-stu-id="fe825-105">Type</span></span>|<span data-ttu-id="fe825-106">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="fe825-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="fe825-107">Herhangi bir başvuru türü</span><span class="sxs-lookup"><span data-stu-id="fe825-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="fe825-108">Herhangi bir [yerleşik integral sayısal türü](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="fe825-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="fe825-109">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="fe825-109">0 (zero)</span></span>|
|<span data-ttu-id="fe825-110">Herhangi bir [yerleşik kayan nokta sayısal türü](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="fe825-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="fe825-111">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="fe825-111">0 (zero)</span></span>|
|[<span data-ttu-id="fe825-112">bool</span><span class="sxs-lookup"><span data-stu-id="fe825-112">bool</span></span>](../builtin-types/bool.md)|`false`|
|[<span data-ttu-id="fe825-113">char</span><span class="sxs-lookup"><span data-stu-id="fe825-113">char</span></span>](../builtin-types/char.md)|<span data-ttu-id="fe825-114">`'\0'` (U + 0000)</span><span class="sxs-lookup"><span data-stu-id="fe825-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="fe825-115">enum</span><span class="sxs-lookup"><span data-stu-id="fe825-115">enum</span></span>](../builtin-types/enum.md)|<span data-ttu-id="fe825-116">İfade tarafından üretilen değer `(E)0`, burada `E` enum tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="fe825-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="fe825-117">struct</span><span class="sxs-lookup"><span data-stu-id="fe825-117">struct</span></span>](struct.md)|<span data-ttu-id="fe825-118">Tüm değer türü alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak oluşturulan değer `null`.</span><span class="sxs-lookup"><span data-stu-id="fe825-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="fe825-119">Herhangi bir [Nullable değer türü](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="fe825-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span></span>|<span data-ttu-id="fe825-120"><xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız bir örnek.</span><span class="sxs-lookup"><span data-stu-id="fe825-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="fe825-121">Bu varsayılan değer null olabilen bir değer türünün *null* değeri olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="fe825-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="fe825-122">Aşağıdaki örnekte gösterildiği gibi, bir türün varsayılan değerini oluşturmak için [varsayılan işleci](../operators/default.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="fe825-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="fe825-123">7,1 ' C# den başlayarak, türü varsayılan değeri olan bir değişkeni başlatmak için [`default` değişmez](../operators/default.md#default-literal) değerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fe825-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="fe825-124">Bir değer türü için, örtük parametresiz Oluşturucu, aşağıdaki örnekte gösterildiği gibi türün varsayılan değerini de üretir:</span><span class="sxs-lookup"><span data-stu-id="fe825-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="fe825-125">Çalışma zamanında, <xref:System.Type?displayProperty=nameWithType> örneği bir değer türünü temsil ediyorsa, türün varsayılan değerini almak üzere parametresiz oluşturucuyu çağırmak için <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe825-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fe825-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="fe825-126">C# language specification</span></span>

<span data-ttu-id="fe825-127">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="fe825-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="fe825-128">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="fe825-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="fe825-129">Varsayılan oluşturucular</span><span class="sxs-lookup"><span data-stu-id="fe825-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="fe825-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe825-130">See also</span></span>

- [<span data-ttu-id="fe825-131">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="fe825-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fe825-132">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fe825-132">C# keywords</span></span>](index.md)
- [<span data-ttu-id="fe825-133">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="fe825-133">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="fe825-134">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="fe825-134">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
