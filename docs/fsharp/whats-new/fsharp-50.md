---
title: 'F # 5,0-F # kılavuzundaki yenilikler'
description: "F # 5,0 ' de bulunan yeni özelliklere genel bakış alın."
ms.date: 11/06/2020
ms.openlocfilehash: 51d6dd2457ee9966a86d0d9ac686f2af15772999
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557148"
---
# <a name="whats-new-in-f-50"></a>F # 5,0 ' deki yenilikler

F # 5,0, F # diline ve F# Etkileşimli çeşitli iyileştirmeler ekler. **.NET 5** ile kullanıma sunuldu.

[.Net İndirmeleri sayfasından](https://dotnet.microsoft.com/download)en son .NET SDK 'sını indirebilirsiniz.

## <a name="get-started"></a>başlarken

F # 5,0 tüm .NET Core dağıtımları ve Visual Studio Araçları 'nda mevcuttur. Daha fazla bilgi için bkz. [F # ile çalışmaya başlama](../get-started/index.md) daha fazla bilgi.

## <a name="package-references-in-f-scripts"></a>F # betiklerine paket başvuruları

F # 5, F # betiklerinin sözdizimi ile paket başvuruları için destek sunar `#r "nuget:..."` . Örneğin, aşağıdaki paket başvurusunu göz önünde bulundurun:

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn "%s" (JsonConvert.SerializeObject o)
```

Ayrıca, paketin adından sonra aşağıdaki gibi bir açık sürüm sağlayabilirsiniz:

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

Paket, ML.NET gibi yerel bağımlılıklarla destek paketlerine başvurur.

Paket başvuruları, bağımlı s 'ye başvurma konusunda özel gereksinimlere sahip paketleri de destekler `.dll` . Örneğin, kullanıcıların [FParsec](https://www.nuget.org/packages/FParsec/) `FParsecCS.dll` `FParsec.dll` F# Etkileşimli ' de başvurulmadan önce kendisine bağımlı olarak başvurulduğunu El Ile garantilemek Için kullanılan fparsec paketi. Artık gerekli değildir ve pakete aşağıdaki gibi başvurabilirsiniz:

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn "Success: %A" result
    | Failure(errorMsg, _, _) -> printfn "Failure: %s" errorMsg

test pfloat "1.234"
```

Paket başvuruları hakkında daha fazla bilgi için [F# Etkileşimli](../tutorials/fsharp-interactive/index.md) öğreticisine bakın.

## <a name="string-interpolation"></a>Dize ilişkilendirme

F # enterpolasyonlu dizeler, C# veya JavaScript 'te enterpolasyonlu dizeler için oldukça benzerdir. böylece, bir dize sabit değeri içinde "delikler" içinde kod yazmanızı sağlar Basit bir örnek verelim:

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

Ancak, F # enterpolasyonlu dizeler aynı zamanda işlev gibi tür atanmış ara için de, `sprintf` enterpolasyonlu bağlam içindeki bir ifadenin belirli bir türe uygun olmasını zorunlu kılmak için de izin verir. Aynı biçim belirticilerini kullanır.

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

Önceki tür enterpolasyon örneğinde,, ilişkilendirme 'nin `%s` türü olmasını gerektirir `string` , ancak `%d` ilişkilendirme bir olmalıdır `integer` .

Ayrıca, herhangi bir rastgele F # ifadesi (veya ifadeleri) enterpolasyon bağlamının yanına yerleştirilebilir. Daha karmaşık bir ifade yazmak da olasıdır, örneğin:

```fsharp
let str =
    $"""The result of squaring each odd item in {[1..10]} is:
{
    let square x = x * x
    let isOdd x = x % 2 <> 0
    let oddSquares xs =
        xs
        |> List.filter isOdd
        |> List.map square
    oddSquares [1..10]
}
"""
```

Bu, uygulamada çok fazla yapmanız önerilmez.

## <a name="support-for-nameof"></a>NameOf desteği

F # 5, `nameof` için kullanılmakta olan sembolü çözümleyen ve f # kaynağında adını üreten işleci destekler. Bu, günlüğe kaydetme gibi çeşitli senaryolarda faydalıdır ve günlüğe kaydetme işleminin kaynak kodundaki değişikliklere karşı korunmasını sağlar.

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) (sprintf "Value passed in was %d." month)

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

Son satır bir özel durum oluşturur ve hata iletisinde "month" görüntülenir.

Neredeyse her F # yapısının adını alabilirsiniz:

```fsharp
module M =
    let f x = nameof x

printfn "%s" (M.f 12)
printfn "%s" (nameof M)
printfn "%s" (nameof M.f)
```

Üç son ekleme, operatörlerin nasıl çalıştığı ile ilgili değişiklikler: `nameof<'type-parameter>` genel tür parametreleri için form ekleme ve `nameof` bir model eşleştirme ifadesinde bir model olarak kullanma özelliği.

Bir işlecin adının alınması, kaynak dizesini verir. Derlenmiş forma ihtiyacınız varsa, bir işlecin derlenmiş adını kullanın:

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

Bir tür parametresinin adının alınması biraz farklı bir sözdizimi gerektirir:

```fsharp
type C<'TType> =
    member _.TypeName = nameof<'TType>
```

Bu `typeof<'T>` ve `typedefof<'T>` işleçlerine benzerdir.

F # 5, ifadelerde kullanılabilecek bir model için de destek ekler `nameof` `match` :

```fsharp
[<Struct; IsByRefLike>]
type RecordedEvent = { EventType: string; Data: ReadOnlySpan<byte> }

type MyEvent =
    | AData of int
    | BData of string

let deserialize (e: RecordedEvent) : MyEvent =
    match e.EventType with
    | nameof AData -> AData (JsonSerializer.Deserialize<int> e.Data)
    | nameof BData -> BData (JsonSerializer.Deserialize<string> e.Data)
    | t -> failwithf "Invalid EventType: %s" t
```

Önceki kod, Match ifadesinde dize sabit değeri yerine ' NameOf ' kullanır.

## <a name="open-type-declarations"></a>Açık tür bildirimleri

F # 5, açık tür bildirimleri için de destek ekler. Açık tür bildirimi, bazı farklı söz dizimi ve F # semantiğini sığdırmak için biraz farklı davranış dışında C# dilinde statik bir sınıf açma gibidir.

Açık tür bildirimleri sayesinde, `open` içindeki statik içerikleri açığa çıkarmak için herhangi bir tür yapabilirsiniz. Ayrıca, `open` içeriğini açığa çıkarmak için F # tanımlı birleşimler ve kayıtlar da oluşturabilirsiniz. Örneğin, bir modülde tanımlanmış bir birleşiminize sahipseniz ve durumlarına erişmek istiyorsanız ancak modülün tamamını açmak istemiyorsanız bu yararlı olabilir.

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

C# ' den farklı olarak, `open type` aynı ada sahip bir üyeyi kullanıma sunan iki tür üzerinde olduğunuzda, `open` diğer adı gölgeli son türden üye. Bu, zaten mevcut olan gölgeleme etrafında F # semantiğinin tutarlıdır.

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a>Yerleşik veri türleri için tutarlı Dilimleme davranışı

`FSharp.Core`F # 5 ' ten önce tutarlı olmaması için kullanılan yerleşik veri türlerini (dizi, liste, dize, 2B dizi, 3B dizi, 4d dizi) Dilimleme davranışı. Bazı kenar durumu davranışları özel durum oluşturdu ve bazı durumlar. F # 5 ' te, tüm yerleşik türler artık oluşturulması imkansız olan dilimler için boş dilimler döndürüyor:

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

// Before: would return empty list
// F# 5: same
let emptyList = l.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty array
let emptyArray = a.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty string
let emptyString = s.[-2..(-1)]
```

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a>FSharp. Core 'da 3B ve 4D dizileri için sabit Dizin dilimleri

F # 5,0, yerleşik 3B ve 4D dizi türlerinde sabit bir dizinle Dilimleme desteği sunar.

Bunu göstermek için aşağıdaki 3B diziyi göz önünde bulundurun:

*z = 0*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 0 | 1 |
| **1** | 2 | 3 |

*z = 1*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 4 | 5 |
| **1** | 6 | 7 |

Dilimi diziden ayıklamak istediğinizde ne olacak `[| 4; 5 |]` ? Bu artık çok basittir!

```fsharp
// First, create a 3D array to slice

let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

## <a name="f-quotations-improvements"></a>F # tırnak geliştirmeleri

F # [kod teklifleri](../language-reference/code-quotations.md) artık tür kısıtlaması bilgilerini tutma özelliğine sahiptir. Aşağıdaki örneği inceleyin:

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

İşlev tarafından oluşturulan kısıtlama `inline` , kod kullanımı içinde tutulur. `negate`İşlevin alıntı yapılabilir formu artık değerlendirilebilirler.

## <a name="applicative-computation-expressions"></a>Uygulama hesaplama Ifadeleri

[Hesaplama ifadeleri (CEs)](../language-reference/computation-expressions.md) , bugün "bağlamsal hesaplamalar" modellemek için veya daha işlevsel programlama kolay terminolojisinde, birli hesaplamalar için kullanılır.

F # 5, farklı bir hesaplama modeli sunan uygulama ve uygulama sunar. Uygulama, her hesaplamanın bağımsız olduğu ve sonuçları sonunda biriktiği için daha verimli hesaplamalar sağlar. Hesaplamalar diğerinden bağımsız olduğunda, Ayrıca, CE yazarlarının daha verimli kitaplıklar yazmasına olanak tanımak de oldukça paralelleştirilebilir. Bu avantaj bir kısıtlamada gelir, ancak daha önce hesaplanan değerlere bağımlı olan hesaplamalar buna izin verilmez.

Aşağıdaki örnek, türü için temel bir uygulama gösterir `Result` .

```fsharp
// First, define a 'zip' function
module Result =
    let zip x1 x2 =
        match x1,x2 with
        | Ok x1res, Ok x2res -> Ok (x1res, x2res)
        | Error e, _ -> Error e
        | _, Error e -> Error e

// Next, define a builder with 'MergeSources' and 'BindReturn'
type ResultBuilder() =
    member _.MergeSources(t1: Result<'T,'U>, t2: Result<'T1,'U>) = Result.zip t1 t2
    member _.BindReturn(x: Result<'T,'U>, f) = Result.map f x

let result = ResultBuilder()

let run r1 r2 r3 =
    // And here is our applicative!
    let res1: Result<int, string> =
        result {
            let! a = r1
            and! b = r2
            and! c = r3
            return a + b - c
        }

    match res1 with
    | Ok x -> printfn "%s is: %d" (nameof res1) x
    | Error e -> printfn "%s is: %s" (nameof res1) e

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

Günümüzde bu kitaplıkta yer alan bir kitaplık yazarımız varsa, bilmeniz gereken bazı ek hususlar vardır.

## <a name="interfaces-can-be-implemeneted-at-different-generic-instantiations"></a>Arabirimler farklı genel örneklerde uygulanabilir

Artık aynı arabirimi farklı genel örneklerde de uygulayabilirsiniz:

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="default-interface-member-consumption"></a>Varsayılan arabirim üyesi tüketimi

F # 5, [arabirimleri varsayılan uygulamalarla](../../csharp/tutorials/default-interface-methods-versions.md)kullanmanıza olanak sağlar.

C# ' de tanımlanan bir arabirimi şöyle düşünün:

```csharp
using System;

namespace CSharp
{
    public interface MyDimasd
    {
        public int Z => 0;
    }
}
```

Bunu F # içinde, bir arabirimi uygulama konusunda standart yollardan herhangi biriyle kullanabilirsiniz:

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn "DIM from C#: %d" md.Z

// You can also implement it via an object expression
let md' = { new MyDim }
printfn "DIM from C# but via Object Expression: %d" md'.Z
```

Bu, kullanıcıların varsayılan bir uygulama kullanabilmesini beklediklerinde modern C# dilinde yazılmış C# kodu ve .NET bileşenlerinden yararlanarak güvenle yararlanmanızı sağlar.

## <a name="simplified-interop-with-nullable-value-types"></a>Null yapılabilir değer türleriyle Basitleştirilmiş birlikte çalışma

[Null yapılabilir (değer) türleri](https://docs.microsoft.com/dotnet/api/system.nullable-1) (tarihsel olarak null yapılabilir türler olarak adlandırılır) F # tarafından desteklenmelidir, ancak bunlarla etkileşim kurmak istediğiniz `Nullable` her seferinde bir veya sarmalayıcı oluşturmanız gerektiğinden bu, geleneksel olarak bir sorun teşkil etti `Nullable<SomeType>` . Artık derleyici, hedef türü eşleşiyorsa bir değer türünü bir olarak öğesine dönüştürür `Nullable<ThatValueType>` . Aşağıdaki kod artık mümkündür:

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

## <a name="preview-reverse-indexes"></a>Önizleme: ters dizinler

F # 5 Ayrıca ters dizinlere izin vermek için bir önizleme sunar. Söz dizimi `^idx` şeklindedir. Listenin sonundan bir öğe 1 değeri aşağıdaki gibi olabilir:

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

Ayrıca, kendi türleriniz için ters dizinler tanımlayabilirsiniz. Bunu yapmak için aşağıdaki yöntemi uygulamanız gerekir:

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

Türü için bir örnek aşağıda verilmiştir `Span<'T>` :

```fsharp
open System

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

    member sp.GetReverseIndex(_, offset: int) =
        sp.Length - offset

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let run () =
    let sp = [| 1; 2; 3; 4; 5 |].AsSpan()

    // Pre-# 5.0 slicing on a Span<'T>
    printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..3] // [|1; 2; 3|]
    printSpan sp.[1..3] // |2; 3|]

    // Same slices, but only using from-the-end index
    printSpan sp.[..^0] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..^2] // [|1; 2; 3|]
    printSpan sp.[^4..^2] // [|2; 3|]

run() // Prints the same thing twice
```

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a>Önizleme: hesaplama ifadelerinde özel anahtar sözcüklerin aşırı yüklemeleri

Hesaplama ifadeleri, kitaplık ve çerçeve yazarları için güçlü bir özelliktir. Bunlar, çalışmakta olduğunuz etki alanı için iyi bilinen üyeleri tanımlamanıza ve bir DSL oluşturacak şekilde bileşenlerinizi önemli ölçüde iyileştirmenize olanak tanır.

F # 5 hesaplama Ifadelerinde ek yükleme özel işlemleri için Önizleme desteği ekler. Aşağıdaki kodun yazıldı ve tüketilmesi için aşağıdaki kodun kullanılmasına izin verir:

```fsharp
open System

type InputKind =
    | Text of placeholder:string option
    | Password of placeholder: string option

type InputOptions =
  { Label: string option
    Kind : InputKind
    Validators : (string -> bool) array }

type InputBuilder() =
    member t.Yield(_) =
      { Label = None
        Kind = Text None
        Validators = [||] }

    [<CustomOperation("text")>]
    member this.Text(io, ?placeholder) =
        { io with Kind = Text placeholder }

    [<CustomOperation("password")>]
    member this.Password(io, ?placeholder) =
        { io with Kind = Password placeholder }

    [<CustomOperation("label")>]
    member this.Label(io, label) =
        { io with Label = Some label }

    [<CustomOperation("with_validators")>]
    member this.Validators(io, [<ParamArray>] validators) =
        { io with Validators = validators }

let input = InputBuilder()

let name =
    input {
    label "Name"
    text
    with_validators
        (String.IsNullOrWhiteSpace >> not)
    }

let email =
    input {
    label "Email"
    text "Your email"
    with_validators
        (String.IsNullOrWhiteSpace >> not)
        (fun s -> s.Contains "@")
    }

let password =
    input {
    label "Password"
    password "Must contains at least 6 characters, one number and one uppercase"
    with_validators
        (String.exists Char.IsUpper)
        (String.exists Char.IsDigit)
        (fun s -> s.Length >= 6)
    }
```

Bu değişiklikten önce, `InputBuilder` türü olduğu gibi yazabilirsiniz, ancak örnekte kullanıldığı şekilde kullanamazsınız. Aşırı Yüklemeler, isteğe bağlı parametreler ve artık `System.ParamArray` türlere izin verildiğinden, her şey yalnızca istediğiniz gibi çalışmaktadır.
