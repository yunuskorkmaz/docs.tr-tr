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
ms.openlocfilehash: 5ca052dea4ee4abc866d2b02055188b0707499d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475939"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Açık Sayısal Dönüşümler Tablosu (C# Başvurusu)
Açık sayısal Dönüşüm, var olan herhangi bir örtük dönüştürmeyi atama ifadesini kullanarak diğer sayısal türleri, herhangi bir sayısal tür dönüştürmek için kullanılır. Aşağıdaki tabloda, bu dönüştürmeleri gösterilmektedir.  
  
 Dönüştürmeler hakkında daha fazla bilgi için bkz. [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong`, veya `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` veya `char`|  
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
  
-   Açık sayısal Dönüşüm, oluşturma özel durumların sonucu veya duyarlık kaybına neden olabilir.  
  
-   Dönüştürürken bir `decimal` bu değer bir tamsayı türüne değeri sıfır en yakın tamsayı değerine yuvarlanır. Sonuçta elde edilen tamsayı değeri hedef türün aralığı dışında ise bir <xref:System.OverflowException> oluşturulur.  
  
-   Gelen dönüştürürken bir `double` veya `float` değeri bir tamsayı türü için değer kısaltılır. Elde edilen tamsayı değer hedef değer aralığının dışında ise sonucu, içerik denetimi overflow'da bağlıdır. Denetlenen bir bağlamda bir `OverflowException` olduğu sırada işaretlenmemiş bir bağlamda, durum, hedef türünün belirtilmeyen bir değeri sonucudur.  
  
-   Dönüştürürken `double` için `float`, `double` değer yuvarlanır en yakın `float` değeri. Varsa `double` değeri çok küçük veya sığdırmak için çok büyük hedef türe sonucu sıfır ya da sonsuz olacaktır.  
  
-   Dönüştürürken `float` veya `double` için `decimal`, kaynak değeri dönüştürülür `decimal` gösterimi ve gerekirse 28 ondalık basamağın sonra en yakın sayıya yuvarlanır. Değerini kaynak bağlı olarak, aşağıdaki sonuçları biriyle karşılaşabilirsiniz:  
  
    -   Kaynak değeri olarak gösterilemeyecek kadar çok küçük ise bir `decimal`, sıfır sonuç olur.  
  
    -   Kaynak değerin NaN (sayı değil), varsa, sonsuz veya olarak gösterilemeyecek kadar çok büyük bir `decimal`, bir `OverflowException` oluşturulur.  
  
-   Dönüştürürken `decimal` için `float` veya `double`, `decimal` değer yuvarlanır en yakın `double` veya `float` değeri.  
  
 C# dil belirtiminde açık açık dönüştürme hakkında daha fazla bilgi için bkz. Spec erişim hakkında daha fazla bilgi için bkz. [C# dil belirtimi](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
- [() İşleci](../../../csharp/language-reference/operators/invocation-operator.md)  
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
