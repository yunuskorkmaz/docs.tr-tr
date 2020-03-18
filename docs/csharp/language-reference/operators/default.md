---
title: varsayılan işleç - C# referans
description: Bir türün varsayılan değerini üretmek için varsayılan işleci kullanma
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399485"
---
# <a name="default-operator-c-reference"></a>varsayılan işleç (C# başvurusu)

İşleç `default` bir türün [varsayılan değerini](../builtin-types/default-values.md) üretir. Işleci için `default` bağımsız değişken bir tür veya tür parametresi adı olmalıdır.

Aşağıdaki örnek, işleç `default` kullanımını gösterir:

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

`default` Ayrıca bir [ `switch` deyim](../keywords/switch.md)içinde varsayılan durum etiketi olarak anahtar kelime kullanın.

## <a name="default-literal"></a>varsayılan edebi

C# 7.1 ile başlayarak, `default` derleyici ifade türünü çıkarabildiği bir türün varsayılan değerini üretmek için literal'ı kullanabilirsiniz. Literal `default` ifade, çıkarılan türdeki `default(T)` ifadeyle `T` aynı değeri üretir. Aşağıdaki durumlardan `default` herhangi birinde gerçek kullanımı yapabilirsiniz:

- Bir değişkenin atamasında veya başlatılmasında.
- İsteğe bağlı yöntem [parametresi](../../methods.md#optional-parameters-and-arguments)için varsayılan değer bildiriminde .
- Bir yöntemde bir bağımsız değişken değeri sağlamak için çağrı.
- [ `return` İfade](../keywords/return.md) de veya [ifade gövdeli](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)bir üyede ifade olarak .

Aşağıdaki `default` örnek, edebi kullanımı gösterir:

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Varsayılan değer ifadeleri](~/_csharplang/spec/expressions.md#default-value-expressions) bölümüne bakın.

`default` Gerçek hakkında daha fazla bilgi için özellik teklifi [notuna](~/_csharplang/proposals/csharp-7.1/target-typed-default.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [C# türlerinin varsayılan değerleri](../builtin-types/default-values.md)
- [.NET içindeki Genel Türler](../../../standard/generics/index.md)
