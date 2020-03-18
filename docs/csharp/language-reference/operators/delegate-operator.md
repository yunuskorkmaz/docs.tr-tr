---
title: temsilci operatörü - C# referansı
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1dd27fe5fdfdc1bc8a63e1298da00d252e800a72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847345"
---
# <a name="delegate-operator-c-reference"></a>temsilci işleci (C# referansı)

İşleç, `delegate` temsilci türüne dönüştürülebilecek anonim bir yöntem oluşturur:

[!code-csharp-interactive[anonymous method](snippets/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> C# 3 ile başlayarak lambda ifadeleri anonim bir işlev oluşturmak için daha kısa ve anlamlı bir yol sağlar. Lambda ifadesini oluşturmak için [=> işleci](lambda-operator.md) kullanın:
>
> [!code-csharp-interactive[lambda expression](snippets/DelegateOperator.cs#Lambda)]
>
> Lambda ifadelerinin özellikleri hakkında daha fazla bilgi için, örneğin, dış değişkenleri yakalama, [Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md)bakın.

İşleç `delegate` kullandığınızda, parametre listesini atlaabilirsiniz. Bunu yaparsanız, oluşturulan anonim yöntem, aşağıdaki örnekte görüldüğü gibi, herhangi bir parametre listesi içeren bir temsilci türüne dönüştürülebilir:

[!code-csharp-interactive[no parameter list](snippets/DelegateOperator.cs#WithoutParameterList)]

Lambda ifadeleri tarafından desteklenmeyen anonim yöntemlerin tek işlevselliği bu. Diğer tüm durumlarda, lambda ifadesi satır içinde kod yazmak için tercih edilen bir yoldur.

Ayrıca bir `delegate` [temsilci türü](../builtin-types/reference-types.md#the-delegate-type)bildirmek için anahtar kelime kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [=> operatörü](lambda-operator.md)
