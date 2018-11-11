---
title: '&amp; İşleci (C# Başvurusu)'
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: a8f76ded0ef9f8e8099838a903d90f1695324991
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "43510984"
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

[Koşullu AND işleci](conditional-and-operator.md) `&&` ayrıca mantıksal hesaplar ve yalnızca ilk işlenen değerlendirilirse işlenenleri ancak ikinci işlenenin değerlendirilir `true`.

Boş değer atanabilir bool işlenenleri, davranışı için `&` işleci SQL'in üç değerli mantığı ile tutarlıdır. Daha fazla bilgi için [bool? türü](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) ikili `&` işleci. Bir ikili olduğunda `&` işleci aşırı yüklenmiş, [AND atama işleci](and-assignment-operator.md) `&=` aynı zamanda örtük olarak aşırı yüklenmiş olan.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [address-of işlecini](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) ve [mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators) bölümlerini [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [| işleci](or-operator.md)
- [^ işleci](xor-operator.md)
- [~ işleci](bitwise-complement-operator.md)
- [& & işleci](conditional-and-operator.md)
