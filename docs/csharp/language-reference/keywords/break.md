---
title: kesme deyimi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713761"
---
# <a name="break-c-reference"></a>break (C# Başvurusu)

İfade, `break` göründüğü en yakın çevreleyen döngü veya [anahtar](./switch.md) deyimini sonlandırır. Denetim, varsa sonlandırılan deyimi izleyen bildirime aktarılır.

## <a name="example"></a>Örnek

Bu örnekte, koşullu deyim 1 ile 100 arasında sayması gereken bir sayaç içerir; ancak, `break` deyim 4 sayar sonra döngü sona erer.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Örnek

Bu örnek, bir `break` [anahtar](./switch.md) deyiminin kullanımını gösterir.

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Girdiyseniz, `4`çıktı:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Örnek

Bu örnekte, `break` deyim iç içe bir döngüden çıkmak ve denetimi dış döngüye döndürmek için kullanılır. Denetim iç içe döngülerde _yalnızca_ bir seviye yukarı döndürülür.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Örnek

Bu örnekte, `break` deyim yalnızca döngüher yineleme sırasında geçerli dalı kırmak için kullanılır. Döngünün kendisi iç içe anahtar `break` deyimine ait [switch](./switch.md) olan örneklerden etkilenmez.

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Anahtarı](./switch.md)
