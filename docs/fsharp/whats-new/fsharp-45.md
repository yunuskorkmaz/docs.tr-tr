---
title: 'F # 4,5-F # kılavuzundaki yenilikler'
description: "F # 4,5 ' de bulunan yeni özelliklere genel bakış alın."
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202359"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="d3692-103">F # 4,5 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="d3692-103">What's new in F# 4.5</span></span>

<span data-ttu-id="d3692-104">F # 4,5, F # diline birden çok geliştirme ekler.</span><span class="sxs-lookup"><span data-stu-id="d3692-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="d3692-105">Bu özelliklerin birçoğu, F # ' ta verimli kod yazmanızı sağlamak için birlikte eklenmiştir ve ayrıca bu kodun güvenli olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3692-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="d3692-106">Bunun yapılması, bu yapılar kullanılırken dile birkaç kavram ve önemli miktarda derleyici analizini ekleme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d3692-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="d3692-107">başlarken</span><span class="sxs-lookup"><span data-stu-id="d3692-107">Get started</span></span>

<span data-ttu-id="d3692-108">F # 4,5 tüm .NET Core dağıtımları ve Visual Studio Araçları 'nda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d3692-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="d3692-109">Daha fazla bilgi edinmek için [F # ile çalışmaya](../get-started/index.md) başlayın.</span><span class="sxs-lookup"><span data-stu-id="d3692-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="d3692-110">Span ve ByRef benzeri yapılar</span><span class="sxs-lookup"><span data-stu-id="d3692-110">Span and byref-like structs</span></span>

<span data-ttu-id="d3692-111"><xref:System.Span%601>.NET Core 'da tanıtılan tür, artık f # 4,5 ile başlayan f # ' da izin verilen kesin olarak belirlenmiş bir şekilde bellekteki arabellekleri temsil etmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d3692-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="d3692-112">Aşağıdaki örnek, <xref:System.Span%601> farklı arabellek temsilleri ile bir üzerinde çalışan bir işlevi nasıl yeniden kullanabileceğinizi gösterir:</span><span class="sxs-lookup"><span data-stu-id="d3692-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

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

<span data-ttu-id="d3692-113">Bunun önemli bir yönü, yayılma ve diğer [ByRef benzeri yapıların](../language-reference/structures.md#byreflike-structs) , kullanımlarını beklenmedik şekilde bulacağınız yöntemlerle sınırlayan, derleyicinin gerçekleştirdiği çok rigıd statik analizine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3692-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="d3692-114">Bu, F # 4,5 ' de sunulan performans, ifade ve güvenlik arasındaki temel zorunluluğunu getirir.</span><span class="sxs-lookup"><span data-stu-id="d3692-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="d3692-115">Revaed ByRef 'ler</span><span class="sxs-lookup"><span data-stu-id="d3692-115">Revamped byrefs</span></span>

<span data-ttu-id="d3692-116">F # 4,5 ' den önce, F # ' ta [Byrefs](../language-reference/byrefs.md) güvenli değildi ve çok sayıda uygulama için ses geri alındı.</span><span class="sxs-lookup"><span data-stu-id="d3692-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="d3692-117">F # 4,5 ' de ve ayrıca, span ve ByRef benzeri yapılar için yapılan aynı statik analizler de, ByRef 'ler etrafında ses sorunları ele alındı.</span><span class="sxs-lookup"><span data-stu-id="d3692-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="d3692-118">ınref< 'T> ve outref< 'T></span><span class="sxs-lookup"><span data-stu-id="d3692-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="d3692-119">Salt okunurdur, salt yazılır ve okuma/yazma yönetilen işaretçisinin kavramını göstermek için F # 4,5, `inref<'T>` `outref<'T>` sırasıyla salt okunurdur ve salt yazılır işaretçileri temsil edecek olan türleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="d3692-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="d3692-120">Her birinin farklı anlamları vardır.</span><span class="sxs-lookup"><span data-stu-id="d3692-120">Each have different semantics.</span></span> <span data-ttu-id="d3692-121">Örneğin, bir öğesine yazamaz `inref<'T>` :</span><span class="sxs-lookup"><span data-stu-id="d3692-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="d3692-122">Varsayılan olarak, tür çıkarımı, `inref<'T>` zaten değişebilir olarak bildirilmemiş olmadığı sürece, yönetilen işaretçileri gerçek F # kodu ile satır içinde olacak şekilde çıkarmış olur.</span><span class="sxs-lookup"><span data-stu-id="d3692-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="d3692-123">Bir şeyi yazılabilir yapmak için, `mutable` adresini onu işleyen bir işleve veya üyeye geçirmeden önce bir tür bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3692-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="d3692-124">Daha fazla bilgi için bkz. [Byrefs](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="d3692-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="d3692-125">ReadOnly yapılar</span><span class="sxs-lookup"><span data-stu-id="d3692-125">Readonly structs</span></span>

<span data-ttu-id="d3692-126">F # 4,5 ile başlayarak, bir yapısına şu şekilde açıklama ekleyebilirsiniz <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> :</span><span class="sxs-lookup"><span data-stu-id="d3692-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="d3692-127">Bu, yapıda kesilebilir üye bildirmesinin yanı sıra F # ve C# ' nin bir derlemeden tüketilirken onu ReadOnly olarak görmesini sağlayan meta verileri yayar.</span><span class="sxs-lookup"><span data-stu-id="d3692-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="d3692-128">Daha fazla bilgi için bkz. [ReadOnly yapılar](../language-reference/structures.md#readonly-structs).</span><span class="sxs-lookup"><span data-stu-id="d3692-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="d3692-129">Void işaretçileri</span><span class="sxs-lookup"><span data-stu-id="d3692-129">Void pointers</span></span>

<span data-ttu-id="d3692-130">`voidptr`Türü, aşağıdaki işlevlerde olduğu gibi F # 4,5 ' a eklenir:</span><span class="sxs-lookup"><span data-stu-id="d3692-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="d3692-131">`NativePtr.ofVoidPtr`void işaretçiyi yerel bir int işaretçisine dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="d3692-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="d3692-132">`NativePtr.toVoidPtr`Yerel bir int işaretçisini void işaretçiye dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="d3692-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="d3692-133">Bu, void işaretçilerin kullanıldığı bir yerel bileşenle birlikte çalışırken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d3692-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="d3692-134">`match!` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d3692-134">The `match!` keyword</span></span>

<span data-ttu-id="d3692-135">`match!`Anahtar sözcüğü, bir hesaplama ifadesi içindeyken model eşleştirmeyi geliştirir:</span><span class="sxs-lookup"><span data-stu-id="d3692-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

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

<span data-ttu-id="d3692-136">Bu, genellikle zaman uyumsuz gibi hesaplama ifadelerle seçenekleri (veya diğer türleri) kapsayan kodu kısaltmaya olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d3692-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="d3692-137">Daha fazla bilgi için bkz. [Match!](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="d3692-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="d3692-138">Dizi, liste ve dizi ifadelerinde gevşek yukarı atama gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="d3692-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="d3692-139">Dizi, liste ve sıra ifadeleri içindeki başka bir diğerinin devraldığı türlerin karıştırma, genellikle türetilmiş herhangi bir türü ya da ile üst türüne yukarı atama yapmak için gereklidir `:>` `upcast` .</span><span class="sxs-lookup"><span data-stu-id="d3692-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="d3692-140">Bu, aşağıda gösterildiği gibi gevşek bir şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="d3692-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="d3692-141">Dizi ve liste ifadeleri için girinti ayırma</span><span class="sxs-lookup"><span data-stu-id="d3692-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="d3692-142">F # 4,5 ' den önce, yöntem çağrılarına bağımsız değişken olarak geçirildiğinde dizi ve liste ifadelerini aşırı girintilendirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3692-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="d3692-143">Bu artık gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="d3692-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
