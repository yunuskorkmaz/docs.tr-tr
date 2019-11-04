---
title: while- C# Reference
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: ab0a8ba0b724757b4f239daf1d3319b989c4531a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421912"
---
# <a name="while-c-reference"></a>while (C# Başvurusu)

`while` deyimi, belirtilen bir Boole ifadesi `true`değerlendirirken bir deyimi veya bir deyim bloğunu yürütür. Bu ifade döngünün her yürütmeden önce değerlendirildiğinden `while` döngüsü sıfır veya daha fazla kez yürütülür. Bu, bir veya daha fazla kez yürütülen [Do](do.md) döngüsünden farklıdır.

`while` bildiri bloğunun içindeki herhangi bir noktada [Break](break.md) ifadesini kullanarak döngünün dışına kesebilirsiniz.

[Continue](continue.md) deyimini kullanarak `while` ifadesinin değerlendirmesine doğrudan ilerleyerek. İfade `true`olarak değerlendirilirse, yürütme döngüdeki ilk deyimde devam eder. Aksi halde, yürütme döngüden sonraki ilk ifadede devam eder.

Ayrıca, [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir `while` döngüsünden çıkabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek `while` deyimin kullanımını gösterir. Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin. Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [while ifadesinin](~/_csharplang/spec/statements.md#the-while-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [do ekstresi](do.md)
