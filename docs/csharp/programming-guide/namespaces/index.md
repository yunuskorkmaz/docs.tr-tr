---
title: "Ad Alanları (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3eb645f5beb61d3cec97a70a54e660c65be52091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-c-programming-guide"></a>Ad Alanları (C# Programlama Kılavuzu)
Ad alanları, C# programlama iki yolla yoğun olarak kullanılır. İlk olarak, .NET Framework gibi birçok sınıflarından düzenlemek için ad alanları kullanır:  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System`bir ad alanıdır ve `Console` bu ad alanındaki bir sınıftır. `using` Anahtar sözcüğü kullanılabilir, böylece tam adı, aşağıdaki örnekte olduğu gibi gerekli değildir:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 Daha fazla bilgi için bkz: [using yönergesi](../../../csharp/language-reference/keywords/using-directive.md).  
  
 İkinci olarak, kendi ad alanlarını bildirme sınıfı ve yöntem adları büyük programlama projelerinde kapsamını denetlemenize yardımcı olabilir. Kullanım [ad alanı](../../../csharp/language-reference/keywords/namespace.md) aşağıdaki örnekteki gibi bir ad alanı bildirmek için anahtar sözcüğü:  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a>Ad alanları genel bakış  
 Ad alanları aşağıdaki özelliklere sahiptir:  
  
-   Bunlar büyük kod projeleri düzenleyin.  
  
-   Kullanarak sınırlandırılır `.` işleci.  
  
-   `using directive` Obviates gereksinimi her sınıf için ad alanı adını belirtin.  
  
-   `global` Ad alanı olan "Kök" ad: `global::System` her zaman .NET Framework ad alanına başvuruda bulunacak `System`.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Ad alanları hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Ad alanlarını kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Nasıl yapılır: Genel Namespace diğer adlarını kullanma](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [Nasıl yapılır: kullanım My Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Namespace anahtar sözcükler](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using yönergesi](../../../csharp/language-reference/keywords/using-directive.md)  
 [:: İşleci](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [. İşleci](../../../csharp/language-reference/operators/member-access-operator.md)
