---
title: '>>= işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220919"
---
# <a name="-operator-c-reference"></a>>> = işleci (C# Başvurusu)

Sağa kaydırma atama işleci.

Bir ifade kullanarak `>>=` işleci gibi

```csharp
x >>= y
```

eşdeğerdir

```csharp
x = x >> y
```

dışında `x` yalnızca bir kez değerlendirilir.

[ `>>` İşleci](right-shift-operator.md) ilk işlenenin ikinci işleneni tarafından tanımlanan bit sayısına göre sağa kaydırır.

Aşağıdaki örnek, kullanımını gösterir. `>>=` işleci:

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [ `>>` işleci](right-shift-operator.md), sağa kaydırma atama işleci `>>=` örtük olarak aşırı yüklendi. Kullanıcı tanımlı bir türe açıkça sağa kaydırma atama işleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C#işleçleri](index.md)