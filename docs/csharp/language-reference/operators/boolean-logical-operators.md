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
ms.openlocfilehash: e355a89e27ea5bd6e4335b39c4e669610c4b0553
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319102"
---
# <a name="boolean-logical-operators-c-reference"></a>Boole mantıksal işleçleri (C# başvuru)

Aşağıdaki işleçler [bool](../keywords/bool.md) işlenenleri ile mantıksal işlemler gerçekleştirir:

- Birli [`!` (mantıksal değilleme)](#logical-negation-operator-) işleci.
- İkili [`&` (MANTıKSAL ve)](#logical-and-operator-), [`|` (mantıksal or)](#logical-or-operator-)ve [`^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler. Bu operatörler her iki işleneni de değerlendirir.
- İkili [`&&` (koşullu MANTıKSAL and)](#conditional-logical-and-operator-) ve [`||` (Koşullu mantıksal or)](#conditional-logical-or-operator-) işleçleri. Bu işleçler yalnızca gerekli olması durumunda sağ işleneni değerlendirir.

[İntegral](../builtin-types/integral-numeric-types.md) türlerinin işlenenleri için, `&`, `|` ve `^` işleçleri bit düzeyinde mantıksal işlemler gerçekleştirir. Daha fazla bilgi için bkz. [bit düzeyinde and SHIFT işleçleri](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Mantıksal Değilleme İşleci!

@No__t-0 işleci birli önek, işleneninin mantıksal olumsuzunu hesaplar. Diğer bir deyişle, işlenen `false` olarak değerlendirilirse `false` ' yi ve işlenen `true` ' e değerlendirilirse,  ' yi üretir:

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

8,0 ile C# başlayarak birli sonek `!` işleci [null-forverme işleçtir](null-forgiving.md).

## <a name="logical-and-operator-"></a>Mantıksal AND işleci &amp;

@No__t-0 işleci, işlenenlerinin mantıksal ve işlecini hesaplar. @No__t-0 ' ın sonucu, hem `x` hem de `y` `true` olarak değerlendirilir `true` ' dir. Aksi takdirde, sonuç `false` ' dır.

@No__t-0 işleci, sol taraftaki işlenen `false` olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece sonuç sağ işlenen değerinden bağımsız olarak `false` olmalıdır.

Aşağıdaki örnekte, `&` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

@No__t-1 [koşullu MANTıKSAL and işleci](#conditional-logical-and-operator-) , işlenenlerinin mantıksal ve ' lerini de hesaplar, ancak sol işlenen `false` olarak değerlendirilirse sağ işleneni değerlendirmez.

İntegral türlerinin işlenenleri için `&` işleci, işlenenlerinin [bit düzeyinde MANTıKSAL ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar. Birli `&` işleci [Adres işleçtir](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Mantıksal dışlamalı OR işleci ^

@No__t-0 işleci, işlenenlerinin mantıksal XOR olarak da bilinen mantıksal dışlamalı veya bir şekilde hesaplar. @No__t-0 ' ın sonucu `true` ' dir. `x` `true` ' ü değerlendiriyor ve `false` ' i  olarak değerlendirir ya da `x` `true` ' a değerlendirilir. Aksi takdirde, sonuç `false` ' dır. Diğer bir deyişle, `bool` işlenenleri için `^` işleci, [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=` ile aynı sonucu hesaplar.

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

İntegral türlerinin işlenenleri için, `^` işleci, işlenenlerinin [bit düzeyinde mantıksal dışlamalı veya](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) bunların işlenenleri hesaplar.

## <a name="logical-or-operator-"></a>Mantıksal OR işleci |

@No__t-0 işleci, işlenenlerinin mantıksal veya işlecini hesaplar. @No__t-2 veya `y` ' ü `true` olarak değerlendirilirse `x | y` ' ın sonucu `true` ' dir. Aksi takdirde, sonuç `false` ' dır.

@No__t-0 işleci, sol taraftaki işlenen `true` olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece sonuç sağ işlenen değerinden bağımsız olarak `true` olmalıdır.

Aşağıdaki örnekte, `|` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

@No__t-1 [koşullu MANTıKSAL or işleci](#conditional-logical-or-operator-) , işlenenlerinin MANTıKSAL veya veya işlecini de hesaplar, ancak sol işlenen `true` olarak değerlendirilirse sağ işleneni değerlendirmez.

İntegral türlerinin işlenenleri için `|` işleci, işlenenlerinin [bit düzeyinde MANTıKSAL veya](bitwise-and-shift-operators.md#logical-or-operator-) işlecini hesaplar.

## <a name="conditional-logical-and-operator-"></a>Koşullu mantıksal AND işleci &amp; @ no__t-2

"Kısa devre dışı" mantıksal AND işleci olarak da bilinen Koşullu mantıksal AND işleci `&&`, işlenenlerinin mantıksal ve işlecini hesaplar. @No__t-0 ' ın sonucu, hem `x` hem de `y` `true` olarak değerlendirilir `true` ' dir. Aksi takdirde, sonuç `false` ' dır. @No__t-0 `false` olarak değerlendirilirse `y` değerlendirilmez.

Aşağıdaki örnekte, `&&` işlecinin sağ işleneni, sol taraftaki işlenen `false` olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

@No__t-1 [MANTıKSAL ve işleci](#logical-and-operator-) , işlenenlerinin mantıksal ve işlecini de hesaplar, ancak her iki işleneni de değerlendirir.

## <a name="conditional-logical-or-operator-"></a>Koşullu mantıksal OR işleci | |

"Kısa devre dışı" mantıksal OR işleci olarak da bilinen Koşullu mantıksal OR işleci `||`, işlenenlerinin mantıksal veya işlecini hesaplar. @No__t-2 veya `y` ' ü `true` olarak değerlendirilirse `x || y` ' ın sonucu `true` ' dir. Aksi takdirde, sonuç `false` ' dır. @No__t-0 `true` olarak değerlendirilirse `y` değerlendirilmez.

Aşağıdaki örnekte, `||` işlecinin sağ işleneni, sol taraftaki işlenen `true` olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

@No__t-1 [MANTıKSAL or işleci](#logical-or-operator-) , işlenenlerinin mantıksal veya her ikisini de hesaplar, ancak her iki işleneni de değerlendirir.

## <a name="nullable-boolean-logical-operators"></a>Null yapılabilir Boolean mantıksal işleçler

@No__t-0 işlenenleri için, `&` ve `|` işleçleri üç değerli mantığı destekler. Bu işleçlerin semantiği aşağıdaki tablo tarafından tanımlanır:  
  
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

Bu işleçlerin davranışı, null yapılabilir değer türleriyle tipik işleç davranışından farklıdır. Genellikle, bir değer türünün işlenenleri için tanımlanan bir işleç, karşılık gelen Nullable değer türünün işlenenleri ile de kullanılabilir. Bu tür bir operatör, işlenenlerinden herhangi biri `null` ise `null` üretir. Ancak, `&` ve `|` işleçleri, işlenenleri `null` olsa bile null olmayan bir şekilde üretebilir. Null yapılabilir değer türleriyle operatör davranışı hakkında daha fazla bilgi için, [Nullable değer türlerini kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesindeki [işleçler](../../programming-guide/nullable-types/using-nullable-types.md#operators) bölümüne bakın.

Aşağıdaki örnekte gösterildiği gibi `!` ve `^` işleçlerini `bool?` işlenenleriyle de kullanabilirsiniz:

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

@No__t-0 ve `||` Koşullu mantıksal işleçler `bool?` işlenenlerini desteklemez.

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

@No__t-0, `|` ve `^` işleçleri, aşağıdaki örnekte gösterildiği gibi bileşik atamayı destekler:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

@No__t-0 ve `||` Koşullu mantıksal işleçler bileşik atamayı desteklemez.

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, en yüksek öncelikten başlayarak mantıksal işleçleri en düşüğe göre sıralar:

- Mantıksal Değilleme İşleci `!`
- Mantıksal AND işleci `&`
- Mantıksal dışlamalı OR işleci `^`
- Mantıksal OR işleci `|`
- Koşullu mantıksal AND işleci `&&`
- Koşullu mantıksal OR işleci `||`

İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantez, `()` kullanın:

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için bkz [ C# . işleçler](index.md).

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür, `!`, `&`, `|` ve `^` işleçlerini [aşırı](operator-overloading.md) yükleyebilir. İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.

Kullanıcı tanımlı bir tür, `&&` ve `||` Koşullu mantıksal işleçleri aşırı yükleyemez. Ancak, Kullanıcı tanımlı bir tür [doğru ve yanlış işleçleri](true-false-operators.md) ve `&` veya `|` işlecini belirli bir şekilde aşırı yükleiyorsa, sırasıyla `&&` veya `||` işlemi, bu türün işlenenleri için değerlendirilebilir. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.

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
