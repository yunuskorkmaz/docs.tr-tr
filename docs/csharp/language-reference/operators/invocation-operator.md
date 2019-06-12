---
title: () işleci - C# başvurusu
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 032215dd2ca028af2a07fe113e7732e4d8e7ad0d
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024976"
---
# <a name="-operator-c-reference"></a>() işleci (C# Başvurusu)

Parantez `()`, yöntem veya temsilci çağırma veya cast ifadeleri kullanılır.

Ayrıca bir ifade işlemlerinde değerlendirilecek sırayı belirtmek için parantez kullanın. Daha fazla bilgi için [ayraç ekleme](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) bölümünü [işleçleri](../../programming-guide/statements-expressions-operators/operators.md) makalesi. İşleçler, öncelik düzeyine göre sıralı listesi için bkz. [ C# işleçleri](index.md).

## <a name="method-invocation"></a>Yöntem çağırma

Aşağıdaki örnek, dolgulu veya bağımsız değişkenleri, bir temsilci yöntemi çağırma gösterilmektedir:

[!code-csharp-interactive[use for invocation](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

Çağırdığınızda parantez de kullanmak bir [Oluşturucusu](../../programming-guide/classes-and-structs/constructors.md) ile bir [ `new` ](../keywords/new-operator.md) işleci.

Yöntemleri hakkında daha fazla bilgi için bkz. [yöntemleri](../../programming-guide/classes-and-structs/methods.md). Temsilciler hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/delegates/index.md).

## <a name="cast-expression"></a>Cast ifadesi

Atama ifadesi formun `(T)E` ifadenin değerine dönüştürmek için bir dönüştürme operatörünün çağırır `E` türüne `T`. Açık bir dönüştürme türünden varsa `E` türüne `T`, bir derleme zamanı hatası oluşur. Bir dönüşüm işleci tanımlama hakkında daha fazla bilgi için bkz: [açık](../keywords/explicit.md) ve [örtük](../keywords/implicit.md) anahtar sözcüğü makaleler.

Aşağıdaki örnek, sayısal türler arasında tür dönüştürme gösterilmektedir:

[!code-csharp-interactive[use for cast](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

Sayısal türler arasında önceden tanımlanmış açık dönüştürmeler hakkında daha fazla bilgi için bkz: [açık sayısal dönüşümler tablosu](../keywords/explicit-numeric-conversions-table.md).

Daha fazla bilgi için [atama ve tür dönüştürmeleri](../../programming-guide/types/casting-and-type-conversions.md) ve [dönüştürme işleçleri](../../programming-guide/statements-expressions-operators/conversion-operators.md).

## <a name="operator-overloadability"></a>İşleç overloadability

İşleç `()` aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [çağrı ifadeleri](~/_csharplang/spec/expressions.md#invocation-expressions) ve [Cast ifadeleri](~/_csharplang/spec/expressions.md#cast-expressions) bölümlerini [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
