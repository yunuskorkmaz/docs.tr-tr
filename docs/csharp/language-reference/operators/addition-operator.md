---
title: + Operator - C# başvurusu
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 0f04ba837f9c03107acd0b2174cbd07c14a8c213
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504476"
---
# <a name="-operator-c-reference"></a>+ İşleci (C# Başvurusu)

`+` İşleci iki biçimde desteklenir: bir birli artı işleci veya bir ikili Toplama işleci.

## <a name="unary-plus-operator"></a>Tekli artı işleci

Birli `+` işleci, işlenenin değerini döndürür. Tüm sayısal türler tarafından desteklenir.

## <a name="numeric-addition"></a>Sayısal toplama

Sayısal türlerin `+` işleci işlenenleri toplamını hesaplar:

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

Aritmetik işleçler hakkında daha fazla bilgi için bkz: [aritmetik işleçler](arithmetic-operators.md).

## <a name="string-concatenation"></a>Dize birleştirme

Bir veya iki işlenenin türünde olduğunda [dize](../keywords/string.md), `+` işleci, işlenenleri dize temsillerini art arda ekler:

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

İle başlayarak C# 6, [dize ilişkilendirme](../tokens/interpolated.md) biçim dizeleri için daha kolay bir yol sağlar:

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Temsilci birleşimi

İçin [temsilci](../keywords/delegate.md) türleri `+` işleci döndüren yeni bir temsilci örneği, çağrılır, birinci işlenenin çağırır ve ardından ikinci işlenenin çağırır. İşlenenden ise `null`, `+` işleci, başka bir işlenenin değerini döndürür (Ayrıca olabilen `null`). Aşağıdaki örnek, temsilciler ne birleştirilebilir gösterir `+` işleci:

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

Temsilci türleri hakkında daha fazla bilgi için bkz: [Temsilciler](../../programming-guide/delegates/index.md).

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) tekli veya ikili `+` işleçleri. Bir ikili olduğunda `+` işleci aşırı yüklenmiş, [toplama atama işleci](addition-assignment-operator.md) `+=` aynı zamanda örtük olarak aşırı yüklenmiş olan.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [birli artı işleci](~/_csharplang/spec/expressions.md#unary-plus-operator) ve [Toplama işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerini [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [Dize ilişkilendirme](../tokens/interpolated.md)
- [Nasıl yapılır: Birden çok dizeyi birleştirme](../../how-to/concatenate-multiple-strings.md)
- [Temsilciler](../../programming-guide/delegates/index.md)
- [Checked ve unchecked](../keywords/checked-and-unchecked.md)
