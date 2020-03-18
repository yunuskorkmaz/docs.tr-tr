---
title: arayüz - C# Referans
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625858"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface":::(C# Referans)

Arabirim bir sözleşme tanımlar. Bu [`class`](class.md) [`struct`](../builtin-types/struct.md) sözleşmeyi uygulayan herhangi biri veya bu sözleşme, arabirimde tanımlanan üyelerin uygulanmasını sağlamalıdır. C# 8.0 ile başlayarak, bir arabirim üyeler için varsayılan bir uygulama tanımlayabilir. Ortak işlevsellik [`static`](static.md) için tek bir uygulama sağlamak için üyeleri de tanımlayabilir.

Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.

Daha fazla bilgi ve örnekler için [Arabirimler'e](../../programming-guide/interfaces/index.md)bakın.

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Arabirim, ad alanının veya sınıfın üyesi olabilir. Arabirim bildirimi, aşağıdaki üyelerin bildirimlerini (herhangi bir uygulama olmaksızın imzalar) içerebilir:

- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)
- [Özellikler](../../programming-guide/classes-and-structs/using-properties.md)
- [Dizin Oluşturucular](../../programming-guide/indexers/using-indexers.md)
- [Olaylar](event.md)

Bu önceki üye bildirimleri genellikle bir gövde içermez. C# 8.0 ile başlayarak, bir arabirim üyesi gövde bildirebilir. Buna varsayılan *uygulama*denir. Gövdeleri olan üyeler, arabirimin, geçersiz bir uygulama sağlamayan sınıflar ve yapıstları için "varsayılan" bir uygulama sağlamasına izin verir. Buna ek olarak, C# 8.0 ile başlayan bir arayüz şunları içerebilir:

- [Sabitler](const.md)
- [İşleçler](../operators/operator-overloading.md)
- [Statik yapıcı](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [İç içe türleri](../../programming-guide/classes-and-structs/nested-types.md)
- [Statik alanlar, yöntemler, özellikler, dizinleyiciler ve olaylar](static.md)
- Açık arabirim uygulaması sözdizimini kullanan üye bildirimleri.
- Açık erişim değiştiriciler (varsayılan [`public`](access-modifiers.md)erişim).

Arabirimler örnek durumu içermeyebilir. Statik alanlara artık izin verilirken, örnek alanlara arabirimlerde izin verilmez. [Örnek otomatik özellikler,](../../programming-guide/classes-and-structs/auto-implemented-properties.md) gizli bir alanı dolaylı olarak beyan ettikleri için arabirimlerde desteklenmez. Bu kuralın özellik bildirimleri üzerinde ince bir etkisi vardır. Arabirim bildiriminde, aşağıdaki kod otomatik olarak uygulanan bir özelliği bir `class` `struct`veya . Bunun yerine, varsayılan bir uygulaması olmayan ancak arabirimi uygulayan herhangi bir türde uygulanması gereken bir özellik bildirir:

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir. Bir arabirim, temel arabirimde uygulanan [bir yöntemi geçersiz kılarsa,](override.md) [açık arabirim uygulama](../../programming-guide/interfaces/explicit-interface-implementation.md) sözdizimini kullanmalıdır.

Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.

Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir. Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir. Buna ek olarak, varsayılan arabirim üyelerine yalnızca arabirimin bir örneği üzerinden erişilebilir.

Açık arabirim uygulaması hakkında daha fazla bilgi için [bkz.](../../programming-guide/interfaces/explicit-interface-implementation.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, ara birim uygulamasını gösterir. Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir. `IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Arabirimler](~/_csharplang/spec/interfaces.md) bölümüne ve Varsayılan arabirim üyeleri için özellik belirtimine bakın [- C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Referans Türleri](reference-types.md)
- [Arabirimler](../../programming-guide/interfaces/index.md)
- [Özellikleri Kullanma](../../programming-guide/classes-and-structs/using-properties.md)
- [Dizin Oluşturucular Kullanma](../../programming-guide/indexers/using-indexers.md)
- [Arabirimler](../../programming-guide/interfaces/index.md)
