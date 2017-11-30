---
title: "Dönüşüm İşleçleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5277c1160c604ee56ff575df5bd603e115588d21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
-   [Dönüşüm işleçleri kullanma](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Nasıl yapılır: yapılar arasında kullanıcı tanımlı dönüşümler](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [açık](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [örtük](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [statik](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Convert>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Kullanıcı tanımlı zincirleme açık dönüşümler C#](http://go.microsoft.com/fwlink/?LinkId=112384)
