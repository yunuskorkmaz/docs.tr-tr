---
title: arabirim- C# başvuru
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625858"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface"::: (C# başvuru)

Arabirim, bir sözleşmeyi tanımlar. Bu sözleşmeyi uygulayan [`class`](class.md) veya [`struct`](../builtin-types/struct.md) , arabirimde tanımlı üyelerin bir uygulamasını sağlaması gerekir. 8,0 ile C# başlayarak bir arabirim, Üyeler için varsayılan bir uygulama tanımlayabilir. Ayrıca, yaygın işlevselliğe tek bir uygulama sağlamak için [`static`](static.md) üyelerini tanımlayabilir.

Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.

Daha fazla bilgi ve örnek için bkz. [arabirimler](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Arabirim, bir ad alanı veya sınıf üyesi olabilir. Arabirim bildirimi, aşağıdaki üyelerin bildirimlerini (herhangi bir uygulama olmadan imzalar) içerebilir:

- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)
- [Özellikler](../../programming-guide/classes-and-structs/using-properties.md)
- [Dizin Oluşturucular](../../programming-guide/indexers/using-indexers.md)
- [Olaylar](event.md)

Bu önceki üye bildirimleri genellikle gövde içermez. 8,0 ile C# başlayarak bir arabirim üyesi bir gövde bildirebilir. Bu, varsayılan bir *uygulama*olarak adlandırılır. Gövdeler içeren Üyeler, arabirimin geçersiz kılan bir uygulama sağlamayan sınıflar ve yapılar için "varsayılan" bir uygulama sağlamasına izin verir. Ayrıca, 8,0 ile C# başlayarak bir arabirim şunlar olabilir:

- [Sabitler](const.md)
- [İşleçler](../operators/operator-overloading.md)
- [Statik Oluşturucu](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [İç içe türler](../../programming-guide/classes-and-structs/nested-types.md)
- [Statik alanlar, Yöntemler, özellikler, Dizin oluşturucular ve olaylar](static.md)
- Açık arabirim uygulama sözdizimini kullanan üye bildirimleri.
- Açık erişim değiştiricileri (varsayılan erişim [`public`](access-modifiers.md)).

Arabirimler örnek durumu içermeyebilir. Statik alanlara artık izin verildiğinde, arabirimlerde örnek alanlarına izin verilmez. [Örnek otomatik Özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) , açıkça gizli bir alan bildirdiklerinde arabirimlerde desteklenmez. Bu kuralın Özellik bildirimlerinde hafif bir etkisi vardır. Bir arabirim bildiriminde, aşağıdaki kod bir `class` veya `struct`olduğu için otomatik olarak uygulanan bir özellik bildirmiyor. Bunun yerine, varsayılan bir uygulamasına sahip olmayan ancak arabirimini uygulayan herhangi bir türde uygulanması gereken bir özellik bildirir:

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir. Bir arabirim Temel arabirimde uygulanan [bir yöntemi geçersiz kıldığında](override.md) , [Açık arabirim uygulama](../../programming-guide/interfaces/explicit-interface-implementation.md) söz dizimini kullanmalıdır.

Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.

Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir. Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir. Ayrıca, varsayılan arabirim üyelerine yalnızca arabirimin bir örneği üzerinden erişilebilir.

Açık arabirim uygulama hakkında daha fazla bilgi için bkz. [Açık arabirim uygulama](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, ara birim uygulamasını gösterir. Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir. `IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [varsayılan arabirim üyeleri C# ](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md) için [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) ve özellik belirtiminin [arabirimler](~/_csharplang/spec/interfaces.md) bölümüne bakın-8,0

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Başvuru Türleri](reference-types.md)
- [Arabirimler](../../programming-guide/interfaces/index.md)
- [Özellikleri Kullanma](../../programming-guide/classes-and-structs/using-properties.md)
- [Dizin Oluşturucular Kullanma](../../programming-guide/indexers/using-indexers.md)
- [Arabirimler](../../programming-guide/interfaces/index.md)
