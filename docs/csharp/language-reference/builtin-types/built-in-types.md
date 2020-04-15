---
title: Yerleşik türleri - C# başvurusu
description: C# yerleşik değer ve başvuru türlerini öğrenin
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: bf8823c6674b1ff3f0028a50df8ce8d0f803cfc1
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389489"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="d30d3-103">Yerleşik türleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d30d3-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="d30d3-104">Aşağıdaki tabloda C# yerleşik [değer](value-types.md) türleri listelenir:</span><span class="sxs-lookup"><span data-stu-id="d30d3-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="d30d3-105">C# türü anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="d30d3-105">C# type keyword</span></span>|<span data-ttu-id="d30d3-106">.NET türü</span><span class="sxs-lookup"><span data-stu-id="d30d3-106">.NET type</span></span>|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

<span data-ttu-id="d30d3-107">Aşağıdaki tabloda C# yerleşik [başvuru](../keywords/reference-types.md) türleri listelenebilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d30d3-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="d30d3-108">C# türü anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="d30d3-108">C# type keyword</span></span>|<span data-ttu-id="d30d3-109">.NET türü</span><span class="sxs-lookup"><span data-stu-id="d30d3-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

<span data-ttu-id="d30d3-110">Önceki tablolarda, sol sütundaki her C# türü anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="d30d3-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="d30d3-111">Değiştirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="d30d3-111">They are interchangeable.</span></span> <span data-ttu-id="d30d3-112">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="d30d3-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="d30d3-113">[`void`](void.md) Anahtar kelime bir türün yokluğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d30d3-113">The [`void`](void.md) keyword represents the absence of a type.</span></span> <span data-ttu-id="d30d3-114">Bir değer döndürmeyen bir yöntemin dönüş türü olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d30d3-114">You use it as the return type of a method that doesn't return a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="d30d3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d30d3-115">See also</span></span>

- [<span data-ttu-id="d30d3-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d30d3-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d30d3-117">C# türlerinin varsayılan değerleri</span><span class="sxs-lookup"><span data-stu-id="d30d3-117">Default values of C# types</span></span>](default-values.md)
- [<span data-ttu-id="d30d3-118">`dynamic`Anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="d30d3-118">`dynamic` keyword</span></span>](reference-types.md#the-dynamic-type)
