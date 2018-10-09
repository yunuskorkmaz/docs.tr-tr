---
title: interface (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 4adc7ba106e0044ba6aff94ea3180d9c8e3ded7b
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48872949"
---
# <a name="interface-c-reference"></a>interface (C# Başvurusu)

Bir arabirim yalnızca ait imzaları içerir [yöntemleri](../../programming-guide/classes-and-structs/methods.md), [özellikleri](../../programming-guide/classes-and-structs/properties.md), [olayları](../../programming-guide/events/index.md) veya [dizin oluşturucular](../../programming-guide/indexers/index.md). Ara birimi uygulayan bir sınıfın veya yapının, ara birim tanımında belirtilen ara birim üyelerini uygulaması gerekir. Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.

Daha fazla bilgi ve örnekler için bkz. [arabirimleri](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Ara birim, bir ad alanının veya bir sınıfın üyesi olabilir ve aşağıdaki üyelerin imzalarını içerebilir:

- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)

- [Özellikler](../../programming-guide/classes-and-structs/using-properties.md)

- [Dizin Oluşturucular](../../programming-guide/indexers/using-indexers.md)

- [Olaylar](event.md)

Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir.

Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.

Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir. Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir.

Daha fazla ayrıntı ve kod örnekleri açık arabirim uygulaması üzerinde görmek [açık arabirim uygulaması](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, ara birim uygulamasını gösterir. Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir. `IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [Başvuru Türleri](reference-types.md)  
- [Arabirimler](../../programming-guide/interfaces/index.md)  
- [Özellikleri Kullanma](../../programming-guide/classes-and-structs/using-properties.md)  
- [Dizin Oluşturucular Kullanma](../../programming-guide/indexers/using-indexers.md)  
- [class](class.md)  
- [struct](struct.md)  
- [Arabirimler](../../programming-guide/interfaces/index.md)
