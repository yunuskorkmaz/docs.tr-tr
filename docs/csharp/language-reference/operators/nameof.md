---
title: işlecinin adı - C# referansı
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846278"
---
# <a name="nameof-operator-c-reference"></a>işlecinin adı (C# referansı)

İşleç, `nameof` dize sabiti olarak bir değişkenin, yazın veya üyenin adını alır:

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

Yukarıdaki örnekte de görüldüğü gibi, bir tür ve ad alanı durumunda, üretilen ad genellikle [tam olarak nitelikli](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)değildir.

Operatör `nameof` derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkisi yoktur.

Bağımsız değişken `nameof` denetimi kodunu daha koruyabilir hale getirmek için işleci kullanabilirsiniz:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

Operatör `nameof` C# 6 ve sonrası mevcuttur.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İfadeler](~/_csharplang/spec/expressions.md#nameof-expressions) Bölümü'ne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
