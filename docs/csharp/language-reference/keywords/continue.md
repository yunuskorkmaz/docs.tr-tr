---
title: continue deyimi - C# Reference
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713669"
---
# <a name="continue-c-reference"></a>continue (C# Başvurusu)

İfade, `continue` [denetimi,](./while.md)içinde göründüğü her ifade için , yapmak , [yapmak](./do.md)veya [her biri](./foreach-in.md) [için](./for.md)iken, çevreleyen bir sonraki yinelemeye geçirir.

## <a name="example"></a>Örnek

Bu örnekte, sayaç 1'den 10'a kadar saymak üzere başharfe işlenir. `continue` İfade ile birlikte ifade `(i < 9)`kullanılarak, gövdenin `continue` `for` sonu ile arasındaki ifadeler atlanır.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [break Deyimi](/cpp/cpp/break-statement-cpp)
