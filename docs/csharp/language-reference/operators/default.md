---
title: Varsayılan değer ifadeleri-C# başvurusu
description: Bir türün varsayılan değerini elde etmek için varsayılan değer ifadelerini kullanın
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 92ad8e919567e1f9f57e6875d53c4055eb960829
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997644"
---
# <a name="default-value-expressions-c-reference"></a>Varsayılan değer ifadeleri (C# Başvurusu)

Varsayılan değer ifadesi bir türün [varsayılan değerini](../builtin-types/default-values.md) üretir. İki tür varsayılan değer ifadesi vardır: [varsayılan işleç](#default-operator) çağrısı ve [varsayılan bir sabit](#default-literal)değer.

Ayrıca, `default` anahtar sözcüğünü bir [ `switch` deyimindeki](../keywords/switch.md)varsayılan Case etiketi olarak da kullanabilirsiniz.

## <a name="default-operator"></a>default işleçi

`default`Aşağıdaki örnekte gösterildiği gibi, işlecin bağımsız değişkeni bir tür veya tür parametresinin adı olmalıdır:

[!code-csharp-interactive[default of T](snippets/shared/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a>Varsayılan sabit değer

C# 7,1 ' den başlayarak, `default` derleyicinin ifade türünü çıkardığı zaman bir türün varsayılan değerini oluşturmak için değişmez değeri kullanabilirsiniz. `default`Değişmez değer ifadesi, `default(T)` çıkarılan tür olan ifadesiyle aynı değeri üretir `T` . `default`Aşağıdaki durumlardan herhangi birinde değişmez değeri kullanabilirsiniz:

- Bir değişkenin atamasında veya başlatılmasında.
- [İsteğe bağlı bir yöntem parametresi](../../methods.md#optional-parameters-and-arguments)için varsayılan değer bildiriminde.
- Bir bağımsız değişken değeri sağlamak için bir yöntem çağrısında.
- Bir deyimde [ `return` veya bir](../keywords/return.md) [ifade ile](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)ifade olarak ifade olarak.

Aşağıdaki örnek, `default` değişmez değerin kullanımını gösterir:

[!code-csharp-interactive[default literal](snippets/shared/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [varsayılan değer ifadeleri](~/_csharplang/spec/expressions.md#default-value-expressions) bölümüne bakın.

Değişmez değer hakkında daha fazla bilgi için `default` bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [C# türlerinin varsayılan değerleri](../builtin-types/default-values.md)
- [.NET içindeki Genel Türler](../../../standard/generics/index.md)
