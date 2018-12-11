---
title: false işleci (C# Başvurusu)
ms.date: 12/03/2018
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 4428d88acb08246623e2deb71a9daf7fb1cca692
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152311"
---
# <a name="false-operator-c-reference"></a>false işleci (C# Başvurusu)

Döndürür [bool](bool.md) değer `true` işleneni kesinlikle false olduğunu belirtmek için. Bir türü tanımlıyorsa `false` işleci, bu da tanımlamalıdır [true işleci](true-operator.md). `true` Ve `false` işleçleri birbirini tamamlar için garanti edilmez.

> [!TIP]
> Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli mantıksal türünü destekleyen veritabanları ile. Daha fazla bilgi için [bool? türü](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.

Bir türü varsa tanımlanan ile `false` işleci [aşırı](operator.md) [mantıksal AND işlecinin](../operators/and-operator.md) `&` belirli bir şekilde [koşullu mantıksal AND işlecinin](../operators/conditional-and-operator.md) `&&`, short-circuiting, olduğu değerlendirmesi yapılamıyor, o türündeki işlenenler için. Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

Aşağıdaki örnek her ikisi de tanımlayan türü sunar `true` ve `false` işleçleri. Ayrıca, mantıksal ve işlecini aşırı `&` şekilde, işlecin `&&` , o türündeki işlenenler için ayrıca değerlendirilir.

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

Short-circuiting davranışla `&&` işleci. Zaman `GetFuelLaunchStatus` yöntemi döndürür `LaunchStatus.Red`, ikinci işleneni `&&` işleci değerlendirilmez. Çünkü `LaunchStatus.Red` kesinlikle false'tur. Ardından mantıksal AND sonucunu ikinci işlenenin değerine bağımlı değildir. Örnek çıktısı aşağıdaki gibidir:

```console
Getting fuel launch status...
Wait!
```

Ayrıca dikkat koşullu ifadede [koşullu işleç `?:` ](../operators/conditional-operator.md) değil `LaunchStatus` türü. Mümkün olan çünkü `LaunchStatus` tanımlar `true` işleci. Daha fazla bilgi için [Boolean ifadeler](~/_csharplang/spec/expressions.md#boolean-expressions) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [C# İşleçleri](../operators/index.md)
- [`false` değişmez değer](false-literal.md)