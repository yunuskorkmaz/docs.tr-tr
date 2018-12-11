---
title: '&amp;= İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 223d2f30ee77457e1f9d5304ec299517932499d0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237031"
---
# <a name="amp-operator-c-reference"></a>&amp;= İşleci (C# Başvurusu)

AND atama işleci.

Bir ifade kullanarak `&=` işleci gibi

```csharp
x &= y
```

eşdeğerdir

```csharp
x = x & y
```

dışında `x` yalnızca bir kez değerlendirilir.

Tamsayı işlenenleri için [ `&` işleci](and-operator.md) hesaplar. bit düzeyinde mantıksal AND işlenenleri için; [bool](../keywords/bool.md) işlenen, mantıksal ve işlenenleri, hesaplar.

Aşağıdaki örnek, kullanımını gösterir. `&=` işleci:

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [ `&` işleci](and-operator.md), AND atama işleci `&=` örtük olarak aşırı yüklendi. Kullanıcı tanımlı bir türe açıkça AND atama işleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
