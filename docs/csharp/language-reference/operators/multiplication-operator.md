---
title: '* Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: a5e120d26614f1e38cc2f2db02949552140b594e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689092"
---
# <a name="-operator-c-reference"></a>* işleci (C# Başvurusu)

`*` İşleci iki biçimde desteklenir: Birli işaretçi yöneltme işleci veya bir ikili çarpma işleci.

## <a name="pointer-indirection-operator"></a>İşaretçi yöneltme işleci

Birli kullanın `*` işleci bir işlenen bir işaretçi türünün işaret ettiği değişken elde edilir. Daha fazla bilgi için [nasıl yapılır: işaretçi değişkeninin değerini edinme](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).

İşaretçi yöneltme işleci `*` gerektirir [güvenli](../keywords/unsafe.md) bağlamı.

## <a name="multiplication-operator"></a>Çarpma işleci

Sayısal türlerin `*` işleci işlenenleri çarpımını hesaplar:

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) bir ikili `*` işleci. Bir ikili olduğunda `*` işleci aşırı yüklenmiş, [çarpma atama işleci](multiplication-assignment-operator.md) `*=` aynı zamanda örtük olarak aşırı yüklenmiş olan.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [işaretçi yöneltmesi](~/_csharplang/spec/unsafe-code.md#pointer-indirection) ve [çarpma işleci](~/_csharplang/spec/expressions.md#multiplication-operator) bölümlerini [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)