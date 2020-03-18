---
title: '! (null-affgiving) operatörü - C# referans'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 36bfa46cebd2b35c4985dfc23dbe84f8f5dc9201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846339"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-affgiving) işleci (C# referans)

C# 8.0 ve daha sonra mevcuttur, `!` unary postfix işleci null-affgiving işlecidir. Etkin [bir geçersiz ek açıklama bağlamında,](../../nullable-references.md#nullable-annotation-context)bir başvuru türünün ifadesinin `x` şu olmadığını `null`bildirmek için `x!`null-affgiving işleci kullanırsınız: . Unary önek `!` işleci [mantıksal olumsuzlama işlecidir.](boolean-logical-operators.md#logical-negation-operator-)

Null-affgiving işleci çalışma zamanında hiçbir etkisi yoktur. Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış çözümlemesi etkiler. Çalışma zamanında, `x!` ifade altta yatan ifadenin `x`sonucunu değerlendirir.

Nullable başvuru türleri özelliği hakkında daha fazla bilgi için, [Nullable başvuru türleri](../../nullable-references.md)bakın.

## <a name="examples"></a>Örnekler

Null-affgiving işlecinin kullanım durumlardan biri bağımsız değişken doğrulama mantığını test etmektir. Örneğin, aşağıdaki sınıfı göz önünde bulundurun:

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucudaki doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Null-affgiving işleci olmadan, derleyici önceki kod için aşağıdaki `Warning CS8625: Cannot convert null literal to non-nullable reference type`uyarıyı oluşturur: . Null-affgiving işleci kullanarak, derlemeye geçişin `null` beklendiğini ve bu konuda uyarılmaması gerektiğini bildirirsiniz.

Bir ifadenin olamayacağını `null` kesinlikle bildiğinizde, null-affgiving işlecide de kullanabilirsiniz, ancak derleyici bunu fark etmeyi başaramaz. Aşağıdaki örnekte, `IsValid` yöntem dönerse, `true`bağımsız değişkeni değil `null` ve güvenli bir şekilde dereference olabilir:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Null-affgiving işleci olmadan, derleyici `p.Name` kod için aşağıdaki `Warning CS8602: Dereference of a possibly null reference`uyarıyı oluşturur: .

`IsValid` Yöntemi değiştirebilirseniz, derleyiciye `IsValid` yöntemin bir bağımsız değişkeninin yöntem döndürdüğünde `null` `true`olamayacağını bildirmek için [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz:

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

Önceki örnekte, `p` `null` `if` derleyicideyimin içinde olamayacağını öğrenmek için yeterli bilgiye sahip olduğundan, geçersiz affedici işleci kullanmanız gerekmez. Bir değişkenin null durumu hakkında ek bilgi sağlamanıza olanak tanıyan öznitelikler hakkında daha fazla bilgi için, [null beklentilerini tanımlamak için öznitelikleri içeren Yükseltme API'lerine](../../nullable-attributes.md)bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [nullable başvuru türleri belirtimi taslağının](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md) [null-affgiving işleç](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Öğretici: Nullable başvuru türleri ile tasarım](../../tutorials/nullable-reference-types.md)
