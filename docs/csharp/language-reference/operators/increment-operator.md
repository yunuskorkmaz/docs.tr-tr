---
title: ++ İşleci (C# Başvurusu)
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: b29f4f1ab00c0f8026f118cb72b090e3b728bfc5
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2018
ms.locfileid: "48030476"
---
# <a name="-operator-c-reference"></a>++ İşleci (C# Başvurusu)

Tekli artırma işleci `++` işleneniyle 1 artar. İki biçimde desteklenir: sonek artırma işlecini `x++`ve önek artırma işleci `++x`.

## <a name="postfix-increment-operator"></a>Sonek artırma işleci

Sonucu `x++` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a>Önek artırma işleci

Sonucu `++x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a>Açıklamalar

Artırım işleci tüm önceden tanımlanan [tam sayı türleri](../keywords/integral-types-table.md) (dahil olmak üzere [char](../keywords/char.md) türü), [kayan nokta türleri](../keywords/floating-point-types-table.md)ve tüm [enum](../keywords/enum.md) yazın.

Artırma işlecinin işleneni, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `++` işleci.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [sonek arttırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) ve [önek arttırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) bölümlerini [ C# dilbelirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [-- İşleci](decrement-operator.md)
- [Nasıl yapılır: işaretçileri artırma ve azaltma](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
