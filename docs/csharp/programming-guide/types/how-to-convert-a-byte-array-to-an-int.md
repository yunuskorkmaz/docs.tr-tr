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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Nasıl yapılır: byte Dizisini int'e Dönüştürme (C# Programlama Kılavuzu)

Bu örnek, bir bayt dizisini bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 'e ve bir bayt dizisine geri dönüştürmek için <xref:System.BitConverter> sınıfının nasıl kullanılacağını gösterir. Örneğin, ağ dışı baytları okuduktan sonra bayttan bir yerleşik veri türüne dönüştürmeniz gerekebilir. Örnekteki [ToInt32 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemine ek olarak aşağıdaki tablo, <xref:System.BitConverter> sınıfındaki, baytları (bir bayt dizisinden) diğer yerleşik türlere dönüştüren yöntemleri listeler.

|Döndürülen tür|Yöntem|
|-------------------|------------|
|`bool`|[ToBoolean (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble (bayt @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[Toınt16 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[Toınt32 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[Toınt64 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[Touınt16 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[Touınt32 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[Touınt64 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Örnek

Bu örnek, bir bayt dizisini başlatır, bilgisayar mimarisi az endian ise diziyi tersine çevirir (yani, ilk olarak en az önemli bayt depolanır) ve ardından, dört baytı dönüştürmek için [ToInt32 (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) yöntemini çağırır. dizi `int`. Toınt32 ikinci bağımsız değişkeni [(Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) bayt dizisinin başlangıç dizinini belirtir.

> [!NOTE]
> Çıktı, bilgisayarınızın mimarisinin bitiminden birine bağlı olarak farklılık gösterebilir.

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>Örnek

Bu örnekte, <xref:System.BitConverter> sınıfının <xref:System.BitConverter.GetBytes%28System.Int32%29> yöntemi `int` bir bayt dizisine dönüştürmek için çağırılır.

> [!NOTE]
> Çıktı, bilgisayarınızın mimarisinin bitiminden birine bağlı olarak farklılık gösterebilir.

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Türler](./index.md)
