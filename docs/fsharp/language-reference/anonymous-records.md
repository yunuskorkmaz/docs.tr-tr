---
title: Anonim Kayıtlar
description: Verilerin manipülasyonuna yardımcı olan bir dil özelliği olan Anonim Kayıtlar'ı oluşturma ve kullanma hakkında bilgi edinin.
ms.date: 06/12/2019
ms.openlocfilehash: ef3aa8fccdb6ff406542932816e4138040845a59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187489"
---
# <a name="anonymous-records"></a>Anonim Kayıtlar

Anonim kayıtlar, kullanılmadan önce bildirilmesi gerekmeyen adlandırılmış değerlerin basit toplamıdır. Bunları yapı veya başvuru türü olarak bildirebilirsiniz. Varsayılan olarak başvuru türleridir.

## <a name="syntax"></a>Sözdizimi

Aşağıdaki örnekler, anonim kayıt sözdizimini gösterir. Öğeler isteğe `[item]` bağlı olarak sınırlıdır.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Temel kullanım

Anonim kayıtlar, anlık olarak bildirilmesi gerekmeyen F# kayıt türleri olarak en iyi şekilde düşünülür.

Örneğin, burada anonim bir kayıt üreten bir işlevle nasıl etkileşimkurabilirsiniz:

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

Aşağıdaki örnek, giriş olarak anonim `printCircleStats` bir kayıt alan bir işlevle öncekinde genişler:

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

Giriş `printCircleStats` türüyle aynı "şekle" sahip olmayan herhangi bir anonim kayıt türüyle arama yapmak derlemek için başarısız olur:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Struct anonim kayıtları

Anonim kayıtlar, isteğe bağlı `struct` anahtar kelimeyle birlikte yapı olarak da tanımlanabilir. Aşağıdaki örnek, bir öncekini, bir yapı anonim kaydı üreterek ve tüketerek genişletir:

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

### <a name="structness-inference"></a>Structness çıkarım

Struct anonim kayıtları da arama sitesinde `struct` anahtar kelime belirtmeniz gerekmez "structness çıkarım" için izin verir. Bu örnekte, anahtar `struct` kelimeyi ararken aşağıdakileri alasınız: `printCircleStats`

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Ters desen - `struct` giriş türü bir yapı anonim kayıt ne zaman belirten - derlemek için başarısız olur.

## <a name="embedding-anonymous-records-within-other-types"></a>Anonim kayıtları diğer türlere gömme

Davaları kayıt olan [ayrımcı sendikaları](discriminated-unions.md) beyan etmek yararlı olur. Ancak kayıtlardaki veriler, ayrımyapılan birlikle aynı türdeyse, tüm türleri karşılıklı özyinelemeolarak tanımlamanız gerekir. Anonim kayıtların kullanılması bu kısıtlamayı önler. Aşağıdaki ler, üzerinde eşleşen bir örnek türü ve işlevidir:

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

## <a name="copy-and-update-expressions"></a>İfadeleri kopyalama ve güncelleştirme

Anonim kayıtlar [kopyalama ve güncelleştirme ifadeleri](copy-and-update-record-expressions.md)ile yapıyı destekler. Örneğin, varolan bir kaydın verilerini kopyalayan anonim bir kaydın yeni bir örneğini şu şekilde oluşturabilirsiniz:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Ancak, adlandırılmış kayıtların aksine, anonim kayıtlar kopyala ve güncelleştirme ifadeleri ile tamamen farklı formlar oluşturmanıza olanak sağlar. Aşağıdaki örnek, önceki örnekten aynı anonim kaydı alır ve yeni bir anonim kayda genişletir:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Adlandırılmış kayıt örneklerinden anonim kayıtlar oluşturmak da mümkündür:

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Ayrıca, bilgileri referans avesi ve yapı anonim kayıtlarına kopyalayabilirsiniz:

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

## <a name="properties-of-anonymous-records"></a>Anonim kayıtların özellikleri

Anonim kayıtlar, nasıl kullanılabileceğini tam olarak anlamak için gerekli olan bir dizi özelliktedir.

### <a name="anonymous-records-are-nominal"></a>Anonim kayıtlar nominal

Anonim kayıtlar [nominal türleridir.](https://en.wikipedia.org/wiki/Nominal_type_system) Bunlar en iyi adlandırılmış [kayıt](records.md) türleri olarak düşünülür (aynı zamanda nominal olan) bir ön bildirim gerektirmeyen.

İki anonim kayıt bildirimiyle aşağıdaki örneği göz önünde bulundurun:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

`x` Ve `y` değerleri farklı türleri vardır ve birbirleriyle uyumlu değildir. Onlar ekvatora uygun değildir ve karşılaştırılabilir değildir. Bunu göstermek için, adlandırılmış bir kayıt eşdeğeri düşünün:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Tür eşdeğerliği veya karşılaştırması ile ilgili olarak adlandırılmış kayıt eşdeğerleri ile karşılaştırıldığında anonim kayıtlar hakkında doğal olarak farklı bir şey yoktur.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Anonim kayıtlar yapısal eşitlik ve karşılaştırma kullanır

Kayıt türleri gibi, anonim kayıtlar yapısal olarak eşit lenebilir ve karşılaştırılabilir. Bu, yalnızca tüm kurucu türleri kayıt türleri gibi eşitliği ve karşılaştırmayı destekliyorsa geçerlidir. Eşitliği veya karşılaştırmayı desteklemek için, iki anonim kaydın aynı "şekle" sahip olması gerekir.

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Anonim kayıtlar serileştirilebilir

Anonim kayıtları, adlandırılmış kayıtlarla olabildiğince seri hale getirebilirsiniz. Burada [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/)kullanarak bir örnektir:

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Anonim kayıtlar, önceden serileştirilmiş/deserialized türleri niz için bir etki alanı tanımlamaya gerek kalmadan bir ağ üzerinden hafif veri göndermek için yararlıdır.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Anonim kayıtlar C# anonim türleri ile birlikte çalışır

[C# anonim türlerinin](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)kullanılmasını gerektiren bir .NET API kullanmak mümkündür. C# anonim türleri anonim kayıtları kullanarak birlikte çalışmak için önemsizdir. Aşağıdaki örnek, anonim bir tür gerektiren [bir LINQ](../../csharp/programming-guide/concepts/linq/index.md) aşırı yüklemesi çağırmak için anonim kayıtların nasıl kullanılacağını gösterir:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

.NET'te kullanılan ve anonim bir türde geçmenin kullanılmasını gerektiren çok sayıda başka API vardır. Anonim kayıtlar onlarla çalışmak için aracınızdır.

## <a name="limitations"></a>Sınırlamalar

Anonim kayıtların kullanımında bazı kısıtlamalar vardır. Bazıları tasarımlarının doğasında vardır, ancak diğerleri değişmeye elverişlidir.

### <a name="limitations-with-pattern-matching"></a>Desen eşleştirmesi ile sınırlamalar

Adlandırılmış kayıtların aksine, adlandırılmış kayıtlar desen eşleştirmeyi desteklemez. Üç nedeni vardır:

1. Adlandırılmış kayıt türlerinin aksine, bir desen anonim bir kaydın her alanını hesaba katmak zorunda kalırdı. Bunun nedeni, anonim kayıtların yapısal alt yazımı desteklememesidir – bunlar nominal türlerdir.
2. (1) nedeniyle, her farklı desen farklı bir anonim kayıt türü anlamına geleceğini gibi, bir desen eşleştirme ifadesinde ek desenler olması için hiçbir yeteneği yoktur.
3. (3) nedeniyle, herhangi bir anonim kayıt deseni "nokta" gösterimi kullanımından daha ayrıntılı olacaktır.

[Sınırlı bağlamlarda desen eşleştirmesine izin](https://github.com/fsharp/fslang-suggestions/issues/713)vermek için açık dil önerisi vardır.

### <a name="limitations-with-mutability"></a>Susturulabilirlik ile sınırlamalar

Şu anda verilerle `mutable` anonim bir kayıt tanımlamak mümkün değildir. Mutable verilere izin vermek için [açık dil önerisi](https://github.com/fsharp/fslang-suggestions/issues/732) vardır.

### <a name="limitations-with-struct-anonymous-records"></a>Yapı anonim kayıtları ile sınırlamalar

Struct anonim kayıtlarının "veya `IsByRefLike` `IsReadOnly`. " olarak bildirin mümkün değildir. Ve `IsByRefLike` `IsReadOnly` anonim kayıtlar için açık bir dil [önerisi](https://github.com/fsharp/fslang-suggestions/issues/712) vardır.
