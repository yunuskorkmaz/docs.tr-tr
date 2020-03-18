---
title: Atama işleçleri - C# başvurusu
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 420b41f586a6980d40cf1171eef00dad37bf5abf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399254"
---
# <a name="assignment-operators-c-reference"></a>Atama işleçleri (C# başvurusu)

Atama işleci, `=` sağ el operand değerini bir değişkene, bir [özelliğe](../../programming-guide/classes-and-structs/properties.md)veya sol operand tarafından verilen bir [dizinleyici](../../programming-guide/indexers/index.md) öğeye atar. Atama ifadesinin sonucu, sol operanda atanan değerdir. Sağ operand türü sol operand türü ile aynı olmalıdır veya dolaylı olarak dönüştürülebilir.

Atama işleci `=` sağ-bağşdırıcı, yani formun bir ifadesi

```csharp
a = b = c
```

olarak değerlendirilir

```csharp
a = (b = c)
```

Aşağıdaki örnek, atama işlecinin yerel bir değişken, özellik ve dizinleyici öğesi ile sol operand olarak kullanımını gösterir:

[!code-csharp-interactive[simple assignment](snippets/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>ref atama operatörü

C# 7.3 ile başlayarak, ref `= ref` atama işlecini kullanarak bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref salt yerel](../keywords/ref.md#ref-readonly-locals) değişkeni yeniden atayabilirsiniz. Aşağıdaki örnek, ref atama işlecinin kullanımını gösterir:

[!code-csharp[ref assignment operator](snippets/AssignmentOperator.cs#RefAssignment)]

Ref atama işleci söz konusu olduğunda, her iki operands aynı tip olmalıdır.

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

Bileşik atama [aritmetik](arithmetic-operators.md#compound-assignment)tarafından desteklenir , [Boolean mantıksal](boolean-logical-operators.md#compound-assignment), ve [bitwise mantıksal ve kaydırma](bitwise-and-shift-operators.md#compound-assignment) işleçleri.

## <a name="null-coalescing-assignment"></a>Null-coalescing atama

C# 8.0 ile başlayarak, null-coalescing `??=` atama işleci nin sağ operand değerini sol operand'ına atamak için kullanabilirsiniz ve `null`ancak sol operand'ın değerlendirilmesi durumunda. Daha fazla bilgi için, bkz [?? = işleçler](null-coalescing-operator.md) makale.

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür atama işlecinin [aşırı yüklenemez.](operator-overloading.md) Ancak, kullanıcı tanımlı bir tür, başka bir türe örtülü dönüştürme tanımlayabilir. Bu şekilde, kullanıcı tanımlı bir türün değeri başka bir türdeki bir değişkene, bir özelliğe veya dizinleyici öğesine atanabilir. Daha fazla bilgi için [Bkz. Kullanıcı tanımlı dönüşüm operatörleri.](user-defined-conversion-operators.md)

Kullanıcı tanımlı bir tür, bileşik atama işlecinin aşırı yüklenemeyeceğini açıkça ifade eder. Ancak, kullanıcı tanımlı bir tür bir `op`ikili `op=` işleci aşırı yüklerse , operatör, varsa, aynı zamanda örtülü olarak aşırı yüklenir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Atama işleçleri](~/_csharplang/spec/expressions.md#assignment-operators) bölümüne bakın.

Ref atama işleci `= ref`hakkında daha fazla bilgi [için, özellik teklif notuna](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [ref anahtar kelime](../keywords/ref.md)
