---
title: Tür Genişletmeleri
description: Tür uzantılarının F# daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize nasıl izin vereceğinizi öğrenin.
ms.date: 02/05/2020
ms.openlocfilehash: 9ab3a007783f67fd8d80cff840ac3085fdcd60f7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092687"
---
# <a name="type-extensions"></a>Tür uzantıları

Tür uzantıları ( _genişletmeler_de denir), daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize olanak sağlayan bir özellik ailesidir. Üç özellik şunlardır:

- İç tür uzantıları
- İsteğe bağlı tür uzantıları
- Uzantı yöntemleri

Her biri farklı senaryolarda kullanılabilir ve farklı avantajları vardır.

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

- `Variant` türünün bildirimi
- `Variant` sınıfını "şekle" göre yazdırma işlevselliği
- Nesne stili `.`gösterimi ile yazdırma işlevlerine erişmenin bir yolu

Bu, her şeyi `Variant`üye olarak tanımlamaya alternatiftir. Doğal olarak daha iyi bir yaklaşım olmasa da, bazı durumlarda işlevlerin temizleyici bir gösterimi olabilir.

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

Artık `RepeatElements`, `Extensions` modülü üzerinde çalıştığınız kapsamda açıldığı sürece <xref:System.Collections.Generic.IEnumerable%601> bir üyesi olarak erişebilirsiniz.

İsteğe bağlı uzantılar, yansıma tarafından incelenmişse genişletilmiş tür üzerinde görünmez. İsteğe bağlı uzantılar modüllerde olmalıdır ve yalnızca uzantıyı içeren modül açık olduğunda ya da kapsamda yoksa kapsam içinde yer alır.

İsteğe bağlı uzantı üyeleri, nesne örneğinin örtük olarak ilk parametre olarak geçirildiği statik üyelere derlenir. Ancak bunlar, nasıl bildirilenler doğrultusunda örnek üye veya statik üyeler gibi davranır.

İsteğe bağlı uzantı üyeleri, tüketicilerle de C# görünmez veya Visual Basic. Yalnızca başka F# bir kodda tüketilebilir.

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

- Olduğu gibi `Sum` üyesinin, tür uzantısının tanımladığı `'T` (`static member get_Zero` ve `static member (+)`) farklı bir kısıtlaması vardır.
- Tür uzantısının aynı kısıtlamaya sahip olacak şekilde değiştirilmesi, `Sum` artık `IEnumerable<'T>`tanımlı kısıtlama ile eşleşmez.
- `member this.Sum` `member inline this.Sum` olarak değiştirmek, tür kısıtlamalarının eşleşmeyen bir hata verir.

İstenen, "boşluk olarak float" ve bir tür genişledikleri gibi sunulabilir statik yöntemlerdir. Bu, uzantı yöntemlerinin gerekli hale geldiği yerdir.

## <a name="extension-methods"></a>Uzantı yöntemleri

Son olarak, uzantı yöntemleri (bazen "C# stil uzantısı üyeleri" olarak da adlandırılır) bir F# sınıf üzerinde statik üye yöntemi olarak ' de belirtilebilir.

Uzantı yöntemleri, tür değişkenini kısıtlayan genel bir tür üzerinde uzantı tanımlamak istediğinizde yararlıdır. Örneğin:

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Kullanıldığında, bu kod, `Extensions` açıldığı veya kapsam içinde olduğu sürece, `Sum` <xref:System.Collections.Generic.IEnumerable%601>tanımlanmış gibi görünmesini sağlayacak.

Uzantının VB.NET kodu tarafından kullanılabilmesi için, derleme düzeyinde ek bir `ExtensionAttribute` gereklidir:

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
- [Söz diziminde](type-extensions.md#syntax) `self-identifier` belirteci, normal Üyeler gibi, çağrılan türün örneğini temsil eder.
- Genişletilmiş Üyeler statik veya örnek üyeleri olabilir.
- Tür uzantısı üzerindeki tür değişkenleri, belirtilen tür kısıtlamasıyla eşleşmelidir.

Tür uzantıları için aşağıdaki sınırlamalar de mevcuttur:

- Tür uzantıları sanal veya soyut yöntemleri desteklemez.
- Tür uzantıları, geçersiz kılma yöntemlerini genişletmeler olarak desteklemez.
- Tür uzantıları [statik olarak çözümlenen tür parametrelerini](./generics/statically-resolved-type-parameters.md)desteklemez.
- İsteğe bağlı tür uzantıları, oluşturucuları genişletmeler olarak desteklemez.
- Tür genişletmeleri [tür kısaltmaları](type-abbreviations.md)üzerinde tanımlanamaz.
- Tür uzantıları `byref<'T>` için geçerli değil (bildirilebilecek olmasına rağmen).
- Tür uzantıları, öznitelikler için geçerli değildir (ancak bildirilenler olabilir).
- Aynı ada sahip diğer yöntemleri aşırı yükleyen uzantılar tanımlayabilirsiniz, ancak belirsiz bir çağrı varsa F# derleyici uzantı olmayan yöntemlere tercih verir.

Son olarak, bir tür için birden çok iç tür uzantısı varsa, tüm üyelerin benzersiz olması gerekir. İsteğe bağlı tür uzantıları için, aynı türe sahip farklı tür uzantılarındaki Üyeler aynı ada sahip olabilir. Belirsizlik hataları yalnızca istemci kodu aynı üye adlarını tanımlayan iki farklı kapsam açarsa oluşur.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Üyeler](./members/index.md)
