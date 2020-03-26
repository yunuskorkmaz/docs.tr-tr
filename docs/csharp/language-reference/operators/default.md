---
title: varsayılan değer ifadeleri - C# başvurusu
description: Bir türün varsayılan değerini elde etmek için varsayılan değer ifadelerini kullanma
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 2adfd8d24066e9dad50c3c18407d3ade71b4b68e
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507184"
---
# <a name="default-value-expressions-c-reference"></a>varsayılan değer ifadeleri (C# başvurusu)

Varsayılan değer ifadesi, bir türün [varsayılan değerini](../builtin-types/default-values.md) üretir. İki tür varsayılan değer ifadesi vardır: [varsayılan işleç](#default-operator) çağrısı ve [varsayılan bir literal](#default-literal).

`default` Ayrıca bir [ `switch` deyim](../keywords/switch.md)içinde varsayılan durum etiketi olarak anahtar kelime kullanın.

## <a name="default-operator"></a>default işleçi

Aşağıdaki örnekte `default` görüldüğü gibi, işlecibağımsız değişkenbir tür veya tür parametresi adı olmalıdır:

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

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
