---
title: Explicit anahtar sözcüğü (C# Başvurusu)
ms.date: 08/24/2018
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 3567a2c5aa549aa3141ed59c3e93e7b07975da70
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463149"
---
# <a name="explicit-c-reference"></a>explicit (C# Başvurusu)

`explicit` Anahtar sözcüğü, bir yayın ile çağrılan bir kullanıcı tanımlı tür dönüştürme işleci bildirir.

Aşağıdaki örnek, dönüştürür işleci tanımlar. bir `Fahrenheit` sınıfının bir `Celsius` sınıfı. İşleç olmalıdır ya da iç tanımlanan bir `Fahrenheit` sınıfı veya `Celsius` sınıfı:

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

Aşağıdaki örnekte gösterildiği gibi bir tür dönüştürme ile tanımlı dönüştürme işleci çağırmayı:

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

Dönüştürme işleci bir kaynak türden hedef türe dönüştürür. Kaynak türü dönüştürme işleci sağlar. Örtük dönüştürme, bir atama yoluyla açık dönüştürme işleçleri çağrılması gerekir. Bir dönüştürme işlemini özel durumlarına neden veya bilgi kaybı işaretlemelisiniz `explicit`. Bu, derleyici sessiz bir şekilde dönüştürme işlemi muhtemelen öngörülemeyen sonuçlara yürütmesini engeller.

Derleme zamanı hatası CS0266 atama sonuçlarında atlama.

Daha fazla bilgi için [dönüştürme işleçleri kullanarak](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek sağlayan bir `Fahrenheit` ve `Celsius` sınıfı, her biri için başka bir sınıfın açık bir dönüştürme operatörü sağlar.

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapı tanımlar `Digit`, temsil eden tek bir ondalık basamak. Bir işleç dönüştürmelerinde tanımlanan `byte` için `Digit`, ancak tüm baytlar dönüştürülebilir bir `Digit`, dönüştürme açıktır.

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [implicit](implicit.md)  
- [İşleci (C# Başvurusu)](operator.md)  
- [Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
- [Kullanıcı tanımlı C# ' de açık dönüştürmeler zincirleme](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  
