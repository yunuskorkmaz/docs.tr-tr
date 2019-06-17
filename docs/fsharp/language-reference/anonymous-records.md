---
title: Anonim kayıtları
description: Yapı kullanan ve anonim kayıtları, verilerin işlenmesini bir dil özelliği kullanma hakkında bilgi edinin.
ms.date: 06/12/2019
ms.openlocfilehash: e576210d4fb76ccfd09f8feb157ef4542aa94ccf
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041796"
---
# <a name="anonymous-records"></a>Anonim kayıtları

Basit toplamalarla kullanılmadan önce bildirilmesine gerekmez adlandırılmış değerler anonim kayıtlardır. Bunları yapılar veya başvuru türleri olarak bildirebilirsiniz. Bunlar, başvuru türleri varsayılan olarak hedeflenmiştir.

## <a name="syntax"></a>Sözdizimi

Aşağıdaki örnekler, anonim kayıt sözdizimini göstermektedir. Öğeleri ayrılmış olarak `[item]` isteğe bağlıdır.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Temel kullanım

Anonim kayıt en iyi düşündüğünüz biri olarak F# kayıt türleri oluşturmada önce bildirilmiş gerekmez.

Bir işlev ile etkileşim kurabilir nasıl Örneğin, burada, anonim bir kayıt oluşturur:

```fsharp

open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Aşağıdaki örnek Öncekine ile genişletir. bir `printCircleStats` işlevi giriş olarak anonim bir kaydı alır:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let printCircleStats r (stats: {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

Çağırma `printCircleStats` aynı "şekline" giriş türü derleme başarısız olarak olmayan anonim tüm kayıt türleri ile:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Yapı anonim kayıtları

Anonim kayıtları da tanımlanabilir yapıyla birlikte isteğe bağlı olarak `struct` anahtar sözcüğü. Aşağıdaki örnek, oluşturmayı ve bir yapı anonim kaydı tüketen Öncekine artırmaktadır:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    // Note that the keyword comes before the '{| |}' brace pair
    struct {| Area = a; Circumference = c; Diameter = d |}

// the 'struct' keyword also comes before the '{| |}' brace pair when declaring the parameter type
let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

### <a name="structness-inference"></a>Structness çıkarımı

Yapı anonim kayıtları da burada belirtmeniz gerekmez "structness çıkarımı için" izin `struct` anahtar sözcüğü çağrısı sitesinde. Bu örnekte, elide `struct` çağırırken anahtar sözcüğü `printCircleStats`:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Ters deseni - belirtme `struct` giriş türü bir yapı anonim kaydı - olmadığında derleme başarısız olur.

## <a name="embedding-anonymous-records-within-other-types"></a>Diğer türleri içinde anonim kayıt ekleme

Bildirmek kullanışlıdır [ayrılmış birleşimler](discriminated-unions.md) olan durumlarda kayıtlardır. Ancak kayıtlardaki veriler birleşimdir aynı türde ise, tüm türleri karşılıklı özyinelemeli tanımlamanız gerekir. Anonim kayıtları kullanarak bu kısıtlama önler. Bir örnek aşağıda verilmiştir tür ve işlevi bu desenle eşleşen üzerine:

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named for Manager and Executive would require mutually recursive definitions.
type Employee =
    | Engineer of FullName
    | Manager of {| Name: FullName; Reports: Employee list |}
    | Executive of {| Name: FullName; Reports: Employee list; Assistant: Employee |}

let getFirstName e =
    match e with
    | Engineer fullName -> fullName.FirstName
    | Manager m -> m.Name.FirstName
    | Executive ex -> ex.Name.FirstName
```

## <a name="copy-and-update-expressions"></a>Kopyalama ve güncelleştirme ifadeleri

Anonim kayıtları desteği çalışılmış [kopyalama ve güncelleştirme ifadeleri](copy-and-update-record-expressions.md). Örneğin, işte birinin mevcut kopyalayan bir anonim kaydı yeni bir örneğini nasıl oluşturabilirsiniz veri:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Ancak, adlandırılmış kayıtları, anonim kayıtları, kopyalama ile tamamen farklı formları oluşturmak ve ifadeleri güncelleştirme olanak tanır. Aşağıdaki örnekte, önceki örnekte aynı anonim kaydı alır ve yeni bir anonim kayıtta genişletir:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Adlandırılmış kayıtları örneklerini anonim kayıtları oluşturmak mümkündür:

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Ayrıca, başvuru ve yapı anonim kayıtlarını gelen ve giden veri kopyalayabilirsiniz:

```fsharp
// Copy data from a reference record into a struct anonymous record
type R1 = { X: int }
let r1 = { X = 1 }

let data1 = struct {| r1 with Y = 1 |}

// Copy data from a struct record into a reference anonymous record
[<Struct>]
type R2 = { X: int }
let r2 = { X = 1 }

let data2 = {| r1 with Y = 1 |}

// Copy the reference anonymous record data into a struct anonymous record
let data3 = struct {| data2 with Z = r2.X |}
```

## <a name="properties-of-anonymous-records"></a>Anonim kayıtlarının özelliklerini

Anonim kayıtları çeşitli tam olarak bunlar nasıl kullanılabileceğini anlamak için gerekli olan özelliklere sahiptir.

### <a name="anonymous-records-are-nominal"></a>Anonim kayıtları nominal

Anonim kayıtlar [nominal türleri](https://en.wikipedia.org/wiki/Nominal_type_system). En iyi düşünce olarak adlandırılan oldukları [kayıt](records.md) bir ön bildirimi gerektirmeyen (nominal) türü.

Aşağıdaki örnek iki anonim kayıt bildirimi ile göz önünde bulundurun:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

`x` Ve `y` değerleri farklı olan ve birbiriyle uyumlu değildir. Bunlar equatable değildir ve bunlar karşılaştırılabilir değil. Bunu açıklamak üzere; adlı bir kayıt eşdeğer göz önünde bulundurun:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Adlandırılmış kayıt eşdeğerlerine tür denkliği veya karşılaştırma ilgili olduğunda karşılaştırıldığında anonim kayıtları hakkında doğal olarak farklı bir şey yoktur.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Anonim kayıtları yapısal eşitlik ve karşılaştırma kullan

Kayıt türleri gibi yapısal olarak equatable ve karşılaştırılabilir anonim kaydeder. Bu seçenek yalnızca bağlı olan tüm türleri eşitlik ve karşılaştırma gibi kayıt türleri ile destekliyorsa geçerlidir. Eşitlik ya da karşılaştırma desteklemek için iki anonim kaydı "şekline" aynı olması gerekir.

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Anonim kayıtları seri hale getirilebilir

Adlandırılmış kayıtlarla gibi anonim kayıtları serileştirebiliyorsa. İşte bir örnek kullanarak [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Anonim kayıtları, bir etki alanı için serileştirilmiş ve seri türlerinizi Önden tanımlamak için gerek kalmadan bir ağ üzerinden basit veri göndermek için kullanışlıdır.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Anonim kayıtları birlikte çalışmanızın C# anonim türler

Kullanılmasını gerektiren .NET API'si kullanmak da mümkündür [ C# anonim türler](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). C#Anonim türler, anonim kayıtları kullanarak birlikte çalışmanız Önemsiz. Aşağıdaki örnek çağırmak için anonim kayıtları kullanmayı gösterir. bir [LINQ](../../csharp/programming-guide/concepts/linq/index.md) anonim bir tür gerektiren aşırı yükleme:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Çok sayıda geçirme anonim bir tür kullanımı gerektiren .NET kullanılan diğer API'ler vardır. Aracınızın onlarla çalışmak için anonim kayıtlardır.

## <a name="limitations"></a>Sınırlamalar

Anonim kayıtların kullanımları bazı kısıtlamalar vardır. Bazı bunların tasarıma belirlidir, ancak diğerleri değiştirmek için tfs'deki.

### <a name="limitations-with-pattern-matching"></a>Desen eşleştirme ile sınırlamaları

Anonim kayıtlar adlandırılmış kayıtları desen eşleştirme desteklemez. Üç neden vardır:

1. Bir desen adlandırılmış kayıt türlerinin aksine, anonim bir kaydın tüm alanlarını hesabı gerekir. Bunun nedeni anonim kayıtları yapısal subtyping desteklemeyen – bunlar nominal türleridir.
2. (1) nedeniyle ek bir desen eşleme ifadesi sahiptir olanağı her ayrı desen farklı bir anonim kayıt türü yaptığından gibi bulunur.
3. Tüm anonim kayıt düzeni nedeniyle (3), "dot" belirtimi kullanımını daha fazla ayrıntılı olacaktır.

Bir açık dil önerinizi yoktur [desen eşleştirme içinde sınırlı bağlamları izin](https://github.com/fsharp/fslang-suggestions/issues/713).

### <a name="limitations-with-mutability"></a>Kesilebilirlik sınırlamaları

Anonim bir kayıtla tanımlamak şu anda mümkün değildir `mutable` veri. Var olan bir [dil öneri açın](https://github.com/fsharp/fslang-suggestions/issues/732) değişebilir veri izin vermek için.

### <a name="limitations-with-struct-anonymous-records"></a>Yapı anonim kayıtlarla sınırlamaları

Yapı anonim kayıtları olarak bildirmek mümkün değildir `IsByRefLike` veya `IsReadOnly`. Var. bir [açın dil öneri](https://github.com/fsharp/fslang-suggestions/issues/712) için için `IsByRefLike` ve `IsReadOnly` anonim kaydeder.
