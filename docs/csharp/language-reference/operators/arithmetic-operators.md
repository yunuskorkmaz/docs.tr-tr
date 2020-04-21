---
title: Aritmetik işleçler - C# referansı
description: Sayısal türleri ile çarpma, bölme, geri kama, ekleme ve çıkarma işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: ea9bf9e065b2953fd20e0503a19d1dc143064c5d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738740"
---
# <a name="arithmetic-operators-c-reference"></a>Aritmetik işleçler (C# referansı)

Aşağıdaki işleçler sayısal tiplerin operands ile aritmetik işlemleri gerçekleştirmek:

- Unary [ `++` (artış)](#increment-operator-), [ `--` (kararname)](#decrement-operator---), [ `+` (artı)](#unary-plus-and-minus-operators)ve [ `-` (eksi)](#unary-plus-and-minus-operators) işleçleri
- İkili [ `*` (çarpma)](#multiplication-operator-), [ `/` (bölme)](#division-operator-), [ `%` (kalan)](#remainder-operator-), [ `+` (toplama)](#addition-operator-)ve [ `-` (çıkarma) işleçleri](#subtraction-operator--)

Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.

## <a name="increment-operator-"></a>Artış işleci ++

Unary artış işleci `++` operand 1 oranında artışlar. Operand bir değişken, bir [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya bir [dizinleyici](../../programming-guide/indexers/index.md) erişimi olmalıdır.

Artış işleci iki şekilde desteklenir: postfix artış işleci `x++`ve önek artış işleci, `++x`.

### <a name="postfix-increment-operator"></a>Sonek artırma işleci

Aşağıdaki örnekte görüldüğü gibi, işlemin `x++` `x` *önceki* değerinin sonucu:

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Önek artış işleci

Aşağıdaki örnekte görüldüğü `x` gibi, işlem den *sonraki* değerin sonucudur: `++x`

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Kararname işleci --

Unary kararname işleci `--` operand'ı 1 oranında azat eder. Operand bir değişken, bir [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya bir [dizinleyici](../../programming-guide/indexers/index.md) erişimi olmalıdır.

Decrement işleci iki şekilde desteklenir: postfix decrement işleci, `x--`ve önek `--x`decrement işleci, .

### <a name="postfix-decrement-operator"></a>Sonek azaltma işleci

Aşağıdaki örnekte görüldüğü gibi, işlemin `x--` `x` *önceki* değerinin sonucu:

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Önek giderme işleci

Aşağıdaki örnekte görüldüğü `x` gibi, işlem den *sonraki* değerin sonucudur: `--x`

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Unary artı ve eksi işleçleri

Unary `+` işleci, operand değerini döndürür. Unary `-` işleci, operand'ının sayısal olumsuzluğunu hesaplar.

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

[Ulong](../builtin-types/integral-numeric-types.md) türü unary `-` işleci desteklemez.

## <a name="multiplication-operator-"></a>Çarpma işleci *

Çarpma işleci, `*` operandlarının ürününü hesaplar:

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

Unary `*` işleci [işaretçi indirection işlecidir.](pointer-related-operators.md#pointer-indirection-operator-)

## <a name="division-operator-"></a>Bölme operatörü /

Bölme işleci `/` sol operand'ını sağ operand'a böler.

### <a name="integer-division"></a>Sonsayı bölümü

İnteger türlerinin operandları için, işlecinin `/` sonucu bir hemşeri türüdür ve sıfıra doğru yuvarlatılmış iki operandun katibine eşittir:

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

Kayan nokta sayısı olarak iki operands'ın katsayısını elde `float` `double`etmek `decimal` için , veya türü kullanın:

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Kayan nokta bölümü

`float`, , `double`ve `decimal` türleri için, `/` işleç sonucu iki operands bölüm:

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

Eğer operands biri `decimal`ise , başka bir `float` operand ne ne de `double`olabilir , çünkü ne ne de `float` `double` örtülü olarak dönüştürülebilir `decimal`. Açıkça `float` `double` `decimal` veya operand türüne dönüştürmek gerekir. Sayısal türler arasındaki dönüşümler hakkında daha fazla bilgi için yerleşik [sayısal dönüşümler'e](../builtin-types/numeric-conversions.md)bakın.

## <a name="remainder-operator-"></a>Kalan işleç %

Kalan işleç, `%` sol operand'ı sağ operand'a böldükten sonra geri kalanını hesaplar.

### <a name="integer-remainder"></a>İnteger geri kalanı

İnteger türlerinin operands için, `a % b` sonucu tarafından `a - (a / b) * b`üretilen değerdir. Sıfır olmayan geri kalan işareti, aşağıdaki örnekte görüldüğü gibi, sol operand ile aynıdır:

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

Hem <xref:System.Math.DivRem%2A?displayProperty=nameWithType> tamsayı bölümünü hem de kalan sonuçları hesaplamak için yöntemi kullanın.

### <a name="floating-point-remainder"></a>Kayan nokta geri kalanı

`float` Ve `double` operands `x % y` için, sonlu `x` için sonucu `y` ve `z` değeri böyle

- "Sıfır `z`değilse" işareti, `x`" işaretiyle aynıdır.
- Mutlak `z` değeri, `|x| - n * |y|` mümkün `n` olan en büyük tamsayı olan ve sırasıyla mutlak `|x| / |y|` `|x|` değerleri `|y|` olan ve `x` mutlak `y`değerler olan değerdir.

> [!NOTE]
> Bu hesaplama yöntemi, tamsayı operands için kullanılan, ancak IEEE 754 belirtimi farklı benzer. IEEE 754 belirtimine uygun kalan operasyona ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemi kullanın.

`%` Sonlu olmayan operands ile işlecinin davranışı hakkında bilgi için [C# dil belirtimiNin](~/_csharplang/spec/introduction.md) [Kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümüne bakın.

`decimal` Operands için, kalan `%` işleç <xref:System.Decimal?displayProperty=nameWithType> türünün kalan [işleci](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) eşdeğerdir.

Aşağıdaki örnek, kalan işleç kayan nokta operands ile davranışını gösterir:

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>İlave işleci +

Ek işleci, `+` operandlarının toplamını hesaplar:

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

Dize `+` birleşimi ve temsilci birleşimi için işleci de kullanabilirsiniz. Daha fazla bilgi için, ve [ `+` `+=` operatörler](addition-operator.md) makaleye bakın.

## <a name="subtraction-operator--"></a>Çıkarma operatörü -

Çıkarma işleci `-` sağ operand'ını sol operand'ından çıkarır:

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

`-` Temsilci kaldırma için işleci de kullanabilirsiniz. Daha fazla bilgi için, ve [ `-` `-=` operatörler](subtraction-operator.md) makaleye bakın.

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

Aşağıdaki örnek, bileşik atamanın aritmetik işleçlerle kullanımını göstermektedir:

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

Sayısal [promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle, `op` işlemin sonucu dolaylı olarak türüne `T` dönüştürülebilir `x`olmayabilir. Böyle bir durumda, `op` önceden tanımlanmış bir işleç ise ve işlemin sonucu açıkça `T` `x`türüne dönüştürülebilir ise `x op= y` , formun bileşik atama ifadesi eşdeğerdir `x = (T)(x op y)`, sadece bir kez değerlendirilir dışında. `x` Aşağıdaki örnek, davranışı gösterir:

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Ayrıca, sırasıyla `-=` bir [olaya](../keywords/event.md)abone olmak ve aboneliğinizi iptal etmek için `+=` ve işleçleri de kullanırsınız. Daha fazla bilgi için [olaylara nasıl abone olunur ve bu etkinliklerden aboneliğinizi iptal edebilirsiniz.](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

## <a name="operator-precedence-and-associativity"></a>Operatör önceliği ve bağlantı

Aşağıdaki liste, en yüksek öncelikten en düşükbaştan başlayarak aritmetik işleçleri sıralar:

- Düzeltme artış `x++` ve decrement `x--` işleçleri
- Önek `++x` artış ve `--x` decrement ve `+` `-` unary ve operatörler
- Çarpan , `*` `/`ve `%` işleçler
- Katkı `+` `-` maddesi ve operatörler

İkili aritmetik işleçler sol-bağdaştırıcıdır. Diğer bir diğer olarak, aynı öncelik düzeyine sahip işleçler soldan sağa değerlendirilir.

Operatör önceliği ve `()`bağlantısı tarafından dayatılan değerlendirme sırasını değiştirmek için parantez kullanın.

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Öncelik düzeyine göre sıralanan C# işleçlerinin tam listesi için [C# işleçleri](index.md) makalesinin [Operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="arithmetic-overflow-and-division-by-zero"></a>Aritmetik taşma ve sıfır ile bölme

Bir aritmetik işlemin sonucu ilgili sayısal türün olası sonlu değerleri aralığının dışında olduğunda, aritmetik işleç davranışı operands türüne bağlıdır.

### <a name="integer-arithmetic-overflow"></a>Tamsayı aritmetik taşma

Sıfır ile Tamsayı bölümü her <xref:System.DivideByZeroException>zaman bir atar .

Tamsayı aritmetik taşma durumunda, [denetlenebilir veya işaretlenmemiş](../keywords/checked-and-unchecked.md)bir taşma denetimi bağlamı, ortaya çıkan davranışı denetler:

- Denetlenen bir bağlamda, taşma sabit bir ifadede gerçekleşirse, derleme zamanı hatası oluşur. Aksi takdirde, işlem çalışma zamanında gerçekleştirildiğinde, bir atılır. <xref:System.OverflowException>
- Denetlenmemiş bir bağlamda, sonuç hedef türüne sığmayacak yüksek sıralı bitler atılarak kesilir.

[Denetlenen ve işaretlenmemiş](../keywords/checked-and-unchecked.md) ifadelerile birlikte, bir `checked` `unchecked` ifadenin değerlendirildiği taşma denetimi bağlamını denetlemek için ve işleçleri kullanabilirsiniz:

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

Varsayılan olarak, aritmetik işlemler *denetlenmemiş* bir bağlamda oluşur.

### <a name="floating-point-arithmetic-overflow"></a>Kayan nokta aritmetik taşma

Ve `float` `double` türleri ile aritmetik işlemler asla bir özel durum atmak. Bu türlerle yapılan aritmetik işlemlerin sonucu, sonsuzluğu ve sayı yı temsil etmeyen özel değerlerden biri olabilir:

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

`decimal` Türünün operands için, aritmetik taşma her <xref:System.OverflowException> zaman sıfır bir ve <xref:System.DivideByZeroException>bölünme atar her zaman bir .

## <a name="round-off-errors"></a>Yuvarlama hataları

Reel sayıların kayan nokta gösteriminin genel sınırlamaları ve kayan nokta aritmetik nedeniyle, kayan nokta türleri ile hesaplamalarda yuvarlama hataları oluşabilir. Diğer bir ifadenin üretilen sonucu beklenen matematiksel sonuçtan farklı olabilir. Aşağıdaki örnek, bu gibi birkaç örneği göstermektedir:

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

Daha fazla bilgi için [System.Double,](/dotnet/api/system.double#remarks) [System.Single](/dotnet/api/system.single#remarks)veya [System.Ondalık](/dotnet/api/system.decimal#remarks) başvuru sayfalarındaki açıklamalara bakın.

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür, unary`++` `--` `+`(, `-`, ,`*`ve `/` `%`) `+`ve `-`ikili ( , , , , ve ) aritmetik işleçleri [aşırı yükleyebilir.](operator-overloading.md) Bir ikili işleci aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenir. Kullanıcı tanımlı bir tür, bileşik atama işlecinin aşırı yüklenemeyeceğini açıkça ifade eder.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Düzeltme artış ve decrement işleçleri](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Önek artış ve decrement işleçleri](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Tekli artı işleci](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Unary eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Çarpma işleci](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Bölme operatörü](~/_csharplang/spec/expressions.md#division-operator)
- [Kalan işleç](~/_csharplang/spec/expressions.md#remainder-operator)
- [İlave işleci](~/_csharplang/spec/expressions.md#addition-operator)
- [Çıkarma operatörü](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)
- [Denetlenen ve işaretlenmemiş işleçler](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
