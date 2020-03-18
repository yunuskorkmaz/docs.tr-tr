---
title: doğru ve yanlış operatörler - C# referans
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 5ccd08a348478902bbbac36e99acf7ffc1fc814b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846226"
---
# <a name="true-and-false-operators-c-reference"></a>doğru ve yanlış işleçler (C# referansı)

Operatör, `true` operand'ın kesinlikle doğru olduğunu belirtmek için [bool](../builtin-types/bool.md) değerini `true` döndürür. İşletici, `false` `true` operand'ın kesinlikle yanlış olduğunu belirtmek için değeri döndürür. `bool` Ve `true` `false` işleçlerin birbirini tamamlayacakları garanti edilmez. Diğer bir `true` süre, `false` hem işleç hem de işleç aynı operand için `bool` değeri `false` döndürebilir. Bir tür iki işleçten birini tanımlıyorsa, başka bir işleç de tanımlaması gerekir.

> [!TIP]
> Üç `bool?` değerli mantığı desteklemeniz gerekiyorsa (örneğin, üç değerli Boolean türünü destekleyen veritabanlarıyla çalışırken) türü kullanın. C# `&` `bool?` operands ile üç değerli mantığı destekleyen ve `|` işleçleri sağlar. Daha fazla bilgi için [Boolean mantıksal işleçleri](boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçleri](boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

## <a name="boolean-expressions"></a>Mantıksal ifadeler

Tanımlanan `true` işleci ile bir tür [if,](../keywords/if-else.md) [do](../keywords/do.md), [while](../keywords/while.md), ve ifadeler [için](../keywords/for.md) ve [koşullu `?:`işleç ](conditional-operator.md)bir kontrol koşullu ifade sonucu türü olabilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Boolean ifadeleri](~/_csharplang/spec/expressions.md#boolean-expressions) bölümüne bakın.

## <a name="user-defined-conditional-logical-operators"></a>Kullanıcı tanımlı koşullu mantıksal işleçler

Tanımlanan `true` ve `false` işleçleri olan bir tür [mantıksal OR işleci](boolean-logical-operators.md#logical-or-operator-) `|` veya mantıksal AND [işleci](boolean-logical-operators.md#logical-and-operator-) `&` belirli bir şekilde [aşırı yükler,](operator-overloading.md) [koşullu mantıksal VEYA işleci](boolean-logical-operators.md#conditional-logical-or-operator-) `||` veya [koşullu mantıksal VE işleci](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, sırasıyla, bu tür operands için değerlendirilebilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı koşullu mantıksal işleçleri](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, hem de `true` `false` işleçleri tanımlayan türü gösterir. Tür ayrıca mantıksal AND `&` `&&` işlecinin de bu tip operands için değerlendirilebilir şekilde aşırı yükler.

[!code-csharp[true and false operators example](snippets/TrueFalseOperators.cs)]

Operatörün kısa devre davranışına `&&` dikkat edin. `GetFuelLaunchStatus` Yöntem döndüğünde, `LaunchStatus.Red`operatörün `&&` sağ operand'ı değerlendirilmez. Çünkü kesinlikle `LaunchStatus.Red` yanlıştır. Sonra mantıksal ve sonucu sağ operand değerine bağlı değildir. Örneğin çıktısı aşağıdaki gibidir:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
