---
title: Soyut sınıflar
description: Bazı veya F# tüm üyeleri uygulanmayan ve çeşitli nesne türleri kümesinin yaygın işlevlerini temsil eden soyut sınıflar hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: a6bbfc23b858d5f3833f3f52b6dca46753080f03
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629673"
---
# <a name="abstract-classes"></a>Soyut sınıflar

*Soyut sınıflar* , bazı veya tüm üyelerini uygulanmayan sınıflardır ve bu sayede uygulamalar türetilmiş sınıflar tarafından sağlanabilmelidir.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>Açıklamalar

Nesne odaklı programlamada, soyut bir sınıf hiyerarşinin temel sınıfı olarak kullanılır ve farklı nesne türleri kümesinin yaygın işlevlerini temsil eder. "Soyut" adının gösterdiği gibi, soyut sınıflar genellikle sorun etki alanında doğrudan somut varlıklara karşılık gelmez. Ancak, yaygın olarak kaç farklı somut varlık olduğunu temsil eder.

Soyut sınıfların `AbstractClass` özniteliği olmalıdır. Uygulanamazlar ve uygulanmayan Üyeler üyelere sahip olabilirler. Bir sınıfa uygulandığında *soyut* olan terim kullanımı, diğer .net dilleridir. Ancak, yöntemlere (ve özelliklere) uygulandığında *Özet* teriminin kullanımı, diğer .NET dillerinde kullanımı için biraz farklıdır F# . ' F#De, bir yöntem `abstract` anahtar sözcüğüyle işaretlendiğinde, bu bir üyenin sanal bir *dağıtım yuvası*olarak bilinen, bu tür için iç sanal işlevlerin iç tablosunda bir girişi olduğunu gösterir. Diğer bir deyişle, `virtual` anahtar sözcüğü F# dilde kullanılmasa da, yöntemi sanal olur. Anahtar sözcüğü `abstract` , yöntemin uygulanıp uygulanmadığına bakılmaksızın sanal yöntemlerde kullanılır. Bir sanal dağıtım yuvasının bildirimi, bu dağıtım yuvası için bir yöntemin tanımından ayrıdır. Bu nedenle, F# bir sanal yöntem bildiriminin ve tanımının başka bir .net dilinde eşdeğeri, `default` anahtar sözcüğü ya `override` da anahtar sözcüğüyle birlikte bir soyut Yöntem bildiriminin ve ayrı bir tanımın birleşimidir. Daha fazla bilgi ve örnek için bkz. [Yöntemler](./members/methods.md).

Bir sınıf, yalnızca tanımlanmış ancak tanımlanmamış soyut yöntemler varsa Özet olarak değerlendirilir. Bu nedenle, soyut yöntemleri olan sınıfların soyut sınıflar olması gerekmez. Bir sınıfın tanımsız soyut yöntemleri yoksa, abstract **Ctclass** özniteliğini kullanmayın.

Önceki sözdiziminde, *Erişilebilirlik-değiştirici* `public` `private` veya `internal`olabilir. Daha fazla bilgi için bkz. [Access Control](access-control.md).

Diğer türlerde olduğu gibi, soyut sınıfların bir temel sınıfı ve bir veya daha fazla temel arabirimi olabilir. Her temel sınıf veya arabirim, `inherit` anahtar sözcüğüyle birlikte ayrı bir satırda görüntülenir.

Soyut bir sınıfın tür tanımı, tam olarak tanımlanmış Üyeler içerebilir, ancak soyut Üyeler de içerebilir. Soyut üyelerin sözdizimi, Önceki sözdiziminde ayrı olarak gösterilir. Bu sözdiziminde, bir üyenin *tür imzası* , belirteç ve/veya `->` `*` belirteçlere göre ayrılmış parametrelere uygun şekilde, sırasıyla parametre türlerini ve dönüş türlerini içeren bir listesidir. Soyut üye türü imzaları için sözdizimi, imza dosyalarında kullanılan ve Visual Studio Code düzenleyicisinde IntelliSense tarafından gösterilen ile aynıdır.

Aşağıdaki kod, soyut olmayan iki türetilmiş sınıfa, kareyle ve daireye sahip olan bir soyut sınıf şeklini gösterir. Örnek, soyut sınıfların, yöntemlerin ve özelliklerin nasıl kullanılacağını gösterir. Örnekte, soyut sınıf şekli, somut varlıkların dairenin ve karenin ortak öğelerini temsil eder. Tüm şekillerin ortak özellikleri (iki boyutlu bir koordinat sisteminde) şekil sınıfına soyutlanır: kılavuzdaki konum, bir döndürme açısı ve alan ve çevre özellikleri. Bunlar, konum dışında, tek şekillerin değiştireamaması için geçersiz kılınabilir.

Döndürme yöntemi, kendi simetri nedeniyle dönüş sabiti olan Circle sınıfında olduğu gibi geçersiz kılınabilir. Bu nedenle, Circle sınıfında, döndürme yöntemi hiçbir şey olmayan bir yöntemle değiştirilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Çıkış:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar](classes.md)
- [Üyeler](./members/index.md)
- [Yöntemler](./members/methods.md)
- [Özellikler](./members/Properties.md)
