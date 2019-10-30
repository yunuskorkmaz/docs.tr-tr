---
title: Aritmetik işleçler- C# başvuru
description: Sayısal türlerle C# çarpma, bölme, geri kalan, toplama ve çıkarma işlemleri gerçekleştiren işleçler hakkında bilgi edinin.
ms.date: 03/27/2019
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
ms.openlocfilehash: ca2513a0f865fd7da728f7d3247bdb7b50a2f48a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036421"
---
# <a name="arithmetic-operators-c-reference"></a>Aritmetik işleçler (C# başvuru)

Aşağıdaki işleçler, sayısal türlerde işlenenler ile aritmetik işlemler gerçekleştirir:

- Birli [`++` (artış)](#increment-operator-), [`--` (azaltma)](#decrement-operator---), [`+` (artı)](#unary-plus-and-minus-operators)ve [`-` (eksi)](#unary-plus-and-minus-operators) işleçleri
- İkili [`*` (çarpma)](#multiplication-operator-), [`/` (bölme)](#division-operator-), [`%` (kalan)](#remainder-operator-), [`+` (toplama)](#addition-operator-)ve [`-` (çıkarma)](#subtraction-operator--) işleçleri

Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.

## <a name="increment-operator-"></a>Artış işleci + +

Birli artış işleci `++` işlenenini 1 artırır. İşlenen bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) erişimi olmalıdır.

Artırma işleci iki biçimde desteklenir: sonek artırma işleci, `x++` ve önek artışı işleci, `++x`.

### <a name="postfix-increment-operator"></a>Sonek artırma işleci

Aşağıdaki örnekte gösterildiği gibi, `x++` sonucu işlemden *önce* `x` değeridir:

[!code-csharp-interactive[postfix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Ön ek artırma işleci

Aşağıdaki örnekte gösterildiği gibi, `++x` sonucu işlemden *sonra* `x` değeridir:

[!code-csharp-interactive[prefix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Azaltma işleci--

Birli azaltma işleci `--` işlenenini 1 azaltır. İşlenen bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) erişimi olmalıdır.

Azaltma işleci iki formda desteklenir: sonek azaltma işleci, `x--` ve ön ek azaltma işleci, `--x`.

### <a name="postfix-decrement-operator"></a>Sonek azaltma işleci

Aşağıdaki örnekte gösterildiği gibi, `x--` sonucu işlemden *önce* `x` değeridir:

[!code-csharp-interactive[postfix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Önek azaltma işleci

Aşağıdaki örnekte gösterildiği gibi, `--x` sonucu işlemden *sonra* `x` değeridir:

[!code-csharp-interactive[prefix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Birli artı ve eksi işleçleri

Birli `+` işleci, işleneninin değerini döndürür. Birli `-` işleci, işleneninin sayısal olumsuzunu hesaplar.

[!code-csharp-interactive[unary plus and minus](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

[Ulong](../builtin-types/integral-numeric-types.md) türü birli `-` işlecini desteklemez.

## <a name="multiplication-operator-"></a>Çarpma işleci *

Çarpma işleci `*` işlenenlerinin çarpımını hesaplar:

[!code-csharp-interactive[multiplication operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

Birli `*` işleci, [işaretçi yöneltme işleçtir](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Bölme işleci/

Bölme işleci `/` sol tarafından sağ işleneniyle böler.

### <a name="integer-division"></a>Tamsayı bölme

Tamsayı türlerinin işlenenleri için, `/` işlecinin sonucu bir tamsayı türüdür ve iki işlenenlerin sıfıra yuvarlayarak Bu bölüm eşittir:

[!code-csharp-interactive[integer division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

İki işlenenin bir kayan noktalı sayı olarak bölümünü almak için `float`, `double` veya `decimal` türünü kullanın:

[!code-csharp-interactive[integer as floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Kayan nokta bölme

`float`, `double`ve `decimal` türlerinde, `/` işlecinin sonucu iki işlenenin bir bölümü olur:

[!code-csharp-interactive[floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

İşlenenlerden biri `decimal`, başka bir işlenen `float` veya `double` olamaz, çünkü hiçbir `float` veya `double` örtük olarak `decimal` dönüştürülebilir. `float` veya `double` işlenenini `decimal` türüne açıkça dönüştürmeniz gerekir. Sayısal türler arasındaki dönüşümler hakkında daha fazla bilgi için bkz. [yerleşik sayısal dönüşümler](../builtin-types/numeric-conversions.md).

## <a name="remainder-operator-"></a>Kalan işleç yüzdesi

Geri kalan işleç `%` sol taraftaki işleneni sağ tarafıyla ayırarak kalanı hesaplar.

### <a name="integer-remainder"></a>Tamsayı geri kalanı

Tamsayı türlerinin işlenenleri için `a % b` sonucu, `a - (a / b) * b`tarafından oluşturulan değerdir. Sıfır olmayan geri kalanın işareti, aşağıdaki örnekte gösterildiği gibi, sol taraftaki işleneniyle aynıdır:

[!code-csharp-interactive[integer remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

Hem tamsayı bölme hem de kalan sonuçları hesaplamak için <xref:System.Math.DivRem%2A?displayProperty=nameWithType> yöntemini kullanın.

### <a name="floating-point-remainder"></a>Kayan nokta kalanı

`float` ve `double` işlenenleri için `x % y` sonucu sınırlı `x` ve `y` için `z` değer

- Sıfır olmayan `z` işareti, `x` işaretiyle aynıdır.
- `z` mutlak değeri, `n` `|x| / |y|` ve `|x|` sıfırdan küçük veya buna eşit olan en büyük olası tamsayıdır ve `|y|` `x` ve `y`değerlerinin mutlak değerleri olduğundan, `|x| - n * |y|` tarafından oluşturulan değerdir. anı.

> [!NOTE]
> Bu geri kalanı hesaplama yöntemi, tamsayı işlenenleri için kullanılan, ancak IEEE 754 belirtiminden farklı olacak şekilde benzerdir. IEEE 754 belirtimine uyan geri kalan işleme ihtiyacınız varsa <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemini kullanın.

`%` işlecinin sonlu olmayan işlenenlerle davranışı hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [geri kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümüne bakın.

`decimal` işlenenleri için, `%` kalan işleç <xref:System.Decimal?displayProperty=nameWithType> türünün [kalan işlecine](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) eşdeğerdir.

Aşağıdaki örnek, kayan nokta işlenenleri geri kalan işlecinin davranışını gösterir:

[!code-csharp-interactive[floating-point remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Toplama işleci +

Toplama işleci `+` işlenenlerinin toplamını hesaplar:

[!code-csharp-interactive[addition operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

Dize birleştirme ve temsilci birleşimi için `+` işlecini de kullanabilirsiniz. Daha fazla bilgi için [`+` ve `+=` İşletmenleri](addition-operator.md) makalesine bakın.

## <a name="subtraction-operator--"></a>Çıkarma işleci-

Çıkarma işleci `-` sağ işlenenini sol tarafından çıkartır:

[!code-csharp-interactive[subtraction operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

Temsilci kaldırma için `-` işlecini de kullanabilirsiniz. Daha fazla bilgi için [`-` ve `-=` İşletmenleri](subtraction-operator.md) makalesine bakın.

## <a name="compound-assignment"></a>Bileşik atama

Bir ikili işleci için `op`, formun bileşik atama ifadesi

```csharp
x op= y
```

eşdeğerdir

```csharp
x = x op y
```

`x` yalnızca bir kez değerlendirilir.

Aşağıdaki örnek, aritmetik bir atama kullanımını Aritmetik işleçlerle gösterir:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

[Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle `op` işleminin sonucu `x` `T` türüne örtülü olarak dönüştürülebilir olmayabilir. Böyle bir durumda, `op` önceden tanımlanmış bir işleçse ve işlemin sonucu `x` `T` türüne açıkça dönüştürülesiyse, formun bileşik atama ifadesi `x op= y` eşdeğerdir `x = (T)(x op y)` `x` hariç, yalnızca bir kez değerlendirilir. Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Ayrıca, sırasıyla bir [olaya](../keywords/event.md)abone olmak ve aboneliği kaldırmak için `+=` ve `-=` işleçlerini da kullanırsınız. Daha fazla bilgi için bkz. [nasıl yapılır: olaylara abone olma ve aboneliği kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-precedence-and-associativity"></a>İşleç önceliği ve ilişkilendirilebilirlik

Aşağıdaki liste, en yüksek öncelikten en düşüğe başlayarak aritmetik işleçleri sıralar:

- Sonek artırma `x++` ve azaltma `x--` işleçleri
- Önek artırma `++x` ve azaltma `--x` ve birli `+` ve `-` işleçleri
- Çarpma `*`, `/`ve `%` işleçleri
- Adli `+` ve `-` işleçleri

İkili aritmetik işleçler sola ilişkilendirilebilir. Diğer bir deyişle, aynı öncelik düzeyine sahip işleçler soldan sağa değerlendirilir.

İşleç önceliği ve ilişkilendirilebilirliği tarafından uygulanan değerlendirmenin sırasını değiştirmek için parantez, `()` kullanın.

[!code-csharp-interactive[precedence and associativity](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için, [ C# işleçler](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="arithmetic-overflow-and-division-by-zero"></a>Aritmetik taşma ve sıfıra bölme

Bir aritmetik işlemin sonucu, ilgili sayısal türün olası sonlu değerler aralığının dışında olduğunda, bir aritmetik işlecin davranışı işlenenlerinin türüne bağlıdır.

### <a name="integer-arithmetic-overflow"></a>Tamsayı aritmetik taşması

Sayı sıfıra bölme her zaman bir <xref:System.DivideByZeroException> oluşturur.

Tamsayı aritmetik taşması olması durumunda, [denetlenen veya işaretlenmemiş](../keywords/checked-and-unchecked.md)bir taşma Denetim bağlamı ortaya çıkan davranışı denetler:

- Denetlenen bir bağlamda, sabit bir ifadede taşma gerçekleşirse, derleme zamanı hatası oluşur. Aksi takdirde, işlem çalışma zamanında gerçekleştirildiğinde bir <xref:System.OverflowException> oluşturulur.
- İşaretlenmemiş bir bağlamda, sonuç, hedef türüne sığmayan yüksek sıralı bitleri atarak kesilir.

[Checked ve unchecked](../keywords/checked-and-unchecked.md) deyimlerinin yanı sıra, bir ifadenin değerlendirildiği taşma denetimi bağlamını denetlemek için `checked` ve `unchecked` işleçlerini kullanabilirsiniz:

[!code-csharp-interactive[checked and unchecked](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

Varsayılan olarak, aritmetik işlemler *işaretlenmemiş* bir bağlamda oluşur.

### <a name="floating-point-arithmetic-overflow"></a>Kayan nokta aritmetik taşması

`float` ve `double` türleriyle aritmetik işlemler hiçbir şekilde özel durum oluşturmaz. Bu türlere sahip aritmetik işlemlerin sonucu, sonsuz ve bir sayı olmayan özel değerlerden biri olabilir:

[!code-csharp-interactive[double non-finite values](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

`decimal` türünün işlenenleri için aritmetik taşma her zaman bir <xref:System.OverflowException> oluşturur ve sıfıra bölme her zaman bir <xref:System.DivideByZeroException>oluşturur.

## <a name="round-off-errors"></a>Yuvarlama hataları

Gerçek sayıların ve kayan nokta aritmetiğinin kayan nokta gösteriminin genel sınırlamaları nedeniyle, kayan nokta türleriyle hesaplamalar halinde yuvarlama hataları oluşabilir. Diğer bir deyişle, bir ifadenin üretilen sonucu beklenen matematik sonucundan farklı olur. Aşağıdaki örnekte bu gibi birkaç durum gösterilmektedir:

[!code-csharp-interactive[round-off errors](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

Daha fazla bilgi için bkz. [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)veya [System. Decimal](/dotnet/api/system.decimal#remarks) başvuru sayfalarındaki açıklamalar.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür birli (`++`, `--`, `+`ve `-`) ve ikili (`*`, `/`, `%`, `+`ve `-`) aritmetik operatörlerini [aşırı](operator-overloading.md) yükleyebilir. İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Sonek artırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Ön ek artırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Birli Plus işleci](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Birli eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Çarpma işleci](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Bölme işleci](~/_csharplang/spec/expressions.md#division-operator)
- [Kalan işleç](~/_csharplang/spec/expressions.md#remainder-operator)
- [Toplama işleci](~/_csharplang/spec/expressions.md#addition-operator)
- [Çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)
- [Checked ve unchecked işleçleri](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
