---
title: Statik Olarak Çözümlenmiş Tür Parametreleri
description: Statik olarak çözümlenen bir F# tür parametresini nasıl kullanacağınızı öğrenin. Bu, çalışma zamanı yerine derleme sırasında gerçek bir tür ile değiştirilmiştir.
ms.date: 05/16/2016
ms.openlocfilehash: 017c18dd3caaa484ddc653557573f548e3224ca0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425005"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="16386-103">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="16386-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="16386-104">*Statik olarak çözümlenen tür parametresi* , çalışma zamanı yerine derleme sırasında gerçek tür ile değiştirilmiş bir tür parametresidir.</span><span class="sxs-lookup"><span data-stu-id="16386-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="16386-105">Önünde bir şapka (^) simgesi gelir.</span><span class="sxs-lookup"><span data-stu-id="16386-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="16386-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16386-106">Syntax</span></span>

```fsharp
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="16386-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16386-107">Remarks</span></span>

<span data-ttu-id="16386-108">F# Dilde iki farklı türde tür parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="16386-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="16386-109">İlk tür standart genel tür parametresidir.</span><span class="sxs-lookup"><span data-stu-id="16386-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="16386-110">Bunlar, `'T` ve `'U`gibi bir kesme işareti (') ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="16386-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="16386-111">Bunlar, diğer .NET Framework dillerdeki genel tür parametrelerine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="16386-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="16386-112">Diğer tür statik olarak çözümlenir ve `^T` ve `^U`gibi bir giriş işareti simgesiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="16386-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="16386-113">Statik olarak çözümlenen tür parametreleri, genellikle bir tür bağımsız değişkeninin kullanılabilmesi için belirli bir üyeye veya üyelere sahip olması gerektiğini belirtmenize imkan tanıyan kısıtlamalar olan üye kısıtlamalarıyla birlikte faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="16386-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="16386-114">Normal genel tür parametresi kullanarak bu tür bir kısıtlamayı oluşturmanın bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="16386-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="16386-115">Aşağıdaki tabloda, iki tür parametre türüyle benzerlik ve farklar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="16386-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="16386-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="16386-116">Feature</span></span>|<span data-ttu-id="16386-117">Genel</span><span class="sxs-lookup"><span data-stu-id="16386-117">Generic</span></span>|<span data-ttu-id="16386-118">Statik olarak çözümlendi</span><span class="sxs-lookup"><span data-stu-id="16386-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="16386-119">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16386-119">Syntax</span></span>|<span data-ttu-id="16386-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="16386-120">`'T`, `'U`</span></span>|<span data-ttu-id="16386-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="16386-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="16386-122">Çözümleme süresi</span><span class="sxs-lookup"><span data-stu-id="16386-122">Resolution time</span></span>|<span data-ttu-id="16386-123">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="16386-123">Run time</span></span>|<span data-ttu-id="16386-124">Derleme zamanı</span><span class="sxs-lookup"><span data-stu-id="16386-124">Compile time</span></span>|
|<span data-ttu-id="16386-125">Üye kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="16386-125">Member constraints</span></span>|<span data-ttu-id="16386-126">Üye kısıtlamalarıyla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="16386-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="16386-127">, Üye kısıtlamalarıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16386-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="16386-128">Kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="16386-128">Code generation</span></span>|<span data-ttu-id="16386-129">Standart genel tür parametrelerine sahip bir tür (veya yöntem), tek bir genel tür veya yöntemin oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="16386-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="16386-130">Her bir tür için bir tane olmak üzere tür ve yöntemlerin birden çok örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="16386-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="16386-131">Türlerle kullanma</span><span class="sxs-lookup"><span data-stu-id="16386-131">Use with types</span></span>|<span data-ttu-id="16386-132">Türleri üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16386-132">Can be used on types.</span></span>|<span data-ttu-id="16386-133">Türler üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="16386-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="16386-134">Satır içi işlevlerle kullanma</span><span class="sxs-lookup"><span data-stu-id="16386-134">Use with inline functions</span></span>|<span data-ttu-id="16386-135">Hayır.</span><span class="sxs-lookup"><span data-stu-id="16386-135">No.</span></span> <span data-ttu-id="16386-136">Bir satır içi işlev standart bir genel tür parametresiyle parametreleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="16386-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="16386-137">Evet.</span><span class="sxs-lookup"><span data-stu-id="16386-137">Yes.</span></span> <span data-ttu-id="16386-138">Statik olarak çözümlenen tür parametreleri, satır içi olmayan işlevlerde veya metotlarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="16386-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="16386-139">Birçok F# Çekirdek Kitaplığı işlevi, özellikle işleçler, statik olarak çözümlenen tür parametrelerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="16386-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="16386-140">Bu işlevler ve işleçler satır içine alınır ve sayısal hesaplamalar için verimli kod oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="16386-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="16386-141">Ve statik olarak çözümlenen tür parametrelerine sahip diğer işlevleri kullanan satır içi Yöntemler ve işlevler, statik olarak çözümlenen tür parametrelerinin kendisini de kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="16386-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="16386-142">Genellikle, tür çıkarımı statik olarak çözümlenen tür parametrelerine sahip olan satır içi işlevleri tür çıkarıcılar.</span><span class="sxs-lookup"><span data-stu-id="16386-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="16386-143">Aşağıdaki örnek, statik olarak çözümlenen bir tür parametresine sahip olacak şekilde gösterilen bir işleç tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16386-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="16386-144">Çözümlenmiş `(+@)` türü hem `(+)` hem de `(*)`, her ikisi de statik olarak çözümlenen tür parametrelerinde üye kısıtlamalarını çıkarması neden olan tür çıkarımı ' nı temel alır.</span><span class="sxs-lookup"><span data-stu-id="16386-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="16386-145">Çözülen tür, yorumlayıcıda F# gösterildiği gibi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="16386-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="16386-146">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="16386-146">The output is as follows.</span></span>

```console
2
1.500000
```

<span data-ttu-id="16386-147">4,1 ile F# başlayarak statik olarak çözümlenen tür parametre imzaları içinde somut tür adları da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16386-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="16386-148">Dilin önceki sürümlerinde tür adı aslında derleyici tarafından çıkarsanamıyor, ancak İmzada belirtilenemez.</span><span class="sxs-lookup"><span data-stu-id="16386-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="16386-149">F# 4,1 itibariyle statik olarak çözümlenen tür parametre imzaları içinde somut tür adları da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16386-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="16386-150">Örnek buradadır:</span><span class="sxs-lookup"><span data-stu-id="16386-150">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="16386-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16386-151">See also</span></span>

- [<span data-ttu-id="16386-152">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="16386-152">Generics</span></span>](index.md)
- [<span data-ttu-id="16386-153">Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="16386-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="16386-154">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="16386-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="16386-155">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="16386-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="16386-156">Satır İçi İşlevler</span><span class="sxs-lookup"><span data-stu-id="16386-156">Inline Functions</span></span>](../functions/inline-functions.md)
