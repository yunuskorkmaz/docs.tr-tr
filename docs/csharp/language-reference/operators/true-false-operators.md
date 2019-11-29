---
title: true ve false işleçleri- C# Reference
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f65ed3b362080d7a8afe89e22bd132d1fc190b06
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552458"
---
# <a name="true-and-false-operators-c-reference"></a>true ve false işleçleri (C# başvuru)

`true` işleci, işleneninin kesinlikle doğru olduğunu göstermek için `true` [bool](../builtin-types/bool.md) değer döndürür. `false` işleci, işleneninin kesinlikle yanlış olduğunu göstermek için `bool` değer `true` döndürür. `true` ve `false` işleçleri birbirini tamamlamak için garanti edilmez. Diğer bir deyişle, `true` ve `false` işlecinin her ikisi de aynı işlenen için `false` `bool` değeri döndürebilir. Bir tür iki işleçten birini tanımlıyorsa, aynı zamanda başka bir işleç tanımlamalıdır.

> [!TIP]
> Üç değerli mantığı desteklemeniz gerekiyorsa (örneğin, üç değerli bir Boolean türünü destekleyen veritabanlarıyla çalışırken) `bool?` türünü kullanın. C#`bool?`işlenenleriyle üç değerli mantığı destekleyen`&`ve`|`işleçlerini sağlar. Daha fazla bilgi için, [Boole mantıksal işleçler](boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

## <a name="boolean-expressions"></a>Boole ifadeleri

Tanımlı `true` işlecine sahip bir tür, [IF](../keywords/if-else.md), [Do](../keywords/do.md), [while](../keywords/while.md)ve [for](../keywords/for.md) deyimlerinde ve [koşullu işleç `?:`](conditional-operator.md)bir denetim koşullu ifadesi sonucunun türü olabilir. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Boole ifadeleri](~/_csharplang/spec/expressions.md#boolean-expressions) bölümüne bakın.

## <a name="user-defined-conditional-logical-operators"></a>Kullanıcı tanımlı Koşullu mantıksal işleçler

Tanımlı `true` ve [`false` işleçleriyle](operator-overloading.md) bir tür, [mantıksal veya işlecini](boolean-logical-operators.md#logical-or-operator-) `|` ya da [mantıksal ve işleç](boolean-logical-operators.md#logical-and-operator-) `&` belırlı bir şekilde, [Koşullu mantıksal or işleci](boolean-logical-operators.md#conditional-logical-or-operator-) `||` veya [ Koşullu mantıksal ve işleç](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, sırasıyla bu türün işlenenleri için değerlendirilebilir. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek hem `true` hem de `false` işleçlerini tanımlayan türü gösterir. Bu tür Ayrıca, mantıksal ve işleç `&` de, `&&` işlecinin bu türdeki işlenenler için değerlendirilebilecek şekilde de yeniden yükler.

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

`&&` işlecinin kısa devre dışı davranışına dikkat edin. `GetFuelLaunchStatus` yöntemi `LaunchStatus.Red`döndürdüğünde `&&` işlecinin sağ işleneni değerlendirilmez. Bunun nedeni, `LaunchStatus.Red` kesinlikle false olur. Sonra mantıksal ve sonucu, sağ işlenenin değerine bağlı değildir. Örneğin çıktısı aşağıdaki gibidir:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
