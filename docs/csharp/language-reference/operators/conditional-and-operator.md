---
title: '&amp;&amp; İşleci (C# Başvurusu)'
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: d0e6d9a5aedc7dc87393e3dea070bf442b3268dc
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "43529241"
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; İşleci (C# Başvurusu)

Koşullu mantıksal AND işlecinin `&&`, "kısa devre" mantıksal AND işleci, hesaplar, mantıksal AND olarak da bilinir, [bool](../keywords/bool.md) işlenen. Sonucu `x && y` olduğu `true` hem `x` ve `y` vermesi `true`. Aksi halde sonuç, `false`. Birinci işlenenin değerlendirilirse `false`, ikinci işlenenin değerlendirilmez ve işlemin sonucu olan `false`. Aşağıdaki örnek, bu davranış gösterir:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

[Mantıksal AND işlecinin](and-operator.md) `&` Ayrıca, mantıksal ve hesaplar, `bool` işlenenler, ancak her iki işlenen de her zaman değerlendirilir.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür koşullu mantıksal AND işleci aşırı yüklenemez. Ancak, kullanıcı tanımlı bir tür aşırı [mantıksal AND](and-operator.md), [true](../keywords/true-operator.md), ve [false](../keywords/false-operator.md) işleçleri belirli bir şekilde `&&` işlemi değerlendirmesi yapılamıyor için işlenen türü. Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [|| işleci](conditional-or-operator.md)
- [! işleci](logical-negation-operator.md)
- [& işleci](and-operator.md)
