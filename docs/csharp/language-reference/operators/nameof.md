---
title: ifade adı - C# referansı
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507145"
---
# <a name="nameof-expression-c-reference"></a>ifade adı (C# referansı)

Bir `nameof` ifade, dize sabiti olarak bir değişkenin, yazın veya üyenin adını üretir:

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Yukarıdaki örnekte de görüldüğü gibi, bir tür ve ad alanı durumunda, üretilen ad genellikle [tam olarak nitelikli](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)değildir.

Bir `nameof` ifade derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkisi yoktur.

Bağımsız değişken `nameof` denetleme kodunu daha koruyabilir hale getirmek için bir ifade kullanabilirsiniz:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

C# `nameof` 6 ve sonraki bir ifade kullanılabilir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İfadeler](~/_csharplang/spec/expressions.md#nameof-expressions) Bölümü'ne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
