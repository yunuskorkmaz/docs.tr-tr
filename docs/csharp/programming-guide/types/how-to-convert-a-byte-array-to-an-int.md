---
title: Bir bayt dizisini int C# programlama kılavuzuna dönüştürme
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 9f477649dba1b42d7a10d521c010977707daf3ec
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698761"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Byte dizisini int 'e dönüştürme (C# Programlama Kılavuzu)

Bu örnek, bir bayt dizisinin bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 'e ve bir bayt dizisine geri dönüştürülmesi için <xref:System.BitConverter> sınıfını nasıl kullanacağınızı gösterir. Örneğin, ağ dışı baytları okuduktan sonra bayttan bir yerleşik veri türüne dönüştürmeniz gerekebilir. Örnekteki [ToInt32 (byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemine ek olarak, aşağıdaki tablo, baytları (bayt dizisinden bir diziden) diğer yerleşik türlere dönüştüren <xref:System.BitConverter> sınıfındaki yöntemleri listelemektedir.

|Döndürülen tür|Yöntem|
|-------------------|------------|
|`bool`|[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar (bayt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble (bayt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[Toınt16 (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[Toınt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[Toınt64 (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[Touınt16 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[Touınt32 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[Touınt64 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Örnek

Bu örnek, bir bayt dizisini başlatır, bilgisayar mimarisi az endian ise diziyi tersine çevirir (yani öncelikle en az önemli bayt depolanır) ve sonra dizideki dört baytı bir `int`dönüştürmek için [ToInt32 (byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemini çağırır. Toınt32 için ikinci bağımsız değişken [(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) bayt dizisinin başlangıç dizinini belirtir.

> [!NOTE]
> Çıktı, bilgisayarınızın mimarisinin bitiliğine bağlı olarak farklılık gösterebilir.

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>Örnek

Bu örnekte, bir `int` bayt dizisine dönüştürmek için <xref:System.BitConverter> sınıfının <xref:System.BitConverter.GetBytes%28System.Int32%29> yöntemi çağırılır.

> [!NOTE]
> Çıktı, bilgisayarınızın mimarisinin bitiliğine bağlı olarak farklılık gösterebilir.

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Türler](./index.md)
