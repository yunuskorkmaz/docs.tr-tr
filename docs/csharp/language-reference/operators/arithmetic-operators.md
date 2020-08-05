---
title: Aritmetik işleçler-C# başvurusu
description: Sayısal türlerle çarpma, bölme, geri kalan, toplama ve çıkarma işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: 03bf7f246884fc8cd0095f0dd1375389a95e1ef0
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555480"
---
# <a name="arithmetic-operators-c-reference"></a>Aritmetik işleçler (C# Başvurusu)

Aşağıdaki işleçler, sayısal türlerde işlenenler ile aritmetik işlemler gerçekleştirir:

- Birli [ `++` (artış)](#increment-operator-), [ `--` (azaltma)](#decrement-operator---), [ `+` (artı)](#unary-plus-and-minus-operators)ve [ `-` (eksi)](#unary-plus-and-minus-operators) işleçler
- İkili [ `*` (çarpma)](#multiplication-operator-), [ `/` (bölme)](#division-operator-), [ `%` (geri kalan)](#remainder-operator-), [ `+` (toplama)](#addition-operator-)ve [ `-` (çıkarma)](#subtraction-operator--) işleçleri

Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.

İntegral türleri söz konusu olduğunda, bu işleçler ( `++` ve `--` işleçleri hariç),,, `int` `uint` `long` ve türleri için tanımlanır `ulong` . İşlenenler diğer integral türlerinde ( `sbyte` , `byte` , `short` , `ushort` , veya `char` ) olduğunda, değerleri `int` bir işlemin sonuç türü olan türüne dönüştürülür. İşlenenler farklı integral veya kayan nokta türleri olduğunda, bu tür varsa, değerleri en yakın türe dönüştürülür. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions) bölümüne bakın. `++`Ve `--` işleçleri tüm integral ve kayan nokta sayısal türleri ve [char](../builtin-types/char.md) türü için tanımlanır.

## <a name="increment-operator-"></a>Artış işleci + +

Birli artış işleci, `++` işleneni 1 artırır. İşlenen bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) erişimi olmalıdır.

Artırma işleci iki biçimde desteklenir: Sonek artışı işleci, `x++` ve önek artışı işleci, `++x` .

### <a name="postfix-increment-operator"></a>Sonek artırma işleci

Sonucu, `x++` `x` Aşağıdaki örnekte gösterildiği gibi, işlemden *önceki* değeridir:

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Ön ek artırma işleci

Sonucu, `++x` `x` Aşağıdaki örnekte gösterildiği gibi, işlemden *sonraki* değerdir:

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Azaltma işleci--

Birli azaltma işleci, `--` işleneninin 1 değerini azaltır. İşlenen bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) erişimi olmalıdır.

Azaltma işleci iki formda desteklenir: sonek azaltma işleci, `x--` ve önek azaltma işleci, `--x` .

### <a name="postfix-decrement-operator"></a>Sonek azaltma işleci

Sonucu, `x--` `x` Aşağıdaki örnekte gösterildiği gibi, işlemden *önceki* değeridir:

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Önek azaltma işleci

Sonucu, `--x` `x` Aşağıdaki örnekte gösterildiği gibi, işlemden *sonraki* değerdir:

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Birli artı ve eksi işleçleri

Birli `+` işleç, işleneninin değerini döndürür. Birli `-` işleç, işleneninin sayısal olumsuzunu hesaplar.

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

[Ulong](../builtin-types/integral-numeric-types.md) türü birli `-` işleci desteklemiyor.

## <a name="multiplication-operator-"></a>Çarpma işleci *

Çarpma işleci, `*` işlenenlerinin çarpımını hesaplar:

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

Birli `*` işleç, [işaretçi yöneltme işleçtir](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Bölme işleci/

Bölme işleci, `/` sol işlenenini sağ işleneniyle böler.

### <a name="integer-division"></a>Tamsayı bölme

Tamsayı türlerinin işlenenleri için, `/` işlecin sonucu bir tamsayı türüdür ve iki işlenenlerin sıfıra yuvarlayarak sonuna eşittir:

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

İki işlenenin bir kayan noktalı sayı olarak bölümünü almak için, `float` `double` veya `decimal` türünü kullanın:

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Kayan nokta bölme

`float`, `double` , Ve türleri için `decimal` `/` işlecinin sonucu iki işlenenin bir bölümü olur:

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

İşlenenlerden biri ise başka bir işlenen ne de, ne de `decimal` `float` örtük olarak `double` `float` `double` dönüştürülememiş olabilir `decimal` . Ya da işleneni açıkça türüne dönüştürmeniz gerekir `float` `double` `decimal` . Sayısal türler arasındaki dönüşümler hakkında daha fazla bilgi için bkz. [yerleşik sayısal dönüşümler](../builtin-types/numeric-conversions.md).

## <a name="remainder-operator-"></a>Kalan işleç yüzdesi

Kalan işleç, `%` sol işlenenin sağ işleneniyle bölündükten sonra kalanı hesaplar.

### <a name="integer-remainder"></a>Tamsayı geri kalanı

Tamsayı türlerinin işlenenleri için, sonucu `a % b` tarafından üretilen değerdir `a - (a / b) * b` . Sıfır olmayan geri kalanın işareti, aşağıdaki örnekte gösterildiği gibi, sol taraftaki işleneniyle aynıdır:

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<xref:System.Math.DivRem%2A?displayProperty=nameWithType>Hem tamsayı bölme hem de kalan sonuçları hesaplamak için yöntemini kullanın.

### <a name="floating-point-remainder"></a>Kayan nokta kalanı

`float`Ve işlenenleri için `double` , `x % y` sonsuz `x` `y` değeri `z` için sonuç olarak

- `z`Sıfır olmayan, işareti, işaretiyle aynıdır `x` .
- Öğesinin mutlak değeri, `z` tarafından üretilen `|x| - n * |y|` `n` en büyük olası tamsayı, ve `|x| / |y|` `|x|` `|y|` ' nin mutlak değerleri `x` sırasıyla ve `y` ' den daha az olan sayıdır.

> [!NOTE]
> Bu geri kalanı hesaplama yöntemi, tamsayı işlenenleri için kullanılan, ancak IEEE 754 belirtiminden farklı olacak şekilde benzerdir. IEEE 754 belirtimine uyan geri kalan işleme ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemini kullanın.

İşlecinin sınırlı olmayan işlenenlerle davranışı hakkında daha fazla bilgi için `%` [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [kalan işleç](~/_csharplang/spec/expressions.md#remainder-operator) bölümüne bakın.

İşlenenler için `decimal` , kalan işleç `%` türün [geri kalan işlecine](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) eşdeğerdir <xref:System.Decimal?displayProperty=nameWithType> .

Aşağıdaki örnek, kayan nokta işlenenleri geri kalan işlecinin davranışını gösterir:

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Toplama işleci +

Toplama işleci, `+` işlenenlerinin toplamını hesaplar:

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

Ayrıca, `+` dize birleştirme ve temsilci birleşimi için işlecini de kullanabilirsiniz. Daha fazla bilgi için, [ `+` ve `+=` işleçleri](addition-operator.md) makalesine bakın.

## <a name="subtraction-operator--"></a>Çıkarma işleci-

Çıkarma işleci, `-` sağ işlenenini sol tarafından çıkartır:

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

`-`Temsilci kaldırma için işlecini de kullanabilirsiniz. Daha fazla bilgi için, [ `-` ve `-=` işleçleri](subtraction-operator.md) makalesine bakın.

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

Aşağıdaki örnek, aritmetik bir atama kullanımını Aritmetik işleçlerle gösterir:

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

[Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle, `op` işlemin sonucu örtük olarak türüne dönüştürülebilir olmayabilir `T` `x` . Böyle bir durumda, `op` önceden tanımlanmış bir işleçse ve işlemin sonucu türüne açıkça dönüştürülebilir ise, `T` `x` formun bileşik atama ifadesi `x op= y` öğesine eşdeğerdir `x = (T)(x op y)` , ancak `x` yalnızca bir kez değerlendirilir. Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Ayrıca, `+=` `-=` sırasıyla bir olaya abone olmak ve bu [olaydan](../keywords/event.md)abonelik kaldırmak için ve işleçlerini kullanın. Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-precedence-and-associativity"></a>İşleç önceliği ve ilişkilendirilebilirlik

Aşağıdaki liste, en yüksek öncelikten en düşüğe başlayarak aritmetik işleçleri sıralar:

- Sonek artırma `x++` ve azaltma `x--` işleçleri
- Ön ek artırma `++x` ve azaltma `--x` ve birli `+` ve `-` işleçler
- Çoğultıcı `*` , `/` , ve `%` işleçler
- Eklenebilir `+` ve `-` işleçler

İkili aritmetik işleçler sola ilişkilendirilebilir. Diğer bir deyişle, aynı öncelik düzeyine sahip işleçler soldan sağa değerlendirilir.

`()`İşleç önceliği ve ilişkilendirilebilirliği tarafından uygulanan değerlendirmenin sırasını değiştirmek için parantezleri kullanın.

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için [c# işleçleri](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="arithmetic-overflow-and-division-by-zero"></a>Aritmetik taşma ve sıfıra bölme

Bir aritmetik işlemin sonucu, ilgili sayısal türün olası sonlu değerler aralığının dışında olduğunda, bir aritmetik işlecin davranışı işlenenlerinin türüne bağlıdır.

### <a name="integer-arithmetic-overflow"></a>Tamsayı aritmetik taşması

Sıfıra göre tam sayı bölümü her zaman bir oluşturur <xref:System.DivideByZeroException> .

Tamsayı aritmetik taşması olması durumunda, [denetlenen veya işaretlenmemiş](../keywords/checked-and-unchecked.md)bir taşma Denetim bağlamı ortaya çıkan davranışı denetler:

- Denetlenen bir bağlamda, sabit bir ifadede taşma gerçekleşirse, derleme zamanı hatası oluşur. Aksi takdirde, işlem çalışma zamanında gerçekleştirildiğinde bir oluşturulur <xref:System.OverflowException> .
- İşaretlenmemiş bir bağlamda, sonuç, hedef türüne sığmayan yüksek sıralı bitleri atarak kesilir.

[Checked ve unchecked](../keywords/checked-and-unchecked.md) deyimlerinin yanı sıra, `checked` `unchecked` bir ifadenin değerlendirildiği taşma denetimi bağlamını denetlemek için ve işleçlerini kullanabilirsiniz:

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

Varsayılan olarak, aritmetik işlemler *işaretlenmemiş* bir bağlamda oluşur.

### <a name="floating-point-arithmetic-overflow"></a>Kayan nokta aritmetik taşması

Ve türleri ile aritmetik `float` İşlemler `double` hiçbir şekilde özel durum oluşturmaz. Bu türlere sahip aritmetik işlemlerin sonucu, sonsuz ve bir sayı olmayan özel değerlerden biri olabilir:

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

Türün işlenenleri için `decimal` , aritmetik taşma her zaman <xref:System.OverflowException> sıfır tarafından bir ve bölme her zaman bir oluşturur <xref:System.DivideByZeroException> .

## <a name="round-off-errors"></a>Yuvarlama hataları

Gerçek sayıların ve kayan nokta aritmetiğinin kayan nokta gösteriminin genel sınırlamaları nedeniyle, kayan nokta türleriyle hesaplamalar halinde yuvarlama hataları oluşabilir. Diğer bir deyişle, bir ifadenin üretilen sonucu beklenen matematik sonucundan farklı olur. Aşağıdaki örnekte bu gibi birkaç durum gösterilmektedir:

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

Daha fazla bilgi için bkz. [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)veya [System. Decimal](/dotnet/api/system.decimal#remarks) başvuru sayfalarındaki açıklamalar.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür birli ( [overload](operator-overloading.md) `++` ,, `--` `+` , ve `-` ) ve ikili (,,, `*` `/` `%` `+` ve `-` ) aritmetik operatörlerini aşırı yükleyebilir. İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Sonek artırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Önek arttırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Birli artı işleci](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Birli eksi işareti](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Çarpma işleci](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Bölme işleci](~/_csharplang/spec/expressions.md#division-operator)
- [Kalan işleç](~/_csharplang/spec/expressions.md#remainder-operator)
- [Toplama işleci](~/_csharplang/spec/expressions.md#addition-operator)
- [Çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)
- [Checked ve unchecked işleçleri](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
