---
title: New işleci-C# başvurusu
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: ed18c42cd28412a967c94a65c2a92b0b75097b52
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199735"
---
# <a name="new-operator-c-reference"></a>New işleci (C# Başvurusu)

İşleci `new` , bir türün yeni bir örneğini oluşturur.

`new` Anahtar sözcüğünü [üye bildirim değiştiricisi](../keywords/new-modifier.md) veya [genel tür kısıtlaması](../keywords/new-constraint.md)olarak da kullanabilirsiniz.

## <a name="constructor-invocation"></a>Oluşturucu çağırma

Bir türün yeni bir örneğini oluşturmak için, genellikle `new` işlecini kullanarak bu türdeki [oluşturuculardan](../../programming-guide/classes-and-structs/constructors.md) birini çağırın:

[!code-csharp-interactive[invoke constructor](snippets/NewOperator.cs#Constructor)]

Aşağıdaki örnekte gösterildiği gibi, bir ifadede bir nesne oluşturmak `new` ve başlatmak için işleciyle bir [nesne veya koleksiyon başlatıcısı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) kullanabilirsiniz:

[!code-csharp-interactive[constructor with initializer](snippets/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Dizi oluşturma

Aşağıdaki örnekte gösterildiği gibi `new` , bir dizi örneği oluşturmak için işlecini de kullanabilirsiniz:

[!code-csharp-interactive[create array](snippets/NewOperator.cs#Array)]

Dizi başlatma söz dizimini kullanarak bir dizi örneği oluşturun ve tek bir deyimdeki öğelerle doldurun. Aşağıdaki örnek, bunu nasıl yapabilmenizin çeşitli yollarını göstermektedir:

[!code-csharp-interactive[initialize array](snippets/NewOperator.cs#ArrayInitialization)]

Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Anonim türlerin örneklenmesi

[Anonim türün](../../programming-guide/classes-and-structs/anonymous-types.md)bir örneğini oluşturmak için `new` işleç ve nesne Başlatıcısı söz dizimini kullanın:

[!code-csharp-interactive[anonymous type](snippets/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Tür örneklerinin yok edilmesi

Önceden oluşturulmuş tür örneklerini yok etmeniz gerekmez. Başvuru ve değer türlerinin örnekleri otomatik olarak yok edilir. Değer türlerinin örnekleri, bunları içeren bağlam yok edilir oluşturmaz yok edilir. Başvuru türlerinin örnekleri, son başvuru kaldırıldıktan sonra bazı belirtilmeyen bir zamanda [çöp toplayıcı](../../../standard/garbage-collection/index.md) tarafından yok edilir.

Yönetilmeyen kaynakları içeren tür örneklerinde, örneğin bir dosya tanıtıcısı için, içerdikleri kaynakların mümkün olan en kısa sürede serbest bırakılacağını sağlamak üzere belirleyici Temizleme kullanılması önerilir. Daha fazla bilgi için bkz. <xref:System.IDisposable?displayProperty=nameWithType> API başvurusu ve [using ekstresi](../keywords/using-statement.md) makalesi.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür `new` işleci aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni işleç](~/_csharplang/spec/expressions.md#the-new-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
