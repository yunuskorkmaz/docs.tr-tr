---
title: Bit düzeyinde ve kaydırma işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# gerçekleştirmek bit düzeyinde işleçler mantıksal veya tam sayı türleri olan işlenenler kaydırma işleçlerini.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: c18a06971887049a443f0bd1af7c77610a787a27
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609949"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Bit düzeyinde ve kaydırma işleçleri (C# Başvurusu)

Aşağıdaki işleçler bit düzeyinde gerçekleştirmek veya işlenenleri işlemleriyle kaydırmak [tam sayı türleri](../builtin-types/integral-numeric-types.md):

- Birli [ `~` (bit düzeyinde tamamlayıcı)](#bitwise-complement-operator-) işleci
- İkili [ `<<` (sola kaydırma)](#left-shift-operator-) ve [ `>>` (sağa kaydırma)](#right-shift-operator-) kaydırma işleçleri
- İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal veya)](#logical-or-operator-), ve [ `^` (mantıksal XOR)](#logical-exclusive-or-operator-) işleçleri

Bu işleçler için tanımlanan `int`, `uint`, `long`, ve `ulong` türleri. Her iki işlenen de integral türde olduğunda (`sbyte`, `byte`, `short`, `ushort`, veya `char`), değerlerine dönüştürülür `int` aynı zamanda bir işlemin sonuç türü olan türü. Değerleri, işlenenleri farklı tamsayı türleri olduğunda, en yakın kapsayan integral türüne dönüştürülür. Daha fazla bilgi için [sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

`&`, `|`, Ve `^` işleçleri için işlenenler de tanımlanır `bool` türü. Daha fazla bilgi için [Boolean mantıksal işleçler](boolean-logical-operators.md).

Bit düzeyinde kaydırma işleçlerini asla taşmaya neden ve aynı sonuçlar [checked ve unchecked](../keywords/checked-and-unchecked.md) bağlamı.

## <a name="bitwise-complement-operator-"></a>Bit düzeyinde tamamlama işleci ~

`~` İşleci her bit ters çevirerek bir bit düzeyinde tamamlayıcı işlenenin üretir:

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Ayrıca `~` sonlandırıcılar bildirmek için Sembol. Daha fazla bilgi için [sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Sola kaydırma işleci \<\<

`<<` İşleci sol işleneniyle tarafından sağ işlenen tarafından tanımlanan bit sayısı kadar sola kaydırır.

Sola kaydırma işleminin sonucu türü aralığının dışında olan ve düşük düzey boş bit konumları sıfır, aşağıdaki örnekte gösterildiği gibi ayarlar yüksek sıra bitleri atar:

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

Kaydırma işleçleri yalnızca tanımlandığından `int`, `uint`, `long`, ve `ulong` türlerini, her zaman bir işlemin sonucunu içeren en az 32 bit. Sol işlenen başka bir integral türü ise (`sbyte`, `byte`, `short`, `ushort`, veya `char`), değeri dönüştürülür `int` türü, aşağıdaki örnekte gösterildiği gibi:

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Hakkında bilgi için sağ işleneni `<<` işleci tanımlar kaydırma sayısı, bkz: [kaydırma işleçlerinin sayısı](#shift-count-of-the-shift-operators) bölümü.

## <a name="right-shift-operator-"></a>Sağa kaydırma işleci >>

`>>` İşleci kaydırır sol işleneniyle sağ tarafından sağ işlenen tarafından tanımlanan bit sayısı.

Sağa kaydırma işlemi aşağıdaki örnekte gösterildiği gibi alt sıra bitleri atar:

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

Yüksek düzeyli boş bit konumları sol işlenenin türü üzerinde aşağıdaki gibi temel ayarlanır:

- Sol işlenen türü ise [int](../builtin-types/integral-numeric-types.md) veya [uzun](../builtin-types/integral-numeric-types.md), sağa kaydırma işleci gerçekleştiren bir *aritmetik* shift: en anlamlı biti (imza biti) değeri sol işlenen, yüksek sıralı boş bit konumlarına yayılır. Diğer bir deyişle, sol işlenen negatif ise yüksek düzeyli boş bit konumları sıfır olarak ayarlanır ve negatif ise birine ayarlayın.

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Sol işlenen türü ise [uint](../builtin-types/integral-numeric-types.md) veya [ulong](../builtin-types/integral-numeric-types.md), sağa kaydırma işleci gerçekleştiren bir *mantıksal* shift: yüksek düzeyli boş bit konumları her zaman sıfır olarak ayarlayın.

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Hakkında bilgi için sağ işleneni `>>` işleci tanımlar kaydırma sayısı, bkz: [kaydırma işleçlerinin sayısı](#shift-count-of-the-shift-operators) bölümü.

## <a name="logical-and-operator-"></a> Mantıksal AND işleci &amp;

`&` Kendi işlenenden bit seviyesinde mantıksal ve işlecini hesaplar:

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

İşlenen için `bool` türü `&` işleci hesaplar [mantıksal AND](boolean-logical-operators.md#logical-and-operator-) işlenenleri. Birli `&` işleci [address-of işleci](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Mantıksal Dışlayıcı veya işlecini ^

`^` İşleci hesaplar. bit düzeyinde mantıksal özel veya olarak da bilinen kendi işlenenden bit seviyesinde mantıksal XOR:

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

İşlenen için `bool` türü `^` işleci hesaplar [mantıksal XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) işlenenleri.

## <a name="logical-or-operator-"></a>Mantıksal OR işlecinin |

`|` Kendi işlenenden bit seviyesinde mantıksal veya işlecini hesaplar:

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

İşlenen için `bool` türü `|` işleci hesaplar [mantıksal OR](boolean-logical-operators.md#logical-or-operator-) işlenenleri.

## <a name="compound-assignment"></a>Bileşik atama

İkili işleç için `op`, formun bir bileşik atama ifadesi

```csharp
x op= y
```

eşdeğerdir

```csharp
x = x op y
```

dışında `x` yalnızca bir kez değerlendirilir.

Aşağıdaki örnek, kaydırma işleçleri ve bileşik atama ile bit kullanımını göstermektedir:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Nedeniyle [sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions), sonucunu `op` işlemi olabilir değil türe örtük olarak dönüştürülebilir `T` , `x`. Böyle bir durumda ise `op` önceden tanımlanmış bir işleç ve işlemin sonucu türüne açıkça dönüştürülebilir ise `T` , `x`, formun bir bileşik atama ifadesi `x op= y` eşdeğerdir `x = (T)(x op y)`, dışında `x` yalnızca bir kez değerlendirilir. Aşağıdaki örnek, bu davranış gösterir:

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste siparişleri bit düzeyinde ve en yüksek öncelikten en düşük başlangıç kaydırma işleçleri:

- Bit düzeyinde tamamlama işleci `~`
- Kaydırma işleçleri `<<` ve `>>`
- Mantıksal AND işleci `&`
- Özel mantıksal OR işleci `^`
- Mantıksal OR işleci `|`

Parantez kullanın `()`İşleç önceliği tarafından belirlenen değerlendirmenin sırasını değiştirmek için:

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).

## <a name="shift-count-of-the-shift-operators"></a>Kaydırma işleçleri kaydırma sayısı

Kaydırma işleçleri için `<<` ve `>>`, sağ işlenenin türünde olmalıdır [int](../builtin-types/integral-numeric-types.md) veya olan bir türü bir [örtülü sayısal dönüştürme önceden tanımlanmış](../keywords/implicit-numeric-conversions-table.md) için `int`.

İçin `x << count` ve `x >> count` ifadeleri, gerçek kaydırma sayısı türüne bağlıdır `x` gibi:

- Varsa türünü `x` olduğu [int](../builtin-types/integral-numeric-types.md) veya [uint](../builtin-types/integral-numeric-types.md), kaydırma sayısı düşük düzey tarafından tanımlanan *beş* sağ işlenenin bit. Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x1F` (veya `count & 0b_1_1111`).

- Varsa türünü `x` olduğu [uzun](../builtin-types/integral-numeric-types.md) veya [ulong](../builtin-types/integral-numeric-types.md), kaydırma sayısı düşük düzey tarafından tanımlanan *altı* sağ işlenenin bit. Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x3F` (veya `count & 0b_11_1111`).

Aşağıdaki örnek, bu davranış gösterir:

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a>Mantıksal işleçler numaralandırması

`~`, `&`, `|`, Ve `^` işleçleri de tanımlanır için [numaralandırma](../keywords/enum.md) türü. İşlenenler aynı numaralandırma türü için bir mantıksal işlemi temel tamsayı türüne karşılık gelen değerleri üzerinde gerçekleştirilir. Örneğin, tüm `x` ve `y` bir numaralandırma türünün `T` bir temel türü ile `U`, `x & y` ifade aynı sonucu üretir `(T)((U)x & (U)y)` ifade.

İle tanımlanmış bir numaralandırma türü ile mantıksal bit düzeyinde işleçler kullanın [bayrakları](xref:System.FlagsAttribute) özniteliği. Daha fazla bilgi için [bit bayrakları olarak numaralandırma türleri](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) bölümünü [Numaralandırma türleri](../../programming-guide/enumeration-types.md) makalesi.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür için [aşırı](operator-overloading.md) `~`, `<<`, `>>`, `&`, `|`, ve `^` işleçleri. İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş. Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.

Kullanıcı tanımlı bir tür ederse `T` aşırı `<<` veya `>>` işleci sol işlenenin türü olmalıdır `T` ve sağ işleneninin türü olmalıdır `int`.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):

- [Bit düzeyinde tamamlama işleci](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Kaydırma işleçleri](~/_csharplang/spec/expressions.md#shift-operators)
- [Mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)
- [Sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [Boolean mantıksal işleçler](boolean-logical-operators.md)
