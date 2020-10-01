---
description: New işleci-C# başvurusu
title: New işleci-C# başvurusu
ms.date: 10/02/2020
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3125f3d2c694dcfc5682ee482f3f76072ac3726d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609388"
---
# <a name="new-operator-c-reference"></a>New işleci (C# Başvurusu)

`new`İşleci, bir türün yeni bir örneğini oluşturur.

`new`Anahtar sözcüğünü [üye bildirim değiştiricisi](../keywords/new-modifier.md) veya [genel tür kısıtlaması](../keywords/new-constraint.md)olarak da kullanabilirsiniz.

## <a name="constructor-invocation"></a>Oluşturucu çağırma

Bir türün yeni bir örneğini oluşturmak için, genellikle işlecini kullanarak bu türdeki [oluşturuculardan](../../programming-guide/classes-and-structs/constructors.md) birini çağırın `new` :

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

[object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) `new` Aşağıdaki örnekte gösterildiği gibi, bir ifadede bir nesne oluşturmak ve başlatmak için işleciyle bir nesne veya koleksiyon başlatıcısı kullanabilirsiniz:

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

C# 9,0 ile başlayarak, Oluşturucu çağırma ifadeleri Target türünde. Diğer bir deyişle, bir ifadenin hedef türü biliniyorsa, aşağıdaki örnekte gösterildiği gibi, bir tür adını atlayabilirsiniz:

:::code language="csharp" source="snippets/shared/NewOperator.cs" id="SnippetTargetTyped":::

Yukarıdaki örnekte gösterildiği gibi, her zaman ayraçları hedef türü bir `new` ifadede kullanırsınız.

Bir ifadenin hedef türü `new` bilinmiyorsa (örneğin, [`var`](../keywords/var.md) anahtar sözcüğünü kullandığınızda), bir tür adı belirtmeniz gerekir.

## <a name="array-creation"></a>Dizi oluşturma

`new`Aşağıdaki örnekte gösterildiği gibi, bir dizi örneği oluşturmak için işlecini de kullanabilirsiniz:

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

Dizi başlatma söz dizimini kullanarak bir dizi örneği oluşturun ve tek bir deyimdeki öğelerle doldurun. Aşağıdaki örnek, bunu nasıl yapabilmenizin çeşitli yollarını göstermektedir:

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Anonim türlerin örneklenmesi

[Anonim türün](../../programming-guide/classes-and-structs/anonymous-types.md)bir örneğini oluşturmak için `new` işleç ve nesne Başlatıcısı söz dizimini kullanın:

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Tür örneklerinin yok edilmesi

Önceden oluşturulmuş tür örneklerini yok etmeniz gerekmez. Başvuru ve değer türlerinin örnekleri otomatik olarak yok edilir. Değer türlerinin örnekleri, bunları içeren bağlam yok edilir oluşturmaz yok edilir. Başvuru türlerinin örnekleri, son başvuru kaldırıldıktan sonra bazı belirtilmeyen bir zamanda [çöp toplayıcı](../../../standard/garbage-collection/index.md) tarafından yok edilir.

Yönetilmeyen kaynakları içeren tür örneklerinde, örneğin bir dosya tanıtıcısı için, içerdikleri kaynakların mümkün olan en kısa sürede serbest bırakılacağını sağlamak üzere belirleyici Temizleme kullanılması önerilir. Daha fazla bilgi için bkz <xref:System.IDisposable?displayProperty=nameWithType> . API başvurusu ve [using ekstresi](../keywords/using-statement.md) makalesi.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür işleci aşırı yükleyemez `new` .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni işleç](~/_csharplang/spec/expressions.md#the-new-operator) bölümüne bakın.

Hedef türü belirtilmiş bir ifade hakkında daha fazla bilgi için `new` bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-9.0/target-typed-new.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
