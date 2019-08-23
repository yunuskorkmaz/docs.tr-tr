---
title: 'Nasıl yapılır: Byte dizisini int C# programlama kılavuzuna dönüştürme'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: ffb00325bc04aad79d61558925546e0aa8544551
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921757"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Nasıl yapılır: Byte dizisini int 'e dönüştürme (C# Programlama Kılavuzu)
Bu örnek, bir bayt dizisini [int](../../language-reference/builtin-types/integral-numeric-types.md) 'e <xref:System.BitConverter> ve bir bayt dizisine geri dönüştürmek için sınıfını nasıl kullanacağınızı gösterir. Örneğin, ağ dışı baytları okuduktan sonra bayttan bir yerleşik veri türüne dönüştürmeniz gerekebilir. Örnekteki [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemine ek olarak, aşağıdaki tablo, <xref:System.BitConverter> sınıftaki baytları (bayt dizisinden bir diziyle) diğer yerleşik türlere dönüştüren sınıf içindeki yöntemleri listelemektedir.  
  
|Döndürülen tür|Yöntem|  
|-------------------|------------|  
|`bool`|[ToBoolean (bayt\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|  
|`char`|[ToChar (bayt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|  
|`double`|[ToDouble (bayt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|  
|`short`|[ToInt16 (bayt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|  
|`int`|[ToInt32 (bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|  
|`long`|[ToInt64 (bayt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|  
|`float`|[ToSingle (bayt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|  
|`ushort`|[ToUInt16 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|  
|`uint`|[ToUInt32 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|  
|`ulong`|[ToUInt64 (bayt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir bayt dizisini başlatır, bilgisayar mimarisi az endian ise diziyi tersine çevirir (yani, ilk olarak en az önemli bayt depolanır) ve ardından dönüştürmek için [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemini çağırır dizideki dört bayt `int`. [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) için ikinci bağımsız değişken bayt dizisinin başlangıç dizinini belirtir.  
  
> [!NOTE]
> Çıktı, bilgisayarınızın mimarisinin bitiminden birine bağlı olarak farklılık gösterebilir.  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.BitConverter.GetBytes%28System.Int32%29> <xref:System.BitConverter> sınıfının yöntemi bir `int` bayt dizisine dönüştürmek için çağırılır.  
  
> [!NOTE]
> Çıktı, bilgisayarınızın mimarisinin bitiminden birine bağlı olarak farklılık gösterebilir.  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Türler](./index.md)
