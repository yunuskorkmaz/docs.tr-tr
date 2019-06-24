---
title: = işleci - C# başvurusu
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: ef9c9bab5c1cebb06edf934254507180e2197349
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306561"
---
# <a name="-operator-c-reference"></a>= işleci (C# Başvurusu)

Atama işleci `=` , sağ işleneninin değeri bir değişkene atar bir [özelliği](../../programming-guide/classes-and-structs/properties.md), veya bir [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) , sol işlenen tarafından belirtilen öğe. Atama ifadesi sol işlenen için atanan değer sonucudur. Sağ işleneninin türü, sol işlenen veya örtük olarak dönüştürülebilir ona türü ile aynı olmalıdır.

Atama işleci sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu

```csharp
a = b = c
```

olarak değerlendirilir

```csharp
a = (b = c)
```

Aşağıdaki örnek, sol işlenen olarak yerel bir değişken, bir özellik ve dizin oluşturucu öğenin atama işlecinin kullanımını gösterir:

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>başvuru atama işleci

İle başlayarak C# 7.3, başvuru atama işleci kullanabileceğiniz `= ref` yeniden atamak için bir [ref yerel](../keywords/ref.md#ref-locals) veya [salt okunur yerel başvuru](../keywords/ref.md#ref-readonly-locals) değişkeni. Aşağıdaki örnek, başvuru atama işlecinin kullanımını gösterir:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

Başvuru atama işleci söz konusu olduğunda, her iki işlenenleri türünü aynı olmalıdır.

Daha fazla bilgi için [özellik teklif Not](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

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

Tarafından desteklenen bileşik atama [aritmetik](arithmetic-operators.md#compound-assignment), [Boolean mantıksal](boolean-logical-operators.md#compound-assignment), ve [bit düzeyinde mantıksal and -shift ile](bitwise-and-shift-operators.md#compound-assignment) işleçleri.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür atama işleci aşırı yüklenemez. Ancak, kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilirsiniz. Bu şekilde, bir değişken, bir özellik veya dizin oluşturucu öğenin başka bir tür için kullanıcı tanımlı bir tür değeri atanabilir. Daha fazla bilgi için [örtük](../keywords/implicit.md) anahtar sözcüğü makalesi.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [atama işleçleri](~/_csharplang/spec/expressions.md#assignment-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [ref anahtar sözcüğü](../keywords/ref.md)
