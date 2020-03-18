---
title: Bayt dizisini int'e dönüştürme - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 9f477649dba1b42d7a10d521c010977707daf3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698761"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="95de0-102">Bayt dizisini int'e dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="95de0-102">How to convert a byte array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="95de0-103">Bu örnek, bir bayt dizisini <xref:System.BitConverter> [int'e](../../language-reference/builtin-types/integral-numeric-types.md) dönüştürmek ve bir bayt dizisine geri dönmek için sınıfı nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="95de0-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="95de0-104">Örneğin, ağdan baytokuduktan sonra baytlardan yerleşik veri türüne dönüştürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="95de0-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="95de0-105">Örnekteki [ToInt32(Byte,\[\]Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemine ek olarak, aşağıdaki tabloda baytları (bayt dizisinden) diğer yerleşik türlere dönüştüren yöntemler <xref:System.BitConverter> listelenir.</span><span class="sxs-lookup"><span data-stu-id="95de0-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="95de0-106">Döndürülen tür</span><span class="sxs-lookup"><span data-stu-id="95de0-106">Type returned</span></span>|<span data-ttu-id="95de0-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="95de0-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="95de0-108">[ToBoolean(Bayt,\[\]Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="95de0-109">[ToChar(Bayt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="95de0-110">[ToDouble(Bayt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="95de0-111">[ToInt16(Bayt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="95de0-112">[ToInt32(Bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="95de0-113">[ToInt64(Bayt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="95de0-114">[ToSingle(Bayt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="95de0-115">[ToUInt16(Bayt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="95de0-116">[ToUInt32(Bayt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="95de0-117">[ToUInt64(Bayt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="95de0-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="95de0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="95de0-118">Example</span></span>

<span data-ttu-id="95de0-119">Bu örnek, bir bayt dizisini başharfe çevirir, bilgisayar mimarisi az endian ise diziyi tersine çevirir (yani, en [\[\]](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) az öneme sahip bayt önce depolanır) ve ardından dizideki dört `int`bayt'ı bir .</span><span class="sxs-lookup"><span data-stu-id="95de0-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="95de0-120">[ToInt32(Byte,\[\]Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) için ikinci bağımsız değişken bayt dizisinin başlangıç dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="95de0-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="95de0-121">Çıktı, bilgisayarınızın mimarisinin son özelliklerine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="95de0-121">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="95de0-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="95de0-122">Example</span></span>

<span data-ttu-id="95de0-123">Bu örnekte, <xref:System.BitConverter.GetBytes%28System.Int32%29> <xref:System.BitConverter> sınıfın yöntemi bir `int` bayt dizisine dönüştürmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="95de0-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="95de0-124">Çıktı, bilgisayarınızın mimarisinin son özelliklerine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="95de0-124">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="95de0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95de0-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="95de0-126">Türler</span><span class="sxs-lookup"><span data-stu-id="95de0-126">Types</span></span>](./index.md)
