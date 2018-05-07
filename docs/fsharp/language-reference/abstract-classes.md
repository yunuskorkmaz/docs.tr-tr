---
title: Soyut Sınıflar (F#)
description: 'Gerçeklenmemiş bazı veya tüm üyeleri bırakın F # soyut sınıfları hakkında bilgi edinin ve nesne türlerini farklı bir dizi ortak işlevselliğini temsil eder.'
ms.date: 05/16/2016
ms.openlocfilehash: c472e9d164ae78bde716bb5102e54f4e698b61b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="abstract-classes"></a>Soyut sınıflar

*Soyut sınıflar* gerçeklenmemiş, bazı veya tüm üyeleri bırakın ve böylece uygulamaları türetilmiş sınıfları tarafından sağlanabilir sınıflarıdır.

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
Nesne odaklı programlama, bir Özet sınıf bir hiyerarşinin temel sınıf olarak kullanılan ve farklı nesne türleri birtakım ortak işlevselliğini temsil eder. "Özet" adı da anlaşılacağı gibi soyut sınıflar doğrudan somut varlıklar sorun etki alanında oturum genellikle benzemez. Ancak, bunlar ne birçok farklı somut varlıklar ortaktır temsil eder.

Soyut sınıflar olmalıdır `AbstractClass` özniteliği. Bunlar sahip uygulanan ve üyeleri gerçeklenmemiş. Terimi kullanımını *soyut* uygulandığında bir sınıfı diğer .NET dilleri; olduğu gibi aynıdır ancak terimi kullanımını *soyut* yöntemleri (ve özellikleri) uygulandığında biraz farklı bir F #'olan kendi Diğer .NET dilleri kullanın. F bir yöntem ile işaretlendiğinde, #, `abstract` anahtar sözcüğü, bu gösteren bir üye olarak bilinen bir giriş olduğunu bir *sanal dağıtım yuvası*, bu tür için sanal işlevleri iç tablosuna. Diğer bir deyişle, sanal yöntemdir rağmen `virtual` anahtar sözcüğü F # dilinde kullanılmaz. Anahtar sözcüğü `abstract` olup yöntemin bağımsız olarak sanal yöntemler kullanılır. Bir sanal dağıtım yuvası bildirimi, o dağıtım yuvası için bir yöntem tanımını ayrıdır. Bu nedenle, F # sanal yöntem bildirimi ve tanımı başka bir .NET dilinde bir Özet yöntem bildirimi ve ile ya da ayrı bir tanımı bileşimini eşdeğerdir `default` anahtar sözcüğü veya `override` anahtar sözcüğü. Daha fazla bilgi ve örnekler için bkz: [yöntemleri](members/methods.md).

Bir sınıf bildirildi, ancak tanımlı soyut yöntemler varsa soyut olarak kabul edilir. Bu nedenle, soyut yöntemler olan sınıfları mutlaka soyut sınıflar değildir. Bir sınıf soyut yöntemler tanımsız sürece kullanmayın **AbstractClass** özniteliği.

Önceki sözdiziminde *erişim değiştiricisi* olabilir `public`, `private` veya `internal`. Daha fazla bilgi için bkz: [erişim denetimi](access-control.md).

Soyut sınıflar diğer türleriyle gibi bir taban sınıf ve bir veya daha fazla arabirimleri temel sahip olabilir. Her bir temel sınıf veya arabirim ile birlikte ayrı bir satırda görünen `inherit` anahtar sözcüğü.

Soyut bir sınıf türü tanımını tam olarak tanımlanan üyeler içerebilir, ancak soyut üyelerini içerebilir. Soyut üyelerini sözdizimi önceki sözdiziminde ayrı olarak gösterilir. Bu sözdiziminde *tür imzası* üyesi içeren bir liste sırası ve dönüş türleri parametre türleri ile ayrılır `->` belirteçleri ve/veya `*` belirteçler uygun şekilde curried için ve tupled parametreleri. Soyut üye türü imzaları sözdizimi imza dosyalarında kullanılan ve IntelliSense Visual Studio Kod Düzenleyicisi'nde gösterilen aynı değil.

Aşağıdaki kod bir Özet sınıf iki Özet olmayan türetilen sınıflar, kare ve daire sahip şekli gösterir. Örnek soyut sınıfları, yöntemleri ve özellikleri kullanmayı gösterir. Örnekte, soyut sınıf şekli somut varlıklar daire ve kare ortak öğelerini temsil eder. Tüm şekillerde (iki boyutlu bir koordinat sistemi) ortak özelliklerini out şekli sınıfına soyutlanır: kılavuz, döndürme açısı ve alan ve çevre özellikleri konum. Bunlar, hangi tek tek şekilleri değiştiremezsiniz davranışı konumu dışında geçersiz kılınabilir.

Döndürme yöntemi, dönüş değişmez nedeniyle kendi simetrisi olan daire sınıfı olduğu gibi geçersiz kılınabilir. Bu nedenle daire sınıfında hiçbir şey yapmaz bir yöntemle döndürme yöntemi değiştirilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Çıktı:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Ayrıca Bkz.
[Sınıflar](classes.md)

[Üyeler](members/index.md)

[Yöntemler](members/methods.md)

[Özellikler](members/Properties.md)
