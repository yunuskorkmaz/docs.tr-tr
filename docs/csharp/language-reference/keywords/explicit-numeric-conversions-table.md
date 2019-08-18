---
title: Açık sayısal dönüştürmeler tablosu- C# başvuru
ms.custom: seodec18
ms.date: 09/06/2018
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 4dee46d075ea3d45d53ac0f64b539231188cf867
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566322"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Açık Sayısal Dönüşümler Tablosu (C# başvuru)

Aşağıdaki tabloda, [örtük dönüştürme](implicit-numeric-conversions-table.md)olmayan .net sayısal türleri arasında önceden tanımlanmış açık dönüştürmeler gösterilmektedir.

|Başlangıç|Bitiş|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`byte``ushort` ,,,`uint`veya `ulong``char`|  
|[byte](../builtin-types/integral-numeric-types.md)|`sbyte` veya `char`|  
|[short](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`ushort`, ,veya`uint` `ulong``char`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`,veya `short``char`|  
|[int](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`uint`,veya `ulong` `ushort``char`|  
|[uint](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`short`, ,veya`ushort` `int``char`|  
|[long](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`int`, ,`uint`veya `ushort` `ulong``char`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`int`, ,`uint`veya `ushort` `long``char`|  
|[char](char.md)|`sbyte`, `byte`, veya`short`|  
|[float](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`int`, ,`long`,, ,`char`veya `ushort` `uint` `ulong``decimal`|  
|[double](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`int`, ,`long`,,, ,`float`veya `ushort` `uint` `ulong` `char``decimal`|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`int`, ,`long`,,, ,`float`veya `ushort` `uint` `ulong` `char``double`|  
  
## <a name="remarks"></a>Açıklamalar  
  
- Açık sayısal dönüştürme duyarlık kaybına neden olabilir veya tipik olarak bir <xref:System.OverflowException>özel durum oluşturulmasına yol açabilir.  

- İntegral türdeki bir değeri başka bir integral türüne dönüştürdüğünüzde, sonuç taşma [Denetim bağlamına](checked-and-unchecked.md)bağlıdır. Denetlenen bir bağlamda, kaynak değer hedef türünün aralığı içindeyse dönüştürme başarılı olur. Aksi takdirde, <xref:System.OverflowException> bir oluşturulur. İşaretlenmemiş bir bağlamda, dönüştürme her zaman başarılı olur ve şu şekilde devam eder:

  - Kaynak türü hedef türünden büyükse, "ekstra" en önemli bitleri atarak kaynak değer kesilir. Sonuç daha sonra hedef türünün bir değeri olarak değerlendirilir.

  - Kaynak türü hedef türünden küçükse, hedef türle aynı boyutta olması için, kaynak değeri ya imza veya sıfır genişletilmiş ya da sıfır genişletilmiş olur. Kaynak türü imzalanmışsa, oturum açma uzantısı kullanılır; Kaynak türü işaretsiz ise sıfır uzantı kullanılır. Sonuç daha sonra hedef türünün bir değeri olarak değerlendirilir.

  - Kaynak türü hedef türle aynı boyutta ise, kaynak değer hedef türün bir değeri olarak değerlendirilir.
  
- Bir `decimal` değeri integral türüne dönüştürdüğünüzde, bu değer en yakın tamsayı değerine sıfır doğru yuvarlanır. Elde edilen integral değeri, hedef türü aralığının dışındaysa, bir <xref:System.OverflowException> atılır.  
  
- Bir veya `double` `float` değerini bir integral türüne dönüştürdüğünüzde, bu değer en yakın tamsayı değerine sıfır doğru yuvarlanır. Elde edilen integral değeri, hedef türü aralığının dışındaysa sonuç, taşma [denetimi bağlamına](checked-and-unchecked.md)bağlıdır. Denetlenen bir bağlamda, bir <xref:System.OverflowException> işaretsiz bağlamda, sonuç, hedef türün belirtilmeyen bir değeri olur.  
  
- `float`' `double` Adönüştürdüğünüzde`float` değer en yakın değere yuvarlanır. `double` `double` Değer çok küçükse veya hedef türüne sığmayacak kadar büyükse, sonuç sıfır veya sonsuz olur.  
  
- `float` `decimal` Ya da`double` ' a dönüştürdüğünüzde, kaynak değer gösterimine dönüştürülür ve gerekirse 28 ondalık haneli, en yakın sayıya yuvarlanır. `decimal` Kaynak değerin değerine bağlı olarak, aşağıdaki sonuçlardan biri meydana gelebilir:  

  - Kaynak değeri bir `decimal`olarak gösterilemeyecek kadar küçükse, sonuç sıfır olur.  

  - Kaynak değeri NaN (sayı değil), sonsuz veya bir `decimal`olarak temsil edilebilmesi için çok büyük ise <xref:System.OverflowException> , oluşturulur.  
  
- `float` Veya 'adönüştürdüğünüzde`decimal` değerenyakın`double` veya değere`float` yuvarlanır. `decimal` `double`  
  
 Açık dönüştürmeler hakkında daha fazla bilgi için, [ C# dil belirtiminin](../language-specification/index.md) [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [Atama ve tür dönüşümleri](../../programming-guide/types/casting-and-type-conversions.md)
- [() işleci](../operators/type-testing-and-cast.md#cast-operator-)
- [Integral türleri](../builtin-types/integral-numeric-types.md)
- [Kayan nokta türleri tablosu](../builtin-types/floating-point-numeric-types.md)
- [Yerleşik türler tablosu](built-in-types-table.md)
- [Örtük Sayısal dönüştürmeler tablosu](implicit-numeric-conversions-table.md)
