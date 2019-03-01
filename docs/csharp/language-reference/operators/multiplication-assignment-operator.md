---
title: '* = İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967392"
---
# <a name="-operator-c-reference"></a>\*= İşleci (C# Başvurusu)

Çarpma atama işleci.

Bir ifade kullanarak `*=` işleci gibi

```csharp
x *= y
```

eşdeğerdir

```csharp
x = x * y
```

dışında `x` yalnızca bir kez değerlendirilir.

Sayısal türlerin [ \* işleci](multiplication-operator.md) işlenenleri çarpımını hesaplar.

Aşağıdaki örnek, kullanımını gösterir. `*=` işleci:

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [çarpma işleci](multiplication-operator.md) `*`, çarpma atama işleci `*=` örtük olarak aşırı yüklendi. Kullanıcı tanımlı bir türe açıkça çarpma atama işleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
