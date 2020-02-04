---
title: ByRef’ler
description: İçindeki F#ByRef ve ByRef benzeri türler hakkında bilgi edinin ve bu, alt düzey programlama için kullanılır.
ms.date: 11/04/2019
ms.openlocfilehash: 05a40059ad5b72829233b0c4135c76eb1cff4da5
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965821"
---
# <a name="byrefs"></a><span data-ttu-id="8282a-103">ByRef’ler</span><span class="sxs-lookup"><span data-stu-id="8282a-103">Byrefs</span></span>

<span data-ttu-id="8282a-104">F#, alt düzey programlama alanında ele alan iki önemli özellik alanına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8282a-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="8282a-105">`byref`/`inref`yönetilen işaretçiler olan /`outref` türler.</span><span class="sxs-lookup"><span data-stu-id="8282a-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="8282a-106">Çalışma zamanında geçersiz bir program derleyememesi için kullanım kısıtlamalarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8282a-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="8282a-107">Benzer semantiğini ve `byref<'T>`aynı derleme zamanı kısıtlamalarını [içeren `byref`benzeri bir yapı](structures.md) .</span><span class="sxs-lookup"><span data-stu-id="8282a-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="8282a-108">Bir örnek <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="8282a-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="8282a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8282a-109">Syntax</span></span>

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a><span data-ttu-id="8282a-110">ByRef, ınref ve outref</span><span class="sxs-lookup"><span data-stu-id="8282a-110">Byref, inref, and outref</span></span>

<span data-ttu-id="8282a-111">Üç `byref`biçimi vardır:</span><span class="sxs-lookup"><span data-stu-id="8282a-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="8282a-112">temel alınan değeri okumak için yönetilen bir işaretçi `inref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="8282a-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="8282a-113">temel alınan değere yazmak için yönetilen bir işaretçi olan `outref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="8282a-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="8282a-114">temel alınan değeri okumak ve yazmak için yönetilen bir işaretçi olan `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="8282a-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="8282a-115">Bir `inref<'T>` beklendiğinde `byref<'T>` geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8282a-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="8282a-116">Benzer şekilde, bir `outref<'T>` beklenildiği bir `byref<'T>` geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8282a-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="8282a-117">ByRef 'ler kullanma</span><span class="sxs-lookup"><span data-stu-id="8282a-117">Using byrefs</span></span>

<span data-ttu-id="8282a-118">`inref<'T>`kullanmak için, `&`bir işaretçi değeri almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8282a-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="8282a-119">`outref<'T>` veya `byref<'T>`kullanarak işaretçiye yazmak için, `mutable`işaretçiyi aldığınız değeri de yapmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8282a-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="8282a-120">Yalnızca işaretçiyi okumak yerine yazıyorsanız, `byref<'T>`yerine `outref<'T>` kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8282a-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="8282a-121">Inref semantiği</span><span class="sxs-lookup"><span data-stu-id="8282a-121">Inref semantics</span></span>

<span data-ttu-id="8282a-122">Aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="8282a-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="8282a-123">Anlam, bu, aşağıdakiler anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="8282a-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="8282a-124">`x` işaretçisinin sahibi yalnızca değeri okumak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8282a-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="8282a-125">`SomeStruct` içinde iç içe `struct` alanlara alınan herhangi bir işaretçiye `inref<_>`türü verilir.</span><span class="sxs-lookup"><span data-stu-id="8282a-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="8282a-126">Aşağıdakiler de doğrudur:</span><span class="sxs-lookup"><span data-stu-id="8282a-126">The following is also true:</span></span>

* <span data-ttu-id="8282a-127">Diğer iş parçacıklarının veya diğer adların `x`için yazma erişimine sahip olmadığı kesin değildir.</span><span class="sxs-lookup"><span data-stu-id="8282a-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="8282a-128">`SomeStruct` `inref``x` sanallaştırılan bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="8282a-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="8282a-129">Ancak, sabit F# olan değer türleri için `this` işaretçisi bir `inref`olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="8282a-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="8282a-130">Tüm bu kuralların birlikte bir `inref` işaretçisinin sahibi, işaret edilen belleğin hemen içeriğini değiştiremeyebilir.</span><span class="sxs-lookup"><span data-stu-id="8282a-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="8282a-131">Outref semantiği</span><span class="sxs-lookup"><span data-stu-id="8282a-131">Outref semantics</span></span>

<span data-ttu-id="8282a-132">`outref<'T>` amacı, işaretçinin yalnızca yazılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8282a-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="8282a-133">Beklenmedik şekilde, `outref<'T>` ada rağmen temel alınan değerin okunmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="8282a-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="8282a-134">Bu uyumluluk amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="8282a-134">This is for compatibility purposes.</span></span> <span data-ttu-id="8282a-135">Anlamsal, `outref<'T>` `byref<'T>`farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="8282a-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="8282a-136">C\# ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="8282a-136">Interop with C\#</span></span>

<span data-ttu-id="8282a-137">C#`ref` dönüşe ek olarak `in ref` ve `out ref` anahtar sözcüklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="8282a-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="8282a-138">Aşağıdaki tabloda, ne F# C# kadar yorumlama yapılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8282a-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="8282a-139">C#oluşturma</span><span class="sxs-lookup"><span data-stu-id="8282a-139">C# construct</span></span>|<span data-ttu-id="8282a-140">F#algılar</span><span class="sxs-lookup"><span data-stu-id="8282a-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="8282a-141">`ref` dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="8282a-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="8282a-142">`ref readonly` dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="8282a-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="8282a-143">`in ref` parametresi</span><span class="sxs-lookup"><span data-stu-id="8282a-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="8282a-144">`out ref` parametresi</span><span class="sxs-lookup"><span data-stu-id="8282a-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="8282a-145">Aşağıdaki tabloda neler F# olduğu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8282a-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="8282a-146">F#oluşturma</span><span class="sxs-lookup"><span data-stu-id="8282a-146">F# construct</span></span>|<span data-ttu-id="8282a-147">Yayınlanan Yapı</span><span class="sxs-lookup"><span data-stu-id="8282a-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="8282a-148">`inref<'T>` bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="8282a-148">`inref<'T>` argument</span></span>|<span data-ttu-id="8282a-149">bağımsız değişkende `[In]` özniteliği</span><span class="sxs-lookup"><span data-stu-id="8282a-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="8282a-150">`inref<'T>` dön</span><span class="sxs-lookup"><span data-stu-id="8282a-150">`inref<'T>` return</span></span>|<span data-ttu-id="8282a-151">değer üzerinde `modreq` özniteliği</span><span class="sxs-lookup"><span data-stu-id="8282a-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="8282a-152">Soyut yuva veya uygulamada `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="8282a-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="8282a-153">bağımsız değişkende veya dönüşte `modreq`</span><span class="sxs-lookup"><span data-stu-id="8282a-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="8282a-154">`outref<'T>` bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="8282a-154">`outref<'T>` argument</span></span>|<span data-ttu-id="8282a-155">bağımsız değişkende `[Out]` özniteliği</span><span class="sxs-lookup"><span data-stu-id="8282a-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="8282a-156">Tür çıkarımı ve aşırı yükleme kuralları</span><span class="sxs-lookup"><span data-stu-id="8282a-156">Type inference and overloading rules</span></span>

<span data-ttu-id="8282a-157">Aşağıdaki durumlarda F# derleyici tarafından bir `inref<'T>` türü algılanır:</span><span class="sxs-lookup"><span data-stu-id="8282a-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="8282a-158">Bir `IsReadOnly` özniteliği olan bir .NET parametresi veya dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="8282a-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="8282a-159">`this` işaretçisi, değişebilir alanları olmayan bir struct türü üzerinde.</span><span class="sxs-lookup"><span data-stu-id="8282a-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="8282a-160">Başka bir `inref<_>` işaretçisinden türetilen bir bellek konumunun adresi.</span><span class="sxs-lookup"><span data-stu-id="8282a-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="8282a-161">`inref` örtük bir adresi çekilirken, `inref<SomeType>`türünde bir bağımsız değişkenle birlikte `SomeType` türünde bağımsız değişkene sahip bir aşırı yükleme tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="8282a-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="8282a-162">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8282a-162">For example:</span></span>

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

<span data-ttu-id="8282a-163">Her iki durumda da, `inref<System.DateTime>`alan aşırı yüklemeler yerine `System.DateTime` alan aşırı yüklemeler çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="8282a-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="8282a-164">ByRef benzeri yapılar</span><span class="sxs-lookup"><span data-stu-id="8282a-164">Byref-like structs</span></span>

<span data-ttu-id="8282a-165">`byref`/`inref`/`outref` Trio 'ya ek olarak, `byref`benzer anlamlarına uygun olan kendi yapı birimlerinizi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8282a-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="8282a-166">Bu, <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliğiyle yapılır:</span><span class="sxs-lookup"><span data-stu-id="8282a-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="8282a-167">`IsByRefLike` `Struct`göstermez.</span><span class="sxs-lookup"><span data-stu-id="8282a-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="8282a-168">Her ikisi de türünde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8282a-168">Both must be present on the type.</span></span>

<span data-ttu-id="8282a-169">İçindeki F# "`byref`-LIKE" yapısı, yığın bağlantılı bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="8282a-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="8282a-170">Yönetilen yığında hiçbir şekilde ayrılmadı.</span><span class="sxs-lookup"><span data-stu-id="8282a-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="8282a-171">`byref`benzeri bir yapı, yoğun ömür ve yakalama olmayan bir dizi güçlü denetim ile zorlandığından, yüksek performanslı programlama için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8282a-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="8282a-172">Kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8282a-172">The rules are:</span></span>

* <span data-ttu-id="8282a-173">İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem geri dönüş olarak kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="8282a-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="8282a-174">Bunlar statik veya bir sınıfın ya da normal yapının örnek üyeleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="8282a-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="8282a-175">Bunlar herhangi bir kapanış yapısı (`async` Yöntemler veya lambda ifadeleri) tarafından yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="8282a-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="8282a-176">Genel parametre olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8282a-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="8282a-177">Bu son nokta, işlem hattı F# stili programlama için önemlidir. `|>`, giriş türlerini parametreleştiren genel bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="8282a-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="8282a-178">Bu kısıtlama, gelecekte `|>` için gevşek olabilir ve gövdesinde satır içi olmayan genel işlevlere hiçbir çağrı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="8282a-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="8282a-179">Bu kurallar kullanımı kesin olarak kısıtlıyor olsa da, yüksek performanslı bilgi işlem taahhüdünü güvenli bir şekilde yerine getirmek için bu işlemleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="8282a-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="8282a-180">ByRef dönüşler</span><span class="sxs-lookup"><span data-stu-id="8282a-180">Byref returns</span></span>

<span data-ttu-id="8282a-181">ByRef, F# işlevlerden veya üyelerin üretilebilir ve tüketilebilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8282a-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="8282a-182">`byref`döndüren bir yöntemi kullanırken, değer örtük olarak başvurulduğunu.</span><span class="sxs-lookup"><span data-stu-id="8282a-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="8282a-183">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8282a-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) = 
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="8282a-184">ByRef değeri döndürmek için değeri içeren değişken geçerli kapsamdan daha uzun bir süre etkin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8282a-184">To return a value byref, the variable which contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="8282a-185">Ayrıca, ByRef döndürmek için & değerini kullanın (değeri, geçerli kapsamdan daha uzun bir süre bulunan bir değişkendir).</span><span class="sxs-lookup"><span data-stu-id="8282a-185">Also, to return byref, use &value (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="8282a-186">Birden çok zincirleme çağrı yoluyla başvuru geçirme gibi örtük başvuru yapmaktan kaçınmak için `&x` (`x` değerdir) kullanın.</span><span class="sxs-lookup"><span data-stu-id="8282a-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="8282a-187">Ayrıca, bir dönüş `byref`doğrudan atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8282a-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="8282a-188">Aşağıdaki (son derece kesinlik düzeyi) programı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="8282a-188">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

<span data-ttu-id="8282a-189">Bu çıktı.</span><span class="sxs-lookup"><span data-stu-id="8282a-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="8282a-190">ByRef 'ler için kapsam</span><span class="sxs-lookup"><span data-stu-id="8282a-190">Scoping for byrefs</span></span>

<span data-ttu-id="8282a-191">`let`ilişkili bir değerin başvurusu tanımlandığı kapsamı aşamaz.</span><span class="sxs-lookup"><span data-stu-id="8282a-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="8282a-192">Örneğin, aşağıdakilere izin verilmez:</span><span class="sxs-lookup"><span data-stu-id="8282a-192">For example, the following is disallowed:</span></span>

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

<span data-ttu-id="8282a-193">Bu, iyileştirmelere göre derleme yaptığınızda veya kapadığınıza bağlı olarak farklı sonuçlar almanızı önler.</span><span class="sxs-lookup"><span data-stu-id="8282a-193">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
