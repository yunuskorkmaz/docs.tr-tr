---
title: Anonim Kayıtlar
description: Verilerin manipülasyonuna yardımcı olan bir dil özelliği olan Anonim Kayıtlar'ı oluşturma ve kullanma hakkında bilgi edinin.
ms.date: 06/12/2019
ms.openlocfilehash: 121f0f638dff2ae529b2488d8e3b1ad9c064cf90
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738497"
---
# <a name="anonymous-records"></a><span data-ttu-id="bf568-103">Anonim Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="bf568-103">Anonymous Records</span></span>

<span data-ttu-id="bf568-104">Anonim kayıtlar, kullanılmadan önce bildirilmesi gerekmeyen adlandırılmış değerlerin basit toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="bf568-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="bf568-105">Bunları yapı veya başvuru türü olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf568-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="bf568-106">Varsayılan olarak başvuru türleridir.</span><span class="sxs-lookup"><span data-stu-id="bf568-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf568-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf568-107">Syntax</span></span>

<span data-ttu-id="bf568-108">Aşağıdaki örnekler, anonim kayıt sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf568-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="bf568-109">Öğeler isteğe `[item]` bağlı olarak sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf568-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="bf568-110">Temel kullanım</span><span class="sxs-lookup"><span data-stu-id="bf568-110">Basic usage</span></span>

<span data-ttu-id="bf568-111">Anonim kayıtlar, anlık olarak bildirilmesi gerekmeyen F# kayıt türleri olarak en iyi şekilde düşünülür.</span><span class="sxs-lookup"><span data-stu-id="bf568-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="bf568-112">Örneğin, burada anonim bir kayıt üreten bir işlevle nasıl etkileşimkurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf568-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="bf568-113">Aşağıdaki örnek, giriş olarak anonim `printCircleStats` bir kayıt alan bir işlevle öncekinde genişler:</span><span class="sxs-lookup"><span data-stu-id="bf568-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="bf568-114">Giriş `printCircleStats` türüyle aynı "şekle" sahip olmayan herhangi bir anonim kayıt türüyle arama yapmak derlemek için başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="bf568-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="bf568-115">Struct anonim kayıtları</span><span class="sxs-lookup"><span data-stu-id="bf568-115">Struct anonymous records</span></span>

<span data-ttu-id="bf568-116">Anonim kayıtlar, isteğe bağlı `struct` anahtar kelimeyle birlikte yapı olarak da tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="bf568-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="bf568-117">Aşağıdaki örnek, bir öncekini, bir yapı anonim kaydı üreterek ve tüketerek genişletir:</span><span class="sxs-lookup"><span data-stu-id="bf568-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="bf568-118">Structness çıkarım</span><span class="sxs-lookup"><span data-stu-id="bf568-118">Structness inference</span></span>

<span data-ttu-id="bf568-119">Struct anonim kayıtları da arama sitesinde `struct` anahtar kelime belirtmeniz gerekmez "structness çıkarım" için izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf568-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="bf568-120">Bu örnekte, anahtar `struct` kelimeyi ararken aşağıdakileri alasınız: `printCircleStats`</span><span class="sxs-lookup"><span data-stu-id="bf568-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="bf568-121">Ters desen - `struct` giriş türü bir yapı anonim kayıt ne zaman belirten - derlemek için başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bf568-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="bf568-122">Anonim kayıtları diğer türlere gömme</span><span class="sxs-lookup"><span data-stu-id="bf568-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="bf568-123">Davaları kayıt olan [ayrımcı sendikaları](discriminated-unions.md) beyan etmek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="bf568-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="bf568-124">Ancak kayıtlardaki veriler, ayrımyapılan birlikle aynı türdeyse, tüm türleri karşılıklı özyinelemeolarak tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf568-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="bf568-125">Anonim kayıtların kullanılması bu kısıtlamayı önler.</span><span class="sxs-lookup"><span data-stu-id="bf568-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="bf568-126">Aşağıdaki ler, üzerinde eşleşen bir örnek türü ve işlevidir:</span><span class="sxs-lookup"><span data-stu-id="bf568-126">What follows is an example type and function that pattern matches over it:</span></span>

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named record for Manager and Executive would require mutually recursive definitions.
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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="bf568-127">İfadeleri kopyalama ve güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="bf568-127">Copy and update expressions</span></span>

<span data-ttu-id="bf568-128">Anonim kayıtlar [kopyalama ve güncelleştirme ifadeleri](copy-and-update-record-expressions.md)ile yapıyı destekler.</span><span class="sxs-lookup"><span data-stu-id="bf568-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="bf568-129">Örneğin, varolan bir kaydın verilerini kopyalayan anonim bir kaydın yeni bir örneğini şu şekilde oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf568-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="bf568-130">Ancak, adlandırılmış kayıtların aksine, anonim kayıtlar kopyala ve güncelleştirme ifadeleri ile tamamen farklı formlar oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf568-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="bf568-131">Aşağıdaki örnek, önceki örnekten aynı anonim kaydı alır ve yeni bir anonim kayda genişletir:</span><span class="sxs-lookup"><span data-stu-id="bf568-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="bf568-132">Adlandırılmış kayıt örneklerinden anonim kayıtlar oluşturmak da mümkündür:</span><span class="sxs-lookup"><span data-stu-id="bf568-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="bf568-133">Ayrıca, bilgileri referans avesi ve yapı anonim kayıtlarına kopyalayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf568-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="bf568-134">Anonim kayıtların özellikleri</span><span class="sxs-lookup"><span data-stu-id="bf568-134">Properties of anonymous records</span></span>

<span data-ttu-id="bf568-135">Anonim kayıtlar, nasıl kullanılabileceğini tam olarak anlamak için gerekli olan bir dizi özelliktedir.</span><span class="sxs-lookup"><span data-stu-id="bf568-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="bf568-136">Anonim kayıtlar nominal</span><span class="sxs-lookup"><span data-stu-id="bf568-136">Anonymous records are nominal</span></span>

<span data-ttu-id="bf568-137">Anonim kayıtlar [nominal türleridir.](https://en.wikipedia.org/wiki/Nominal_type_system)</span><span class="sxs-lookup"><span data-stu-id="bf568-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="bf568-138">Bunlar en iyi adlandırılmış [kayıt](records.md) türleri olarak düşünülür (aynı zamanda nominal olan) bir ön bildirim gerektirmeyen.</span><span class="sxs-lookup"><span data-stu-id="bf568-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="bf568-139">İki anonim kayıt bildirimiyle aşağıdaki örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="bf568-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="bf568-140">`x` Ve `y` değerleri farklı türleri vardır ve birbirleriyle uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf568-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="bf568-141">Onlar ekvatora uygun değildir ve karşılaştırılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="bf568-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="bf568-142">Bunu göstermek için, adlandırılmış bir kayıt eşdeğeri düşünün:</span><span class="sxs-lookup"><span data-stu-id="bf568-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="bf568-143">Tür eşdeğerliği veya karşılaştırması ile ilgili olarak adlandırılmış kayıt eşdeğerleri ile karşılaştırıldığında anonim kayıtlar hakkında doğal olarak farklı bir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="bf568-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="bf568-144">Anonim kayıtlar yapısal eşitlik ve karşılaştırma kullanır</span><span class="sxs-lookup"><span data-stu-id="bf568-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="bf568-145">Kayıt türleri gibi, anonim kayıtlar yapısal olarak eşit lenebilir ve karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf568-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="bf568-146">Bu, yalnızca tüm kurucu türleri kayıt türleri gibi eşitliği ve karşılaştırmayı destekliyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bf568-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="bf568-147">Eşitliği veya karşılaştırmayı desteklemek için, iki anonim kaydın aynı "şekle" sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf568-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="bf568-148">Anonim kayıtlar serileştirilebilir</span><span class="sxs-lookup"><span data-stu-id="bf568-148">Anonymous records are serializable</span></span>

<span data-ttu-id="bf568-149">Anonim kayıtları, adlandırılmış kayıtlarla olabildiğince seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf568-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="bf568-150">Burada [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/)kullanarak bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="bf568-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="bf568-151">Anonim kayıtlar, önceden serileştirilmiş/deserialized türleri niz için bir etki alanı tanımlamaya gerek kalmadan bir ağ üzerinden hafif veri göndermek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf568-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="bf568-152">Anonim kayıtlar C# anonim türleri ile birlikte çalışır</span><span class="sxs-lookup"><span data-stu-id="bf568-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="bf568-153">[C# anonim türlerinin](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)kullanılmasını gerektiren bir .NET API kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="bf568-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="bf568-154">C# anonim türleri anonim kayıtları kullanarak birlikte çalışmak için önemsizdir.</span><span class="sxs-lookup"><span data-stu-id="bf568-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="bf568-155">Aşağıdaki örnek, anonim bir tür gerektiren [bir LINQ](../../csharp/programming-guide/concepts/linq/index.md) aşırı yüklemesi çağırmak için anonim kayıtların nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="bf568-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="bf568-156">.NET'te kullanılan ve anonim bir türde geçmenin kullanılmasını gerektiren çok sayıda başka API vardır.</span><span class="sxs-lookup"><span data-stu-id="bf568-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="bf568-157">Anonim kayıtlar onlarla çalışmak için aracınızdır.</span><span class="sxs-lookup"><span data-stu-id="bf568-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="bf568-158">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="bf568-158">Limitations</span></span>

<span data-ttu-id="bf568-159">Anonim kayıtların kullanımında bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="bf568-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="bf568-160">Bazıları tasarımlarının doğasında vardır, ancak diğerleri değişmeye elverişlidir.</span><span class="sxs-lookup"><span data-stu-id="bf568-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="bf568-161">Desen eşleştirmesi ile sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="bf568-161">Limitations with pattern matching</span></span>

<span data-ttu-id="bf568-162">Adlandırılmış kayıtların aksine, adlandırılmış kayıtlar desen eşleştirmeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bf568-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="bf568-163">Üç nedeni vardır:</span><span class="sxs-lookup"><span data-stu-id="bf568-163">There are three reasons:</span></span>

1. <span data-ttu-id="bf568-164">Adlandırılmış kayıt türlerinin aksine, bir desen anonim bir kaydın her alanını hesaba katmak zorunda kalırdı.</span><span class="sxs-lookup"><span data-stu-id="bf568-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="bf568-165">Bunun nedeni, anonim kayıtların yapısal alt yazımı desteklememesidir – bunlar nominal türlerdir.</span><span class="sxs-lookup"><span data-stu-id="bf568-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="bf568-166">(1) nedeniyle, her farklı desen farklı bir anonim kayıt türü anlamına geleceğini gibi, bir desen eşleştirme ifadesinde ek desenler olması için hiçbir yeteneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="bf568-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="bf568-167">(3) nedeniyle, herhangi bir anonim kayıt deseni "nokta" gösterimi kullanımından daha ayrıntılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf568-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="bf568-168">[Sınırlı bağlamlarda desen eşleştirmesine izin](https://github.com/fsharp/fslang-suggestions/issues/713)vermek için açık dil önerisi vardır.</span><span class="sxs-lookup"><span data-stu-id="bf568-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="bf568-169">Susturulabilirlik ile sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="bf568-169">Limitations with mutability</span></span>

<span data-ttu-id="bf568-170">Şu anda verilerle `mutable` anonim bir kayıt tanımlamak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="bf568-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="bf568-171">Mutable verilere izin vermek için [açık dil önerisi](https://github.com/fsharp/fslang-suggestions/issues/732) vardır.</span><span class="sxs-lookup"><span data-stu-id="bf568-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="bf568-172">Yapı anonim kayıtları ile sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="bf568-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="bf568-173">Struct anonim kayıtlarının "veya `IsByRefLike` `IsReadOnly`. " olarak bildirin mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="bf568-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="bf568-174">Ve `IsByRefLike` `IsReadOnly` anonim kayıtlar için açık bir dil [önerisi](https://github.com/fsharp/fslang-suggestions/issues/712) vardır.</span><span class="sxs-lookup"><span data-stu-id="bf568-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
