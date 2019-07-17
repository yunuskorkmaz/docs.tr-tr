---
title: nameof işlecinin - C# başvurusu
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 945a8a8ff6d96cb505fa10e85c21a93347661a23
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238692"
---
# <a name="nameof-operator-c-reference"></a>nameof işlecinin (C# Başvurusu)

`nameof` İşleci bir değişken, türü veya dize sabiti olarak üye adını alır:

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

Bir tür ve ad alanı, söz konusu olduğunda yukarıdaki örnekte gösterildiği gibi üretilen adı genellikle değil [tam](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

`nameof` İşleci derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkisi olmaz.

Kullanabileceğiniz `nameof` bağımsız değişken denetimi kod daha sürdürülebilir hale getirmek için işleç:

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

`nameof` İşleci kullanılabilir C# 6 ve üzeri.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [Nameof ifadeleri](~/_csharplang/spec/expressions.md#nameof-expressions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
