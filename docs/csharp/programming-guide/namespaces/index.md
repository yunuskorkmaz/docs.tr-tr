---
title: Ad alanları-C# Programlama Kılavuzu
description: C# programlamada ad alanları hakkında bilgi edinin. Bkz. ad alanı özelliklerine genel bakış ve ek kaynakları görüntüleme.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: fca2c641520bd9cd19a48bff2119a6f09c3713ea
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382106"
---
# <a name="namespaces-c-programming-guide"></a>Ad Alanları (C# Programlama Kılavuzu)

Ad alanları, C# programlamada iki şekilde çok fazla kullanılır. İlk olarak, .NET, aşağıdaki gibi birçok sınıfını düzenlemek için ad alanlarını kullanır:  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System>bir ad alanıdır ve <xref:System.Console> Bu ad alanındaki bir sınıftır. `using`Anahtar sözcüğü, aşağıdaki örnekte olduğu gibi, tüm adı gerekli olmaması için kullanılabilir:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

Daha fazla bilgi için bkz. [using yönergesi](../../language-reference/keywords/using-directive.md).

İkincisi, kendi ad alanlarınızı bildirmek daha büyük programlama projelerindeki sınıf ve yöntem adlarının kapsamını denetlemenize yardımcı olabilir. Aşağıdaki örnekte olduğu gibi bir ad alanı bildirmek için [Namespace](../../language-reference/keywords/namespace.md) anahtar sözcüğünü kullanın:

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Ad alanının adı geçerli bir C# [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.

## <a name="namespaces-overview"></a>Ad alanlarına genel bakış

Ad alanları aşağıdaki özelliklere sahiptir:

- Büyük kod projelerini düzenler.
- İşleci kullanılarak sınırlandırılır `.` .
- `using`Yönergesi, her sınıf için ad alanının adını belirtmek için gereksinimi obviates.
- `global`Ad alanı "root" ad alanıdır: `global::System` her zaman .net ad alanına başvurur <xref:System> .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [namespaces](~/_csharplang/spec/namespaces.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ad alanlarını kullanma](using-namespaces.md)
- [My ad alanını kullanma](how-to-use-the-my-namespace.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [using Yönergesi](../../language-reference/keywords/using-directive.md)
- [:: İşleci](../../language-reference/operators/namespace-alias-qualifier.md)
