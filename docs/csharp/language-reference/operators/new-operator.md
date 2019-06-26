---
title: New işleci - C# başvurusu
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3d64c4805abe38c80301748ffa6b35fc87563b60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402513"
---
# <a name="new-operator-c-reference"></a>New işleci (C# Başvurusu)

`new` İşleci, bir türün yeni bir örneğini oluşturur.

Ayrıca `new` as anahtar sözcüğü bir [üye bildirim değiştirici](../keywords/new-modifier.md) veya [genel tür kısıtlaması](../keywords/new-constraint.md).

## <a name="constructor-invocation"></a>Oluşturucu çağrı

Bir türün yeni bir örneğini oluşturmak için genellikle aşağıdakilerden birini çağırma [oluşturucular](../../programming-guide/classes-and-structs/constructors.md) bu türü kullanarak `new` işleci:

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

Kullanabileceğiniz bir [nesne veya koleksiyon Başlatıcı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) ile `new` işleci örneği oluşturun ve aşağıdaki örnekte gösterildiği gibi bir ifade bir nesneyi başlatmak için:

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Dizi oluşturma

Ayrıca `new` işleci aşağıdaki örnekte gösterildiği gibi bir dizi örneği oluşturmak için:

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

Dizi başlatma söz dizimi, bir dizi örneği oluşturun ve öğeleri bir ifade ile doldurmak için kullanın. Aşağıdaki örnekte, nasıl yapabileceğiniz çeşitli yollar gösterir:

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Anonim türdeki örnek oluşturma

Bir örneğini oluşturmak için bir [anonim tür](../../programming-guide/classes-and-structs/anonymous-types.md), kullanın `new` işleci ve nesne Başlatıcısı sözdizimi:

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Tür örnekleri, yok etme

Daha önce oluşturulan tür örnekleri yok gerekmez. Hem başvuru ve değer türlerinin örnekleri otomatik olarak yok edilir. Değer türlerinin örnekleri, bunları içeren bir bağlam yok hemen sonra yok edilir. Başvuru türlerinin örnekleri tarafından edilir [çöp toplayıcı](../../../standard/garbage-collection/index.md) bunları son başvuruysa kaldırıldıktan sonra belirtilmeyen zaman.

Yönetilmeyen kaynakları içeren türleri için örneğin, bir dosya tanıtıcısı, belirlenimci içerdikleri kaynakları hemen serbest emin olmak için temizleme kullanmak istemiyorsunuz önerilir. Daha fazla bilgi için <xref:System.IDisposable?displayProperty=nameWithType> API Başvurusu ve [using deyimi](../keywords/using-statement.md) makalesi.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür aşırı yüklenemez `new` işleci.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [new işleci](~/_csharplang/spec/expressions.md#the-new-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [Nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
