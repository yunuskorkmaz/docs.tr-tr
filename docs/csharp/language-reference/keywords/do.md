---
title: yapılacak C# başvuru
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 38224ce70c19ff67ad80b99d3da52155849f1341
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713595"
---
# <a name="do-c-reference"></a>do (C# Başvurusu)

`do` deyimi, belirtilen bir Boole ifadesi `true`değerlendirirken bir deyimi veya bir deyim bloğunu yürütür. Bu ifade döngünün her yürütülmesinden sonra değerlendirildiğinden, bir `do-while` döngüsü bir veya daha fazla kez yürütülür. Bu, sıfır veya daha fazla kez yürütülen [while](while.md) döngüsünden farklıdır.

`do` bildiri bloğunun içindeki herhangi bir noktada [Break](break.md) ifadesini kullanarak döngünün dışına kesebilirsiniz.

[Continue](continue.md) deyimini kullanarak `while` ifadesinin değerlendirmesine doğrudan ilerleyerek. İfade `true`olarak değerlendirilirse, yürütme döngüdeki ilk deyimde devam eder. Aksi halde, yürütme döngüden sonraki ilk ifadede devam eder.

Ayrıca, [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir `do-while` döngüsünden çıkabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek `do` deyimin kullanımını gösterir. Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin. Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [Do deyimin](~/_csharplang/spec/statements.md#the-do-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [while ekstresi](while.md)
