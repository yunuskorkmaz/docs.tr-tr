---
title: Boolean mantıksal işleçleri - C# referansı
description: Boolean operands ile mantıksal olumsuzlama, bağlaç (AND) ve kapsayıcı ve özel ayırma (OR) işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399499"
---
# <a name="boolean-logical-operators-c-reference"></a>Boolean mantıksal işleçleri (C# referansı)

Aşağıdaki işleçler [bool](../builtin-types/bool.md) operands ile mantıksal işlemler gerçekleştirin:

- Unary [ `!` (mantıksal olumsuzlama)](#logical-negation-operator-) işleci.
- İkili [ `&` (mantıksal AND)](#logical-and-operator-), [ `|` (mantıksal OR)](#logical-or-operator-)ve [ `^` (mantıksal özel OR)](#logical-exclusive-or-operator-) işleçleri. Bu operatörler her zaman her iki operands değerlendirmek.
- İkili [ `&&` (koşullu mantıksal AND)](#conditional-logical-and-operator-) ve [ `||` (koşullu mantıksal OR)](#conditional-logical-or-operator-) işleçleri. Bu operatörler sağ operve sadece gerekli olduğunda değerlendirirler.

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)operands `&`için `|`, `^` , ve operatörler bitwise mantıksal işlemler gerçekleştirin. Daha fazla bilgi için [Bitwise ve shift işleçleri'ne](bitwise-and-shift-operators.md)bakın.

## <a name="logical-negation-operator-"></a>Mantıksal olumsuzlama operatörü!

Unary önek `!` işleci, operand'ının mantıksal olumsuzluğunu hesaplar. Yani, `true`üretir , eğer operand değerlendirir `false`, `false`ve , eğer operand `true`değerlendirir:

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

C# 8.0 ile başlayarak, `!` unary postfix işleci [null-affgiving işlecidir.](null-forgiving.md)

## <a name="logical-and-operator-"></a>Mantıksal VE işleç&amp;

İşletici, `&` operandlarının mantıksal ve mantıksal ve hesaplamalarını. Bunun sonucu `x & y` `true` ise `x` her `y` ikisi `true`de ve değerlendirmek . Aksi takdirde, `false`sonuç .

Operatör, `&` sol daki operand'ı değerlendirse bile, operasyon `false`sonucunun sağ operand'ın `false` değerine bakılmaksızın her iki operandı da değerlendirir.

Aşağıdaki örnekte, `&` işleç sağ operand sol operand değeri ne olursa olsun gerçekleştirilen bir yöntem çağrısıdır:

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

[Koşullu mantıksal VE işleci](#conditional-logical-and-operator-) `&&` de mantıksal VE onun operands hesaplamak, ancak sağ operand değerlendirmek değil eğer sol `false`operand değerlendirir .

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)operands `&` için, operatör [bitwise mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) onun operands hesaplar. Unary `&` [işleci, işlecin adresidir.](pointer-related-operators.md#address-of-operator-)

## <a name="logical-exclusive-or-operator-"></a>Mantıksal özel OR operatörü ^

İşletici, `^` operandlarının mantıksal XOR olarak da bilinen mantıksal özel veya'sini hesaplar. Bunun `x ^ y` sonucu, `true` `x` `true` eğer değerlendirirve `y` `false`değerlendirirse, `x` ya `false` da `y` değerlendirir `true`ve değerlendirir. Aksi takdirde, `false`sonuç . Diğer bir `bool` deyişle, operands `^` için, operatör [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=`olarak aynı sonucu hesaplamak.

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)operands `^` için, operatör [bitwise mantıksal özel VEYA](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) operands bilgisayara.

## <a name="logical-or-operator-"></a>Mantıksal OR işleci |

İşletici, `|` operandlarının mantıksal VEYA'sini hesaplar. `x | y` Bunun sonucu, `true` eğer `x` `y` ya da `true`değerlendirir. Aksi takdirde, `false`sonuç .

Operatör, `|` sol daki operand'ı değerlendirse bile, operasyon `true`sonucunun sağ operand'ın `true` değerine bakılmaksızın her iki operandı da değerlendirir.

Aşağıdaki örnekte, `|` işleç sağ operand sol operand değeri ne olursa olsun gerçekleştirilen bir yöntem çağrısıdır:

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

[Koşullu mantıksal OR işleci](#conditional-logical-or-operator-) `||` de onun operands mantıksal OR bilgisayar, ancak sağ operand değerlendirmek değil eğer sol operand `true`değerlendirir .

[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)operands `|` için, operatör [bitwise mantıksal VEYA](bitwise-and-shift-operators.md#logical-or-operator-) operands bilgisayara.

## <a name="conditional-logical-and-operator-"></a>Koşullu mantıksal VE işleç&amp;&amp;

Koşullu mantıksal VE `&&`işleç , aynı zamanda "kısa devre" mantıksal VE işleci olarak bilinen, mantıksal VE onun operands hesaplamak. Bunun sonucu `x && y` `true` ise `x` her `y` ikisi `true`de ve değerlendirmek . Aksi takdirde, `false`sonuç . `x` Değerlendiriliyorsa, `y` `false`değerlendirilmez.

Aşağıdaki örnekte, `&&` işleç sağ operand sol el operand değerlendirirse yapılmaz bir yöntem çağrısı `false`vardır:

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

[Mantıksal VE işleci](#logical-and-operator-) `&` de mantıksal VE onun operands bilgisayara, ama her zaman her iki operands değerlendirir.

## <a name="conditional-logical-or-operator-"></a>Koşullu mantıksal OR işleci ||

Koşullu mantıksal OR `||`işleci , "kısa devre" mantıksal OR işleci olarak da bilinir, onun operands mantıksal VEYA bilgisayar. `x || y` Bunun sonucu, `true` eğer `x` `y` ya da `true`değerlendirir. Aksi takdirde, `false`sonuç . `x` Değerlendiriliyorsa, `y` `true`değerlendirilmez.

Aşağıdaki örnekte, `||` işleç sağ operand sol el operand değerlendirirse yapılmaz bir yöntem çağrısı `true`vardır:

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

[Mantıksal OR işleci](#logical-or-operator-) `|` de onun operands mantıksal OR bilgisayar, ama her zaman her iki operands değerlendirir.

## <a name="nullable-boolean-logical-operators"></a>Nullable Boolean mantıksal işleçleri

Operands `bool?` için, `&` `|` ve operatörler üç değerli mantığı destekler. Bu işleçlerin anlambilimi aşağıdaki tablo ile tanımlanır:  
  
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

Bu işleçlerin davranışı, nullable değer türleri ile tipik işleç davranışı farklıdır. Tipik olarak, bir değer türünün operands için tanımlanan bir işleç de karşılık gelen nullable değer türü operands ile kullanılabilir. Böyle bir `null` operatör, herhangi bir operands `null`değerlendirirse üretir. Ancak, `&` operands biri değerlendirilse bile ve `|` operatörler non-null `null`üretebilir. Nullable değer türleri ile işleç davranışı hakkında daha fazla bilgi için, [Nullable değer türleri](../builtin-types/nullable-value-types.md) makalenin [Kaldırılan işleçler](../builtin-types/nullable-value-types.md#lifted-operators) bölümüne bakın.

Aşağıdaki örnekte `!` görüldüğü `^` gibi, operandlu ve operandlu `bool?` işleçleri de kullanabilirsiniz:

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

Koşullu mantıksal `&&` işleçler `||` ve `bool?` operands destekyok.

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

, `&` `|`, `^` ve işleçler bileşik atamayı destekler, aşağıdaki örnekte görüldüğü gibi:

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

Koşullu mantıksal `&&` işleçler ve `||` bileşik atama desteklemiyor.

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, mantıksal işleçleri en yüksek öncelikten en düşüke doğru sipariş verir:

- Mantıksal olumsuzlama işleci`!`
- Mantıksal VE işleç`&`
- Mantıksal özel OR işleci`^`
- Mantıksal VEYA işleci`|`
- Koşullu mantıksal VE işleç`&&`
- Koşullu mantıksal OR işleci`||`

Operatör önceliği tarafından `()`dayatılan değerlendirme sırasını değiştirmek için parantez kullanın:

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

Öncelik düzeyine göre sıralanan C# işleçlerinin tam listesi için [C# işleçleri](index.md) makalesinin [Operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür `!`, `&` `|`, `^` , ve işleçleri [aşırı yükleyebilir.](operator-overloading.md) Bir ikili işleci aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenir. Kullanıcı tanımlı bir tür, bileşik atama işlecinin aşırı yüklenemeyeceğini açıkça ifade eder.

Kullanıcı tanımlı bir tür koşullu mantıksal `&&` `||`işleçleri aşırı yükleyemez ve . Ancak, kullanıcı tanımlı bir tür doğru ve yanlış `&` `|` [işleçleri](true-false-operators.md) ve veya `&&` `||` işleci belirli bir şekilde aşırı yüklerse, sırasıyla işlem veya işlem, bu tür operands için değerlendirilebilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı koşullu mantıksal işleçleri](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Mantıksal olumsuzlama işleci](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators)
- [Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Bit düzeyinde ve kaydırma işleçleri](bitwise-and-shift-operators.md)
