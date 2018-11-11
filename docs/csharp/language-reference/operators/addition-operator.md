---
title: + İşleci (C# Başvurusu)
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 27ea47d698b20f112880750ec0bc931f1917f142
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50192310"
---
# <a name="-operator-c-reference"></a>+ İşleci (C# Başvurusu)

`+` İşleci iki biçimde desteklenir: bir birli artı işleci veya bir ikili Toplama işleci.

## <a name="unary-plus-operator"></a>Tekli artı işleci

Birli `+` işleci, işlenenin değerini döndürür. Tüm sayısal türler tarafından desteklenir.

## <a name="numeric-addition"></a>Sayısal toplama

Sayısal türlerin `+` işleci işlenenleri toplamını hesaplar:

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

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
- [Nasıl yapılır: Birden Çok Dizeyi Birleştirme](../../how-to/concatenate-multiple-strings.md)
- [Temsilciler](../../programming-guide/delegates/index.md)
- [Checked ve unchecked](../keywords/checked-and-unchecked.md)
