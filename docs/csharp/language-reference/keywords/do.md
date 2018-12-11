---
title: do (C# Başvurusu)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 4dd5f4034bcd60b714071eb7eb9518e66ac0c848
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129031"
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

Daha fazla bilgi için [do deyimi](~/_csharplang/spec/statements.md#the-do-statement) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Yineleme Deyimleri](iteration-statements.md)
- [while deyimi](while.md)
