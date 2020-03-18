---
title: Yerleşik sayısal dönüşümler - C# başvurusu
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5380e8480c39d1940df13b2ecb50a0f394367388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399604"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Yerleşik sayısal dönüşümler (C# başvurusu)

C# [integral](integral-numeric-types.md) ve [kayan nokta](floating-point-numeric-types.md) sayısal türleri kümesi sağlar. Örtük veya açık olan iki sayısal tür arasında bir dönüşüm vardır. Açık bir dönüştürme çağırmak için [döküm işleci `()` ](../operators/type-testing-and-cast.md#cast-operator-) kullanmanız gerekir.

## <a name="implicit-numeric-conversions"></a>Örtük sayısal dönüşümler

Aşağıdaki tablo, yerleşik sayısal türler arasındaki önceden tanımlanmış örtük dönüşümleri gösterir:

|Başlangıç|Alıcı|
|----------|--------|
|[Sbyte](integral-numeric-types.md)|`short`, `int` `long`, `float` `double`, , veya`decimal`|
|[Bayt](integral-numeric-types.md)|`short`, `ushort` `int`, `uint` `long`, `ulong` `float`, `double`, , veya`decimal`|
|[short](integral-numeric-types.md)|`int`, `long` `float`, `double`, veya`decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint` `long`, `ulong` `float`, `double`, , veya`decimal`|
|[int](integral-numeric-types.md)|`long`, `float` `double`, veya`decimal`|
|[Uint](integral-numeric-types.md)|`long`, `ulong` `float`, `double`, veya`decimal`|
|[long](integral-numeric-types.md)|`float`, `double`veya`decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double`veya`decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> `int`' `uint` `ulong` `float` `long` `ulong` `double` den, , veya gelen veya ya da gelen örtük dönüşümler kesinlik kaybına neden olabilir, ancak büyüklük bir sipariş kaybı asla. `long` Diğer örtük sayısal dönüşümler hiçbir zaman bilgi kaybetmez.

Ayrıca unutmayın

- Herhangi bir [integral sayısal türü](integral-numeric-types.md) örtülü olarak herhangi bir [kayan nokta sayısal türüne](floating-point-numeric-types.md)dönüştürülebilir.

- Örtük dönüşümler `byte` ve `sbyte` türleri vardır. Ve `double` `decimal` türlerden örtülü dönüşümler yoktur.

- `decimal` Tür ve `float` tür veya `double` türleri arasında örtülü dönüşüm yoktur.

- Türünün `int` sabit bir ifadesinin değeri (örneğin, bir tamsayı ile temsil edilen bir değer) `sbyte` `byte`dolaylı `short` `ushort`olarak `uint`, `ulong`, , , veya , hedef türünün aralığında ysa dönüştürülebilir:

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Yukarıdaki örnekte de görüldüğü gibi, sabit değer hedef türü aralığında değilse, [cs0031](../../misc/cs0031.md) derleyici hatası oluşur.

## <a name="explicit-numeric-conversions"></a>Açık sayısal dönüşümler

Aşağıdaki tablo, [örtülü dönüştürme](#implicit-numeric-conversions)bulunmayan yerleşik sayısal türler arasındaki önceden tanımlanmış açık dönüşümleri gösterir:

|Başlangıç|Alıcı|
|----------|--------|
|[Sbyte](integral-numeric-types.md)|`byte`, `ushort` `uint`, veya`ulong`|
|[Bayt](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte` `ushort`, `uint`, veya`ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte`veya`short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `uint`, , veya`ulong`|
|[Uint](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort`, veya`int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint`, , veya`ulong`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint`, , veya`long`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong`, , veya`decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , veya`decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , veya`double`|

> [!NOTE]
> Açık bir sayısal dönüştürme veri kaybına neden olabilir veya genellikle <xref:System.OverflowException>bir özel durum atabilir.

Ayrıca unutmayın

- İntegral türündeki bir değeri başka bir integral türüne dönüştürdüğünüzde, sonuç taşma [denetimi bağlamına](../keywords/checked-and-unchecked.md)bağlıdır. Denetlenen bir bağlamda, kaynak değeri hedef türün aralığındaysa dönüştürme başarılı olur. Aksi takdirde, bir <xref:System.OverflowException> atılır. Denetlenmemiş bir bağlamda, dönüştürme her zaman başarılı dır ve aşağıdaki gibi devam eder:

  - Kaynak türü hedef kinden daha büyükse, kaynak değeri "ekstra" en önemli bitleri atılarak kesilir. Sonuç daha sonra hedef türünün bir değeri olarak kabul edilir.

  - Kaynak türü hedef türünden küçükse, kaynak değeri işaretle genişletilmiş veya hedef türüyle aynı boyutta olacak şekilde sıfır uzatılır. Kaynak türü imzalanırsa işaret uzantısı kullanılır; kaynak türü imzalanmamışsa sıfır uzantısı kullanılır. Sonuç daha sonra hedef türünün bir değeri olarak kabul edilir.

  - Kaynak türü hedef türüyle aynı boyuttaysa, kaynak değeri hedef türün değeri olarak kabul edilir.

- Bir `decimal` değeri integral türüne dönüştürdüğünüzde, bu değer en yakın integral değerine sıfıra yuvarlanır. Elde edilen integral değeri hedef türün aralığının <xref:System.OverflowException> dışındaysa, bir atılır.

- Bir `double` veya `float` değeri integral türüne dönüştürdüğünüzde, bu değer en yakın integral değerine sıfıra yuvarlanır. Elde edilen integral değeri hedef türünün aralığının dışındaysa, sonuç taşma [denetimi bağlamına](../keywords/checked-and-unchecked.md)bağlıdır. Denetlenen bir bağlamda, <xref:System.OverflowException> işaretlenmemiş bir bağlamda sonuç hedef türünün belirtilmemiş bir değeri iken, bir atılmıştır.

- Dönüştürüldüğünüzde `double` `float` `double` , değer en yakın `float` değere yuvarlanır. `double` Değer türe sığmayacak kadar küçük veya `float` çok büyükse, sonuç sıfır veya sonsuzdur.

- Dönüştürdüğünüzde `float` `double` veya `decimal`dönüştürdüğüzde, kaynak `decimal` değeri temsile dönüştürülür ve gerekirse 28. Kaynak değerin değerine bağlı olarak, aşağıdaki sonuçlardan biri oluşabilir:

  - Kaynak değeri temsil edilemeyecek kadar `decimal`küçükse, sonuç sıfır olur.

  - Kaynak değeri NaN ise (sayı değil), sonsuzluk veya bir `decimal`, bir <xref:System.OverflowException> olarak temsil edilemeyecek kadar büyük.

- Kaynak değeri `decimal` `float` `double`sırasıyla en yakın `float` veya `double` değere yuvarlanır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Örtük sayısal dönüşümler](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Açık sayısal dönüşümler](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Döküm ve tür dönüşümleri](../../programming-guide/types/casting-and-type-conversions.md)
