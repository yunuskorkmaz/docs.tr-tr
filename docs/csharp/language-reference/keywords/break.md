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
ms.openlocfilehash: 2628da73364cf94a52e2862d349243c100d4afaf
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179929"
---
# <a name="break-c-reference"></a>Break (C# başvuru)

@No__t-0 ifadesi, göründüğü en yakın kapsayan döngüyü veya [Switch](./switch.md) ifadesini sonlandırır. Denetim, varsa, sonlandırılmış deyimden sonraki ifadeye geçirilir.

## <a name="example"></a>Örnek

Bu örnekte, koşullu ifade 1 ile 100 arasında bir sayı olması beklenen bir sayaç içerir; Ancak `break` ifadesinde, döngü 4 saydıktan sonra sonlandırılır.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Örnek

Bu örnek, [Switch](./switch.md) ifadesinde `break` ' ın kullanımını gösterir.

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

@No__t-0 girdiyseniz, çıkış şöyle olur:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Örnek

Bu örnekte, `break`, iç içe geçmiş bir döngüyü bölmek için kullanılır ve denetimin dıştaki döngüye dönmesini sağlar. Denetim, iç içe Döngülerde _yalnızca_ bir düzey yukarı döndürülür.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Örnek

Bu örnekte, `break` deyimleri yalnızca döngünün her yinelemesi sırasında geçerli dalı bölmek için kullanılır. Döngünün kendisi, iç içe geçmiş [anahtar](./switch.md) ifadesine ait olan `break` örneklerinden etkilenmez.

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>C#dil belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C#Programlama Kılavuzu](../../programming-guide/index.md)
- [C#Lerimi](./index.md)
- [değiştirebilirsiniz](./switch.md)
