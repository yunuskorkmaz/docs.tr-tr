---
title: Zkratka
description: Byref ve byref-like türleri hakkında F#, alt düzey programlama için kullanılır.
ms.date: 09/02/2018
ms.openlocfilehash: c0bad26672fbb9eb315eee1c3e275183ddeb9297
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703198"
---
# <a name="byrefs"></a><span data-ttu-id="add74-103">Zkratka</span><span class="sxs-lookup"><span data-stu-id="add74-103">Byrefs</span></span>

<span data-ttu-id="add74-104">F#düşük düzeydeki programlama alanında baş iki önemli özellik alanlarını sahiptir:</span><span class="sxs-lookup"><span data-stu-id="add74-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="add74-105">`byref` / `inref` / `outref` Yönetilen işaretçiler türlerinden.</span><span class="sxs-lookup"><span data-stu-id="add74-105">The `byref`/`inref`/`outref` types, which are a managed pointers.</span></span> <span data-ttu-id="add74-106">Böylece, çalışma zamanında geçersiz bir program derlenemez kullanım kısıtlamaları sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="add74-106">They have restrictions on usage so that you cannot compile a program that is invalid at runtime.</span></span>
* <span data-ttu-id="add74-107">A `byref`-olan yapı gibi bir [yapısı](structures.md) benzer semantiğe ve aynı derleme zamanı kısıtlamalara sahip `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="add74-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="add74-108">Bir örnek <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="add74-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="add74-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="add74-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="add74-110">ByRef ve inref outref</span><span class="sxs-lookup"><span data-stu-id="add74-110">Byref, inref, and outref</span></span>

<span data-ttu-id="add74-111">Üç tür vardır `byref`:</span><span class="sxs-lookup"><span data-stu-id="add74-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="add74-112">`inref<'T>`, temeldeki değeri okumak için yönetilen bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="add74-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="add74-113">`outref<'T>`, temel alınan değeri yazmak için yönetilen bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="add74-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="add74-114">`byref<'T>`, temeldeki değer yazma ve okuma için yönetilen bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="add74-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="add74-115">A `byref<'T>` nerede geçirilebilir bir `inref<'T>` beklenir.</span><span class="sxs-lookup"><span data-stu-id="add74-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="add74-116">Benzer şekilde, bir `byref<'T>` nerede geçirilebilir bir `outref<'T>` beklenir.</span><span class="sxs-lookup"><span data-stu-id="add74-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="add74-117">Zkratka kullanma</span><span class="sxs-lookup"><span data-stu-id="add74-117">Using byrefs</span></span>

<span data-ttu-id="add74-118">Kullanılacak bir `inref<'T>`, bir işaretçi değeri ile almanız gereken `&`:</span><span class="sxs-lookup"><span data-stu-id="add74-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    
let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="add74-119">İşaretçiyi kullanarak yazmak için bir `outref<'T>` veya `byref<'T>`, almak için bir işaretçi değeri de yapmalısınız `mutable`.</span><span class="sxs-lookup"><span data-stu-id="add74-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="add74-120">İşaretçiyi, okuma yerine yalnızca yazıyorsanız kullanmayı `outref<'T>` yerine `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="add74-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="add74-121">Inref semantiği</span><span class="sxs-lookup"><span data-stu-id="add74-121">Inref semantics</span></span>

<span data-ttu-id="add74-122">Aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="add74-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="add74-123">Anlamsal olarak, bu aşağıdaki gelir:</span><span class="sxs-lookup"><span data-stu-id="add74-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="add74-124">Sahibi `x` işaretçi yalnızca kullanabilir, değeri okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="add74-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="add74-125">Herhangi bir işaretçi için alınan `struct` iç içe alanlar içinde `SomeStruct` türü verilen `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="add74-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="add74-126">Aşağıdakileri de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="add74-126">The following is also true:</span></span>

* <span data-ttu-id="add74-127">Diğer adlar yazma erişimine sahip değil veya diğer iş parçacıkları çekilmeye yoktur `x`.</span><span class="sxs-lookup"><span data-stu-id="add74-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="add74-128">Çekilmeye yoktur, `SomeStruct` tarafından virtue, sabittir `x` olan bir `inref`.</span><span class="sxs-lookup"><span data-stu-id="add74-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="add74-129">Ancak, F# değer türleri **olan** değişmezse, `this` işaretçi olarak çıkarılan bir `inref`.</span><span class="sxs-lookup"><span data-stu-id="add74-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="add74-130">Tüm bu kuralların birlikte sahibi anlamına bir `inref` işaretçi işaret edilen bellek hemen içeriğini değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="add74-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="add74-131">Outref semantiği</span><span class="sxs-lookup"><span data-stu-id="add74-131">Outref semantics</span></span>

<span data-ttu-id="add74-132">Amacı `outref<'T>` işaretçi gelen yalnızca okunmalıdır belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="add74-132">The purpose of `outref<'T>` is to indicate that the pointer should only be read from.</span></span> <span data-ttu-id="add74-133">Beklenmedik bir şekilde, `outref<'T>` değer adını rağmen temel alınan okuma izin verir.</span><span class="sxs-lookup"><span data-stu-id="add74-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="add74-134">Bu, uyumluluk amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="add74-134">This is for compatibility purposes.</span></span> <span data-ttu-id="add74-135">Anlamsal olarak, `outref<'T>` farklı değildir `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="add74-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="add74-136">C ile birlikte çalışma\#</span><span class="sxs-lookup"><span data-stu-id="add74-136">Interop with C\#</span></span>

<span data-ttu-id="add74-137">C# destekler `in ref` ve `out ref` yanı sıra anahtar sözcükleri `ref` döndürür.</span><span class="sxs-lookup"><span data-stu-id="add74-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="add74-138">Aşağıdaki tabloda nasıl F# ne yorumlar C# gösterir:</span><span class="sxs-lookup"><span data-stu-id="add74-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="add74-139">C# yapısı</span><span class="sxs-lookup"><span data-stu-id="add74-139">C# construct</span></span>|<span data-ttu-id="add74-140">F#algılar</span><span class="sxs-lookup"><span data-stu-id="add74-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="add74-141">`ref` Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="add74-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="add74-142">`ref readonly` Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="add74-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="add74-143">`in ref` Parametre</span><span class="sxs-lookup"><span data-stu-id="add74-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="add74-144">`out ref` Parametre</span><span class="sxs-lookup"><span data-stu-id="add74-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="add74-145">Aşağıdaki tabloda neler gösterilmektedir F# gösterir:</span><span class="sxs-lookup"><span data-stu-id="add74-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="add74-146">F#yapısı</span><span class="sxs-lookup"><span data-stu-id="add74-146">F# construct</span></span>|<span data-ttu-id="add74-147">Yayılan yapısı</span><span class="sxs-lookup"><span data-stu-id="add74-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="add74-148">`inref<'T>` Bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="add74-148">`inref<'T>` argument</span></span>|<span data-ttu-id="add74-149">`[In]` bağımsız değişken özniteliği</span><span class="sxs-lookup"><span data-stu-id="add74-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="add74-150">`inref<'T>` döndürülecek</span><span class="sxs-lookup"><span data-stu-id="add74-150">`inref<'T>` return</span></span>|<span data-ttu-id="add74-151">`modreq` öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="add74-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="add74-152">`inref<'T>` soyut yuvası veya uygulama</span><span class="sxs-lookup"><span data-stu-id="add74-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="add74-153">`modreq` bağımsız değişken veya dönüş</span><span class="sxs-lookup"><span data-stu-id="add74-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="add74-154">`outref<'T>` Bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="add74-154">`outref<'T>` argument</span></span>|<span data-ttu-id="add74-155">`[Out]` bağımsız değişken özniteliği</span><span class="sxs-lookup"><span data-stu-id="add74-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="add74-156">Tür çıkarımı ve kuralları aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="add74-156">Type inference and overloading rules</span></span>

<span data-ttu-id="add74-157">Bir `inref<'T>` türü tarafından çıkarılan F# derleyici aşağıdaki durumlarda:</span><span class="sxs-lookup"><span data-stu-id="add74-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="add74-158">Olan bir .NET parametre veya dönüş türü bir `IsReadOnly` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="add74-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="add74-159">`this` Değişebilir hiçbir alan bir yapı türü işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="add74-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="add74-160">Bir bellek konumunun adresini başka bir türetilmiş `inref<_>` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="add74-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="add74-161">Örtük bir adres, bir `inref` alınır, bir yükleme türünde bir bağımsız değişken ile `SomeType` türünde bir bağımsız değişken bir aşırı yüklemesi için tercih edilen `inref<SomeType>`.</span><span class="sxs-lookup"><span data-stu-id="add74-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="add74-162">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="add74-162">For example:</span></span>

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

<span data-ttu-id="add74-163">Her iki durumda da alma aşırı `System.DateTime` alma aşırı yerine çözümlendiği `inref<System.DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="add74-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="add74-164">ByRef benzeri yapılar</span><span class="sxs-lookup"><span data-stu-id="add74-164">Byref-like structs</span></span>

<span data-ttu-id="add74-165">Ek olarak `byref` / `inref` / `outref` sorularının cevabını, uyması için kendi yapılar tanımlayabilirsiniz `byref`-semantiği ister.</span><span class="sxs-lookup"><span data-stu-id="add74-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="add74-166">Bunun <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliği:</span><span class="sxs-lookup"><span data-stu-id="add74-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="add74-167">`IsByRefLike` değil gelmez `Struct`.</span><span class="sxs-lookup"><span data-stu-id="add74-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="add74-168">Her ikisi de türünde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="add74-168">Both must be present on the type.</span></span>

<span data-ttu-id="add74-169">Bir "`byref`-gibi" yapıda F# yığın bağlı değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="add74-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="add74-170">Bu, hiçbir zaman yönetilen yığında ayrılır.</span><span class="sxs-lookup"><span data-stu-id="add74-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="add74-171">A `byref`-gibi yaşam süresi ve yakalama olmayan hakkında güçlü denetimleri kümesiyle zorlanmış olarak yapı yüksek performanslı programlama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="add74-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="add74-172">Kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="add74-172">The rules are:</span></span>

* <span data-ttu-id="add74-173">İşlev parametrelerini, yöntem parametreleri, yerel değişkenler döner kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="add74-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="add74-174">Statik olamaz veya bir sınıf ya da normal yapı üyelerinin örneği.</span><span class="sxs-lookup"><span data-stu-id="add74-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="add74-175">Herhangi bir kapanış yapısı tarafından yakalanamıyor (`async` yöntemlerde veya lambda ifadelerinde).</span><span class="sxs-lookup"><span data-stu-id="add74-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="add74-176">Genel parametre olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="add74-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="add74-177">Bu son noktası için çok önemlidir F# ardışık düzen stili programlamada, olarak `|>` giriş türlerinden parametreleştiren genel bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="add74-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="add74-178">Bu kısıtlama için rahat olmalıdır `|>` gelecekte satır içidir ve satır içi olmayan genel işlev çağrıları, gövdesinde yapmaz.</span><span class="sxs-lookup"><span data-stu-id="add74-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="add74-179">Bu kurallar çok kesin kullanımını kısıtlıyor olsa da, bunlar promise yüksek performanslı bilgi işlem güvenli bir şekilde karşılamak için bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="add74-179">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="add74-180">ByRef dönüşleri</span><span class="sxs-lookup"><span data-stu-id="add74-180">Byref returns</span></span>

<span data-ttu-id="add74-181">ByRef döndüğü F# işlevleri veya üyeleri kullanılabilir üretilen ve tüketilen.</span><span class="sxs-lookup"><span data-stu-id="add74-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="add74-182">Tüketildiğinde bir `byref`-yöntemi döndürmek, örtük olarak başvurusu kaldırılmış bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="add74-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="add74-183">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="add74-183">For example:</span></span>

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

<span data-ttu-id="add74-184">Zincirleme birden çok çağrı yoluyla bir başvurusu geçirme gibi örtük başvuru önlemek için `&x` (burada `x` değerdir).</span><span class="sxs-lookup"><span data-stu-id="add74-184">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="add74-185">Bir geri dönmek de doğrudan atayabilir `byref`.</span><span class="sxs-lookup"><span data-stu-id="add74-185">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="add74-186">Aşağıdaki (kesinlik temelli yüksek oranda) programı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="add74-186">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
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

<span data-ttu-id="add74-187">Bu çıktı.</span><span class="sxs-lookup"><span data-stu-id="add74-187">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="add74-188">Zkratka için kapsam belirleme</span><span class="sxs-lookup"><span data-stu-id="add74-188">Scoping for byrefs</span></span>

<span data-ttu-id="add74-189">A `let`-ilişkili değeri, tanımlandığı kapsamı aşıyor, başvuru sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="add74-189">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="add74-190">Örneğin, aşağıdaki izin verilmiyor:</span><span class="sxs-lookup"><span data-stu-id="add74-190">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="add74-191">Bu iyileştirmeler açıp ile derleme yaparsanız bağlı olarak farklı sonuçlar alma engeller.</span><span class="sxs-lookup"><span data-stu-id="add74-191">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
