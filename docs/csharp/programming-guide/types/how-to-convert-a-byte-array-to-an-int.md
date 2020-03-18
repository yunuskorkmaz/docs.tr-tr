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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Bayt dizisini int'e dönüştürme (C# Programlama Kılavuzu)

Bu örnek, bir bayt dizisini <xref:System.BitConverter> [int'e](../../language-reference/builtin-types/integral-numeric-types.md) dönüştürmek ve bir bayt dizisine geri dönmek için sınıfı nasıl kullanacağınızı gösterir. Örneğin, ağdan baytokuduktan sonra baytlardan yerleşik veri türüne dönüştürmeniz gerekebilir. Örnekteki [ToInt32(Byte,\[\]Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemine ek olarak, aşağıdaki tabloda baytları (bayt dizisinden) diğer yerleşik türlere dönüştüren yöntemler <xref:System.BitConverter> listelenir.

|Döndürülen tür|Yöntem|
|-------------------|------------|
|`bool`|[ToBoolean(Bayt,\[\]Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar(Bayt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble(Bayt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[ToInt16(Bayt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[ToInt32(Bayt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[ToInt64(Bayt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle(Bayt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[ToUInt16(Bayt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[ToUInt32(Bayt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[ToUInt64(Bayt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Örnek

Bu örnek, bir bayt dizisini başharfe çevirir, bilgisayar mimarisi az endian ise diziyi tersine çevirir (yani, en [\[\]](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) az öneme sahip bayt önce depolanır) ve ardından dizideki dört `int`bayt'ı bir . [ToInt32(Byte,\[\]Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) için ikinci bağımsız değişken bayt dizisinin başlangıç dizini belirtir.

> [!NOTE]
> Çıktı, bilgisayarınızın mimarisinin son özelliklerine bağlı olarak farklılık gösterebilir.

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>Örnek

Bu örnekte, <xref:System.BitConverter.GetBytes%28System.Int32%29> <xref:System.BitConverter> sınıfın yöntemi bir `int` bayt dizisine dönüştürmek için çağrılır.

> [!NOTE]
> Çıktı, bilgisayarınızın mimarisinin son özelliklerine bağlı olarak farklılık gösterebilir.

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Türler](./index.md)
