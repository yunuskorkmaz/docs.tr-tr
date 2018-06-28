---
title: Explicit anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 66d271fdac0bad356ee0bafc1732e2f410854da1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027947"
---
# <a name="explicit-c-reference"></a>explicit (C# Başvurusu)

`explicit` Anahtar sözcüğü ile bir cast çağrılan bir kullanıcı tanımlı tür dönüştürme işleci bildirir. Örneğin, bu işleç Fahrenhayt derece adlı bir sınıf olarak adlandırılan bir sınıftan dönüştürür:

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

Bu dönüşüm işleci çağrılan şöyle:

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

Dönüşüm işleci kaynak türünden bir hedef türe dönüştürür. Kaynak türü dönüşüm işleci sağlar. Örtük dönüştürme, açık dönüşüm işleçleri atama yoluyla çağrılması gerekir. Dönüştürme işlemi özel durumlara neden bilgileri kaybeder veya işaretlemeniz gerekir `explicit`. Bu, büyük olasılıkla öngörülemeyen sonuçlara dönüştürme işlemi sessizce çağırma derleyici önler.

Derleme zamanı hatası CS0266 cast sonuçlarında atlama.

Daha fazla bilgi için bkz: [dönüşüm işleçleri kullanma](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek sağlayan bir `Fahrenheit` ve `Celsius` sınıfı, her biri bir açık dönüşüm işleci için başka bir sınıf sağlar.

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapının tanımlar `Digit`, tek bir ondalık basamak temsil eden. Bir işleç dönüştürmeleri için tanımlanan `byte` için `Digit`, ancak tüm bayt dönüştürülebilir bir `Digit`, dönüştürme açık değildir.

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

[C# başvurusu](../index.md)  
[C# Programlama Kılavuzu](../../programming-guide/index.md)  
[C# Anahtar Sözcükleri](index.md)  
[implicit](implicit.md)  
[işleci (C# Başvurusu)](operator.md)  
[Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
[Kullanıcı tanımlı zincirleme açık dönüşümler C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  