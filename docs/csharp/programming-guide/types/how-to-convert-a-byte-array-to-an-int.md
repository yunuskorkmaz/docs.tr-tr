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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Nasıl yapılır: byte Dizisini int'e Dönüştürme (C# Programlama Kılavuzu)
Bu örnek nasıl kullanılacağını gösterir <xref:System.BitConverter> sınıfı için bir bayt dizisi dönüştürmek için bir [int](../../../csharp/language-reference/keywords/int.md) daha sonra tekrar bir bayt dizisi. Örneğin Ağ kapalı bayt okuduktan sonra bayt, kaynağı bir yerleşik veri türüne dönüştürmek olabilir. Ek olarak [Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemi örnekte, aşağıdaki tabloda listelenmektedir yöntemleri <xref:System.BitConverter> diğer yerleşik türleri için (bayt dizesi) baytlar Dönüştür sınıfı.  
  
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
 Bu örnek bir bayt dizisi başlatır, bilgisayar mimarisi little endian ise dizi tersine çevirir (diğer bir deyişle, en az önemli bayt ilk depolanır) ve ardından çağırır [Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))dört bayt dizisine olarak dönüştürmek için yöntem bir `int`. İkinci bağımsız değişkeni [Toınt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) bayt dizisi başlangıç dizinini belirtir.  
  
> [!NOTE]
>  Çıkış, bilgisayarınızın mimarisine endianess bağlı olarak değişebilir.  
  
 [!code-csharp[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.BitConverter.GetBytes%28System.Int32%29> yöntemi <xref:System.BitConverter> sınıfı dönüştürmek için çağrıldığında bir `int` bir bayt dizisi için.  
  
> [!NOTE]
>  Çıkış, bilgisayarınızın mimarisine endianess bağlı olarak değişebilir.  
  
 [!code-csharp[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.BitConverter>  
 <xref:System.BitConverter.IsLittleEndian>  
 [Türler](../../../csharp/programming-guide/types/index.md)
