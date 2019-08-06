---
title: varsayılan işleç- C# başvuru
ms.custom: seodec18
description: Bir türün varsayılan değerini oluşturmak için varsayılan işleci kullanın
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 5623cb9dc3790b5bb99635c41cb3f122f4c71d8e
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68804240"
---
# <a name="default-operator-c-reference"></a>Default işleci (C# başvuru)

İşleci bir türün [varsayılan değerini](../keywords/default-values-table.md) üretir. `default` `default` İşlecin bağımsız değişkeni bir türün veya tür parametresinin adı olmalıdır.

Aşağıdaki örnek `default` işlecinin kullanımını gösterir:

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

Ayrıca, `default` anahtar sözcüğünü [ `switch` deyimdeki](../keywords/switch.md)varsayılan Case etiketi olarak da kullanabilirsiniz.

## <a name="default-literal"></a>Varsayılan sabit değer

7,1 ' C# den başlayarak, derleyicinin ifade türünü `default` çıkardığı zaman bir türün varsayılan değerini oluşturmak için değişmez değeri kullanabilirsiniz. Değişmez değer ifadesi, çıkarılan tür `T` olan `default(T)` ifadesiyle aynı değeri üretir. `default` Aşağıdaki durumlardan herhangi birinde `default` değişmez değeri kullanabilirsiniz:

- Bir değişkenin atamasında veya başlatılmasında.
- İsteğe bağlı bir yöntem parametresi için varsayılan değer bildiriminde.
- Bir bağımsız değişken değeri sağlamak için bir yöntem çağrısında.
- Bir `return` deyimde veya bir ifade ile ifade olarak ifade olarak.

Aşağıdaki örnek, `default` değişmez değerin kullanımını gösterir:

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [varsayılan değer ifadeleri](~/_csharplang/spec/expressions.md#default-value-expressions) bölümüne bakın.

`default` Değişmez değer hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Varsayılan değerler tablosu](../keywords/default-values-table.md)
