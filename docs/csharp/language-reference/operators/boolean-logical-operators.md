---
title: Boolean mantıksal işleçler - C# başvurusu
description: Hakkında bilgi edinin C# mantıksal olumsuzlama, (ve) birlikte ve Boole işlenenler dahil ve hariç ayrım (veya) işlemleri gerçekleştiren işleçleri.
ms.date: 04/08/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 60907eb1bbfeb1daa9d9a74733387c4771accb45
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423982"
---
# <a name="boolean-logical-operators-c-reference"></a>Boolean mantıksal işleçleri (C# Başvurusu)

Aşağıdaki işleçleri ile mantıksal işlemleri [bool](../keywords/bool.md) işlenenler:

- Birli [ `!` (mantıksal olumsuzlama)](#logical-negation-operator-) işleci.
- İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal veya)](#logical-or-operator-), ve [ `^` (mantıksal XOR)](#logical-exclusive-or-operator-) işleçleri. Bu işleçler, her iki işlenen de her zaman değerlendirin.
- İkili [ `&&` (koşullu mantıksal ve)](#conditional-logical-and-operator-) ve [ `||` (koşullu mantıksal veya)](#conditional-logical-or-operator-) işleçleri. Yalnızca gerekli olduğunda bu işleçleri atamada sağ işlenen değerlendirin.

İşlenen için [integral](../builtin-types/integral-numeric-types.md) türleri `&`, `|`, ve `^` işleçleri mantıksal bit düzeyinde işlemler gerçekleştirin. Daha fazla bilgi için [işleçler bit düzeyinde and -shift](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Mantıksal değilleme işleci!

`!` İşleci, işlenenin mantıksal olumsuzlama hesaplar. Diğer bir deyişle, ürettiği `true`, işlenenin değerlendirilirse `false`, ve `false`, işlenenin değerlendirilirse `true`:

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

## <a name="logical-and-operator-"></a> Mantıksal AND işleci &amp;

`&` İşlenenleri, mantıksal AND işleci hesaplar. Sonucu `x & y` olduğu `true` hem `x` ve `y` vermesi `true`. Aksi halde sonuç, `false`.

`&` İşleci sol işlenenin değerlendirilir olsa bile her iki işlenen de değerlendirir `false`, sonuç olmalıdır böylece `false` sağ işlenenin değerinden bağımsız olarak.

Aşağıdaki örnekte, sağ işleneni `&` işleci sol işlenenin değerini bağımsız olarak gerçekleştirilen bir yöntem çağrısının:

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

[Koşullu mantıksal AND işlecinin](#conditional-logical-and-operator-) `&&` ayrıca mantıksal ve işlenenleri, hesaplar, ancak atamada sağ işlenen, sol işlenen değerlendirilirse değerlendirmez `false`.

İntegral türündeki işlenenler için `&` işleci hesaplar [mantıksal bit düzeyinde AND](bitwise-and-shift-operators.md#logical-and-operator-) işlenenleri biri. Birli `&` işleci [address-of işleci](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Mantıksal Dışlayıcı veya işlecini ^

`^` Mantıksal Dışlayıcı veya olarak da bilinir, işlenenleri mantıksal XOR işleci hesaplar. Sonucu `x ^ y` olduğu `true` varsa `x` değerlendiren `true` ve `y` değerlendiren `false`, veya `x` değerlendiren `false` ve `y` değerlendiren `true`. Aksi halde sonuç, `false`. Diğer bir deyişle, için `bool` işlenenini `^` işleci aynı sonucu hesaplar [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

İntegral türündeki işlenenler için `^` işleci hesaplar [mantıksal bit düzeyinde dışlamalı OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) işlenenleri biri.

## <a name="logical-or-operator-"></a>Mantıksal OR işlecinin |

`|` İşlenenleri, mantıksal OR işleci hesaplar. Sonucu `x | y` olduğu `true` ya da `x` veya `y` değerlendiren `true`. Aksi halde sonuç, `false`.

`|` İşleci sol işlenenin değerlendirilir olsa bile her iki işlenen de değerlendirir `true`, sonuç olmalıdır böylece `true` sağ işlenenin değerinden bağımsız olarak.

Aşağıdaki örnekte, sağ işleneni `|` işleci sol işlenenin değerini bağımsız olarak gerçekleştirilen bir yöntem çağrısının:

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

[Koşullu mantıksal OR işlecinin](#conditional-logical-or-operator-) `||` ayrıca mantıksal OR işlenenleri, hesaplar, ancak atamada sağ işlenen, sol işlenen değerlendirilirse değerlendirmez `true`.

İntegral türündeki işlenenler için `|` işleci hesaplar [mantıksal bit düzeyinde OR](bitwise-and-shift-operators.md#logical-or-operator-) işlenenleri biri.

## <a name="conditional-logical-and-operator-"></a> Koşullu mantıksal AND işleci &amp;&amp;

Koşullu mantıksal AND işlecinin `&&`, mantıksal ve işlenenleri, "kısa devre" mantıksal AND işleci, hesaplar olarak da bilinir. Sonucu `x && y` olduğu `true` hem `x` ve `y` vermesi `true`. Aksi halde sonuç, `false`. Varsa `x` değerlendiren `false`, `y` değerlendirilmez.

Aşağıdaki örnekte, sağ işleneni `&&` işleci sol işlenenin değerlendirilirse yapılamaz bir yöntem çağrısının, `false`:

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

[Mantıksal AND işlecinin](#logical-and-operator-) `&` ayrıca mantıksal ve işlenenleri, hesaplar, ancak her iki işlenen de her zaman değerlendirilir.

## <a name="conditional-logical-or-operator-"></a>Mantıksal OR işlecinin koşullu ||

Koşullu mantıksal OR işlecinin `||`, "kısa devre" mantıksal OR işleci, işlenenleri, mantıksal OR hesaplar olarak da bilinir. Sonucu `x || y` olduğu `true` ya da `x` veya `y` değerlendiren `true`. Aksi halde sonuç, `false`. Varsa `x` değerlendiren `true`, `y` değerlendirilmez.

Aşağıdaki örnekte, sağ işleneni `||` işleci sol işlenenin değerlendirilirse yapılamaz bir yöntem çağrısının, `true`:

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

[Mantıksal OR işlecinin](#logical-or-operator-) `|` ayrıca mantıksal OR işlenenleri, hesaplar, ancak her iki işlenen de her zaman değerlendirilir.

## <a name="nullable-boolean-logical-operators"></a>Boş değer atanabilir Boolean mantıksal işleçler

İçin `bool?` işlenenini `&` ve `|` üç değerli mantıksal işleçleri destekler. Bu işleçler semantiği aşağıdaki tabloda tanımlanır:  
  
|x|y|x & y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  

Bu işleçlerin davranışını boş değer atanabilen değer türleri ile tipik işleci davranışından farklıdır. Genellikle, bir değer türündeki işlenenler için tanımlanan bir işleç işlenenleri karşılık gelen null yapılabilir değer türü ile birlikte kullanılabilir. Böyle bir işleç üretir `null` işlenenleri biri `null`. Ancak, `&` ve `|` işleçleri işlenenlerden olsa bile, null olmayan üretebilir `null`. Boş değer atanabilen değer türleri ile işleci davranış hakkında daha fazla bilgi için bkz. [işleçleri](../../programming-guide/nullable-types/using-nullable-types.md#operators) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.

Ayrıca `!` ve `^` işleçlerle `bool?` aşağıdaki örnekte gösterildiği gibi işlenenler:

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

Koşullu mantıksal işleçler `&&` ve `||` desteklemeyen `bool?` işlenen.

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

`&`, `|`, Ve `^` aşağıdaki örnekte gösterildiği gibi bileşik atama işleçleri destekler:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

Koşullu mantıksal işleçler `&&` ve `||` bileşik atama desteklemez.

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, en yüksek öncelikten en düşük başlangıç mantıksal işleçler sıralar:

- Mantıksal değilleme işleci `!`
- Mantıksal AND işleci `&`
- Özel mantıksal OR işleci `^`
- Mantıksal OR işleci `|`
- Koşullu mantıksal AND işleci `&&`
- Koşullu mantıksal OR işleci `||`

Parantez kullanın `()`İşleç önceliği tarafından belirlenen değerlendirmenin sırasını değiştirmek için:

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `!`, `&`, `|`, ve `^` işleçleri. İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş. Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.

Kullanıcı tanımlı bir tür koşullu mantıksal işleçler aşırı yüklenemez `&&` ve `||`. Ancak, kullanıcı tanımlı bir tür aşırı [true ve false işleçleri](true-false-operators.md) ve `&` veya `|` işleci belirli bir şekilde `&&` veya `||` işlemi, sırasıyla değerlendirmesi yapılamıyor için işlenen türü. Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):

- [Mantıksal değilleme işleci](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators)
- [Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [Bit düzeyinde ve kaydırma işleçleri](bitwise-and-shift-operators.md)
