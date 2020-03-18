---
title: namespace anahtar kelime - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: b35f0a2a5cc0b2895b491d4ee24f89955f4b8fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625806"
---
# <a name="namespace-c-reference"></a>namespace (C# Başvurusu)

Anahtar `namespace` kelime, ilgili nesneler kümesini içeren bir kapsamı bildirmek için kullanılır. Kod öğelerini düzenlemek ve genel olarak benzersiz türler oluşturmak için bir ad alanı kullanabilirsiniz.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Açıklamalar

Ad alanı içinde, aşağıdaki türlerden sıfır veya daha fazlasını bildirebilirsiniz:

- başka bir ad alanı

- [Sınıfı](class.md)

- [Arabirim](interface.md)

- [Yapı](../builtin-types/struct.md)

- [Enum](../builtin-types/enum.md)

- [temsilci](../builtin-types/reference-types.md#the-delegate-type)

C# kaynak dosyasında bir ad alanını açıkça beyan edin veya bildirmeseniz de, derleyici varsayılan bir ad alanı ekler. Bu adsız ad alanı, bazen genel ad alanı olarak da adlandırılır, her dosyada bulunur. Genel ad alanındaki herhangi bir tanımlayıcı adlandırılmış bir ad alanında kullanılabilir.

Ad alanları örtülü olarak genel erişime sahiptir ve bu değiştirilemez. Erişim değiştiriciler bir tartışma için bir ad alanı öğeleri atayabilirsiniz, [Erişim Değiştiriciler](access-modifiers.md)bakın.

İki veya daha fazla bildirimde bir ad alanı tanımlamak mümkündür. Örneğin, aşağıdaki örnek, iki sınıfı ad `MyCompany` alanının bir parçası olarak tanımlar:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, iç içe geçmiş bir ad alanında statik bir yöntemin nasıl çağrılmasını gösterir.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Ad Alanları](~/_csharplang/spec/namespaces.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Kullan -arak](using-directive.md)
- [statik kullanarak](using-static.md)
- [Ad alanı diğer ad niteleyici`::`](../operators/namespace-alias-qualifier.md)
- [Ad Alanları](../../programming-guide/namespaces/index.md)
