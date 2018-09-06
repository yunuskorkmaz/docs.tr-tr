---
title: do (C# Başvurusu)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 89c13f5b547c13052e229ff6eb3a39ae5babce41
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036888"
---
# <a name="do-c-reference"></a>do (C# Başvurusu)

`do` Deyimi, bir deyimi veya bir deyimler bloğunu belirtilen bir Boole ifadesi değerlendirilir sırada yürütür `true`. Bu ifade döngünün her yürütülmesi değerlendirilir çünkü bir `do-while` bir veya daha fazla kez döngü yürütür. Bu farklıdır [sırada](while.md) döngü, sıfır veya daha fazla kez yürütülür.

Herhangi bir anda işaret içinde `do` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi.

Değerlendirme için doğrudan geçebilirsiniz `while` kullanarak ifade [devam](continue.md) deyimi. İfade değerlendirme sonucu `true`, yürütme Döngüdeki ilk deyimde devam eder. Aksi takdirde, yürütme döngüyü sonra ilk deyimde devam eder.

Ayrıca çıkış bir `do-while` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kullanımını gösterir. `do` deyimi. Seçin **çalıştırma** örnek kodu çalıştırmak için. Bundan sonra bu kodu Değiştir ve yeniden çalıştırın.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [do-while Deyimi (C++)](/cpp/cpp/do-while-statement-cpp)  
- [Yineleme Deyimleri](iteration-statements.md)  
- [while deyimi](while.md)  
