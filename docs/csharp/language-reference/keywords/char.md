---
title: Char anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771796"
---
# <a name="char-c-reference"></a>Char (C# başvuru)

@No__t_0 Type anahtar sözcüğü, bir Unicode UTF-16 karakteri temsil eden .NET <xref:System.Char?displayProperty=nameWithType> yapı türü için bir diğer addır:

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000-U + FFFF|16 bit|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Sabit değerler

@No__t_0 türünün sabitleri, karakter sabit değerleri, onaltılık kaçış dizisi veya Unicode temsili olarak yazılabilir. Ayrıca, bir integral karakter kodunu karşılık gelen `char` değerine de çevirebilirsiniz. Aşağıdaki örnekte, `char` dizisinin dört öğesi aynı karakterle `X` başlatılır:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Dönüşümler

@No__t_0 türü örtük olarak şu [integral](../builtin-types/integral-numeric-types.md) türlerine dönüştürülebilir: `ushort`, `int`, `uint`, `long` ve `ulong`. Ayrıca yerleşik [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türlerine örtülü olarak dönüştürülebilir: `float`, `double` ve `decimal`. @No__t_0, `byte` ve `short` integral türlerine açıkça dönüştürülebilir.

Diğer türlerden `char` türüne örtük dönüştürme yok. Ancak, herhangi bir [integral](../builtin-types/integral-numeric-types.md) veya [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türü `char` açıkça dönüştürülebilir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Integral türler](~/_csharplang/spec/types.md#integral-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# anahtar sözcükleri](./index.md)
- [Yerleşik türler tablosu](./built-in-types-table.md)
- [Dizeler](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
