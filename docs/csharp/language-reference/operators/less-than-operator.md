---
title: < İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: ab21e32b7609bc0c8753b42ccf8b6091bf3ad57b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286643"
---
# <a name="-operator-c-reference"></a>\< İşleci (C# Başvurusu)

"Az" ilişkisel işleç `<` döndürür `true` ilk işleneni küçükse değerinden ikinci işleneniyle `false` Aksi takdirde. Tüm sayısal ve Numaralandırma türleri desteği `<` işleci. Aynı işlenenleri için [enum](../keywords/enum.md) türü, temel alınan integral türünün karşılık gelen değerleri karşılaştırılır.

> [!NOTE]
> İlişkisel işleçler için `==`, `>`, `<`, `>=`, ve `<=`herhangi bir işlenen değil, bir sayı (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>) işleminin sonucudur `false`. Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) değeri. Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.

Aşağıdaki örnek, kullanımını gösterir. `<` işleci:

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `<` işleci. Bir tür "az" işleci aşırı `<`, ayrıca aşırı gerekir ["büyüktür" işleci](greater-than-operator.md) `>`.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [<= İşleci](less-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
