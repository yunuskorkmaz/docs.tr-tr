---
title: Yerleşik sayısal dönüşümler- C# başvuru
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5380e8480c39d1940df13b2ecb50a0f394367388
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776035"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Yerleşik sayısal dönüşümler (C# başvuru)

C#[integral](integral-numeric-types.md) ve [kayan nokta](floating-point-numeric-types.md) sayısal türleri kümesi sağlar. Örtük veya açık olmak üzere iki sayısal tür arasında bir dönüştürme var. Açık bir dönüştürme çağırmak için [`()`cast işlecini](../operators/type-testing-and-cast.md#cast-operator-) kullanmanız gerekir.

## <a name="implicit-numeric-conversions"></a>Örtük Sayısal dönüştürmeler

Aşağıdaki tabloda, yerleşik sayısal türler arasında önceden tanımlanmış örtük dönüştürmeler gösterilmektedir:

|Başlangıç|Bitiş|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double`veya `decimal`|
|[byte](integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`veya `decimal`|
|[short](integral-numeric-types.md)|`int`, `long`, `float`, `double`veya `decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`veya `decimal`|
|[int](integral-numeric-types.md)|`long`, `float`, `double`veya `decimal`|
|[uint](integral-numeric-types.md)|`long`, `ulong`, `float`, `double`veya `decimal`|
|[long](integral-numeric-types.md)|`float`, `double`veya `decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double`veya `decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> `int`, `uint`, `long`ya da `ulong` 'den `float` ve `long` `ulong` ya da `double` arasında örtük dönüştürmeler, duyarlık kaybına neden olabilir, ancak hiçbir şekilde bir büyüklük kaybı olmaz. Diğer örtük sayısal dönüştürmeler hiçbir bilgiyi hiçbir şekilde kaybetmez.

Ayrıca,

- Tüm [integral sayısal türleri](integral-numeric-types.md) örtük olarak herhangi bir [kayan nokta sayısal türüne](floating-point-numeric-types.md)dönüştürülebilir.

- `byte` ve `sbyte` türlerine örtük dönüştürmeler yok. `double` ve `decimal` türlerinden örtük dönüştürmeler yok.

- `decimal` türü ile `float` veya `double` türleri arasında örtük dönüştürme yok.

- `int` türünde sabit bir ifadenin değeri (örneğin, bir tamsayı değişmez değeri ile temsil edilen bir değer), hedef türün aralığı içindeyse örtülü olarak `sbyte`, `byte`, `short`, `ushort`, `uint`veya `ulong`dönüştürülebilir :

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Yukarıdaki örnekte gösterildiği gibi, sabit değer hedef türünün aralığı içinde değilse, bir derleyici hatası [CS0031](../../misc/cs0031.md) oluşur.

## <a name="explicit-numeric-conversions"></a>Açık sayısal dönüştürmeler

Aşağıdaki tabloda, [örtük dönüştürme](#implicit-numeric-conversions)olmayan yerleşik sayısal türler arasında önceden tanımlanmış açık dönüştürmeler gösterilmektedir:

|Başlangıç|Bitiş|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`byte`, `ushort`, `uint`veya `ulong`|
|[byte](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint`veya `ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte`veya `short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`veya `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`veya `int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`veya `ulong`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`veya `long`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`veya `decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`veya `decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`veya `double`|

> [!NOTE]
> Açık bir sayısal dönüştürme, veri kaybına neden olabilir veya genellikle bir <xref:System.OverflowException>özel durum oluşturabilir.

Ayrıca,

- İntegral türdeki bir değeri başka bir integral türüne dönüştürdüğünüzde, sonuç taşma [Denetim bağlamına](../keywords/checked-and-unchecked.md)bağlıdır. Denetlenen bir bağlamda, kaynak değer hedef türünün aralığı içindeyse dönüştürme başarılı olur. Aksi takdirde, bir <xref:System.OverflowException> oluşturulur. İşaretlenmemiş bir bağlamda, dönüştürme her zaman başarılı olur ve şu şekilde devam eder:

  - Kaynak türü hedef türünden büyükse, "ekstra" en önemli bitleri atarak kaynak değer kesilir. Sonuç daha sonra hedef türünün bir değeri olarak değerlendirilir.

  - Kaynak türü hedef türünden küçükse, hedef türle aynı boyutta olması için, kaynak değeri ya imza veya sıfır genişletilmiş ya da sıfır genişletilmiş olur. Kaynak türü imzalanmışsa, oturum açma uzantısı kullanılır; Kaynak türü işaretsiz ise sıfır uzantı kullanılır. Sonuç daha sonra hedef türünün bir değeri olarak değerlendirilir.

  - Kaynak türü hedef türle aynı boyutta ise, kaynak değer hedef türün bir değeri olarak değerlendirilir.

- Bir `decimal` değerini bir integral türüne dönüştürdüğünüzde, bu değer en yakın tamsayı değerine sıfır doğru yuvarlanır. Elde edilen integral değeri, hedef türü aralığının dışındaysa bir <xref:System.OverflowException> oluşturulur.

- Bir `double` veya `float` değerini bir integral türüne dönüştürdüğünüzde, bu değer en yakın tamsayı değerine sıfır doğru yuvarlanır. Elde edilen integral değeri, hedef türü aralığının dışındaysa sonuç, taşma [denetimi bağlamına](../keywords/checked-and-unchecked.md)bağlıdır. Denetlenen bir bağlamda, bir <xref:System.OverflowException> atılır, ancak işaretlenmemiş bir bağlamda sonuç, hedef türünün belirtilmeyen bir değeridir.

- `double` `float`dönüştürdüğünüzde `double` değeri en yakın `float` değerine yuvarlanır. `double` değeri çok küçük veya `float` türüne sığmayacak kadar büyükse, sonuç sıfır veya sonsuzluk olur.

- `float` veya `double` `decimal`'e dönüştürdüğünüzde, kaynak değer `decimal` gösterimine dönüştürülür ve gerekirse 28 ondalık haneli, en yakın sayıya yuvarlanır. Kaynak değerin değerine bağlı olarak, aşağıdaki sonuçlardan biri meydana gelebilir:

  - Kaynak değeri `decimal`olarak gösterilemeyecek kadar küçükse, sonuç sıfır olur.

  - Kaynak değeri NaN (sayı değil), sonsuz veya `decimal`olarak temsil edilebilmesi için çok büyük ise, bir <xref:System.OverflowException> oluşturulur.

- `decimal` `float` veya `double`dönüştürdüğünüzde, kaynak değer sırasıyla en yakın `float` veya `double` değere yuvarlanır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Örtük Sayısal dönüştürmeler](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Açık sayısal dönüştürmeler](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [Atama ve tür dönüşümleri](../../programming-guide/types/casting-and-type-conversions.md)
