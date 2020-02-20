---
title: Anonim Kayıtlar
description: Oluşturma ve veri işlemeye yardımcı olacak bir dil özelliği olan anonim kayıtları nasıl kullanacağınızı öğrenin.
ms.date: 06/12/2019
ms.openlocfilehash: 061fd3279c84b9a3161c687d9392947ee7ce9c83
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453032"
---
# <a name="anonymous-records"></a>Anonim Kayıtlar

Anonim kayıtlar, kullanılmadan önce bildirilmesini gerektirmeyen adlandırılmış değerlerin basit toplamalarda bulunur. Bunları yapılar veya başvuru türleri olarak bildirebilirsiniz. Bunlar varsayılan olarak başvuru türlerdir.

## <a name="syntax"></a>Sözdizimi

Aşağıdaki örneklerde anonim kayıt sözdizimi gösterilmektedir. `[item]` olarak sınırlandırılmış öğeler isteğe bağlıdır.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Temel kullanım

Anonim kayıtlar, örnek oluşturmadan önce bildirilmesini F# gerektirmeyen kayıt türleri olarak en iyi şekilde düşünülebilir.

Örneğin, burada anonim bir kayıt üreten bir işlevle etkileşim kurabilirsiniz:

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

Aşağıdaki örnek, giriş olarak anonim bir kaydı alan `printCircleStats` bir işlevle önceki bir üzerinde genişletilir:

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

Giriş türü derlenemeyeceği için aynı "şekle" sahip olmayan herhangi bir anonim kayıt türüyle `printCircleStats` çağrısı başarısız olur:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Yapı anonim kayıtları

Anonim kayıtlar, isteğe bağlı `struct` anahtar sözcüğüyle yapı olarak da tanımlanabilir. Aşağıdaki örnek, bir struct anonim kaydı üreterek ve tüketerek bir öncekini genişlettiğini azaltır:

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

### <a name="structness-inference"></a>Struclük çıkarımı

Yapı anonim kayıtları, çağrı sitesinde `struct` anahtar sözcüğünü belirtmeniz gerekmeyen "yapı zaman çıkarımı" için de izin verir. Bu örnekte, `printCircleStats`çağrılırken `struct` anahtar sözcüğünü devre dışı olursunuz:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Ters desenler-giriş türü bir struct anonim kayıt olmadığında `struct` belirtmek için derleme başarısız olur.

## <a name="embedding-anonymous-records-within-other-types"></a>Anonim kayıtları diğer türler içine ekleme

Durumları kayıtları olan [ayrılmış birleşimler](discriminated-unions.md) bildirmek yararlı olur. Ancak Kayıtlardaki veriler ayrılmış birleşimle aynı türde ise, tüm türleri birbirini dışlayan özyinelemeli olarak tanımlamanız gerekir. Anonim kayıtları kullanmak bu kısıtlamayı önler. Aşağıdaki örnek bir tür ve bir düzenin onunla eşleşen işlevdir:

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

## <a name="copy-and-update-expressions"></a>İfadeleri Kopyala ve Güncelleştir

Anonim kayıtlar [kopyalama ve güncelleştirme ifadeleri](copy-and-update-record-expressions.md)ile oluşturmayı destekler. Örneğin, var olan bir kaynağın verilerini kopyalayan bir anonim kaydın yeni bir örneğini nasıl oluşturabileceğiniz aşağıda açıklanmıştır:

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Ancak, adlandırılmış kayıtlardan farklı olarak, anonim kayıtlar kopyalama ve güncelleştirme ifadelerine tamamen farklı formlar oluşturmanız için izin verir. Aşağıdaki örnek, önceki örnekteki aynı anonim kaydı alır ve yeni bir anonim kayda genişletir:

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

Ayrıca, başvuruya ve yapı anonim kayıtlarına veri kopyalayabilirsiniz:

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

Anonim kayıtlar, nasıl kullanılabilecekleri hakkında tam olarak anlamak için gereken birçok özelliğe sahiptir.

### <a name="anonymous-records-are-nominal"></a>Anonim kayıtlar kabul edilir

Anonim kayıtlar [nominal türlerdir](https://en.wikipedia.org/wiki/Nominal_type_system). Bunlar, önde gelen bildirim gerektirmeyen adlandırılmış [kayıt](records.md) türleri (de kabul edilir) olarak en iyi şekilde düşünüldüler.

İki anonim kayıt bildirimi ile aşağıdaki örneği göz önünde bulundurun:

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

`x` ve `y` değerleri farklı türlere sahiptir ve birbiriyle uyumlu değildir. Bunlar equatable değildir ve karşılaştırılabilir değildir. Bunu göstermek için adlandırılmış bir kayıt eşdeğerini göz önünde bulundurun:

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Tür Denkliği veya karşılaştırmayla ilgili olarak adlandırılmış kayıt eşdeğerleri ile karşılaştırıldığında anonim kayıtlar hakkında doğal olarak farklı bir şey yoktur.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Anonim kayıtlar yapısal eşitlik ve karşılaştırma kullanır

Kayıt türleri gibi anonim kayıtlar yapısal equatable ve karşılaştırılabilir. Bu yalnızca, tüm bileşen türleri eşitlik ve karşılaştırmayı destekliyorsa, örneğin, kayıt türleriyle geçerlidir. Eşitlik veya karşılaştırmayı desteklemek için, iki anonim kayıt aynı "şekle" sahip olmalıdır.

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Anonim kayıtlar seri hale getirilebilir

Anonim kayıtları, adlandırılmış kayıtlarla yaptığınız gibi seri hale getirebilirsiniz. [Newtonsoft. JSON](https://www.nuget.org/packages/Newtonsoft.Json/)kullanarak bir örnek aşağıda verilmiştir:

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip') 

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Anonim kayıtlar, serileştirilmiş/seri durumdan çıkarılan türler için bir etki alanı tanımlamaya gerek olmadan bir ağ üzerinden hafif veri göndermek için yararlıdır.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Anonim türlerle birlikte C# çalışan anonim kayıtlar

Anonim türlerin kullanılması gereken bir .NET API 'si kullanmak mümkündür. [ C# ](../../csharp/programming-guide/classes-and-structs/anonymous-types.md) C#anonim türler, anonim kayıtlar kullanılarak ile birlikte çalışır. Aşağıdaki örnek, anonim kayıtların adsız bir tür gerektiren bir [LINQ](../../csharp/programming-guide/concepts/linq/index.md) aşırı yüklemesini çağırmak için nasıl kullanılacağını gösterir:

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

.NET genelinde bir anonim türde geçirme kullanılması gereken çok sayıda diğer API 'Ler vardır. Anonim kayıtlar, bu kişilerle çalışmaya yönelik aracımız.

## <a name="limitations"></a>Sınırlamalar

Anonim kayıtlar, kullanımlarında bazı kısıtlamalar vardır. Bazıları tasarımına göre değişir, ancak başkaları değiştirebilecektir.

### <a name="limitations-with-pattern-matching"></a>Model eşleştirme sınırlamaları

Anonim kayıtlar, adlandırılmış kayıtlardan farklı olarak, model eşleştirmeyi desteklemez. Üç neden vardır:

1. Adlandırılmış kayıt türlerinden farklı olarak, bir düzenin adsız kaydın her alanı için bir hesaba sahip olması gerekir. Bunun nedeni, anonim kayıtların yapısal alt yazmayı desteklememe yöntemidir. Bunlar, nominal türlerdir.
2. (1) nedeniyle, her farklı düzen farklı bir anonim kayıt türünü aşacağından, desen eşleştirme ifadesinde ek desenler olamaz.
3. (3) nedeniyle, herhangi bir anonim kayıt deseninin "nokta" gösterimi kullanmaktan daha ayrıntılı olması gerekir.

[Sınırlı bağlamlarda model eşleştirmeye izin veren](https://github.com/fsharp/fslang-suggestions/issues/713)açık bir dil önerisi vardır.

### <a name="limitations-with-mutability"></a>Değiştirici ile sınırlamalar

`mutable` verileri olan anonim bir kayıt tanımlamak Şu anda mümkün değildir. Değişebilir verilere izin veren [açık bir dil önerisi](https://github.com/fsharp/fslang-suggestions/issues/732) vardır.

### <a name="limitations-with-struct-anonymous-records"></a>Struct anonim kayıtlarıyla sınırlamalar

Yapı anonim kayıtlarını `IsByRefLike` veya `IsReadOnly`olarak bildirmek mümkün değildir. `IsByRefLike` ve anonim kayıtları `IsReadOnly` için [açık bir dil önerisi](https://github.com/fsharp/fslang-suggestions/issues/712) vardır.
