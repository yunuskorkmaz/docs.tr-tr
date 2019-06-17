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
# <a name="anonymous-records"></a><span data-ttu-id="adf27-103">Anonim kayıtları</span><span class="sxs-lookup"><span data-stu-id="adf27-103">Anonymous Records</span></span>

<span data-ttu-id="adf27-104">Basit toplamalarla kullanılmadan önce bildirilmesine gerekmez adlandırılmış değerler anonim kayıtlardır.</span><span class="sxs-lookup"><span data-stu-id="adf27-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="adf27-105">Bunları yapılar veya başvuru türleri olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="adf27-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="adf27-106">Bunlar, başvuru türleri varsayılan olarak hedeflenmiştir.</span><span class="sxs-lookup"><span data-stu-id="adf27-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="adf27-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adf27-107">Syntax</span></span>

<span data-ttu-id="adf27-108">Aşağıdaki örnekler, anonim kayıt sözdizimini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="adf27-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="adf27-109">Öğeleri ayrılmış olarak `[item]` isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="adf27-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="adf27-110">Temel kullanım</span><span class="sxs-lookup"><span data-stu-id="adf27-110">Basic usage</span></span>

<span data-ttu-id="adf27-111">Anonim kayıt en iyi düşündüğünüz biri olarak F# kayıt türleri oluşturmada önce bildirilmiş gerekmez.</span><span class="sxs-lookup"><span data-stu-id="adf27-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="adf27-112">Bir işlev ile etkileşim kurabilir nasıl Örneğin, burada, anonim bir kayıt oluşturur:</span><span class="sxs-lookup"><span data-stu-id="adf27-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="adf27-113">Aşağıdaki örnek Öncekine ile genişletir. bir `printCircleStats` işlevi giriş olarak anonim bir kaydı alır:</span><span class="sxs-lookup"><span data-stu-id="adf27-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="adf27-114">Çağırma `printCircleStats` aynı "şekline" giriş türü derleme başarısız olarak olmayan anonim tüm kayıt türleri ile:</span><span class="sxs-lookup"><span data-stu-id="adf27-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="adf27-115">Yapı anonim kayıtları</span><span class="sxs-lookup"><span data-stu-id="adf27-115">Struct anonymous records</span></span>

<span data-ttu-id="adf27-116">Anonim kayıtları da tanımlanabilir yapıyla birlikte isteğe bağlı olarak `struct` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="adf27-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="adf27-117">Aşağıdaki örnek, oluşturmayı ve bir yapı anonim kaydı tüketen Öncekine artırmaktadır:</span><span class="sxs-lookup"><span data-stu-id="adf27-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="adf27-118">Structness çıkarımı</span><span class="sxs-lookup"><span data-stu-id="adf27-118">Structness inference</span></span>

<span data-ttu-id="adf27-119">Yapı anonim kayıtları da burada belirtmeniz gerekmez "structness çıkarımı için" izin `struct` anahtar sözcüğü çağrısı sitesinde.</span><span class="sxs-lookup"><span data-stu-id="adf27-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="adf27-120">Bu örnekte, elide `struct` çağırırken anahtar sözcüğü `printCircleStats`:</span><span class="sxs-lookup"><span data-stu-id="adf27-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="adf27-121">Ters deseni - belirtme `struct` giriş türü bir yapı anonim kaydı - olmadığında derleme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="adf27-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="adf27-122">Diğer türleri içinde anonim kayıt ekleme</span><span class="sxs-lookup"><span data-stu-id="adf27-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="adf27-123">Bildirmek kullanışlıdır [ayrılmış birleşimler](discriminated-unions.md) olan durumlarda kayıtlardır.</span><span class="sxs-lookup"><span data-stu-id="adf27-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="adf27-124">Ancak kayıtlardaki veriler birleşimdir aynı türde ise, tüm türleri karşılıklı özyinelemeli tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="adf27-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="adf27-125">Anonim kayıtları kullanarak bu kısıtlama önler.</span><span class="sxs-lookup"><span data-stu-id="adf27-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="adf27-126">Bir örnek aşağıda verilmiştir tür ve işlevi bu desenle eşleşen üzerine:</span><span class="sxs-lookup"><span data-stu-id="adf27-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="adf27-127">Kopyalama ve güncelleştirme ifadeleri</span><span class="sxs-lookup"><span data-stu-id="adf27-127">Copy and update expressions</span></span>

<span data-ttu-id="adf27-128">Anonim kayıtları desteği çalışılmış [kopyalama ve güncelleştirme ifadeleri](copy-and-update-record-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="adf27-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="adf27-129">Örneğin, işte birinin mevcut kopyalayan bir anonim kaydı yeni bir örneğini nasıl oluşturabilirsiniz veri:</span><span class="sxs-lookup"><span data-stu-id="adf27-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="adf27-130">Ancak, adlandırılmış kayıtları, anonim kayıtları, kopyalama ile tamamen farklı formları oluşturmak ve ifadeleri güncelleştirme olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="adf27-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="adf27-131">Aşağıdaki örnekte, önceki örnekte aynı anonim kaydı alır ve yeni bir anonim kayıtta genişletir:</span><span class="sxs-lookup"><span data-stu-id="adf27-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="adf27-132">Adlandırılmış kayıtları örneklerini anonim kayıtları oluşturmak mümkündür:</span><span class="sxs-lookup"><span data-stu-id="adf27-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="adf27-133">Ayrıca, başvuru ve yapı anonim kayıtlarını gelen ve giden veri kopyalayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="adf27-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="adf27-134">Anonim kayıtlarının özelliklerini</span><span class="sxs-lookup"><span data-stu-id="adf27-134">Properties of anonymous records</span></span>

<span data-ttu-id="adf27-135">Anonim kayıtları çeşitli tam olarak bunlar nasıl kullanılabileceğini anlamak için gerekli olan özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="adf27-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="adf27-136">Anonim kayıtları nominal</span><span class="sxs-lookup"><span data-stu-id="adf27-136">Anonymous records are nominal</span></span>

<span data-ttu-id="adf27-137">Anonim kayıtlar [nominal türleri](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="adf27-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="adf27-138">En iyi düşünce olarak adlandırılan oldukları [kayıt](records.md) bir ön bildirimi gerektirmeyen (nominal) türü.</span><span class="sxs-lookup"><span data-stu-id="adf27-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="adf27-139">Aşağıdaki örnek iki anonim kayıt bildirimi ile göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="adf27-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="adf27-140">`x` Ve `y` değerleri farklı olan ve birbiriyle uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="adf27-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="adf27-141">Bunlar equatable değildir ve bunlar karşılaştırılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="adf27-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="adf27-142">Bunu açıklamak üzere; adlı bir kayıt eşdeğer göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="adf27-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="adf27-143">Adlandırılmış kayıt eşdeğerlerine tür denkliği veya karşılaştırma ilgili olduğunda karşılaştırıldığında anonim kayıtları hakkında doğal olarak farklı bir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="adf27-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="adf27-144">Anonim kayıtları yapısal eşitlik ve karşılaştırma kullan</span><span class="sxs-lookup"><span data-stu-id="adf27-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="adf27-145">Kayıt türleri gibi yapısal olarak equatable ve karşılaştırılabilir anonim kaydeder.</span><span class="sxs-lookup"><span data-stu-id="adf27-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="adf27-146">Bu seçenek yalnızca bağlı olan tüm türleri eşitlik ve karşılaştırma gibi kayıt türleri ile destekliyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="adf27-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="adf27-147">Eşitlik ya da karşılaştırma desteklemek için iki anonim kaydı "şekline" aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="adf27-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="adf27-148">Anonim kayıtları seri hale getirilebilir</span><span class="sxs-lookup"><span data-stu-id="adf27-148">Anonymous records are serializable</span></span>

<span data-ttu-id="adf27-149">Adlandırılmış kayıtlarla gibi anonim kayıtları serileştirebiliyorsa.</span><span class="sxs-lookup"><span data-stu-id="adf27-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="adf27-150">İşte bir örnek kullanarak [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="adf27-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="adf27-151">Anonim kayıtları, bir etki alanı için serileştirilmiş ve seri türlerinizi Önden tanımlamak için gerek kalmadan bir ağ üzerinden basit veri göndermek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="adf27-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="adf27-152">Anonim kayıtları birlikte çalışmanızın C# anonim türler</span><span class="sxs-lookup"><span data-stu-id="adf27-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="adf27-153">Kullanılmasını gerektiren .NET API'si kullanmak da mümkündür [ C# anonim türler](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="adf27-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="adf27-154">C#Anonim türler, anonim kayıtları kullanarak birlikte çalışmanız Önemsiz.</span><span class="sxs-lookup"><span data-stu-id="adf27-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="adf27-155">Aşağıdaki örnek çağırmak için anonim kayıtları kullanmayı gösterir. bir [LINQ](../../csharp/programming-guide/concepts/linq/index.md) anonim bir tür gerektiren aşırı yükleme:</span><span class="sxs-lookup"><span data-stu-id="adf27-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="adf27-156">Çok sayıda geçirme anonim bir tür kullanımı gerektiren .NET kullanılan diğer API'ler vardır.</span><span class="sxs-lookup"><span data-stu-id="adf27-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="adf27-157">Aracınızın onlarla çalışmak için anonim kayıtlardır.</span><span class="sxs-lookup"><span data-stu-id="adf27-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="adf27-158">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="adf27-158">Limitations</span></span>

<span data-ttu-id="adf27-159">Anonim kayıtların kullanımları bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="adf27-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="adf27-160">Bazı bunların tasarıma belirlidir, ancak diğerleri değiştirmek için tfs'deki.</span><span class="sxs-lookup"><span data-stu-id="adf27-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="adf27-161">Desen eşleştirme ile sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="adf27-161">Limitations with pattern matching</span></span>

<span data-ttu-id="adf27-162">Anonim kayıtlar adlandırılmış kayıtları desen eşleştirme desteklemez.</span><span class="sxs-lookup"><span data-stu-id="adf27-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="adf27-163">Üç neden vardır:</span><span class="sxs-lookup"><span data-stu-id="adf27-163">There are three reasons:</span></span>

1. <span data-ttu-id="adf27-164">Bir desen adlandırılmış kayıt türlerinin aksine, anonim bir kaydın tüm alanlarını hesabı gerekir.</span><span class="sxs-lookup"><span data-stu-id="adf27-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="adf27-165">Bunun nedeni anonim kayıtları yapısal subtyping desteklemeyen – bunlar nominal türleridir.</span><span class="sxs-lookup"><span data-stu-id="adf27-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="adf27-166">(1) nedeniyle ek bir desen eşleme ifadesi sahiptir olanağı her ayrı desen farklı bir anonim kayıt türü yaptığından gibi bulunur.</span><span class="sxs-lookup"><span data-stu-id="adf27-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="adf27-167">Tüm anonim kayıt düzeni nedeniyle (3), "dot" belirtimi kullanımını daha fazla ayrıntılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="adf27-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="adf27-168">Bir açık dil önerinizi yoktur [desen eşleştirme içinde sınırlı bağlamları izin](https://github.com/fsharp/fslang-suggestions/issues/713).</span><span class="sxs-lookup"><span data-stu-id="adf27-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="adf27-169">Kesilebilirlik sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="adf27-169">Limitations with mutability</span></span>

<span data-ttu-id="adf27-170">Anonim bir kayıtla tanımlamak şu anda mümkün değildir `mutable` veri.</span><span class="sxs-lookup"><span data-stu-id="adf27-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="adf27-171">Var olan bir [dil öneri açın](https://github.com/fsharp/fslang-suggestions/issues/732) değişebilir veri izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="adf27-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="adf27-172">Yapı anonim kayıtlarla sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="adf27-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="adf27-173">Yapı anonim kayıtları olarak bildirmek mümkün değildir `IsByRefLike` veya `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="adf27-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="adf27-174">Var. bir [açın dil öneri](https://github.com/fsharp/fslang-suggestions/issues/712) için için `IsByRefLike` ve `IsReadOnly` anonim kaydeder.</span><span class="sxs-lookup"><span data-stu-id="adf27-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
