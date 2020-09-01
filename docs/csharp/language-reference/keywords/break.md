---
description: Break ekstresi-C# başvurusu
title: Break ekstresi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134750"
---
# <a name="break-c-reference"></a>break (C# Başvurusu)

`break`İfadesi göründüğü en yakın kapsayan döngüyü veya [Switch](./switch.md) ifadesini sonlandırır. Denetim, varsa, sonlandırılmış deyimden sonraki ifadeye geçirilir.

## <a name="example"></a>Örnek

Bu örnekte, koşullu ifade 1 ile 100 arasında bir sayı olması beklenen bir sayaç içerir; Ancak, `break` ifade 4 saydıktan sonra döngüyü sonlandırır.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Örnek

Bu örnek, `break` bir [Switch](./switch.md) deyimindeki öğesinin kullanımını gösterir.

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Girdiğinizde `4` , çıkış şöyle olacaktır:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Örnek

Bu örnekte, `break` iç içe geçmiş bir döngüyü bölmek ve denetimi dış döngüye döndürmek için ifade kullanılır. Denetim, iç içe Döngülerde _yalnızca_ bir düzey yukarı döndürülür.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Örnek

Bu örnekte, `break` ifade yalnızca döngünün her yinelemesi sırasında geçerli dalı bölmek için kullanılır. Döngünün kendisi, `break` iç içe geçmiş [anahtar](./switch.md) ifadesine ait örneklerinden etkilenmez.

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](./index.md)
- [değiştirebilirsiniz](./switch.md)
