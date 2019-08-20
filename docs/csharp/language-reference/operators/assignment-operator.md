---
title: = işleci- C# başvuru
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: f30b48fc6bd1e896658a7234a58409ea9a0f5e6f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601948"
---
# <a name="-operator-c-reference"></a>= işleci (C# başvuru)

Atama işleci `=` , sağ işleneninin değerini bir değişkene, [özelliğe](../../programming-guide/classes-and-structs/properties.md)veya kendi sol işleneni tarafından verilen bir [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesine atar. Atama ifadesinin sonucu, sol işlenene atanan değerdir. Sağ işlenenin türü, sol işlenenin türüyle aynı veya örtülü olarak dönüştürülebilir olmalıdır.

Atama işleci, doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi

```csharp
a = b = c
```

şöyle değerlendirilir

```csharp
a = (b = c)
```

Aşağıdaki örnek, bir yerel değişken, bir özellik ve bir Dizin Oluşturucu öğesi olan atama işlecinin kullanımını sol işlenen olarak gösterir:

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>ref atama işleci

7,3 ' C# den başlayarak ref atama işlecini `= ref` kullanarak bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkenini yeniden atayabilirsiniz. Aşağıdaki örnek, ref atama işlecinin kullanımını gösterir:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

Ref atama operatörü durumunda, her iki işleneninin türü aynı olmalıdır.

Daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

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

Bileşik atama [Aritmetik](arithmetic-operators.md#compound-assignment), [Boole mantıksal](boolean-logical-operators.md#compound-assignment)ve [bit düzeyinde mantıksal ve kaydırma](bitwise-and-shift-operators.md#compound-assignment) işleçleri tarafından desteklenir.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür atama işlecini aşırı yükleyemez. Ancak, Kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilir. Bu şekilde, Kullanıcı tanımlı bir türün değeri bir değişkene, özelliğe veya başka bir türün Dizin Oluşturucu öğesine atanabilir. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](../language-specification/index.md) [atama işleçleri](~/_csharplang/spec/expressions.md#assignment-operators) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [ref anahtar sözcüğü](../keywords/ref.md)
