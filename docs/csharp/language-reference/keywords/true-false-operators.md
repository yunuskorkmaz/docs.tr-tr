---
title: TRUE ve false işleçleri - C# başvurusu
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 0a75566fdb6222157ecda12a50fd78e22f92fcb4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245749"
---
# <a name="true-and-false-operators-c-reference"></a>TRUE ve false işleçleri (C# Başvurusu)

`true` İşleci döndürür [bool](bool.md) değer `true` işleneni kesinlikle doğru olduğunu belirtmek için. `false` İşleci döndürür `bool` değer `true` işleneni kesinlikle false olduğunu belirtmek için. `true` Ve `false` işleçleri birbirini tamamlar için garanti edilmez. Diğer bir deyişle, her ikisi de `true` ve `false` işleci döndürebilir `bool` değer `false` aynı işlenen için. Bir tür iki işleç tanımlıyorsa, aynı zamanda başka bir işleç tanımlamanız gerekir.

Bir tür ederse ile tanımlanan `true` ve `false` işleçleri [aşırı](operator.md) [mantıksal OR işlecinin](../operators/or-operator.md) `|` veya [mantıksal AND işleci](../operators/and-operator.md) `&` belirli bir şekilde [koşullu mantıksal OR işlecinin](../operators/conditional-or-operator.md) `||` veya [koşullu mantıksal AND işleci](../operators/conditional-and-operator.md) `&&`sırayla değerlendirilir Bu türündeki işlenenler için. Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

Tanımlanan bir türü `true` işleci denetleyen bir koşullu deyim sonucu türü olabilir [varsa](if-else.md), [yapmak](do.md), [sırada](while.md), ve [ için](for.md) deyimleri ve [koşullu işleç `?:` ](../operators/conditional-operator.md). Daha fazla bilgi için [Boolean ifadeler](~/_csharplang/spec/expressions.md#boolean-expressions) bölümünü [ C# dil belirtimi](../language-specification/index.md).

> [!TIP]
> Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli mantıksal türünü destekleyen veritabanları ile. Daha fazla bilgi için [bool? türü](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.

Aşağıdaki örnek her ikisi de tanımlayan türü sunar `true` ve `false` işleçleri. Ayrıca, mantıksal ve işlecini aşırı `&` şekilde, işlecin `&&` , o türündeki işlenenler için ayrıca değerlendirilir.

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

Short-circuiting davranışla `&&` işleci. Zaman `GetFuelLaunchStatus` yöntemi döndürür `LaunchStatus.Red`, ikinci işleneni `&&` işleci değerlendirilmez. Çünkü `LaunchStatus.Red` kesinlikle false'tur. Ardından mantıksal AND sonucunu ikinci işlenenin değerine bağımlı değildir. Örnek çıktısı aşağıdaki gibidir:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [C# İşleçleri](../operators/index.md)
- [`true` değişmez değer](true-literal.md)
- [`false` değişmez değer](false-literal.md)