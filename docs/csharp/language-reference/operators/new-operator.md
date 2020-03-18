---
title: yeni operatör - C# referans
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 84131bc503a106961419a27fc4e3e0f2d82306a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846239"
---
# <a name="new-operator-c-reference"></a>yeni işleç (C# referans)

İşleç, `new` yeni bir tür örneği oluşturur.

Anahtar kelimeyi `new` üye bildirimi [değiştiricisi](../keywords/new-modifier.md) veya genel tür [kısıtlaması](../keywords/new-constraint.md)olarak da kullanabilirsiniz.

## <a name="constructor-invocation"></a>Yapıcı çağırma

Yeni bir tür örneği oluşturmak için, genellikle `new` işleci kullanarak bu tür [yapıcılardan](../../programming-guide/classes-and-structs/constructors.md) birini çağırırsınız:

[!code-csharp-interactive[invoke constructor](snippets/NewOperator.cs#Constructor)]

Aşağıdaki örnekte görüldüğü gibi, bir `new` [nesneyi](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) bir ifadede anlık olarak kullanmak ve başlatmak için işleçle birlikte bir nesne veya koleksiyon başlatılması nı kullanabilirsiniz:

[!code-csharp-interactive[constructor with initializer](snippets/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Dizi oluşturma

Aşağıdaki örnekte `new` görüldüğü gibi, bir dizi örneği oluşturmak için işleci de kullanırsınız:

[!code-csharp-interactive[create array](snippets/NewOperator.cs#Array)]

Dizi örneği oluşturmak ve tek bir deyimdeki öğelerle doldurmak için dizi başlatma sözdizimini kullanın. Aşağıdaki örnek, bunu nasıl yapabileceğinizi çeşitli şekillerde gösterir:

[!code-csharp-interactive[initialize array](snippets/NewOperator.cs#ArrayInitialization)]

Diziler hakkında daha fazla bilgi için [Diziler'e](../../programming-guide/arrays/index.md)bakın.

## <a name="instantiation-of-anonymous-types"></a>Anonim türlerin anında

Anonim bir [tür](../../programming-guide/classes-and-structs/anonymous-types.md)örneği oluşturmak `new` için, işleç ve nesne başharf sözdizimini kullanın:

[!code-csharp-interactive[anonymous type](snippets/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Tür örneklerinin yok edilmesi

Daha önce oluşturulmuş tür örneklerini yok etmek zorunda değilsiniz. Hem başvuru hem de değer türlerinin örnekleri otomatik olarak yok edilir. Değer türleri örnekleri, bunları içeren bağlam yok edilir yok edilir etmez yok edilir. Başvuru türleri örnekleri, son başvuru kaldırıldıktan sonra, çöp [toplayıcı](../../../standard/garbage-collection/index.md) tarafından belirtilmeyen bir zamanda yok edilir.

Yönetilmeyen kaynaklar içeren tür örnekleriiçin ( örneğin, bir dosya işlemesi, içerdikleri kaynakların mümkün olan en kısa sürede serbest bırakıldığından emin olmak için deterministik temizleme kullanılması önerilir. Daha fazla bilgi <xref:System.IDisposable?displayProperty=nameWithType> için API başvurusuna ve [kullanarak ifade](../keywords/using-statement.md) makalesine bakın.

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür `new` işleci aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yeni işleç](~/_csharplang/spec/expressions.md#the-new-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Nesne ve toplama başharfleri](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
