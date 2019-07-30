---
title: Yapılar
description: Küçük bir veri F# miktarı ve basit davranışları olan türler için bir sınıftan daha verimli bir kompakt nesne türü yapı hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: e638b450fe43e0993c9980cade246c3f26d25e2d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630765"
---
# <a name="structures"></a>Yapılar

*Yapı* , az miktarda veri ve basit davranışa sahip olan türler için bir sınıftan daha verimli olabilecek bir Compact nesne türüdür.

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a>Açıklamalar

Yapılar *değer türlerdir*, bu, doğrudan yığında depolandıkları veya alan veya dizi öğeleri olarak kullanıldıkları zaman, üst tür içinde satır içi olarak kullanıldıkları anlamına gelir. Sınıfların ve kayıtlardan farklı olarak, yapıların değer geçişi semantiği vardır. Bu, öncelikli olarak sık erişilen ve kopyalandığı verilerin küçük toplamalar için yararlı oldukları anlamına gelir.

Önceki sözdiziminde iki form gösterilir. İlki basit sözdizimi değildir, ancak, `struct` ve `end` anahtar sözcüklerini kullandığınızda, ikinci formda görünen `StructAttribute` özniteliği atlayabilirsiniz, ancak. `StructAttribute` Yalnızca`Struct`' i kısaltabilirsiniz.

Önceki sözdiziminde bulunan *tür tanımı-öğeler-ve-Üyeler* üye bildirimlerini ve tanımlarını temsil eder. Yapılar, oluşturucular ve değişebilir ve sabit alanlara sahip olabilir ve üyeleri ve arabirim uygulamalarını bildirebilirler. Daha fazla bilgi için bkz. [Üyeler](./members/index.md).

Yapılar devralmaya katılamaz, `let` veya `do` bağlama içeremez ve kendi türündeki alanları özyinelemeli olarak içeremez (ancak kendi türlerine başvuran başvuru hücreleri içerebilse de).

Yapılar bağlamalara izin `let` vermediğinden, `val` anahtar sözcüğünü kullanarak yapıların alanlarını bildirmeniz gerekir. Anahtar `val` sözcüğü bir alanı ve türünü tanımlar, ancak başlatmaya izin vermez. Bunun yerine `val` , bildirimler sıfır veya null olarak başlatılır. Bu nedenle, örtük Oluşturucusu olan yapılar (diğer bir deyişle, bildirimdeki yapı adından hemen sonra verilen Parametreler), `val` bildirimlerin `DefaultValue` özniteliğiyle açıklanabilmesini gerektirir. Tanımlı bir oluşturucuya sahip olan yapılar sıfır başlatmayı desteklemeye devam eder. Bu nedenle öznitelik, bu tür sıfır değeri alan için geçerli olan bir bildirimidir. `DefaultValue` Tür üzerinde `do` bağlamalara izin verilmediğinden, yapılar için örtük `let` oluşturucular hiçbir eylem gerçekleştirmez, ancak geçirilen örtük Oluşturucu parametre değerleri özel alanlar olarak kullanılabilir.

Açık oluşturucular alan değerlerinin başlatılmasını içerebilir. Açık Oluşturucusu olan bir yapınız varsa, yine de sıfır başlatmayı destekler; Ancak, açık Oluşturucu ile çakıştığından, `DefaultValue` bu özniteliği `val` bildirimlerinde kullanmayın. Bildirimler hakkında `val` daha fazla bilgi için bkz [. açık alanlar: `val` Anahtar sözcüğü](./members/explicit-fields-the-val-keyword.md).

Yapılar üzerinde özniteliklere ve erişilebilirlik değiştiricilerine izin verilir ve diğer türlerle aynı kuralları izler. Daha fazla bilgi için bkz. [öznitelikler](attributes.md) ve [Access Control](access-control.md).

Aşağıdaki kod örnekleri yapı tanımlarını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>ByRefLike yapıları

Benzer anlambilimi olan `byref`kendi yapı birimlerinizi tanımlayabilirsiniz: daha fazla bilgi için bkz. [byrefs](byrefs.md) . Bu, <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliğiyle yapılır:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`göstermez `Struct`. Her ikisi de türünde bulunmalıdır.

İçindeki F# "`byref`-LIKE" yapısı, yığın bağlantılı bir değer türüdür. Yönetilen yığında hiçbir şekilde ayrılmadı. Bir `byref`-LIKE yapısı, yoğun ömür ve yakalama olmayan bir güçlü denetim kümesiyle zorlandığından, yüksek performanslı programlama için yararlıdır. Kurallar şunlardır:

* İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem geri dönüş olarak kullanılabilirler.
* Bunlar statik veya bir sınıfın ya da normal yapının örnek üyeleri olamaz.
* Bunlar herhangi bir kapanış yapısı (`async` Yöntemler veya lambda ifadeleri) tarafından yakalanamaz.
* Genel parametre olarak kullanılamaz.

Bu kurallar kullanımı çok kuvvetli olsa da, yüksek performanslı bilgi işlem taahhüdünü güvenli bir şekilde yerine getirmelerini sağlar.

## <a name="readonly-structs"></a>ReadOnly yapılar

<xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> Özniteliği olan yapılara not ekleyebilirsiniz. Örneğin:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly`göstermez `Struct`. `IsReadOnly` Yapısına sahip olmak için her ikisini de eklemeniz gerekir.

Bu özniteliğin kullanılması, verileri sırasıyla ve F# `in ref`olarak C# `inref<'T>` değerlendirmek için meta verileri yayar.

Salt okunur bir yapının içinde kesilebilir değer tanımlamak bir hata oluşturur.

## <a name="struct-records-and-discriminated-unions"></a>Struct kayıtları ve ayırt edici birleşimler

Özniteliği`[<Struct>]` ile yapılar olarak [kayıtları](records.md) ve [ayırt edici birleşimleri](discriminated-unions.md) temsil edebilirsiniz.  Daha fazla bilgi için her makaleye bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Sınıflar](classes.md)
- [Kayıtlar](records.md)
- [Üyeler](./members/index.md)
