---
title: C#işleçler- C# başvuru
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 7db61e530ba5c3e0b5ae0ee0002621e369e1833b
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566845"
---
# <a name="c-operators-c-reference"></a>C#İşleçler (C# başvuru)

C#Yerleşik türler tarafından desteklenen bir dizi önceden tanımlanmış işleç sağlar. Örneğin, [Aritmetik işleçler](arithmetic-operators.md) , yerleşik sayısal türlerin işlenenleriyle aritmetik işlemler gerçekleştirir ve [Boole mantıksal işleçleri](boolean-logical-operators.md) [bool](../keywords/bool.md) işlenenleri ile mantıksal işlemler gerçekleştirir.

Kullanıcı tanımlı bir tür, bu türün işlenenleri için karşılık gelen davranışı tanımlamak üzere bazı işleçleri aşırı yükleyebilir. Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](operator-overloading.md).

Aşağıdaki tabloda en düşük önceliğe C# göre başlayan işleçler listelenmektedir. Her satır içindeki işleçler aynı öncelik düzeyini paylaşır.

| İşleçler | Kategori veya ad |
| --------- | ---------------- |
| [x. y](member-access-operators.md#member-access-operator-), [x?. y](member-access-operators.md#null-conditional-operators--and-), [x? [ y]](member-access-operators.md#null-conditional-operators--and-), [f (x)](member-access-operators.md#invocation-operator-), [a&#91;i&#93;](member-access-operators.md#indexer-operator-), [x + +](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [New](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [Checked](../keywords/checked.md), [denetimsiz](../keywords/unchecked.md), [Default](default.md), [NameOf](nameof.md), [Delegate](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x-> y](pointer-related-operators.md#pointer-member-access-operator--) | Birincil |
| [+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [+ + x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [(T) x](type-testing-and-cast.md#cast-operator-), [await](../keywords/await.md), [& x](pointer-related-operators.md#address-of-operator-), [* x](pointer-related-operators.md#pointer-indirection-operator-), [true ve false](true-false-operators.md) | Li |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-) | Çarpma|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Msal |
| [ x\< y ,\< ](bitwise-and-shift-operators.md#left-shift-operator-) [x > > y](bitwise-and-shift-operators.md#right-shift-operator-) | Shift |
| [x\< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-), [](type-testing-and-cast.md#is-operator),, [şöyle](type-testing-and-cast.md#as-operator) | İlişkisel ve tür-test |
| [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-) | Eşitlik |
| `x & y` | [Boolean MANTıKSAL ve](boolean-logical-operators.md#logical-and-operator-) veya [BIT düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Boole MANTıKSAL XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) veya [BIT düzeyinde mantıksal XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [Boolean MANTıKSAL veya](boolean-logical-operators.md#logical-or-operator-) veya [BIT düzeyinde mantıksal or](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) | Koşullu VE |
| [x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | Koşullu VEYA |
| [x?? Iz](null-coalescing-operator.md) | Null birleşim işleci |
| [,? t: f](conditional-operator.md) | Koşullu işleç |
| [x = y](assignment-operator.md), [x + = y](arithmetic-operators.md#compound-assignment), [x-= y](arithmetic-operators.md#compound-assignment), [x * = y](arithmetic-operators.md#compound-assignment), [x/= y](arithmetic-operators.md#compound-assignment), [x% = y](arithmetic-operators.md#compound-assignment), [x & = y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^ = y](boolean-logical-operators.md#compound-assignment), [x < < = y](bitwise-and-shift-operators.md#compound-assignment), [x > > = y](bitwise-and-shift-operators.md#compound-assignment),[=>](lambda-operator.md) | Atama ve lambda bildirimi |

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [İşleçler](../../programming-guide/statements-expressions-operators/operators.md)
