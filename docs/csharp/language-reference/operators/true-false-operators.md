---
title: true ve false işleçleri-C# başvurusu
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 15342c3d9cd66195639e38265875a7ed4008dd51
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916627"
---
# <a name="true-and-false-operators-c-reference"></a>true ve false işleçleri (C# Başvurusu)

`true`İşleci, [bool](../builtin-types/bool.md) `true` işleneninin kesinlikle doğru olduğunu göstermek için bool değeri döndürür. `false`İşleci, `bool` `true` işleneninin kesinlikle yanlış olduğunu göstermek için değeri döndürür. `true`Ve `false` işleçleri birbirini tamamlamak için garanti edilmez. Diğer bir deyişle, `true` ve `false` işleci `bool` `false` aynı işlenen için değeri döndürebilir. Bir tür iki işleçten birini tanımlıyorsa, aynı zamanda başka bir işleç tanımlamalıdır.

> [!TIP]
> `bool?`Üç değerli mantığı desteklemeniz gerekiyorsa (örneğin, üç değerli bir Boolean türünü destekleyen veritabanlarıyla çalışırken) türünü kullanın. C#, `&` `|` işlenenlerle üç değerli mantığı destekleyen ve işleçlerini sağlar `bool?` . Daha fazla bilgi için, [Boole mantıksal işleçler](boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

## <a name="boolean-expressions"></a>Mantıksal ifadeler

Tanımlı işleci olan bir tür `true` , [IF](../keywords/if-else.md), [Do](../keywords/do.md), [while](../keywords/while.md), ve [for](../keywords/for.md) deyimlerinde ve [koşullu işleçte `?:` ](conditional-operator.md)bir denetim koşullu ifadesi sonucunun türü olabilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Boole ifadeleri](~/_csharplang/spec/expressions.md#boolean-expressions) bölümüne bakın.

## <a name="user-defined-conditional-logical-operators"></a>Kullanıcı tanımlı Koşullu mantıksal işleçler

Tanımlı `true` ve işleçlere sahip bir tür `false` [mantıksal veya IŞLECINI](boolean-logical-operators.md#logical-or-operator-) [overloads](operator-overloading.md) `|` veya [mantıksal ve işlecini](boolean-logical-operators.md#logical-and-operator-) `&` belirli bir şekilde aşırı YÜKIYORSA, [Koşullu mantıksal or işleci](boolean-logical-operators.md#conditional-logical-or-operator-) `||` veya [Koşullu mantıksal ve işleç](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` sırasıyla bu türün işlenenleri için değerlendirilebilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek hem hem de işleçlerini tanımlayan türü gösterir `true` `false` . Bu tür ayrıca mantıksal ve işlecini, `&` `&&` işlecin bu türdeki işlenenler için de değerlendirilebilecek şekilde de aşırı yükler.

[!code-csharp[true and false operators example](snippets/shared/TrueFalseOperators.cs)]

İşlecin kısa devre dışı davranışına dikkat edin `&&` . Yöntemi döndürüldüğünde `GetFuelLaunchStatus` `LaunchStatus.Red` , işlecin sağ işleneni `&&` değerlendirilmez. Bunun nedeni `LaunchStatus.Red` kesinlikle false 'tur. Sonra mantıksal ve sonucu, sağ işlenenin değerine bağlı değildir. Örneğin çıktısı aşağıdaki gibidir:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
