---
description: '! (null-forverme) işleci-C# başvurusu'
title: '! (null-forverme) işleci-C# başvurusu'
ms.date: 10/11/2019
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 5418f96a3b4515224c49a1c1aa38784c348a86db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516157"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-forverme) işleci (C# Başvurusu)

C# 8,0 ve üzeri sürümlerde, birli sonek `!` operatörü null-forverme işleçtir. Etkin bir [null yapılabilir ek açıklama bağlamında](../../nullable-references.md#nullable-annotation-context), bir başvuru türünün ifadesinin bu ifade olduğunu bildirmek için null-forverme işlecini kullanırsınız `x` `null` : `x!` . Birli önek `!` işleci, [mantıksal değilleme işleçtir](boolean-logical-operators.md#logical-negation-operator-).

Null-forverme işlecinin çalışma zamanında hiçbir etkisi yoktur. Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış analizini etkiler. Çalışma zamanında ifade, `x!` temel alınan ifadenin sonucu olarak değerlendirilir `x` .

> [!NOTE]
> C# 8 ' de, null-forverme işleci önceki [null koşullu](member-access-operators.md#null-conditional-operators--and-) işlemlerin listesini sonlandırır. Örneğin, ifadesi `x?.y!.z` olarak ayrıştırılır `(x?.y)!.z` . Bu yorum nedeniyle,, `z` olsa bile değerlendirilir, bu da `x` `null` bir ile sonuçlanabilir <xref:System.NullReferenceException> .

Null yapılabilir başvuru türleri özelliği hakkında daha fazla bilgi için bkz. [Nullable başvuru türleri](../builtin-types/nullable-reference-types.md).

## <a name="examples"></a>Örnekler

Null-forverme işlecinin kullanım çalışmalarından biri bağımsız değişken doğrulama mantığını test ediyor. Örneğin, aşağıdaki sınıfı göz önünde bulundurun:

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucuda doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

Null-forverme işleci olmadan derleyici, önceki kod için aşağıdaki uyarıyı oluşturur: `Warning CS8625: Cannot convert null literal to non-nullable reference type` . Null-forverme işlecini kullanarak, derleyiciye iletme `null` beklendiğine ve hakkında uyarı olmaması gerektiğini bilgilendirmelisiniz.

Ayrıca, bir ifadenin `null` olmadığını kesin olarak bildiğiniz ancak derleyici bunu tanımak için yönetmediğinden null-forverme işlecini de kullanabilirsiniz. Aşağıdaki örnekte, `IsValid` yöntemi döndürürse `true` , bağımsız değişkeni değildir `null` ve güvenli bir şekilde başvurusu yapabilirsiniz:

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

Null-forverme işleci olmadan derleyici, kod için aşağıdaki uyarıyı oluşturur `p.Name` : `Warning CS8602: Dereference of a possibly null reference` .

Yöntemi değiştirebiliyorsanız `IsValid` , derleyicinin yöntemin bir bağımsız değişkeninin yöntemin döndürdüğü zaman değiştiremediğini bildirmek Için [notnullıf](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz `IsValid` `null` `true` :

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

Önceki örnekte, derleyicinin, ifadenin içinde yer alamaz bilgi almak için yeterli bilgisi olduğundan, null-forverme işlecini kullanmanız gerekmez `p` `null` `if` . Bir değişkenin null durumu hakkında ek bilgi sağlamanıza olanak tanıyan öznitelikler hakkında daha fazla bilgi için bkz. [null beklentilerini tanımlamak Için API 'leri özniteliklerle yükseltme](../attributes/nullable-analysis.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [Nullable başvuru türleri belirtiminin taslağının](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md) [null-forverme işleci](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Öğretici: null yapılabilir başvuru türleriyle tasarlayın](../../tutorials/nullable-reference-types.md)
