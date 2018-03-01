---
title: "explicit (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eab79d3ac48192f3c176ed44685ab58e50fc89be
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2017
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [örtük](../../../csharp/language-reference/keywords/implicit.md)  
 [işleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md)  
 [Nasıl yapılır: yapılar arasında kullanıcı tanımlı dönüşümler](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [Kullanıcı tanımlı zincirleme açık dönüşümler C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
