---
title: Tür Genişletmeleri
description: 'F # tür uzantılarının daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize nasıl izin sağladığını öğrenin.'
ms.date: 02/05/2020
ms.openlocfilehash: 8fdb2d5e527643b23d24a6118e8cef6b11f1a546
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559134"
---
# <a name="type-extensions"></a><span data-ttu-id="15972-103">Tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="15972-103">Type extensions</span></span>

<span data-ttu-id="15972-104">Tür uzantıları ( _genişletmeler_de denir), daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize olanak sağlayan bir özellik ailesidir.</span><span class="sxs-lookup"><span data-stu-id="15972-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="15972-105">Üç özellik şunlardır:</span><span class="sxs-lookup"><span data-stu-id="15972-105">The three features are:</span></span>

- <span data-ttu-id="15972-106">İç tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="15972-106">Intrinsic type extensions</span></span>
- <span data-ttu-id="15972-107">İsteğe bağlı tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="15972-107">Optional type extensions</span></span>
- <span data-ttu-id="15972-108">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="15972-108">Extension methods</span></span>

<span data-ttu-id="15972-109">Her biri farklı senaryolarda kullanılabilir ve farklı avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="15972-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="15972-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="15972-110">Syntax</span></span>

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
    [<Extension>]
    static member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="15972-111">İç tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="15972-111">Intrinsic type extensions</span></span>

<span data-ttu-id="15972-112">İç tür uzantısı, Kullanıcı tanımlı bir türü genişleten bir tür uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="15972-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="15972-113">İç tür uzantılarının, genişledikleri türle aynı dosyada **ve** aynı ad alanında veya modülde tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="15972-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="15972-114">Diğer herhangi bir tanım, [isteğe bağlı tür uzantılarına](type-extensions.md#optional-type-extensions)neden olur.</span><span class="sxs-lookup"><span data-stu-id="15972-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="15972-115">İç tür uzantıları bazen tür bildiriminden işlevselliği birbirinden ayıran temizleyici bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="15972-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="15972-116">Aşağıdaki örnek, bir iç tür uzantısının nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="15972-116">The following example shows how to define an intrinsic type extension:</span></span>

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

<span data-ttu-id="15972-117">Bir tür uzantısı kullanmak, aşağıdakilerin her birini ayırmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="15972-117">Using a type extension allows you to separate each of the following:</span></span>

- <span data-ttu-id="15972-118">Bir `Variant` türün bildirimi</span><span class="sxs-lookup"><span data-stu-id="15972-118">The declaration of a `Variant` type</span></span>
- <span data-ttu-id="15972-119">`Variant`Sınıfı "şekle" göre yazdırma işlevselliği</span><span class="sxs-lookup"><span data-stu-id="15972-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
- <span data-ttu-id="15972-120">Nesne stili gösterimle yazdırma işlevlerine erişmenin bir yolu `.`</span><span class="sxs-lookup"><span data-stu-id="15972-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="15972-121">Bu, her şeyi üzerinde üye olarak tanımlamaya alternatiftir `Variant` .</span><span class="sxs-lookup"><span data-stu-id="15972-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="15972-122">Doğal olarak daha iyi bir yaklaşım olmasa da, bazı durumlarda işlevlerin temizleyici bir gösterimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="15972-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="15972-123">İç tür uzantıları, genişlettikleri türün üyeleri olarak derlenir ve tür yansıma tarafından incelenirse tür üzerinde görünür.</span><span class="sxs-lookup"><span data-stu-id="15972-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="15972-124">İsteğe bağlı tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="15972-124">Optional type extensions</span></span>

<span data-ttu-id="15972-125">İsteğe bağlı bir tür uzantısı, genişletilmekte olan türün özgün modülünün, ad alanının veya derlemenin dışında görünen bir uzantıdır.</span><span class="sxs-lookup"><span data-stu-id="15972-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="15972-126">İsteğe bağlı tür uzantıları, kendi tanımladığınız bir türü genişletmek için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="15972-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="15972-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="15972-127">For example:</span></span>

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

<span data-ttu-id="15972-128">Artık, `RepeatElements` <xref:System.Collections.Generic.IEnumerable%601> `Extensions` modül üzerinde çalıştığınız kapsamda açıldığı sürece bir üyesi olan olarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15972-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="15972-129">İsteğe bağlı uzantılar, yansıma tarafından incelenmişse genişletilmiş tür üzerinde görünmez.</span><span class="sxs-lookup"><span data-stu-id="15972-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="15972-130">İsteğe bağlı uzantılar modüllerde olmalıdır ve yalnızca uzantıyı içeren modül açık olduğunda ya da kapsamda yoksa kapsam içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="15972-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="15972-131">İsteğe bağlı uzantı üyeleri, nesne örneğinin örtük olarak ilk parametre olarak geçirildiği statik üyelere derlenir.</span><span class="sxs-lookup"><span data-stu-id="15972-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="15972-132">Ancak bunlar, nasıl bildirilenler doğrultusunda örnek üye veya statik üyeler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="15972-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="15972-133">İsteğe bağlı uzantı üyeleri, C# veya Visual Basic tüketicilerine de görünmez.</span><span class="sxs-lookup"><span data-stu-id="15972-133">Optional extension members are also not visible to C# or Visual Basic consumers.</span></span> <span data-ttu-id="15972-134">Bunlar yalnızca diğer F # kodunda tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="15972-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="15972-135">İç ve isteğe bağlı tür uzantılarının genel sınırlaması</span><span class="sxs-lookup"><span data-stu-id="15972-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="15972-136">Tür değişkeninin kısıtlı olduğu genel bir türde bir tür uzantısı bildirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="15972-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="15972-137">Gereksinim, uzantı bildiriminin kısıtlaması, belirtilen tür kısıtlamasıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="15972-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="15972-138">Ancak, tanımlı bir tür ve tür uzantısı arasında kısıtlamalar eşleştirildiği halde, bir kısıtlama, tür parametresinde, belirtilen türden farklı bir gereksinim getiren bir genişletilmiş üyenin gövdesi tarafından çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="15972-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="15972-139">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="15972-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="15972-140">Bu kodu isteğe bağlı bir tür uzantısıyla çalışacak şekilde almanın bir yolu yoktur:</span><span class="sxs-lookup"><span data-stu-id="15972-140">There is no way to get this code to work with an optional type extension:</span></span>

- <span data-ttu-id="15972-141">Olduğu gibi, `Sum` üyenin `'T` `static member get_Zero` tür uzantısının tanımladığı sayıdan farklı bir kısıtlaması (ve `static member (+)` ) vardır.</span><span class="sxs-lookup"><span data-stu-id="15972-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
- <span data-ttu-id="15972-142">Tür uzantısının aynı kısıtlamaya sahip olacak şekilde değiştirilmesi, `Sum` ' deki tanımlı kısıtlamayla artık eşleşmeyecektir `IEnumerable<'T>` .</span><span class="sxs-lookup"><span data-stu-id="15972-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
- <span data-ttu-id="15972-143">`member this.Sum`Olarak değiştirmek `member inline this.Sum` , tür kısıtlamalarının eşleşmeyen bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="15972-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="15972-144">İstenen, "boşluk olarak float" ve bir tür genişledikleri gibi sunulabilir statik yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="15972-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="15972-145">Bu, uzantı yöntemlerinin gerekli hale geldiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="15972-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="15972-146">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="15972-146">Extension methods</span></span>

<span data-ttu-id="15972-147">Son olarak, uzantı yöntemleri (bazen "C# stil uzantısı üyeleri" olarak adlandırılır), F # içinde bir sınıf üzerinde statik üye yöntemi olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="15972-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="15972-148">Uzantı yöntemleri, tür değişkenini kısıtlayan genel bir tür üzerinde uzantı tanımlamak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="15972-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="15972-149">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="15972-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Collections.Generic
open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="15972-150">Kullanıldığında, bu kod ' de tanımlandığı gibi görünür, bu `Sum` <xref:System.Collections.Generic.IEnumerable%601> yüzden `Extensions` Açık veya kapsam içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="15972-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

<span data-ttu-id="15972-151">Uzantının VB.NET kodu tarafından kullanılabilmesi için, `ExtensionAttribute` derleme düzeyinde bir ek gereklidir:</span><span class="sxs-lookup"><span data-stu-id="15972-151">For the extension to be available to VB.NET code, an extra `ExtensionAttribute` is required at the assembly level:</span></span>

```fsharp
module AssemblyInfo
open System.Runtime.CompilerServices
[<assembly:Extension>]
do ()
```

## <a name="other-remarks"></a><span data-ttu-id="15972-152">Diğer açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15972-152">Other remarks</span></span>

<span data-ttu-id="15972-153">Tür uzantıları da aşağıdaki özniteliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="15972-153">Type extensions also have the following attributes:</span></span>

- <span data-ttu-id="15972-154">Erişilebilen herhangi bir tür genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="15972-154">Any type that can be accessed can be extended.</span></span>
- <span data-ttu-id="15972-155">İç ve isteğe bağlı tür uzantıları, yalnızca yöntemleri değil _herhangi bir_ üye türünü tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="15972-155">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="15972-156">Bu nedenle, örneğin uzantı özellikleri de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="15972-156">So extension properties are also possible, for example.</span></span>
- <span data-ttu-id="15972-157">`self-identifier` [Söz diziminde](type-extensions.md#syntax) belirteç, normal üyelerde olduğu gibi, çağrılan türün örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="15972-157">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
- <span data-ttu-id="15972-158">Genişletilmiş Üyeler statik veya örnek üyeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="15972-158">Extended members can be static or instance members.</span></span>
- <span data-ttu-id="15972-159">Tür uzantısı üzerindeki tür değişkenleri, belirtilen tür kısıtlamasıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="15972-159">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="15972-160">Tür uzantıları için aşağıdaki sınırlamalar de mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="15972-160">The following limitations also exist for type extensions:</span></span>

- <span data-ttu-id="15972-161">Tür uzantıları sanal veya soyut yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="15972-161">Type extensions do not support virtual or abstract methods.</span></span>
- <span data-ttu-id="15972-162">Tür uzantıları, geçersiz kılma yöntemlerini genişletmeler olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="15972-162">Type extensions do not support override methods as augmentations.</span></span>
- <span data-ttu-id="15972-163">Tür uzantıları [statik olarak çözümlenen tür parametrelerini](./generics/statically-resolved-type-parameters.md)desteklemez.</span><span class="sxs-lookup"><span data-stu-id="15972-163">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
- <span data-ttu-id="15972-164">İsteğe bağlı tür uzantıları, oluşturucuları genişletmeler olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="15972-164">Optional Type extensions do not support constructors as augmentations.</span></span>
- <span data-ttu-id="15972-165">Tür genişletmeleri [tür kısaltmaları](type-abbreviations.md)üzerinde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="15972-165">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
- <span data-ttu-id="15972-166">Tür uzantıları için geçerli değildir `byref<'T>` (ancak bildirilenler olabilir).</span><span class="sxs-lookup"><span data-stu-id="15972-166">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
- <span data-ttu-id="15972-167">Tür uzantıları, öznitelikler için geçerli değildir (ancak bildirilenler olabilir).</span><span class="sxs-lookup"><span data-stu-id="15972-167">Type extensions are not valid for attributes (though they can be declared).</span></span>
- <span data-ttu-id="15972-168">Aynı ada sahip diğer yöntemleri aşırı yükleyen uzantılar tanımlayabilirsiniz, ancak belirsiz bir çağrı varsa F # derleyicisi uzantı olmayan yöntemlere tercih verir.</span><span class="sxs-lookup"><span data-stu-id="15972-168">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="15972-169">Son olarak, bir tür için birden çok iç tür uzantısı varsa, tüm üyelerin benzersiz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="15972-169">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="15972-170">İsteğe bağlı tür uzantıları için, aynı türe sahip farklı tür uzantılarındaki Üyeler aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="15972-170">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="15972-171">Belirsizlik hataları yalnızca istemci kodu aynı üye adlarını tanımlayan iki farklı kapsam açarsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="15972-171">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="15972-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15972-172">See also</span></span>

- [<span data-ttu-id="15972-173">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="15972-173">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="15972-174">Üyeler</span><span class="sxs-lookup"><span data-stu-id="15972-174">Members</span></span>](./members/index.md)
