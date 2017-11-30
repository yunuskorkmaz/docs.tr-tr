---
title: "Statik Olarak Çözümlenmiş Tür Parametreleri (F#)"
description: "F # kullanmayı öğrenin gerçek bir türüyle derleme zamanında yerine çalışma zamanında değiştirilir statik olarak çözümlenmiş tür parametresi."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b3797415-3e49-4f8a-a8ee-fa614c5721aa
ms.openlocfilehash: 88b4590a4323e75949c1915503b51793283792de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="4294e-104">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="4294e-104">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="4294e-105">A *statik olarak çözümlenmiş tür parametresi* gerçek bir türüyle derleme zamanında yerine çalışma zamanında değiştirilir bir tür parametresidir.</span><span class="sxs-lookup"><span data-stu-id="4294e-105">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="4294e-106">Bunlar, bir şapka (^) simgesi öncesinde olur.</span><span class="sxs-lookup"><span data-stu-id="4294e-106">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="4294e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4294e-107">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="4294e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4294e-108">Remarks</span></span>
<span data-ttu-id="4294e-109">F # dili, tür parametreleri iki farklı tür vardır.</span><span class="sxs-lookup"><span data-stu-id="4294e-109">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="4294e-110">İlk standart genel tür parametresi türüdür.</span><span class="sxs-lookup"><span data-stu-id="4294e-110">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="4294e-111">Bunlar kesme işareti (') olarak gösterilen `'T` ve `'U`.</span><span class="sxs-lookup"><span data-stu-id="4294e-111">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="4294e-112">Bunlar, diğer .NET Framework dillerde genel tür parametreleri için eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="4294e-112">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="4294e-113">Diğer türü statik olarak çözümlenmiş ve düzeltme işareti sembolü tarafından olarak belirtilen `^T` ve `^U`.</span><span class="sxs-lookup"><span data-stu-id="4294e-113">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="4294e-114">Statik olarak çözümlenmiş tür parametreleri, tür bağımsız değişkeni belirli bir üye veya üyeleri kullanılması için sahip gerektiğini belirtmenize olanak veren sınırlamalardır üye kısıtlamaları birlikte öncelikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="4294e-114">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="4294e-115">Normal genel tür parametresi kullanarak bu tür bir kısıtlama oluşturmak için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="4294e-115">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="4294e-116">Aşağıdaki tabloda benzerlikler ve tür parametreleri iki türleri arasındaki farklar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4294e-116">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="4294e-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="4294e-117">Feature</span></span>|<span data-ttu-id="4294e-118">Genel</span><span class="sxs-lookup"><span data-stu-id="4294e-118">Generic</span></span>|<span data-ttu-id="4294e-119">Statik olarak çözümlenmiş</span><span class="sxs-lookup"><span data-stu-id="4294e-119">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="4294e-120">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4294e-120">Syntax</span></span>|<span data-ttu-id="4294e-121">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="4294e-121">`'T`, `'U`</span></span>|<span data-ttu-id="4294e-122">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="4294e-122">`^T`, `^U`</span></span>|
|<span data-ttu-id="4294e-123">Çözümleme süresi</span><span class="sxs-lookup"><span data-stu-id="4294e-123">Resolution time</span></span>|<span data-ttu-id="4294e-124">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="4294e-124">Run time</span></span>|<span data-ttu-id="4294e-125">Derleme zamanı</span><span class="sxs-lookup"><span data-stu-id="4294e-125">Compile time</span></span>|
|<span data-ttu-id="4294e-126">Üye kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="4294e-126">Member constraints</span></span>|<span data-ttu-id="4294e-127">Üye kısıtlamalarıyla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4294e-127">Cannot be used with member constraints.</span></span>|<span data-ttu-id="4294e-128">Üye kısıtlamaları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4294e-128">Can be used with member constraints.</span></span>|
|<span data-ttu-id="4294e-129">Kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="4294e-129">Code generation</span></span>|<span data-ttu-id="4294e-130">Tek genel türü veya yöntemi oluşturma bir türü (veya yöntem) standart genel tür parametreleri ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="4294e-130">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="4294e-131">Birden çok örneklemesi türleri ve yöntemleri üretilir, biri her türü için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4294e-131">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="4294e-132">Türleriyle kullanın</span><span class="sxs-lookup"><span data-stu-id="4294e-132">Use with types</span></span>|<span data-ttu-id="4294e-133">Türlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4294e-133">Can be used on types.</span></span>|<span data-ttu-id="4294e-134">Türleri üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4294e-134">Cannot be used on types.</span></span>|
|<span data-ttu-id="4294e-135">Satır içi işlevlerle kullanın</span><span class="sxs-lookup"><span data-stu-id="4294e-135">Use with inline functions</span></span>|<span data-ttu-id="4294e-136">Hayır.</span><span class="sxs-lookup"><span data-stu-id="4294e-136">No.</span></span> <span data-ttu-id="4294e-137">Satır içi işlev standart genel tür parametresi ile parametreli olamaz.</span><span class="sxs-lookup"><span data-stu-id="4294e-137">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="4294e-138">Evet.</span><span class="sxs-lookup"><span data-stu-id="4294e-138">Yes.</span></span> <span data-ttu-id="4294e-139">Statik olarak çözümlenmiş tür parametreleri işlevleri veya satır içi olmayan yöntemleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4294e-139">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="4294e-140">Birçok F # core kitaplık işlevleri, özellikle de operatörler statik olarak çözümlenmiş tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="4294e-140">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="4294e-141">Bu işlevler ve işleçler satır içi ve verimli kod oluşturma sayısal hesaplamalar için sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="4294e-141">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="4294e-142">Satır içi yöntemleri ve işleçleri veya statik olarak çözümlenmiş tür parametreleri, diğer işlevleri kullanın işlevleri statik olarak çözümlenmiş tür parametreleri kendileri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4294e-142">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="4294e-143">Genellikle, tür çıkarımı statik olarak çözümlenmiş tür parametreleri gibi satır içi işlevler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4294e-143">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="4294e-144">Aşağıdaki örnek, bir statik olarak çözümlenmiş tür parametreye sahip çıkarımı yapılan bir işleç tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4294e-144">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="4294e-145">Çözümlenen türü `(+@)` ikisinin kullanım dayanarak `(+)` ve `(*)`, her iki hangi tür çıkarımı üye statik olarak çözümlenmiş tür parametrelerindeki kısıtlamalar Infer neden olarak.</span><span class="sxs-lookup"><span data-stu-id="4294e-145">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="4294e-146">Çözümlenmiş tür F # Yorumlayıcı, gösterildiği gibi gibidir.</span><span class="sxs-lookup"><span data-stu-id="4294e-146">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member (+) : ^a * ^b -> ^d) and
(^a or ^c) : (static member (+) : ^a * ^c -> ^b)
```

<span data-ttu-id="4294e-147">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="4294e-147">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="4294e-148">F # 4.1 ile başlayarak, somut tür adları statik olarak çözümlenmiş tür parametresi imzalarında de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4294e-148">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="4294e-149">Dil önceki sürümlerinde, tür adı derleyici tarafından gerçekten çıkarsanamadı, ancak gerçekte imzası belirlenemedi.</span><span class="sxs-lookup"><span data-stu-id="4294e-149">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="4294e-150">F # 4.1 itibariyle, somut tür adları statik olarak çözümlenmiş tür parametresi imzalarında de belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="4294e-150">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="4294e-151">Örnek buradadır:</span><span class="sxs-lookup"><span data-stu-id="4294e-151">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4294e-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4294e-152">See Also</span></span>
[<span data-ttu-id="4294e-153">Genel türler</span><span class="sxs-lookup"><span data-stu-id="4294e-153">Generics</span></span>](index.md)

[<span data-ttu-id="4294e-154">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="4294e-154">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="4294e-155">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="4294e-155">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="4294e-156">Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="4294e-156">Constraints</span></span>](constraints.md)

[<span data-ttu-id="4294e-157">Satır içi işlevler</span><span class="sxs-lookup"><span data-stu-id="4294e-157">Inline Functions</span></span>](../functions/inline-functions.md)
