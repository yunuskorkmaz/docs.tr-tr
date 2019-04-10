---
title: TRUE ve false işleçleri - C# başvurusu
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 869eeab6515340b2f1884ab7206979e83654a10b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328250"
---
# <a name="true-and-false-operators-c-reference"></a>TRUE ve false işleçleri (C# Başvurusu)

`true` İşleci döndürür [bool](bool.md) değer `true` işleneni kesinlikle doğru olduğunu belirtmek için. `false` İşleci döndürür `bool` değer `true` işleneni kesinlikle false olduğunu belirtmek için. `true` Ve `false` işleçleri birbirini tamamlar için garanti edilmez. Diğer bir deyişle, her ikisi de `true` ve `false` işleci döndürebilir `bool` değer `false` aynı işlenen için. Bir tür iki işleç tanımlıyorsa, aynı zamanda başka bir işleç tanımlamanız gerekir.

Bir tür ederse ile tanımlanan `true` ve `false` işleçleri [aşırı](operator.md) [mantıksal OR işlecinin](../operators/boolean-logical-operators.md#logical-or-operator-) `|` veya [mantıksal AND işleci](../operators/boolean-logical-operators.md#logical-and-operator-) `&` belirli bir şekilde [koşullu mantıksal OR işlecinin](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) `||` veya [koşullu mantıksal AND işleci](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) `&&`sırayla değerlendirilir Bu türündeki işlenenler için. Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

Tanımlanan bir türü `true` işleci denetleyen bir koşullu deyim sonucu türü olabilir [varsa](if-else.md), [yapmak](do.md), [sırada](while.md), ve [ için](for.md) deyimleri ve [koşullu işleç `?:` ](../operators/conditional-operator.md). Daha fazla bilgi için [Boolean ifadeler](~/_csharplang/spec/expressions.md#boolean-expressions) bölümünü [ C# dil belirtimi](../language-specification/index.md).

> [!TIP]
> Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli Boole türü destekleyen veritabanları ile. C#sağlar `&` ve `|` ile üç değerli mantığını destekleyecek işleçleri `bool?` işlenen. Daha fazla bilgi için [boş değer atanabilir Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümünü [Boolean mantıksal işleçler](../operators/boolean-logical-operators.md) makalesi.

Aşağıdaki örnek her ikisi de tanımlayan türü sunar `true` ve `false` işleçleri. Ayrıca, mantıksal ve işlecini aşırı `&` şekilde, işlecin `&&` , o türündeki işlenenler için ayrıca değerlendirilir.

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

Short-circuiting davranışla `&&` işleci. Zaman `GetFuelLaunchStatus` yöntemi döndürür `LaunchStatus.Red`, ikinci işleneni `&&` işleci değerlendirilmez. Çünkü `LaunchStatus.Red` kesinlikle false'tur. Ardından mantıksal AND sonucunu ikinci işlenenin değerine bağımlı değildir. Örnek çıktısı aşağıdaki gibidir:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# Başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [C# İşleçleri](../operators/index.md)
- [`true` değişmez değer](true-literal.md)
- [`false` değişmez değer](false-literal.md)