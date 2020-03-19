---
title: Yapılar
description: Küçük miktarda veri ve basit davranış içeren türler için bir sınıftan genellikle daha verimli olan kompakt bir nesne türü olan F# yapısı hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400283"
---
# <a name="structures"></a>Yapılar

*Yapı,* az miktarda veri ve basit davranış alabilen türler için bir sınıftan daha verimli olabilecek kompakt bir nesne türüdür.

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

Yapılar *değer türleridir,* bu da doğrudan yığında veya üst türde satır veya dizi öğesi olarak kullanıldıklarında depolandıkları anlamına gelir. Sınıfların ve kayıtların aksine, yapıların pass-by-value semantik vardır. Bu, bunların öncelikle erişilen ve sık sık kopyalanan küçük veri toplamları için yararlı olduğu anlamına gelir.

Önceki sözdiziminde iki form gösterilir. Birincisi hafif sözdizimi değildir, ancak yine de sık sık kullanılır, `struct` çünkü `end` anahtar kelimeleri ve anahtar `StructAttribute` kelimeleri kullandığınızda, ikinci formda görünen özniteliği atlayabilirsiniz. Sadece `StructAttribute` `Struct`kısaltma kullanabilirsiniz .

Önceki sözdiziminde *tür tanım-tanım-elemanlar ve üyeler* üye bildirimlerini ve tanımlarını temsil eder. Yapıların oluşturucuları, mutable ve değişmez alanları olabilir ve üyeleri ve arayüz uygulamalarını bildirebilirler. Daha fazla bilgi için [Üyeler'e](./members/index.md)bakın.

Yapılar kalıtıma katılamaz, `let` `do` ciltleme veya içeremez ve kendi türünden alanları özyinelemeli olarak içeremez (ancak kendi türüne başvuran referans hücreleri içerebilirler).

Yapılar bağlamaya `let` izin vermeygerektiğinden, `val` anahtar sözcüğü kullanarak yapılardaki alanları bildirmeniz gerekir. `val` Anahtar kelime bir alanı ve türünü tanımlar, ancak başlatmaya izin vermez. Bunun `val` yerine, bildirimler sıfır veya null olarak başharfe alınır. Bu nedenle, örtük bir oluşturucuya sahip yapılar (yani bildirimdeki yapı adından hemen `val` sonra verilen parametreler) bildirimlerin öznitelik ile `DefaultValue` açıklamalı olmasını gerektirir. Tanımlı bir oluşturucuya sahip yapılar hala sıfır başlatmayı destekler. Bu nedenle, `DefaultValue` öznitelik böyle bir sıfır değeri alan için geçerli olduğunu bir bildirimdir. Yapıların örtük oluşturucuları herhangi bir `let` `do` eylem gerçekleştirmez, çünkü türde bağlamalara izin verilmez, ancak geçirilen örtük yapıcı parametre değerleri özel alanlar olarak kullanılabilir.

Açık oluşturucular alan değerlerinin başlatılmasını içerebilir. Açık bir oluşturucuya sahip bir yapınız varsa, yine de sıfır başlatmayı destekler; ancak, açık oluşturucuile çakıştığı için `DefaultValue` `val` bildirimlerdeki özniteliği kullanmayın. Bildirimler hakkında `val` daha fazla bilgi için Bkz. [Açık Alanlar: `val` Anahtar Kelime](./members/explicit-fields-the-val-keyword.md).

Özniteliklere ve erişilebilirlik değiştiricilerine yapılarda izin verilir ve diğer türler için aynı kurallara uyar. Daha fazla bilgi için [Bkz. Öznitelikler](attributes.md) ve [Erişim Denetimi.](access-control.md)

Aşağıdaki kod örnekleri yapı tanımlarını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>ByRefLike structs

Semantik gibi kendi yapılarınızı tanımlayabilirsiniz: `byref`daha fazla bilgi için [Byrefs'a](byrefs.md) bakın. Bu öznitelik <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> ile yapılır:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`anlamına `Struct`gelmez. Her ikisi de türünde mevcut olmalıdır.

F#'daki "-like"`byref`struct, yığına bağlı bir değer türüdür. Yönetilen yığına hiçbir zaman ayrılmaz. Bir `byref`-benzeri yapı, yaşam boyu ve yakalamama ile ilgili güçlü denetimler kümesiyle uygulandığından, yüksek performanslı programlama için yararlıdır. Kurallar şunlardır:

- İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem döndürürler olarak kullanılabilirler.
- Bunlar statik veya bir sınıfın veya normal yapının örnek üyeleri olamaz.
- Herhangi bir kapatma yapısı (yöntemler`async` veya lambda ifadeleri) tarafından ele geçirilemezler.
- Genel bir parametre olarak kullanılamazlar.

Bu kurallar kullanımı çok güçlü bir şekilde kısıtlasa da, bunu yüksek performanslı bilgi işlem sözünü güvenli bir şekilde yerine getirmek için yapar.

## <a name="readonly-structs"></a>ReadOnly structs

Yapılarını öznitelikile <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> ekleyebilirsiniz. Örnek:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly`anlamına `Struct`gelmez. Bir `IsReadOnly` yapı ya da yapı için ikisini de eklemeniz gerekir.

Bu özniteliğin kullanımı, meta verileri, F# ve C#'ın sırasıyla `inref<'T>` ve `in ref`sırasıyla

Okunan bir yapının içinde değişken bir değer tanımlamak bir hata üretir.

## <a name="struct-records-and-discriminated-unions"></a>Yapı Kayıtları ve Ayrımcı Birlikler

[Kayıtlar](records.md) ve [Ayrımcı Birleþmeler'](discriminated-unions.md) i `[<Struct>]` öznitelikile yapý cuzk olarak temsil edebilirsiniz.  Daha fazla bilgi edinmek için her makaleye bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dil Referansı](index.md)
- [Sınıflar](classes.md)
- [Kayıtlar](records.md)
- [Üyeler](./members/index.md)
