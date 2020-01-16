---
title: varsayılan işleç- C# başvuru
description: Bir türün varsayılan değerini oluşturmak için varsayılan işleci kullanın
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 651c4698514aee8cf4dab75ea32c98493e19a30b
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964616"
---
# <a name="default-operator-c-reference"></a>Default işleci (C# başvuru)

`default` işleci, bir türün [varsayılan değerini](../builtin-types/default-values.md) üretir. `default` işlecinin bağımsız değişkeni bir türün veya tür parametresinin adı olmalıdır.

Aşağıdaki örnek `default` işlecinin kullanımını gösterir:

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

Ayrıca, bir [`switch` ifadesinde](../keywords/switch.md)varsayılan Case etiketi olarak `default` anahtar sözcüğünü kullanırsınız.

## <a name="default-literal"></a>Varsayılan sabit değer

7,1 ' C# den başlayarak, derleyici ifade türünü çıkarsdığı zaman bir türün varsayılan değerini oluşturmak için `default` değişmez değerini kullanabilirsiniz. `default` değişmez ifadesi, `T` çıkarılan tür olduğu `default(T)` ifadesiyle aynı değeri üretir. `default` değişmez değerini aşağıdaki durumlardan herhangi birinde kullanabilirsiniz:

- Bir değişkenin atamasında veya başlatılmasında.
- [İsteğe bağlı bir yöntem parametresi](../../methods.md#optional-parameters-and-arguments)için varsayılan değer bildiriminde.
- Bir bağımsız değişken değeri sağlamak için bir yöntem çağrısında.
- Bir [`return` deyiminde](../keywords/return.md) veya [ifade-Bodied üye](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)içindeki bir ifade olarak.

Aşağıdaki örnek `default` değişmez değerinin kullanımını gösterir:

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [varsayılan değer ifadeleri](~/_csharplang/spec/expressions.md#default-value-expressions) bölümüne bakın.

`default` değişmez değeri hakkında daha fazla bilgi için bkz. [özellik teklifi notunun](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [C# Türlerin varsayılan değerleri](../builtin-types/default-values.md)
- [.NET 'teki genel türler](../../../standard/generics/index.md)
