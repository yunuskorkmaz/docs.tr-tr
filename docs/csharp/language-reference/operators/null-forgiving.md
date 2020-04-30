---
title: '! (null-forverme) işleci-C# başvurusu'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 772f37f1fc7446eae66f0cd0f12adb5e2e41997d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595955"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-forverme) işleci (C# Başvurusu)

C# 8,0 ve üzeri sürümlerde, birli sonek `!` operatörü null-forverme işleçtir. Etkin bir [null yapılabilir ek açıklama bağlamında](../../nullable-references.md#nullable-annotation-context), bir başvuru türünün ifadesinin bu ifade `x` olduğunu bildirmek için null-forverme işlecini kullanırsınız `null`:. `x!` Birli önek `!` işleci, [mantıksal değilleme işleçtir](boolean-logical-operators.md#logical-negation-operator-).

Null-forverme işlecinin çalışma zamanında hiçbir etkisi yoktur. Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış analizini etkiler. Çalışma zamanında ifade `x!` , temel alınan ifadenin `x`sonucu olarak değerlendirilir.

> [!NOTE]
> C# 8 ' de null-forverme işleci, [null koşullu işleçlerle](member-access-operators.md#null-conditional-operators--and-) beklenmedik şekilde etkileşime girer. İfade `x?.y!.z` olarak `(x?.y)!.z`ayrıştırılır. Bu yorum `z` nedeniyle `x` , `null`olsa bile değerlendirilir, bu da bir <xref:System.NullReferenceException>ile sonuçlanabilir.

Null yapılabilir başvuru türleri özelliği hakkında daha fazla bilgi için bkz. [Nullable başvuru türleri](../builtin-types/nullable-reference-types.md).

## <a name="examples"></a>Örnekler

Null-forverme işlecinin kullanım çalışmalarından biri bağımsız değişken doğrulama mantığını test ediyor. Örneğin, aşağıdaki sınıfı göz önünde bulundurun:

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucuda doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Null-forverme işleci olmadan derleyici, önceki kod için aşağıdaki uyarıyı oluşturur: `Warning CS8625: Cannot convert null literal to non-nullable reference type`. Null-forverme işlecini kullanarak, derleyiciye iletme `null` beklendiğine ve hakkında uyarı olmaması gerektiğini bilgilendirmelisiniz.

Ayrıca, bir ifadenin olmadığını kesin olarak bildiğiniz `null` ancak derleyici bunu tanımak için yönetmediğinden null-forverme işlecini de kullanabilirsiniz. Aşağıdaki örnekte, `IsValid` yöntemi döndürürse `true`, bağımsız değişkeni değildir `null` ve güvenli bir şekilde başvurusu yapabilirsiniz:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Null-forverme işleci olmadan derleyici, `p.Name` kod için aşağıdaki uyarıyı oluşturur:. `Warning CS8602: Dereference of a possibly null reference`

`IsValid` Yöntemi değiştirebiliyorsanız, derleyicinin yöntemin bir bağımsız değişkeninin `IsValid` yöntemin döndürdüğü `null` `true`zaman değiştiremediğini bildirmek için [notnullıf](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz:

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

Önceki örnekte, derleyicinin, `p` `null` `if` ifadenin içinde yer alamaz bilgi almak için yeterli bilgisi olduğundan, null-forverme işlecini kullanmanız gerekmez. Bir değişkenin null durumu hakkında ek bilgi sağlamanıza olanak tanıyan öznitelikler hakkında daha fazla bilgi için bkz. [null beklentilerini tanımlamak Için API 'leri özniteliklerle yükseltme](../attributes/nullable-analysis.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [Nullable başvuru türleri belirtiminin taslağının](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md) [null-forverme işleci](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Öğretici: null yapılabilir başvuru türleriyle tasarlayın](../../tutorials/nullable-reference-types.md)
