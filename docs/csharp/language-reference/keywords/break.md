---
title: Break ekstresi- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713761"
---
# <a name="break-c-reference"></a>break (C# Başvurusu)

`break` ifadesi göründüğü en yakın kapsayan döngüyü veya [Switch](./switch.md) ifadesini sonlandırır. Denetim, varsa, sonlandırılmış deyimden sonraki ifadeye geçirilir.

## <a name="example"></a>Örnek

Bu örnekte, koşullu ifade 1 ile 100 arasında bir sayı olması beklenen bir sayaç içerir; Ancak, `break` ifade döngüyü 4 saydan sonra sonlandırır.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Örnek

Bu örnek, bir [Switch](./switch.md) deyimindeki `break` kullanımını gösterir.

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

`4`girdiyseniz, çıkış şöyle olur:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Örnek

Bu örnekte `break` deyimleri, iç içe geçmiş bir döngüyü bölmek için kullanılır ve denetimin dıştaki döngüye dönmesini sağlar. Denetim, iç içe Döngülerde _yalnızca_ bir düzey yukarı döndürülür.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Örnek

Bu örnekte, `break` deyimleri yalnızca döngünün her yinelemesi sırasında geçerli dalı bölmek için kullanılır. Döngünün kendisi, iç içe geçmiş [anahtar](./switch.md) ifadesine ait `break` örneklerinden etkilenmez.

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [switch](./switch.md)
