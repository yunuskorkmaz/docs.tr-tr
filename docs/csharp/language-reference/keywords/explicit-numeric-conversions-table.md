---
title: Açık sayısal dönüşümler tablosu (C# Başvurusu)
ms.date: 09/06/2018
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 22bb2117e7b78596e1fb6af63584f51b066564c9
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342257"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Açık sayısal dönüşümler tablosu (C# Başvurusu)

Aşağıdaki tabloda önceden tanımlanmış açık dönüştürmeler kendisi için .NET sayısal türler arasında gösterir. hiçbir [örtük dönüştürme](implicit-numeric-conversions-table.md).

|Başlangıç|Bitiş|  
|----------|--------|  
|[sbyte](sbyte.md)|`byte`, `ushort`, `uint`, `ulong`, veya `char`|  
|[byte](byte.md)|`sbyte` veya `char`|  
|[short](short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong`, veya `char`|  
|[ushort](ushort.md)|`sbyte`, `byte`, `short`, veya `char`|  
|[int](int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, veya `char`|  
|[uint](uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, veya `char`|  
|[long](long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, veya `char`|  
|[ulong](ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, veya `char`|  
|[char](char.md)|`sbyte`, `byte`, veya `short`|  
|[float](float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, veya `decimal`|  
|[double](double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, veya `decimal`|  
|[decimal](decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, veya `double`|  
  
## <a name="remarks"></a>Açıklamalar  
  
- Genellikle bir özel durum atma açık sayısal dönüşüm duyarlık veya sonuç kaybına neden olabilir bir <xref:System.OverflowException>.  

- Başka bir integral türü bir tam sayı türünde bir değer dönüştürdüğünüzde, sonucu overflow'da bağlıdır [içerik denetimi](checked-and-unchecked.md). Kaynak değeri hedef türün aralığı içinde ise, denetlenen bir bağlamda dönüştürme başarılı olur. Aksi takdirde, bir <xref:System.OverflowException> oluşturulur. İşaretlenmemiş bir bağlamda dönüştürme her zaman başarılı olur ve aşağıdaki gibi çalışır:

  - Kaynak türü hedef türünden daha büyük ise sonra kaynak değeri, "fazladan" atarak kesilmiş en önemli bitleri. Sonuç, ardından hedef türünde bir değer kabul edilir.

  - Kaynak türü, hedef türünden küçükse, hedef türüyle aynı boyutta olması ardından kaynağı işaret genişletilmiş veya sıfır genişletilmiş değeridir. Kaynak türü açtıysanız oturum uzantısı kullanılır. Kaynak türü imzalanmamış ise sıfır uzantısı kullanılır. Sonuç, ardından hedef türünde bir değer kabul edilir.

  - Hedef türü olarak aynı boyutta kaynak türü ise kaynak değer hedef türünde bir değer kabul edilir.
  
- Dönüştürürken bir `decimal` bu değer bir tamsayı türüne değeri sıfır en yakın tamsayı değerine yuvarlanır. Sonuçta elde edilen tamsayı değeri hedef türün aralığı dışında ise bir <xref:System.OverflowException> oluşturulur.  
  
- Dönüştürürken bir `double` veya `float` bu değer bir tamsayı türüne değeri sıfır en yakın tamsayı değerine yuvarlanır. Elde edilen tamsayı değeri hedef türün aralığı dışında ise, sonuç overflow'da bağlıdır [içerik denetimi](checked-and-unchecked.md). Denetlenen bir bağlamda bir <xref:System.OverflowException> olduğu sırada işaretlenmemiş bir bağlamda, durum, hedef türünün belirtilmeyen bir değeri sonucudur.  
  
- Dönüştürürken `double` için `float`, `double` değer yuvarlanır en yakın `float` değeri. Varsa `double` değeri çok küçük veya sığdırmak için çok büyük hedef türe sonucu sıfır ya da sonsuz olacaktır.  
  
- Dönüştürürken `float` veya `double` için `decimal`, kaynak değeri dönüştürülür `decimal` gösterimi ve gerekirse 28 ondalık basamağın sonra en yakın sayıya yuvarlanır. Değerini kaynak bağlı olarak, aşağıdaki sonuçları biriyle karşılaşabilirsiniz:  

  - Kaynak değeri olarak gösterilemeyecek kadar çok küçük ise bir `decimal`, sıfır sonuç olur.  

  - Kaynak değerin NaN (sayı değil), varsa, sonsuz veya olarak gösterilemeyecek kadar çok büyük bir `decimal`, bir <xref:System.OverflowException> oluşturulur.  
  
- Dönüştürürken `decimal` için `float` veya `double`, `decimal` değer yuvarlanır en yakın `double` veya `float` değeri.  
  
 Açık dönüştürmeler hakkında daha fazla bilgi için bkz: [açık dönüştürmeler](/dotnet/csharp/language-reference/language-specification/conversions#explicit-conversions) bölümünü [C# dil belirtimi](../language-specification/index.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Atama ve tür dönüştürmeleri](../../programming-guide/types/casting-and-type-conversions.md)
- [() İşleci](../operators/invocation-operator.md)
- [Tam sayı türleri tablosu](integral-types-table.md)
- [Kayan nokta türleri tablosu](floating-point-types-table.md)
- [Yerleşik türler tablosu](built-in-types-table.md)
- [Örtük sayısal dönüşümler tablosu](implicit-numeric-conversions-table.md)
