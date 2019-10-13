---
title: '! (null-forverme) işleci- C# başvuru'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291727"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-forverme) işleci (C# başvuru)

C# 8,0 ve üzeri sürümlerde bulunan birli sonek `!` işleci null-forverme işleçtir. Etkin bir [null yapılabilir ek açıklama bağlamında](../../nullable-references.md#nullable-annotation-context), bir başvuru türünün `x` ' inin null olmadığını bildirmek için null-forverme işlecini kullanırsınız: `x!`. Birli önek `!` işleci bir [mantıksal değilleme işleçtir](boolean-logical-operators.md#logical-negation-operator-).

Null-forverme işlecinin çalışma zamanında hiçbir etkisi yoktur. Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış analizini etkiler. Çalışma zamanında, `x!` ifadesi temel alınan `x` ifadesinin sonucu olarak değerlendirilir.

Null yapılabilir başvuru türleri özelliği hakkında daha fazla bilgi için bkz. [Nullable başvuru türleri](../../nullable-references.md).

## <a name="examples"></a>Örnekler

Null-forverme işlecinin kullanım çalışmalarından biri bağımsız değişken doğrulama mantığını test ediyor. Örneğin, aşağıdaki sınıfı göz önünde bulundurun:

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucuda doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

Null-forverme işleci olmadan derleyici, önceki kod için şu uyarıyı üretir: `Warning CS8625: Cannot convert null literal to non-nullable reference type`. Null anlayalım işlecinin kullanımıyla, derleyicinin `null` ' ın geçtiğini ve hakkında uyarı olmaması gerektiğini bilmesini sağlayabilirsiniz.

Ayrıca, bir ifadenin `null` olamaz, ancak derleyicinin bunu tanıması için yönetmediğini kesin bir şekilde öğrendiğinizde null-forverme işlecini de kullanabilirsiniz. Aşağıdaki örnekte, `IsValid` yöntemi `true` döndürürse, bağımsız değişkeni `null` ' dir ve güvenle başvuru yapabilirsiniz:

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

Null-forverme işleci olmadan derleyici `p.Name` kodu için şu uyarıyı üretir: `Warning CS8602: Dereference of a possibly null reference.`.

@No__t-0 yöntemini değiştirebiliyorsanız, derleyicinin `IsValid` yönteminin bir bağımsız değişkeninin, yöntem `true` ' i döndürdüğünde `null` olmadığını bilmesini sağlamak için [Notnullıf](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz:

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

Önceki örnekte, derleyicinin bu @no__t bulmak için yeterli bilgisi olduğundan, null-forverme işlecini kullanmanız gerekmez-0 ' ın `if` ifadesinde `null` olamaz. Bir değişkenin null durumu hakkında ek bilgi belirtmenize izin veren öznitelikler hakkında daha fazla bilgi için bkz. [null beklentilerini tanımlamak Için API 'leri özniteliklerle yükseltme](../../nullable-attributes.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C#işletmenlerinin](index.md)
- [Öğretici: null yapılabilir başvuru türleriyle tasarlayın](../../tutorials/nullable-reference-types.md)
