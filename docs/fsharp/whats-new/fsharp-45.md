---
title: F# 4.5 -F# Kılavuzu'ndaki yenilikler
description: F# 4.5'te bulunan yeni özelliklere genel bir bakış alın.
ms.date: 11/27/2019
ms.openlocfilehash: 560e3dd941f79b76d3b864ba0f6560be154ebc1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186129"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="f1aed-103">F# 4.5'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="f1aed-103">What's new in F# 4.5</span></span>

<span data-ttu-id="f1aed-104">F# 4.5, F# diline birden fazla iyileştirme ekler.</span><span class="sxs-lookup"><span data-stu-id="f1aed-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="f1aed-105">Bu özelliklerin çoğu, f# ile verimli kod yazmanızı sağlarken aynı zamanda bu kodun güvenli olmasını sağlamak için bir araya getirildi.</span><span class="sxs-lookup"><span data-stu-id="f1aed-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="f1aed-106">Bunu yapmak, bu yapıları kullanırken dile birkaç kavram ve önemli miktarda derleyici çözümlemesi eklemek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f1aed-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="f1aed-107">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="f1aed-107">Get started</span></span>

<span data-ttu-id="f1aed-108">F# 4.5 tüm .NET Core dağıtımlarında ve Visual Studio araçlamalarında mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="f1aed-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="f1aed-109">Daha fazla bilgi edinmek için [F# ile başlayın.](../get-started/index.md)</span><span class="sxs-lookup"><span data-stu-id="f1aed-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="f1aed-110">Span ve byref benzeri structs</span><span class="sxs-lookup"><span data-stu-id="f1aed-110">Span and byref-like structs</span></span>

<span data-ttu-id="f1aed-111">.NET Core'da tanıtılan <xref:System.Span%601> tür, bellekteki arabellekleri güçlü bir şekilde temsil etmenizi sağlar ve f# 4.5 ile başlayarak F# ile izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f1aed-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="f1aed-112">Aşağıdaki örnek, farklı arabellek gösterimleri <xref:System.Span%601> ile çalışan bir işlevi nasıl yeniden kullanabileceğinizi gösterir:</span><span class="sxs-lookup"><span data-stu-id="f1aed-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

<span data-ttu-id="f1aed-113">Bunun önemli bir yönü, Span ve diğer [byref benzeri structs](../language-reference/structures.md#byreflike-structs) beklenmeyen bulabileceğiniz şekillerde kullanımlarını kısıtlayan derleyici tarafından gerçekleştirilen çok katı statik analiz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f1aed-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="f1aed-114">Bu, F# 4.5'te sunulan performans, ifade ve güvenlik arasındaki temel dengedir.</span><span class="sxs-lookup"><span data-stu-id="f1aed-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="f1aed-115">Yenilenen byrefs</span><span class="sxs-lookup"><span data-stu-id="f1aed-115">Revamped byrefs</span></span>

<span data-ttu-id="f1aed-116">F# 4.5'den önce, F# [byrefs](../language-reference/byrefs.md) güvensiz ve çok sayıda uygulama için sağlıksız edildi.</span><span class="sxs-lookup"><span data-stu-id="f1aed-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="f1aed-117">Byrefs etrafında sağlamlık sorunları F # 4.5 ele alınmıştır ve span ve byref benzeri structs için yapılan aynı statik analiz de uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f1aed-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="f1aed-118">inref<'T> ve outref<'T></span><span class="sxs-lookup"><span data-stu-id="f1aed-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="f1aed-119">Yalnızca okuma, yalnızca yazma ve okuma/yazma yönetilen işaretçisi kavramını temsil etmek için, F# 4.5 sırasıyla salt okunur ve yalnızca yazma işaretçilerini temsil etmek için `inref<'T>`, türleri `outref<'T>` tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f1aed-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="f1aed-120">Her birinin farklı anlambilimi var.</span><span class="sxs-lookup"><span data-stu-id="f1aed-120">Each have different semantics.</span></span> <span data-ttu-id="f1aed-121">Örneğin, bir `inref<'T>`yazamazsınız:</span><span class="sxs-lookup"><span data-stu-id="f1aed-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="f1aed-122">Varsayılan olarak, bir şey zaten değişken olarak `inref<'T>` bildirilmedikçe, tür çıkarım, F# kodunun değişmez yapısına uygun olarak yönetilen işaretçilerçıkaracaktır.</span><span class="sxs-lookup"><span data-stu-id="f1aed-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="f1aed-123">Bir şeyi yazılabilir hale getirmek için, bir `mutable` türü, adresini onu manipüle eden bir işleve veya üyeye geçirmeden önce olduğu gibi bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1aed-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="f1aed-124">Daha fazla bilgi için [Byrefs'](../language-reference/byrefs.md)e bakın.</span><span class="sxs-lookup"><span data-stu-id="f1aed-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="f1aed-125">Yalnızca okuma structs</span><span class="sxs-lookup"><span data-stu-id="f1aed-125">Readonly structs</span></span>

<span data-ttu-id="f1aed-126">F# 4.5 ile başlayarak, bir yapıya şu <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> şekilde açıklama ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f1aed-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="f1aed-127">Bu, yapıda mutable bir üye ilan etmenizi sağlar ve F# ve C# bir derleme tüketilen zaman okunmuş olarak tedavi etmek için izin meta veri yakar.</span><span class="sxs-lookup"><span data-stu-id="f1aed-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="f1aed-128">Daha fazla bilgi için [readOnly structs'a](../language-reference/structures.md#readonly-structs)bakın.</span><span class="sxs-lookup"><span data-stu-id="f1aed-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="f1aed-129">Geçersiz işaretçiler</span><span class="sxs-lookup"><span data-stu-id="f1aed-129">Void pointers</span></span>

<span data-ttu-id="f1aed-130">F# 4.5'e `voidptr` aşağıdaki işlevler gibi türü eklenir:</span><span class="sxs-lookup"><span data-stu-id="f1aed-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="f1aed-131">`NativePtr.ofVoidPtr`geçersiz bir işaretçiyi yerel int işaretçisine dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f1aed-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="f1aed-132">`NativePtr.toVoidPtr`bir int işaretçisini geçersiz bir işaretçiye dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f1aed-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="f1aed-133">Bu, geçersiz işaretçileri kullanan yerel bir bileşenle çalışırken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f1aed-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="f1aed-134">`match!` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f1aed-134">The `match!` keyword</span></span>

<span data-ttu-id="f1aed-135">Anahtar `match!` kelime, bir hesaplama ifadesinin içindeyken desen eşleştirmesini geliştirir:</span><span class="sxs-lookup"><span data-stu-id="f1aed-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

<span data-ttu-id="f1aed-136">Bu, genellikle karıştırma seçeneklerini (veya diğer türleri) async gibi hesaplama ifadeleriyle içeren kodu kısaltmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1aed-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="f1aed-137">Daha fazla bilgi için, [maç bakın!](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="f1aed-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="f1aed-138">Dizi, liste ve sıra lı ifadelerde rahat upcasting gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="f1aed-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="f1aed-139">Bir dizi, liste ve dizi ifadeleri içinde başka bir devralabilir karıştırma türleri geleneksel olarak kendi üst `:>` türüne `upcast`veya .</span><span class="sxs-lookup"><span data-stu-id="f1aed-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="f1aed-140">Bu şimdi rahat, aşağıdaki gibi gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1aed-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="f1aed-141">Dizi ve liste ifadeleri için girintinasyon gevşemesi</span><span class="sxs-lookup"><span data-stu-id="f1aed-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="f1aed-142">F# 4.5'den önce, yöntem çağrılarına bağımsız değişken olarak geçtiğinde aşırı girintisli dizi ve liste ifadeleri gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="f1aed-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="f1aed-143">Bu artık gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="f1aed-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
