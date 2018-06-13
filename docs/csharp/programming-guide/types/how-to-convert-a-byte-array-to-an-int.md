---
title: "Nasıl yapılır: byte Dizisini int'e Dönüştürme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 4e8c232a604837d32675229f7f91b8e329ac4b5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337879"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="c2f65-102">Nasıl yapılır: byte Dizisini int'e Dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c2f65-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="c2f65-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.BitConverter> sınıfı için bir bayt dizisi dönüştürmek için bir [int](../../../csharp/language-reference/keywords/int.md) daha sonra tekrar bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="c2f65-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="c2f65-104">Örneğin Ağ kapalı bayt okuduktan sonra bayt, kaynağı bir yerleşik veri türüne dönüştürmek olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2f65-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="c2f65-105">Ek olarak [Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemi örnekte, aşağıdaki tabloda listelenmektedir yöntemleri <xref:System.BitConverter> diğer yerleşik türleri için (bayt dizesi) baytlar Dönüştür sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c2f65-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="c2f65-106">Döndürülen türü</span><span class="sxs-lookup"><span data-stu-id="c2f65-106">Type returned</span></span>|<span data-ttu-id="c2f65-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c2f65-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="c2f65-108">[ToBoolean (bayt\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="c2f65-109">[ToChar (bayt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="c2f65-110">[ToDouble (bayt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="c2f65-111">[Toınt16 (bayt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="c2f65-112">[Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="c2f65-113">[Toınt64 (bayt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="c2f65-114">[ToSingle (bayt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="c2f65-115">[Touınt16 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="c2f65-116">[Touınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="c2f65-117">[Touınt64 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c2f65-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c2f65-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2f65-118">Example</span></span>  
 <span data-ttu-id="c2f65-119">Bu örnek bir bayt dizisi başlatır, bilgisayar mimarisi little endian ise dizi tersine çevirir (diğer bir deyişle, en az önemli bayt ilk depolanır) ve ardından çağırır [Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))dört bayt dizisine olarak dönüştürmek için yöntem bir `int`.</span><span class="sxs-lookup"><span data-stu-id="c2f65-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="c2f65-120">İkinci bağımsız değişkeni [Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) bayt dizisi başlangıç dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2f65-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2f65-121">Çıkış, bilgisayarınızın mimarisine endianess bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c2f65-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c2f65-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2f65-122">Example</span></span>  
 <span data-ttu-id="c2f65-123">Bu örnekte, <xref:System.BitConverter.GetBytes%28System.Int32%29> yöntemi <xref:System.BitConverter> sınıfı dönüştürmek için çağrıldığında bir `int` bir bayt dizisi için.</span><span class="sxs-lookup"><span data-stu-id="c2f65-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2f65-124">Çıkış, bilgisayarınızın mimarisine endianess bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c2f65-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c2f65-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2f65-125">See Also</span></span>  
 <xref:System.BitConverter>  
 <xref:System.BitConverter.IsLittleEndian>  
 [<span data-ttu-id="c2f65-126">Türler</span><span class="sxs-lookup"><span data-stu-id="c2f65-126">Types</span></span>](../../../csharp/programming-guide/types/index.md)
