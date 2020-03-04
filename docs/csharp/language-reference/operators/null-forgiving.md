---
title: '! (null-forverme) işleci- C# başvuru'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 026c50d1696b29f8498d316ae106bc851ed16f6a
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239023"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-forverme) işleci (C# başvuru)

C# 8,0 ve sonraki sürümlerde bulunan birli sonek `!` işleci null-forverme işleçtir. Etkin bir [null yapılabilir ek açıklama bağlamında](../../nullable-references.md#nullable-annotation-context), bir başvuru türünün ifadesinin `x` `null`olmadığını bildirmek için null-forverme işlecini kullanırsınız: `x!`. Birli ön ek `!` işleci [mantıksal değilleme işleçtir](boolean-logical-operators.md#logical-negation-operator-).

Null-forverme işlecinin çalışma zamanında hiçbir etkisi yoktur. Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış analizini etkiler. Çalışma zamanında ifade `x!`, temel alınan ifade `x`sonucunu değerlendirir.

Null yapılabilir başvuru türleri özelliği hakkında daha fazla bilgi için bkz. [Nullable başvuru türleri](../../nullable-references.md).

## <a name="examples"></a>Örnekler

Null-forverme işlecinin kullanım çalışmalarından biri bağımsız değişken doğrulama mantığını test ediyor. Örneğin, aşağıdaki sınıfı göz önünde bulundurun:

[!code-csharp[Person class](~/samples/snippets/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucuda doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:

[!code-csharp[Person test](~/samples/snippets/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

Null-forverme işleci olmadan derleyici, önceki kod için şu uyarıyı üretir: `Warning CS8625: Cannot convert null literal to non-nullable reference type`. Null-forverme işlecini kullanarak, derleyiciye `null` geçtiğini ve hakkında uyarı vermemesini bilgilendirmelisiniz.

Ayrıca, bir ifadenin `null` olmadığını, ancak derleyicinin bunu tanımak üzere yönetmediğini kesin olarak bildiğiniz zaman, null-forverme işlecini de kullanabilirsiniz. Aşağıdaki örnekte, `IsValid` yöntemi `true`döndürürse, bağımsız değişkeni `null` değildir ve güvenli bir şekilde başvuru yapabilir:

[!code-csharp[Use null-forgiving operator](~/samples/snippets/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

Null-forverme işleci olmadan derleyici, `p.Name` kodu için aşağıdaki uyarıyı üretir: `Warning CS8602: Dereference of a possibly null reference`.

`IsValid` yöntemini değiştirebiliyorsanız, derleyiciye `IsValid` yönteminin bir bağımsız değişkeninin Yöntem `true`döndürdüğünde `null` olmadığını bildirmek için [Notnullıf](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz:

[!code-csharp[Use an attribute](~/samples/snippets/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

Yukarıdaki örnekte, derleyicinin `if` bildiriminde `null` `p` için yeterli bilgi içerdiğinden, null-forverme işlecini kullanmanız gerekmez. Bir değişkenin null durumu hakkında ek bilgi sağlamanıza olanak tanıyan öznitelikler hakkında daha fazla bilgi için bkz. [null beklentilerini tanımlamak Için API 'leri özniteliklerle yükseltme](../../nullable-attributes.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [Nullable başvuru türleri belirtiminin taslağının](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md) [null-forverme işleci](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Öğretici: null yapılabilir başvuru türleriyle tasarlayın](../../tutorials/nullable-reference-types.md)
