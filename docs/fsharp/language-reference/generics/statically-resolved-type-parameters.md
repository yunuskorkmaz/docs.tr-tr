---
title: Statik Olarak Çözümlenmiş Tür Parametreleri
description: Statik olarak çözümlenen bir F# tür parametresini nasıl kullanacağınızı öğrenin. Bu, çalışma zamanı yerine derleme sırasında gerçek bir tür ile değiştirilmiştir.
ms.date: 05/16/2016
ms.openlocfilehash: bc3310192cdaa5ae4862b8aee46b6152f61da38a
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082921"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="22ed0-103">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="22ed0-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="22ed0-104">*Statik olarak çözümlenen tür parametresi* , çalışma zamanı yerine derleme sırasında gerçek tür ile değiştirilmiş bir tür parametresidir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="22ed0-105">Önünde bir şapka (^) simgesi gelir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="22ed0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22ed0-106">Syntax</span></span>

```fsharp
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="22ed0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22ed0-107">Remarks</span></span>

<span data-ttu-id="22ed0-108">F# Dilde iki farklı türde tür parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="22ed0-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="22ed0-109">İlk tür standart genel tür parametresidir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="22ed0-110">Bunlar, ve `'T` `'U`' de olduğu gibi bir kesme işareti (') ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="22ed0-111">Bunlar, diğer .NET Framework dillerdeki genel tür parametrelerine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="22ed0-112">Diğer tür statik olarak çözümlenir ve ve `^T` `^U`' de olduğu gibi bir giriş işareti simgesiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="22ed0-113">Statik olarak çözümlenen tür parametreleri, genellikle bir tür bağımsız değişkeninin kullanılabilmesi için belirli bir üyeye veya üyelere sahip olması gerektiğini belirtmenize imkan tanıyan kısıtlamalar olan üye kısıtlamalarıyla birlikte faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="22ed0-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="22ed0-114">Normal genel tür parametresi kullanarak bu tür bir kısıtlamayı oluşturmanın bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="22ed0-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="22ed0-115">Aşağıdaki tabloda, iki tür parametre türüyle benzerlik ve farklar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="22ed0-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="22ed0-116">Feature</span></span>|<span data-ttu-id="22ed0-117">Genel</span><span class="sxs-lookup"><span data-stu-id="22ed0-117">Generic</span></span>|<span data-ttu-id="22ed0-118">Statik olarak çözümlendi</span><span class="sxs-lookup"><span data-stu-id="22ed0-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="22ed0-119">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22ed0-119">Syntax</span></span>|<span data-ttu-id="22ed0-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="22ed0-120">`'T`, `'U`</span></span>|<span data-ttu-id="22ed0-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="22ed0-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="22ed0-122">Çözümleme süresi</span><span class="sxs-lookup"><span data-stu-id="22ed0-122">Resolution time</span></span>|<span data-ttu-id="22ed0-123">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="22ed0-123">Run time</span></span>|<span data-ttu-id="22ed0-124">Derleme zamanı</span><span class="sxs-lookup"><span data-stu-id="22ed0-124">Compile time</span></span>|
|<span data-ttu-id="22ed0-125">Üye kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="22ed0-125">Member constraints</span></span>|<span data-ttu-id="22ed0-126">Üye kısıtlamalarıyla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="22ed0-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="22ed0-127">, Üye kısıtlamalarıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="22ed0-128">Kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="22ed0-128">Code generation</span></span>|<span data-ttu-id="22ed0-129">Standart genel tür parametrelerine sahip bir tür (veya yöntem), tek bir genel tür veya yöntemin oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="22ed0-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="22ed0-130">Her bir tür için bir tane olmak üzere tür ve yöntemlerin birden çok örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="22ed0-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="22ed0-131">Türlerle kullanma</span><span class="sxs-lookup"><span data-stu-id="22ed0-131">Use with types</span></span>|<span data-ttu-id="22ed0-132">Türleri üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-132">Can be used on types.</span></span>|<span data-ttu-id="22ed0-133">Türler üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="22ed0-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="22ed0-134">Satır içi işlevlerle kullanma</span><span class="sxs-lookup"><span data-stu-id="22ed0-134">Use with inline functions</span></span>|<span data-ttu-id="22ed0-135">Hayır.</span><span class="sxs-lookup"><span data-stu-id="22ed0-135">No.</span></span> <span data-ttu-id="22ed0-136">Bir satır içi işlev standart bir genel tür parametresiyle parametreleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="22ed0-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="22ed0-137">Evet.</span><span class="sxs-lookup"><span data-stu-id="22ed0-137">Yes.</span></span> <span data-ttu-id="22ed0-138">Statik olarak çözümlenen tür parametreleri, satır içi olmayan işlevlerde veya metotlarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="22ed0-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="22ed0-139">Birçok F# Çekirdek Kitaplığı işlevi, özellikle işleçler, statik olarak çözümlenen tür parametrelerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="22ed0-140">Bu işlevler ve işleçler satır içine alınır ve sayısal hesaplamalar için verimli kod oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="22ed0-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="22ed0-141">Ve statik olarak çözümlenen tür parametrelerine sahip diğer işlevleri kullanan satır içi Yöntemler ve işlevler, statik olarak çözümlenen tür parametrelerinin kendisini de kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="22ed0-142">Genellikle, tür çıkarımı statik olarak çözümlenen tür parametrelerine sahip olan satır içi işlevleri tür çıkarıcılar.</span><span class="sxs-lookup"><span data-stu-id="22ed0-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="22ed0-143">Aşağıdaki örnek, statik olarak çözümlenen bir tür parametresine sahip olacak şekilde gösterilen bir işleç tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="22ed0-144">Çözümlenme türü `(+@)` , hem hem de `(*)`' nin, her `(+)` ikisi de statik olarak çözümlenen tür parametrelerinde üye kısıtlamalarını çıkarmasına neden olan tür çıkarımı ' nın kullanımını temel alır.</span><span class="sxs-lookup"><span data-stu-id="22ed0-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="22ed0-145">Çözülen tür, yorumlayıcıda F# gösterildiği gibi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="22ed0-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="22ed0-146">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="22ed0-146">The output is as follows.</span></span>

```console
2
1.500000
```

<span data-ttu-id="22ed0-147">4,1 ile F# başlayarak statik olarak çözümlenen tür parametre imzaları içinde somut tür adları da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22ed0-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="22ed0-148">Dilin önceki sürümlerinde tür adı aslında derleyici tarafından çıkarsanamıyor, ancak İmzada belirtilenemez.</span><span class="sxs-lookup"><span data-stu-id="22ed0-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="22ed0-149">F# 4,1 itibariyle statik olarak çözümlenen tür parametre imzaları içinde somut tür adları da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22ed0-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="22ed0-150">Örnek buradadır:</span><span class="sxs-lookup"><span data-stu-id="22ed0-150">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="22ed0-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22ed0-151">See also</span></span>

- [<span data-ttu-id="22ed0-152">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="22ed0-152">Generics</span></span>](index.md)
- [<span data-ttu-id="22ed0-153">Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="22ed0-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="22ed0-154">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="22ed0-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="22ed0-155">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="22ed0-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="22ed0-156">Satır İçi İşlevler</span><span class="sxs-lookup"><span data-stu-id="22ed0-156">Inline Functions</span></span>](../functions/inline-functions.md)
