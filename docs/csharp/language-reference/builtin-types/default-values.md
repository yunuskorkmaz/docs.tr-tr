---
title: C# türlerinin varsayılan değerleri - C# başvurusu
description: Bool, char, int, float, double ve daha fazlası gibi C# türlerinin varsayılan değerlerini öğrenin.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 5e34d291ec15c738f3bc9409df321ede454b6710
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507262"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="60cbd-103">C# türlerinin varsayılan değerleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="60cbd-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="60cbd-104">Aşağıdaki tabloc# türlerinin varsayılan değerlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="60cbd-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="60cbd-105">Tür</span><span class="sxs-lookup"><span data-stu-id="60cbd-105">Type</span></span>|<span data-ttu-id="60cbd-106">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="60cbd-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="60cbd-107">Herhangi bir başvuru türü</span><span class="sxs-lookup"><span data-stu-id="60cbd-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="60cbd-108">Herhangi bir [dahili integral sayısal tip](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="60cbd-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="60cbd-109">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="60cbd-109">0 (zero)</span></span>|
|<span data-ttu-id="60cbd-110">Herhangi bir [yerleşik kayan nokta sayısal türü](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="60cbd-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="60cbd-111">0 (sıfır)</span><span class="sxs-lookup"><span data-stu-id="60cbd-111">0 (zero)</span></span>|
|[<span data-ttu-id="60cbd-112">bool</span><span class="sxs-lookup"><span data-stu-id="60cbd-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="60cbd-113">char</span><span class="sxs-lookup"><span data-stu-id="60cbd-113">char</span></span>](char.md)|<span data-ttu-id="60cbd-114">`'\0'`(U+0000)</span><span class="sxs-lookup"><span data-stu-id="60cbd-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="60cbd-115">Enum</span><span class="sxs-lookup"><span data-stu-id="60cbd-115">enum</span></span>](enum.md)|<span data-ttu-id="60cbd-116">İfade `(E)0`tarafından üretilen değer `E` , enum tanımlayıcısı nerededir.</span><span class="sxs-lookup"><span data-stu-id="60cbd-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="60cbd-117">Yapı</span><span class="sxs-lookup"><span data-stu-id="60cbd-117">struct</span></span>](struct.md)|<span data-ttu-id="60cbd-118">Tüm değer türü alanlarını varsayılan değerlerine ve tüm başvuru türü `null`alanlarının .'a ayarlanmasıyla üretilen değer.</span><span class="sxs-lookup"><span data-stu-id="60cbd-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="60cbd-119">Herhangi bir [nullable değer türü](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="60cbd-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="60cbd-120">Özelliğin ve <xref:System.Nullable%601.HasValue%2A> özelliğin `false` <xref:System.Nullable%601.Value%2A> tanımsız olduğu bir örnek.</span><span class="sxs-lookup"><span data-stu-id="60cbd-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="60cbd-121">Bu varsayılan değer, nullable değer türünün *null* değeri olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="60cbd-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="60cbd-122">Aşağıdaki örnekte görüldüğü gibi, bir türün varsayılan değerini üretmek için [ `default` işleci](../operators/default.md#default-operator) kullanın:</span><span class="sxs-lookup"><span data-stu-id="60cbd-122">Use the [`default` operator](../operators/default.md#default-operator) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="60cbd-123">C# 7.1 ile başlayarak, türünün varsayılan değerine sahip bir değişkeni başlatmak için [ `default` literal'ı](../operators/default.md#default-literal) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60cbd-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="60cbd-124">Bir değer türü için, örtük parametresiz oluşturucu da aşağıdaki örnekte görüldüğü gibi, türün varsayılan değerini üretir:</span><span class="sxs-lookup"><span data-stu-id="60cbd-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="60cbd-125">Çalışma zamanında, <xref:System.Type?displayProperty=nameWithType> örnek bir değer türünü temsil ederse, yöntem in türün varsayılan değerini elde etmek için parametresiz oluşturucuyu çağırmak için kullanabilirsiniz. <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="60cbd-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="60cbd-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="60cbd-126">C# language specification</span></span>

<span data-ttu-id="60cbd-127">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="60cbd-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="60cbd-128">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="60cbd-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="60cbd-129">Varsayılan oluşturucular</span><span class="sxs-lookup"><span data-stu-id="60cbd-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="60cbd-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60cbd-130">See also</span></span>

- [<span data-ttu-id="60cbd-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="60cbd-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="60cbd-132">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="60cbd-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
