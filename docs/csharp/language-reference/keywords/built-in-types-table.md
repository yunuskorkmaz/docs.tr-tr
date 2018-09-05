---
title: Yerleşik türler tablosu (C# Başvurusu)
description: Yerleşik C# türleri için anahtar sözcükler
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: fd9ba878d77bdb219542db55bb38023c60c7bec4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507318"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="760ee-103">Yerleşik türler tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="760ee-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="760ee-104">Önceden tanımlanmış tür diğer adları olan yerleşik C# türü için anahtar sözcükleri aşağıdaki tabloda gösterilmektedir, <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="760ee-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="760ee-105">C# türü</span><span class="sxs-lookup"><span data-stu-id="760ee-105">C# type</span></span>|<span data-ttu-id="760ee-106">.NET türü</span><span class="sxs-lookup"><span data-stu-id="760ee-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="760ee-107">bool</span><span class="sxs-lookup"><span data-stu-id="760ee-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-108">byte</span><span class="sxs-lookup"><span data-stu-id="760ee-108">byte</span></span>](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="760ee-109">sbyte</span></span>](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-110">char</span><span class="sxs-lookup"><span data-stu-id="760ee-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-111">decimal</span><span class="sxs-lookup"><span data-stu-id="760ee-111">decimal</span></span>](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-112">double</span><span class="sxs-lookup"><span data-stu-id="760ee-112">double</span></span>](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-113">float</span><span class="sxs-lookup"><span data-stu-id="760ee-113">float</span></span>](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-114">int</span><span class="sxs-lookup"><span data-stu-id="760ee-114">int</span></span>](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-115">uint</span><span class="sxs-lookup"><span data-stu-id="760ee-115">uint</span></span>](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-116">long</span><span class="sxs-lookup"><span data-stu-id="760ee-116">long</span></span>](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-117">ulong</span><span class="sxs-lookup"><span data-stu-id="760ee-117">ulong</span></span>](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-118">object</span><span class="sxs-lookup"><span data-stu-id="760ee-118">object</span></span>](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-119">short</span><span class="sxs-lookup"><span data-stu-id="760ee-119">short</span></span>](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-120">ushort</span><span class="sxs-lookup"><span data-stu-id="760ee-120">ushort</span></span>](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="760ee-121">string</span><span class="sxs-lookup"><span data-stu-id="760ee-121">string</span></span>](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="760ee-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="760ee-122">Remarks</span></span>

<span data-ttu-id="760ee-123">Tüm türleri tabloda dışında `object` ve `string`, basit türler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="760ee-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
<span data-ttu-id="760ee-124">C# anahtar sözcükleri yazın ve diğer adlarını birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="760ee-124">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="760ee-125">Örneğin, aşağıdaki bildirimleri birini kullanarak bir tam sayı değişkeni bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="760ee-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>  

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="760ee-126">Kullanım [typeof](typeof.md) almak için işleci <xref:System.Type?displayProperty=nameWithType> belirtilen türünü temsil eden örneği:</span><span class="sxs-lookup"><span data-stu-id="760ee-126">Use the [typeof](typeof.md) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="760ee-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="760ee-127">See also</span></span>

- [<span data-ttu-id="760ee-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="760ee-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="760ee-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="760ee-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="760ee-130">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="760ee-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="760ee-131">Türler için başvuru tabloları</span><span class="sxs-lookup"><span data-stu-id="760ee-131">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="760ee-132">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="760ee-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="760ee-133">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="760ee-133">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="760ee-134">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="760ee-134">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="760ee-135">dynamic</span><span class="sxs-lookup"><span data-stu-id="760ee-135">dynamic</span></span>](dynamic.md)
