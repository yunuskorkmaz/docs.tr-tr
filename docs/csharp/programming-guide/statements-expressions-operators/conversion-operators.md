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
ms.openlocfilehash: 43e81a342377b155fafe26bd0430384cddad5fd4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608226"
---
# <a name="conversion-operators-c-programming-guide"></a>Dönüşüm işleçleri (C# Programlama Kılavuzu)

C# programcıları, böylece sınıflar veya yapılar için ve/veya diğer sınıflar veya yapılar veya temel türleri dönüştürülebilir sınıflar veya yapılar üzerinde dönüştürmeler bildirmek etkinleştirir. Dönüştürme işleçleri gibi tanımlanır ve dönüştürme, türü adlandırılmış. Dönüştürülecek bağımsız değişken türünü veya dönüştürme, ancak iki değil, sonuç türü kapsayan tür olmalıdır.  
  
 [!code-csharp[csProgGuideStatements#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#10)]  
  
## <a name="conversion-operators-overview"></a>Dönüştürme işleçlerine genel bakış

 Dönüştürme işleçleri aşağıdaki özelliklere sahiptir:  
  
- Olarak bildirilen dönüştürmeler `implicit` gerekli olduğunda otomatik olarak gerçekleşir.  
  
- Olarak bildirilen dönüştürmeler `explicit` çağrılacak bir yayın gerektirir.  
  
- Tüm dönüştürmeler olarak bildirilmelidir `static`.  
  
## <a name="related-sections"></a>İlgili bölümler

 Daha fazla bilgi için:  
  
- [Dönüştürme İşleçleri Kullanma](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
- [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
- [Nasıl yapılır: Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
- [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
- [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
- [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Kullanıcı tanımlı C# ' de açık dönüştürmeler zincirleme](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
