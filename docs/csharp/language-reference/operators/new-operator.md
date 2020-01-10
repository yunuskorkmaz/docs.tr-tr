---
title: Yeni operatör- C# başvuru
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: beb55f0765e7f9090f0587f1d2a06cf03ea90ab8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712669"
---
# <a name="new-operator-c-reference"></a>New işleci (C# başvuru)

`new` işleci, bir türün yeni bir örneğini oluşturur.

`new` anahtar sözcüğünü [üye bildirimi değiştiricisi](../keywords/new-modifier.md) veya [genel tür kısıtlaması](../keywords/new-constraint.md)olarak da kullanabilirsiniz.

## <a name="constructor-invocation"></a>Oluşturucu çağırma

Bir türün yeni bir örneğini oluşturmak için, genellikle `new` işlecini kullanarak bu türdeki [oluşturuculardan](../../programming-guide/classes-and-structs/constructors.md) birini çağırabilirsiniz:

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

Aşağıdaki örnekte gösterildiği gibi, tek bir ifadede bir nesne oluşturmak ve başlatmak için `new` işleçle bir [nesne veya koleksiyon başlatıcısı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) kullanabilirsiniz:

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Dizi oluşturma

Aşağıdaki örnekte gösterildiği gibi, bir dizi örneği oluşturmak için `new` işlecini de kullanabilirsiniz:

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

Dizi başlatma söz dizimini kullanarak bir dizi örneği oluşturun ve tek bir deyimdeki öğelerle doldurun. Aşağıdaki örnek, bunu nasıl yapabilmenizin çeşitli yollarını göstermektedir:

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Anonim türlerin örneklenmesi

[Anonim türün](../../programming-guide/classes-and-structs/anonymous-types.md)bir örneğini oluşturmak için `new` işlecini ve nesne Başlatıcısı sözdizimini kullanın:

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Tür örneklerinin yok edilmesi

Önceden oluşturulmuş tür örneklerini yok etmeniz gerekmez. Başvuru ve değer türlerinin örnekleri otomatik olarak yok edilir. Değer türlerinin örnekleri, bunları içeren bağlam yok edilir oluşturmaz yok edilir. Başvuru türlerinin örnekleri, en son başvuru kaldırıldıktan sonra, belirlenemeyen sürede [çöp toplayıcı](../../../standard/garbage-collection/index.md) tarafından yok edilir.

Yönetilmeyen kaynakları içeren tür örneklerinde, örneğin bir dosya tanıtıcısı için, içerdikleri kaynakların mümkün olan en kısa sürede serbest bırakılacağını sağlamak üzere belirleyici Temizleme kullanılması önerilir. Daha fazla bilgi için bkz. <xref:System.IDisposable?displayProperty=nameWithType> API başvurusu ve [using açıklaması](../keywords/using-statement.md) makalesi.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür `new` işlecini aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni işleç](~/_csharplang/spec/expressions.md#the-new-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
