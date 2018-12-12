---
title: / İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 45bcd64b60e7d13f389064faefeda815ea1f32c9
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286539"
---
# <a name="-operator-c-reference"></a>/ İşleci (C# Başvurusu)

Bölme işleci `/` ilk işlenenin ikinci işleneni olarak böler. Tüm sayısal türler, bölme işleci destekler.

## <a name="integer-division"></a>Tamsayı bölme

Tamsayı türleri sonucunu işlenenleri için `/` işleci bir tamsayı türüdür ve sayının yuvarlanmış sıfır iki işlenenden eşittir:

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#Integer)]

İki işlenenden bölümü bir kayan noktalı sayı olarak almak için kullanın `float`, `double`, veya `decimal` türü:

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#IntegerAsFloatingPoint)]

## <a name="floating-point-division"></a>Kayan nokta bölme

İçin `float`, `double`, ve `decimal` türleri, sonucunu `/` işleci, iki işlenenden bölümü:

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#FloatingPoint)]

İşlenenler ise `decimal`, başka bir işleç ne olabilir `float` ya da `double`, çünkü ne `float` ya da `double` örtük olarak dönüştürülebilir `decimal`. Açıkça dönüştürmelisiniz `float` veya `double` işleneni `decimal` türü. Sayısal türler arasında örtük dönüştürme hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../keywords/implicit-numeric-conversions-table.md).

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `/` işleci. Zaman `/` işleci aşırı yüklenmiş, [bölme atama işleci](division-assignment-operator.md) `/=` aynı zamanda örtük olarak aşırı yüklenmiş olan.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [bölme işleci](~/_csharplang/spec/expressions.md#division-operator) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [% İşleci](remainder-operator.md)
