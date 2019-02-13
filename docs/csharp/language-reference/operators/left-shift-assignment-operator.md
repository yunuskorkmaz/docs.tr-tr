---
title: << = işleci - C# başvurusu
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219457"
---
# <a name="-operator-c-reference"></a>\<\<= işleci (C# Başvurusu)

Sola kaydırma atama işleci.

Bir ifade kullanarak `<<=` işleci gibi

```csharp
x <<= y
```

eşdeğerdir

```csharp
x = x << y
```

dışında `x` yalnızca bir kez değerlendirilir.

[ `<<` İşleci](left-shift-operator.md) ilk işleneni sol tarafından ikinci işleneni tarafından tanımlanan bit sayısı kadar kaydırır.

Aşağıdaki örnek, kullanımını gösterir. `<<=` işleci:

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [ `<<` işleci](left-shift-operator.md), sola kaydırma atama işleci `<<=` örtük olarak aşırı yüklendi. Kullanıcı tanımlı bir türe açıkça sola kaydırma atama işleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
