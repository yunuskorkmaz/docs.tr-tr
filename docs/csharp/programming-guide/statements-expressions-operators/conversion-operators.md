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
ms.openlocfilehash: 539a554da2ea2f785a54bd7e5ff81d09b908c9e4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965221"
---
# <a name="conversion-operators-c-programming-guide"></a>Dönüşüm işleçleri (C# Programlama Kılavuzu)

C# programcıları, böylece sınıflar veya yapılar için ve/veya diğer sınıflar veya yapılar veya temel türleri dönüştürülebilir sınıflar veya yapılar üzerinde dönüştürmeler bildirmek etkinleştirir. Dönüştürme işleçleri gibi tanımlanır ve dönüştürme, türü adlandırılmış. Dönüştürülecek bağımsız değişken türünü veya dönüştürme, ancak iki değil, sonuç türü kapsayan tür olmalıdır.  
  
 [!code-csharp[csProgGuideStatements#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#10)]  
  
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
