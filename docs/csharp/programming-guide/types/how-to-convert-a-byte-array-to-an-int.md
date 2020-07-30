---
title: Bir bayt dizisini int-C# programlama kılavuzuna dönüştürme
description: Byte dizisini int 'e dönüştürmeyi öğrenin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 24037a5e212326cf5e670214a6774eff52bd8faf
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381573"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="b8a14-103">Byte dizisini int 'e dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b8a14-103">How to convert a byte array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="b8a14-104">Bu örnek, bir <xref:System.BitConverter> bayt dizisini [int](../../language-reference/builtin-types/integral-numeric-types.md) 'e ve bir bayt dizisine geri dönüştürmek için sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8a14-104">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="b8a14-105">Örneğin, ağ dışı baytları okuduktan sonra bayttan bir yerleşik veri türüne dönüştürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b8a14-105">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="b8a14-106">Örnekteki [ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemine ek olarak, aşağıdaki tablo, <xref:System.BitConverter> sınıftaki baytları (bayt dizisinden bir diziyle) diğer yerleşik türlere dönüştüren sınıf içindeki yöntemleri listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="b8a14-106">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="b8a14-107">Döndürülen tür</span><span class="sxs-lookup"><span data-stu-id="b8a14-107">Type returned</span></span>|<span data-ttu-id="b8a14-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b8a14-108">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="b8a14-109">[ToBoolean (bayt \[ \] , Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-109">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="b8a14-110">[ToChar (bayt \[ \] , Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-110">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="b8a14-111">[ToDouble (bayt \[ \] , Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-111">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="b8a14-112">[Toınt16 (bayt \[ \] , Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-112">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="b8a14-113">[Toınt32 (bayt \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-113">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="b8a14-114">[Toınt64 (bayt \[ \] , Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-114">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="b8a14-115">[ToSingle (bayt \[ \] , Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-115">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="b8a14-116">[Touınt16 (bayt \[ \] , Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-116">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="b8a14-117">[Touınt32 (bayt \[ \] , Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-117">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="b8a14-118">[Touınt64 (bayt \[ \] , Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b8a14-118">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="b8a14-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8a14-119">Example</span></span>

<span data-ttu-id="b8a14-120">Bu örnek, bir bayt dizisini başlatır, bilgisayar mimarisi az endian ise diziyi tersine çevirir (yani öncelikle en az önemli bayt depolanır) ve sonra dizideki dört baytı bir olarak dönüştürmek için [ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemini çağırır `int` .</span><span class="sxs-lookup"><span data-stu-id="b8a14-120">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="b8a14-121">[ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) için ikinci bağımsız değişken bayt dizisinin başlangıç dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8a14-121">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="b8a14-122">Çıktı, bilgisayarınızın mimarisinin bitiliğine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b8a14-122">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="b8a14-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8a14-123">Example</span></span>

<span data-ttu-id="b8a14-124">Bu örnekte, <xref:System.BitConverter.GetBytes%28System.Int32%29> <xref:System.BitConverter> sınıfının yöntemi bir bayt dizisine dönüştürmek için çağırılır `int` .</span><span class="sxs-lookup"><span data-stu-id="b8a14-124">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="b8a14-125">Çıktı, bilgisayarınızın mimarisinin bitiliğine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b8a14-125">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="b8a14-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8a14-126">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="b8a14-127">Türler</span><span class="sxs-lookup"><span data-stu-id="b8a14-127">Types</span></span>](./index.md)
