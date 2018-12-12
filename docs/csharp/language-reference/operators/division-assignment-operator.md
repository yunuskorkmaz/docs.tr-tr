---
title: / = İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286526"
---
# <a name="-operator-c-reference"></a>/= İşleci (C# Başvurusu)

Bölme atama işleci.

Bir ifade kullanarak `/=` işleci gibi

```csharp
x /= y
```

eşdeğerdir

```csharp
x = x / y
```

dışında `x` yalnızca bir kez değerlendirilir.

[Bölme işleci](division-operator.md) `/` ilk işlenenin ikinci işleneni olarak böler. Tüm sayısal türler tarafından desteklenir.

Aşağıdaki örnek, kullanımını gösterir. `/=` işleci:

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [bölme işleci](division-operator.md) `/`, bölme atama işleci `/=` örtük olarak aşırı yüklendi. Kullanıcı tanımlı bir türe açıkça bölme atama işleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
