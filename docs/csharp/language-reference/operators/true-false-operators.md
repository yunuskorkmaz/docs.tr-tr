---
title: TRUE ve false işleçleri - C# başvurusu
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 7cbfca932b5f9f8a6f658e84204da5005da5ffb8
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609832"
---
# <a name="true-and-false-operators-c-reference"></a>TRUE ve false işleçleri (C# Başvurusu)

`true` İşleci döndürür [bool](../keywords/bool.md) değer `true` işleneni kesinlikle doğru olduğunu belirtmek için. `false` İşleci döndürür `bool` değer `true` işleneni kesinlikle false olduğunu belirtmek için. `true` Ve `false` işleçleri birbirini tamamlar için garanti edilmez. Diğer bir deyişle, her ikisi de `true` ve `false` işleci döndürebilir `bool` değer `false` aynı işlenen için. Bir tür iki işleç tanımlıyorsa, aynı zamanda başka bir işleç tanımlamanız gerekir.

> [!TIP]
> Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli Boole türü destekleyen veritabanları ile. C#sağlar `&` ve `|` ile üç değerli mantığını destekleyecek işleçleri `bool?` işlenen. Daha fazla bilgi için [boş değer atanabilir Boolean mantıksal işleçler](boolean-logical-operators.md#nullable-boolean-logical-operators) bölümünü [Boolean mantıksal işleçler](boolean-logical-operators.md) makalesi.

## <a name="boolean-expressions"></a>Boole ifadeleri

Tanımlanan bir türü `true` işleci denetleyen bir koşullu deyim sonucu türü olabilir [varsa](../keywords/if-else.md), [yapmak](../keywords/do.md), [sırada](../keywords/while.md), ve [ için](../keywords/for.md) deyimleri ve [koşullu işleç `?:` ](conditional-operator.md). Daha fazla bilgi için [Boolean ifadeler](~/_csharplang/spec/expressions.md#boolean-expressions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="user-defined-conditional-logical-operators"></a>Kullanıcı tanımlı koşullu mantıksal işleçler

Bir tür ederse ile tanımlanan `true` ve `false` işleçleri [aşırı](operator-overloading.md) [mantıksal OR işlecinin](boolean-logical-operators.md#logical-or-operator-) `|` veya [mantıksal AND işleci](boolean-logical-operators.md#logical-and-operator-) `&` belirli bir şekilde [koşullu mantıksal OR işlecinin](boolean-logical-operators.md#conditional-logical-or-operator-) `||` veya [koşullu mantıksal AND işleci](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`sırayla değerlendirilir Bu türündeki işlenenler için. Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek her ikisi de tanımlayan türü sunar `true` ve `false` işleçleri. Türü ayrıca mantıksal AND işlecinin aşırı `&` şekilde, işlecin `&&` , o türündeki işlenenler için ayrıca değerlendirilir.

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

Short-circuiting davranışla `&&` işleci. Zaman `GetFuelLaunchStatus` yöntemi döndürür `LaunchStatus.Red`, sağ işleneni `&&` işleci değerlendirilmez. Çünkü `LaunchStatus.Red` kesinlikle false'tur. Ardından mantıksal AND sonucunu sağ işleneninin değerini temel bağımlı değildir. Örnek çıktısı aşağıdaki gibidir:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [TRUE değişmez değeri](../keywords/true-literal.md)
- [false değişmez değeri](../keywords/false-literal.md)
