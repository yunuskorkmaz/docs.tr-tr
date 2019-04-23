---
title: Aritmetik işleçler - C# başvurusu
description: Hakkında bilgi edinin C# sayısal türlerle çarpma, bölme, kalan, toplama ve çıkarma işlemleri gerçekleştiren işleçleri.
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
ms.openlocfilehash: dc817fdb9684f794efc6599444e80be1ef7f9654
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978048"
---
# <a name="arithmetic-operators-c-reference"></a>Aritmetik işleçler (C# Başvurusu)

Aşağıdaki işleçleri ile sayısal türleri aritmetik işlemleri gerçekleştirin:

- Birli [ `++` (artırma)](#increment-operator-), [ `--` (azaltma)](#decrement-operator---), [ `+` (artı)](#unary-plus-and-minus-operators), ve [ `-` (eksi)](#unary-plus-and-minus-operators) işleçleri
- İkili [ `*` (çarpma)](#multiplication-operator-), [ `/` (bölme)](#division-operator-), [ `%` (kalanını)](#remainder-operator-), [ `+` () ek olarak)](#addition-operator-), ve [ `-` (çıkarma)](#subtraction-operator--) işleçleri

Tüm bu işleçleri destekler [integral](../keywords/integral-types-table.md) ve [kayan nokta](../keywords/floating-point-types-table.md) sayısal türler.

## <a name="increment-operator-"></a>Artış işleci ++

Tekli artırma işleci `++` işleneniyle 1 artar. İşlenen, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.

Artırım işleci iki biçimde desteklenir: sonek artırma işlecini `x++`ve önek artırma işleci `++x`.

### <a name="postfix-increment-operator"></a>Sonek artırma işleci

Sonucu `x++` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Önek artırma işleci

Sonucu `++x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Azaltma işleci--

Birli azaltma işleci `--` azaltır işleneniyle 1. İşlenen, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.

Azaltma işleci iki biçimde desteklenir: sonek azaltma işlecinin `x--`ve önek azaltma işleci `--x`.

### <a name="postfix-decrement-operator"></a>Sonek azaltma işleci

Sonucu `x--` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Önek azaltma işleci

Sonucu `--x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Birli artı ve eksi işleçleri

Birli `+` işleci, işlenenin değerini döndürür. Birli `-` işleci, işlenenin sayısal olumsuzlama hesaplar.

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Birli `-` işleci desteklemez [ulong](../keywords/ulong.md) türü.

## <a name="multiplication-operator-"></a>Çarpma işleci *

Çarpma işleci `*` işlenenleri çarpımını hesaplar:

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

Birli `*` işleci [işaretçi yöneltme işleci](multiplication-operator.md#pointer-indirection-operator).

## <a name="division-operator-"></a>Bölme işleci /

Bölme işleci `/` ilk işlenenin ikinci işleneni olarak böler.

### <a name="integer-division"></a>Tamsayı bölme

Tamsayı türleri sonucunu işlenenleri için `/` işleci bir tamsayı türüdür ve sayının yuvarlanmış sıfır iki işlenenden eşittir:

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

İki işlenenden bölümü bir kayan noktalı sayı olarak almak için kullanın `float`, `double`, veya `decimal` türü:

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Kayan nokta bölme

İçin `float`, `double`, ve `decimal` türleri, sonucunu `/` işleci, iki işlenenden bölümü:

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

İşlenenler ise `decimal`, başka bir işleç ne olabilir `float` ya da `double`, çünkü ne `float` ya da `double` örtük olarak dönüştürülebilir `decimal`. Açıkça dönüştürmelisiniz `float` veya `double` işleneni `decimal` türü. Sayısal türler arasında örtük dönüştürme hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../keywords/implicit-numeric-conversions-table.md).

## <a name="remainder-operator-"></a>Kalan işleci %

Kalan işleci `%` ilk işlenenin ikinci işleneni tarafından bölme işleminden kalanı hesaplar.

### <a name="integer-remainder"></a>Tamsayı kalan
  
Tamsayı türleri sonucunu işlenenleri için `a % b` değeri tarafından üretilen `a - (a / b) * b`. Sıfır olmayan kalanı oturum, ilk işlenen, aşağıdaki örnekte gösterildiği gibi aynıdır:

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

Kullanım <xref:System.Math.DivRem%2A?displayProperty=nameWithType> tamsayı bölme hem kalan sonuçları hesaplamak için yöntemi.

### <a name="floating-point-remainder"></a>Kayan nokta kalanını

İçin `float` ve `double` işlenenler, sonucunu `x % y` sınırlı için `x` ve `y` değer `z` gibi

- İşaretini `z`, sıfır olmayan, işaretini aynı `x`.
- mutlak değerini `z` değeri tarafından üretilen `|x| - n * |y|` burada `n` küçük veya eşit en büyük olası tamsayı `|x| / |y|` ve `|x|` ve `|y|` mutlak değerleri `x` ve `y`sırasıyla.

> [!NOTE]
> Kalanı hesaplama, bu yöntem, tamsayı işlenenler için kullanılan benzer, ancak IEEE 754 farklıdır. IEEE 754 ile uyumlu işlemini ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemi.

Davranışı hakkında bilgi için `%` sonlu olmayan işlenenler işleç bkz [kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

İçin `decimal` işlenenler, kalan işleci `%` eşdeğerdir [kalan işleci](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) , <xref:System.Decimal?displayProperty=nameWithType> türü.

Aşağıdaki örnek, kayan nokta işlenenler ile kalan işleci davranışını gösterir:

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Toplama işleci +

Toplama işleci `+` işlenenleri toplamını hesaplar:

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

Ayrıca `+` dize birleştirme ve temsilci birleşimi için işleç. Daha fazla bilgi için [ `+` işleci](addition-operator.md) makalesi.

## <a name="subtraction-operator--"></a>Çıkarma işleci-

Çıkarma işleci `-` gelen ilk işlenenin ikinci işleneni çıkarır:

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

Ayrıca `-` temsilci kaldırma işleci. Daha fazla bilgi için [ `-` işleci](subtraction-operator.md) makalesi.

## <a name="operator-precedence-and-associativity"></a>İşleç önceliği ve ilişkiselliği

Aşağıdaki liste, en yüksek öncelikten en düşük başlangıç aritmetik işleçler sıralar:

- Sonek artırma `x++` ve azaltma `x--` işleçleri
- Önek artırma `++x` ve azaltma `--x` ve birli `+` ve `-` işleçleri
- Çarpma `*`, `/`, ve `%` işleçleri
- Eklenebilir `+` ve `-` işleçleri

İkili aritmetik işleçler ilişkilendirilebilir. Diğer bir deyişle, aynı öncelik düzeyine sahip işleçler, soldan sağa doğru değerlendirilir.

Parantez kullanın `()`, İşleç önceliği ve ilişkilendirilebilirlik tarafından dayatılan Değerlendirme sırasını değiştirmek için.

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).

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

Aşağıdaki örnek, aritmetik işleçlere sahip bileşik atama kullanımını göstermektedir:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

Nedeniyle [sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions), sonucunu `op` işlemi olabilir değil türe örtük olarak dönüştürülebilir `T` , `x`. Böyle bir durumda ise `op` önceden tanımlanmış bir işleç ve işlemin sonucu türüne açıkça dönüştürülebilir ise `T` , `x`, formun bir bileşik atama ifadesi `x op= y` eşdeğerdir `x = (T)(x op y)`, dışında `x` yalnızca bir kez değerlendirilir. Aşağıdaki örnek, bu davranış gösterir:

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Ayrıca `+=` ve `-=` abone ve aboneliği iptal edin işleçleri [olayları](../keywords/event.md). Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="arithmetic-overflow-and-division-by-zero"></a>Aritmetik Taşma ve sıfıra bölme

Aritmetik işlemin sonucu dahil olan sayısal türde olası sınırlı değerler aralığı dışında olduğunda davranışı bir aritmetik işlecinin işlenenleri türüne bağlıdır.

### <a name="integer-arithmetic-overflow"></a>Tamsayı aritmetik taşma

Sıfır ile tamsayı bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.

Olabilen tamsayı aritmetik taşma durumunda, bağlam, denetimi taşma [işaretli veya işaretsiz](../keywords/checked-and-unchecked.md), sonuçta elde edilen davranışı denetler:

- Sabit bir ifadede taşma meydana gelirse denetlenen bir bağlamda, bir derleme zamanı hatası oluşur. Aksi durumda, çalışma zamanında işlemi gerçekleştirilirken bir <xref:System.OverflowException> oluşturulur.
- İşaretlenmemiş bir bağlamda sonucu hedef türüne uygun olmayan herhangi bir yüksek düzeyli BITS atarak kesilir.

İle birlikte [checked ve unchecked](../keywords/checked-and-unchecked.md) kullanabileceğiniz deyimleri `checked` ve `unchecked` işleçler bağlam bir ifade değerlendirme, taşma denetimini için:

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

Varsayılan olarak, aritmetik işlemler oluşan bir *denetlenmeyen* bağlamı.

### <a name="floating-point-arithmetic-overflow"></a>Kayan nokta aritmetik taşma

Aritmetik işlemler `float` ve `double` türleri hiçbir zaman bir özel durum oluşturur. Bu türleri aritmetik işlemler sonucu sonsuzluk ve sayı değil temsil eden özel değerlerden biri olabilir:

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

İşlenen için `decimal` türü, aritmetik taşma her zaman oluşturur bir <xref:System.OverflowException> ve sıfır ile bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.

## <a name="round-off-errors"></a>Yuvarlama hataları

Gerçek sayıları ve kayan nokta aritmetiği kayan nokta temsili genel sınırlamaları nedeniyle, kayan nokta türleriyle hesaplamalarda yuvarlama hataları oluşabilir. Diğer bir deyişle, bir ifadenin üretilen sonucu beklenen matematik sonuç farklı olabilir. Aşağıdaki örnek, bu gibi durumlarda gösterir:

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

Açıklamalar, daha fazla bilgi için bkz. [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), veya [System.Decimal](/dotnet/api/system.decimal#remarks) başvuru sayfalarına.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) birli (`++`, `--`, `+`, ve `-`) ve ikili (`*`, `/`, `%`, `+`ve `-`) Aritmetik işleçler. İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş. Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):

- [Sonek artırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Önek artırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Birli artı işleci](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Birli eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Çarpma işleci](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Bölme işleci](~/_csharplang/spec/expressions.md#division-operator)
- [Kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator)
- [Toplama işleci](~/_csharplang/spec/expressions.md#addition-operator)
- [Çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)
- [Checked ve unchecked işleçleri](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
