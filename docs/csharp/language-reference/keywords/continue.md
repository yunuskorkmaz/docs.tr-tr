---
description: Continue bildirisi-C# başvurusu
title: Continue bildirisi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 6c70934c3b861e1a1433e5c0b95bb32e9d717c53
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877658"
---
# <a name="continue-c-reference"></a>continue (C# Başvurusu)

`continue`İfadesi, denetimi içinde göründüğü [while](./while.md), [Do](./do.md), [for](./for.md)veya [foreach](./foreach-in.md) deyimlerinin bir sonraki yinelemesine geçirir.

## <a name="example"></a>Örnek

Bu örnekte, bir sayaç 1 ile 10 arasında bir sayı olarak başlatılır. `continue`Deyimi ifadesiyle birlikte kullanarak `(i < 9)` , gövde sonu arasındaki deyimler, `continue` 9 ' `for` dan küçük olan yinelemelerde atlanır `i` . Döngünün son iki tekrarda `for` (i = = 9 ve i = = 10), `continue` ifade yürütülmez ve değeri `i` konsola yazdırılır.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](./index.md)
- [Break ekstresi](/cpp/cpp/break-statement-cpp)
