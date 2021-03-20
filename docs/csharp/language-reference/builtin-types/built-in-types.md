---
title: Yerleşik türler-C# başvurusu
description: C# yerleşik değer ve başvuru türleri hakkında bilgi edinin
ms.date: 03/15/2021
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.openlocfilehash: c2b1c736e17e55913ef1c593813717dd33efd6c3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759722"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="07e9d-103">Yerleşik türler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="07e9d-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="07e9d-104">Aşağıdaki tabloda C# yerleşik [değer](value-types.md) türleri listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07e9d-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="07e9d-105">C# Type anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="07e9d-105">C# type keyword</span></span>|<span data-ttu-id="07e9d-106">.NET türü</span><span class="sxs-lookup"><span data-stu-id="07e9d-106">.NET type</span></span>|
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
|[`nint`](nint-nuint.md)|<xref:System.IntPtr?displayProperty=nameWithType>|
|[`nuint`](nint-nuint.md)|<xref:System.UIntPtr?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

<span data-ttu-id="07e9d-107">Aşağıdaki tabloda C# yerleşik [başvuru](../keywords/reference-types.md) türleri listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07e9d-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="07e9d-108">C# Type anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="07e9d-108">C# type keyword</span></span>|<span data-ttu-id="07e9d-109">.NET türü</span><span class="sxs-lookup"><span data-stu-id="07e9d-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|
|[`dynamic`](reference-types.md#the-dynamic-type)|<xref:System.Object?displayProperty=nameWithType>|

<span data-ttu-id="07e9d-110">Yukarıdaki tablolarda, sol sütundan ( [nınt ve nuınt](nint-nuint.md)hariç) her C# tür anahtar sözcüğü, karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="07e9d-110">In the preceding tables, each C# type keyword from the left column (except [nint and nuint](nint-nuint.md)) is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="07e9d-111">Bunlar arasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="07e9d-111">They are interchangeable.</span></span> <span data-ttu-id="07e9d-112">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="07e9d-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="07e9d-113">`nint` `nuint` İlk tablonun son iki satırında ve türleri yerel boyutlu tamsayılardır.</span><span class="sxs-lookup"><span data-stu-id="07e9d-113">The `nint` and `nuint` types in the last two rows of the first table are native-sized integers.</span></span> <span data-ttu-id="07e9d-114">Bunlar, belirtilen .NET türleri tarafından dahili olarak temsil edilir, ancak her durumda anahtar sözcüğü ve .NET türü birbirini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="07e9d-114">They are represented internally by the indicated .NET types, but in each case the keyword and the .NET type are not interchangeable.</span></span> <span data-ttu-id="07e9d-115">Derleyici, `nint` ve için ve `nuint` işaretçi türleri için sağlamayan tamsayı türleri olarak işlemler ve dönüştürmeler sağlar `System.IntPtr` `System.UIntPtr` .</span><span class="sxs-lookup"><span data-stu-id="07e9d-115">The compiler provides operations and conversions for `nint` and `nuint` as integer types that it doesn't provide for the pointer types `System.IntPtr` and `System.UIntPtr`.</span></span> <span data-ttu-id="07e9d-116">Daha fazla bilgi için bkz. [ `nint` ve `nuint` türleri](nint-nuint.md).</span><span class="sxs-lookup"><span data-stu-id="07e9d-116">For more information, see [`nint` and `nuint` types](nint-nuint.md).</span></span>

<span data-ttu-id="07e9d-117">[`void`](void.md)Anahtar sözcüğü bir türün yokluğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07e9d-117">The [`void`](void.md) keyword represents the absence of a type.</span></span> <span data-ttu-id="07e9d-118">Değer döndürmeyen bir yöntemin dönüş türü olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07e9d-118">You use it as the return type of a method that doesn't return a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="07e9d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07e9d-119">See also</span></span>

- [<span data-ttu-id="07e9d-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="07e9d-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="07e9d-121">C# türlerinin varsayılan değerleri</span><span class="sxs-lookup"><span data-stu-id="07e9d-121">Default values of C# types</span></span>](default-values.md)
