---
title: Örtük Sayısal Dönüşümler Tablosu (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 2d417a2020656f300de0517526742679388f262e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Örtük Sayısal Dönüşümler Tablosu (C# Başvurusu)
Aşağıdaki tabloda önceden tanımlanmış örtük sayısal dönüşümler gösterir. Örtük dönüşümler yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`, `int`, `long`, `float`, `double`, veya `decimal`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`, `long`, `float`, `double`, veya `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`, `float`, `double`, veya `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`, `ulong`, `float`, `double`, veya `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`, `double`, veya `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`, `double`, veya `decimal`|  
  
## <a name="remarks"></a>Açıklamalar  
  
-   Dönüşümleri içinde duyarlık ancak değil büyüklük kaybedilebilir `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.  
  
-   Hiçbir örtük dönüşümler vardır `char` türü.  
  
-   Kayan nokta türleri arasında örtük hiçbir dönüştürme vardır ve `decimal` türü.  
  
-   Sabit bir ifade türü `int` dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, sağlanan Hedef aralık içinde sabit ifade değeri yazın.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
