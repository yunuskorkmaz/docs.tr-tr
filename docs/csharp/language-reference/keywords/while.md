---
title: while-C# başvurusu
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: af616c2381b993f86296cbfa43a01ba2f9e000c2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401868"
---
# <a name="while-c-reference"></a>while (C# Başvurusu)

`while`Deyimi, belirtilen bir Boole ifadesi olarak değerlendirilen bir deyimi veya bir deyim bloğunu yürütür `true` . Bu ifade döngünün her yürütmeden önce değerlendirildiğinden, bir `while` döngü sıfır veya daha fazla kez yürütülür. Bu, bir veya daha fazla kez yürütülen [Do](do.md) döngüsünden farklıdır.

Deyimdeki herhangi bir noktada `while` [Break](break.md) ifadesini kullanarak döngünün dışına kesebilirsiniz.

`while` [Continue](continue.md) deyimini kullanarak doğrudan ifadenin değerlendirmesine adım adım ekleyebilirsiniz. İfade olarak değerlendirilirse `true` , yürütme döngüsünde ilk deyimde devam eder. Aksi halde, yürütme döngüden sonraki ilk ifadede devam eder.

Ayrıca `while` [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, ifadesinin kullanımını gösterir `while` . Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin. Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.

[!code-csharp-interactive[while loop example](snippets/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [while ifadesinin](~/_csharplang/spec/statements.md#the-while-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [do ekstresi](do.md)
