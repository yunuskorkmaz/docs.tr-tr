---
title: do-C# başvurusu
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: d75dd816278a876fa05d133e5eb189d606300a5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401933"
---
# <a name="do-c-reference"></a>do (C# Başvurusu)

`do`Deyimi, belirtilen bir Boole ifadesi olarak değerlendirilen bir deyimi veya bir deyim bloğunu yürütür `true` . Bu ifade döngünün her yürütülmesinden sonra değerlendirildiğinden bir `do-while` döngü bir veya daha fazla kez yürütülür. Bu, sıfır veya daha fazla kez yürütülen [while](while.md) döngüsünden farklıdır.

Deyimdeki herhangi bir noktada `do` [Break](break.md) ifadesini kullanarak döngünün dışına kesebilirsiniz.

`while` [Continue](continue.md) deyimini kullanarak doğrudan ifadenin değerlendirmesine adım adım ekleyebilirsiniz. İfade olarak değerlendirilirse `true` , yürütme döngüsünde ilk deyimde devam eder. Aksi halde, yürütme döngüden sonraki ilk ifadede devam eder.

Ayrıca `do-while` [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, ifadesinin kullanımını gösterir `do` . Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin. Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [Do deyimin](~/_csharplang/spec/statements.md#the-do-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [while deyimi](while.md)
