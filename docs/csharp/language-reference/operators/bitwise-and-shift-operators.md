---
title: Bit düzeyinde and Shift işleçleri-C# başvurusu
description: İntegral türlerindeki işlenenleri olan bit düzeyinde mantıksal veya SHIFT işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- <<=_CSharpKeyword
- '>>=_CSharpKeyword'
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
ms.openlocfilehash: 99181855fdf8e937676e44e8b347510f9405aa3d
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916906"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Bit düzeyinde and Shift işleçleri (C# Başvurusu)

Aşağıdaki işleçler [integral sayısal türlerin](../builtin-types/integral-numeric-types.md) veya [char](../builtin-types/char.md) türünün işlenenleri ile bit düzeyinde veya SHIFT işlemleri gerçekleştirir:

- Birli [ `~` (bit düzeyinde tamamlama)](#bitwise-complement-operator-) işleci
- İkili [ `<<` (sol SHIFT)](#left-shift-operator-) ve [ `>>` (sağ SHIFT)](#right-shift-operator-) kaydırma işleçleri
- İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal or)](#logical-or-operator-)ve [ `^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler

Bu işleçler,,, `int` `uint` `long` ve türleri için tanımlanır `ulong` . Her iki işlenen de diğer integral türlerinde ( `sbyte` , `byte` ,, `short` `ushort` veya `char` ) olduğunda, değerleri `int` bir işlemin sonuç türü olan türüne dönüştürülür. İşlenenler farklı integral türlerindiğinde, değerleri, en yakın integral türüne dönüştürülür. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions) bölümüne bakın.

`&`, `|` Ve `^` işleçleri tür işlenenleri için de tanımlanmıştır `bool` . Daha fazla bilgi için bkz. [Boolean mantıksal işleçler](boolean-logical-operators.md).

Bit düzeyinde ve kaydırma işlemleri hiçbir şekilde taşmaya neden olmaz ve [denetlenen ve işaretlenmeyen](../keywords/checked-and-unchecked.md) bağlamlarda aynı sonuçları üretir.

## <a name="bitwise-complement-operator-"></a>Bit düzeyinde tamamlama işleci ~

`~`İşleci her bir biti ters çevirerek işleneni bir bit düzeyinde tamamlayıcı üretir:

[!code-csharp-interactive[bitwise NOT](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseComplement)]

`~`Sonlandırıcıları bildirmek için sembolünü de kullanabilirsiniz. Daha fazla bilgi için bkz. [sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Sola kaydırma işleci\<\<

`<<`İşleci sol taraftaki işlenenini [sağ işleneni tarafından tanımlanan bit sayısına](#shift-count-of-the-shift-operators)göre sola kaydırır.

Aşağıdaki örnekte gösterildiği gibi, sol SHIFT işlemi, sonuç türü aralığının dışındaki yüksek sıralı bitleri atar ve düşük sıralı boş bit konumlarını sıfıra ayarlar:

[!code-csharp-interactive[left shift](snippets/shared/BitwiseAndShiftOperators.cs#LeftShift)]

SHIFT işleçleri yalnızca,, ve türleri için tanımlandığından `int` , `uint` `long` `ulong` bir işlemin sonucu her zaman en az 32 bit içerir. Sol işlenen başka bir integral türü ( `sbyte` , `byte` ,, `short` `ushort` , veya `char` ) ise, `int` Aşağıdaki örnekte gösterildiği gibi, değeri türüne dönüştürülür:

[!code-csharp-interactive[left shift with promotion](snippets/shared/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

İşlecin sağ işleneninin kaydırma sayısını tanımladığı hakkında daha fazla bilgi için `<<` [SHIFT Operators bölümünün kaydırma](#shift-count-of-the-shift-operators) sayısını inceleyin.

## <a name="right-shift-operator-"></a>Sağa kaydırma işleci >>

`>>`İşleci, sol işlenenin [sağ işleneni tarafından tanımlanan bit sayısına](#shift-count-of-the-shift-operators)göre sağa kayar.

Aşağıdaki örnekte gösterildiği gibi, doğru kaydırma işlemi düşük sıralı bitleri atar:

[!code-csharp-interactive[right shift](snippets/shared/BitwiseAndShiftOperators.cs#RightShift)]

Yüksek sıralı boş bit konumları, sol taraftaki işlenenin türüne göre aşağıdaki gibi ayarlanır:

- Sol işlenen türü `int` veya ise `long` , sağ SHIFT işleci bir *Aritmetik* kaydırma gerçekleştirir: sol işlenenin en önemli bit (işaret biti) değeri, yüksek sıralı boş bit konumlarına yayılır. Diğer bir deyişle, sol işlenen negatif olmayan ve negatifse bir tane olarak ayarlandıysa, yüksek sıralı boş bit konumları sıfır olarak ayarlanır.

  [!code-csharp-interactive[arithmetic right shift](snippets/shared/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Sol işlenen veya türünde ise `uint` `ulong` , sağ SHIFT işleci bir *mantıksal* kaydırma gerçekleştirir: yüksek sıralı boş bit konumları her zaman sıfır olarak ayarlanır.

  [!code-csharp-interactive[logical right shift](snippets/shared/BitwiseAndShiftOperators.cs#LogicalRightShift)]

İşlecin sağ işleneninin kaydırma sayısını tanımladığı hakkında daha fazla bilgi için `>>` [SHIFT Operators bölümünün kaydırma](#shift-count-of-the-shift-operators) sayısını inceleyin.

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a>Mantıksal AND işleci&amp;

`&`İşleci, işlenenlerinin bit düzeyinde MANTıKSAL ve işlecini hesaplar:

[!code-csharp-interactive[bitwise AND](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseAnd)]

`bool`İşlenenler için işleç, `&` işlenenlerinin [mantıksal ve](boolean-logical-operators.md#logical-and-operator-) işlecini hesaplar. Birli `&` işleç [Adres işleçtir](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Mantıksal dışlamalı OR işleci ^

`^`İşleci, işlenenlerinin bit düzeyinde MANTıKSAL XOR değeri olarak da bilinen bit düzeyinde mantıksal dışlamalı veya hesaplar:

[!code-csharp-interactive[bitwise XOR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseXor)]

`bool`İşlenenler için işleç, `^` işlenenlerinin [MANTıKSAL dışlamalı veya](boolean-logical-operators.md#logical-exclusive-or-operator-) ' ı hesaplar.

## <a name="logical-or-operator-"></a>Mantıksal OR işleci |

`|`İşleci, işlenenlerinin bit düzeyinde MANTıKSAL veya işlecini hesaplar:

[!code-csharp-interactive[bitwise OR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseOr)]

`bool`İşlenenler için işleç, `|` işlenenlerinin [mantıksal veya](boolean-logical-operators.md#logical-or-operator-) işlecini hesaplar.

## <a name="compound-assignment"></a>Bileşik atama

Bir ikili işleci için `op` , formun bileşik atama ifadesi

```csharp
x op= y
```

eşdeğerdir

```csharp
x = x op y
```

hariç `x` yalnızca bir kez değerlendirilir.

Aşağıdaki örnek, bileşik atamanın bit düzeyinde ve kaydırma işleçleriyle kullanımını gösterir:

[!code-csharp-interactive[compound assignment](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignment)]

[Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle, `op` işlemin sonucu örtük olarak türüne dönüştürülebilir olmayabilir `T` `x` . Böyle bir durumda, `op` önceden tanımlanmış bir işleçse ve işlemin sonucu türüne açıkça dönüştürülebilir ise, `T` `x` formun bileşik atama ifadesi `x op= y` öğesine eşdeğerdir `x = (T)(x op y)` , ancak `x` yalnızca bir kez değerlendirilir. Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp-interactive[compound assignment with cast](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, en yüksek öncelikten en düşüğe başlayarak bit düzeyinde ve kaydırma işleçlerini sıralar:

- Bit düzeyinde tamamlama işleci`~`
- SHIFT işleçleri `<<` ve`>>`
- Mantıksal AND işleci`&`
- Mantıksal dışlamalı OR işleci`^`
- Mantıksal OR işleci`|`

`()`İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantezleri kullanın:

[!code-csharp-interactive[operator precedence](snippets/shared/BitwiseAndShiftOperators.cs#Precedence)]

Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için [c# işleçleri](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="shift-count-of-the-shift-operators"></a>Kaydırma işleçlerinin kaydırma sayısı

SHIFT işleçleri ve için `<<` `>>` sağ işlenen türü `int` veya [önceden tanımlanmış örtük sayısal dönüştürmeye](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) sahip bir tür olmalıdır `int` .

`x << count`Ve ifadeleri için `x >> count` , gerçek kaydırma sayısı `x` aşağıdaki şekilde türüne bağlıdır:

- Türü `x` `int` veya ise `uint` , kaydırma sayısı sağ işlenenin düşük sıralı *beş* biti tarafından tanımlanır. Diğer bir deyişle, kaydırma sayısı `count & 0x1F` (veya) öğesinden hesaplanır `count & 0b_1_1111` .

- Türü `x` `long` veya ise `ulong` , kaydırma sayısı sağ işlenenin alt-sırası *altı* bitsiyle tanımlanır. Diğer bir deyişle, kaydırma sayısı `count & 0x3F` (veya) öğesinden hesaplanır `count & 0b_11_1111` .

Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp-interactive[shift count example](snippets/shared/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> Yukarıdaki örnekte gösterildiği gibi, sağ işlenenin değeri sol işlenendeki bit sayısından büyük olsa da, bir vardiya işleminin sonucu sıfır olmayan bir değer olabilir.

## <a name="enumeration-logical-operators"></a>Sabit listesi mantıksal işleçleri

`~`,, `&` `|` Ve `^` işleçleri her bir [numaralandırma](../builtin-types/enum.md) türü tarafından da desteklenir. Aynı numaralandırma türünün işlenenleri için, temel alınan integral türünün karşılık gelen değerlerinde bir mantıksal işlem gerçekleştirilir. Örneğin, `x` `y` temel alınan bir tür ve bir numaralandırma türü için `T` ifade, `U` `x & y` ifadesiyle aynı sonucu üretir `(T)((U)x & (U)y)` .

Genellikle, [Flags](xref:System.FlagsAttribute) özniteliğiyle tanımlanan bir numaralandırma türü ile bit düzeyinde mantıksal işleçler kullanırsınız. Daha fazla bilgi için [Listeleme türleri](../builtin-types/enum.md) makalesinin [numaralandırma türleri bit bayrakları](../builtin-types/enum.md#enumeration-types-as-bit-flags) bölümüne bakın.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür,, [overload](operator-overloading.md) ,, `~` , `<<` `>>` `&` `|` ve `^` işleçlerini aşırı yükleyebilir. İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.

Kullanıcı tanımlı bir tür `T` `<<` veya işlecini aşırı `>>` yükletir, sol taraftaki işlenenin türü olmalıdır `T` ve sağ işlenen türü olmalıdır `int` .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Bit düzeyinde tamamlama işleci](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Kaydırma işleçleri](~/_csharplang/spec/expressions.md#shift-operators)
- [Mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)
- [Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Boole mantıksal işleçleri](boolean-logical-operators.md)
