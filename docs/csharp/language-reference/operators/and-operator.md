---
title: '&amp; Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 7056d5d34a28de7aa25fe9c311327041f9ae7edf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633159"
---
# <a name="amp-operator-c-reference"></a>&amp; İşleci (C# Başvurusu)

`&` İşleci iki biçimde desteklenir: Adres bir tekli işleç veya bir ikili mantıksal işleç.

## <a name="unary-address-of-operator"></a>Birli adres işleci

Birli `&` işleci, işlenenin adresini verir. Daha fazla bilgi için [nasıl yapılır: değişkenin adresini edinme](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).

Address-of işlecini `&` gerektirir [güvenli](../keywords/unsafe.md) bağlamı.

## <a name="integer-logical-bitwise-and-operator"></a>Tamsayı mantıksal bit düzeyinde AND işleci

Tamsayı türleri için `&` hesaplar işlenenleri, mantıksal bit düzeyinde AND işleci:

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> İkili sabit dizeler önceki örnekte [sunulan C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) ve [içinde Gelişmiş C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).

Tamsayı türlerinde işlemler genellikle sabit listesi türlerinde izin verildiğinden `&` işlecini de destekler [enum](../keywords/enum.md) işlenen.

## <a name="boolean-logical-and-operator"></a>Boolean mantıksal AND işleci

İçin [bool](../keywords/bool.md) işlenenini `&` işlenenleri, mantıksal AND işleci hesaplar. Sonucu `x & y` olduğu `true` hem `x` ve `y` olan `true`. Aksi halde sonuç, `false`.

`&` İşleci, birinci işlenenin değerlendirilir olsa bile her iki işlenen de değerlendirir `false`, sonuç olmalıdır böylece `false` ikinci işlenenin değerinden bağımsız olarak. Aşağıdaki örnek, bu davranış gösterir:

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

[Koşullu AND işleci](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` ayrıca mantıksal ve işlenenleri, hesaplar, ancak değerlendirme sonucu ilk işlenen ikinci işlenende değerlendirmez `false`.

Boş değer atanabilir bool işlenenleri, davranışı için `&` işleci SQL'in üç değerli mantığı ile tutarlıdır. Daha fazla bilgi için [boş değer atanabilir Boolean mantıksal işleçler](boolean-logical-operators.md#nullable-boolean-logical-operators) bölümünü [Boolean mantıksal işleçler](boolean-logical-operators.md) makalesi.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) ikili `&` işleci. Bir ikili olduğunda `&` işleci aşırı yüklenmiş, [AND atama işleci](and-assignment-operator.md) `&=` aynı zamanda örtük olarak aşırı yüklenmiş olan.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [address-of işlecini](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) ve [mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators) bölümlerini [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [Boolean mantıksal işleçler](boolean-logical-operators.md)
- [Bit düzeyinde ve kaydırma işleçleri](bitwise-and-shift-operators.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
