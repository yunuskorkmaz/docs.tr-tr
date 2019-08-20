---
title: 'Nasıl yapılır: Byte dizisini int C# programlama kılavuzuna dönüştürme'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 6d272a1a20cc5eb35edc7f6d971cbffbd9bfdbae
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588417"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="1cc4c-102">Nasıl yapılır: Byte dizisini int 'e dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1cc4c-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="1cc4c-103">Bu örnek, bir bayt dizisini [int](../../language-reference/builtin-types/integral-numeric-types.md) 'e <xref:System.BitConverter> ve bir bayt dizisine geri dönüştürmek için sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cc4c-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="1cc4c-104">Örneğin, ağ dışı baytları okuduktan sonra bayttan bir yerleşik veri türüne dönüştürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1cc4c-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="1cc4c-105">Örnekteki [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemine ek olarak, aşağıdaki tablo, <xref:System.BitConverter> sınıftaki baytları (bayt dizisinden bir diziyle) diğer yerleşik türlere dönüştüren sınıf içindeki yöntemleri listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="1cc4c-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="1cc4c-106">Döndürülen tür</span><span class="sxs-lookup"><span data-stu-id="1cc4c-106">Type returned</span></span>|<span data-ttu-id="1cc4c-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1cc4c-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="1cc4c-108">[ToBoolean (bayt\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="1cc4c-109">[ToChar (bayt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="1cc4c-110">[ToDouble (bayt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="1cc4c-111">[ToInt16 (bayt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="1cc4c-112">[ToInt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="1cc4c-113">[ToInt64 (bayt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="1cc4c-114">[ToSingle (bayt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="1cc4c-115">[ToUInt16 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="1cc4c-116">[ToUInt32 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="1cc4c-117">[ToUInt64 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="1cc4c-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1cc4c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cc4c-118">Example</span></span>  
 <span data-ttu-id="1cc4c-119">Bu örnek, bir bayt dizisini başlatır, bilgisayar mimarisi az endian ise diziyi tersine çevirir (yani, ilk olarak en az önemli bayt depolanır) ve ardından dönüştürmek için [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemini çağırır dizideki dört bayt `int`.</span><span class="sxs-lookup"><span data-stu-id="1cc4c-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="1cc4c-120">[ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) için ikinci bağımsız değişken bayt dizisinin başlangıç dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc4c-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cc4c-121">Çıktı, bilgisayarınızın mimarisinin bitiminden birine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="1cc4c-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a><span data-ttu-id="1cc4c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cc4c-122">Example</span></span>  
 <span data-ttu-id="1cc4c-123">Bu örnekte, <xref:System.BitConverter.GetBytes%28System.Int32%29> <xref:System.BitConverter> sınıfının yöntemi bir `int` bayt dizisine dönüştürmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1cc4c-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cc4c-124">Çıktı, bilgisayarınızın mimarisinin bitiminden birine bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="1cc4c-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a><span data-ttu-id="1cc4c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cc4c-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="1cc4c-126">Türler</span><span class="sxs-lookup"><span data-stu-id="1cc4c-126">Types</span></span>](./index.md)
