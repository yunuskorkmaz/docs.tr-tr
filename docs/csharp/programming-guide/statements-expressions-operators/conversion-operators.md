---
title: Dönüşüm İşleçleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 97e93230658b5d1da676b029169b63bc9006ddb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="conversion-operators-c-programming-guide"></a>Dönüşüm İşleçleri (C# Programlama Kılavuzu)
C# programcıları sınıfları veya yapılar ve/veya diğer sınıflar yapılar veya temel türleri dönüştürülebilir böylece dönüşümleri sınıfları veya yapılar bildirmek etkinleştirir. Dönüşümler like işleçleri tanımlanır ve bunlar dönüştürme türü için adlı. Dönüştürülecek bağımsız değişken türü veya dönüştürme, ancak ikisini birlikte, sonucu türünü içeren türde olması gerekir.  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a>Dönüştürme İşleçlerine Genel Bakış  
 Dönüştürme işleçleri aşağıdaki özelliklere sahiptir:  
  
-   Dönüşümler bildirilen `implicit` gerekli olduğunda otomatik olarak gerçekleşir.  
  
-   Dönüşümler bildirilen `explicit` çağrılacak bir cast gerektirir.  
  
-   Tüm dönüşümler olarak bildirilmelidir `static`.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Dönüştürme İşleçleri Kullanma](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Convert>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Kullanıcı tanımlı zincirleme açık dönüşümler C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
