---
title: Dönüştürme işleçleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 927640b63773d24be93cc90427668f9568a39652
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362736"
---
# <a name="conversion-operators-c-programming-guide"></a>Dönüşüm işleçleri (C# Programlama Kılavuzu)

C# programcıları, böylece sınıflar veya yapılar için ve/veya diğer sınıflar veya yapılar veya temel türleri dönüştürülebilir sınıflar veya yapılar üzerinde dönüştürmeler bildirmek etkinleştirir. Dönüştürme işleçleri gibi tanımlanır ve dönüştürme, türü adlandırılmış. Dönüştürülecek bağımsız değişken türünü veya dönüştürme, ancak iki değil, sonuç türü kapsayan tür olmalıdır.  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a>Dönüştürme işleçlerine genel bakış

 Dönüştürme işleçleri aşağıdaki özelliklere sahiptir:  
  
-   Olarak bildirilen dönüştürmeler `implicit` gerekli olduğunda otomatik olarak gerçekleşir.  
  
-   Olarak bildirilen dönüştürmeler `explicit` çağrılacak bir yayın gerektirir.  
  
-   Tüm dönüştürmeler olarak bildirilmelidir `static`.  
  
## <a name="related-sections"></a>İlgili bölümler

 Daha fazla bilgi için:  
  
-   [Dönüştürme İşleçleri Kullanma](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Nasıl yapılır: Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Kullanıcı tanımlı C# ' de açık dönüştürmeler zincirleme](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
