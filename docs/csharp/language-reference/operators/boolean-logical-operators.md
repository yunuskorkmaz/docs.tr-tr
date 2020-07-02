---
title: Boolean mantıksal işleçler-C# başvurusu
description: Mantıksal olumsuzlama, birlikte (ve) ve kapsamlı ve dışlamalı (veya) işlemleri Boolean işlenenleriyle gerçekleştiren C# işleçleri hakkında bilgi edinin.
ms.date: 06/29/2020
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
ms.openlocfilehash: a19c804c624153ef608885bc6493537302275765
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618200"
---
# <a name="boolean-logical-operators-c-reference"></a>Boole mantıksal işleçleri (C# Başvurusu)

Aşağıdaki işleçler [bool](../builtin-types/bool.md) işlenenleri olan mantıksal işlemler gerçekleştirir:

- Birli [ `!` (mantıksal değilleme)](#logical-negation-operator-) işleci.
- İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal or)](#logical-or-operator-)ve [ `^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler. Bu operatörler her iki işleneni de değerlendirir.
- İkili [ `&&` (Koşullu mantıksal and)](#conditional-logical-and-operator-) ve [ `||` (Koşullu mantıksal or)](#conditional-logical-or-operator-) işleçleri. Bu işleçler yalnızca gerekli olması durumunda sağ işleneni değerlendirir.

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için,, `&` `|` ve `^` işleçleri bit düzeyinde mantıksal işlemler gerçekleştirir. Daha fazla bilgi için bkz. [bit düzeyinde and SHIFT işleçleri](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Mantıksal Değilleme İşleci!

Birli önek `!` işleci, işleneninin mantıksal olumsuzunu hesaplar. Diğer bir deyişle, `true` işlenen olarak değerlendirilirse, ve işleneni şunu değerleniyorsa üretir `false` `false` `true` .

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

C# 8,0 ' den başlayarak birli sonek `!` operatörü [null-forverme işleçtir](null-forgiving.md).

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a>Mantıksal AND işleci&amp;

`&`İşleci, işlenenlerinin MANTıKSAL ve işlecini hesaplar. Sonucu `x & y` `true` her ikisi de olarak değerlendirilir `x` `y` `true` . Aksi takdirde, sonuç olur `false` .

`&`İşleç, sol işlenen olarak değerlendirilse bile her iki işleneni de değerlendirir `false` , böylece işlem sonucu `false` sağ işlenen değerden bağımsız olarak olur.

Aşağıdaki örnekte, işlecinin sağ işleneni, `&` sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

[Koşullu MANTıKSAL and işleci](#conditional-logical-and-operator-) `&&` Ayrıca IŞLENENLERININ mantıksal ve işlecini hesaplar, ancak sol işlenen olarak değerlendirilirse sağ işleneni değerlendirmez `false` .

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `&` işleç, işlenenlerinin [bit düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar. Birli `&` işleç [Adres işleçtir](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Mantıksal dışlamalı OR işleci ^

`^`İşleci, işlenenlerinin MANTıKSAL XOR 'ı olarak da bilinen mantıksal dışlamalı veya hesaplar. Sonucu olarak `x ^ y` değerlendirilir ve değerlendiriyor ya da olarak değerlendirilir ve olarak değerlendirilir `true` `x` `true` `y` `false` `x` `false` `y` `true` . Aksi takdirde, sonuç olur `false` . Diğer bir deyişle, `bool` işleç, işlenenleri `^` [eşitsizlik işleciyle](equality-operators.md#inequality-operator-) aynı sonucu hesaplar `!=` .

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için, `^` işleç [bit DÜZEYINDE mantıksal dışlamalı veya](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) işlenenleri hesaplar.

## <a name="logical-or-operator-"></a>Mantıksal OR işleci |

`|`İşleci, işlenenlerinin MANTıKSAL veya işlecini hesaplar. Sonucu, ya `x | y` `true` da `x` `y` olarak değerlendirilir `true` . Aksi takdirde, sonuç olur `false` .

`|`İşleç, sol işlenen olarak değerlendirilse bile her iki işleneni de değerlendirir `true` , böylece işlem sonucu `true` sağ işlenen değerden bağımsız olarak olur.

Aşağıdaki örnekte, işlecinin sağ işleneni, `|` sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

[Koşullu MANTıKSAL or işleci](#conditional-logical-or-operator-) `||` Ayrıca, işlenenlerinin mantıksal veya işlecini hesaplar, ancak sol işlenen olarak değerlendirilirse sağ işleneni değerlendirmez `true` .

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `|` işleç, işlenenlerinin [bit düzeyinde mantıksal veya](bitwise-and-shift-operators.md#logical-or-operator-) işlecini hesaplar.

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a>Koşullu mantıksal AND işleci&amp;&amp;

`&&`"Kısa devre dışı" MANTıKSAL and işleci olarak da bilinen koşullu MANTıKSAL and işleci, işlenenlerinin MANTıKSAL ve işlecini hesaplar. Sonucu `x && y` `true` her ikisi de olarak değerlendirilir `x` `y` `true` . Aksi takdirde, sonuç olur `false` . `x`, Olarak değerlendirilirse `false` , `y` değerlendirilmez.

Aşağıdaki örnekte, işlecinin sağ işleneni, `&&` sol taraftaki işlenen şu şekilde değerlendirildiğinde gerçekleştirilmeyen bir yöntem çağrıdır `false` :

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

[MANTıKSAL and işleci](#logical-and-operator-) , `&` işlenenlerinin mantıksal ve işlecini de hesaplar, ancak her iki işleneni de değerlendirir.

## <a name="conditional-logical-or-operator-"></a>Koşullu mantıksal OR işleci | |

`||`"Kısa devre dışı" MANTıKSAL or işleci olarak da bilinen koşullu MANTıKSAL or işleci, işlenenlerinin MANTıKSAL veya işlecini hesaplar. Sonucu, ya `x || y` `true` da `x` `y` olarak değerlendirilir `true` . Aksi takdirde, sonuç olur `false` . `x`, Olarak değerlendirilirse `true` , `y` değerlendirilmez.

Aşağıdaki örnekte, işlecinin sağ işleneni, `||` sol taraftaki işlenen şu şekilde değerlendirildiğinde gerçekleştirilmeyen bir yöntem çağrıdır `true` :

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

[MANTıKSAL or işleci](#logical-or-operator-) `|` Ayrıca işlenenlerinin mantıksal veya ' lerini hesaplar, ancak her iki işleneni de değerlendirir.

## <a name="nullable-boolean-logical-operators"></a>Null yapılabilir Boolean mantıksal işleçler

`bool?`İşlenenler için [ `&` (mantıksal ve)](#logical-and-operator-) ve [ `|` (mantıksal or)](#logical-or-operator-) işleçleri aşağıdaki gibi üç değerli mantığı destekler:

- `&`İşleci `true` yalnızca işlenenlerinin değerlendirmesi durumunda üretir `true` . Ya da `x` `y` olarak değerlendirilirse `false` , `x & y` `false` (başka bir işlenen olarak değerlendirilen bile) üretir `null` . Aksi takdirde, sonucu `x & y` olur `null` .

- `|`İşleci `false` yalnızca işlenenlerinin değerlendirmesi durumunda üretir `false` . Ya da `x` `y` olarak değerlendirilirse `true` , `x | y` `true` (başka bir işlenen olarak değerlendirilen bile) üretir `null` . Aksi takdirde, sonucu `x | y` olur `null` .

Aşağıdaki tabloda bu anlambilimi sunulmaktadır:

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

Bu işleçlerin davranışı, null yapılabilir değer türleriyle tipik işleç davranışından farklıdır. Genellikle, bir değer türünün işlenenleri için tanımlanan bir işleç, karşılık gelen Nullable değer türünün işlenenleri ile de kullanılabilir. Böyle bir işleç `null` , işlenenlerinin herhangi biri olarak değerlendirilirse üretir `null` . Ancak, `&` ve `|` işleçleri işlenenlerden biri olarak değerlendirilse bile null olmayan bir üretebilir `null` . Null yapılabilir değer türleriyle operatör davranışı hakkında daha fazla bilgi için, [Nullable değer türleri](../builtin-types/nullable-value-types.md) makalesinin [yükseltilmemiş işleçleri](../builtin-types/nullable-value-types.md#lifted-operators) bölümüne bakın.

Ayrıca, `!` `^` `bool?` Aşağıdaki örnekte gösterildiği gibi işlenenlerle birlikte ve işleçlerini kullanabilirsiniz:

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

Koşullu mantıksal işleçler `&&` ve `||` `bool?` işlenenleri desteklemez.

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

`&` `|` `^` Aşağıdaki örnekte gösterildiği gibi,, ve işleçleri bileşik atamayı destekler:

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

`()`İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantezleri kullanın:

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için [c# işleçleri](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür,, [overload](operator-overloading.md) , `!` `&` `|` ve işleçlerini aşırı yükleyebilir `^` . İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.

Kullanıcı tanımlı bir tür koşullu mantıksal işleçleri `&&` ve ' i aşırı yükleyemez `||` . Ancak, Kullanıcı tanımlı bir tür [true ve false işleçlerini](true-false-operators.md) ve `&` ya da işlecini belirli bir şekilde aşırı yükleiyorsa, `|` `&&` veya `||` işlemi sırasıyla bu türün işlenenleri için değerlendirilebilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Mantıksal değilleme işleci](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators)
- [Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Bit düzeyinde ve kaydırma işleçleri](bitwise-and-shift-operators.md)
