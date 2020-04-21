---
title: while - C# Referans
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 481d3f7b87dbe874de010825c3c7f052e4bc33c0
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738750"
---
# <a name="while-c-reference"></a>while (C# Başvurusu)

`while` İfade bir deyim veya ifade bloğu yürütürken, belirli bir `true`Boolean ifadesi .'ye göre değerlendirilir. Bu ifade döngünün her yürütülmesinden önce `while` değerlendirildiği için, bir döngü sıfır veya daha fazla kez yürütür. Bu, bir veya daha fazla kez yürüten [do](do.md) döngüsünden farklıdır.

`while` İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilirsiniz.

Continue deyimini kullanarak ifadenin `while` değerlendirilmesi [continue](continue.md) için doğrudan adım atabilirsiniz. İfade, `true`yürütme yi değerlendirirse, döngüdeki ilk ifadede devam eder. Aksi takdirde, yürütme döngüden sonra ilk deyimde devam ediyor.

Ayrıca [goto](goto.md) `while` tarafından bir döngü çıkmak , [return](return.md), veya ifadeler [atmak.](throw.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, `while` deyimin kullanımını gösterir. Örnek kodu çalıştırmak için **Çalıştır'ı** seçin. Bundan sonra kodu değiştirebilir ve yeniden çalıştırabilirsiniz.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [while deyimi](~/_csharplang/spec/statements.md#the-while-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [deyimi yapmak](do.md)
