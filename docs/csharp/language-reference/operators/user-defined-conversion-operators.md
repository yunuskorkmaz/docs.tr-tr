---
title: Kullanıcı tanımlı dönüştürme operatörleri - C# başvurusu
description: Özel örtük ve açık tür dönüştürmelerinde tanımlamayı öğrenin C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 5d1882048b2af12c29a3771055cbeba9565b7dab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67788500"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Kullanıcı tanımlı dönüştürme işleçleri (C# Başvurusu)

Kullanıcı tanımlı bir tür özel örtük veya açık dönüştürme ya da başka bir türe tanımlayabilirsiniz.

Örtük dönüştürmeleri çağrılacak özel sözdizimi gerektirmeyen ve bir çeşitli durumlarda, örneğin, atamalar ve yöntem çağrılarını içinde ortaya çıkabilir. Önceden tanımlanmış C# örtülü dönüştürmeler her zaman başarılı ve hiçbir zaman bir özel durum veya bilgileri kaybedersiniz. Kullanıcı tanımlı örtük dönüştürmeleri bu yolla çalışacaktır. Özel bir dönüştürme bir özel durum veya bilgi kaybı, açık bir dönüştürme tanımlayın.

Kullanıcı tanımlı dönüştürmeler tarafından dikkate alınmaz [olduğu](type-testing-and-conversion-operators.md#is-operator) ve [olarak](type-testing-and-conversion-operators.md#as-operator) işleçleri. Kullanım [atama işleci ()](type-testing-and-conversion-operators.md#cast-operator-) kullanıcı tanımlı açık dönüştürme çağırmak için.

Kullanım `operator` ve `implicit` veya `explicit` örtük veya açık bir dönüştürme sırasıyla tanımlamak için anahtar sözcükler. Bir dönüştürme tanımlayan türü kaynak türü veya bu dönüştürme hedef türünde olmalıdır. İki kullanıcı tanımlı türler arasında dönüştürme iki türlerinden birini tanımlanabilir.

Aşağıdaki örnek, örtük ve açık bir dönüştürme tanımlamak gösterilmektedir:

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

Ayrıca `operator` önceden tanımlanmış bir aşırı yüklemeyi anahtar sözcüğü C# işleci. Daha fazla bilgi için [işleci aşırı yüklemesi](operator-overloading.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):

- [Dönüştürme işleçleri](~/_csharplang/spec/classes.md#conversion-operators)
- [Kullanıcı tanımlı dönüşümler](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Örtük dönüşümler](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Açık dönüştürmeler](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [İşleç aşırı yüklemesi](operator-overloading.md)
- [Tür test etme ve dönüştürme işleçleri](type-testing-and-conversion-operators.md)
- [Atama ve tür dönüştürme](../../programming-guide/types/casting-and-type-conversions.md)
- [Kullanıcı tanımlı C# ' de açık dönüştürmeler zincirleme](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
