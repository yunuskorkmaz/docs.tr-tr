---
title: Kullanıcı tanımlı dönüştürme işleçleri- C# başvuru
description: İçinde C#özel örtük ve açık tür dönüştürmeleri tanımlama hakkında bilgi edinin.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 8788883a6c60032de2ffab658fcf2721654fc6f7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566667"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Kullanıcı tanımlı dönüştürme işleçleri (C# başvuru)

Kullanıcı tanımlı bir tür, ya da başka bir türe özel örtük veya açık bir dönüştürme tanımlayabilir.

Örtük dönüştürmeler özel sözdiziminin çağrılmasını gerektirmez ve örneğin atamalar ve Yöntemler çağırmaları gibi çeşitli durumlarda gerçekleşebilir. Önceden C# tanımlanmış örtük dönüştürmeler her zaman başarılı olur ve hiçbir zaman özel durum oluşturmaz veya bilgi kaybeder. Kullanıcı tanımlı örtük dönüştürmeler de bu şekilde davranmalıdır. Özel bir dönüştürme özel durum oluşturabilir veya bilgi kaybedebilir, onu açık bir dönüştürme olarak tanımlayın.

Kullanıcı tanımlı dönüştürmeler, ve [gibi](type-testing-and-cast.md#as-operator) işleçler tarafından değerlendirilmez [](type-testing-and-cast.md#is-operator) . Kullanıcı tanımlı bir açık dönüştürme çağırmak için [cast işlecini ()](type-testing-and-cast.md#cast-operator-) kullanın.

Sırasıyla örtük veya `implicit` açık `explicit` bir dönüştürme tanımlamak için veveyaanahtarsözcüklerinikullanın.`operator` Bir dönüştürmeyi tanımlayan tür bir kaynak türü ya da bu dönüştürmenin hedef türü olmalıdır. Kullanıcı tanımlı iki tür arasında dönüştürme iki türden birinde tanımlanabilir.

Aşağıdaki örnek, örtük ve açık bir dönüştürmenin nasıl tanımlanacağını göstermektedir:

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

Ayrıca, `operator` önceden tanımlanmış C# bir işleci aşırı yüklemek için anahtar sözcüğünü de kullanabilirsiniz. Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](operator-overloading.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Dönüştürme işleçleri](~/_csharplang/spec/classes.md#conversion-operators)
- [Kullanıcı tanımlı dönüştürmeler](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Örtük dönüştürmeler](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [İşleç aşırı yüklemesi](operator-overloading.md)
- [Tür testi ve atama işleçleri](type-testing-and-cast.md)
- [Atama ve tür dönüştürme](../../programming-guide/types/casting-and-type-conversions.md)
- [Üzerinde Kullanıcı tanımlı açık dönüşümlerC#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
