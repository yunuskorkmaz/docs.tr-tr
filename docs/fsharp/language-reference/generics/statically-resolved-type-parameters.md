---
title: Statik Olarak Çözümlenmiş Tür Parametreleri (F#)
description: 'F # kullanmayı öğrenin gerçek bir türüyle derleme zamanında yerine çalışma zamanında değiştirilir statik olarak çözümlenmiş tür parametresi.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da730014f1c40b6c79d72e4f46a18ef36f50de36
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="3767d-103">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="3767d-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="3767d-104">A *statik olarak çözümlenmiş tür parametresi* gerçek bir türüyle derleme zamanında yerine çalışma zamanında değiştirilir bir tür parametresidir.</span><span class="sxs-lookup"><span data-stu-id="3767d-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="3767d-105">Bunlar, bir şapka (^) simgesi öncesinde olur.</span><span class="sxs-lookup"><span data-stu-id="3767d-105">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="3767d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3767d-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="3767d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3767d-107">Remarks</span></span>
<span data-ttu-id="3767d-108">F # dili, tür parametreleri iki farklı tür vardır.</span><span class="sxs-lookup"><span data-stu-id="3767d-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="3767d-109">İlk standart genel tür parametresi türüdür.</span><span class="sxs-lookup"><span data-stu-id="3767d-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="3767d-110">Bunlar kesme işareti (') olarak gösterilen `'T` ve `'U`.</span><span class="sxs-lookup"><span data-stu-id="3767d-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="3767d-111">Bunlar, diğer .NET Framework dillerde genel tür parametreleri için eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="3767d-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="3767d-112">Diğer türü statik olarak çözümlenmiş ve düzeltme işareti sembolü tarafından olarak belirtilen `^T` ve `^U`.</span><span class="sxs-lookup"><span data-stu-id="3767d-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="3767d-113">Statik olarak çözümlenmiş tür parametreleri, tür bağımsız değişkeni belirli bir üye veya üyeleri kullanılması için sahip gerektiğini belirtmenize olanak veren sınırlamalardır üye kısıtlamaları birlikte öncelikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="3767d-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="3767d-114">Normal genel tür parametresi kullanarak bu tür bir kısıtlama oluşturmak için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="3767d-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="3767d-115">Aşağıdaki tabloda benzerlikler ve tür parametreleri iki türleri arasındaki farklar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3767d-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="3767d-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="3767d-116">Feature</span></span>|<span data-ttu-id="3767d-117">Genel</span><span class="sxs-lookup"><span data-stu-id="3767d-117">Generic</span></span>|<span data-ttu-id="3767d-118">Statik olarak çözümlenmiş</span><span class="sxs-lookup"><span data-stu-id="3767d-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="3767d-119">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3767d-119">Syntax</span></span>|<span data-ttu-id="3767d-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="3767d-120">`'T`, `'U`</span></span>|<span data-ttu-id="3767d-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="3767d-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="3767d-122">Çözümleme süresi</span><span class="sxs-lookup"><span data-stu-id="3767d-122">Resolution time</span></span>|<span data-ttu-id="3767d-123">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="3767d-123">Run time</span></span>|<span data-ttu-id="3767d-124">Derleme zamanı</span><span class="sxs-lookup"><span data-stu-id="3767d-124">Compile time</span></span>|
|<span data-ttu-id="3767d-125">Üye kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3767d-125">Member constraints</span></span>|<span data-ttu-id="3767d-126">Üye kısıtlamalarıyla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3767d-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="3767d-127">Üye kısıtlamaları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3767d-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="3767d-128">Kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="3767d-128">Code generation</span></span>|<span data-ttu-id="3767d-129">Tek genel türü veya yöntemi oluşturma bir türü (veya yöntem) standart genel tür parametreleri ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3767d-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="3767d-130">Birden çok örneklemesi türleri ve yöntemleri üretilir, biri her türü için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3767d-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="3767d-131">Türleriyle kullanın</span><span class="sxs-lookup"><span data-stu-id="3767d-131">Use with types</span></span>|<span data-ttu-id="3767d-132">Türlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3767d-132">Can be used on types.</span></span>|<span data-ttu-id="3767d-133">Türleri üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3767d-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="3767d-134">Satır içi işlevlerle kullanın</span><span class="sxs-lookup"><span data-stu-id="3767d-134">Use with inline functions</span></span>|<span data-ttu-id="3767d-135">Hayır.</span><span class="sxs-lookup"><span data-stu-id="3767d-135">No.</span></span> <span data-ttu-id="3767d-136">Satır içi işlev standart genel tür parametresi ile parametreli olamaz.</span><span class="sxs-lookup"><span data-stu-id="3767d-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="3767d-137">Evet.</span><span class="sxs-lookup"><span data-stu-id="3767d-137">Yes.</span></span> <span data-ttu-id="3767d-138">Statik olarak çözümlenmiş tür parametreleri işlevleri veya satır içi olmayan yöntemleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3767d-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="3767d-139">Birçok F # core kitaplık işlevleri, özellikle de operatörler statik olarak çözümlenmiş tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="3767d-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="3767d-140">Bu işlevler ve işleçler satır içi ve verimli kod oluşturma sayısal hesaplamalar için sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3767d-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="3767d-141">Satır içi yöntemleri ve işleçleri veya statik olarak çözümlenmiş tür parametreleri, diğer işlevleri kullanın işlevleri statik olarak çözümlenmiş tür parametreleri kendileri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3767d-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="3767d-142">Genellikle, tür çıkarımı statik olarak çözümlenmiş tür parametreleri gibi satır içi işlevler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3767d-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="3767d-143">Aşağıdaki örnek, bir statik olarak çözümlenmiş tür parametreye sahip çıkarımı yapılan bir işleç tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3767d-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="3767d-144">Çözümlenen türü `(+@)` ikisinin kullanım dayanarak `(+)` ve `(*)`, her iki hangi tür çıkarımı üye statik olarak çözümlenmiş tür parametrelerindeki kısıtlamalar Infer neden olarak.</span><span class="sxs-lookup"><span data-stu-id="3767d-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="3767d-145">Çözümlenmiş tür F # Yorumlayıcı, gösterildiği gibi gibidir.</span><span class="sxs-lookup"><span data-stu-id="3767d-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="3767d-146">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3767d-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="3767d-147">F # 4.1 ile başlayarak, somut tür adları statik olarak çözümlenmiş tür parametresi imzalarında de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3767d-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="3767d-148">Dil önceki sürümlerinde, tür adı derleyici tarafından gerçekten çıkarsanamadı, ancak gerçekte imzası belirlenemedi.</span><span class="sxs-lookup"><span data-stu-id="3767d-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="3767d-149">F # 4.1 itibariyle, somut tür adları statik olarak çözümlenmiş tür parametresi imzalarında de belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="3767d-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="3767d-150">Örnek buradadır:</span><span class="sxs-lookup"><span data-stu-id="3767d-150">Here's an example:</span></span>

```fsharp
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

## <a name="see-also"></a><span data-ttu-id="3767d-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3767d-151">See Also</span></span>
[<span data-ttu-id="3767d-152">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="3767d-152">Generics</span></span>](index.md)

[<span data-ttu-id="3767d-153">Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="3767d-153">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="3767d-154">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="3767d-154">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="3767d-155">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="3767d-155">Constraints</span></span>](constraints.md)

[<span data-ttu-id="3767d-156">Satır İçi İşlevler</span><span class="sxs-lookup"><span data-stu-id="3767d-156">Inline Functions</span></span>](../functions/inline-functions.md)
