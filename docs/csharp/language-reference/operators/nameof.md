---
title: NameOf ifadesi-C# başvurusu
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: d71acf0cf7d5cdcfa5310455af2120fa1f82d567
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135925"
---
# <a name="nameof-expression-c-reference"></a>NameOf ifadesi (C# Başvurusu)

Bir `nameof` ifade, dize sabiti olarak bir değişkenin, türün veya üyenin adını üretir:

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Yukarıdaki örnekte gösterildiği gibi, bir tür ve ad alanı durumunda, oluşturulan ad genellikle [tam olarak nitelenir](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Tam [tanımlayıcılar](../tokens/verbatim.md)söz konusu olduğunda, aşağıdaki örnekte `@` gösterildiği gibi karakter bir adın parçası değildir:

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

Bir `nameof` ifade derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkiye sahip değildir.

Bağımsız değişken denetleme kodunun `nameof` daha sürdürülebilir olması için bir ifade kullanabilirsiniz:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

C# `nameof` 6 ve sonrasında bir ifade mevcuttur.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [NameOf ifadeleri](~/_csharplang/spec/expressions.md#nameof-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
