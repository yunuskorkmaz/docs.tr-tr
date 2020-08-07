---
title: Kullanıcı tanımlı dönüştürme işleçleri-C# başvurusu
description: C# ' de özel örtük ve açık tür dönüştürmeleri tanımlama hakkında bilgi edinin.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
- explicit
- implicit
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 70f553b129d5ef8a0f9077c16656a17d8e88fed4
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855848"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Kullanıcı tanımlı dönüştürme işleçleri (C# Başvurusu)

Kullanıcı tanımlı bir tür, ya da başka bir türe özel örtük veya açık bir dönüştürme tanımlayabilir.

Örtük dönüştürmeler özel sözdiziminin çağrılmasını gerektirmez ve örneğin atamalar ve Yöntemler çağırmaları gibi çeşitli durumlarda gerçekleşebilir. Önceden tanımlanmış C# örtük dönüştürmeleri her zaman başarılı olur ve hiçbir zaman özel durum oluşturmaz. Kullanıcı tanımlı örtük dönüştürmeler de bu şekilde davranmalıdır. Özel bir dönüştürme özel durum oluşturabilir veya bilgi kaybedebilir, onu açık bir dönüştürme olarak tanımlayın.

Kullanıcı tanımlı dönüştürmeler [, ve](type-testing-and-cast.md#is-operator) [gibi](type-testing-and-cast.md#as-operator) işleçler tarafından değerlendirilmez. Kullanıcı tanımlı açık dönüştürmeyi çağırmak için bir [atama ifadesi](type-testing-and-cast.md#cast-expression) kullanın.

`operator` `implicit` `explicit` Sırasıyla örtük veya açık bir dönüştürme tanımlamak için ve veya anahtar sözcüklerini kullanın. Bir dönüştürmeyi tanımlayan tür bir kaynak türü ya da bu dönüştürmenin hedef türü olmalıdır. Kullanıcı tanımlı iki tür arasında dönüştürme iki türden birinde tanımlanabilir.

Aşağıdaki örnek, örtük ve açık bir dönüştürmenin nasıl tanımlanacağını göstermektedir:

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

Ayrıca, `operator` önceden tanımlanmış bir C# işlecini aşırı yüklemek için anahtar sözcüğünü de kullanabilirsiniz. Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](operator-overloading.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Dönüştürme işleçleri](~/_csharplang/spec/classes.md#conversion-operators)
- [Kullanıcı tanımlı dönüştürmeler](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Örtük dönüştürmeler](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [İşleç aşırı yüklemesi](operator-overloading.md)
- [Tür testi ve atama işleçleri](type-testing-and-cast.md)
- [Atama ve tür dönüştürme](../../programming-guide/types/casting-and-type-conversions.md)
- [Tasarım yönergeleri-dönüştürme işleçleri](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [C 'de Kullanıcı tanımlı açık dönüştürmeler zincirleme #](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
