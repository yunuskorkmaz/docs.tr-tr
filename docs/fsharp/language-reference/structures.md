---
title: "Yapılar (F#)"
description: "F # yapısı hakkında genellikle bir compact nesne türü öğrenin küçük miktarda veri ve basit davranışı türleriyle için bir sınıf daha verimlidir."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 50819506-3210-418f-9602-0ee1c9a52177
ms.openlocfilehash: 542b69a5aacb8fcfb0e8f6d6c943fe1954c4c59c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="structures"></a>Yapılar

A *yapısı* küçük miktarda veri ve basit davranışı türleri için bir sınıf daha etkili olabilir compact nesne türüdür.

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a>Açıklamalar
Yapıları olan *değer türleri*, doğrudan yığında veya olarak kullanıldığında depolanan anlamına alanları veya dizi öğeleri, satır içi üst yazın. Sınıfları ve kayıtları aksine, yapıları geçişi değerli semantiklerine sahip. Bu, öncelikle erişilen ve sık kopyalanan verilerin küçük Toplamalar için yararlı oldukları anlamına gelir.

Önceki sözdiziminde iki form gösterilmektedir. İlk basit sözdizimi değil, ancak yine de sık kullandığınızda, çünkü kullanılır `struct` ve `end` anahtar sözcüklerini atlayın `StructAttribute` ikinci biçiminde görünür öznitelik. Kısaltma `StructAttribute` henüz için `Struct`.

*Tür tanımı öğeleri* önceki sözdiziminde üye bildirimler ve tanımlar temsil eder. Yapıları oluşturucular ve kesilebilir ve değişmez alanları olabilir ve bunlar üyeleri ve arabirim uygulamaları bildirebilirsiniz. Daha fazla bilgi için bkz: [üyeleri](members/index.md).

Yapıları devralma katılamaz, içeremez `let` veya `do` bağlamalar ve yinelemeli olarak (kendi türü başvuru başvuru hücreleri içerebilse) kendi türünde alanlar içeremez.

Yapıları izin verme çünkü `let` bağlamaları kullanarak yapıları alanlarında bildirmelidir `val` anahtar sözcüğü. `val` Anahtar sözcüğü bir alan ve türünü tanımlar ancak başlatma izin vermiyor. Bunun yerine, `val` bildirimleri sıfır başlatılmış veya null. Bu nedenle, gerektiren bir örtük Oluşturucu (diğer bir deyişle, hemen sonra bildiriminde yapısı adı verilen parametreleri) sahip yapıları, `val` bildirimleri açıklama ile `DefaultValue` özniteliği. Tanımlanan bir oluşturucuya sahip yapıları hala sıfır başlatma destekler. Bu nedenle, `DefaultValue` böyle sıfır değerini alan için geçerli bir bildirimi bir özniteliktir. Örtük oluşturucuları yapıları için kullanılmayacak herhangi bir eylem olduğundan `let` ve `do` bağlamaları türüne izin verilmiyor, ancak geçirilen örtük Oluşturucu parametre değerlerini özel alanlar olarak kullanılabilir.

Açıkça oluşturucular alan değerlerinin başlatma gerektirebilir. Açık bir oluşturucuya sahip bir yapıya sahip olduğunda hala sıfır başlatma destekler; Ancak, kullanmaz `DefaultValue` özniteliği `val` bildirimleri açık Oluşturucu ile çakıştığı için. Hakkında daha fazla bilgi için `val` bildirimleri, bkz: [açık alanlar: `val` anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).

Öznitelikler ve erişilebilirlik değiştiricileri yapıları izin verilir ve bu diğer türleri olarak aynı kuralları izleyin. Daha fazla bilgi için bkz: [öznitelikleri](attributes.md) ve [erişim denetimi](access-control.md).

Aşağıdaki kod örnekleri yapısı tanımları gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a>Yapı kaydeder ve ayrılmış birleşimler

F # 4.1 ile başlayarak, size gösterebilir [kayıtları](records.md) ve [ayrılmış birleşimler](discriminated-unions.md) ile yapılar olarak `[<Struct>]` özniteliği.  Daha fazla bilgi için her makalesine bakın.
    
## <a name="see-also"></a>Ayrıca Bkz.
[F # dili başvurusu](index.md)

[Sınıfları](classes.md)

[Kayıtları](records.md)

[Üyeleri](members/index.md)
