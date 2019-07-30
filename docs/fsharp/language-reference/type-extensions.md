---
title: Tür Genişletmeleri
description: Tür uzantılarının F# daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize nasıl izin vereceğinizi öğrenin.
ms.date: 02/08/2019
ms.openlocfilehash: 502b8636052139b39c800447870c6076a8cd2643
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630192"
---
# <a name="type-extensions"></a><span data-ttu-id="ee439-103">Tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="ee439-103">Type extensions</span></span>

<span data-ttu-id="ee439-104">Tür uzantıları ( _genişletmeler_de denir), daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize olanak sağlayan bir özellik ailesidir.</span><span class="sxs-lookup"><span data-stu-id="ee439-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="ee439-105">Üç özellik şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ee439-105">The three features are:</span></span>

* <span data-ttu-id="ee439-106">İç tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="ee439-106">Intrinsic type extensions</span></span>
* <span data-ttu-id="ee439-107">İsteğe bağlı tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="ee439-107">Optional type extensions</span></span>
* <span data-ttu-id="ee439-108">Uzantı yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ee439-108">Extension methods</span></span>

<span data-ttu-id="ee439-109">Her biri farklı senaryolarda kullanılabilir ve farklı avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="ee439-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee439-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee439-110">Syntax</span></span>

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="ee439-111">İç tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="ee439-111">Intrinsic type extensions</span></span>

<span data-ttu-id="ee439-112">İç tür uzantısı, Kullanıcı tanımlı bir türü genişleten bir tür uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="ee439-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="ee439-113">İç tür uzantılarının, genişledikleri türle aynı dosyada **ve** aynı ad alanında veya modülde tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee439-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="ee439-114">Diğer herhangi bir tanım, [isteğe bağlı tür uzantılarına](type-extensions.md#optional-type-extensions)neden olur.</span><span class="sxs-lookup"><span data-stu-id="ee439-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="ee439-115">İç tür uzantıları bazen tür bildiriminden işlevselliği birbirinden ayıran temizleyici bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="ee439-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="ee439-116">Aşağıdaki örnek, bir iç tür uzantısının nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="ee439-116">The following example shows how to define an intrinsic type extension:</span></span>

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

<span data-ttu-id="ee439-117">Bir tür uzantısı kullanmak, aşağıdakilerin her birini ayırmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="ee439-117">Using a type extension allows you to separate each of the following:</span></span>

* <span data-ttu-id="ee439-118">Bir `Variant` türün bildirimi</span><span class="sxs-lookup"><span data-stu-id="ee439-118">The declaration of a `Variant` type</span></span>
* <span data-ttu-id="ee439-119">`Variant` Sınıfı "şekle" göre yazdırma işlevselliği</span><span class="sxs-lookup"><span data-stu-id="ee439-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
* <span data-ttu-id="ee439-120">Nesne stili `.`gösterimle yazdırma işlevlerine erişmenin bir yolu</span><span class="sxs-lookup"><span data-stu-id="ee439-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="ee439-121">Bu, her şeyi üzerinde `Variant`üye olarak tanımlamaya alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="ee439-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="ee439-122">Doğal olarak daha iyi bir yaklaşım olmasa da, bazı durumlarda işlevlerin temizleyici bir gösterimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee439-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="ee439-123">İç tür uzantıları, genişlettikleri türün üyeleri olarak derlenir ve tür yansıma tarafından incelenirse tür üzerinde görünür.</span><span class="sxs-lookup"><span data-stu-id="ee439-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="ee439-124">İsteğe bağlı tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="ee439-124">Optional type extensions</span></span>

<span data-ttu-id="ee439-125">İsteğe bağlı bir tür uzantısı, genişletilmekte olan türün özgün modülünün, ad alanının veya derlemenin dışında görünen bir uzantıdır.</span><span class="sxs-lookup"><span data-stu-id="ee439-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="ee439-126">İsteğe bağlı tür uzantıları, kendi tanımladığınız bir türü genişletmek için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee439-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="ee439-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ee439-127">For example:</span></span>

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

<span data-ttu-id="ee439-128">Artık, `Extensions` modül üzerinde `RepeatElements` çalıştığınız kapsamda açıldığı sürece bir üyesi olan <xref:System.Collections.Generic.IEnumerable%601> olarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee439-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="ee439-129">İsteğe bağlı uzantılar, yansıma tarafından incelenmişse genişletilmiş tür üzerinde görünmez.</span><span class="sxs-lookup"><span data-stu-id="ee439-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="ee439-130">İsteğe bağlı uzantılar modüllerde olmalıdır ve yalnızca uzantıyı içeren modül açık olduğunda ya da kapsamda yoksa kapsam içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="ee439-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="ee439-131">İsteğe bağlı uzantı üyeleri, nesne örneğinin örtük olarak ilk parametre olarak geçirildiği statik üyelere derlenir.</span><span class="sxs-lookup"><span data-stu-id="ee439-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="ee439-132">Ancak bunlar, nasıl bildirilenler doğrultusunda örnek üye veya statik üyeler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="ee439-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="ee439-133">İsteğe bağlı uzantı üyeleri, C# veya vb tüketicilerine de görünmez.</span><span class="sxs-lookup"><span data-stu-id="ee439-133">Optional extension members are also not visible to C# or VB consumers.</span></span> <span data-ttu-id="ee439-134">Yalnızca başka F# bir kodda tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee439-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="ee439-135">İç ve isteğe bağlı tür uzantılarının genel sınırlaması</span><span class="sxs-lookup"><span data-stu-id="ee439-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="ee439-136">Tür değişkeninin kısıtlı olduğu genel bir türde bir tür uzantısı bildirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ee439-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="ee439-137">Gereksinim, uzantı bildiriminin kısıtlaması, belirtilen tür kısıtlamasıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="ee439-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="ee439-138">Ancak, tanımlı bir tür ve tür uzantısı arasında kısıtlamalar eşleştirildiği halde, bir kısıtlama, tür parametresinde, belirtilen türden farklı bir gereksinim getiren bir genişletilmiş üyenin gövdesi tarafından çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="ee439-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="ee439-139">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ee439-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="ee439-140">Bu kodu isteğe bağlı bir tür uzantısıyla çalışacak şekilde almanın bir yolu yoktur:</span><span class="sxs-lookup"><span data-stu-id="ee439-140">There is no way to get this code to work with an optional type extension:</span></span>

* <span data-ttu-id="ee439-141">Olduğu gibi, `Sum` üyenin tür uzantısının tanımladığı sayıdan farklı bir `'T` kısıtlaması`static member get_Zero` ( `static member (+)`ve) vardır.</span><span class="sxs-lookup"><span data-stu-id="ee439-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
* <span data-ttu-id="ee439-142">Tür uzantısının aynı kısıtlamaya `Sum` sahip olacak şekilde değiştirilmesi, ' deki `IEnumerable<'T>`tanımlı kısıtlamayla artık eşleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="ee439-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
* <span data-ttu-id="ee439-143">`member this.Sum` Olarak`member inline this.Sum` değiştirmek, tür kısıtlamalarının eşleşmeyen bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="ee439-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="ee439-144">İstenen, "boşluk olarak float" ve bir tür genişledikleri gibi sunulabilir statik yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="ee439-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="ee439-145">Bu, uzantı yöntemlerinin gerekli hale geldiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="ee439-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="ee439-146">Uzantı yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ee439-146">Extension methods</span></span>

<span data-ttu-id="ee439-147">Son olarak, uzantı yöntemleri (bazen "C# stil uzantısı üyeleri" olarak da adlandırılır) bir F# sınıf üzerinde statik üye yöntemi olarak ' de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee439-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="ee439-148">Uzantı yöntemleri, tür değişkenini kısıtlayan genel bir tür üzerinde uzantı tanımlamak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ee439-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="ee439-149">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ee439-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="ee439-150">Kullanıldığında, bu kod ' de `Sum` <xref:System.Collections.Generic.IEnumerable%601>tanımlandığı gibi görünür, bu yüzden `Extensions` açık veya kapsam içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="ee439-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

## <a name="other-remarks"></a><span data-ttu-id="ee439-151">Diğer açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee439-151">Other remarks</span></span>

<span data-ttu-id="ee439-152">Tür uzantıları da aşağıdaki özniteliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ee439-152">Type extensions also have the following attributes:</span></span>

* <span data-ttu-id="ee439-153">Erişilebilen herhangi bir tür genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee439-153">Any type that can be accessed can be extended.</span></span>
* <span data-ttu-id="ee439-154">İç ve isteğe bağlı tür uzantıları, yalnızca yöntemleri değil _herhangi bir_ üye türünü tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ee439-154">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="ee439-155">Bu nedenle, örneğin uzantı özellikleri de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ee439-155">So extension properties are also possible, for example.</span></span>
* <span data-ttu-id="ee439-156">[Söz diziminde belirteç,](type-extensions.md#syntax) normal üyelerde olduğu gibi, çağrılan türün örneğini temsil eder. `self-identifier`</span><span class="sxs-lookup"><span data-stu-id="ee439-156">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
* <span data-ttu-id="ee439-157">Genişletilmiş Üyeler statik veya örnek üyeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee439-157">Extended members can be static or instance members.</span></span>
* <span data-ttu-id="ee439-158">Tür uzantısı üzerindeki tür değişkenleri, belirtilen tür kısıtlamasıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="ee439-158">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="ee439-159">Tür uzantıları için aşağıdaki sınırlamalar de mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="ee439-159">The following limitations also exist for type extensions:</span></span>

* <span data-ttu-id="ee439-160">Tür uzantıları sanal veya soyut yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ee439-160">Type extensions do not support virtual or abstract methods.</span></span>
* <span data-ttu-id="ee439-161">Tür uzantıları, geçersiz kılma yöntemlerini genişletmeler olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ee439-161">Type extensions do not support override methods as augmentations.</span></span>
* <span data-ttu-id="ee439-162">Tür uzantıları [statik olarak çözümlenen tür parametrelerini](./generics/statically-resolved-type-parameters.md)desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ee439-162">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
* <span data-ttu-id="ee439-163">İsteğe bağlı tür uzantıları, oluşturucuları genişletmeler olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ee439-163">Optional Type extensions do not support constructors as augmentations.</span></span>
* <span data-ttu-id="ee439-164">Tür genişletmeleri [tür kısaltmaları](type-abbreviations.md)üzerinde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="ee439-164">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
* <span data-ttu-id="ee439-165">Tür uzantıları için `byref<'T>` geçerli değildir (ancak bildirilenler olabilir).</span><span class="sxs-lookup"><span data-stu-id="ee439-165">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
* <span data-ttu-id="ee439-166">Tür uzantıları, öznitelikler için geçerli değildir (ancak bildirilenler olabilir).</span><span class="sxs-lookup"><span data-stu-id="ee439-166">Type extensions are not valid for attributes (though they can be declared).</span></span>
* <span data-ttu-id="ee439-167">Aynı ada sahip diğer yöntemleri aşırı yükleyen uzantılar tanımlayabilirsiniz, ancak belirsiz bir çağrı varsa F# derleyici uzantı olmayan yöntemlere tercih verir.</span><span class="sxs-lookup"><span data-stu-id="ee439-167">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="ee439-168">Son olarak, bir tür için birden çok iç tür uzantısı varsa, tüm üyelerin benzersiz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee439-168">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="ee439-169">İsteğe bağlı tür uzantıları için, aynı türe sahip farklı tür uzantılarındaki Üyeler aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee439-169">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="ee439-170">Belirsizlik hataları yalnızca istemci kodu aynı üye adlarını tanımlayan iki farklı kapsam açarsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="ee439-170">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee439-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee439-171">See also</span></span>

- [<span data-ttu-id="ee439-172">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ee439-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="ee439-173">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ee439-173">Members</span></span>](./members/index.md)
