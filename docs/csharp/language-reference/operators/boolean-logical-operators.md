---
title: Boolean mantıksal işleçler-C# başvurusu
description: Mantıksal olumsuzlama, birlikte (ve) ve kapsamlı ve dışlamalı (veya) işlemleri Boolean işlenenleriyle gerçekleştiren C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 5f85b88236c2e643f97453c64173a3f4f7159a35
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795007"
---
# <a name="boolean-logical-operators-c-reference"></a>Boole mantıksal işleçleri (C# Başvurusu)

Aşağıdaki işleçler [bool](../builtin-types/bool.md) işlenenleri olan mantıksal işlemler gerçekleştirir:

- Birli [ `!` (mantıksal değilleme)](#logical-negation-operator-) işleci.
- İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal or)](#logical-or-operator-)ve [ `^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler. Bu operatörler her iki işleneni de değerlendirir.
- İkili [ `&&` (Koşullu mantıksal and)](#conditional-logical-and-operator-) ve [ `||` (Koşullu mantıksal or)](#conditional-logical-or-operator-) işleçleri. Bu işleçler yalnızca gerekli olması durumunda sağ işleneni değerlendirir.

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md) `&` `|`işlenenleri için,, ve `^` işleçleri bit düzeyinde mantıksal işlemler gerçekleştirir. Daha fazla bilgi için bkz. [bit düzeyinde and SHIFT işleçleri](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Mantıksal Değilleme İşleci!

Birli önek `!` işleci, işleneninin mantıksal olumsuzunu hesaplar. Diğer bir deyişle, işlenen `true`olarak değerlendirilirse `false`, ve `false`işleneni şunu değerleniyorsa üretir. `true`

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

C# 8,0 ' den başlayarak birli sonek `!` operatörü [null-forverme işleçtir](null-forgiving.md).

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a>Mantıksal AND işleci&amp;

`&` İşleci, işlenenlerinin mantıksal ve işlecini hesaplar. Sonucu `x & y` `true` her ikisi de `x` `y` olarak `true`değerlendirilir. Aksi takdirde, sonuç olur `false`.

`&` İşleç, sol işlenen olarak `false`değerlendirilse bile her iki işleneni de değerlendirir, böylece işlem sonucu sağ işlenen değerden bağımsız olarak olur `false` .

Aşağıdaki örnekte, `&` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

[Koşullu mantıksal and işleci](#conditional-logical-and-operator-) `&&` Ayrıca işlenenlerinin mantıksal ve işlecini hesaplar, ancak sol işlenen olarak `false`değerlendirilirse sağ işleneni değerlendirmez.

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `&` işleç, işlenenlerinin [bit düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar. Birli `&` işleç [Adres işleçtir](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Mantıksal dışlamalı OR işleci ^

`^` İşleci, IŞLENENLERININ mantıksal XOR 'ı olarak da bilinen mantıksal dışlamalı veya hesaplar. Sonucu `x ^ y` olarak `true` `x` değerlendirilir `true` `y` ve `false` `x` değerlendiriyor ya da olarak değerlendirilir `false` ve `y` olarak değerlendirilir. `true` Aksi takdirde, sonuç olur `false`. `bool` Diğer bir deyişle, `^` işleç, işlenenleri [eşitsizlik işleciyle](equality-operators.md#inequality-operator-) `!=`aynı sonucu hesaplar.

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için, `^` işleç [BIT düzeyinde mantıksal dışlamalı veya](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) işlenenleri hesaplar.

## <a name="logical-or-operator-"></a>Mantıksal OR işleci |

`|` İşleci, işlenenlerinin mantıksal veya işlecini hesaplar. Sonucu `x | y` `true` , ya da `x` olarak `y` `true`değerlendirilir. Aksi takdirde, sonuç olur `false`.

`|` İşleç, sol işlenen olarak `true`değerlendirilse bile her iki işleneni de değerlendirir, böylece işlem sonucu sağ işlenen değerden bağımsız olarak olur `true` .

Aşağıdaki örnekte, `|` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

[Koşullu mantıksal or işleci](#conditional-logical-or-operator-) `||` Ayrıca, işlenenlerinin mantıksal veya işlecini hesaplar, ancak sol işlenen olarak `true`değerlendirilirse sağ işleneni değerlendirmez.

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `|` işleç, işlenenlerinin [bit düzeyinde mantıksal veya](bitwise-and-shift-operators.md#logical-or-operator-) işlecini hesaplar.

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a>Koşullu mantıksal AND işleci&amp;&amp;

"Kısa devre dışı" `&&`mantıksal and işleci olarak da bilinen Koşullu mantıksal and işleci, işlenenlerinin mantıksal ve işlecini hesaplar. Sonucu `x && y` `true` her ikisi de `x` `y` olarak `true`değerlendirilir. Aksi takdirde, sonuç olur `false`. , `x` Olarak `false`değerlendirilirse, `y` değerlendirilmez.

Aşağıdaki örnekte, `&&` işlecinin sağ işleneni, sol taraftaki işlenen şu şekilde `false`değerlendirildiğinde gerçekleştirilmeyen bir yöntem çağrıdır:

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

[Mantıksal and işleci](#logical-and-operator-) `&` , işlenenlerinin mantıksal ve işlecini de hesaplar, ancak her iki işleneni de değerlendirir.

## <a name="conditional-logical-or-operator-"></a>Koşullu mantıksal OR işleci | |

"Kısa devre dışı" `||`mantıksal or işleci olarak da bilinen Koşullu mantıksal or işleci, işlenenlerinin mantıksal veya işlecini hesaplar. Sonucu `x || y` `true` , ya da `x` olarak `y` `true`değerlendirilir. Aksi takdirde, sonuç olur `false`. , `x` Olarak `true`değerlendirilirse, `y` değerlendirilmez.

Aşağıdaki örnekte, `||` işlecinin sağ işleneni, sol taraftaki işlenen şu şekilde `true`değerlendirildiğinde gerçekleştirilmeyen bir yöntem çağrıdır:

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

[Mantıksal or işleci](#logical-or-operator-) `|` Ayrıca işlenenlerinin mantıksal veya ' lerini hesaplar, ancak her iki işleneni de değerlendirir.

## <a name="nullable-boolean-logical-operators"></a>Null yapılabilir Boolean mantıksal işleçler

İşlenenler `bool?` için `&` ve `|` işleçleri üç değerli mantığı destekler. Bu işleçlerin semantiği aşağıdaki tablo tarafından tanımlanır:  
  
|x|y|x&y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|yanlış|yanlış|true|  
|true|null|null|true|  
|yanlış|true|yanlış|true|  
|yanlış|yanlış|yanlış|yanlış|  
|yanlış|null|yanlış|null|  
|null|true|null|true|  
|null|yanlış|yanlış|null|  
|null|null|null|null|  

Bu işleçlerin davranışı, null yapılabilir değer türleriyle tipik işleç davranışından farklıdır. Genellikle, bir değer türünün işlenenleri için tanımlanan bir işleç, karşılık gelen Nullable değer türünün işlenenleri ile de kullanılabilir. Böyle bir işleç, `null` işlenenlerinin herhangi biri olarak `null`değerlendirilirse üretir. Ancak, `&` ve `|` işleçleri işlenenlerden biri olarak `null`değerlendirilse bile null olmayan bir üretebilir. Null yapılabilir değer türleriyle operatör davranışı hakkında daha fazla bilgi için, [Nullable değer türleri](../builtin-types/nullable-value-types.md) makalesinin [yükseltilmemiş işleçleri](../builtin-types/nullable-value-types.md#lifted-operators) bölümüne bakın.

Ayrıca, `!` aşağıdaki örnekte gösterildiği gibi `^` işlenenlerle `bool?` birlikte ve işleçlerini kullanabilirsiniz:

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

Koşullu mantıksal işleçler `&&` ve `||` işlenenleri desteklemez. `bool?`

## <a name="compound-assignment"></a>Bileşik atama

Bir ikili işleci `op`için, formun bileşik atama ifadesi

```csharp
x op= y
```

eşdeğerdir

```csharp
x = x op y
```

`x` hariç yalnızca bir kez değerlendirilir.

Aşağıdaki `&`örnekte `|`gösterildiği gibi `^` ,, ve işleçleri bileşik atamayı destekler:

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> Koşullu mantıksal işleçler `&&` ve `||` bileşik atamayı desteklemez.

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, en yüksek öncelikten başlayarak mantıksal işleçleri en düşüğe göre sıralar:

- Mantıksal Değilleme İşleci`!`
- Mantıksal AND işleci`&`
- Mantıksal dışlamalı OR işleci`^`
- Mantıksal OR işleci`|`
- Koşullu mantıksal AND işleci`&&`
- Koşullu mantıksal OR işleci`||`

İşleç önceliğine göre `()`uygulanan değerlendirmenin sırasını değiştirmek için parantezleri kullanın:

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için [c# işleçleri](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir `!`tür `&` `|`,,, ve `^` işleçlerini [aşırı](operator-overloading.md) yükleyebilir. İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.

Kullanıcı tanımlı bir tür koşullu mantıksal işleçleri `&&` ve ' i `||`aşırı yükleyemez. Ancak, Kullanıcı tanımlı bir tür [true ve false işleçlerini](true-false-operators.md) ve `&` ya `|` da işlecini belirli bir şekilde aşırı yükleiyorsa, `&&` veya `||` işlemi sırasıyla bu türün işlenenleri için değerlendirilebilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Mantıksal Değilleme İşleci](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators)
- [Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Bit düzeyinde ve kaydırma işleçleri](bitwise-and-shift-operators.md)
