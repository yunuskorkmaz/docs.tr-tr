---
title: do - C# Referans
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 38224ce70c19ff67ad80b99d3da52155849f1341
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713595"
---
# <a name="do-c-reference"></a>do (C# Başvurusu)

`do` İfade bir deyim veya ifade bloğu yürütürken, belirli bir `true`Boolean ifadesi .'ye göre değerlendirilir. Bu ifade döngünün her yürütülmesinden sonra `do-while` değerlendirildiği için, bir döngü bir veya daha fazla kez yürütür. Bu, sıfır veya daha fazla kez yürüten [while](while.md) döngüsünden farklıdır.

`do` İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilirsiniz.

Continue deyimini kullanarak ifadenin `while` değerlendirilmesi [continue](continue.md) için doğrudan adım atabilirsiniz. İfade, `true`yürütme yi değerlendirirse, döngüdeki ilk ifadede devam eder. Aksi takdirde, yürütme döngüden sonra ilk deyimde devam ediyor.

Ayrıca `do-while` [goto,](goto.md) [return](return.md)veya [atmak](throw.md) ifadeleri tarafından bir döngü çıkabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `do` deyimin kullanımını gösterir. Örnek kodu çalıştırmak için **Çalıştır'ı** seçin. Bundan sonra kodu değiştirebilir ve yeniden çalıştırabilirsiniz.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [do deyimi](~/_csharplang/spec/statements.md#the-do-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [ifade ederken](while.md)
