---
title: Bit yönünden ve kaydırma işleçleri - C# referansı
description: İntegral türlerinin operands ile bitwise mantıksal veya shift işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 54198368672e0c9324210a232c7851b5a90402cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399268"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Bit yönünde ve kaydırma işleçleri (C# referansı)

Aşağıdaki işleçler, [integral sayısal türlerin intiyazları](../builtin-types/integral-numeric-types.md) veya [char](../builtin-types/char.md) türüyle bityönünde veya kaydırma işlemleri gerçekleştirir:

- Unary [ `~` (bitwise kompleman)](#bitwise-complement-operator-) işleci
- İkili [ `<<` (sol kaydırma)](#left-shift-operator-) ve [ `>>` (sağ kaydırma)](#right-shift-operator-) kaydırma işleçleri
- İkili [ `&` (mantıksal AND)](#logical-and-operator-), [ `|` (mantıksal OR)](#logical-or-operator-)ve [ `^` (mantıksal özel OR)](#logical-exclusive-or-operator-) işleçleri

Bu işleçler `int`, `uint` `long`, `ulong` , ve türleri için tanımlanır. Her iki operands diğer integral`sbyte` `byte`türleri `short` `ushort`(, `char`, , , , `int` veya ), değerleri de bir işlemin sonucu türüdür, dönüştürülür. Operandlar farklı integral türlerine sahip olduklarında, değerleri en yakın integral türüne dönüştürülür. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions) bölümüne bakın.

`&`, `|`ve `^` işleçler de `bool` türünün operands için tanımlanır. Daha fazla bilgi için [Boolean mantıksal işleçleri'ne](boolean-logical-operators.md)bakın.

Bitwise ve shift işlemleri hiçbir zaman taşma neden ve [denetlenmiş ve işaretlenmemiş](../keywords/checked-and-unchecked.md) bağlamlarda aynı sonuçları üretmek.

## <a name="bitwise-complement-operator-"></a>Bitwise kompleman operatörü ~

Operatör, `~` her biti tersine çevirerek operand'ın biraz daha tamamlayıcısını üretir:

[!code-csharp-interactive[bitwise NOT](snippets/BitwiseAndShiftOperators.cs#BitwiseComplement)]

`~` Ayrıca sonlandırıcıları bildirmek için sembolü kullanabilirsiniz. Daha fazla bilgi için [Finalizers'a](../../programming-guide/classes-and-structs/destructors.md)bakın.

## <a name="left-shift-operator-"></a>Sol kaydırma işleci\<\<

Operatör `<<` sol operand soldaki [operand'ı sağ operand'ı ile tanımlanan bit sayısına](#shift-count-of-the-shift-operators)göre kaydırır.

Sol kaydırma işlemi, sonuç türünün aralığının dışında kalan yüksek sıralı bitleri atar ve aşağıdaki örnekte görüldüğü gibi düşük sıralı boş bit konumlarını sıfıra ayarlar:

[!code-csharp-interactive[left shift](snippets/BitwiseAndShiftOperators.cs#LeftShift)]

Vardiya işleçleri `int`yalnızca , `uint`, `long`, `ulong` ve türleri için tanımlandıklarından, bir işlemin sonucu her zaman en az 32 bit içerir. Sol operand başka bir integral türüne`sbyte` `byte`aitse ( , `short`, , `ushort`, veya `char`, değeri aşağıdaki örnekte görüldüğü gibi, `int` türe dönüştürülür:

[!code-csharp-interactive[left shift with promotion](snippets/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Operatörün `<<` sağ operand'ının vardiya sayısını nasıl tanımladığı hakkında bilgi [için, vardiya işleçleri bölümünün Shift sayısına](#shift-count-of-the-shift-operators) bakın.

## <a name="right-shift-operator-"></a>Sağ vites operatörü >>

Operatör, `>>` sol operand'ı [sağ operand'ı tanımlayan bit sayısına](#shift-count-of-the-shift-operators)göre kaydırır.

Sağ kaydırma işlemi, aşağıdaki örnekte görüldüğü gibi, düşük sıralı bitleri atar:

[!code-csharp-interactive[right shift](snippets/BitwiseAndShiftOperators.cs#RightShift)]

Yüksek sıralı boş bit konumları sol operand'ın türüne göre ayarlanır ve aşağıdaki gibi:

- Sol operand türündeyse `int` veya `long`sağ kaydırma işleci *aritmetik* bir kayma gerçekleştiriyorsa: sol operand'ın en önemli bitinin (işaret biti) değeri yüksek sıralı boş bit pozisyonlarına yayılır. Diğer bir süre, sol operand negatif değilse, yüksek sıralı boş bit konumları sıfıra ayarlanır ve negatifse bire ayarlanır.

  [!code-csharp-interactive[arithmetic right shift](snippets/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Sol operand türündeyse `uint` veya `ulong`sağ kaydırma işleci *mantıksal* bir kayma gerçekleştiriyorsa: yüksek sıralı boş bit konumları her zaman sıfıra ayarlanır.

  [!code-csharp-interactive[logical right shift](snippets/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Operatörün `>>` sağ operand'ının vardiya sayısını nasıl tanımladığı hakkında bilgi [için, vardiya işleçleri bölümünün Shift sayısına](#shift-count-of-the-shift-operators) bakın.

## <a name="logical-and-operator-"></a>Mantıksal VE işleç&amp;

İşletici, `&` bitwise mantıksal VE onun operands hesaplar:

[!code-csharp-interactive[bitwise AND](snippets/BitwiseAndShiftOperators.cs#BitwiseAnd)]

Operands `bool` için, `&` operatör mantıksal [VE](boolean-logical-operators.md#logical-and-operator-) onun operands hesaplar. Unary `&` [işleci, işlecin adresidir.](pointer-related-operators.md#address-of-operator-)

## <a name="logical-exclusive-or-operator-"></a>Mantıksal özel OR operatörü ^

İşletici, `^` bitwise mantıksal XOR olarak da bilinen bitwise mantıksal özel OR'unu operands'ını hesaplar:

[!code-csharp-interactive[bitwise XOR](snippets/BitwiseAndShiftOperators.cs#BitwiseXor)]

Operands `bool` için, `^` operatör onun operands [mantıksal özel OR](boolean-logical-operators.md#logical-exclusive-or-operator-) bilgisayar.

## <a name="logical-or-operator-"></a>Mantıksal OR işleci |

İşletici, `|` operandlarının bitwise mantıksal VEYA'sini hesaplar:

[!code-csharp-interactive[bitwise OR](snippets/BitwiseAndShiftOperators.cs#BitwiseOr)]

Operands `bool` için, `|` operatör onun operands [mantıksal OR](boolean-logical-operators.md#logical-or-operator-) bilgisayar.

## <a name="compound-assignment"></a>Bileşik atama

Bir ikili `op`işleç için, formun bileşik atama ifadesi

```csharp
x op= y
```

eşdeğerdir

```csharp
x = x op y
```

`x` bunun dışında sadece bir kez değerlendirilir.

Aşağıdaki örnek, bitwise ve shift işleçleri ile bileşik atama kullanımını gösterir:

[!code-csharp-interactive[compound assignment](snippets/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Sayısal [promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle, `op` işlemin sonucu dolaylı olarak türüne `T` dönüştürülebilir `x`olmayabilir. Böyle bir durumda, `op` önceden tanımlanmış bir işleç ise ve işlemin sonucu açıkça `T` `x`türüne dönüştürülebilir ise `x op= y` , formun bileşik atama ifadesi eşdeğerdir `x = (T)(x op y)`, sadece bir kez değerlendirilir dışında. `x` Aşağıdaki örnek, davranışı gösterir:

[!code-csharp-interactive[compound assignment with cast](snippets/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, en yüksek öncelikten en düşüke başlayarak bit yönünde ve kaydırma işleçlerini siparişleri verir:

- Bitwise kompleman operatörü`~`
- Shift `<<` operatörleri ve`>>`
- Mantıksal VE işleç`&`
- Mantıksal özel OR işleci`^`
- Mantıksal VEYA işleci`|`

Operatör önceliği tarafından `()`dayatılan değerlendirme sırasını değiştirmek için parantez kullanın:

[!code-csharp-interactive[operator precedence](snippets/BitwiseAndShiftOperators.cs#Precedence)]

Öncelik düzeyine göre sıralanan C# işleçlerinin tam listesi için [C# işleçleri](index.md) makalesinin [Operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="shift-count-of-the-shift-operators"></a>Vardiya operatörlerinin vardiya sayısı

Shift `<<` operatörleri ve `>>`, sağ operand türü veya `int` önceden tanımlanmış bir [örtülü sayısal dönüşüm](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) olan `int`bir tür olmalıdır.

Ve ifadeler için, gerçek kaydırma sayısı aşağıdaki gibi `x` türüne bağlıdır: `x >> count` `x << count`

- Eğer `x` türü `int` veya `uint`, vardiya sayısı sağ operand düşük sıralı *beş* bit tarafından tanımlanır. Diğer bir şey, vardiya sayısı `count & 0x1F` (veya) `count & 0b_1_1111`adresinden hesaplanır.

- Eğer `x` türü `long` veya `ulong`, vardiya sayısı sağ operand düşük sıralı *altı* bit tarafından tanımlanır. Diğer bir şey, vardiya sayısı `count & 0x3F` (veya) `count & 0b_11_1111`adresinden hesaplanır.

Aşağıdaki örnek, davranışı gösterir:

[!code-csharp-interactive[shift count example](snippets/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> Yukarıdaki örnekte de görüldüğü gibi, sağ operand değeri sol operandbit sayısından fazla olsa bile, bir kaydırma işleminin sonucu sıfır sızabilir.

## <a name="enumeration-logical-operators"></a>Numaralandırma mantıksal işleçleri

, `~` `&`, `|`, `^` ve operatörler de herhangi bir [numaralandırma](../builtin-types/enum.md) türü tarafından desteklenir. Aynı numaralandırma türündeki operandlar için, altta yatan integral türünün karşılık gelen değerleri üzerinde mantıksal bir işlem gerçekleştirilir. Örneğin, altta `x` yatan `y` türü `T` `U`olan herhangi bir numaralandırma türü `x & y` için ifade, `(T)((U)x & (U)y)` ifadeyle aynı sonucu üretir.

Genellikle [Bayraklar](xref:System.FlagsAttribute) özniteliği ile tanımlanan bir numaralandırma türü ile bitwise mantıksal işleçleri kullanın. Daha fazla bilgi için, Numaralandırma türleri makalesinin bit bayrakları bölümü [olarak Numaralandırma](../builtin-types/enum.md#enumeration-types-as-bit-flags) [türlerine](../builtin-types/enum.md) bakın.

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir `~`tür, `<<`, `>>` `&`, `|`, `^` , ve işleçleri [aşırı yükleyebilir.](operator-overloading.md) Bir ikili işleci aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenir. Kullanıcı tanımlı bir tür, bileşik atama işlecinin aşırı yüklenemeyeceğini açıkça ifade eder.

Kullanıcı tanımlı bir `T` tür `<<` veya `>>` işleci aşırı yüklerse, sol operand'ın türü ve `T` sağ operand'ın türü olmalıdır. `int`

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Bitwise kompleman operatörü](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Kaydırma işleçleri](~/_csharplang/spec/expressions.md#shift-operators)
- [Mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)
- [Sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Boole mantıksal işleçleri](boolean-logical-operators.md)
