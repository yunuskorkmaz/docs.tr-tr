---
title: temsilci işleci- C# başvuru
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1fe281776bd75d8fa869065cd24e85f04fec849d
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331775"
---
# <a name="delegate-operator-c-reference"></a>temsilci işleci (C# başvuru)

İşleci `delegate` , bir temsilci türüne dönüştürülebilen anonim bir yöntem oluşturur:

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

3 ile C# başlayarak [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) anonim bir işlev oluşturmak için daha kısa ve açıklayıcı bir yol sağlar. Lambda ifadesi oluşturmak için [= > işlecini](lambda-operator.md) kullanın:

[!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]

`delegate` İşlecini kullandığınızda parametre listesini atlayabilirsiniz. Bunu yaparsanız, oluşturulan anonim yöntem, aşağıdaki örnekte gösterildiği gibi, herhangi bir parametre listesiyle bir temsilci türüne dönüştürülebilir:

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

Bu, lambda ifadeleri tarafından desteklenmeyen anonim yöntemlerin tek işlevsellikleridir. Diğer tüm durumlarda, bir lambda ifadesi satır içi kod yazmak için tercih edilen bir yoldur. Lambda ifadelerinin özellikleri hakkında daha fazla bilgi için örneğin, dış değişkenleri yakalama, bkz. [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

Bir [temsilci türü](../builtin-types/reference-types.md#the-delegate-type)bildirmek `delegate` için anahtar sözcüğünü de kullanabilirsiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
