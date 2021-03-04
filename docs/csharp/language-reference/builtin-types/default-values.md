---
title: C# türlerinin varsayılan değerleri-C# başvurusu
description: Bool, Char, int, float, Double ve daha fazlası gibi C# türlerinin varsayılan değerlerini öğrenin.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 72d6249ed56ae6ae34a6f51102e1e7bbd3f64ab7
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104121"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="155a8-103">C# türlerinin varsayılan değerleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="155a8-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="155a8-104">Aşağıdaki tabloda C# türlerinin varsayılan değerleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="155a8-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="155a8-105">Tür</span><span class="sxs-lookup"><span data-stu-id="155a8-105">Type</span></span>|<span data-ttu-id="155a8-106">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="155a8-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="155a8-107">Herhangi bir [başvuru türü](../keywords/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="155a8-107">Any [reference type](../keywords/reference-types.md)</span></span>|`null`|
|<span data-ttu-id="155a8-108">Herhangi bir [yerleşik integral sayısal türü](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="155a8-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="155a8-109">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="155a8-109">0 (zero)</span></span>|
|<span data-ttu-id="155a8-110">Herhangi bir [yerleşik kayan nokta sayısal türü](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="155a8-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="155a8-111">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="155a8-111">0 (zero)</span></span>|
|[<span data-ttu-id="155a8-112">bool</span><span class="sxs-lookup"><span data-stu-id="155a8-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="155a8-113">char</span><span class="sxs-lookup"><span data-stu-id="155a8-113">char</span></span>](char.md)|<span data-ttu-id="155a8-114">`'\0'` (U + 0000)</span><span class="sxs-lookup"><span data-stu-id="155a8-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="155a8-115">yardımının</span><span class="sxs-lookup"><span data-stu-id="155a8-115">enum</span></span>](enum.md)|<span data-ttu-id="155a8-116">İfade tarafından üretilen `(E)0` , `E` numaralandırma tanımlayıcısı olan değer.</span><span class="sxs-lookup"><span data-stu-id="155a8-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="155a8-117">sýný</span><span class="sxs-lookup"><span data-stu-id="155a8-117">struct</span></span>](struct.md)|<span data-ttu-id="155a8-118">Tüm değer türü alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak oluşturulan değer `null` .</span><span class="sxs-lookup"><span data-stu-id="155a8-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="155a8-119">Herhangi bir [Nullable değer türü](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="155a8-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="155a8-120"><xref:System.Nullable%601.HasValue%2A>Özelliği `false` ve özelliği tanımsız olan bir örnek <xref:System.Nullable%601.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="155a8-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="155a8-121">Bu varsayılan değer null olabilen bir değer türünün *null* değeri olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="155a8-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="155a8-122">Aşağıdaki örnekte gösterildiği gibi, bir türün varsayılan değerini oluşturmak için [ `default` işlecini](../operators/default.md#default-operator) kullanın:</span><span class="sxs-lookup"><span data-stu-id="155a8-122">Use the [`default` operator](../operators/default.md#default-operator) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="155a8-123">C# 7,1 ' den başlayarak, bir değişkeni türünün varsayılan değeri ile başlatmak için [ `default` değişmez](../operators/default.md#default-literal) değeri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="155a8-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="155a8-124">Bir değer türü için, örtük parametresiz Oluşturucu, aşağıdaki örnekte gösterildiği gibi türün varsayılan değerini de üretir:</span><span class="sxs-lookup"><span data-stu-id="155a8-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="155a8-125">Çalışma zamanında, <xref:System.Type?displayProperty=nameWithType> örnek bir değer türünü temsil ediyorsa, <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> türünün varsayılan değerini almak üzere parametresiz oluşturucuyu çağırmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="155a8-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="155a8-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="155a8-126">C# language specification</span></span>

<span data-ttu-id="155a8-127">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="155a8-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="155a8-128">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="155a8-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="155a8-129">Varsayılan oluşturucular</span><span class="sxs-lookup"><span data-stu-id="155a8-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="155a8-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="155a8-130">See also</span></span>

- [<span data-ttu-id="155a8-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="155a8-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="155a8-132">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="155a8-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
