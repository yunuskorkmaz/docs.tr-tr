---
title: Ad alanları C# -Programlama Kılavuzu
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: e3e9dc22186e5e319c63e34bd85e5e317effde88
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712019"
---
# <a name="namespaces-c-programming-guide"></a>Ad Alanları (C# Programlama Kılavuzu)

Ad alanları, C# programlamada iki şekilde çok fazla kullanılır. İlk olarak .NET Framework, aşağıdaki gibi birçok sınıfını düzenlemek için ad alanlarını kullanır:  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
`System` bir ad alanıdır ve `Console` bu ad alanındaki bir sınıftır. `using` anahtar sözcüğü, aşağıdaki örnekte olduğu gibi, tüm adı gerekli olmaması için kullanılabilir:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
Daha fazla bilgi için bkz. [using yönergesi](../../language-reference/keywords/using-directive.md).  
  
İkincisi, kendi ad alanlarınızı bildirmek daha büyük programlama projelerindeki sınıf ve yöntem adlarının kapsamını denetlemenize yardımcı olabilir. Aşağıdaki örnekte olduğu gibi bir ad alanı bildirmek için [Namespace](../../language-reference/keywords/namespace.md) anahtar sözcüğünü kullanın:  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Ad alanının adı geçerli C# bir [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.

## <a name="namespaces-overview"></a>Ad alanlarına genel bakış  

Ad alanları aşağıdaki özelliklere sahiptir:  
  
- Büyük kod projelerini düzenler.  
- `.` işleci kullanılarak sınırlandırılır.  
- `using` yönergesi, her sınıf için ad alanının adını belirtmek için gereksinimi obviates.  
- `global` ad alanı "root" ad alanıdır: `global::System` her zaman .NET <xref:System> ad alanına başvuracaktır.  

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanları](~/_csharplang/spec/namespaces.md) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ad Alanlarını Kullanma](using-namespaces.md)
- [My ad alanım 'ı kullanma](how-to-use-the-my-namespace.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [using Yönergesi](../../language-reference/keywords/using-directive.md)
- [:: İşleci](../../language-reference/operators/namespace-alias-qualifier.md)
