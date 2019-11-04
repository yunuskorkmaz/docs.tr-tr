---
title: namespace anahtar sözcüğü C# -başvurusu
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: d1e30162cbce65193783d2fb0607900f209cc648
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422681"
---
# <a name="namespace-c-reference"></a>namespace (C# Başvurusu)

`namespace` anahtar sözcüğü, ilgili nesneler kümesini içeren bir kapsamı bildirmek için kullanılır. Kod öğelerini düzenlemek ve genel benzersiz türler oluşturmak için bir ad alanı kullanabilirsiniz.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Açıklamalar

Bir ad alanı içinde, aşağıdaki türlerden sıfır veya daha fazlasını bildirebilirsiniz:

- başka bir ad alanı

- [class](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](enum.md)

- [delegate](../builtin-types/reference-types.md)

Bir C# kaynak dosyasında açıkça bir ad alanı bildirip bildirmeyeceğinizi belirtir, derleyici varsayılan bir ad alanı ekler. Her zaman genel ad alanı olarak adlandırılan bu adlandırılmamış ad alanı her dosyada mevcuttur. Genel ad alanındaki herhangi bir tanımlayıcı, adlandırılmış bir ad alanında kullanılmak üzere kullanılabilir.

Ad alanları örtük olarak ortak erişime sahiptir ve bu değiştirilebilir değildir. Bir ad alanındaki öğelere atayabileceğiniz erişim değiştiricilerine ilişkin bir tartışma için bkz. [erişim değiştiricileri](access-modifiers.md).

İki veya daha fazla bildiriminde bir ad alanı tanımlamak mümkündür. Örneğin, aşağıdaki örnek, `MyCompany` ad alanının parçası olarak iki sınıfı tanımlar:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, iç içe bir ad alanında statik bir yöntemin nasıl çağrılacağını gösterir.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanları](~/_csharplang/spec/namespaces.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# anahtar sözcükleri](index.md)
- [using](using-directive.md)
- [statik kullanma](using-static.md)
- [Ad alanı diğer adı niteleyicisi `::`](../operators/namespace-alias-qualifier.md)
- [Ad alanları](../../programming-guide/namespaces/index.md)
