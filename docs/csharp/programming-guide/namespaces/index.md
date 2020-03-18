---
title: İsim Alanları - C# Programlama Kılavuzu
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937607"
---
# <a name="namespaces-c-programming-guide"></a>Ad Alanları (C# Programlama Kılavuzu)

Ad boşlukları C# programlamada iki şekilde kullanılır. İlk olarak, .NET birçok sınıfını düzenlemek için ad boşluklarını aşağıdaki gibi kullanır:  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System>bir ad alanıdır ve <xref:System.Console> bu ad alanında bir sınıftır. Anahtar `using` kelime, aşağıdaki örnekte olduğu gibi tam adın gerekli olmaması için kullanılabilir:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

Daha fazla bilgi için [bkz.](../../language-reference/keywords/using-directive.md)

İkinci olarak, kendi ad alanlarınızı bildirmek, daha büyük programlama projelerinde sınıf ve yöntem adlarının kapsamını denetlemenize yardımcı olabilir. Aşağıdaki örnekte olduğu gibi ad alanı bildirmek için [ad alanı](../../language-reference/keywords/namespace.md) anahtar sözcük lerini kullanın:

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Ad alanının adı geçerli bir C# [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.

## <a name="namespaces-overview"></a>Ad boşluklarına genel bakış

Ad alanları aşağıdaki özelliklere sahiptir:

- Büyük kod projeleri düzenlerler.
- `.` İşleç kullanılarak sınırlandırılırlar.
- Yönerge, `using` her sınıf için ad alanının adını belirtme gereksinimini ortadan uzatır.
- `global` Ad alanı "kök" ad alanıdır: `global::System` her zaman <xref:System> .NET ad alanına başvurur.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Ad Alanları](~/_csharplang/spec/namespaces.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ad Alanlarını Kullanma](using-namespaces.md)
- [My ad alanını kullanma](how-to-use-the-my-namespace.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [using Yönergesi](../../language-reference/keywords/using-directive.md)
- [:: Operatör](../../language-reference/operators/namespace-alias-qualifier.md)
