---
title: ByRef’ler
description: 'F # içinde, alt düzey programlama için kullanılan ByRef ve ByRef benzeri türler hakkında bilgi edinin.'
ms.date: 11/04/2019
ms.openlocfilehash: ff2c06d8940f7341d5d8b1d942be264bfac586c5
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740321"
---
# <a name="byrefs"></a><span data-ttu-id="21455-103">ByRef’ler</span><span class="sxs-lookup"><span data-stu-id="21455-103">Byrefs</span></span>

<span data-ttu-id="21455-104">F #, alt düzey programlama alanında ele alan iki önemli özellik alanına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="21455-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="21455-105">`byref` / `inref` / `outref` Yönetilen işaretçiler olan türler.</span><span class="sxs-lookup"><span data-stu-id="21455-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="21455-106">Çalışma zamanında geçersiz bir program derleyememesi için kullanım kısıtlamalarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="21455-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="21455-107">`byref`Benzer semantiğe ve aynı derleme zamanı kısıtlamalarına sahip olan bir [Yapı](structures.md) olan, benzeri bir struct `byref<'T>` .</span><span class="sxs-lookup"><span data-stu-id="21455-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="21455-108">Örnek olarak bir örnektir <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="21455-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="21455-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="21455-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="21455-110">ByRef, ınref ve outref</span><span class="sxs-lookup"><span data-stu-id="21455-110">Byref, inref, and outref</span></span>

<span data-ttu-id="21455-111">Üç biçimi vardır `byref` :</span><span class="sxs-lookup"><span data-stu-id="21455-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="21455-112">`inref<'T>`, temel alınan değeri okumak için yönetilen bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="21455-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="21455-113">`outref<'T>`, temel alınan değere yazmak için yönetilen bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="21455-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="21455-114">`byref<'T>`, temel alınan değeri okumak ve yazmak için yönetilen bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="21455-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="21455-115">Bir olması `byref<'T>` `inref<'T>` beklendiğinde geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="21455-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="21455-116">Benzer şekilde, bir `byref<'T>` beklenen yerde bir de geçirilebilir `outref<'T>` .</span><span class="sxs-lookup"><span data-stu-id="21455-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="21455-117">ByRef 'ler kullanma</span><span class="sxs-lookup"><span data-stu-id="21455-117">Using byrefs</span></span>

<span data-ttu-id="21455-118">Kullanmak için bir `inref<'T>` işaretçi değeri almanız gerekir `&` :</span><span class="sxs-lookup"><span data-stu-id="21455-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn $"Now: %O{dt}"

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="21455-119">Bir veya kullanarak işaretçiye yazmak için `outref<'T>` `byref<'T>` bir işaretçi aldığınız değeri de yapmalısınız `mutable` .</span><span class="sxs-lookup"><span data-stu-id="21455-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn $"Now: %O{dt}"
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="21455-120">Yalnızca işaretçiyi okumak yerine yazıyorsanız, yerine kullanmayı göz önünde bulundurun `outref<'T>` `byref<'T>` .</span><span class="sxs-lookup"><span data-stu-id="21455-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="21455-121">Inref semantiği</span><span class="sxs-lookup"><span data-stu-id="21455-121">Inref semantics</span></span>

<span data-ttu-id="21455-122">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="21455-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="21455-123">Anlam, bu, aşağıdakiler anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="21455-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="21455-124">`x`İşaretçinin sahibi yalnızca değeri okumak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="21455-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="21455-125">`struct`İçinde iç içe geçmiş alanlara alınan herhangi bir işaretçiye `SomeStruct` tür verilir `inref<_>` .</span><span class="sxs-lookup"><span data-stu-id="21455-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="21455-126">Aşağıdakiler de doğrudur:</span><span class="sxs-lookup"><span data-stu-id="21455-126">The following is also true:</span></span>

* <span data-ttu-id="21455-127">Diğer iş parçacıklarının veya diğer adların yazma erişimine sahip olmadığı kesin değildir `x` .</span><span class="sxs-lookup"><span data-stu-id="21455-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="21455-128">' A `SomeStruct` kadar sabit olan bir engel yoktur `x` `inref` .</span><span class="sxs-lookup"><span data-stu-id="21455-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="21455-129">Ancak **, sabit olan** F # değer türleri için, `this` işaretçi bir olarak algılanır `inref` .</span><span class="sxs-lookup"><span data-stu-id="21455-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="21455-130">Tüm bu kuralların birlikte bir işaretçi sahibinin, `inref` işaret edilen belleğin hemen içeriğini değiştirebileceğine ilişkin anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="21455-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="21455-131">Outref semantiği</span><span class="sxs-lookup"><span data-stu-id="21455-131">Outref semantics</span></span>

<span data-ttu-id="21455-132">Amacı, `outref<'T>` işaretçinin yalnızca üzerine yazılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="21455-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="21455-133">Beklenmedik şekilde, `outref<'T>` ada rağmen temel alınan değerin okunmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="21455-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="21455-134">Bu uyumluluk amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="21455-134">This is for compatibility purposes.</span></span> <span data-ttu-id="21455-135">Anlamsal olarak, `outref<'T>` şundan farklı değildir `byref<'T>` .</span><span class="sxs-lookup"><span data-stu-id="21455-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="21455-136">C ile birlikte çalışma\#</span><span class="sxs-lookup"><span data-stu-id="21455-136">Interop with C\#</span></span>

<span data-ttu-id="21455-137">C#, `in ref` `out ref` dönüşe ek olarak ve anahtar sözcüklerini destekler `ref` .</span><span class="sxs-lookup"><span data-stu-id="21455-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="21455-138">Aşağıdaki tabloda, F # ' ın C# ' ın nasıl yorumlayacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="21455-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="21455-139">C# yapısı</span><span class="sxs-lookup"><span data-stu-id="21455-139">C# construct</span></span>|<span data-ttu-id="21455-140">F # anlar</span><span class="sxs-lookup"><span data-stu-id="21455-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="21455-141">`ref` dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="21455-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="21455-142">`ref readonly` dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="21455-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="21455-143">`in ref` parametresinin</span><span class="sxs-lookup"><span data-stu-id="21455-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="21455-144">`out ref` parametresinin</span><span class="sxs-lookup"><span data-stu-id="21455-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="21455-145">Aşağıdaki tabloda, hangi F # yayar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="21455-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="21455-146">F # yapısı</span><span class="sxs-lookup"><span data-stu-id="21455-146">F# construct</span></span>|<span data-ttu-id="21455-147">Yayınlanan Yapı</span><span class="sxs-lookup"><span data-stu-id="21455-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="21455-148">`inref<'T>` bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="21455-148">`inref<'T>` argument</span></span>|<span data-ttu-id="21455-149">`[In]` bağımsız değişkende özniteliği</span><span class="sxs-lookup"><span data-stu-id="21455-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="21455-150">`inref<'T>` döndürülmesini</span><span class="sxs-lookup"><span data-stu-id="21455-150">`inref<'T>` return</span></span>|<span data-ttu-id="21455-151">`modreq` değer üzerinde öznitelik</span><span class="sxs-lookup"><span data-stu-id="21455-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="21455-152">`inref<'T>` Soyut yuva veya uygulamada</span><span class="sxs-lookup"><span data-stu-id="21455-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="21455-153">`modreq` bağımsız değişkende veya dönüşte</span><span class="sxs-lookup"><span data-stu-id="21455-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="21455-154">`outref<'T>` bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="21455-154">`outref<'T>` argument</span></span>|<span data-ttu-id="21455-155">`[Out]` bağımsız değişkende özniteliği</span><span class="sxs-lookup"><span data-stu-id="21455-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="21455-156">Tür çıkarımı ve aşırı yükleme kuralları</span><span class="sxs-lookup"><span data-stu-id="21455-156">Type inference and overloading rules</span></span>

<span data-ttu-id="21455-157">Bir `inref<'T>` tür, F # derleyicisi tarafından aşağıdaki durumlarda algılanır:</span><span class="sxs-lookup"><span data-stu-id="21455-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="21455-158">Özniteliği olan bir .NET parametresi veya dönüş türü `IsReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="21455-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="21455-159">`this`Değişebilir alanı olmayan bir struct türündeki işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21455-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="21455-160">Başka bir işaretçiden türetilmiş bellek konumunun adresi `inref<_>` .</span><span class="sxs-lookup"><span data-stu-id="21455-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="21455-161">Örtük bir adresi `inref` çekilirken, türü bağımsız değişkenine sahip bir aşırı yükleme, `SomeType` türünde bir bağımsız değişkenle bir aşırı yüklemeye tercih edilir `inref<SomeType>` .</span><span class="sxs-lookup"><span data-stu-id="21455-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="21455-162">Örnek:</span><span class="sxs-lookup"><span data-stu-id="21455-162">For example:</span></span>

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

<span data-ttu-id="21455-163">Her iki durumda da, alma aşırı yüklemeler yerine, bu aşırı yüklemeler `System.DateTime` çözümlenmelidir `inref<System.DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="21455-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="21455-164">ByRef benzeri yapılar</span><span class="sxs-lookup"><span data-stu-id="21455-164">Byref-like structs</span></span>

<span data-ttu-id="21455-165">Trio 'ya ek olarak `byref` / `inref` / `outref` , benzer semantiğe uygun olan kendi yapı birimlerinizi tanımlayabilirsiniz `byref` .</span><span class="sxs-lookup"><span data-stu-id="21455-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="21455-166">Bu, <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliğiyle yapılır:</span><span class="sxs-lookup"><span data-stu-id="21455-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="21455-167">`IsByRefLike` göstermez `Struct` .</span><span class="sxs-lookup"><span data-stu-id="21455-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="21455-168">Her ikisi de türünde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21455-168">Both must be present on the type.</span></span>

<span data-ttu-id="21455-169">`byref`F # içinde "-LIKE" yapısı, yığın bağlantılı bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="21455-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="21455-170">Yönetilen yığında hiçbir şekilde ayrılmadı.</span><span class="sxs-lookup"><span data-stu-id="21455-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="21455-171">Bir `byref` -LIKE yapısı, yoğun ömür ve yakalama olmayan bir güçlü denetim kümesiyle zorlandığından, yüksek performanslı programlama için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="21455-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="21455-172">Kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="21455-172">The rules are:</span></span>

* <span data-ttu-id="21455-173">İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem geri dönüş olarak kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="21455-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="21455-174">Bunlar statik veya bir sınıfın ya da normal yapının örnek üyeleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="21455-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="21455-175">Bunlar herhangi bir kapanış yapısı ( `async` Yöntemler veya lambda ifadeleri) tarafından yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="21455-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="21455-176">Genel parametre olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="21455-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="21455-177">Bu son nokta, F # ardışık düzen stili programlama için önemlidir. Bu, `|>` giriş türlerini parametreleştiren genel bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="21455-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="21455-178">Bu kısıtlama `|>` gelecekte, satır içi olduğu için gevşek olabilir ve gövdesinde satır içi olmayan genel işlevlere hiçbir çağrı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="21455-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="21455-179">Bu kurallar kullanımı kesin olarak kısıtlıyor olsa da, yüksek performanslı bilgi işlem taahhüdünü güvenli bir şekilde yerine getirmek için bu işlemleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="21455-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="21455-180">ByRef dönüşler</span><span class="sxs-lookup"><span data-stu-id="21455-180">Byref returns</span></span>

<span data-ttu-id="21455-181">F # işlevlerinden ByRef dönüşler veya Üyeler üretilebilir ve tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="21455-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="21455-182">Bir `byref` döndüren yöntemi kullanırken, değer örtük olarak başvurulduğunu.</span><span class="sxs-lookup"><span data-stu-id="21455-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="21455-183">Örnek:</span><span class="sxs-lookup"><span data-stu-id="21455-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn $"%d{squared}"
```

<span data-ttu-id="21455-184">ByRef değeri döndürmek için değeri içeren değişken geçerli kapsamdan daha uzun bir süre etkin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21455-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="21455-185">Ayrıca, ByRef döndürmek için `&value` (değeri geçerli kapsamdan daha uzun süre bulunan bir değişkendir) kullanın.</span><span class="sxs-lookup"><span data-stu-id="21455-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="21455-186">Birden çok zincirleme çağrı yoluyla başvuru geçirme gibi örtük başvuruya engel olmak için kullanın `&x` (burada `x` değeri).</span><span class="sxs-lookup"><span data-stu-id="21455-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="21455-187">Ayrıca, bir dönüşe doğrudan atayabilirsiniz `byref` .</span><span class="sxs-lookup"><span data-stu-id="21455-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="21455-188">Aşağıdaki (son derece kesinlik düzeyi) programı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="21455-188">Consider the following (highly imperative) program:</span></span>

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
    printfn $"Original sequence: %O{c}"

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn $"New sequence:      %O{c}"

    0 // return an integer exit code
```

<span data-ttu-id="21455-189">Bu çıktı.</span><span class="sxs-lookup"><span data-stu-id="21455-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="21455-190">ByRef 'ler için kapsam</span><span class="sxs-lookup"><span data-stu-id="21455-190">Scoping for byrefs</span></span>

<span data-ttu-id="21455-191">Bir `let` -bağlanacak değerin başvurusu tanımlandığı kapsamı aşamaz.</span><span class="sxs-lookup"><span data-stu-id="21455-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="21455-192">Örneğin, aşağıdakilere izin verilmez:</span><span class="sxs-lookup"><span data-stu-id="21455-192">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="21455-193">Bu, iyileştirmelere göre derlemenize bağlı olarak farklı sonuçlar almanızı önler.</span><span class="sxs-lookup"><span data-stu-id="21455-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
