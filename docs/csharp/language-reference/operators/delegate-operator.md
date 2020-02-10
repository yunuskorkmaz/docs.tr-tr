---
title: delegate işleci- C# başvuru
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 9a78faaccffa9e7d4bf2829d8dfa0fa62a788bba
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039036"
---
# <a name="delegate-operator-c-reference"></a>delegate işleci (C# başvuru)

`delegate` işleci, bir temsilci türüne dönüştürülebilen anonim bir yöntem oluşturur:

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> 3 ile C# başlayarak lambda ifadeleri anonim bir işlev oluşturmak için daha kısa ve açıklayıcı bir yol sağlar. Lambda ifadesi oluşturmak için [= > işlecini](lambda-operator.md) kullanın:
>
> [!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]
>
> Lambda ifadelerinin özellikleri hakkında daha fazla bilgi için örneğin, dış değişkenleri yakalama, bkz. [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

`delegate` işlecini kullandığınızda parametre listesini atlayabilirsiniz. Bunu yaparsanız, oluşturulan anonim yöntem, aşağıdaki örnekte gösterildiği gibi, herhangi bir parametre listesiyle bir temsilci türüne dönüştürülebilir:

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

Bu, lambda ifadeleri tarafından desteklenmeyen anonim yöntemlerin tek işlevsellikleridir. Diğer tüm durumlarda, bir lambda ifadesi satır içi kod yazmak için tercih edilen bir yoldur.

Ayrıca, bir [temsilci türü](../builtin-types/reference-types.md#the-delegate-type)bildirmek için `delegate` anahtar sözcüğünü kullanırsınız.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [= > işleci](lambda-operator.md)
