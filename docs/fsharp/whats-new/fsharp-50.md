---
title: 'F # 5,0-F # kılavuzundaki yenilikler'
description: "F # 5,0 ' de bulunan yeni özelliklere genel bakış alın."
ms.date: 11/06/2020
ms.openlocfilehash: 9b138e4801a3e599db650990acd53c0f956b78b8
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190734"
---
# <a name="whats-new-in-f-50"></a><span data-ttu-id="38596-103">F # 5,0 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="38596-103">What's new in F# 5.0</span></span>

<span data-ttu-id="38596-104">F # 5,0, F # diline ve F# Etkileşimli çeşitli iyileştirmeler ekler.</span><span class="sxs-lookup"><span data-stu-id="38596-104">F# 5.0 adds several improvements to the F# language and F# Interactive.</span></span> <span data-ttu-id="38596-105">**.NET 5** ile kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="38596-105">It is released with **.NET 5**.</span></span>

<span data-ttu-id="38596-106">[.Net İndirmeleri sayfasından](https://dotnet.microsoft.com/download)en son .NET SDK 'sını indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38596-106">You can download the latest .NET SDK from the [.NET downloads page](https://dotnet.microsoft.com/download).</span></span>

## <a name="get-started"></a><span data-ttu-id="38596-107">başlarken</span><span class="sxs-lookup"><span data-stu-id="38596-107">Get started</span></span>

<span data-ttu-id="38596-108">F # 5,0 tüm .NET Core dağıtımları ve Visual Studio Araçları 'nda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="38596-108">F# 5.0 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="38596-109">Daha fazla bilgi için bkz. [F # ile çalışmaya başlama](../get-started/index.md) daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="38596-109">For more information, see [Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="package-references-in-f-scripts"></a><span data-ttu-id="38596-110">F # betiklerine paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="38596-110">Package references in F# scripts</span></span>

<span data-ttu-id="38596-111">F # 5, F # betiklerinin sözdizimi ile paket başvuruları için destek sunar `#r "nuget:..."` .</span><span class="sxs-lookup"><span data-stu-id="38596-111">F# 5 brings support for package references in F# scripts with `#r "nuget:..."` syntax.</span></span> <span data-ttu-id="38596-112">Örneğin, aşağıdaki paket başvurusunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="38596-112">For example, consider the following package reference:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn $"{JsonConvert.SerializeObject o}"
```

<span data-ttu-id="38596-113">Ayrıca, paketin adından sonra aşağıdaki gibi bir açık sürüm sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="38596-113">You can also supply an explicit version after the name of the package like this:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

<span data-ttu-id="38596-114">Paket, ML.NET gibi yerel bağımlılıklarla destek paketlerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="38596-114">Package references support packages with native dependencies, such as ML.NET.</span></span>

<span data-ttu-id="38596-115">Paket başvuruları, bağımlı s 'ye başvurma konusunda özel gereksinimlere sahip paketleri de destekler `.dll` .</span><span class="sxs-lookup"><span data-stu-id="38596-115">Package references also support packages with special requirements about referencing dependent `.dll`s.</span></span> <span data-ttu-id="38596-116">Örneğin, kullanıcıların [](https://www.nuget.org/packages/FParsec/) `FParsecCS.dll` `FParsec.dll` F# Etkileşimli ' de başvurulmadan önce kendisine bağımlı olarak başvurulduğunu El Ile garantilemek Için kullanılan fparsec paketi.</span><span class="sxs-lookup"><span data-stu-id="38596-116">For example, the [FParsec](https://www.nuget.org/packages/FParsec/) package used to require that users manually ensure that its dependent `FParsecCS.dll` was referenced first before `FParsec.dll` was referenced in F# Interactive.</span></span> <span data-ttu-id="38596-117">Artık gerekli değildir ve pakete aşağıdaki gibi başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="38596-117">This is no longer needed, and you can reference the package as follows:</span></span>

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn $"Success: {result}"
    | Failure(errorMsg, _, _) -> printfn $"Failure: {errorMsg}"

test pfloat "1.234"
```

<span data-ttu-id="38596-118">Bu özellik [F # Tooling RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-118">This feature implements [F# Tooling RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md).</span></span> <span data-ttu-id="38596-119">Paket başvuruları hakkında daha fazla bilgi için [F# Etkileşimli](../tools/fsharp-interactive/index.md) öğreticisine bakın.</span><span class="sxs-lookup"><span data-stu-id="38596-119">For more information on package references, see the [F# Interactive](../tools/fsharp-interactive/index.md) tutorial.</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="38596-120">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="38596-120">String interpolation</span></span>

<span data-ttu-id="38596-121">F # enterpolasyonlu dizeler, C# veya JavaScript 'te enterpolasyonlu dizeler için oldukça benzerdir. böylece, bir dize sabit değeri içinde "delikler" içinde kod yazmanızı sağlar</span><span class="sxs-lookup"><span data-stu-id="38596-121">F# interpolated strings are fairly similar to C# or JavaScript interpolated strings, in that they let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="38596-122">Basit bir örnek verelim:</span><span class="sxs-lookup"><span data-stu-id="38596-122">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="38596-123">Ancak, F # enterpolasyonlu dizeler aynı zamanda işlev gibi tür atanmış ara için de, `sprintf` enterpolasyonlu bağlam içindeki bir ifadenin belirli bir türe uygun olmasını zorunlu kılmak için de izin verir.</span><span class="sxs-lookup"><span data-stu-id="38596-123">However, F# interpolated strings also allow for typed interpolations, just like the `sprintf` function, to enforce that an expression inside of an interpolated context conforms to a particular type.</span></span> <span data-ttu-id="38596-124">Aynı biçim belirticilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="38596-124">It uses the same format specifiers.</span></span>

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="38596-125">Önceki tür enterpolasyon örneğinde,, ilişkilendirme 'nin `%s` türü olmasını gerektirir `string` , ancak `%d` ilişkilendirme bir olmalıdır `integer` .</span><span class="sxs-lookup"><span data-stu-id="38596-125">In the preceding typed interpolation example, the `%s` requires the interpolation to be of type `string`, whereas the `%d` requires the interpolation to be an `integer`.</span></span>

<span data-ttu-id="38596-126">Ayrıca, herhangi bir rastgele F # ifadesi (veya ifadeleri) enterpolasyon bağlamının yanına yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="38596-126">Additionally, any arbitrary F# expression (or expressions) can be placed in side of an interpolation context.</span></span> <span data-ttu-id="38596-127">Daha karmaşık bir ifade yazmak da olasıdır, örneğin:</span><span class="sxs-lookup"><span data-stu-id="38596-127">It is even possible to write a more complicated expression, like so:</span></span>

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

<span data-ttu-id="38596-128">Bu, uygulamada çok fazla yapmanız önerilmez.</span><span class="sxs-lookup"><span data-stu-id="38596-128">Although we don't recommend doing this too much in practice.</span></span>

<span data-ttu-id="38596-129">Bu özellik [F # RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-129">This feature implements [F# RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md).</span></span>

## <a name="support-for-nameof"></a><span data-ttu-id="38596-130">NameOf desteği</span><span class="sxs-lookup"><span data-stu-id="38596-130">Support for nameof</span></span>

<span data-ttu-id="38596-131">F # 5, `nameof` için kullanılmakta olan sembolü çözümleyen ve f # kaynağında adını üreten işleci destekler.</span><span class="sxs-lookup"><span data-stu-id="38596-131">F# 5 supports the `nameof` operator, which resolves the symbol it's being used for and produces its name in F# source.</span></span> <span data-ttu-id="38596-132">Bu, günlüğe kaydetme gibi çeşitli senaryolarda faydalıdır ve günlüğe kaydetme işleminin kaynak kodundaki değişikliklere karşı korunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="38596-132">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

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

printfn $"{lookupMonth 12}"
printfn $"{lookupMonth 1}"
printfn $"{lookupMonth 13}"
```

<span data-ttu-id="38596-133">Son satır bir özel durum oluşturur ve hata iletisinde "month" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="38596-133">The last line will throw an exception and "month" will be shown in the error message.</span></span>

<span data-ttu-id="38596-134">Neredeyse her F # yapısının adını alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="38596-134">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn $"{M.f 12}"
printfn $"{nameof M}"
printfn $"{nameof M.f}"
```

<span data-ttu-id="38596-135">Üç son ekleme, operatörlerin nasıl çalıştığı ile ilgili değişiklikler: `nameof<'type-parameter>` genel tür parametreleri için form ekleme ve `nameof` bir model eşleştirme ifadesinde bir model olarak kullanma özelliği.</span><span class="sxs-lookup"><span data-stu-id="38596-135">Three final additions are changes to how operators work: the addition of the `nameof<'type-parameter>` form for generic type parameters, and the ability to use `nameof` as a pattern in a pattern match expression.</span></span>

<span data-ttu-id="38596-136">Bir işlecin adının alınması, kaynak dizesini verir.</span><span class="sxs-lookup"><span data-stu-id="38596-136">Taking a name of an operator gives its source string.</span></span> <span data-ttu-id="38596-137">Derlenmiş forma ihtiyacınız varsa, bir işlecin derlenmiş adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="38596-137">If you need the compiled form, use the compiled name of an operator:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

<span data-ttu-id="38596-138">Bir tür parametresinin adının alınması biraz farklı bir sözdizimi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="38596-138">Taking the name of a type parameter requires a slightly different syntax:</span></span>

```fsharp
type C<'TType> =
    member _.TypeName = nameof<'TType>
```

<span data-ttu-id="38596-139">Bu `typeof<'T>` ve `typedefof<'T>` işleçlerine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="38596-139">This is similar to the `typeof<'T>` and `typedefof<'T>` operators.</span></span>

<span data-ttu-id="38596-140">F # 5, ifadelerde kullanılabilecek bir model için de destek ekler `nameof` `match` :</span><span class="sxs-lookup"><span data-stu-id="38596-140">F# 5 also adds support for a `nameof` pattern that can be used in `match` expressions:</span></span>

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

<span data-ttu-id="38596-141">Önceki kod, Match ifadesinde dize sabit değeri yerine ' NameOf ' kullanır.</span><span class="sxs-lookup"><span data-stu-id="38596-141">The preceding code uses 'nameof' instead of the string literal in the match expression.</span></span>

<span data-ttu-id="38596-142">Bu özellik [F # RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-142">This feature implements [F# RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md).</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="38596-143">Açık tür bildirimleri</span><span class="sxs-lookup"><span data-stu-id="38596-143">Open type declarations</span></span>

<span data-ttu-id="38596-144">F # 5, açık tür bildirimleri için de destek ekler.</span><span class="sxs-lookup"><span data-stu-id="38596-144">F# 5 also adds support for open type declarations.</span></span> <span data-ttu-id="38596-145">Açık tür bildirimi, bazı farklı söz dizimi ve F # semantiğini sığdırmak için biraz farklı davranış dışında C# dilinde statik bir sınıf açma gibidir.</span><span class="sxs-lookup"><span data-stu-id="38596-145">An open type declaration is like opening a static class in C#, except with some different syntax and some slightly different behavior to fit F# semantics.</span></span>

<span data-ttu-id="38596-146">Açık tür bildirimleri sayesinde, `open` içindeki statik içerikleri açığa çıkarmak için herhangi bir tür yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38596-146">With open type declarations, you can `open` any type to expose static contents inside of it.</span></span> <span data-ttu-id="38596-147">Ayrıca, `open` içeriğini açığa çıkarmak için F # tanımlı birleşimler ve kayıtlar da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38596-147">Additionally, you can `open` F#-defined unions and records to expose their contents.</span></span> <span data-ttu-id="38596-148">Örneğin, bir modülde tanımlanmış bir birleşiminize sahipseniz ve durumlarına erişmek istiyorsanız ancak modülün tamamını açmak istemiyorsanız bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="38596-148">For example, this can be useful if you have a union defined in a module and want to access its cases, but don't want to open the entire module.</span></span>

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn $"{A}"
```

<span data-ttu-id="38596-149">C# ' den farklı olarak, `open type` aynı ada sahip bir üyeyi kullanıma sunan iki tür üzerinde olduğunuzda, `open` diğer adı gölgeli son türden üye.</span><span class="sxs-lookup"><span data-stu-id="38596-149">Unlike C#, when you `open type` on two types that expose a member with the same name, the member from the last type being `open`ed shadows the other name.</span></span> <span data-ttu-id="38596-150">Bu, zaten mevcut olan gölgeleme etrafında F # semantiğinin tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="38596-150">This is consistent with F# semantics around shadowing that exist already.</span></span>

<span data-ttu-id="38596-151">Bu özellik [F # RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-151">This feature implements [F# RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md).</span></span>

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a><span data-ttu-id="38596-152">Yerleşik veri türleri için tutarlı Dilimleme davranışı</span><span class="sxs-lookup"><span data-stu-id="38596-152">Consistent slicing behavior for built-in data types</span></span>

<span data-ttu-id="38596-153">`FSharp.Core`F # 5 ' ten önce tutarlı olmaması için kullanılan yerleşik veri türlerini (dizi, liste, dize, 2B dizi, 3B dizi, 4d dizi) Dilimleme davranışı.</span><span class="sxs-lookup"><span data-stu-id="38596-153">Behavior for slicing the built-in `FSharp.Core` data types (array, list, string, 2D array, 3D array, 4D array) used to not be consistent prior to F# 5.</span></span> <span data-ttu-id="38596-154">Bazı kenar durumu davranışları özel durum oluşturdu ve bazı durumlar.</span><span class="sxs-lookup"><span data-stu-id="38596-154">Some edge-case behavior threw an exception and some wouldn't.</span></span> <span data-ttu-id="38596-155">F # 5 ' te, tüm yerleşik türler artık oluşturulması imkansız olan dilimler için boş dilimler döndürüyor:</span><span class="sxs-lookup"><span data-stu-id="38596-155">In F# 5, all built-in types now return empty slices for slices that are impossible to generate:</span></span>

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

<span data-ttu-id="38596-156">Bu özellik [F # RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-156">This feature implements [F# RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md).</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a><span data-ttu-id="38596-157">FSharp. Core 'da 3B ve 4D dizileri için sabit Dizin dilimleri</span><span class="sxs-lookup"><span data-stu-id="38596-157">Fixed-index slices for 3D and 4D arrays in FSharp.Core</span></span>

<span data-ttu-id="38596-158">F # 5,0, yerleşik 3B ve 4D dizi türlerinde sabit bir dizinle Dilimleme desteği sunar.</span><span class="sxs-lookup"><span data-stu-id="38596-158">F# 5.0 brings support for slicing with a fixed index in the built-in 3D and 4D array types.</span></span>

<span data-ttu-id="38596-159">Bunu göstermek için aşağıdaki 3B diziyi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="38596-159">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="38596-160">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="38596-160">*z = 0*</span></span>
| <span data-ttu-id="38596-161">x\y</span><span class="sxs-lookup"><span data-stu-id="38596-161">x\y</span></span>   | <span data-ttu-id="38596-162">0</span><span class="sxs-lookup"><span data-stu-id="38596-162">0</span></span> | <span data-ttu-id="38596-163">1</span><span class="sxs-lookup"><span data-stu-id="38596-163">1</span></span> |
|-------|---|---|
| <span data-ttu-id="38596-164">**0**</span><span class="sxs-lookup"><span data-stu-id="38596-164">**0**</span></span> | <span data-ttu-id="38596-165">0</span><span class="sxs-lookup"><span data-stu-id="38596-165">0</span></span> | <span data-ttu-id="38596-166">1</span><span class="sxs-lookup"><span data-stu-id="38596-166">1</span></span> |
| <span data-ttu-id="38596-167">**1**</span><span class="sxs-lookup"><span data-stu-id="38596-167">**1**</span></span> | <span data-ttu-id="38596-168">2</span><span class="sxs-lookup"><span data-stu-id="38596-168">2</span></span> | <span data-ttu-id="38596-169">3</span><span class="sxs-lookup"><span data-stu-id="38596-169">3</span></span> |

<span data-ttu-id="38596-170">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="38596-170">*z = 1*</span></span>
| <span data-ttu-id="38596-171">x\y</span><span class="sxs-lookup"><span data-stu-id="38596-171">x\y</span></span>   | <span data-ttu-id="38596-172">0</span><span class="sxs-lookup"><span data-stu-id="38596-172">0</span></span> | <span data-ttu-id="38596-173">1</span><span class="sxs-lookup"><span data-stu-id="38596-173">1</span></span> |
|-------|---|---|
| <span data-ttu-id="38596-174">**0**</span><span class="sxs-lookup"><span data-stu-id="38596-174">**0**</span></span> | <span data-ttu-id="38596-175">4</span><span class="sxs-lookup"><span data-stu-id="38596-175">4</span></span> | <span data-ttu-id="38596-176">5</span><span class="sxs-lookup"><span data-stu-id="38596-176">5</span></span> |
| <span data-ttu-id="38596-177">**1**</span><span class="sxs-lookup"><span data-stu-id="38596-177">**1**</span></span> | <span data-ttu-id="38596-178">6</span><span class="sxs-lookup"><span data-stu-id="38596-178">6</span></span> | <span data-ttu-id="38596-179">7</span><span class="sxs-lookup"><span data-stu-id="38596-179">7</span></span> |

<span data-ttu-id="38596-180">Dilimi diziden ayıklamak istediğinizde ne olacak `[| 4; 5 |]` ?</span><span class="sxs-lookup"><span data-stu-id="38596-180">What if you wanted to extract the slice `[| 4; 5 |]` from the array?</span></span> <span data-ttu-id="38596-181">Bu artık çok basittir!</span><span class="sxs-lookup"><span data-stu-id="38596-181">This is now very simple!</span></span>

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

<span data-ttu-id="38596-182">Bu özellik [F # RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md)'yi uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-182">This feature implements [F# RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md).</span></span>

## <a name="f-quotations-improvements"></a><span data-ttu-id="38596-183">F # tırnak geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="38596-183">F# quotations improvements</span></span>

<span data-ttu-id="38596-184">F # [kod teklifleri](../language-reference/code-quotations.md) artık tür kısıtlaması bilgilerini tutma özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="38596-184">F# [code quotations](../language-reference/code-quotations.md) now have the ability to retain type constraint information.</span></span> <span data-ttu-id="38596-185">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="38596-185">Consider the following example:</span></span>

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

<span data-ttu-id="38596-186">İşlev tarafından oluşturulan kısıtlama, `inline` kod teklifinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="38596-186">The constraint generated by the `inline` function is retained in the code quotation.</span></span> <span data-ttu-id="38596-187">`negate`İşlevin alıntı yapılabilir formu artık değerlendirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="38596-187">The `negate` function's quotated form can now be evaluated.</span></span>

<span data-ttu-id="38596-188">Bu özellik [F # RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-188">This feature implements [F# RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md).</span></span>

## <a name="applicative-computation-expressions"></a><span data-ttu-id="38596-189">Uygulama hesaplama Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="38596-189">Applicative Computation Expressions</span></span>

<span data-ttu-id="38596-190">[Hesaplama ifadeleri (CEs)](../language-reference/computation-expressions.md) , bugün "bağlamsal hesaplamalar" modellemek için veya daha işlevsel programlama kullanımı kolay terminoloji, monanabilir hesaplamalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38596-190">[Computation expressions (CEs)](../language-reference/computation-expressions.md) are used today to model "contextual computations", or in more functional programming-friendly terminology, monadic computations.</span></span>

<span data-ttu-id="38596-191">F # 5, farklı bir hesaplama modeli sunan uygulama ve uygulama sunar.</span><span class="sxs-lookup"><span data-stu-id="38596-191">F# 5 introduces applicative CEs, which offer a different computational model.</span></span> <span data-ttu-id="38596-192">Uygulama, her hesaplamanın bağımsız olduğu ve sonuçları sonunda biriktiği için daha verimli hesaplamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="38596-192">Applicative CEs allow for more efficient computations provided that every computation is independent, and their results are accumulated at the end.</span></span> <span data-ttu-id="38596-193">Hesaplamalar diğerinden bağımsız olduğunda, Ayrıca, CE yazarlarının daha verimli kitaplıklar yazmasına olanak tanımak de oldukça paralelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="38596-193">When computations are independent of one another, they are also trivially parallelizable, allowing CE authors to write more efficient libraries.</span></span> <span data-ttu-id="38596-194">Bu avantaj bir kısıtlamada gelir, ancak önceden hesaplanan değerlere bağımlı olan hesaplamalar buna izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="38596-194">This benefit comes at a restriction, though: computations that depend on previously computed values are not allowed.</span></span>

<span data-ttu-id="38596-195">Aşağıdaki örnek, türü için temel bir uygulama gösterir `Result` .</span><span class="sxs-lookup"><span data-stu-id="38596-195">The follow example shows a basic applicative CE for the `Result` type.</span></span>

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
    | Ok x -> printfn $"{nameof res1} is: %d{x}"
    | Error e -> printfn $"{nameof res1} is: {e}"

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

<span data-ttu-id="38596-196">Günümüzde bu kitaplıkta yer alan bir kitaplık yazarımız varsa, bilmeniz gereken bazı ek hususlar vardır.</span><span class="sxs-lookup"><span data-stu-id="38596-196">If you're a library author who exposes CEs in their library today, there are some additional considerations you'll need to be aware of.</span></span>

<span data-ttu-id="38596-197">Bu özellik [F # RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-197">This feature implements [F# RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md).</span></span>

## <a name="interfaces-can-be-implemented-at-different-generic-instantiations"></a><span data-ttu-id="38596-198">Arabirimler, farklı genel örneklerde uygulanabilir</span><span class="sxs-lookup"><span data-stu-id="38596-198">Interfaces can be implemented at different generic instantiations</span></span>

<span data-ttu-id="38596-199">Artık aynı arabirimi farklı genel örneklerde de uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="38596-199">You can now implement the same interface at different generic instantiations:</span></span>

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

<span data-ttu-id="38596-200">Bu özellik [F # RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-200">This feature implements [F# RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md).</span></span>

## <a name="default-interface-member-consumption"></a><span data-ttu-id="38596-201">Varsayılan arabirim üyesi tüketimi</span><span class="sxs-lookup"><span data-stu-id="38596-201">Default interface member consumption</span></span>

<span data-ttu-id="38596-202">F # 5, [arabirimleri varsayılan uygulamalarla](../../csharp/tutorials/default-interface-methods-versions.md)kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="38596-202">F# 5 lets you consume [interfaces with default implementations](../../csharp/tutorials/default-interface-methods-versions.md).</span></span>

<span data-ttu-id="38596-203">C# ' de tanımlanan bir arabirimi şöyle düşünün:</span><span class="sxs-lookup"><span data-stu-id="38596-203">Consider an interface defined in C# like this:</span></span>

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

<span data-ttu-id="38596-204">Bunu F # içinde, bir arabirimi uygulama konusunda standart yollardan herhangi biriyle kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="38596-204">You can consume it in F# through any of the standard means of implementing an interface:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

<span data-ttu-id="38596-205">Bu, kullanıcıların varsayılan bir uygulama kullanabilmesini beklediklerinde modern C# dilinde yazılmış C# kodu ve .NET bileşenlerinden yararlanarak güvenle yararlanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="38596-205">This lets you safely take advantage of C# code and .NET components written in modern C# when they expect users to be able to consume a default implementation.</span></span>

<span data-ttu-id="38596-206">Bu özellik [F # RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-206">This feature implements [F# RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md).</span></span>

## <a name="simplified-interop-with-nullable-value-types"></a><span data-ttu-id="38596-207">Null yapılabilir değer türleriyle Basitleştirilmiş birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="38596-207">Simplified interop with nullable value types</span></span>

<span data-ttu-id="38596-208">[Null yapılabilir (değer) türleri](/dotnet/api/system.nullable-1) (tarihsel olarak null yapılabilir türler olarak adlandırılır) F # tarafından desteklenmelidir, ancak bunlarla etkileşim kurmak istediğiniz `Nullable` her seferinde bir veya sarmalayıcı oluşturmanız gerektiğinden bu, geleneksel olarak bir sorun teşkil etti `Nullable<SomeType>` .</span><span class="sxs-lookup"><span data-stu-id="38596-208">[Nullable (value) types](/dotnet/api/system.nullable-1) (called Nullable Types historically) have long been supported by F#, but interacting with them has traditionally been somewhat of a pain since you'd have to construct a `Nullable` or `Nullable<SomeType>` wrapper every time you wanted to pass a value.</span></span> <span data-ttu-id="38596-209">Artık derleyici, hedef türü eşleşiyorsa bir değer türünü bir olarak öğesine dönüştürür `Nullable<ThatValueType>` .</span><span class="sxs-lookup"><span data-stu-id="38596-209">Now the compiler will implicitly convert a value type into a `Nullable<ThatValueType>` if the target type matches.</span></span> <span data-ttu-id="38596-210">Aşağıdaki kod artık mümkündür:</span><span class="sxs-lookup"><span data-stu-id="38596-210">The following code is now possible:</span></span>

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

<span data-ttu-id="38596-211">Bu özellik [F # RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-211">This feature implements [F# RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md).</span></span>

## <a name="preview-reverse-indexes"></a><span data-ttu-id="38596-212">Önizleme: ters dizinler</span><span class="sxs-lookup"><span data-stu-id="38596-212">Preview: reverse indexes</span></span>

<span data-ttu-id="38596-213">F # 5 Ayrıca ters dizinlere izin vermek için bir önizleme sunar.</span><span class="sxs-lookup"><span data-stu-id="38596-213">F# 5 also introduces a preview for allowing reverse indexes.</span></span> <span data-ttu-id="38596-214">Söz dizimi `^idx` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="38596-214">The syntax is `^idx`.</span></span> <span data-ttu-id="38596-215">Listenin sonundan bir öğe 1 değeri aşağıdaki gibi olabilir:</span><span class="sxs-lookup"><span data-stu-id="38596-215">Here's how you can an element 1 value from the end of a list:</span></span>

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

<span data-ttu-id="38596-216">Ayrıca, kendi türleriniz için ters dizinler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38596-216">You can also define reverse indexes for your own types.</span></span> <span data-ttu-id="38596-217">Bunu yapmak için aşağıdaki yöntemi uygulamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="38596-217">To do so, you'll need to implement the following method:</span></span>

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

<span data-ttu-id="38596-218">Türü için bir örnek aşağıda verilmiştir `Span<'T>` :</span><span class="sxs-lookup"><span data-stu-id="38596-218">Here's an example for the `Span<'T>` type:</span></span>

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
    printfn $"{arr}"

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

<span data-ttu-id="38596-219">Bu özellik [F # RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-219">This feature implements [F# RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md).</span></span>

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a><span data-ttu-id="38596-220">Önizleme: hesaplama ifadelerinde özel anahtar sözcüklerin aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="38596-220">Preview: overloads of custom keywords in computation expressions</span></span>

<span data-ttu-id="38596-221">Hesaplama ifadeleri, kitaplık ve çerçeve yazarları için güçlü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="38596-221">Computation expressions are a powerful feature for library and framework authors.</span></span> <span data-ttu-id="38596-222">Bunlar, çalışmakta olduğunuz etki alanı için iyi bilinen üyeleri tanımlamanıza ve bir DSL oluşturacak şekilde bileşenlerinizi önemli ölçüde iyileştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="38596-222">They allow you to greatly improve the expressiveness of your components by letting you define well-known members and form a DSL for the domain you're working in.</span></span>

<span data-ttu-id="38596-223">F # 5 hesaplama Ifadelerinde ek yükleme özel işlemleri için Önizleme desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="38596-223">F# 5 adds preview support for overloading custom operations in Computation Expressions.</span></span> <span data-ttu-id="38596-224">Aşağıdaki kodun yazılmasına ve kullanılmasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="38596-224">It allows the following code to be written and consumed:</span></span>

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

<span data-ttu-id="38596-225">Bu değişiklikten önce, `InputBuilder` türü olduğu gibi yazabilirsiniz, ancak örnekte kullanıldığı şekilde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="38596-225">Prior to this change, you could write the `InputBuilder` type as it is, but you couldn't use it the way it's used in the example.</span></span> <span data-ttu-id="38596-226">Aşırı Yüklemeler, isteğe bağlı parametreler ve artık `System.ParamArray` türlere izin verildiğinden, her şey yalnızca istediğiniz gibi çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38596-226">Since overloads, optional parameters, and now `System.ParamArray` types are allowed, everything just works as you'd expect it to.</span></span>

<span data-ttu-id="38596-227">Bu özellik [F # RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md)' i uygular.</span><span class="sxs-lookup"><span data-stu-id="38596-227">This feature implements [F# RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md).</span></span>
