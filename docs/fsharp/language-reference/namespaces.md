---
title: Ad Alanları (F#)
description: 'F # ad alanı, program öğeleri gruplandırması için bir ad eklemek sağlayarak, ilgili işlevleri alanlarına kod düzenlemek nasıl olanak tanıdığını öğrenin.'
ms.date: 04/24/2017
ms.openlocfilehash: 769a1241f76ac32d3a6a80bd637078493119bb3c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44178266"
---
# <a name="namespaces"></a><span data-ttu-id="cd4b6-103">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="cd4b6-103">Namespaces</span></span>

<span data-ttu-id="cd4b6-104">Bir ad alanı program öğeleri gruplandırması için bir ad eklemek sağlayarak, ilgili işlevleri alanlarına kod düzenlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd4b6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd4b6-105">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="cd4b6-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd4b6-106">Remarks</span></span>

<span data-ttu-id="cd4b6-107">Bir ad alanında kod koymak istiyorsanız, ilk bildirimi dosyasındaki ad alanı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-107">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="cd4b6-108">Tüm dosya içeriğini, ardından ad alanı bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-108">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="cd4b6-109">Ad alanları, doğrudan değerleri ve işlevler içeremez.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-109">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="cd4b6-110">Bunun yerine, değerleri ve işlevleri modüllerde eklenmelidir, ve modülleri ad alanlarında yer alır.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-110">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="cd4b6-111">Ad alanlarını, türleri, modülleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-111">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="cd4b6-112">Ad alanları açıkça ad alanı anahtar sözcüğüyle veya örtük olarak bir modül bildirirken bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-112">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="cd4b6-113">Bir ad alanını açıkça bildirmek için ad alanı adından önce gelen ad alanı anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-113">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="cd4b6-114">Aşağıdaki örnek, bir ad alanı pencere öğeleri ve o ad alanında bulunan bir modül türü ile bildirir. bir kod dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-114">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="cd4b6-115">Dosyanın tüm içeriğini bir modülde varsa, ayrıca ad alanlarında örtülü olarak kullanarak bildirebilirsiniz `module` anahtar sözcüğü ve tam modül adı yeni ad alanı adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-115">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="cd4b6-116">Aşağıdaki örnek, bir ad alanını tanımlayan bir kod dosyası gösterir. `Widgets` ve modül `WidgetsModule`, bir işlev içerir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-116">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="cd4b6-117">Aşağıdaki kod, önceki koda eşdeğerdir, ancak bir yerel modül bildirimi modülüdür.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-117">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="cd4b6-118">Bu durumda, ad alanı, kendi satırında yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-118">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="cd4b6-119">Aynı dosyada bir veya daha fazla ad alanlarında birden fazla modülü gerekiyorsa, yerel modül bildirimlerinde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-119">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="cd4b6-120">Yerel modül bildirimlerinde kullandığınızda, tam ad alanı, modül bildirimlerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-120">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="cd4b6-121">Aşağıdaki kod, bir ad alanı bildirimi ve iki yerel modül bildirimi içeren bir dosya gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-121">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="cd4b6-122">Bu durumda, modülleri doğrudan ad alanında bulunan; dosyayla aynı ada sahip hiçbir örtük olarak oluşturulmuş modülü yoktur.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-122">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="cd4b6-123">Diğer kod dosyasında aşağıdaki gibi bir `do` modülü üye nitelemek gereken bağlama, ad alanında ancak iç modülleri olduğundan `widgetFunction` kullanarak modül adı.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-123">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="cd4b6-124">Bu örnek çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-124">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="cd4b6-125">Daha fazla bilgi için [modülleri](modules.md).</span><span class="sxs-lookup"><span data-stu-id="cd4b6-125">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="cd4b6-126">İç içe geçmiş ad alanları</span><span class="sxs-lookup"><span data-stu-id="cd4b6-126">Nested Namespaces</span></span>

<span data-ttu-id="cd4b6-127">Bir iç içe geçmiş ad alanı oluşturduğunuzda, tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-127">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="cd4b6-128">Aksi takdirde, yeni bir üst düzey ad alanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-128">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="cd4b6-129">Girinti ad alanı bildirimi göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-129">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="cd4b6-130">Aşağıdaki örnek, bir iç içe geçmiş ad alanı bildirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-130">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="cd4b6-131">Dosyaları ve derlemeleri ad alanları</span><span class="sxs-lookup"><span data-stu-id="cd4b6-131">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="cd4b6-132">Ad alanları, birden çok dosyayı tek bir proje veya derleme yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-132">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="cd4b6-133">Terim *ad alanı parça* bir dosyada bulunan bir ad alanı parçası açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-133">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="cd4b6-134">Ad alanları, birden çok bütünleştirilmiş koda da yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-134">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="cd4b6-135">Örneğin, `System` çoğu derleme yayılan ve çoğu iç içe ad alanlarını içeren tüm .NET Framework, ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-135">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="cd4b6-136">Genel Namespace</span><span class="sxs-lookup"><span data-stu-id="cd4b6-136">Global Namespace</span></span>

<span data-ttu-id="cd4b6-137">Önceden tanımlanmış ad alanını kullanacak `global` adları .NET en üst düzey ad alanında yerleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-137">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="cd4b6-138">Ayrıca genel kullanabileceğiniz üst düzey .NET ad alanı, örneğin başvurmak için diğer ad alanları ile ad çakışmalarını çözmek için.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-138">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="cd4b6-139">Özyinelemeli ad alanları</span><span class="sxs-lookup"><span data-stu-id="cd4b6-139">Recursive namespaces</span></span>

<span data-ttu-id="cd4b6-140">F # 4.1 karşılıklı özyinelemeli olarak tüm kapsanan kodunu sağlayan ad alanları kavramını sunar.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="cd4b6-141">Bu aracılığıyla yapılır `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="cd4b6-142">Kullanım `namespace rec` türler ve modüller arasında karşılıklı başvurusal kod yazmak boyutlandırılmamışsa, bazı sorunlar hafifletmek.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="cd4b6-143">Bunun bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cd4b6-143">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="cd4b6-144">Unutmayın özel durum `DontSqueezeTheBananaException` ve sınıf `Banana` de birbirine başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="cd4b6-145">Buna ek olarak, modül `BananaHelpers` ve sınıf `Banana` ayrıca birbirine bakın.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="cd4b6-146">Bu F #'ta kaldırdıysanız express mümkün olmazdı `rec` from anahtar sözcüğü `MutualReferences` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="cd4b6-147">Bu özellik için de kullanılabilir olan en üst düzey [modülleri](modules.md) F # 4.1 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd4b6-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd4b6-148">See also</span></span>

- [<span data-ttu-id="cd4b6-149">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cd4b6-149">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="cd4b6-150">Modüller</span><span class="sxs-lookup"><span data-stu-id="cd4b6-150">Modules</span></span>](modules.md)
- [<span data-ttu-id="cd4b6-151">F # RFC FS-1009 - karşılıklı başvurusal türler ve modüller daha büyük dosyaları kapsamlarda üzerinden izin ver</span><span class="sxs-lookup"><span data-stu-id="cd4b6-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
