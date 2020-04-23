---
title: '! (null-affgiving) operatörü - C# referans'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: f3d06dec42ba117cd30dbf4d05fa4a6f594e57e5
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82101987"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-affgiving) işleci (C# referans)

C# 8.0 ve daha sonra mevcuttur, `!` unary postfix işleci null-affgiving işlecidir. Etkin [bir geçersiz ek açıklama bağlamında,](../../nullable-references.md#nullable-annotation-context)bir başvuru türünün ifadesinin `x` şu olmadığını `null`bildirmek için `x!`null-affgiving işleci kullanırsınız: . Unary önek `!` işleci [mantıksal olumsuzlama işlecidir.](boolean-logical-operators.md#logical-negation-operator-)

Null-affgiving işleci çalışma zamanında hiçbir etkisi yoktur. Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış çözümlemesi etkiler. Çalışma zamanında, `x!` ifade altta yatan ifadenin `x`sonucunu değerlendirir.

Nullable başvuru türleri özelliği hakkında daha fazla bilgi için, [Nullable başvuru türleri](../builtin-types/nullable-reference-types.md)bakın.

## <a name="examples"></a>Örnekler

Null-affgiving işlecinin kullanım durumlardan biri bağımsız değişken doğrulama mantığını test etmektir. Örneğin, aşağıdaki sınıfı göz önünde bulundurun:

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucudaki doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Null-affgiving işleci olmadan, derleyici önceki kod için aşağıdaki `Warning CS8625: Cannot convert null literal to non-nullable reference type`uyarıyı oluşturur: . Null-affgiving işleci kullanarak, derlemeye geçişin `null` beklendiğini ve bu konuda uyarılmaması gerektiğini bildirirsiniz.

Bir ifadenin olamayacağını `null` ancak derleyicinin bunu fark edemediğini kesinlikle bildiğinizde, hükümsüz affedici işleci de kullanabilirsiniz. Aşağıdaki örnekte, `IsValid` yöntem dönerse, `true`bağımsız değişkeni değil `null` ve güvenli bir şekilde dereference olabilir:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Null-affgiving işleci olmadan, derleyici `p.Name` kod için aşağıdaki `Warning CS8602: Dereference of a possibly null reference`uyarıyı oluşturur: .

`IsValid` Yöntemi değiştirebilirseniz, derleyiciye `IsValid` yöntemin bir bağımsız değişkeninin yöntem döndürdüğünde `null` `true`olamayacağını bildirmek için [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz:

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

Önceki örnekte, `p` `null` `if` derleyicideyimin içinde olamayacağını öğrenmek için yeterli bilgiye sahip olduğundan, geçersiz affedici işleci kullanmanız gerekmez. Bir değişkenin null durumu hakkında ek bilgi sağlamanıza olanak tanıyan öznitelikler hakkında daha fazla bilgi için, [null beklentilerini tanımlamak için öznitelikleri içeren Yükseltme API'lerine](../attributes/nullable-analysis.md)bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [nullable başvuru türleri belirtimi taslağının](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md) [null-affgiving işleç](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Öğretici: Nullable başvuru türleri ile tasarım](../../tutorials/nullable-reference-types.md)
