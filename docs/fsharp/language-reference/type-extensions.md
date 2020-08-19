---
title: Tür Genişletmeleri
description: 'F # tür uzantılarının daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize nasıl izin sağladığını öğrenin.'
ms.date: 02/05/2020
ms.openlocfilehash: 8fdb2d5e527643b23d24a6118e8cef6b11f1a546
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559134"
---
# <a name="type-extensions"></a>Tür uzantıları

Tür uzantıları ( _genişletmeler_de denir), daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize olanak sağlayan bir özellik ailesidir. Üç özellik şunlardır:

- İç tür uzantıları
- İsteğe bağlı tür uzantıları
- Genişletme yöntemleri

Her biri farklı senaryolarda kullanılabilir ve farklı avantajları vardır.

## <a name="syntax"></a>Syntax

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
    [<Extension>]
    static member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a>İç tür uzantıları

İç tür uzantısı, Kullanıcı tanımlı bir türü genişleten bir tür uzantısıdır.

İç tür uzantılarının, genişledikleri türle aynı dosyada **ve** aynı ad alanında veya modülde tanımlanması gerekir. Diğer herhangi bir tanım, [isteğe bağlı tür uzantılarına](type-extensions.md#optional-type-extensions)neden olur.

İç tür uzantıları bazen tür bildiriminden işlevselliği birbirinden ayıran temizleyici bir yoldur. Aşağıdaki örnek, bir iç tür uzantısının nasıl tanımlanacağını göstermektedir:

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

Bir tür uzantısı kullanmak, aşağıdakilerin her birini ayırmanızı sağlar:

- Bir `Variant` türün bildirimi
- `Variant`Sınıfı "şekle" göre yazdırma işlevselliği
- Nesne stili gösterimle yazdırma işlevlerine erişmenin bir yolu `.`

Bu, her şeyi üzerinde üye olarak tanımlamaya alternatiftir `Variant` . Doğal olarak daha iyi bir yaklaşım olmasa da, bazı durumlarda işlevlerin temizleyici bir gösterimi olabilir.

İç tür uzantıları, genişlettikleri türün üyeleri olarak derlenir ve tür yansıma tarafından incelenirse tür üzerinde görünür.

## <a name="optional-type-extensions"></a>İsteğe bağlı tür uzantıları

İsteğe bağlı bir tür uzantısı, genişletilmekte olan türün özgün modülünün, ad alanının veya derlemenin dışında görünen bir uzantıdır.

İsteğe bağlı tür uzantıları, kendi tanımladığınız bir türü genişletmek için faydalıdır. Örneğin:

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

Artık, `RepeatElements` <xref:System.Collections.Generic.IEnumerable%601> `Extensions` modül üzerinde çalıştığınız kapsamda açıldığı sürece bir üyesi olan olarak erişebilirsiniz.

İsteğe bağlı uzantılar, yansıma tarafından incelenmişse genişletilmiş tür üzerinde görünmez. İsteğe bağlı uzantılar modüllerde olmalıdır ve yalnızca uzantıyı içeren modül açık olduğunda ya da kapsamda yoksa kapsam içinde yer alır.

İsteğe bağlı uzantı üyeleri, nesne örneğinin örtük olarak ilk parametre olarak geçirildiği statik üyelere derlenir. Ancak bunlar, nasıl bildirilenler doğrultusunda örnek üye veya statik üyeler gibi davranır.

İsteğe bağlı uzantı üyeleri, C# veya Visual Basic tüketicilerine de görünmez. Bunlar yalnızca diğer F # kodunda tüketilebilir.

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>İç ve isteğe bağlı tür uzantılarının genel sınırlaması

Tür değişkeninin kısıtlı olduğu genel bir türde bir tür uzantısı bildirmek mümkündür. Gereksinim, uzantı bildiriminin kısıtlaması, belirtilen tür kısıtlamasıyla eşleşir.

Ancak, tanımlı bir tür ve tür uzantısı arasında kısıtlamalar eşleştirildiği halde, bir kısıtlama, tür parametresinde, belirtilen türden farklı bir gereksinim getiren bir genişletilmiş üyenin gövdesi tarafından çıkarsanamıyor. Örneğin:

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

Bu kodu isteğe bağlı bir tür uzantısıyla çalışacak şekilde almanın bir yolu yoktur:

- Olduğu gibi, `Sum` üyenin `'T` `static member get_Zero` tür uzantısının tanımladığı sayıdan farklı bir kısıtlaması (ve `static member (+)` ) vardır.
- Tür uzantısının aynı kısıtlamaya sahip olacak şekilde değiştirilmesi, `Sum` ' deki tanımlı kısıtlamayla artık eşleşmeyecektir `IEnumerable<'T>` .
- `member this.Sum`Olarak değiştirmek `member inline this.Sum` , tür kısıtlamalarının eşleşmeyen bir hata verir.

İstenen, "boşluk olarak float" ve bir tür genişledikleri gibi sunulabilir statik yöntemlerdir. Bu, uzantı yöntemlerinin gerekli hale geldiği yerdir.

## <a name="extension-methods"></a>Genişletme yöntemleri

Son olarak, uzantı yöntemleri (bazen "C# stil uzantısı üyeleri" olarak adlandırılır), F # içinde bir sınıf üzerinde statik üye yöntemi olarak bildirilemez.

Uzantı yöntemleri, tür değişkenini kısıtlayan genel bir tür üzerinde uzantı tanımlamak istediğinizde yararlıdır. Örneğin:

```fsharp
namespace Extensions

open System.Collections.Generic
open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Kullanıldığında, bu kod ' de tanımlandığı gibi görünür, bu `Sum` <xref:System.Collections.Generic.IEnumerable%601> yüzden `Extensions` Açık veya kapsam içinde yer alır.

Uzantının VB.NET kodu tarafından kullanılabilmesi için, `ExtensionAttribute` derleme düzeyinde bir ek gereklidir:

```fsharp
module AssemblyInfo
open System.Runtime.CompilerServices
[<assembly:Extension>]
do ()
```

## <a name="other-remarks"></a>Diğer açıklamalar

Tür uzantıları da aşağıdaki özniteliklere sahiptir:

- Erişilebilen herhangi bir tür genişletilebilir.
- İç ve isteğe bağlı tür uzantıları, yalnızca yöntemleri değil _herhangi bir_ üye türünü tanımlayabilir. Bu nedenle, örneğin uzantı özellikleri de mümkündür.
- `self-identifier` [Söz diziminde](type-extensions.md#syntax) belirteç, normal üyelerde olduğu gibi, çağrılan türün örneğini temsil eder.
- Genişletilmiş Üyeler statik veya örnek üyeleri olabilir.
- Tür uzantısı üzerindeki tür değişkenleri, belirtilen tür kısıtlamasıyla eşleşmelidir.

Tür uzantıları için aşağıdaki sınırlamalar de mevcuttur:

- Tür uzantıları sanal veya soyut yöntemleri desteklemez.
- Tür uzantıları, geçersiz kılma yöntemlerini genişletmeler olarak desteklemez.
- Tür uzantıları [statik olarak çözümlenen tür parametrelerini](./generics/statically-resolved-type-parameters.md)desteklemez.
- İsteğe bağlı tür uzantıları, oluşturucuları genişletmeler olarak desteklemez.
- Tür genişletmeleri [tür kısaltmaları](type-abbreviations.md)üzerinde tanımlanamaz.
- Tür uzantıları için geçerli değildir `byref<'T>` (ancak bildirilenler olabilir).
- Tür uzantıları, öznitelikler için geçerli değildir (ancak bildirilenler olabilir).
- Aynı ada sahip diğer yöntemleri aşırı yükleyen uzantılar tanımlayabilirsiniz, ancak belirsiz bir çağrı varsa F # derleyicisi uzantı olmayan yöntemlere tercih verir.

Son olarak, bir tür için birden çok iç tür uzantısı varsa, tüm üyelerin benzersiz olması gerekir. İsteğe bağlı tür uzantıları için, aynı türe sahip farklı tür uzantılarındaki Üyeler aynı ada sahip olabilir. Belirsizlik hataları yalnızca istemci kodu aynı üye adlarını tanımlayan iki farklı kapsam açarsa oluşur.

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [Üyeler](./members/index.md)
