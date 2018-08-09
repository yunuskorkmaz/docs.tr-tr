---
title: Tür Uzantıları (F#)
description: 'Bir önceden tanımlanmış nesne türü için yeni üyeler eklemek, F # tür uzantıları nasıl izin öğrenin.'
ms.date: 07/20/2018
ms.openlocfilehash: 2181745ea75894fbfe35d5522c130baaf1876455
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "33566892"
---
# <a name="type-extensions"></a>Tür uzantıları

Tür Uzantıları (olarak da adlandırılan _genişletmelerinde_) olan bir aile özelliklerinin bir önceden tanımlanmış nesne türü için yeni üye eklemenizi sağlar. Üç özellikleri şunlardır:

* İç tür uzantıları
* İsteğe bağlı türü uzantıları
* Genişletme yöntemleri

Her farklı senaryolarda kullanılabilir ve farklı Artıları ve eksileri vardır.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a>İç tür uzantıları

Gerçek tür uzantısı kullanıcı tarafından tanımlanan bir türü genişleten bir türü uzantısıdır.

Aynı dosyada iç tür uzantıları tanımlanan **ve** aynı ad alanı veya modül olarak genişletme türü. Diğer bir tanımı bunları neden olacak olan [isteğe bağlı türü uzantıları](type-extensions.md#optional-type-extensions).

İç tür uzantıları bazen işlevi türü bildirimden ayırmak için bir temizleme yoludur. Aşağıdaki örnek, gerçek tür uzantısı tanımlamak gösterilmektedir:

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

Bir tür uzantısı kullanarak aşağıdakilerin her biri ayrı sağlar:

* Bildirimi bir `Variant` türü
* Yazdırma işlevselliği `Variant` "şeklini" bağlı olarak sınıfı
* Nesne stiliyle yazdırma işlevselliği erişmek için bir yol `.`-gösterimi

Bu üye olarak her şey üzerinde tanımlama alternatiftir `Variant`. Doğal olarak daha iyi bir yaklaşım olmasa da, bu işlevsellik bazı durumlarda daha net bir temsilini olabilir.

İç tür uzantıları büyütmek ve tür yansıma tarafından incelendiğinde tür üzerinde görünür bir türün üyeleri olarak derlenir.

## <a name="optional-type-extensions"></a>İsteğe bağlı türü uzantıları

İsteğe bağlı tür uzantısı özgün modülü, ad alanı veya Genişletilmekte olan türün derlemenin dışında görünür bir uzantısıdır.

İsteğe bağlı türü uzantıları kendiniz tanımlamadığınız bir türü genişletmek için kullanışlıdır. Örneğin:

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

Artık erişebilirsiniz `RepeatElements` üyesi ise gibi <xref:System.Collections.Generic.IEnumerable%601> sürece `Extensions` modülü içinde çalışmakta olduğunuz kapsam içinde açılır.

Genişletilmiş tür yansıma tarafından incelendiğinde, isteğe bağlı uzantılar görünmez. İsteğe bağlı uzantılar, modüller halinde olmalıdır ve uzantıyı içeren modül açık veya aksi halde kapsam içinde olduğunda yalnızca kapsamda oldukları.

İsteğe bağlı uzantı üyeleri, nesne örneğinin örtülü olarak ilk parametre olarak geçirildiği statik üyeler için derlenmiştir. Örnek üyeleri veya göre nasıl bildirilen statik üye oldukları gibi ancak bunlar işlevi görür.

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>Genel SORUMLULUĞUN iç ve isteğe bağlı türü uzantıları

Burada tür değişkeni kısıtlı genel türde bir tür uzantısı bildirmek mümkündür. Uzantı bildirimi kısıtlaması bildirilen türü kısıtlamasını eşleştiğini gereksinimidir.

Bildirilen tür ve tür uzantısı arasında kısıtlamaları bile eşleştirilir, ancak bildirilen türünden tür parametresi üzerinde farklı bir gereksinim uygular genişletilmiş bir üyesinin gövdesi tarafından çıkarılan için bir kısıtlama mümkündür. Örneğin:

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

Bir isteğe bağlı tür uzantısı ile çalışmak için bu kodu erişmenin bir yolu vardır:

* Olduğu gibi `Sum` üye var. farklı bir kısıtlama `'T` (`static member get_Zero` ve `static member (+)`) daha ne tür uzantısı tanımlar.
* Tür uzantısı olarak aynı kısıtlamasına sahip değiştirme `Sum` üzerinde tanımlanan kısıtlaması artık eşleşecektir `IEnumerable<'T>`.
* Üye değiştirme yapmadan `member inline Sum` tür kısıtlamaları uyumsuz bir hata verir

İstenildiği gibi bir türü genişletmek gibi sunulan ve "alanında kayan" statik yöntem bulunmaktadır. Burada uzantı yöntemleri gerekli hale budur.

## <a name="extension-methods"></a>Genişletme yöntemleri

Son olarak, genişletme yöntemleri ("C# stili uzantı üyeleri" olarak da adlandırılır) F #'ta bir statik üye yöntemi olarak sınıfta bildirilebilir.

Genişletme yöntemleri, ne zaman uzantılar tür değişkeni sınırlamak bir genel tür tanımlamak istediğiniz için kullanışlıdır. Örneğin:

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Kullanıldığında, bu kod görünmesini yapar gibi `Sum` tanımlanan <xref:System.Collections.Generic.IEnumerable%601>, sürece `Extensions` açılmış veya kapsamdadır.

## <a name="other-remarks"></a>Diğer açıklamalar

Tür uzantıları ayrıca aşağıdaki özniteliklere sahiptir:

* Erişilebilen herhangi bir türü genişletilebilir.
* İç ve isteğe bağlı türü uzantıları tanımlayabilirsiniz _herhangi_ üye türü, yalnızca yöntemi. Bu nedenle uzantı özellikleri da örneğin, mümkündür.
* `self-identifier` Belirtecini [söz dizimi](type-extensions.md#syntax) , sıradan üyelerdeki gibi çağrılmakta olan türün örneğini temsil eder.
* Genişletilmiş üyeleri, statik veya örnek üyeler.
* Bir tür uzantısı türü değişkenlerde bildirilen tür kısıtlamaları eşleşmesi gerekir.

Aşağıdaki sınırlamalar türü uzantıları için de mevcuttur:

* Tür uzantıları sanal veya soyut yöntemleri desteklemez.
* Tür uzantıları genişletmeleri geçersiz kılma yöntemleri desteklemez.
* Tür uzantıları desteklemez [statik olarak çözümlenmiş tür Parametreleri'nde](generics/statically-resolved-type-parameters.md).
* İsteğe bağlı türü uzantıları genişletmelerinde oluşturucuları desteklemez.
* Tür uzantıları tanımlanamaz [yazın kısaltmalar](type-abbreviations.md).
* Tür uzantıları için geçerli olmayan `byref<'T>` (bunlar bildirilebilir rağmen).
* Tür Uzantıları (bunlar bildirilebilir rağmen) öznitelikler için geçerli değildir.
* Aynı ada sahip diğer yöntemleri aşırı uzantıları tanımlayabilirsiniz, ancak belirsiz bir çağrı ise F # derleyici tercihi uzantısı olmayan yöntemlere verir.

Son olarak, bir tür için birden çok gerçek tür uzantısı varsa, tüm üyelerin benzersiz olması gerekir. İsteğe bağlı türü uzantıları için farklı tür Uzantılardaki aynı türe üyeleri aynı adları olabilir. Belirsizlik hataları yalnızca istemci kodu aynı üye adını tanımlayan iki farklı kapsamı açarsa oluşur.

## <a name="see-also"></a>Ayrıca bkz.

[F# Dili Başvurusu](index.md)

[Üyeler](members/index.md)
