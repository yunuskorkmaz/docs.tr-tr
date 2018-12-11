---
title: Ad alanları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 4abdf8a0008ce50a89eb5f3ad3512a9579dc832a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236758"
---
# <a name="namespaces-c-programming-guide"></a>Ad Alanları (C# Programlama Kılavuzu)

Ad alanlarında, C# programlama iki yolla yoğun olarak kullanılır. İlk olarak, .NET Framework ad alanları, çok sayıda sınıfa gibi düzenlemek için kullanır:  
  
[!code-csharp[csProgGuide#22](../inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
`System` bir ad alanı ve `Console` bu ad alanındaki bir sınıftır. `using` Anahtar sözcüğü kullanılabilir, böylece tam adı, aşağıdaki örnekte olduğu gibi gerekli değildir:  
  
[!code-csharp[csProgGuide#1](../inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
[!code-csharp[csProgGuide#25](../inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
Daha fazla bilgi için [using yönergesi](../../language-reference/keywords/using-directive.md).  
  
İkinci olarak, kendi ad alanlarını bildirme sınıf ve yöntem adları büyük programlama projelerinde kapsamını denetlemenize yardımcı olabilir. Kullanım [ad alanı](../../language-reference/keywords/namespace.md) aşağıdaki örnekteki gibi bir ad alanı bildirmek için anahtar:  
  
[!code-csharp[csProgGuideNamespaces#6](codesnippet/CSharp/index_4.cs)]

Ad geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md).

## <a name="namespaces-overview"></a>Ad alanlarına genel bakış  

Ad alanları, aşağıdaki özelliklere sahiptir:  
  
- Bunlar, büyük kod projeleri düzenleyin.  
- Kullanarak sınırlandırılmıştır `.` işleci.  
- `using` Yönergesi obviates gereksinimi her sınıf ad alanının adını belirtin.  
- `global` Ad "Kök" ad alanı: `global::System` .NET için her zaman başvuracaktır <xref:System> ad alanı.  

## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Ad Alanlarını Kullanma](using-namespaces.md)
- [Nasıl yapılır: Genel Namespace diğer adlarını kullanma](how-to-use-the-global-namespace-alias.md)
- [Nasıl yapılır: Kullanım My Namespace](how-to-use-the-my-namespace.md)
- [C# Programlama Kılavuzu](../index.md)  
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [Ad Alanı Anahtar Sözcükleri](../../language-reference/keywords/namespace-keywords.md)  
- [using Yönergesi](../../language-reference/keywords/using-directive.md)  
- [:: İşleç](../../language-reference/operators/namespace-alias-qualifer.md)  
- [. İşleç](../../language-reference/operators/member-access-operator.md)
