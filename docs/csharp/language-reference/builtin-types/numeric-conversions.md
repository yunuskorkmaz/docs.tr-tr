---
description: "C 'deki yerleşik sayısal türler arasında örtük ve açık dönüştürmeler hakkında bilgi edinin #"
title: Yerleşik sayısal dönüşümler-C# başvurusu
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: ee5def3b5e0e067919a8c8335db701dbb6dd4d88
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142251"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Yerleşik sayısal dönüşümler (C# Başvurusu)

C#, [integral](integral-numeric-types.md) ve [kayan nokta](floating-point-numeric-types.md) sayısal türleri kümesi sağlar. Örtük veya açık olmak üzere iki sayısal tür arasında bir dönüştürme var. Açık bir dönüştürme gerçekleştirmek için bir [atama ifadesi](../operators/type-testing-and-cast.md#cast-expression) kullanmanız gerekir.

## <a name="implicit-numeric-conversions"></a>Örtük Sayısal dönüştürmeler

Aşağıdaki tabloda, yerleşik sayısal türler arasında önceden tanımlanmış örtük dönüştürmeler gösterilmektedir:

|Kaynak|Amaç|
|----------|--------|
|[SByte](integral-numeric-types.md)|`short`, `int` , `long` , `float` , `double` veya `decimal`|
|[bayt](integral-numeric-types.md)|`short`, `ushort` , `int` , `uint` , `long` , `ulong` , `float` , `double` veya `decimal`|
|[short](integral-numeric-types.md)|`int`,,, `long` `float` `double` veya `decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint` , `long` , `ulong` , `float` , `double` veya `decimal`|
|[int](integral-numeric-types.md)|`long`, `float` , `double` veya `decimal`|
|[uint](integral-numeric-types.md)|`long`,,, `ulong` `float` `double` veya `decimal`|
|[long](integral-numeric-types.md)|`float`, `double` , veya `decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double` , veya `decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> `int`,, `uint` `long` , Veya türünden `ulong` `float` ve öğesinden veya türünden örtük dönüştürmeler `long` `ulong` `double` duyarlık kaybına neden olabilir, ancak hiçbir şekilde bir büyüklük kaybı olmaz. Diğer örtük sayısal dönüştürmeler hiçbir bilgiyi hiçbir şekilde kaybetmez.

Ayrıca,

- Tüm [integral sayısal türleri](integral-numeric-types.md) örtük olarak herhangi bir [kayan nokta sayısal türüne](floating-point-numeric-types.md)dönüştürülebilir.

- Ve türlerine örtük dönüştürmeler yoktur `byte` `sbyte` . Ve türlerinden örtük dönüştürmeler yoktur `double` `decimal` .

- `decimal`Tür ve veya türleri arasında örtük dönüştürme yok `float` `double` .

- Türünde sabit bir ifadenin değeri `int` (örneğin, bir tamsayı değişmez değeri ile temsil edilen bir değer) örtük olarak,,,, `sbyte` veya, `byte` `short` `ushort` `uint` `ulong` hedef türü aralığı içindeyse,,,, veya öğesine dönüştürülebilir:

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Yukarıdaki örnekte gösterildiği gibi, sabit değer hedef türünün aralığı içinde değilse, bir derleyici hatası [CS0031](../../misc/cs0031.md) oluşur.

## <a name="explicit-numeric-conversions"></a>Açık sayısal dönüştürmeler

Aşağıdaki tabloda, [örtük dönüştürme](#implicit-numeric-conversions)olmayan yerleşik sayısal türler arasında önceden tanımlanmış açık dönüştürmeler gösterilmektedir:

|Kaynak|Amaç|
|----------|--------|
|[SByte](integral-numeric-types.md)|`byte`, `ushort` , `uint` veya `ulong`|
|[bayt](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`,,, `byte` `ushort` `uint` veya `ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte` , veya `short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `uint` veya `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`,,, `byte` `short` `ushort` veya `int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` veya `ulong`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` veya `long`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` veya `decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `float` , veya `decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `float` , veya `double`|

> [!NOTE]
> Açık bir sayısal dönüştürme, veri kaybına neden olabilir veya genellikle bir özel durum oluşturabilir <xref:System.OverflowException> .

Ayrıca,

- İntegral türdeki bir değeri başka bir integral türüne dönüştürdüğünüzde, sonuç taşma [Denetim bağlamına](../keywords/checked-and-unchecked.md)bağlıdır. Denetlenen bir bağlamda, kaynak değer hedef türünün aralığı içindeyse dönüştürme başarılı olur. Aksi takdirde, bir oluşturulur <xref:System.OverflowException> . İşaretlenmemiş bir bağlamda, dönüştürme her zaman başarılı olur ve şu şekilde devam eder:

  - Kaynak türü hedef türünden büyükse, "ekstra" en önemli bitleri atarak kaynak değer kesilir. Sonuç daha sonra hedef türünün bir değeri olarak değerlendirilir.

  - Kaynak türü hedef türünden küçükse, hedef türle aynı boyutta olması için, kaynak değeri ya imza veya sıfır genişletilmiş ya da sıfır genişletilmiş olur. Kaynak türü imzalanmışsa, oturum açma uzantısı kullanılır; Kaynak türü işaretsiz ise sıfır uzantı kullanılır. Sonuç daha sonra hedef türünün bir değeri olarak değerlendirilir.

  - Kaynak türü hedef türle aynı boyutta ise, kaynak değer hedef türün bir değeri olarak değerlendirilir.

- Bir `decimal` değeri integral türüne dönüştürdüğünüzde, bu değer en yakın tamsayı değerine sıfır doğru yuvarlanır. Elde edilen integral değeri, hedef türü aralığının dışındaysa, bir <xref:System.OverflowException> atılır.

- Bir `double` veya `float` değerini bir integral türüne dönüştürdüğünüzde, bu değer en yakın tamsayı değerine sıfır doğru yuvarlanır. Elde edilen integral değeri, hedef türü aralığının dışındaysa sonuç, taşma [denetimi bağlamına](../keywords/checked-and-unchecked.md)bağlıdır. Denetlenen bir bağlamda, bir <xref:System.OverflowException> işaretsiz bağlamda, sonuç, hedef türün belirtilmeyen bir değeri olur.

- ' A dönüştürdüğünüzde `double` `float` `double` değer en yakın `float` değere yuvarlanır. `double`Değer çok küçükse veya türe sığmayacak kadar büyükse `float` , sonuç sıfır veya sonsuzluk olur.

- Ya da ' a dönüştürdüğünüzde `float` `double` `decimal` , kaynak değer `decimal` gösterimine dönüştürülür ve gerekirse 28 ondalık haneli, en yakın sayıya yuvarlanır. Kaynak değerin değerine bağlı olarak, aşağıdaki sonuçlardan biri meydana gelebilir:

  - Kaynak değeri bir olarak gösterilemeyecek kadar küçükse `decimal` , sonuç sıfır olur.

  - Kaynak değeri NaN (sayı değil), sonsuz veya bir olarak temsil edilebilmesi için çok büyük ise `decimal` , <xref:System.OverflowException> oluşturulur.

- `decimal`Veya ' a dönüştürdüğünüzde `float` , `double` kaynak değer sırasıyla en yakın `float` veya `double` değere yuvarlanır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Örtük Sayısal dönüştürmeler](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Açık sayısal dönüştürmeler](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Atama ve tür dönüşümleri](../../programming-guide/types/casting-and-type-conversions.md)
