---
title: "Nasıl yapılır: Byte dizisini int'e - dönüştürme C# Programlama Kılavuzu"
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 3563b0ffd5360c575404ead81e0e847ccab46f0c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972436"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Nasıl yapılır: Byte dizisini int'e dönüştürme (C# Programlama Kılavuzu)
Bu örnek nasıl kullanılacağını gösterir <xref:System.BitConverter> sınıfı için bayt dizisine dönüştürmek için bir [int](../../../csharp/language-reference/keywords/int.md) ve tekrar bayt dizisi. Örneğin Ağ kapalı bayt okuduktan sonra gelen baytlar için yerleşik veri türü dönüştürmeniz gerekebilir. Ek olarak [Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) örnek yöntemi, aşağıdaki tabloda listelenmektedir yöntemleri <xref:System.BitConverter> diğer yerleşik türlerine (bayt dizesi) bayt dönüştürme sınıfı.  
  
|Döndürülen türü|Yöntem|  
|-------------------|------------|  
|`bool`|[ToBoolean (bayt\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|  
|`char`|[ToChar (bayt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|  
|`double`|[ToDouble (bayt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|  
|`short`|[Toınt16 (bayt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|  
|`int`|[Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|  
|`long`|[Toınt64 (bayt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|  
|`float`|[ToSingle (bayt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|  
|`ushort`|[Touınt16 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|  
|`uint`|[Touınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|  
|`ulong`|[Touınt64 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|  
  
## <a name="example"></a>Örnek  
 Bu örnek bir bayt dizisi başlatır, bilgisayar mimarisi endian ise dizi tersine çevirir (diğer bir deyişle, en az önemli bayt ilk depolanan) ve ardından çağırır [Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))dört bayt dizisine dönüştürmek için yöntemi bir `int`. İkinci bağımsız değişkeni [Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) bayt dizisi başlangıç dizinini belirtir.  
  
> [!NOTE]
>  Çıkış endianess bilgisayarınızın mimarisine bağlı olarak farklı olabilir.  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.BitConverter.GetBytes%28System.Int32%29> yöntemi <xref:System.BitConverter> sınıfı dönüştürmek için çağrılan bir `int` bayt dizisi.  
  
> [!NOTE]
>  Çıkış endianess bilgisayarınızın mimarisine bağlı olarak farklı olabilir.  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Türler](../../../csharp/programming-guide/types/index.md)
