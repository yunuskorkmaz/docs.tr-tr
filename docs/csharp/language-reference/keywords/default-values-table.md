---
title: Varsayılan değerler tablo- C# başvuru
ms.custom: seodec18
description: C# Türlerin varsayılan değerlerini öğrenin.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 23fba8269670156000cb68b3aa07ae7c770eada1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627745"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="c91f8-103">Varsayılan değerler tablosu (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="c91f8-103">Default values table (C# reference)</span></span>

<span data-ttu-id="c91f8-104">Aşağıdaki tabloda, C# türlerin varsayılan değerleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c91f8-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="c91f8-105">Tür</span><span class="sxs-lookup"><span data-stu-id="c91f8-105">Type</span></span>|<span data-ttu-id="c91f8-106">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="c91f8-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="c91f8-107">Herhangi bir başvuru türü</span><span class="sxs-lookup"><span data-stu-id="c91f8-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="c91f8-108">Herhangi bir [yerleşik integral sayısal türü](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="c91f8-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="c91f8-109">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="c91f8-109">0 (zero)</span></span>|
|<span data-ttu-id="c91f8-110">Herhangi bir [yerleşik kayan nokta sayısal türü](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="c91f8-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="c91f8-111">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="c91f8-111">0 (zero)</span></span>|
|[<span data-ttu-id="c91f8-112">bool</span><span class="sxs-lookup"><span data-stu-id="c91f8-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="c91f8-113">char</span><span class="sxs-lookup"><span data-stu-id="c91f8-113">char</span></span>](char.md)|<span data-ttu-id="c91f8-114">`'\0'`(U + 0000)</span><span class="sxs-lookup"><span data-stu-id="c91f8-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="c91f8-115">enum</span><span class="sxs-lookup"><span data-stu-id="c91f8-115">enum</span></span>](enum.md)|<span data-ttu-id="c91f8-116">İfade `(E)0`tarafından üretilen `E` , numaralandırma tanımlayıcısı olan değer.</span><span class="sxs-lookup"><span data-stu-id="c91f8-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="c91f8-117">struct</span><span class="sxs-lookup"><span data-stu-id="c91f8-117">struct</span></span>](struct.md)|<span data-ttu-id="c91f8-118">Tüm değer türü alanları varsayılan değerlerine ve tüm başvuru türü alanlarına `null`ayarlanarak oluşturulan değer.</span><span class="sxs-lookup"><span data-stu-id="c91f8-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="c91f8-119">Herhangi bir [Nullable değer türü](../../programming-guide/nullable-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="c91f8-119">Any [nullable value type](../../programming-guide/nullable-types/index.md)</span></span>|<span data-ttu-id="c91f8-120"><xref:System.Nullable%601.HasValue%2A> Özelliği ve özelliği<xref:System.Nullable%601.Value%2A> tanımsız olan bir örnek. `false`</span><span class="sxs-lookup"><span data-stu-id="c91f8-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="c91f8-121">Bu varsayılan değer null yapılabilir değer türünün *null* değeri olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="c91f8-121">That default value is also known as the *null* value of the nullable value type.</span></span>|

<span data-ttu-id="c91f8-122">Aşağıdaki örnekte gösterildiği gibi, bir türün varsayılan değerini oluşturmak için [varsayılan değer ifadesini](../../programming-guide/statements-expressions-operators/default-value-expressions.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="c91f8-122">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="c91f8-123">7,1 ' C# den başlayarak, bir değişkeni türünün varsayılan değeri ile başlatmak için [ `default` değişmez](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) değeri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c91f8-123">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="c91f8-124">Bir değer türü için, örtük parametresiz Oluşturucu, aşağıdaki örnekte gösterildiği gibi türün varsayılan değerini de üretir:</span><span class="sxs-lookup"><span data-stu-id="c91f8-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="c91f8-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c91f8-125">C# language specification</span></span>

<span data-ttu-id="c91f8-126">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="c91f8-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c91f8-127">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="c91f8-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="c91f8-128">Varsayılan oluşturucular</span><span class="sxs-lookup"><span data-stu-id="c91f8-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="c91f8-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c91f8-129">See also</span></span>

- [<span data-ttu-id="c91f8-130">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="c91f8-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c91f8-131">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c91f8-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="c91f8-132">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="c91f8-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="c91f8-133">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="c91f8-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
