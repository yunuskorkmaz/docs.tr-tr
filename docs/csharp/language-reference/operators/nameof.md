---
title: NameOf ifadesi-C# başvurusu
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 1bd8800a553eb9b3363da8a3b5f230caecddf223
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556416"
---
# <a name="nameof-expression-c-reference"></a>NameOf ifadesi (C# Başvurusu)

Bir `nameof` ifade, dize sabiti olarak bir değişkenin, türün veya üyenin adını üretir:

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Yukarıdaki örnekte gösterildiği gibi, bir tür ve ad alanı durumunda, oluşturulan ad genellikle [tam olarak nitelenir](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Tam [tanımlayıcılar](../tokens/verbatim.md)söz konusu olduğunda, `@` Aşağıdaki örnekte gösterildiği gibi karakter bir adın parçası değildir:

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

Bir `nameof` ifade derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkiye sahip değildir.

`nameof`Bağımsız değişken denetleme kodunun daha sürdürülebilir olması için bir ifade kullanabilirsiniz:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

`nameof`C# 6 ve sonrasında bir ifade mevcuttur.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [NameOf ifadeleri](~/_csharplang/spec/expressions.md#nameof-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
