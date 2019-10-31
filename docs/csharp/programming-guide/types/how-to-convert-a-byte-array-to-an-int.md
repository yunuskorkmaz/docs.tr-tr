---
title: 'Nasıl yapılır: bir bayt dizisini int C# programlama kılavuzuna dönüştürme'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: cb6252069302a28f8a85247aa4584a9284b26c4d
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195460"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="79925-102">Nasıl yapılır: byte Dizisini int'e Dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="79925-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="79925-103">Bu örnek, bir bayt dizisini bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 'e ve bir bayt dizisine geri dönüştürmek için <xref:System.BitConverter> sınıfının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="79925-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="79925-104">Örneğin, ağ dışı baytları okuduktan sonra bayttan bir yerleşik veri türüne dönüştürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="79925-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="79925-105">Örnekteki [ToInt32 (byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemine ek olarak, aşağıdaki tablo, baytları (bayt dizisinden bir diziden) diğer yerleşik türlere dönüştüren <xref:System.BitConverter> sınıfındaki yöntemleri listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="79925-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="79925-106">Döndürülen tür</span><span class="sxs-lookup"><span data-stu-id="79925-106">Type returned</span></span>|<span data-ttu-id="79925-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="79925-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="79925-108">[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="79925-109">[ToChar (bayt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="79925-110">[ToDouble (bayt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="79925-111">[Toınt16 (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="79925-112">[Toınt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="79925-113">[Toınt64 (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="79925-114">[ToSingle (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="79925-115">[Touınt16 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="79925-116">[Touınt32 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="79925-117">[Touınt64 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="79925-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="79925-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="79925-118">Example</span></span>

<span data-ttu-id="79925-119">Bu örnek, bir bayt dizisini başlatır, bilgisayar mimarisi az endian ise diziyi tersine çevirir (yani, ilk olarak en az önemli bayt depolanır) ve ardından dört baytı dönüştürmek için [ToInt32 (byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemini çağırır dizide `int`.</span><span class="sxs-lookup"><span data-stu-id="79925-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="79925-120">Toınt32 için ikinci bağımsız değişken [(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) bayt dizisinin başlangıç dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79925-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="79925-121">Çıktı, bilgisayarınızın mimarisinin bitiliğine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="79925-121">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="79925-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="79925-122">Example</span></span>

<span data-ttu-id="79925-123">Bu örnekte, bir `int` bayt dizisine dönüştürmek için <xref:System.BitConverter> sınıfının <xref:System.BitConverter.GetBytes%28System.Int32%29> yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="79925-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="79925-124">Çıktı, bilgisayarınızın mimarisinin bitiliğine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="79925-124">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="79925-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79925-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="79925-126">Türler</span><span class="sxs-lookup"><span data-stu-id="79925-126">Types</span></span>](./index.md)
