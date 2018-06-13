---
title: Açık Sayısal Dönüşümler Tablosu (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 7363df3e4b2449924222745de409fd68349b93de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218390"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Açık Sayısal Dönüşümler Tablosu (C# Başvurusu)
Açık sayısal dönüşüm var olduğu örtük dönüştürme, bir cast ifadesi kullanarak herhangi diğer bir sayısal tür, herhangi bir sayısal tür dönüştürmek için kullanılır. Aşağıdaki tabloda bu dönüşümleri gösterir.  
  
 Dönüştürme hakkında daha fazla bilgi için bkz: [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong`, veya `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` Veya `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong`, veya `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`, `byte`, `short`, veya `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, veya `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, veya `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, veya `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, veya `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`, `byte`, veya `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, veya `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, veya `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, veya `double`|  
  
## <a name="remarks"></a>Açıklamalar  
  
-   Açık sayısal dönüşüm oluşturma durumlar duyarlık veya sonuç kaybına neden olabilir.  
  
-   Dönüştürürken bir `decimal` en yakın tam sayı değeri sıfıra doğru tamsayı türü, bu değer değerine yuvarlanır. Sonuçta elde edilen tam sayı değeri hedef türü aralık dışında ise bir <xref:System.OverflowException> oluşturulur.  
  
-   Gelen dönüştürürken bir `double` veya `float` tamsayı türü, değerin değerine kısaltılır. Sonuç tam sayı değeri hedef değeri aralığın dışında ise, sonuç bağlamını kontrol taşma bağlıdır. Checked bağlamında bir `OverflowException` olduğu sırada denetlenmeyen bir bağlamda, durum, hedef türü belirtilmeyen bir değeri sonucudur.  
  
-   Dönüştürürken `double` için `float`, `double` değeri yuvarlanır en yakın `float` değeri. Varsa `double` değeri çok küçük veya sığması için çok büyük hedef türü sonucu sıfır ya da sonsuz olacaktır.  
  
-   Dönüştürürken `float` veya `double` için `decimal`, kaynak değerin dönüştürülür `decimal` gösterimi ve gerekirse 28 ondalık basamak sonra en yakın sayıya yuvarlanır. Kaynak değerin değerini bağlı olarak, aşağıdaki sonuçları biriyle karşılaşabilirsiniz:  
  
    -   Kaynak değerin olarak gösterilemeyecek kadar küçük olup olmadığını bir `decimal`, sonuç sıfır olur.  
  
    -   Kaynak değerin NaN (sayı değil), ise sonsuz, veya olarak gösterilemeyecek kadar çok büyük bir `decimal`, bir `OverflowException` oluşturulur.  
  
-   Dönüştürürken `decimal` için `float` veya `double`, `decimal` değeri yuvarlanır en yakın `double` veya `float` değeri.  
  
 Açık dönüştürme hakkında daha fazla bilgi için C# dil belirtimi Explicit bakın. Spec erişim hakkında daha fazla bilgi için bkz: [C# dil belirtimi](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [() İşleci](../../../csharp/language-reference/operators/invocation-operator.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
