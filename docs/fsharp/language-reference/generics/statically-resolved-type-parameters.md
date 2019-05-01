---
title: Statik Olarak Çözümlenmiş Tür Parametreleri
description: Nasıl kullanacağınızı öğrenin bir F# derleme zamanında yerine çalışma zamanında gerçek türle değiştirilen statik olarak çözümlenen tür parametresi.
ms.date: 05/16/2016
ms.openlocfilehash: 9ad23a881e644dfe2bccd56fa04d3c219b51cf7d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937494"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="812e5-103">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="812e5-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="812e5-104">A *statik olarak çözümlenmiş tür parametresi* derleme zamanında yerine çalışma zamanında gerçek türle değiştirilen bir parametre türüdür.</span><span class="sxs-lookup"><span data-stu-id="812e5-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="812e5-105">Bunlar, bir şapka (^) simgesi öncesinde olur.</span><span class="sxs-lookup"><span data-stu-id="812e5-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="812e5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="812e5-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="812e5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="812e5-107">Remarks</span></span>

<span data-ttu-id="812e5-108">İçinde F# dil, iki farklı türden tür parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="812e5-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="812e5-109">Standart genel tür parametresini ilk türüdür.</span><span class="sxs-lookup"><span data-stu-id="812e5-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="812e5-110">Bu kesme işareti (') olarak gösterilen `'T` ve `'U`.</span><span class="sxs-lookup"><span data-stu-id="812e5-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="812e5-111">Bunlar, diğer .NET Framework dillerinde genel tür parametreleri için eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="812e5-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="812e5-112">Diğer tür istatistiksel olarak çözümlenir ve gibi bir şapka karakteri ile belirtilir `^T` ve `^U`.</span><span class="sxs-lookup"><span data-stu-id="812e5-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="812e5-113">Statik çözülen tür parametrelerinin birlikte bir tür bağımsız değişkeni belirli bir üyeye veya belirli üyelere kullanılabilmesi için sahip olması gerektiğini belirtmenize izin veren kısıtlamalar olan üye kısıtlamalarıyla öncelikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="812e5-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="812e5-114">Normal genel tür parametre kullanarak bu tür bir kısıtlama oluşturmanın hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="812e5-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="812e5-115">İki tür parametre çeşidi arasındaki benzerlikler ve aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="812e5-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="812e5-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="812e5-116">Feature</span></span>|<span data-ttu-id="812e5-117">Genel</span><span class="sxs-lookup"><span data-stu-id="812e5-117">Generic</span></span>|<span data-ttu-id="812e5-118">Statik olarak çözümlenmiş</span><span class="sxs-lookup"><span data-stu-id="812e5-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="812e5-119">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="812e5-119">Syntax</span></span>|<span data-ttu-id="812e5-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="812e5-120">`'T`, `'U`</span></span>|<span data-ttu-id="812e5-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="812e5-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="812e5-122">Çözümleme süresi</span><span class="sxs-lookup"><span data-stu-id="812e5-122">Resolution time</span></span>|<span data-ttu-id="812e5-123">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="812e5-123">Run time</span></span>|<span data-ttu-id="812e5-124">Derleme zamanı</span><span class="sxs-lookup"><span data-stu-id="812e5-124">Compile time</span></span>|
|<span data-ttu-id="812e5-125">Üye kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="812e5-125">Member constraints</span></span>|<span data-ttu-id="812e5-126">Üye kısıtlamaları ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="812e5-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="812e5-127">Üye kısıtlamaları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="812e5-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="812e5-128">Kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="812e5-128">Code generation</span></span>|<span data-ttu-id="812e5-129">Standart genel türdeki parametrelere sahip bir türü (veya yöntem), bir tek genel tür veya yöntemin nesildeki sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="812e5-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="812e5-130">Türlerin ve yöntemlerin birden çok örnek oluşumu oluşturulur, biri her tür için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="812e5-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="812e5-131">Türler ile kullanın</span><span class="sxs-lookup"><span data-stu-id="812e5-131">Use with types</span></span>|<span data-ttu-id="812e5-132">Türlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="812e5-132">Can be used on types.</span></span>|<span data-ttu-id="812e5-133">Türlerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="812e5-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="812e5-134">Satır içi işlevleri ile kullanın</span><span class="sxs-lookup"><span data-stu-id="812e5-134">Use with inline functions</span></span>|<span data-ttu-id="812e5-135">Hayır.</span><span class="sxs-lookup"><span data-stu-id="812e5-135">No.</span></span> <span data-ttu-id="812e5-136">Satır içi işlev bir standart genel tür parametreyle parametreleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="812e5-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="812e5-137">Evet.</span><span class="sxs-lookup"><span data-stu-id="812e5-137">Yes.</span></span> <span data-ttu-id="812e5-138">İşlevleri veya satır içi olmayan yöntemleri statik olarak çözümlenmiş tür parametreleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="812e5-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="812e5-139">Birçok F# çekirdek kitaplığı işlevinde, özellikle işleçlerde, tür parametreleri statik olarak çözümlenmiş.</span><span class="sxs-lookup"><span data-stu-id="812e5-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="812e5-140">Bu işlevler ve işleçler satır içi ve sayısal hesaplamalar için etkili kod oluşturmayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="812e5-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="812e5-141">Satır içi yöntemler ve işleçleri kullanan ya da statik olarak çözümlenmiş tür parametreleri, diğer işlevleri kullanan işlevler statik çözülen tür parametrelerinin kendilerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="812e5-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="812e5-142">Genellikle, tür çıkarımı, statik olarak çözümlenmiş tür parametreleri için gibi satır içi işlevleri çıkarır.</span><span class="sxs-lookup"><span data-stu-id="812e5-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="812e5-143">Aşağıdaki örnek, statik olarak çözümlenmiş tür parametresi için ortaya çıkan bir işleç tanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="812e5-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="812e5-144">Çözümlenen türünü `(+@)` kullanımına dayalı `(+)` ve `(*)`hem statik olarak çözülen tür parametreler üzerinde üye sınırlamalarını çıkarmak çıkarım neden olan.</span><span class="sxs-lookup"><span data-stu-id="812e5-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="812e5-145">Gösterilen çözülen tür F# yorumlayıcısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="812e5-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="812e5-146">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="812e5-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="812e5-147">İle başlayarak F# 4.1, somut tür adları statik olarak çözümlenen tür parametresi imzaları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="812e5-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="812e5-148">Dilin önceki sürümlerinde, tür adı derleyici tarafından gerçekten çıkarılan, ancak gerçekte imzasında belirlenemedi.</span><span class="sxs-lookup"><span data-stu-id="812e5-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="812e5-149">Sürümünden itibaren F# 4.1, somut tür adları statik olarak çözümlenen tür parametresi imzaları de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="812e5-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="812e5-150">Örnek buradadır:</span><span class="sxs-lookup"><span data-stu-id="812e5-150">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="812e5-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="812e5-151">See also</span></span>

- [<span data-ttu-id="812e5-152">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="812e5-152">Generics</span></span>](index.md)
- [<span data-ttu-id="812e5-153">Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="812e5-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="812e5-154">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="812e5-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="812e5-155">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="812e5-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="812e5-156">Satır İçi İşlevler</span><span class="sxs-lookup"><span data-stu-id="812e5-156">Inline Functions</span></span>](../functions/inline-functions.md)