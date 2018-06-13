---
title: explicit (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: c8a05aef3318eb34242ed1268ea26663592e4d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216483"
---
# <a name="explicit-c-reference"></a>explicit (C# Başvurusu)
`explicit` Anahtar sözcüğü ile bir cast çağrılan bir kullanıcı tanımlı tür dönüştürme işleci bildirir. Örneğin, bu işleç Fahrenhayt derece adlı bir sınıf olarak adlandırılan bir sınıftan dönüştürür:  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 Bu dönüşüm işleci çağrılan şöyle:  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 Dönüşüm işleci kaynak türünden bir hedef türe dönüştürür. Kaynak türü dönüşüm işleci sağlar. Örtük dönüştürme, açık dönüşüm işleçleri atama yoluyla çağrılması gerekir. Dönüştürme işlemi özel durumlara neden bilgileri kaybeder veya işaretlemeniz gerekir `explicit`. Bu, büyük olasılıkla öngörülemeyen sonuçlara dönüştürme işlemi sessizce çağırma derleyici önler.  
  
 Derleme zamanı hatası CS0266 cast sonuçlarında atlama.  
  
 Daha fazla bilgi için bkz: [dönüşüm işleçleri kullanma](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sağlayan bir `Fahrenheit` ve `Celsius` sınıfı, her biri bir açık dönüşüm işleci için başka bir sınıf sağlar.  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yapının tanımlar `Digit`, tek bir ondalık basamak temsil eden. Bir işleç dönüştürmeleri için tanımlanan `byte` için `Digit`, ancak tüm bayt dönüştürülebilir bir `Digit`, dönüştürme açık değildir.  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [İşleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md)  
 [Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [Kullanıcı tanımlı zincirleme açık dönüşümler C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
