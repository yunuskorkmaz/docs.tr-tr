---
title: Statik Olarak Çözümlenmiş Tür Parametreleri (F#)
description: Bir F#'ı kullanmayı öğrenin, derleme zamanında yerine çalışma zamanında gerçek türle değiştirilen statik olarak çözümlenmiş tür parametresi.
ms.date: 05/16/2016
ms.openlocfilehash: 747917fef2746dcbf363ef4b717ace5e47229800
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "48032783"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="79bed-103">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="79bed-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="79bed-104">A *statik olarak çözümlenmiş tür parametresi* derleme zamanında yerine çalışma zamanında gerçek türle değiştirilen bir parametre türüdür.</span><span class="sxs-lookup"><span data-stu-id="79bed-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="79bed-105">Bunlar, bir şapka (^) simgesi öncesinde olur.</span><span class="sxs-lookup"><span data-stu-id="79bed-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="79bed-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79bed-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="79bed-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79bed-107">Remarks</span></span>

<span data-ttu-id="79bed-108">F# dilinde iki farklı türden tür parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="79bed-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="79bed-109">Standart genel tür parametresini ilk türüdür.</span><span class="sxs-lookup"><span data-stu-id="79bed-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="79bed-110">Bu kesme işareti (') olarak gösterilen `'T` ve `'U`.</span><span class="sxs-lookup"><span data-stu-id="79bed-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="79bed-111">Bunlar, diğer .NET Framework dillerinde genel tür parametreleri için eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="79bed-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="79bed-112">Diğer tür istatistiksel olarak çözümlenir ve gibi bir şapka karakteri ile belirtilir `^T` ve `^U`.</span><span class="sxs-lookup"><span data-stu-id="79bed-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="79bed-113">Statik çözülen tür parametrelerinin birlikte bir tür bağımsız değişkeni belirli bir üyeye veya belirli üyelere kullanılabilmesi için sahip olması gerektiğini belirtmenize izin veren kısıtlamalar olan üye kısıtlamalarıyla öncelikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="79bed-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="79bed-114">Normal genel tür parametre kullanarak bu tür bir kısıtlama oluşturmanın hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="79bed-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="79bed-115">İki tür parametre çeşidi arasındaki benzerlikler ve aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="79bed-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="79bed-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="79bed-116">Feature</span></span>|<span data-ttu-id="79bed-117">Genel</span><span class="sxs-lookup"><span data-stu-id="79bed-117">Generic</span></span>|<span data-ttu-id="79bed-118">Statik olarak çözümlenmiş</span><span class="sxs-lookup"><span data-stu-id="79bed-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="79bed-119">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79bed-119">Syntax</span></span>|<span data-ttu-id="79bed-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="79bed-120">`'T`, `'U`</span></span>|<span data-ttu-id="79bed-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="79bed-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="79bed-122">Çözümleme süresi</span><span class="sxs-lookup"><span data-stu-id="79bed-122">Resolution time</span></span>|<span data-ttu-id="79bed-123">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="79bed-123">Run time</span></span>|<span data-ttu-id="79bed-124">Derleme zamanı</span><span class="sxs-lookup"><span data-stu-id="79bed-124">Compile time</span></span>|
|<span data-ttu-id="79bed-125">Üye kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="79bed-125">Member constraints</span></span>|<span data-ttu-id="79bed-126">Üye kısıtlamaları ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="79bed-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="79bed-127">Üye kısıtlamaları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="79bed-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="79bed-128">Kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="79bed-128">Code generation</span></span>|<span data-ttu-id="79bed-129">Standart genel türdeki parametrelere sahip bir türü (veya yöntem), bir tek genel tür veya yöntemin nesildeki sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="79bed-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="79bed-130">Türlerin ve yöntemlerin birden çok örnek oluşumu oluşturulur, biri her tür için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="79bed-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="79bed-131">Türler ile kullanın</span><span class="sxs-lookup"><span data-stu-id="79bed-131">Use with types</span></span>|<span data-ttu-id="79bed-132">Türlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="79bed-132">Can be used on types.</span></span>|<span data-ttu-id="79bed-133">Türlerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="79bed-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="79bed-134">Satır içi işlevleri ile kullanın</span><span class="sxs-lookup"><span data-stu-id="79bed-134">Use with inline functions</span></span>|<span data-ttu-id="79bed-135">Hayır.</span><span class="sxs-lookup"><span data-stu-id="79bed-135">No.</span></span> <span data-ttu-id="79bed-136">Satır içi işlev bir standart genel tür parametreyle parametreleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="79bed-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="79bed-137">Evet.</span><span class="sxs-lookup"><span data-stu-id="79bed-137">Yes.</span></span> <span data-ttu-id="79bed-138">İşlevleri veya satır içi olmayan yöntemleri statik olarak çözümlenmiş tür parametreleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="79bed-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="79bed-139">Çoğu F# çekirdek kitaplığı işlevinde, özellikle işleçlerde, statik olarak çözümlenmiş tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="79bed-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="79bed-140">Bu işlevler ve işleçler satır içi ve sayısal hesaplamalar için etkili kod oluşturmayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="79bed-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="79bed-141">Satır içi yöntemler ve işleçleri kullanan ya da statik olarak çözümlenmiş tür parametreleri, diğer işlevleri kullanan işlevler statik çözülen tür parametrelerinin kendilerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79bed-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="79bed-142">Genellikle, tür çıkarımı, statik olarak çözümlenmiş tür parametreleri için gibi satır içi işlevleri çıkarır.</span><span class="sxs-lookup"><span data-stu-id="79bed-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="79bed-143">Aşağıdaki örnek, statik olarak çözümlenmiş tür parametresi için ortaya çıkan bir işleç tanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="79bed-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="79bed-144">Çözümlenen türünü `(+@)` kullanımına dayalı `(+)` ve `(*)`hem statik olarak çözülen tür parametreler üzerinde üye sınırlamalarını çıkarmak çıkarım neden olan.</span><span class="sxs-lookup"><span data-stu-id="79bed-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="79bed-145">Çözümlenen tür F# yorumlayıcıda gösterildiği gibidir.</span><span class="sxs-lookup"><span data-stu-id="79bed-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="79bed-146">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="79bed-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="79bed-147">F# 4.1 ile başlayarak, somut tür adları statik olarak çözümlenen tür parametresi imzaları de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79bed-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="79bed-148">Dilin önceki sürümlerinde, tür adı derleyici tarafından gerçekten çıkarılan, ancak gerçekte imzasında belirlenemedi.</span><span class="sxs-lookup"><span data-stu-id="79bed-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="79bed-149">F# 4.1 itibariyle, somut tür adları statik olarak çözümlenen tür parametresi imzaları de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79bed-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="79bed-150">Örnek buradadır:</span><span class="sxs-lookup"><span data-stu-id="79bed-150">Here's an example:</span></span>

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a><span data-ttu-id="79bed-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79bed-151">See also</span></span>

- [<span data-ttu-id="79bed-152">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="79bed-152">Generics</span></span>](index.md)
- [<span data-ttu-id="79bed-153">Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="79bed-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="79bed-154">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="79bed-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="79bed-155">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="79bed-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="79bed-156">Satır İçi İşlevler</span><span class="sxs-lookup"><span data-stu-id="79bed-156">Inline Functions</span></span>](../functions/inline-functions.md)
