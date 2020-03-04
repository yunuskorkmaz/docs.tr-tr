---
title: Bit düzeyinde and Shift işleçleri C# -başvuru
description: İntegral türlerindeki C# işlenenleri olan bit düzeyinde mantıksal veya SHIFT işlemleri gerçekleştiren işleçler hakkında bilgi edinin.
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
ms.openlocfilehash: a6319cbbbe8a691f5d2a01a13a5abfa2550b3705
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239527"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Bit düzeyinde ve kaydırma işleçleriC# (başvuru)

Aşağıdaki işleçler [integral sayısal türlerin](../builtin-types/integral-numeric-types.md) veya [char](../builtin-types/char.md) türünün işlenenleri ile bit düzeyinde veya SHIFT işlemleri gerçekleştirir:

- Birli [`~` (bit düzeyinde tamamlama)](#bitwise-complement-operator-) işleci
- İkili [`<<` (sol SHIFT)](#left-shift-operator-) ve [`>>` (Sağ Shift)](#right-shift-operator-) kaydırma işleçleri
- İkili [`&` (MANTıKSAL ve)](#logical-and-operator-), [`|` (mantıksal or)](#logical-or-operator-)ve [`^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler

Bu işleçler `int`, `uint`, `long`ve `ulong` türleri için tanımlanmıştır. Her iki işlenen de diğer integral türlerindiğinde (`sbyte`, `byte`, `short`, `ushort`veya `char`), değerleri bir işlemin sonuç türü olan `int` türüne dönüştürülür. İşlenenler farklı integral türlerindiğinde, değerleri, en yakın integral türüne dönüştürülür. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions) bölümüne bakın.

`&`, `|`ve `^` işleçleri Ayrıca `bool` türünün işlenenleri için de tanımlanmıştır. Daha fazla bilgi için bkz. [Boolean mantıksal işleçler](boolean-logical-operators.md).

Bit düzeyinde ve kaydırma işlemleri hiçbir şekilde taşmaya neden olmaz ve [denetlenen ve işaretlenmeyen](../keywords/checked-and-unchecked.md) bağlamlarda aynı sonuçları üretir.

## <a name="bitwise-complement-operator-"></a>Bit düzeyinde tamamlama işleci ~

`~` işleci, her biti ters çevirerek işleneni bir bit düzeyinde tamamlayıcı üretir:

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Sonlandırıcıları bildirmek için `~` sembolünü de kullanabilirsiniz. Daha fazla bilgi için bkz. [sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Sola kaydırma işleci \<\<

`<<` işleci sol taraftaki işlenenini [sağ işleneni tarafından tanımlanan bit sayısına](#shift-count-of-the-shift-operators)göre sola kaydırır.

Aşağıdaki örnekte gösterildiği gibi, sol SHIFT işlemi, sonuç türü aralığının dışındaki yüksek sıralı bitleri atar ve düşük sıralı boş bit konumlarını sıfıra ayarlar:

[!code-csharp-interactive[left shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

SHIFT işleçleri yalnızca `int`, `uint`, `long`ve `ulong` türleri için tanımlandığından, bir işlemin sonucu her zaman en az 32 bit içerir. Sol işlenen başka bir integral türü (`sbyte`, `byte`, `short`, `ushort`veya `char`) ise, aşağıdaki örnekte gösterildiği gibi, değeri `int` türüne dönüştürülür:

[!code-csharp-interactive[left shift with promotion](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

`<<` işlecinin sağ işleneninin kaydırma sayısını tanımladığı hakkında daha fazla bilgi için [SHIFT Operators bölümünün kaydırma sayısına](#shift-count-of-the-shift-operators) bakın.

## <a name="right-shift-operator-"></a>Sağa kaydırma işleci > >

`>>` işleci, sol işlenenin [sağ işleneni tarafından tanımlanan bit sayısına](#shift-count-of-the-shift-operators)göre sağa kayar.

Aşağıdaki örnekte gösterildiği gibi, doğru kaydırma işlemi düşük sıralı bitleri atar:

[!code-csharp-interactive[right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

Yüksek sıralı boş bit konumları, sol taraftaki işlenenin türüne göre aşağıdaki gibi ayarlanır:

- Sol işlenen `int` veya `long`türünde ise, sağ SHIFT işleci bir *Aritmetik* kaydırma gerçekleştirir: sol işlenenin en önemli bit (işaret biti) değeri, yüksek sıralı boş bit konumlarına yayılır. Diğer bir deyişle, sol işlenen negatif olmayan ve negatifse bir tane olarak ayarlandıysa, yüksek sıralı boş bit konumları sıfır olarak ayarlanır.

  [!code-csharp-interactive[arithmetic right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Sol işlenen `uint` veya `ulong`türünde ise, sağ SHIFT işleci bir *mantıksal* kaydırma gerçekleştirir: yüksek sıralı boş bit konumları her zaman sıfır olarak ayarlanır.

  [!code-csharp-interactive[logical right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

`>>` işlecinin sağ işleneninin kaydırma sayısını tanımladığı hakkında daha fazla bilgi için [SHIFT Operators bölümünün kaydırma sayısına](#shift-count-of-the-shift-operators) bakın.

## <a name="logical-and-operator-"></a>Mantıksal AND işleci &amp;

`&` işleci, işlenenlerinin bit düzeyinde mantıksal ve işlecini hesaplar:

[!code-csharp-interactive[bitwise AND](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

`bool` işlenenleri için `&` işleci, işlenenlerinin [MANTıKSAL ve](boolean-logical-operators.md#logical-and-operator-) işlecini hesaplar. Birli `&` işleci, [Adres işleçtir](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Mantıksal dışlamalı OR işleci ^

`^` işleci, işlenenlerinin bit düzeyinde mantıksal XOR değeri olarak da bilinen bit düzeyinde mantıksal dışlamalı veya bir şekilde hesaplar:

[!code-csharp-interactive[bitwise XOR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

`bool` işlenenleri için `^` işleci, işlenenlerinin [mantıksal dışlamalı veya](boolean-logical-operators.md#logical-exclusive-or-operator-) bir listesini hesaplar.

## <a name="logical-or-operator-"></a>Mantıksal OR işleci |

`|` işleci, işlenenlerinin bit düzeyinde mantıksal veya işlecini hesaplar:

[!code-csharp-interactive[bitwise OR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

`bool` işlenenleri için `|` işleci, işlenenlerinin [MANTıKSAL veya](boolean-logical-operators.md#logical-or-operator-) işlecini hesaplar.

## <a name="compound-assignment"></a>Bileşik atama

Bir ikili işleç `op`için, formun bileşik atama ifadesi

```csharp
x op= y
```

eşdeğerdir

```csharp
x = x op y
```

`x` hariç, yalnızca bir kez değerlendirilir.

Aşağıdaki örnek, bileşik atamanın bit düzeyinde ve kaydırma işleçleriyle kullanımını gösterir:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

[Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle `op` işleminin sonucu `x``T` türüne örtülü olarak dönüştürülebilir olmayabilir. Böyle bir durumda, `op` önceden tanımlanmış bir işleçse ve işlemin sonucu `x``T` türüne açıkça dönüştürülesiyse, `x = (T)(x op y)`yalnızca bir kez değerlendirilmemesi dışında, form `x op= y` bir bileşik atama ifadesi `x` değerine eşdeğerdir. Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, en yüksek öncelikten en düşüğe başlayarak bit düzeyinde ve kaydırma işleçlerini sıralar:

- Bit düzeyinde tamamlama işleci `~`
- SHIFT işleçleri `<<` ve `>>`
- Mantıksal AND işleci `&`
- Mantıksal dışlamalı OR işleci `^`
- Mantıksal OR işleci `|`

İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantez, `()`kullanın:

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için, [ C# işleçler](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="shift-count-of-the-shift-operators"></a>Kaydırma işleçlerinin kaydırma sayısı

`<<` ve `>>`kaydırma işleçleri için sağ işlenen türü, `int`için [önceden tanımlanmış bir örtülü sayısal dönüştürmeye](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) sahip `int` veya bir tür olmalıdır.

`x << count` ve `x >> count` ifadelerinde, gerçek kaydırma sayısı `x` türüne aşağıdaki gibi bağlıdır:

- `x` türü `int` veya `uint`ise, kaydırma sayısı sağ işlenenin düşük sıralı *beş* biti tarafından tanımlanır. Diğer bir deyişle, kaydırma sayısı `count & 0x1F` (veya `count & 0b_1_1111`) olarak hesaplanır.

- `x` türü `long` veya `ulong`ise, kaydırma sayısı sağ işlenenin alt-sırası *altı* bitsiyle tanımlanır. Diğer bir deyişle, kaydırma sayısı `count & 0x3F` (veya `count & 0b_11_1111`) olarak hesaplanır.

Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> Yukarıdaki örnekte gösterildiği gibi, sağ işlenenin değeri sol işlenendeki bit sayısından büyük olsa da, bir vardiya işleminin sonucu sıfır olmayan bir değer olabilir.

## <a name="enumeration-logical-operators"></a>Sabit listesi mantıksal işleçleri

`~`, `&`, `|`ve `^` işleçleri her bir [numaralandırma](../builtin-types/enum.md) türü tarafından da desteklenir. Aynı numaralandırma türünün işlenenleri için, temel alınan integral türünün karşılık gelen değerlerinde bir mantıksal işlem gerçekleştirilir. Örneğin, herhangi bir `x` ve `y` bir numaralandırma türü `T` temel alınan bir tür `U`için, `x & y` ifadesi `(T)((U)x & (U)y)` ifadesiyle aynı sonucu üretir.

Genellikle, [Flags](xref:System.FlagsAttribute) özniteliğiyle tanımlanan bir numaralandırma türü ile bit düzeyinde mantıksal işleçler kullanırsınız. Daha fazla bilgi için [Listeleme türleri](../builtin-types/enum.md) makalesinin [numaralandırma türleri bit bayrakları](../builtin-types/enum.md#enumeration-types-as-bit-flags) bölümüne bakın.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür `~`, `<<`, `>>`, `&`, `|`ve `^` işleçlerini [aşırı](operator-overloading.md) yükleyebilir. İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.

Kullanıcı tanımlı bir tür `T` `<<` veya `>>` işlecini aşırı yükletir, sol taraftaki işlenenin türü `T` olmalı ve sağ işlenen türü `int`olmalıdır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Bit düzeyinde tamamlama işleci](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Kaydırma işleçleri](~/_csharplang/spec/expressions.md#shift-operators)
- [Mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)
- [Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Boole mantıksal işleçler](boolean-logical-operators.md)
