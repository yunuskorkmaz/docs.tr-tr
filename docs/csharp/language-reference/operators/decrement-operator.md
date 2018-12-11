---
title: -- İşleci (C# Başvurusu)
ms.date: 11/26/2018
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 0858321d6fe192a55bc548f169c558542238a981
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153347"
---
# <a name="---operator-c-reference"></a>-- İşleci (C# Başvurusu)

Birli azaltma işleci `--` azaltır işleneniyle 1. İki biçimde desteklenir: sonek azaltma işlecinin `x--`ve önek azaltma işleci `--x`.

## <a name="postfix-decrement-operator"></a>Sonek azaltma işleci

Sonucu `x--` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixDecrement)]

## <a name="prefix-decrement-operator"></a>Önek azaltma işleci

Sonucu `--x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixDecrement)]

## <a name="remarks"></a>Açıklamalar

Azaltma işleci tüm önceden tanımlanan [tam sayı türleri](../keywords/integral-types-table.md) (dahil olmak üzere [char](../keywords/char.md) türü), [kayan nokta türleri](../keywords/floating-point-types-table.md)ve tüm [enum](../keywords/enum.md) yazın.

Azaltma işlecinin işleneni, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `--` işleci.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [sonek arttırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) ve [önek arttırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) bölümlerini [ C# dilbelirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [++ İşleci](increment-operator.md)
- [Nasıl yapılır: işaretçileri artırma ve azaltma](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
