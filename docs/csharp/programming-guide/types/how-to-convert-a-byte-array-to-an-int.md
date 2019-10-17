---
title: 'Nasıl yapılır: bir bayt dizisini int C# programlama kılavuzuna dönüştürme'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 96507f03a3d64b96ef6059a92459bfc7fa854372
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395680"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="3c4f1-102">Nasıl yapılır: byte Dizisini int'e Dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3c4f1-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="3c4f1-103">Bu örnek, bir bayt dizisini bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 'e ve bir bayt dizisine geri dönüştürmek için <xref:System.BitConverter> sınıfının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c4f1-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="3c4f1-104">Örneğin, ağ dışı baytları okuduktan sonra bayttan bir yerleşik veri türüne dönüştürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3c4f1-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="3c4f1-105">Örnekteki [ToInt32 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemine ek olarak aşağıdaki tablo, <xref:System.BitConverter> sınıfındaki, baytları (bir bayt dizisinden) diğer yerleşik türlere dönüştüren yöntemleri listeler.</span><span class="sxs-lookup"><span data-stu-id="3c4f1-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="3c4f1-106">Döndürülen tür</span><span class="sxs-lookup"><span data-stu-id="3c4f1-106">Type returned</span></span>|<span data-ttu-id="3c4f1-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3c4f1-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="3c4f1-108">[ToBoolean (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="3c4f1-109">[ToChar (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="3c4f1-110">[ToDouble (bayt @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="3c4f1-111">[Toınt16 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="3c4f1-112">[Toınt32 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="3c4f1-113">[Toınt64 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="3c4f1-114">[ToSingle (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="3c4f1-115">[Touınt16 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="3c4f1-116">[Touınt32 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="3c4f1-117">[Touınt64 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3c4f1-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="3c4f1-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c4f1-118">Example</span></span>

<span data-ttu-id="3c4f1-119">Bu örnek, bir bayt dizisini başlatır, bilgisayar mimarisi az endian ise diziyi tersine çevirir (yani, ilk olarak en az önemli bayt depolanır) ve ardından, dört baytı dönüştürmek için [ToInt32 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemini çağırır. dizi `int`.</span><span class="sxs-lookup"><span data-stu-id="3c4f1-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="3c4f1-120">Toınt32 ikinci bağımsız değişkeni [(Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) bayt dizisinin başlangıç dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c4f1-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="3c4f1-121">Çıktı, bilgisayarınızın mimarisinin bitiminden birine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3c4f1-121">The output may differ depending on the endianess of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="3c4f1-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c4f1-122">Example</span></span>

<span data-ttu-id="3c4f1-123">Bu örnekte, <xref:System.BitConverter> sınıfının <xref:System.BitConverter.GetBytes%28System.Int32%29> yöntemi `int` bir bayt dizisine dönüştürmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3c4f1-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="3c4f1-124">Çıktı, bilgisayarınızın mimarisinin bitiminden birine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3c4f1-124">The output may differ depending on the endianess of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="3c4f1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c4f1-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="3c4f1-126">Türler</span><span class="sxs-lookup"><span data-stu-id="3c4f1-126">Types</span></span>](./index.md)
