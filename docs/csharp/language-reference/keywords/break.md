---
title: Break ekstresi- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 77d18d12cd0fabb26906a5b58dc3939da6214a29
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602251"
---
# <a name="break-c-reference"></a>break (C# Başvurusu)

İfadesi göründüğü en yakın kapsayan döngüyü veya switch ifadesini sonlandırır. [](./switch.md) `break` Denetim, varsa, sonlandırılmış deyimden sonraki ifadeye geçirilir.

## <a name="example"></a>Örnek

Bu örnekte, koşullu ifade 1 ile 100 arasında bir sayı olması beklenen bir sayaç içerir; Ancak, `break` ifade 4 saydıktan sonra döngüyü sonlandırır.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Örnek

Bu örnekte, `break` iç içe geçmiş bir döngüyü bölmek ve denetimi dış döngüye döndürmek için ifade kullanılır.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Örnek

Bu örnek, bir [Switch](./switch.md) deyimindeki `break` öğesinin kullanımını gösterir.

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Girdiğinizde `4`, çıkış şöyle olacaktır:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [switch](./switch.md)
