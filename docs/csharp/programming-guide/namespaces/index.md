---
title: Ad Alanları (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934879"
---
# <a name="namespaces-c-programming-guide"></a>Ad Alanları (C# Programlama Kılavuzu)
Ad alanlarında, C# programlama iki yolla yoğun olarak kullanılır. İlk olarak, .NET Framework ad alanları, çok sayıda sınıfa gibi düzenlemek için kullanır:  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System` bir ad alanı ve `Console` bu ad alanındaki bir sınıftır. `using` Anahtar sözcüğü kullanılabilir, böylece tam adı, aşağıdaki örnekte olduğu gibi gerekli değildir:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 Daha fazla bilgi için [using yönergesi](../../../csharp/language-reference/keywords/using-directive.md).  
  
 İkinci olarak, kendi ad alanlarını bildirme sınıf ve yöntem adları büyük programlama projelerinde kapsamını denetlemenize yardımcı olabilir. Kullanım [ad alanı](../../../csharp/language-reference/keywords/namespace.md) aşağıdaki örnekteki gibi bir ad alanı bildirmek için anahtar:  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a>Ad alanlarına genel bakış  
 Ad alanları, aşağıdaki özelliklere sahiptir:  
  
-   Bunlar, büyük kod projeleri düzenleyin.  
  
-   Kullanarak sınırlandırılmıştır `.` işleci.  
  
-   `using directive` Obviates gereksinimi her sınıf ad alanının adını belirtin.  
  
-   `global` Ad "Kök" ad alanı: `global::System` her zaman .NET Framework ad alanına başvuruda bulunacak `System`.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Ad alanları hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Ad Alanlarını Kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [Nasıl yapılır: Ad Alanımı Kullanma](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Ad Alanı Anahtar Sözcükleri](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using Yönergesi](../../../csharp/language-reference/keywords/using-directive.md)  
 [:: İşleci](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [. İşleç](../../../csharp/language-reference/operators/member-access-operator.md)
