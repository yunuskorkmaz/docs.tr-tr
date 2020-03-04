---
title: Boole mantıksal işleçler- C# başvuru
description: Mantıksal olumsuzlama, birlikte (ve) ve kapsamlı ve dışlamalı (ya da) işlemleri Boolean işlenenleriyle gerçekleştiren işleçler hakkında C# bilgi edinin.
ms.date: 09/27/2019
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
ms.openlocfilehash: d8fe68fc04300b65bea9b66a6dc6c20e3c69abf4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239449"
---
# <a name="boolean-logical-operators-c-reference"></a>Boole mantıksal işleçleri (C# başvuru)

Aşağıdaki işleçler [bool](../builtin-types/bool.md) işlenenleri olan mantıksal işlemler gerçekleştirir:

- Birli [`!` (mantıksal değilleme)](#logical-negation-operator-) işleci.
- İkili [`&` (MANTıKSAL ve)](#logical-and-operator-), [`|` (mantıksal or)](#logical-or-operator-)ve [`^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler. Bu operatörler her iki işleneni de değerlendirir.
- İkili [`&&` (koşullu MANTıKSAL and)](#conditional-logical-and-operator-) ve [`||` (Koşullu mantıksal or)](#conditional-logical-or-operator-) işleçleri. Bu işleçler yalnızca gerekli olması durumunda sağ işleneni değerlendirir.

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için, `&`, `|`ve `^` işleçleri bit düzeyinde mantıksal işlemler gerçekleştirir. Daha fazla bilgi için bkz. [bit düzeyinde and SHIFT işleçleri](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Mantıksal Değilleme İşleci!

Birli önek `!` işleci, işleneninin mantıksal olumsuzunu hesaplar. Diğer bir deyişle, işlenen `false`değerlendirilirse `true`üretir ve işlenen `true`olarak değerlendirilirse `false`:

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

8,0 ile C# başlayarak birli sonek `!` işleci [null-forverme işleçtir](null-forgiving.md).

## <a name="logical-and-operator-"></a>Mantıksal AND işleci &amp;

`&` işleci, işlenenlerinin mantıksal ve işlecini hesaplar. `x & y` sonucu, hem `x` hem de `y` `true`olarak değerlendirilir `true`. Aksi takdirde, sonuç `false`.

`&` işleci, sol taraftaki işlenen `false`olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece işlem sonucu sağ işlenen değerden bağımsız olarak `false`.

Aşağıdaki örnekte, `&` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

[Koşullu MANTıKSAL and işleci](#conditional-logical-and-operator-) `&&` Ayrıca, işlenenlerinin mantıksal ve işlecini hesaplar, ancak sol işlenen `false`olarak değerlendirilirse sağ işleneni değerlendirmez.

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `&` işleci, işlenenlerinin [BIT düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar. Birli `&` işleci, [Adres işleçtir](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Mantıksal dışlamalı OR işleci ^

`^` işleci, işlenenlerinin mantıksal XOR olarak da bilinen mantıksal dışlamalı veya bir şekilde hesaplar. `x ^ y` sonucu, `x` `true` olarak değerlendirilir ve `y` `false`olarak değerlendirilir ve `x` `false` olarak değerlendirilir `true`.`y``true` Aksi takdirde, sonuç `false`. Diğer bir deyişle, `bool` işlenenleri için `^` işleci, [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=`aynı sonucu hesaplar.

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için, `^` işleci, işlenenlerinin [bit düzeyinde MANTıKSAL dışlamalı veya](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) bunların işlenenleri hesaplar.

## <a name="logical-or-operator-"></a>Mantıksal OR işleci |

`|` işleci, işlenenlerinin mantıksal veya işlecini hesaplar. `x | y` sonucu, `x` veya `y` `true`olarak değerlendirilirse `true`. Aksi takdirde, sonuç `false`.

`|` işleci, sol taraftaki işlenen `true`olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece işlem sonucu sağ işlenen değerden bağımsız olarak `true`.

Aşağıdaki örnekte, `|` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

[Koşullu MANTıKSAL or işleci](#conditional-logical-or-operator-) `||` Ayrıca, işlenenlerinin mantıksal veya işlecini hesaplar, ancak sol işlenen `true`olarak değerlendirilirse sağ işleneni değerlendirmez.

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `|` işleci, işlenenlerinin [BIT düzeyinde mantıksal veya](bitwise-and-shift-operators.md#logical-or-operator-) işlecini hesaplar.

## <a name="conditional-logical-and-operator-"></a>Koşullu mantıksal AND işleci &amp;&amp;

"Kısa devre dışı" mantıksal AND işleci olarak da bilinen Koşullu mantıksal ve işleç `&&`, işlenenlerinin mantıksal ve işlecini hesaplar. `x && y` sonucu, hem `x` hem de `y` `true`olarak değerlendirilir `true`. Aksi takdirde, sonuç `false`. `x` `false`değerlendirilirse `y` değerlendirilmez.

Aşağıdaki örnekte, `&&` işlecinin sağ işleneni, sol taraftaki işlenen `false`olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

[MANTıKSAL and işleci](#logical-and-operator-) `&` Ayrıca IŞLENENLERININ mantıksal ve ' lerini hesaplar, ancak her iki işleneni de değerlendirir.

## <a name="conditional-logical-or-operator-"></a>Koşullu mantıksal OR işleci | |

"Kısa devre dışı" mantıksal OR işleci olarak da bilinen Koşullu mantıksal OR işleci `||`, işlenenlerinin mantıksal veya işlecini hesaplar. `x || y` sonucu, `x` veya `y` `true`olarak değerlendirilirse `true`. Aksi takdirde, sonuç `false`. `x` `true`değerlendirilirse `y` değerlendirilmez.

Aşağıdaki örnekte, `||` işlecinin sağ işleneni, sol taraftaki işlenen `true`olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

Ayrıca, [MANTıKSAL or işleci](#logical-or-operator-) `|` işlenenlerini de hesaplar, ancak her iki işleneni de değerlendirir.

## <a name="nullable-boolean-logical-operators"></a>Null yapılabilir Boolean mantıksal işleçler

`bool?` işlenenleri için, `&` ve `|` işleçleri üç değerli mantığı destekler. Bu işleçlerin semantiği aşağıdaki tablo tarafından tanımlanır:  
  
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

Bu işleçlerin davranışı, null yapılabilir değer türleriyle tipik işleç davranışından farklıdır. Genellikle, bir değer türünün işlenenleri için tanımlanan bir işleç, karşılık gelen Nullable değer türünün işlenenleri ile de kullanılabilir. Bu tür bir operatör, işlenenleri `null`değerlendirilirse `null` üretir. Ancak, `&` ve `|` işleçleri, işlenenlerden biri `null`olarak değerlendirilse bile null olmayan üretebilir. Null yapılabilir değer türleriyle operatör davranışı hakkında daha fazla bilgi için, [Nullable değer türleri](../builtin-types/nullable-value-types.md) makalesinin [yükseltilmemiş işleçleri](../builtin-types/nullable-value-types.md#lifted-operators) bölümüne bakın.

Aşağıdaki örnekte gösterildiği gibi, `!` ve `^` işleçlerini `bool?` işlenenleriyle de kullanabilirsiniz:

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

Koşullu mantıksal işleçler `&&` ve `||` `bool?` işlenenleri desteklemez.

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

`&`, `|`ve `^` işleçleri, aşağıdaki örnekte gösterildiği gibi bileşik atamayı destekler:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

Koşullu mantıksal işleçler `&&` ve `||` bileşik atamayı desteklemez.

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, en yüksek öncelikten başlayarak mantıksal işleçleri en düşüğe göre sıralar:

- Mantıksal Değilleme İşleci `!`
- Mantıksal AND işleci `&`
- Mantıksal dışlamalı OR işleci `^`
- Mantıksal OR işleci `|`
- Koşullu mantıksal AND işleci `&&`
- Koşullu mantıksal OR işleci `||`

İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantez, `()`kullanın:

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için, [ C# işleçler](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür `!`, `&`, `|`ve `^` işleçlerini [aşırı](operator-overloading.md) yükleyebilir. İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.

Kullanıcı tanımlı bir tür koşullu mantıksal işleçleri `&&` ve `||`aşırı yükleyemez. Ancak, Kullanıcı tanımlı bir tür [true ve false işleçlerini](true-false-operators.md) ve `&` ya da `|` işlecini belirli bir şekilde aşırı yükleiyorsa, sırasıyla `&&` veya `||` işlemi bu türün işlenenleri için değerlendirilebilir. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Mantıksal Değilleme İşleci](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators)
- [Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Bit düzeyinde ve kaydırma işleçleri](bitwise-and-shift-operators.md)
