---
title: Anonim Kayıtlar
description: Oluşturma ve veri işlemeye yardımcı olacak bir dil özelliği olan anonim kayıtları nasıl kullanacağınızı öğrenin.
ms.date: 06/12/2019
ms.openlocfilehash: 0a7a819cc471c6579feacd621ed15aa89a6423ba
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569465"
---
# <a name="anonymous-records"></a><span data-ttu-id="2af5a-103">Anonim Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="2af5a-103">Anonymous Records</span></span>

<span data-ttu-id="2af5a-104">Anonim kayıtlar, kullanılmadan önce bildirilmesini gerektirmeyen adlandırılmış değerlerin basit toplamalarda bulunur.</span><span class="sxs-lookup"><span data-stu-id="2af5a-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="2af5a-105">Bunları yapılar veya başvuru türleri olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2af5a-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="2af5a-106">Bunlar varsayılan olarak başvuru türlerdir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="2af5a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2af5a-107">Syntax</span></span>

<span data-ttu-id="2af5a-108">Aşağıdaki örneklerde anonim kayıt sözdizimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="2af5a-109">`[item]` olarak sınırlandırılmış öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2af5a-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="2af5a-110">Temel kullanım</span><span class="sxs-lookup"><span data-stu-id="2af5a-110">Basic usage</span></span>

<span data-ttu-id="2af5a-111">Anonim kayıtlar, örnek oluşturmadan önce bildirilmesini F# gerektirmeyen kayıt türleri olarak en iyi şekilde düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="2af5a-112">Örneğin, burada anonim bir kayıt üreten bir işlevle etkileşim kurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2af5a-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="2af5a-113">Aşağıdaki örnek, giriş olarak anonim bir kaydı alan `printCircleStats` bir işlevle önceki bir üzerinde genişletilir:</span><span class="sxs-lookup"><span data-stu-id="2af5a-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="2af5a-114">Giriş türü derlenemeyeceği için aynı "şekle" sahip olmayan herhangi bir anonim kayıt türüyle `printCircleStats` çağrısı başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="2af5a-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="2af5a-115">Yapı anonim kayıtları</span><span class="sxs-lookup"><span data-stu-id="2af5a-115">Struct anonymous records</span></span>

<span data-ttu-id="2af5a-116">Anonim kayıtlar, isteğe bağlı `struct` anahtar sözcüğüyle yapı olarak da tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="2af5a-117">Aşağıdaki örnek, bir struct anonim kaydı üreterek ve tüketerek bir öncekini genişlettiğini azaltır:</span><span class="sxs-lookup"><span data-stu-id="2af5a-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="2af5a-118">Struclük çıkarımı</span><span class="sxs-lookup"><span data-stu-id="2af5a-118">Structness inference</span></span>

<span data-ttu-id="2af5a-119">Yapı anonim kayıtları, çağrı sitesinde `struct` anahtar sözcüğünü belirtmeniz gerekmeyen "yapı zaman çıkarımı" için de izin verir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="2af5a-120">Bu örnekte, `printCircleStats`çağrılırken `struct` anahtar sözcüğünü devre dışı olursunuz:</span><span class="sxs-lookup"><span data-stu-id="2af5a-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="2af5a-121">Ters desenler-giriş türü bir struct anonim kayıt olmadığında `struct` belirtmek için derleme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="2af5a-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="2af5a-122">Anonim kayıtları diğer türler içine ekleme</span><span class="sxs-lookup"><span data-stu-id="2af5a-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="2af5a-123">Durumları kayıtları olan [ayrılmış birleşimler](discriminated-unions.md) bildirmek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="2af5a-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="2af5a-124">Ancak Kayıtlardaki veriler ayrılmış birleşimle aynı türde ise, tüm türleri birbirini dışlayan özyinelemeli olarak tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="2af5a-125">Anonim kayıtları kullanmak bu kısıtlamayı önler.</span><span class="sxs-lookup"><span data-stu-id="2af5a-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="2af5a-126">Aşağıdaki örnek bir tür ve bir düzenin onunla eşleşen işlevdir:</span><span class="sxs-lookup"><span data-stu-id="2af5a-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="2af5a-127">İfadeleri Kopyala ve Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="2af5a-127">Copy and update expressions</span></span>

<span data-ttu-id="2af5a-128">Anonim kayıtlar [kopyalama ve güncelleştirme ifadeleri](copy-and-update-record-expressions.md)ile oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="2af5a-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="2af5a-129">Örneğin, var olan bir kaynağın verilerini kopyalayan bir anonim kaydın yeni bir örneğini nasıl oluşturabileceğiniz aşağıda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="2af5a-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="2af5a-130">Ancak, adlandırılmış kayıtlardan farklı olarak, anonim kayıtlar kopyalama ve güncelleştirme ifadelerine tamamen farklı formlar oluşturmanız için izin verir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="2af5a-131">Aşağıdaki örnek, önceki örnekteki aynı anonim kaydı alır ve yeni bir anonim kayda genişletir:</span><span class="sxs-lookup"><span data-stu-id="2af5a-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="2af5a-132">Adlandırılmış kayıt örneklerinden anonim kayıtlar oluşturmak da mümkündür:</span><span class="sxs-lookup"><span data-stu-id="2af5a-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="2af5a-133">Ayrıca, başvuruya ve yapı anonim kayıtlarına veri kopyalayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2af5a-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="2af5a-134">Anonim kayıtların özellikleri</span><span class="sxs-lookup"><span data-stu-id="2af5a-134">Properties of anonymous records</span></span>

<span data-ttu-id="2af5a-135">Anonim kayıtlar, nasıl kullanılabilecekleri hakkında tam olarak anlamak için gereken birçok özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="2af5a-136">Anonim kayıtlar kabul edilir</span><span class="sxs-lookup"><span data-stu-id="2af5a-136">Anonymous records are nominal</span></span>

<span data-ttu-id="2af5a-137">Anonim kayıtlar [nominal türlerdir](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="2af5a-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="2af5a-138">Bunlar, önde gelen bildirim gerektirmeyen adlandırılmış [kayıt](records.md) türleri (de kabul edilir) olarak en iyi şekilde düşünüldüler.</span><span class="sxs-lookup"><span data-stu-id="2af5a-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="2af5a-139">İki anonim kayıt bildirimi ile aşağıdaki örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="2af5a-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="2af5a-140">`x` ve `y` değerleri farklı türlere sahiptir ve birbiriyle uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="2af5a-141">Bunlar equatable değildir ve karşılaştırılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="2af5a-142">Bunu göstermek için adlandırılmış bir kayıt eşdeğerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="2af5a-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="2af5a-143">Tür Denkliği veya karşılaştırmayla ilgili olarak adlandırılmış kayıt eşdeğerleri ile karşılaştırıldığında anonim kayıtlar hakkında doğal olarak farklı bir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="2af5a-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="2af5a-144">Anonim kayıtlar yapısal eşitlik ve karşılaştırma kullanır</span><span class="sxs-lookup"><span data-stu-id="2af5a-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="2af5a-145">Kayıt türleri gibi anonim kayıtlar yapısal equatable ve karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="2af5a-146">Bu yalnızca, tüm bileşen türleri eşitlik ve karşılaştırmayı destekliyorsa, örneğin, kayıt türleriyle geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="2af5a-147">Eşitlik veya karşılaştırmayı desteklemek için, iki anonim kayıt aynı "şekle" sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2af5a-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="2af5a-148">Anonim kayıtlar seri hale getirilebilir</span><span class="sxs-lookup"><span data-stu-id="2af5a-148">Anonymous records are serializable</span></span>

<span data-ttu-id="2af5a-149">Anonim kayıtları, adlandırılmış kayıtlarla yaptığınız gibi seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2af5a-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="2af5a-150">[Newtonsoft. JSON](https://www.nuget.org/packages/Newtonsoft.Json/)kullanarak bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2af5a-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="2af5a-151">Anonim kayıtlar, serileştirilmiş/seri durumdan çıkarılan türler için bir etki alanı tanımlamaya gerek olmadan bir ağ üzerinden hafif veri göndermek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2af5a-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="2af5a-152">Anonim türlerle birlikte C# çalışan anonim kayıtlar</span><span class="sxs-lookup"><span data-stu-id="2af5a-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="2af5a-153">Anonim türlerin kullanılması gereken bir .NET API 'si kullanmak mümkündür. [ C# ](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="2af5a-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="2af5a-154">C#anonim türler, anonim kayıtlar kullanılarak ile birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="2af5a-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="2af5a-155">Aşağıdaki örnek, anonim kayıtların adsız bir tür gerektiren bir [LINQ](../../csharp/programming-guide/concepts/linq/index.md) aşırı yüklemesini çağırmak için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="2af5a-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="2af5a-156">.NET genelinde bir anonim türde geçirme kullanılması gereken çok sayıda diğer API 'Ler vardır.</span><span class="sxs-lookup"><span data-stu-id="2af5a-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="2af5a-157">Anonim kayıtlar, bu kişilerle çalışmaya yönelik aracımız.</span><span class="sxs-lookup"><span data-stu-id="2af5a-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="2af5a-158">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="2af5a-158">Limitations</span></span>

<span data-ttu-id="2af5a-159">Anonim kayıtlar, kullanımlarında bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="2af5a-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="2af5a-160">Bazıları tasarımına göre değişir, ancak başkaları değiştirebilecektir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="2af5a-161">Model eşleştirme sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="2af5a-161">Limitations with pattern matching</span></span>

<span data-ttu-id="2af5a-162">Anonim kayıtlar, adlandırılmış kayıtlardan farklı olarak, model eşleştirmeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2af5a-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="2af5a-163">Üç neden vardır:</span><span class="sxs-lookup"><span data-stu-id="2af5a-163">There are three reasons:</span></span>

1. <span data-ttu-id="2af5a-164">Adlandırılmış kayıt türlerinden farklı olarak, bir düzenin adsız kaydın her alanı için bir hesaba sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="2af5a-165">Bunun nedeni, anonim kayıtların yapısal alt yazmayı desteklememe yöntemidir. Bunlar, nominal türlerdir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="2af5a-166">(1) nedeniyle, her farklı düzen farklı bir anonim kayıt türünü aşacağından, desen eşleştirme ifadesinde ek desenler olamaz.</span><span class="sxs-lookup"><span data-stu-id="2af5a-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="2af5a-167">(3) nedeniyle, herhangi bir anonim kayıt deseninin "nokta" gösterimi kullanmaktan daha ayrıntılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="2af5a-168">[Sınırlı bağlamlarda model eşleştirmeye izin veren](https://github.com/fsharp/fslang-suggestions/issues/713)açık bir dil önerisi vardır.</span><span class="sxs-lookup"><span data-stu-id="2af5a-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="2af5a-169">Değiştirici ile sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="2af5a-169">Limitations with mutability</span></span>

<span data-ttu-id="2af5a-170">`mutable` verileri olan anonim bir kayıt tanımlamak Şu anda mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="2af5a-171">Değişebilir verilere izin veren [açık bir dil önerisi](https://github.com/fsharp/fslang-suggestions/issues/732) vardır.</span><span class="sxs-lookup"><span data-stu-id="2af5a-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="2af5a-172">Struct anonim kayıtlarıyla sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="2af5a-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="2af5a-173">Yapı anonim kayıtlarını `IsByRefLike` veya `IsReadOnly`olarak bildirmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="2af5a-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="2af5a-174">`IsByRefLike` ve anonim kayıtları `IsReadOnly` için [açık bir dil önerisi](https://github.com/fsharp/fslang-suggestions/issues/712) vardır.</span><span class="sxs-lookup"><span data-stu-id="2af5a-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
