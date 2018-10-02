---
title: Yapılar (F#)
description: 'F # yapısı hakkında genellikle bir compact nesne türü bilgi türleri küçük miktarda veri ve basit davranışı için bir sınıf daha verimlidir.'
ms.date: 05/16/2016
ms.openlocfilehash: 08af88132dda28883e246b94585ff4ed8bd2f16a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459862"
---
# <a name="structures"></a>Yapılar

A *yapısı* küçük miktarda veri ve basit davranışı sahip türleri bir sınıf daha verimli olabilir compact nesne türüdür.

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

Yapıları, *değer türleri*, alanları doğrudan yığını veya olarak kullanılması durumunda depolanan anlamına gelir veya dizi öğeleri, satır içi üst yazın. Sınıfları ve kayıtları aksine, yapıları geçişi değerli semantiklere sahip. Bu, öncelikle küçük toplamları erişilen ve sık kopyalanan verileri için yararlı oldukları anlamına gelir.

Önceki sözdiziminde, iki formları gösterilmektedir. İlk basit söz dizimi değil, ancak yine de sık kullandığınız zaman için kullanılır `struct` ve `end` anahtar çıkarabilirsiniz `StructAttribute` ikinci formda görünen özniteliği. Kısaltabilirsiniz `StructAttribute` yalnızca `Struct`.

*Tür-definition-öğeleri-ve-üyeleri* üye bildirimleri ve tanımları önceki sözdiziminde temsil eder. Yapıları oluşturucular ve alanlar değişebilir ve sabit sahip olabilir ve üyeleri ve arabirim uygulamalarına bildirebilirsiniz. Daha fazla bilgi için [üyeleri](members/index.md).

Yapıları Devralmada alamaz, içeremez `let` veya `do` bağlamaları ve yinelemeli olarak (kendi türüne başvuru hücreleri içerebilse) kendi türünde alanlar içeremez.

Yapıları izin vermez çünkü `let` bağlamaları kullanarak yapılardaki alanlar bildirmeniz gerekir `val` anahtar sözcüğü. `val` Anahtar sözcüğü bir alan ve türünü tanımlar ancak başlatma izin vermiyor. Bunun yerine, `val` bildirimlerdir sıfıra başlatılmış veya null. Bu nedenle, bir örtük Oluşturucu (diğer bir deyişle, hemen sonra bildiriminde yapısı adı verilen parametreleri) sahip yapıları gerektiren `val` bildirimleri ek açıklama ile `DefaultValue` özniteliği. Tanımlı bir oluşturucuya sahip yapıları sıfır başlatma yine de destekler. Bu nedenle, `DefaultValue` özniteliği, bu tür bir sıfır değeri alan için geçerli bir bildirim. Yapıları için örtük Oluşturucu olduğundan herhangi bir eylem gerçekleştirmeyin `let` ve `do` bağlamaları türüne izin verilmiyor, ancak geçirilen örtük Oluşturucu parametre değerlerini özel alanları olarak kullanılabilir.

Alan değerlerinin başlatma açık oluşturucuları gerektirebilir. Açık bir oluşturucu içeren bir yapıya sahip olduğunda sıfır başlatma yine de destekler. kullanmaz ancak `DefaultValue` özniteliği `val` bildirimleri içeren açık Oluşturucu çakıştığı için. Hakkında daha fazla bilgi için `val` bildirimleri için bkz: [açık alanlar: `val` anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).

Öznitelikler ve erişilebilirlik değiştiricileri yapıları izin verilir ve diğer türleri için aynı kuralları uygulayın. Daha fazla bilgi için [öznitelikleri](attributes.md) ve [erişim denetimi](access-control.md).

Aşağıdaki kod örnekleri, yapı tanımları göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>ByRefLike yapılar

Uyması için kendi yapılar tanımlayabilirsiniz `byref`-ister semantiği: bkz [Zkratka](byrefs.md) daha fazla bilgi için. Bunun <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliği:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` değil gelmez `Struct`. Her ikisi de türünde bulunmalıdır.

Bir "`byref`-gibi" yapı F # içinde bir yığın bağlı değer türüdür. Bu, hiçbir zaman yönetilen yığında ayrılır. A `byref`-gibi yaşam süresi ve yakalama olmayan hakkında güçlü denetimleri kümesiyle zorlanmış olarak yapı yüksek performanslı programlama için kullanışlıdır. Kurallar şunlardır:

* İşlev parametrelerini, yöntem parametreleri, yerel değişkenler döner kullanılabilirler.
* Statik olamaz veya bir sınıf ya da normal yapı üyelerinin örneği.
* Herhangi bir kapanış yapısı tarafından yakalanamıyor (`async` yöntemlerde veya lambda ifadelerinde).
* Genel parametre olarak kullanılamaz.

Bu kurallar çok kesin kullanımını kısıtlıyor olsa da, bunlar promise yüksek performanslı bilgi işlem güvenli bir şekilde karşılamak için bunu yapın.

## <a name="readonly-structs"></a>Salt okunur yapılar

Yapılar ile açıklama ekleyebilirsiniz <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> özniteliği. Örneğin:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly` değil gelmez `Struct`. Her ikisi de sahip olarak eklemelisiniz bir `IsReadOnly` yapısı.

Bu özniteliğin kullanımı yayan F # ile C# işleme biçimi için bilmeniz izin vererek meta verileri `inref<'T>` ve `in ref`sırasıyla.

Salt okunur yapı içinde değiştirilebilir bir değer tanımlayan bir hata oluşturur.

## <a name="struct-records-and-discriminated-unions"></a>Yapı kayıtları ve ayrılmış birleşimler

Temsil ettiğiniz [kayıtları](records.md) ve [ayırt edici birleşimler](discriminated-unions.md) yapılar ile olarak `[<Struct>]` özniteliği.  Daha fazla bilgi için her bir makaleye göz atın.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Sınıflar](classes.md)
- [Kayıtlar](records.md)
- [Üyeler](members/index.md)
