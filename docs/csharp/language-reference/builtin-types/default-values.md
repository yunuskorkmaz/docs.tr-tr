---
title: C# Türlerin varsayılan değerleri- C# başvuru
description: Bool, Char, int C# , float, Double ve daha fazlası gibi türlerin varsayılan değerlerini öğrenin.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625871"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="7d113-103">C# Türlerin varsayılan değerleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="7d113-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="7d113-104">Aşağıdaki tabloda, C# türlerin varsayılan değerleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7d113-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="7d113-105">Tür</span><span class="sxs-lookup"><span data-stu-id="7d113-105">Type</span></span>|<span data-ttu-id="7d113-106">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="7d113-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="7d113-107">Herhangi bir başvuru türü</span><span class="sxs-lookup"><span data-stu-id="7d113-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="7d113-108">Herhangi bir [yerleşik integral sayısal türü](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="7d113-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="7d113-109">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="7d113-109">0 (zero)</span></span>|
|<span data-ttu-id="7d113-110">Herhangi bir [yerleşik kayan nokta sayısal türü](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="7d113-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="7d113-111">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="7d113-111">0 (zero)</span></span>|
|[<span data-ttu-id="7d113-112">bool</span><span class="sxs-lookup"><span data-stu-id="7d113-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="7d113-113">char</span><span class="sxs-lookup"><span data-stu-id="7d113-113">char</span></span>](char.md)|<span data-ttu-id="7d113-114">`'\0'` (U + 0000)</span><span class="sxs-lookup"><span data-stu-id="7d113-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="7d113-115">enum</span><span class="sxs-lookup"><span data-stu-id="7d113-115">enum</span></span>](enum.md)|<span data-ttu-id="7d113-116">İfade tarafından üretilen değer `(E)0`, burada `E` enum tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="7d113-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="7d113-117">struct</span><span class="sxs-lookup"><span data-stu-id="7d113-117">struct</span></span>](struct.md)|<span data-ttu-id="7d113-118">Tüm değer türü alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak oluşturulan değer `null`.</span><span class="sxs-lookup"><span data-stu-id="7d113-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="7d113-119">Herhangi bir [Nullable değer türü](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="7d113-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="7d113-120"><xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız bir örnek.</span><span class="sxs-lookup"><span data-stu-id="7d113-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="7d113-121">Bu varsayılan değer null olabilen bir değer türünün *null* değeri olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="7d113-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="7d113-122">Aşağıdaki örnekte gösterildiği gibi, bir türün varsayılan değerini oluşturmak için [varsayılan işleci](../operators/default.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="7d113-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="7d113-123">7,1 ' C# den başlayarak, türü varsayılan değeri olan bir değişkeni başlatmak için [`default` değişmez](../operators/default.md#default-literal) değerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7d113-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="7d113-124">Bir değer türü için, örtük parametresiz Oluşturucu, aşağıdaki örnekte gösterildiği gibi türün varsayılan değerini de üretir:</span><span class="sxs-lookup"><span data-stu-id="7d113-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="7d113-125">Çalışma zamanında, <xref:System.Type?displayProperty=nameWithType> örneği bir değer türünü temsil ediyorsa, türün varsayılan değerini almak üzere parametresiz oluşturucuyu çağırmak için <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d113-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7d113-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7d113-126">C# language specification</span></span>

<span data-ttu-id="7d113-127">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="7d113-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="7d113-128">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="7d113-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="7d113-129">Varsayılan oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7d113-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="7d113-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d113-130">See also</span></span>

- [<span data-ttu-id="7d113-131">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="7d113-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7d113-132">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7d113-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
