---
title: true işleci (C# Başvurusu)
ms.date: 12/03/2018
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 17830e5ae842255dcf71e73097779d17520b81e6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130682"
---
# <a name="true-operator-c-reference"></a>true işleci (C# Başvurusu)

Döndürür [bool](bool.md) değer `true` işleneni kesinlikle doğru olduğunu belirtmek için. Bir türü tanımlıyorsa `true` işleci, bu da tanımlamalıdır [false işleci](false-operator.md). `true` Ve `false` işleçleri birbirini tamamlar için garanti edilmez.

Her ikisi de tanımlar örneğin `true` ve `false` işleçleri görmek [false işleci](false-operator.md) makalesi.

> [!TIP]
> Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli mantıksal türünü destekleyen veritabanları ile. Daha fazla bilgi için [bool? türü](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.

Bir tür ederse ile tanımlanan `true` işleci [aşırı](operator.md) [mantıksal OR işlecinin](../operators/or-operator.md) `|` belirli bir şekilde [koşullu mantıksal OR işlecinin](../operators/conditional-or-operator.md) `||`, short-circuiting, olduğu değerlendirmesi yapılamıyor, o türündeki işlenenler için. Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

Tanımlanan bir türü `true` işleci denetleyen bir koşullu deyim sonucu türü olabilir [varsa](if-else.md), [yapmak](do.md), [sırada](while.md), ve [ için](for.md) deyimleri ve [koşullu işleç `?:` ](../operators/conditional-operator.md). Daha fazla bilgi için [Boolean ifadeler](~/_csharplang/spec/expressions.md#boolean-expressions) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [C# İşleçleri](../operators/index.md)
- [`true` değişmez değer](true-literal.md)