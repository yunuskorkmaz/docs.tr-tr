---
title: Ad alanları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 893ac7bbfcfe159787789238c3142f34ac7ecf35
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423295"
---
# <a name="namespaces-c-programming-guide"></a>Ad Alanları (C# Programlama Kılavuzu)

Ad alanlarında, C# programlama iki yolla yoğun olarak kullanılır. İlk olarak, .NET Framework ad alanları, çok sayıda sınıfa gibi düzenlemek için kullanır:  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
`System` bir ad alanı ve `Console` bu ad alanındaki bir sınıftır. `using` Anahtar sözcüğü kullanılabilir, böylece tam adı, aşağıdaki örnekte olduğu gibi gerekli değildir:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
Daha fazla bilgi için [using yönergesi](../../language-reference/keywords/using-directive.md).  
  
İkinci olarak, kendi ad alanlarını bildirme sınıf ve yöntem adları büyük programlama projelerinde kapsamını denetlemenize yardımcı olabilir. Kullanım [ad alanı](../../language-reference/keywords/namespace.md) aşağıdaki örnekteki gibi bir ad alanı bildirmek için anahtar:  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Ad geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md).

## <a name="namespaces-overview"></a>Ad alanlarına genel bakış  

Ad alanları, aşağıdaki özelliklere sahiptir:  
  
- Bunlar, büyük kod projeleri düzenleyin.  
- Kullanarak sınırlandırılmıştır `.` işleci.  
- `using` Yönergesi obviates gereksinimi her sınıf ad alanının adını belirtin.  
- `global` Ad "Kök" ad alanı: `global::System` .NET için her zaman başvuracaktır <xref:System> ad alanı.  

## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ad Alanlarını Kullanma](using-namespaces.md)
- [Nasıl yapılır: Genel Namespace diğer adlarını kullanma](how-to-use-the-global-namespace-alias.md)
- [Nasıl yapılır: Kullanım My Namespace](how-to-use-the-my-namespace.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [using Yönergesi](../../language-reference/keywords/using-directive.md)
- [:: İşleç](../../language-reference/operators/namespace-alias-qualifer.md)
